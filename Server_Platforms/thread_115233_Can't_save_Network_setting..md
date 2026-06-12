---
title: "Can't save Network setting."
date: 2006-01-10
forum: Server Platforms
---

### Post by irv on 2006-01-10
I have a problem that just croped up. I am running three computers on a network and all are running Ubuntu 5.10, all was working except I was having trouble with ssh to one box, but I found the problem I had a print server on my network with the same IP address. (I fixed that problem), and now can get to that box from one of the other computers, but not from the third one. I need to change my network setting on that one to get it to work. This is where my problem came in. When I go to System>Administration>Network and make changes it will not save them. When I click on the "OK" button it give me a busy icon on my mouse pointer and never goes away. I tried rebooting, but that didn't help. Is there a file I could manually edit to fix this problem? or is there another way to fix it? I can change my hosts file which I tried but this didn't help either. Not sure what to try next? :confused:

---

### Post by greenway on 2006-01-10
I remember the graphical frontend for networking being quite buggy in 5.04 and it's not all that much better in Breezy (at least for me it isn't). Had a lot of trouble configuting network settings using the frontend...

You could edit the network interfaces file manually: sudo gedit /etc/network/interfaces This way you will be sure that the right settings are being saved.

-mattijs

---

### Post by irv on 2006-01-10
[QUOTE=greenway]I remember the graphical frontend for networking being quite buggy in 5.04 and it's not all that much better in Breezy (at least for me it isn't). Had a lot of trouble configuting network settings using the frontend...

You could edit the network interfaces file manually: sudo gedit /etc/network/interfaces This way you will be sure that the right settings are being saved.

-mattijs[/QUOTE]
Thank greenway, I am at work now, but when I get home I will give this a try. and thank again.

---

### Post by greenway on 2006-01-10
No pros! Goodluck

---

