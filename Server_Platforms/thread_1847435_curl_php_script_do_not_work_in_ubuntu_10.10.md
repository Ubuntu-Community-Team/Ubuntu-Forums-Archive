---
title: "curl php script do not work in ubuntu 10.10"
date: 2011-09-20
forum: Server Platforms
---

### Post by sheirkoo on 2011-09-20
***i have an ubuntu 10.10 which this script work perfectly in the last.***
***but from few days ago it does not work strangly .***
***i had downgraded the server php version to 5.2.***
***i have test it in fresh ubuntu 10.04 and it work fine there . ***
***i have reinstalled everything apache php curl but no success***
***some curl script works still in 10.10 but this one did not:***
 
<?php 
 
$post="x_fp_timestamp=1316006050&x_fp_sequence=18&x_fp_hash=f9fcf5389a0db5a75e5e1df7hha75fcf&x_login=78676&x_description=verifyme&x_amount=100&x_currency_code=Rial";
 
 
 
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, "[https://Damoon.bankmelli-iran.com/DamoonVerificationController/](https://Damoon.bankmelli-iran.com/DamoonVerificationController/)");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 0);
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);
//curl_setopt ($ch, CURLOPT_HTTPHEADER, array('SOAPAction: ""')); 
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt ($ch, CURLOPT_POSTFIELDS,$post);
$estore = curl_exec ($ch);
//$info = curl_getinfo($ch);
curl_close ($ch);
 
//echo($estore);
print_r($estore);
 
?>
 
***when i run it take some time and show me a blank page with no error in apache logs.***
 
***Can any one help me ?***

---

### Post by linux2001 on 2011-09-22
You can send this question in php forums.
Where you find the answer.
[http://php.net/manual/fr/book.curl.php](http://php.net/manual/fr/book.curl.php)

---

