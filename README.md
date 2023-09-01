<?php


if(isset($_GET['submit'])){
	
	
	$url=$_GET['url'];
    
    $xxx=$_GET['xxx'];
   
     $id=$_GET['id'];
     
    $link=$_GET['link'];
    
    $amu=$_GET['amu'];
   

   


$data='key='.$xxx.'&action=add&service='.$id.'&link='.$link.'&quantity='.$amu.'';

$ch = curl_init();
	curl_setopt($ch, CURLOPT_URL,$url);
	curl_setopt($ch, CURLOPT_POST, 1);
	curl_setopt($ch, CURLOPT_POSTFIELDS,$data);
	curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
	   
	curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
	 $output= curl_exec ($ch);
	$json=json_decode($output,true);
	curl_close ($ch);



echo $output . "<br><br>" . "Done = " . $amu . "<br>" . "link  = " .   $link ;
echo '<meta http-equiv="refresh" content="0">';
}

	


if(!isset($_GET['submit'])){
echo"<form action='' method='get'>
    

<input type='text' name='url'  class='text' placeholder='Enter Smm Api URL' required><br><br>


<input type='text' name='xxx'  class='text' placeholder='Enter Smm Api Key' required><br><br>

<input type='text' name='id'  class='text' placeholder='Enter Service Id' required><br><br>




<input type='text' name='amu'  class='text' placeholder='Enter Maximum Amount' required><br><br>


<input type='text' name='link'  class='text' placeholder='Username/Link Real Account' required><br><br>


";
echo "<input type='submit' class='submit' name='submit' value='submit'>";
}
?>
