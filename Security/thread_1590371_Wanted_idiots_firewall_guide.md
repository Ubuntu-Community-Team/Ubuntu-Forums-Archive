---
title: "Wanted idiots firewall guide"
date: 2010-10-07
forum: Security
---

### Post by chrisclay on 2010-10-07
Hi
I am running Ubunto server witch I am controlling remotely using Webmin and Vnc. What I am looking for is a simple guide on how to set up a firewall. The main use for the server is to act as a media server,but I also use it to download files and store files so I use a torrent application and samba to enable sharing with windows pc's

any help would be appreciated

---

### Post by sikander3786 on 2010-10-07
Simply, uncomplicated firewall.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by nevius on 2010-10-07
> **chrisclay said:**
> Hi
I am running Ubunto server witch I am controlling remotely using Webmin and Vnc. What I am looking for is a simple guide on how to set up a firewall. The main use for the server is to act as a media server,but I also use it to download files and store files so I use a torrent application and samba to enable sharing with windows pc's

any help would be appreciated


Remotely administering a server with VNC is a bad idea unless you do it [over SSH]("http://martybugs.net/smoothwall/puttyvnc.cgi"). There is a lot of good information and links in the Security sticky at the top of this forum:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by chrisclay on 2010-10-08
> **nevius said:**
> Remotely administering a server with VNC is a bad idea unless you do it [over SSH]("http://martybugs.net/smoothwall/puttyvnc.cgi"). There is a lot of good information and links in the Security sticky at the top of this forum:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
when i wrote that i was administering the server the server using Vnc i should have added that this is all done within the home network and not from outside the home

---

### Post by CharlesA on 2010-10-08
> **chrisclay said:**
> when i wrote that i was administering the server the server using Vnc i should have added that this is all done within the home network and not from outside the home

If that's the case, then it's fine. Just make sure you have a strong password regardless.

Personally I'd prefer something like [FreeNX]("http://www.nomachine.com/select-package.php?os=linux&id=1") over VNC, but that's just me.

I have found it to be better then VNC, and more secure since it uses SSH.

---

### Post by HermanAB on 2010-10-08
Howdy,

VNC is bad news in a home network, since it uses plug and pray to open up ports in home routers.  So if you want to be secure, stop the VNC server and learn how to use SSH instead.  SSH can do everything VNC does and much more. Ferinstance:

$ ssh -X -C -c blowfish user@server gnome-panel

Now you can go click happy.  (This also works using Cygwin on Windows).

---

### Post by CharlesA on 2010-10-08
Indeed. It's too easy to accidentally set it to "configure the network automatically" and have it accessible from the internet.

---

