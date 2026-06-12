---
title: "XP computer breaks internet connection"
date: 2008-02-08
forum: Windows
---

### Post by nvteighen on 2008-02-08
Hi there!
I'll describe the situation: we've got two XP computers and my Ubuntu PC connected to an encrypted wireless network; ocassionally one Vista computer is also added. Anything works fine until one specific XP (Media Center; the other one is Professional) tries to connect: it fails and then no computer can access the internet until the router is turned off and on again.

I've revised Firestarter log at my Ubuntu and see a blocked connection at port 53 (DNS) from 198.162.1.1 (the router). At the XP Media Center I could open a webpage only once through Firefox, but then connection was lost.

If I try to reconnect without restarting the router, it asks for the WEP key, but it refuses it. The strangest is that this last behaivor only occurs at my Ubuntu; the Windows computers just fail to connect and don't even ask for the key.

So, is there anyone which has any idea of what's happening or at least what diagnostic tools I can find to find this out?

Thanks!

---

### Post by DrMega on 2008-02-08
Windows XP Media Centre Edition was what finally pushed me to switch to Linux.

---

### Post by dca on 2008-02-08
Hmmm, is the media center XP machine close enough to your AP/router to just connect an ethernet cable?

---

### Post by dca on 2008-02-08
...you know, I don't know much about the MC vers of XP besides the fact that they added that crazy MC app to take the place of MP...  Is a DNS service or DHCP service running on it?  IOW, the MC was designed to be a stand-alone system that can receive T signals, act as a TiVO/DVR, and have other systems access its services...

---

### Post by nvteighen on 2008-02-09
There's no way to connect the MC with an ethernet cable... I'll check out if there's a DNS or DHCP service running on it, but I doubt it, unless some kind of malware has infected it.

---

### Post by hhhhhx on 2008-02-09
have you tried [linuxMCE]("http://video.google.com/videoplay?docid=2176025602905109829")?

---

