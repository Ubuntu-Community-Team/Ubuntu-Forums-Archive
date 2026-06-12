---
title: "SSLH Service Not Starting on Boot"
date: 2010-06-27
forum: Server Platforms
---

### Post by sparks13 on 2010-06-27
I am trying to run SSH and HTTPS both on Port 443 on an Ubuntu server. I found SSLH  which seems to do the trick. My only problem is getting it to start on system boot. Supposedly, it is already setup to do so. A "sudo update-rc.d sslh defaults" says it is already setup. However, rebooting results in it not starting until I start it manually with a good ol' "sudo /etc/init.d/sslh start" command. I have tried using update-rc.d to remove it and add it again. This did not work either. I was not able to find anything in the logs, but that being said, I am not exactly sure which log file would hold this kind of information. Any help would be greatly appreciated.

---

### Post by windependence on 2010-06-28
Simply add your startup command to the end of your /etc/rc.local.

-Tim

---

### Post by sparks13 on 2010-06-28
I haven't had a chance to look at this yet as I am still at work. However, why would I need to add it to /etc/rc.local?? Isn't that for starting regular scripts without having to go through the effort of setting it up to run through init.d?? This is already setup to go through init.d (with some trouble-shooting). Something like Apache or a regular SSH daemon do not go through this approach. Is this just your quick fix?

Also, is it /etc/rc.local or /etc/init.d/local in Ubuntu?? I got this notion from here: [https://help.ubuntu.com/community/RcLocalHowto]("https://help.ubuntu.com/community/RcLocalHowto")

---

### Post by sparks13 on 2010-06-28
It turns out the vm I was working on was still on Karmic. I had updated packages which I thought would take care of any bugs related to init.d since they have all been listed as fixed. I did a release upgrade to Lucid and the problem went away.

---

