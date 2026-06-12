---
title: "Server Status On Web Page"
date: 2008-05-14
forum: Server Platforms
---

### Post by saj0577 on 2008-05-14
Hey,

How do i make a script or get a script from that works like the top part of this page:

[http://www.aspietom.co.uk/status.php](http://www.aspietom.co.uk/status.php)

Saj

---

### Post by Thirtysixway on 2008-05-14
You can use php to ping different ports that are used for each application.

port - service
-----------
21 - ftp
22 - ssh
80 - http
etc etc
```

<?
////////////////server variables/////////////////////////////////
$address ="192.168.1.107";
$port = "4000";

//////////////////////////////////////////////////////////////
echo("<!--");
$checkport = fsockopen($address, $port, $errnum, $errstr, 2);


if(!$checkport){
echo "--><font color=red><b>The server is offline.</b></font>";
}
else{

echo "--><font color=green><b>The server is online.</b></font>";
}
?>

```

This is an example for one port.  This isn't the best method for a busy site, but you can look around.

As for the bandiwdth image, I know I used to have something installed that would generate a .png to a specified folder of bandwidth usage.  I can't find it though :/

---

### Post by Monicker on 2008-05-14
The chart looks like it was produced by cacti or mrtg.

---

### Post by saj0577 on 2008-05-14
Not so much bothered about the chart only the top bit. Thanks alot guys.

Saj

---

### Post by saj0577 on 2008-05-14
Anyone got an easy way to have it so the script works with multiple ports?


Saj

---

### Post by inportb on 2008-05-14
> **Thirtysixway said:**
> You can use php to ping different ports that are used for each application.

You cannot ping different ports to determine connectivity. The ping protocol is different from HTTP, FTP, and other services. Rather, telnet works... which is similar to fsockopen in your script.

---

### Post by Thirtysixway on 2008-05-14
> **inportb said:**
> You cannot ping different ports to determine connectivity. The ping protocol is different from HTTP, FTP, and other services. Rather, telnet works... which is similar to fsockopen in your script.

Whoops, I guess I used the wrong word there, sorry :)



If you want to use it for multiple ports, you can just run it multiple times.  You could even set it up in a function and just include that php file, call the function like  echo display_status("localhost", "22");

---

### Post by saj0577 on 2008-05-15
```
<?PHP

$imap1 = "142";
$smtp1 = "25";
$pop31 = "110";
echo("<!--");
$checkport = fsockopen($address, $imap1, $errnum, $errstr, 2);


if(!$checkport){
echo "--><font color=red><b>offline.</b></font>";
}
else{
echo("<!--");

$checkport2 = fsockopen($address, $smtp1, $errnum, $errstr, 2);


if(!$checkport2){
echo "--><font color=red><b>offline.</b></font>";
}
else{

echo("<!--");
$checkport3 = fsockopen($address, $pop31, $errnum, $errstr, 2);


if(!$checkport3){
echo "--><font color=red><b>offline.</b></font>";
}
else{

echo "--><font color=green><b>online.</b></font>";
}
?>

```

Can someone help me find the error in this please. Basically I want it to say offline if any of the ports are closed and online if they are ALL open.

Thanks Saj

---

### Post by saj0577 on 2008-05-17
Been thinking and is php the language to do this in?
Maybe it would be easier in another language?

Saj

---

### Post by solcott on 2008-05-18
I can fix your script for you to check and deliver [COLOR="Green"]Online.[/COLOR] if everything is up or [COLOR="Red"]Offline.[/COLOR] if anything is closed.

It looks like you are testing a mail server, yes?

I'll post a script in a few minutes that checks 25, 143 and 110.  (or should it really be 142 like in your script, even though 143 is the IMAP port?)

/EDIT:  OK, here you go, a script hat does what I said it did before I edited the post.

Attached and linked to a running copy.
_[This script in action]("http://www.olcottfamily.com/serverstatus/portstatus.php")_ | _[And the source code]("http://www.olcottfamily.com/serverstatus/portstatus.phps")_

---

### Post by saj0577 on 2008-05-18
Thanks alot looks great. :)

Cheers 
Saj

---

### Post by saj0577 on 2008-05-18
Il mark as solved when i tst it :)

Saj

---

