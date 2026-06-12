---
title: "ddclient not updating zonedit.com"
date: 2008-11-06
forum: Server Platforms
---

### Post by twistedtwig on 2008-11-06
Hi all,

I am having some trouble with ddclient.  I am sure it was working at some point, and believe it is still working to some extent but it is not playing nicely.

I have the following config file:

```
daemon=300
syslog=yes
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.org
protocol=zoneedit1
server=www.zoneedit.com
login=username
password=XXXXXXXXXX
aipoker.co.uk,www.aipoker.co.uk,houseofhawkins.com,www.houseofhawkins.com,spencerandwest.co.uk,www.spencerandwest.co.uk
protocol=dyndns2
server=updates.opendns.com
login=usename
password=XXXXXXXXXXXX
home
```

It seems to be updating opendns.com as that has my current IP (I am not laying lots of money on it actually updating though, it could be coincidence).  But zonedit.com has a different IP altogether and I can not get it to update at all.

I have tried to stop and start ddclient, I have checked the status and it is running but it never updates the IP.

can anyone help me please?

Thanks

---

### Post by twistedtwig on 2008-11-09
Hi all,

I am still stuck with this and would really appreciate some help.

Is there a way to get it to write all the console output to a log file so I can see why it is not updating my IP.

It would seem it is not updating opendns.com either as my IP changed last night and it has not updated this either.

Is there a way to validate each part of the config file?

thanks

---

### Post by twistedtwig on 2008-11-09
I am getting this message in my syslog file:

Nov  9 14:19:18 betty ddclient[32080]: WARNING:  forcing update of home from 90.194.239.24 to 90.195.241.174; 30 days since last update on Thu Oct  9 00:23:59 2008.

I don't know if "home" is the second protocol or some other term, but it is definitely not updating zoneedit. 

I also noticed that for some reason I had 4 copies of ddclient running, but when I killed them all, stopped and started ddclient I only have one copy.

---

### Post by twistedtwig on 2008-11-10
/bump

I hope someone might be able to help me here please.

My IP seems to be changing daily and it is not updating

---

### Post by twistedtwig on 2008-11-12
Running the following commmand gave me a lot of output but I can not see any clues why it failed:

sudo ddclient -daemon=0 -verbose

