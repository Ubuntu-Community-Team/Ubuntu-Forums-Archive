---
title: "Restarted Server and now only able to SSH"
date: 2008-10-28
forum: Security
---

### Post by craigp on 2008-10-28
I'm running ubuntu 8.04 desktop on my server and had SSH and remote desktop and everything all working. i restarted it after doing a kernel update and now i can only SSH into it. It doesnt even prompt me for a username and password for VNC. Nor does it respond to telnet on port 5900 from local machine when i am in SSH. So obviously the service is not running. How can i turn on the remote desktop that comes with the OS back on? i turned it on before with the gui.  Also the server is a ways away so i cant just go over and walk up to it.

Cheers,
Craig

---

### Post by Fire_Chief on 2008-10-28
What happens when you try to start the VNC service from your SSH session?```
sudo /etc/init.d/vnc start
```Of course your VNC service name may be different.
Also, do you see any errors in the messages log?```
tail -n 100 /var/log/messages
```

Cheers!

---

### Post by cariboo on 2008-10-28
If you are using the default remote desktop server, it doesn't start on reboot by default run:

```
vino=preferences
```

at the prompt.

Jim

---

### Post by craigp on 2008-10-28
Thanks for the quick reply but i just got:

sudo: /etc/init.d/vnc: command not found

ls /etc/init.d/

gives this:

services were edited out

---

### Post by craigp on 2008-10-28
> **cariboo907 said:**
> If you are using the default remote desktop server, it doesn't start on reboot by default run:

```
vino=preferences
```

at the prompt.

Jim


it just moved down to the next line with no errors on that and nothing worked.

i also ran nmap localhost and it confirmed the service is not running

---

### Post by cdenley on 2008-10-28
The "service" runs during the user's GUI session. In other words, you have to login locally before you can login remotely. If your server is sitting at a graphical login, you can use x11vnc to connect to the X session, but it gets a little tricky with permissions. I would just stick with your shell using ssh. The "remote desktop" feature (or even a desktop environment) isn't meant for servers.

---

### Post by Fire_Chief on 2008-10-28
I don't see a VNC service installed on the system. Let's install vino like cariboo907 suggested. ```
sudo apt-get install vino
vino-preferences
/usr/lib/vino/vino-server &

```Now you should be able to connect to your server with a VNC client. Once connect, you may want to set a password for your VNC server through the *System -> Preferences -> Remote Desktop* control panel.

Cheers!

---

### Post by craigp on 2008-10-28
> **Fire_Chief said:**
> I don't see a VNC service installed on the system. Let's install vino like cariboo907 suggested. ```
sudo apt-get install vino
vino-preferences
/usr/lib/vino/vino-server &

```Now you should be able to connect to your server with a VNC client. Once connect, you may want to set a password for your VNC server through the *System -> Preferences -> Remote Desktop* control panel.

Cheers!

if i go:
sudo apt-get install vino

i get "vino is already the newest version"

then if i go vino-preferences it says "Gtk-WARNING **: cannot open display:"

and the service is still not running

---

### Post by craigp on 2008-10-28
> **cdenley said:**
> The "service" runs during the user's GUI session. In other words, you have to login locally before you can login remotely. If your server is sitting at a graphical login, you can use x11vnc to connect to the X session, but it gets a little tricky with permissions. I would just stick with your shell using ssh. The "remote desktop" feature (or even a desktop environment) isn't meant for servers.

i want the desktop environment temoprarily and only when i need it. so once i finish configuring i will turn it off and only turn it back on when i want to but i need it for things like configuring the firewall that it is connected to etc as there is no WAN access only DMZ access for configuration on the firewall

---

### Post by cdenley on 2008-10-28
> **craigp said:**
> i want the desktop environment temoprarily and only when i need it. so once i finish configuring i will turn it off and only turn it back on when i want to but i need it for things like configuring the firewall that it is connected to etc as there is no WAN access only DMZ access for configuration on the firewall

[http://ubuntuforums.org/showthread.php?t=656129](http://ubuntuforums.org/showthread.php?t=656129)

---

### Post by craigp on 2008-10-28
> **cdenley said:**
> [http://ubuntuforums.org/showthread.php?t=656129](http://ubuntuforums.org/showthread.php?t=656129)

awesome that worked.. thanks for the quick reply everyone

---

### Post by 080801jk on 2008-10-30
&#20197;&#25968;&#23383;&#32534;&#30721;&#65292;&#21152;&#23494;&#25216;&#26415;[**ic&#21345;&#35835;&#21345;&#22120;**](http://www.jcx.com.cn/)&#38450;&#30423;&#20081;&#24207;&#25216;&#26415;&#20026;&#26680;&#24515;&#30340;&#23494;&#30721;&#38190;&#30424;&#20135;&#21697;&#38142;&#65307;2&#12289; &#20197;&#36719;&#65288;&#30828;[**&#21483;&#21495;&#26426;**](http://www.jcx.com.cn/job.asp)&#35299;&#30721;&#30340;&#30913;&#35760;&#24405;&#25216;&#26415;&#20026;&#26680;&#24515;&#30340;&#30913;&#26465;&#65288;&#21345;&#65289;&#35782;&#21035;&#25216;&#26415;&#20135;&#21697;&#38142;[**&#25490;&#38431;&#26426;**](http://www.jcx.com.cn/job.asp)3&#12289; &#20197;&#25351;&#32441;&#65288;&#29983;&#29289;&#65289;&#25216;&#26415;[**&#21462;&#21495;&#26426;**](http://www.jcx.com.cn/job.asp)ic&#21345;&#25216;&#26415;&#12289;usbKEY&#30340;&#30828;&#20214;&#25216;&#26415;&#19982;&#32593;&#32476;&#36890;&#35759;&#30340;&#36719;&#20214;&#25216;&#26415;&#20026;&#26680;&#24515;&#30340;&#33268;[**&#21047;&#21345;&#22120;**](http://www.jcx.com.cn/job.asp)&#21147;&#20110;&#26588;&#21592;&#23433;&#20840;&#38450;&#33539;&#30340;&#36523;&#20221;&#35748;&#35777;&#31995;&#32479;&#20135;&#21697;&#38142;

---

