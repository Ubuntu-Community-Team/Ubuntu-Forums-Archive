---
title: "Is it possible to run an FTP server off the live CD?"
date: 2006-09-29
forum: Server Platforms
---

### Post by K.Mandla on 2006-09-29
I have a busted laptop with no hard drive that will boot the Edgy live CD, and I was wondering if it is possible to create a small FTP server to transfer files between me and my brother across the state. That's all needs to do -- nothing fancy.

I can install vsftpd and work port forwarding to get a very simple setup in place. I guess my idea was that the files (which aren't big) would exist in the machine's live memory and could me moved off via USB stick. 

With the low power draw of the laptop (60W), I can afford to just leave it plugged in. Battery power is about 2-3 hours at minimal use, so I could weather most ... weather. :rolleyes: 

Is this practical? Or maybe it's a dumb idea. :-k

---

### Post by echo $USER on 2006-09-29
Yeah, it will work.

---

### Post by K.Mandla on 2006-10-01
Just for the record, it works. (I knew it all along ... 8) )

It's a bit of a trick to configure vsftpd (it was for me -- I wanted local user access and no anonymous logins, but that's just me) and I ended up saving configuration files to a USB drive in case I decided to reboot.

But it can be done, and it works fine.

The downside is that there's very little space to actually work with. The live CD seems to grab a percentage of the system memory, rather than a set amount. I need to figure out how to free that up. But otherwise, it's possible. ...

---