```
CONNECT:  checkip.dyndns.org
CONNECTED:  using HTTP
SENDING:  GET / HTTP/1.0
SENDING:   Host: checkip.dyndns.org
SENDING:   User-Agent: ddclient/3.7.3
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK

RECEIVE:  Content-Type: text/html

RECEIVE:  Server: DynDNS-CheckIP/1.0

RECEIVE:  Connection: close

RECEIVE:  Cache-Control: no-cache

RECEIVE:  Pragma: no-cache

RECEIVE:  Content-Length: 105

RECEIVE:  

RECEIVE:  <html><head><title>Current IP Check</title></head><body>Current IP Address: 90.194.239.32</body></html>

WARNING:  forcing update of home from 90.194.239.24 to 90.194.239.32; 30 days since last update on Thu Oct  9 00:23:59 2008.
INFO:     setting IP address to 90.194.239.32 for home
UPDATE:   updating home
CONNECT:  updates.opendns.com
CONNECTED:  using HTTP
SENDING:  GET /nic/update?system=dyndns&hostname=home&myip=90.194.239.32 HTTP/1.0
SENDING:   Host: updates.opendns.com
SENDING:   Authorization: Basic dHdpc3RlZHR3aWc6amFja3JhYmJpdA==
SENDING:   User-Agent: ddclient/3.7.3
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 302 Found

RECEIVE:  Date: Wed, 12 Nov 2008 19:34:36 GMT

RECEIVE:  Server: Apache/2.2.3 (Debian) PHP/5.2.0-8+etch11

RECEIVE:  X-Powered-By: PHP/5.2.0-8+etch11

RECEIVE:  Location: https://www.opendns.com/dashboard/ddns.php

RECEIVE:  Content-Length: 0

RECEIVE:  Connection: close

RECEIVE:  Content-Type: text/html; charset=UTF-8

RECEIVE:  

INFO:     setting IP address to 90.194.239.32 for aipoker.co.uk,houseofhawkins.com,spencerandwest.co.uk,www.aipoker.co.uk,www.houseofhawkins.com,www.spencerandwest.co.uk
UPDATE:   updating aipoker.co.uk,houseofhawkins.com,spencerandwest.co.uk,www.aipoker.co.uk,www.houseofhawkins.com,www.spencerandwest.co.uk
CONNECT:  dynamic.zoneedit.com
CONNECTED:  using HTTP
SENDING:  GET /auth/dynamic.html?host=aipoker.co.uk,houseofhawkins.com,spencerandwest.co.uk,www.aipoker.co.uk,www.houseofhawkins.com,www.spencerandwest.co.uk&dnsto=90.194.239.32 HTTP/1.0
SENDING:   Host: dynamic.zoneedit.com
SENDING:   Authorization: Basic amhhd2tpbnMxMjpqYWNrcmFiYml0
SENDING:   User-Agent: ddclient/3.7.3
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 401 Authorization Required

RECEIVE:  Date: Wed, 12 Nov 2008 19:34:43 GMT

RECEIVE:  Server: Apache

RECEIVE:  WWW-Authenticate: Basic realm="DNS Access"

RECEIVE:  Content-Length: 1541

RECEIVE:  Connection: close

RECEIVE:  Content-Type: text/html; charset=iso-8859-1

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:      

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:       

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  

RECEIVE:  <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

RECEIVE:  <html lang="en-US">

RECEIVE:  <head>

RECEIVE:  <title>Authentication Failed (ZoneEdit.com)</title>

RECEIVE:  

RECEIVE:  <BODY MARGINHEIGHT=0 MARGINWIDTH=0 MARGINTOP=0 MARGINLEFT=0 MARGINRIGHT=0 MARGINBOTTOM=0 LINK=#000000 VLINK=#770077>

RECEIVE:  <center><div align=center>

RECEIVE:  

RECEIVE:  <br>

RECEIVE:  

RECEIVE:  <table width=50% bgcolor=black><tr><td>

RECEIVE:  <table width=100% bgcolor=white><tr><td align=center>

RECEIVE:          <font face="arial, helvetica" size="-1"><b> </b></font>

RECEIVE:          <a href="http://www.zoneedit.com/">

RECEIVE:          <br>

RECEIVE:  

RECEIVE:          <img src="http://www.zoneedit.com/img/logo-idea1.jpg" border="0"></a>

RECEIVE:          <br>

RECEIVE:          <font face="arial, helvetica" size="-1"><b>... the newest way to control the internet</b></font>

RECEIVE:  

RECEIVE:          <p>

RECEIVE:          <font face="arial, helvetica" size="-1">

RECEIVE:  

RECEIVE:          <table width=90%><tr><td bgcolor="#eeeeee">

RECEIVE:          To subscribe to ZoneEdit.com, or to license the ZoneEdit.com technology, including web based real-time dns editing,

RECEIVE:          WebForward, and Starter Web Page, please contact sales@zoneedit.com / +1-847-461-1893

RECEIVE:          </td></tr></table>

RECEIVE:  

RECEIVE:          <p>

RECEIVE:  

RECEIVE:          <table width=90%><tr><td bgcolor="#eeeeee">

RECEIVE:          <a href="http://www.dotster.com/hosting">Web Hosting -- starting at $5.95 per month!  For more information, click here.</a>

RECEIVE:          </td></tr></table>

RECEIVE:  

RECEIVE:          </font>

RECEIVE:  

RECEIVE:          <br>

RECEIVE:  

RECEIVE:  </td></tr></table>

RECEIVE:  </td></tr></table>

RECEIVE:  

RECEIVE:  </div></center>

RECEIVE:  

RECEIVE:  </body>

RECEIVE:  

RECEIVE:  </html>

FAILED:   updating aipoker.co.uk,houseofhawkins.com,spencerandwest.co.uk,www.aipoker.co.uk,www.houseofhawkins.com,www.spencerandwest.co.uk: authorization failed (HTTP/1.1 401 Authorization Required
FAILED:    Date: Wed, 12 Nov 2008 19:34:43 GMT
FAILED:    Server: Apache
FAILED:    WWW-Authenticate: Basic realm="DNS Access"
FAILED:    Content-Length: 1541
FAILED:    Connection: close
FAILED:    Content-Type: text/html; charset=iso-8859-1
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:        
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:         
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    
FAILED:    <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
FAILED:    <html lang="en-US">
FAILED:    <head>
FAILED:    <title>Authentication Failed (ZoneEdit.com)</title>
FAILED:    
FAILED:    <BODY MARGINHEIGHT=0 MARGINWIDTH=0 MARGINTOP=0 MARGINLEFT=0 MARGINRIGHT=0 MARGINBOTTOM=0 LINK=#000000 VLINK=#770077>
FAILED:    <center><div align=center>
FAILED:    
FAILED:    <br>
FAILED:    
FAILED:    <table width=50% bgcolor=black><tr><td>
FAILED:    <table width=100% bgcolor=white><tr><td align=center>
FAILED:            <font face="arial, helvetica" size="-1"><b> </b></font>
FAILED:            <a href="http://www.zoneedit.com/">
FAILED:            <br>
FAILED:    
FAILED:            <img src="http://www.zoneedit.com/img/logo-idea1.jpg" border="0"></a>
FAILED:            <br>
FAILED:            <font face="arial, helvetica" size="-1"><b>... the newest way to control the internet</b></font>
FAILED:    
FAILED:            <p>
FAILED:            <font face="arial, helvetica" size="-1">
FAILED:    
FAILED:            <table width=90%><tr><td bgcolor="#eeeeee">
FAILED:            To subscribe to ZoneEdit.com, or to license the ZoneEdit.com technology, including web based real-time dns editing,
FAILED:            WebForward, and Starter Web Page, please contact sales@zoneedit.com / +1-847-461-1893
FAILED:            </td></tr></table>
FAILED:    
FAILED:            <p>
FAILED:    
FAILED:            <table width=90%><tr><td bgcolor="#eeeeee">
FAILED:            <a href="http://www.dotster.com/hosting">Web Hosting -- starting at $5.95 per month!  For more information, click here.</a>
FAILED:            </td></tr></table>
FAILED:    
FAILED:            </font>
FAILED:    
FAILED:            <br>
FAILED:    
FAILED:    </td></tr></table>
FAILED:    </td></tr></table>
FAILED:    
FAILED:    </div></center>
FAILED:    
FAILED:    </body>
FAILED:    
FAILED:    </html>
FAILED:    )
```

