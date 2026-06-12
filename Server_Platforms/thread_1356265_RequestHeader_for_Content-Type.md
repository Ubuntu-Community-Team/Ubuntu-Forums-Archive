---
title: "RequestHeader for Content-Type"
date: 2009-12-15
forum: Server Platforms
---

### Post by congling on 2009-12-15
Hi all,
   I'm trying to modify the "Content-Type" request header by RequestHeader in mod_headers. But it worked wrong for my ubuntu. The RequestHeader command changed the response header (not the request header) and returns the source code of the php file (php was already been installed) .
  
  The apache server was installed by "apt-get install apache2" and the mod_headers was dynamic-loaded by headers.load. I was tried in my gentoo machine with apache built by src code (with mod_headers built-in). It worked well. So i think it might be the issue of module load order.
   Could you help me on these? thx
  
Here's the config file
   <VirtualHost *:1001>
        ServerAdmin webmaster@localhost

        DocumentRoot /opt/wwwroot/FirstTest

        <Directory />
                Options FollowSymLinks
                AllowOverride None
                SetEnvIf Content-Type ^(multipart/form-data)(.*) NEW_CONTENT_TYPE=multipart/form-data-alternate$2 OLD_CONTENT_TYPE=$1$2
                RequestHeader set Content-Type %{NEW_CONTENT_TYPE}e env=NEW_CONTENT_TYPE
        </Directory>

        ErrorLog /var/log/apache2/FirstTest.error.log
        LogLevel debug
        CustomLog /var/log/apache2/FirstTest.access.log combined

</VirtualHost>

  
Here's the packet
POST /Hello.php HTTP/1.1
Accept: image/gif, image/jpeg, image/pjpeg, image/pjpeg, application/xaml+xml, application/vnd.ms-xpsdocument, application/x-ms-xbap, application/x-ms-application, application/x-shockwave-flash, application/vnd.ms-excel, application/vnd.ms-powerpoint, application/msword, */*
Referer: [http://10.129.62.17:1001/Hello.php](http://10.129.62.17:1001/Hello.php)
Accept-Language: en-us
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.2; WOW64; Trident/4.0; .NET CLR 2.0.50727; .NET CLR 3.0.04506.30; .NET CLR 3.0.04506.648; .NET CLR 3.5.21022; InfoPath.2; .NET CLR 3.0.4506.2152; .NET CLR 3.5.30729; OfficeLiveConnector.1.2)
Content-Type: multipart/form-data; boundary=---------------------------7d931d3110138
Accept-Encoding: gzip, deflate
Host: 10.129.62.17:1001
Content-Length: 142
Connection: Keep-Alive
Pragma: no-cache

-----------------------------7d931d3110138
Content-Disposition: form-data; name="n"

adfdas
-----------------------------7d931d3110138--


HTTP/1.1 200 OK
Date: Wed, 16 Dec 2009 01:58:49 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Wed, 16 Dec 2009 01:58:14 GMT
ETag: "64266-188-47aced6e4c94b"
Accept-Ranges: bytes
Content-Length: 392
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: multipart/form-data-alternate; boundary=---------------------------7d931d3110138

<html>
<body>

<?php 
		//$file_in   =   file_get_contents( "php://input"); 
		//echo   $file_in; 
		//var_dump($HTTP_POST_FILES);
		$headers =  getallheaders(); 
		echo ($headers["Content-Type1"]);
		//echo ($_POST["n"]);
?>
<form action="Hello.php" method="POST" enctype="multipart/form-data">
	<input type="text" name="n" /><input type="submit" value="submit" />
</form>

</body>
</html>




   

Regards,
Cong Ling

---

### Post by BkkBonanza on 2009-12-15
Content-Type on requests is only for POST method and refers to type of data being sent to server not the type of data you want back. The Accept header controls that.

If you are trying to stop php source code from being sent then that's a different issue. For that you need the directive that tells it to execute not send php files.

AddType application/x-httpd-php .php

---

### Post by congling on 2009-12-15
> **BkkBonaza said:**
> Content-Type on requests is only for POST method and refers to type of data being sent to server not the type of data you want back. The Accept header controls that.

If you are trying to stop php source code from being sent then that's a different issue. For that you need the directive that tells it to execute not send php files.

AddType application/x-httpd-php .php

This line had already been appended to the config file by php5.conf.

I changed the content-type because i wanna get raw content of "multipart/form-data". Php didn't has such method to get it if the content-type is "multipart/form-data". So I need to change the request content-type to get it.

---

### Post by congling on 2009-12-15
I did some research and found RequestHeader works well if the header is not "Content-Type", maybe it's the bug of RequestHeader.

---

### Post by BkkBonanza on 2009-12-15
Php can get the raw form data if you use a method like this,

$data = file_get_contents("php://input");

This captures the raw data from the post and stores it in $data.

---

### Post by congling on 2009-12-15
> **BkkBonaza said:**
> Php can get the raw form data if you use a method like this,

$data = file_get_contents("php://input");

This captures the raw data from the post and stores it in $data.

It won't work if the Content-Type is "Mutltipart/form-data". 
The data will be empty.

---

### Post by BkkBonanza on 2009-12-16
Ah, I see. Maybe try a simpler version of the directive without substitution to see if it makes a difference. For example, for one directory only just set all requests to use that content type with a hard coded value. That way you can verify that it's not some problem in the directive syntax.

---

### Post by congling on 2009-12-16
Finally, I fixed the issue. There maybe some bugs for "RequestHeader set" method on Content-Type. In mod_headers.c (httpd 2.2.14, line 681), the set method is diff to "Content-Type", look at the source code below

> case hdr_set:
if (!strcasecmp(hdr->header, "Content-Type")) {
  ap_set_content_type(r, process_tags(hdr, r));
}
apr_table_setn(headers, hdr->header, process_tags(hdr, r));
break;


I don't figure out the detail on it, but after I change the config, it works pretty well.

SetEnvIf Content-Type ^(multipart/form-data)(.*) NEW_CONTENT_TYPE=multipart/form-data-alternate$2 OLD_CONTENT_TYPE=$1$2
RequestHeader unset Content-Type env=NEW_CONTENT_TYPE
RequestHeader add Content-Type %{NEW_CONTENT_TYPE}e env=NEW_CONTENT_TYPE


So, I think it's the issue of RequestHeader set method on dealing with "Content-Type" in mod_headers.c file.

---

