---
title: "CURL Empty"
date: 2011-10-03
forum: Server Platforms
---

### Post by pgp_protector on 2011-10-03
UPDATE: See Post #3 for what's causing the problem.

I'm trying to debug a SOAP Issue

Server is running on 192.168.1.50 
From my desktop I can access my server as soap.myserver.com (works)

I can access & get a wsdl xml file if I go to soap.myserver.com/SOAP/PADL.wsdl (works)

I can use SoapUI 4.0.0 from my desktop and call & execute the functions from the wsdl file correctly.

But now the part that's confusing me.

If I've got a file on that server called SOAP_Client.php @ soap.myserver.com/SOAP/PADL_Client.php Every thing falls apart.

when calling this code
```

<?php
try{
  $sClient = new SoapClient('http://soap.myserver.com/PADL/PADL.wsdl');	// This Connects to the SOAP Server
 
  $FindID = "12345";		// This is The Shipper ID That We Are Looking For

  $AResult= $sClient->GetInfo($FindID );	// This Runs The Command
 
	echo("Value1 ".$AResult->SOID."<br>");
	echo("Value2 ".$AResult->CustomerPO."<br>");
	echo("Value3 ".$AResult->CustomerSA."<br>");
} catch(SoapFault $e){
  var_dump($e);
}
?>
```

i get this error
```


object(SoapFault)#2 (9) { ["message":protected]=> string(156) "SOAP-ERROR: Parsing WSDL: Couldn't load from 'soap.myserver.com/SOAP/PADL.wsdl' : failed to load external entity "soap.myserver.com/SOAP/PADL.wsdl" " ["string":"Exception":private]=> string(0) "" ["code":protected]=> int(0) ["file":protected]=> string(54) "/var/www/clients/client1/web5/web/SOAP/PADL_client.php" ["line":protected]=> int(3) ["trace":"Exception":private]=> array(1) { [0]=> array(6) { ["file"]=> string(54) "/var/www/clients/client1/web5/web/SOAP/PADL_client.php" ["line"]=> int(3) ["function"]=> string(10) "SoapClient" ["class"]=> string(10) "SoapClient" ["type"]=> string(2) "->" ["args"]=> array(1) { [0]=> string(36) "soap.myserver.com/SOAP/PADL.wsdl" } } } ["previous":"Exception":private]=> NULL ["faultstring"]=> string(156) "SOAP-ERROR: Parsing WSDL: Couldn't load from 'soap.myserver.com/SOAP/PADL.wsdl' : failed to load external entity "soap.myserver.com/SOAP/PADL.wsdl" " ["faultcode"]=> string(4) "WSDL" }
```

So after some searching I was reading about PHP Curl issues that might cause this (don't know if true though)
So I created a simple html page 75 bytes in length and a debugging.php page
```

<?php 
ini_set('display_errors',1);

$curl = curl_init(); 
curl_setopt($curl, CURLOPT_URL, 'http://soap.myserver.com/SOAP/sample.html'); 
curl_setopt($curl, CURLOPT_VERBOSE, true); // Display communication with server
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true); // Return data instead of display to std out
curl_exec($curl); 
print_r(curl_getinfo($curl)); 
curl_error($curl);

curl_close($curl);

?>
```

when going to soap.myerver.com/SOAP/debugging.php I get the following
```

Array ( [url] => http://soap.myserver.com/SOAP/sample.html [content_type] => [http_code] => 0 [header_size] => 0 [request_size] => 0 [filetime] => -1 [ssl_verify_result] => 0 [redirect_count] => 0 [total_time] => 0 [namelookup_time] => 0 [connect_time] => 0 [pretransfer_time] => 0 [size_upload] => 0 [size_download] => 0 [speed_download] => 0 [speed_upload] => 0 [download_content_length] => -1 [upload_content_length] => -1 [starttransfer_time] => 0 [redirect_time] => 0 [certinfo] => Array ( ) )
```

Second note:
the same SOAP_Client.php , SOAP.wsdl, SOAP_Server.php all work on a different server (one is at home one at work)  so I'm thinking it must be in the configuration, but I've no idea what to check now.

---

### Post by pgp_protector on 2011-10-03
ETA Running on Ubuntu 11.04 with webmin


System hostname	padlserver.rigelsystems.com
Operating system	Ubuntu Linux 11.04
Webmin version	1.570
Time on system	Mon Oct 3 18:21:45 2011
Kernel and CPU	Linux 2.6.38-11-server on x86_64
Processor information	AMD Phenom(tm) II X4 840T Processor, 4 cores
System uptime	0 hours, 3 minutes
Running processes	154
CPU load averages	0.87 (1 min) 0.29 (5 mins) 0.10 (15 mins)
CPU usage	0% user, 0% kernel, 0% IO, 100% idle
Real memory	5.60 GB total, 531.47 MB used

Virtual memory	5.75 GB total, 0 bytes used

Local disk space	1.79 TB total, 97.26 GB used

---

### Post by pgp_protector on 2011-10-04
Ok bit more info, I know the problem just not how to solve it.


1) From my windows box I've got the ubuntu server acting like the DNS Server so I can ping my box soap.mydomain.com and it resolves to 192.168.1.50 and pings no problem

2) but from the ubuntu box, if I ping soap.mydomain.com it returns unknown host soap.mydomain.com .  So this is causing all my CURL / SOAP Problems I believe as the system can't resolved any addresses for either SOAP / WSDL or CURL Commands.

So how is it the Box can tell windows where soap.mydomain.com is but doesn't know itself that it's hosting soap.mydomain.com ???

---