---

### Post by MJN on 2008-11-12
It looks like your ZoneEdit username and/or password are wrong. Are they?

Mathew

---

### Post by 081104jk on 2008-11-13
&#21487;&#25345;&#32493;&#21457;&#23637;&#65306;&#21271;&#20140;&#24066;&#20140;&#23458;&#32593;&#31185;&#25216;&#26377;&#38480;&#20844;&#21496;&#20174;[**&#32593;&#31449;&#20248;&#21270;**](http://www.jingke.org/)&#25216;&#26415;&#20248;&#21183;&#19978;,&#21306;&#21035;&#20110;&#20854;&#23427;&#26381;&#21153;&#21830;.&#29616;&#22312;&#22823;&#22810;&#25968;&#26381;&#21153;&#21830;&#29992;&#30340;&#26159;&#22806;&#37096;&#36830;&#25509;&#25163;&#27861;.&#21271;&#20140;&#24066;&#20140;&#23458;&#32593;&#31185;&#25216;&#26377;&#38480;&#20844;&#21496;&#21033;&#29992;&#25968;&#21315;&#20010;&#32593;&#31449;&#20316;&#20026;&#36164;&#28304;,&#20174;&#25216;&#26415;&#19978;&#31216;&#20026;&#20869;&#37096;&#36830;&#25509;,&#26159;&#29616;&#22312;&#26381;&#21153;&#21830;&#24456;&#23569;&#33021;&#20570;&#21040;&#30340;.        &#36136;&#37327;&#20445;&#35777;&#19982;&#21487;&#38752;&#24615;&#65306;&#21271;&#20140;&#24066;&#20140;&#23458;&#32593;&#31185;&#25216;&#26377;&#38480;&#20844;&#21496;[**google&#20248;&#21270;**](http://www.jingke.org/)&#24072;&#22312;SEO&#39046;&#22495;&#20973;&#30528;&#22810;&#24180;&#30340;&#25216;&#26415;&#32463;&#39564;&#21644;&#19987;&#19994;&#30340;[**google&#25490;&#21517;**](http://www.jingke.org/)&#35268;&#24459;&#30340;&#20102;&#35299;&#24050;&#22312;&#34892;&#19994;&#20869;&#26377;&#24456;&#39640;&#30340;&#30693;&#21517;&#24230;.       &#26381;&#21153;&#65306;&#26080;&#35770;&#26159;&#22312;&#22269;&#20869;&#36824;&#26159;&#22269;&#22806;&#20140;&#23458;&#32593;&#25216;&#26415;&#39038;&#38382;&#21487;&#38543;&#26102;&#25552;&#20379;&#26381;&#21153;&#12290;&#20140;&#23458;&#32593; &#30340;&#20840;&#29699;&#32593;&#32476;&#33021;&#30830;&#20445;&#21512;&#20316;&#20249;&#20276;&#30340;&#21033;&#30410;&#24471;&#21040;&#29305;&#21035;&#20851;&#27880; &#8212; &#22987;&#32456;&#25552;&#20379;&#26368;&#20339;&#30340;[**&#32593;&#31449;&#25512;&#24191;**](http://www.jingke.org/)&#35299;&#20915;&#26041;&#26696;&#21644;&#23454;&#29616;&#26368;&#32463;&#27982;&#23454;&#24800;&#30340;&#24212;&#29992;&#12290;&#26080;&#35770;&#26159;&#29616;&#22312;&#36824;&#26159;&#23558;&#26469;&#65292;&#26080;&#35770;&#23458;&#25143;&#36523;&#22312;&#20309;&#22788;&#65292;Dunkermotoren&#37117;&#23558;&#19968;&#22914;&#26082;&#24448;&#22320;&#20026;&#24744;&#25552;&#20379;&#20840;&#26041;&#20301;&#26381;&#21153;&#12290;&#20140;&#23458;&#32593;&#20973;&#20511;&#39640;&#36136;&#37327;&#30340;&#26381;&#21153;.&#25216;&#26415;&#20248;&#21183;&#65292;&#20225;&#19994;&#24744;&#22312;&#25105;&#20204;&#20844;&#21496;&#20570;&#20102;[**google&#20248;&#21270;**](http://www.jingke.org/)&#65292;&#21487;&#20197;&#20570;&#21040;&#19968;&#32593;&#25237;&#20837;&#65292;&#65288;&#24517;&#25253;GOOGLE&#65292;&#26032;&#28010;&#65292;SOSO&#19977;&#22823;&#25628;&#32034;&#24341;&#25806;&#22312;&#39318;&#39029;&#65289;&#21313;&#20108;&#32593;&#23459;&#20256;(&#20026;&#20225;&#19994;&#33410;&#30465;95%&#30340;&#36153;&#29992;)&#65306;&#25628;&#29392;&#65288;&#25628;&#29399;&#65289;&#12289;&#32593;&#26131;&#12289;&#38597;&#34382;&#65288;3721&#65289;&#12289;&#26032;&#28010;&#12289;GOOGLE&#12289;&#30334;&#24230;&#12289;&#20013;&#25628;&#12289;TOM&#12289;&#33150;&#35759;SOSO&#12289;&#20013;&#21326;&#25628;&#32034;&#65292;114Vnet,Msn&#31561;&#22269;&#20869;&#22269;&#22806;&#20854;&#20182;&#19978;&#21315;&#20010;&#25628;&#32034;&#24341;&#25806;&#26174;&#31034;&#12290; [IMG]http://www.jingke.org/img/hzhb.jpg[/IMG]

---

### Post by twistedtwig on 2008-11-13
Hi Mathew,

I have triple checked the username and tried the password with and without quotes around it. All without success.

---

### Post by twistedtwig on 2008-11-13
turns out that I had to reset my password.  But I was still able to log in with said password before I had reset it.  There was no hint of this in the error thought.

Take care

---

