---
title: "xrdp on ubuntu server"
date: 2016-04-22
forum: Server Platforms
---

### Post by ryan209 on 2016-04-22
[COLOR=#111111][FONT=Ubuntu]I have set up xrdp on my ubuntu server 15.10, with mate desktop environment and it all works fine and dandy. Except for when I enable UFW. I have the following ports allowed all tcp[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]2222 (ssh)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]3389 (what I believe is for xrdp)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]5910 (because xrdp kept trying to use that port, don't know if I need that open)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]now if I disable ufw, then login to the remote desktop, then close it, and re enable ufw, I can then re open the remote desktop. Once I reboot the server though I find myself in the same predicament.[/FONT][/COLOR]
[h=1]/etc/xrdp/xrdp.ini[/h][globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=high
channel_code=1
max_bpp=24

[xrdp1]
name=sesman-Xvnc
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=ask5910
[COLOR=#111111][FONT=Ubuntu]I have set the port to ask5910 although I would like to set it to just a specific port.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have searched everywhere, and all I can find is allow ssh and 3389/tcp through ufw, and I have done that. So what am I doing wrong? Is there anyway I can use xrdp as soon as my system boots without having to disable my firewall?[/FONT][/COLOR]

---

### Post by ryan209 on 2016-04-22
this may be a bit confusing, but say i restart the server have ufw enabled, and as soon as the servers running i open remote desktop on my pc.  so on the login it by default says 5910, and it errors on trying to connect, but if i do port -1 (that also fails) but then go back to port 5910 i can login... this doesnt make any sense to me.

i just want to be able to reboot my server, and remote login to a port defined without haveing to do the -1 (that fails) then back to the port i want.  Is this even possible?

---

### Post by QIII on 2016-04-22
Are you able to SSH into your server?

---

### Post by ryan209 on 2016-04-22
> **QIII said:**
> Are you able to SSH into your server?

yes, Im just having issues with the remote desktop

this was my install procedure as far as the remote desktop part (good thing i note everything down lol)

```
apt-get install xrdp mate-core mate-desktop-environment mate-notification-daemon
echo mate-session >~/.xsession

/etc/xrdp/xrdp.ini
  encrypt_level=high
[COLOR=#000000]  port=ask5910

[/COLOR]
ufw allow 3389/tcp
ufw allow ssh

```

it may not be clear as day what each step was just notes to help, but i installed it made the changes to xrdp.ini then allowed it through the firewall.

whether the firewall is enabled or not on a fresh reboot i have to fail with port -1 before i can login with port 5910 it just seems kind of off =/

---

### Post by ryan209 on 2016-04-22
heres what i have to do every time when i log into remote desktop for the first time

i can avoid this first error by doing -1 first and getting that error first
[IMG]http://i.imgur.com/s907vsy.png[/IMG]
[IMG]http://i.imgur.com/DcEo3S1.png[/IMG]

but this error i have to do or i cant get in
[IMG]http://i.imgur.com/o9SMMXB.png[/IMG][IMG]http://i.imgur.com/Sh8tU4P.png[/IMG]

and finally it lets me in
[IMG]http://i.imgur.com/Elfuzh7.png[/IMG][IMG]http://i.imgur.com/rVk7sBp.png[/IMG]


is there anyway i can avoid having to do the -1?

---

### Post by ryan209 on 2016-04-22
i may have found a fix... [http://ubuntuforums.org/showthread.php?t=1314336](http://ubuntuforums.org/showthread.php?t=1314336) i dont recall installing vnc but i have installed so much testing things out, im about ready to finalize.  so im going to do a fresh install and ill let you all know =)

seems to be working now this time i was assigned a different port and so i changed my xrdp.ini to:
```
[xrdp1]name=sesman-Xvnc
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=-1


[xrdp2]
name=Reconnect
lib=libvnc.so
ip=127.0.0.1
port=ask
username=ask
password=ask

```

so that way the default can assign my port then in the reconnect i can enter the port to continue the session

---

