---
title: "Installing from USB - getting an erorr about not being able to mount CD Rom"
date: 2010-07-24
forum: Server Platforms
---

### Post by Rock` on 2010-07-24
I have a Poweredge that does NOT have a CD-Rom drive. No biggie, I thought, I could just boot off and install from USB. I look up instructions, download the ISO, use UNETBootIn [and the USB Installer on Ubuntu's website] and have issues with loading from the USB stick [tried 2 separate usb sticks].

The error is "there was a problem reading data from the cd-rom..."

This happens after I set my keyboard to USA.

Thoughts?

---

### Post by C.S.Cameron on 2010-07-24
Check the MD5SUM of your downloaded iso.

---

### Post by Rock` on 2010-07-25
I re-downloaded the ISO and still getting this issue.

---

### Post by Uniqueone on 2010-07-26
Hi Rock,

i just followed the guide for a usb installation and got a similar problem however i was able to solve it, perhaps you are having the same issue.

I found that the file "fs-secondary-modules-2.6.32-21-generic-di_2.6.32-21.32_amd64.ude" should actually be named "fs-secondary-modules-2.6.32-21-generic-di_2.6.32-21.32_amd64.udeb"

once you have followed the guide and extracted the files to the usb you can find this file in the "\pool\main\l\linux" directory.

i was able to determine this by droping to shell after the install failed and checking the contents of syslog.

Hope this helps.

---

### Post by Rock` on 2010-07-26
This worked! Thanks Uniqueone, such a huge oversight!

---

### Post by TheFuturian on 2010-08-25
> **Uniqueone said:**
> Hi Rock,

i just followed the guide for a usb installation and got a similar problem however i was able to solve it, perhaps you are having the same issue.

I found that the file "fs-secondary-modules-2.6.32-21-generic-di_2.6.32-21.32_amd64.ude" should actually be named "fs-secondary-modules-2.6.32-21-generic-di_2.6.32-21.32_amd64.udeb"

once you have followed the guide and extracted the files to the usb you can find this file in the "\pool\main\l\linux" directory.

i was able to determine this by droping to shell after the install failed and checking the contents of syslog.

Hope this helps.

I am definitely going to be giving this a try! :-D 8)

---

### Post by JayG30 on 2010-12-10
> **Uniqueone said:**
> Hi Rock,

i just followed the guide for a usb installation and got a similar problem however i was able to solve it, perhaps you are having the same issue.

I found that the file "fs-secondary-modules-2.6.32-21-generic-di_2.6.32-21.32_amd64.ude" should actually be named "fs-secondary-modules-2.6.32-21-generic-di_2.6.32-21.32_amd64.udeb"

once you have followed the guide and extracted the files to the usb you can find this file in the "\pool\main\l\linux" directory.

i was able to determine this by droping to shell after the install failed and checking the contents of syslog.

Hope this helps.

Thank you so much! I could not for the life of me figure out what was wrong. I tried 10.04 and 10.10 server amd64, multiple times downloaded, and both uNetbootin and universal USB installer. It would just fail. Renaming the file (slightly different numbering in 10.10) solved the problem!

Why is this STILL a problem though? Shouldn't they fix this or something?

---

### Post by PLAY3ER on 2011-03-03
Hey Guys, 

Sorry to bring this post up again, but this needs to be fixed. I just recived this error while trying to install Ubuntu Server from USB and changed the file name in the pool folder and it worked, but I nor others should have to do this.

PS: Thanks for the help :)

---

### Post by IceKold0 on 2012-09-10
This worked a treat.

Simply use any of the USB installers to put the ISO onto the USB, once the USB is created rename the file as mentioned in the solution and then boot from the USB... sorted.

:guitar:

---

### Post by sisco311 on 2012-09-10
[[img]http://ompldr.org/tYzBtcQ[/img]](http://ompldr.org/vYzBtcQ)

Thread closed.

---

