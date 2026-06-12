---
title: "[SOLVED] incorporating cURL and libcURL3 into PHP"
date: 2006-08-16
forum: Ubuntu Backports
---

### Post by afbase on 2006-08-16
okay I installed cURL and libcurl3
```
apt-get install curl
apt-get install libcurl3
```
I copied a small script on my dapper server using curl mod functions into a php file
```
<? 
$url = "http://moneycentral.msn.com/detail/stock_quote"; 
$ch = curl_init(); curl_setopt($ch, CURLOPT_URL,$url); curl_setopt($ch, CURLOPT_FAILONERROR, 1); 
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1); curl_setopt($ch, CURLOPT_RETURNTRANSFER,1); 
curl_setopt($ch, CURLOPT_TIMEOUT, 3); 
curl_setopt($ch, CURLOPT_POST, 1); 
curl_setopt($ch, CURLOPT_POSTFIELDS, "Symbol=".$_GET['ticker'].""); // add POST fields 
$result = curl_exec($ch); // run the whole process curl_close($ch); 
echo $result; 
?>
```
I recieve an error:
Fatal error: Unknown function: curl_init() in C:\xamp\xampp\htdocs\price.php on line 3



So did my installation not incorporate the php mod???
if not, then how can I incoporate cURL into PHP

---

### Post by mlind on 2006-08-16
Why another thread for this? You should probably post this to Breezy or Programming forums instead.

---

### Post by jfang on 2007-06-18
You also need to run one of the following to get CURL working with PHP

apt-get install php4-curl

**OR**

apt-get install php5-curl

---

