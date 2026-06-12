---
title: "Saned + SaneTwain"
date: 2008-02-24
forum: Server Platforms
---

### Post by SumnerBoy on 2008-02-24
Anybody had much success using this? I have installed sane and sane-utils and can see my scanner (USB) when running scanimage -L.

I have followed the instructions here [http://www.linux.com/articles/57798](http://www.linux.com/articles/57798) to add the sane-port service and dameon but when I run the Windows SaneTwain application it can't connect to the server.

The message I get is 'Error establishing connection to host'. Anyone got any ideas about this?

Thanks in advance.
Ben

PS - the scanner is a Canon MP530 all-in-one. I have successfully configured the printer for printing from Windows via Samba.

---

### Post by SumnerBoy on 2008-02-27
bump?

---

### Post by SumnerBoy on 2008-03-25
This turned out to be a permissions problem. The saned xinetd service was configured with the saned:scanner user and group. However the only way I could get the scanner to be accessible was to make the user and group root:scanner.

This is far from ideal (I think) as it is not typically a good idea to give external services root privileges - in case you hadn't guessed I am new to Linux!

So I was wondering if anyone had any ideas why the saned:scanner user and group wasn't working. Is it something to do with the privileges for the usb bus I am using? Any other ideas? I am a little lost here...

---

### Post by apos on 2008-04-06
Hi there,
I could only give you the hint reading additionally the german HowTo I wrote last weak here: [http://wiki.ubuntuusers.de/Baustelle/SANE#head-67833153b78803a6d7ecc87cb2fd689b30111195](http://wiki.ubuntuusers.de/Baustelle/SANE#head-67833153b78803a6d7ecc87cb2fd689b30111195)
 The artcle will move within a few days into to official german wiki.

There is a quick setup for the sane daemon using ubuntu that works for Gutsy/7.10. and above.

Generelly:
- Use *inetd* instead of *xinetd.*
- Don't forget to add the *saned* to the group *scanner* with 
```
sudo adduser saned scanner
```
- Don't change any settings on on permissions of devices or the saned binary at all
- If you are running a firewall, the SANE port 6566 has to be open
- You can try to enable the */etc/sane.d/net.conf* for *localhost* on the scanserver for testing purpose (if the *net* backend is working in general)
- You have to explicitly give permission for each client that wants to have access to the server - */etc/sane.d/saned.conf*


Probably this helps.
Axel

---

### Post by SumnerBoy on 2008-04-07
Thanks Axel - I just tried reverting back to saned:scanner in my xinetd configuration and everything seems to be working (after restarting xinetd). I wonder if my initial problem was something to do with the USB issues I was having previously, and have now solved.

I appreciate your efforts to help out though!

---

