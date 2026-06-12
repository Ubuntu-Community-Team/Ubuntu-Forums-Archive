---
title: "incorporating cURL into php"
date: 2006-08-16
forum: Server Platforms
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
$ch = curl_init();    
curl_setopt($ch, CURLOPT_URL,$url);
curl_setopt($ch, CURLOPT_FAILONERROR, 1);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
curl_setopt($ch, CURLOPT_RETURNTRANSFER,1); 
curl_setopt($ch, CURLOPT_TIMEOUT, 3); 
curl_setopt($ch, CURLOPT_POST, 1); 
curl_setopt($ch, CURLOPT_POSTFIELDS, "Symbol=".$_GET['ticker'].""); // add POST fields
$result = curl_exec($ch); // run the whole process
curl_close($ch); 
echo $result; 
?>

```
I recieve an error:
Fatal error: Unknown function: curl_init() in C:\xamp\xampp\htdocs\price.php on line 3



So did my installation not incorporate the php mod???
if not, then how can I incoporate cURL into PHP

---

### Post by afbase on 2006-08-16
Ok I think i just installed the php-curl mod:
```

apt-get install php5-curl
```
The thing is I just ran my script above again and I got the same error that curl_init() was unknown

---

### Post by jimmygoon on 2006-08-16
First, restart your PC, or at least apache2 ;)

---

### Post by afbase on 2006-08-16
i restarted my server and I still get the error :(

i have yet to find a solution to such a simple problem!!!!!

---

### Post by afbase on 2006-08-16
i have yet to find a solution to the problem folks.  Your help is much appreciated

---

