---
title: "[SOLVED] airsnort problems"
date: 2008-09-29
forum: Security
---

### Post by oneadvent on 2008-09-29
I was trying to test my own wireless device, and I am connected to it now, with it unsecured, I'm thinking that could be a problem with airsnort, but not the first one:

```
oneadvent@jwelch-laptop:~$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not supported.

```
when i try the first command on this guide page: 
[http://wirelessdefence.org/Contents/AirsnortMain.htm](http://wirelessdefence.org/Contents/AirsnortMain.htm)

What does that mean? I tried to just put in airsnort and hit run with no success.

Any help?

---

### Post by cariboo on 2008-09-29
First make sure your device is supported by airsnort and second you can't use airsnort to sniff your key if you are connected to the network. To check your network you will have to have a second wireless  device connected to your network.

Jim

---

### Post by oneadvent on 2008-09-29
Okay, I did find that it always comes up with those errors first and then if I "ctrl-c" it and do it again it works...

How do i know if my wireless device is supported?

---

### Post by binbash on 2008-09-29
you need patched drivers just like aircrack-ng.Go and check aircrack-ng's website ;)

---

### Post by oneadvent on 2008-09-30
Wow, I looked at that page, and I am MORE lost. Is there a good guide that actually works?

Thanks.

---

### Post by Titan8990 on 2008-09-30
Check on the Backtrack forums. Backtrack is all about penetration testing like you are doing.

Here is a link to their tutorials section: [http://forums.remote-exploit.org/forumdisplay.php?f=19](http://forums.remote-exploit.org/forumdisplay.php?f=19)

---

### Post by oneadvent on 2008-09-30
Wow that is a great site, with so much information, and it will take me a while to go over it all.

I'll mark this thread as solved as it has gone as far as is expected in ubuntuforums.org.

Thanks guys!

---

