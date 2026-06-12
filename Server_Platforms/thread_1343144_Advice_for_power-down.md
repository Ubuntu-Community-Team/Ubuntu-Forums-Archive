---
title: "Advice for power-down"
date: 2009-12-01
forum: Server Platforms
---

### Post by Muttley99 on 2009-12-01
I'm using Ubuntu-Server 9.10 as a NAS.

Can someone advise me the best way to power down this so it's in a waiting state for FTP, Samba & NFS calls. It's using 21w at idle and 26w at load. I'd like to power it down to use around 5w but leave it responsive enough to serve as required.
I'm aware that I could use WOL and WOUSB but I'm guessing I'd have to power down the NAS fully for this? 

My motherboard Intel D945SEJT & Arm 270.

---

### Post by Vegan on 2009-12-01
ACPI throttles the CPU down to a low power state and Linux supports it natively.

Ignore the problem, Linux is well suited to sleeping servers.

---

### Post by Muttley99 on 2009-12-01
I've just tried pm-tools to drop it to suspend - NAS is using 3w! :D

Sending a magic-packet wakes the server in seconds! :D

My main problem now is as the NAS moves to suspend my Kubuntu client freezes as the fstab mounted NFS shares become unavailable. I've added intr to the options for the stanza and still the same. Any ideas are welcome!

---

### Post by Vegan on 2009-12-01
Wake on LAN is another old school technology. Its also intrinsic.

---

### Post by fkjensen on 2009-12-02
Have you figured a way to suspend automatically, when the server is not being used?
 
I have seen a lot of requests for this (including my own: [http://ubuntuforums.org/showthread.php?t=1335400](http://ubuntuforums.org/showthread.php?t=1335400) ;)), but have not found a solution yet.
 
Also, waking up the server by normal access (e.g. samba from a windows computer) instead of manually sending a WOL, would be cool, but I am afraid that's not possible...?
 
Well, let my know, if you find any solutions for these problems.
 
~Frank

---

### Post by Muttley99 on 2009-12-03
Frank,

My NAS suspends and wakes perfectly! If you want to do it automatically, You could get your computer to send a WOL at startup through the KDE autostart in Advanced-System settings. I'd be surprised if Gnome doesn't have something similar! (i've found a windows wol client also)  After installing PM-tools + ethtool a wake would be;

[HTML]wakeonlan (mac address)[/HTML]

You should be able to drop this in a script and run it on startup as above.

do the same for shutdown; except;

[HTML]pm-tools suspend[/HTML] (on the server)

---

### Post by fkjensen on 2009-12-03
No, I was looking for a way to suspend *automatically*, i.e. when the server has not been access (via samba, dlna, squeezebox etc.) for e.g. 30 min.
 
And waking up should also be without *manually* sending a WOL and only happen when needed, i.e. when I need to access my files via samba, or show pictures via dlna.
 
~Frank

---

