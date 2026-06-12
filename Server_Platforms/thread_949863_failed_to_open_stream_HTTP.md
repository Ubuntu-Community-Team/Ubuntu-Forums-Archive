---
title: "failed to open stream: HTTP"
date: 2008-10-16
forum: Server Platforms
---

### Post by angstsix on 2008-10-16
Hello,
I'm getting this error from php on Ubuntu, this is a fresh install ( just downloaded and installed this morning ), using the server edition.

I'm simply using the fopen() function, but it fails every time.
I run this same script and other linux servers with no idea. I'm hoping that one one else here has run into this. any ideas would be a big help!


Warning: file_get_contents([http://maps.google.com/maps/geo?q=](http://maps.google.com/maps/geo?q=)[REMOVE THIS PART) [function.file-get-contents]: failed to open stream: HTTP request failed! in /home/sites/mysite/functions/Common.class.php on line 375


thanks in advance for your time!
-Ken

---

### Post by angstsix on 2008-10-16
well I'm beginning to think this is a Ubuntu bug, as no one seems to have an answer to this problem, and i've searched all over.

my script works on all other linux systems that i've tested with, except for other Ubuntu systems where it continues to fail.  :confused:

---

### Post by cdenley on 2008-10-16
Works fine for me, using file_get_contents and fopen, on hardy and intrepid. Try posting your code, or a simple example which demonstrates your "bug". Why does it mean it must be an ubuntu bug if nobody replied within 45 minutes?

---

### Post by angstsix on 2008-10-16
what version of apache and php are you running?

I think it's a bug because:

a) it runs on several other servers that I've tested it on with the same php config.

b) i've been reading around and other people are having this same issue with Ubuntu while using php 5.2 and above w/apache2.

[PHP]
    Function GetLatLng_old($Address,$Type){
        $Request = "http://maps.google.com/maps/geo?q=" . urlencode($Address) . "&output=xml&key=" . GOOGLE_MAP_KEY;
        return str_replace("|","",trim($Request)); exit;
        $page = file_get_contents($Request);
        $xml = new SimpleXMLElement($page);
        $Result = $xml->Response->Placemark->Point->coordinates;
        $LatLng = explode(",",$Result);
        if($Type == "Lng") return $LatLng[0];
        if($Type == "Lat") return $LatLng[1];
    }
[/PHP]

thats the function that made me notice this. but also readfile, fopen and several other similar functions are not working.
and this is a fresh install of Ubuntu that i just setup this morning, it works on all other servers that i've tested, the only servers that failed this were two Ubuntu servers. thinking that it's a bug had nothing to do with the amount of time that i waited for replied ( even when i post for help, i still continue trying to atleast solve the issue on my own ).

thanks again for your time!
-Ken

---

### Post by cdenley on 2008-10-16
The function you posted seems to just return the url you want to read. After commenting that line, it seems to work correctly.
[PHP]
<?php
print_r(GetLatLng_old('1600 Pennsylvania Avenue NW Washington, DC','Lng'));
    Function GetLatLng_old($Address,$Type){
        $Request = "http://maps.google.com/maps/geo?q=" . urlencode($Address) .$
        //return str_replace("|","",trim($Request)); exit;
        $page = file_get_contents($Request);
        $xml = new SimpleXMLElement($page);
        $Result = $xml->Response->Placemark->Point->coordinates;
        $LatLng = explode(",",$Result);
        if($Type == "Lng") return $LatLng[0];
        if($Type == "Lat") return $LatLng[1];
    }
?>
[/PHP]

```

HTTP/1.1 200 OK
Date: Fri, 17 Oct 2008 00:16:22 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch
X-Powered-By: PHP/5.2.4-2ubuntu5.3
Content-Length: 10
Connection: close
Content-Type: text/html

-77.036541

```

That was on hardy with a default LAMP configuration.

---

### Post by angstsix on 2008-10-17
ah, sorry about that i forgot I had some debug code in there.

this is really odd. i can't make this run on either of the two UBuntu servers that I have here. but runs perfectly on my fedora servers.

php version looks the same; PHP Version 5.2.4-2ubuntu5.3

well I'm offically lost now. :(

---

### Post by cdenley on 2008-10-17
What output does this give you?
[PHP]
<?php
$fp = fsockopen("maps.google.com", 80, $errno, $errstr, 30);
if (!$fp) {
    echo "$errstr ($errno)<br />\n";
} else {
    $out = "GET /maps/geo?q=".urlencode('1600 Pennsylvania Avenue NW Washington, DC')." HTTP/1.1\r\n";
    $out .= "Host: maps.google.com\r\n";
    $out .= "Connection: Close\r\n\r\n";

    fwrite($fp, $out);
    while (!feof($fp)) {
        echo fgets($fp, 128);
    }
    fclose($fp);
}
?>
[/PHP]

---

