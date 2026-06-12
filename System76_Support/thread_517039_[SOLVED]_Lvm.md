---
title: "[SOLVED] Lvm?"
date: 2007-08-04
forum: System76 Support
---

### Post by palintheus on 2007-08-04
I was going to use [this]("http://www.psychocats.net/ubuntu/separatehome") guide to create a separate home on my new Darter, but it was written before/without LVM. Just wondering why you guys choose LVM, and if you know of a easy way to do this to give me ~10g / and the rest /home

---

### Post by palintheus on 2007-08-04
Since I changed quite a bit of things mainly from [this]("http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed") site I figured I would just reinstall and create the /home partition and then change things more cautiously so I tried just booting to a Ubuntu LiveCD and received this error:

/bin/sh: can't access tty; job control turned off

I have searched the forums and found [this]("ubuntuforums.org/showthread.php?t=421588") thread, which gets it past the errors and acts like it is booting and then I get a black screen, and from their I'm stuck.....](*,)

---

### Post by palintheus on 2007-08-05
OK I finally got a alternate cd to work which through the install process created a /boot, /home, /, and a swap. when it rebooted x would not start, so I ran 

```
sudo dpkg-reconfigure xserver-xorg
```

accepted most of the defaults used 'vga' as the driver, but nothing worked.

I ctrl-alt-f1 to a terminal, login and use another computer to go to the knowledge76 site about restoring my system figuring the driver _may_ run from the terminal, download it, install it and nothing.

So my search continued, found a thread suggesting intalling the latest intel driver, so I did, redid the dpkg-reconfigure and chose intel as my driver this time, it worked I got a very grainy and blurry desktop, but I was excited, I could now run the driver. 

I go system>adminstration>system76 driver.......and now its telling me that the system is not a system76 driver. I do not know how it recognizes one from another, but I am lost without a map at this point...

I also emailed [email]support@system76.com[/email], but didn't know which, if any, was checked after hours.

---

### Post by thomasaaron on 2007-08-06
Yeah, we've not released the System 76 driver yet that supports the new Darter.

Try this, go back to the restore instructions on the wiki.
Run the wget and dpkg commands again. But instead of using...

wget [http://planet76.com/repositories/system76-driver-2.0.5.deb](http://planet76.com/repositories/system76-driver-2.0.5.deb)
sudo dpkg -i system76-driver-2.0.5.deb

use

wget [http://planet76.com/repositories/system76-driver-2.0.5.deb.1](http://planet76.com/repositories/system76-driver-2.0.5.deb.1)
sudo dpkg -i system76-driver-2.0.5.deb.1

---

### Post by palintheus on 2007-08-06
It gives me a error 404: Not found. I typed [http://planet76.com/repositories/](http://planet76.com/repositories/) into my broswer and system76-driver-2.0.5.deb.1 is not listed.

---

### Post by thomasaaron on 2007-08-06
Try...

2.0.6.deb

---

### Post by palintheus on 2007-08-06
Same error...

---

### Post by thomasaaron on 2007-08-06
OK. Shoot me an email at support[at]system76[dot]com.
I'll email it to you.

Best,
Tom

---

### Post by palintheus on 2007-08-06
I've sent an email over the weekend about this issue, so do I need to send a new one or will you reply to the one I sent?

---

### Post by thomasaaron on 2007-08-06
I saw your email. I sent you the driver. Did you get it?

---

### Post by palintheus on 2007-08-06
Yes I received it, and it is working now.

---

### Post by thomasaaron on 2007-08-06
Schweeeeeet.

---

### Post by palintheus on 2007-08-06
Thats what I said after hosing my new laptop 1 day after receiving it.

---

### Post by thomasaaron on 2007-08-07
Just so you know, you now hold the System 76 record for rapid-hosing.
Could you send us a picture to hang up in our hall of fame? :guitar:

Just kidding. You're not the first, and I'm sure you'll not be the last. That's the beauty of linux. You do what you want, you learn from mistakes, and re-imaging is free and easy.

I have a question though. Is your CD-drive working OK? Please check and let me know. There is a patch for it, but I'm not sure if it is in the driver I sent you.
If it causes an icon to appear on your Desktop when you insert a CD, the patch is in place and all is well.

Best,
Tom

---

### Post by palintheus on 2007-08-07
Nope, it spins up, but doesn't mount the CD/DVD. When I click on the CD-ROM 1 in nautilus it says unable to mound the selected volume and when I click more details it says "mount: special device /dev/hda does not exist.

Also I noticed something loose bouncing around, for lack of a better word, so I took of the bottom and noticed that one end of the WiFi antenna was not connected to anything and had a plastic cover on it, don't know if it is supposed to be connected, but it could have been secured better.

---

### Post by thomasaaron on 2007-08-07
You should have two wires going to your wireless card. The one with the plastic cover is supposed to be unconnected.

I just emailed you the commands to get the drive going. I didn't want to post them here, as they will be coming out i the System 76 driver any day now.

---

### Post by palintheus on 2007-08-07
Yeah, I figured it was supposed to be unconnected, but it was just loose in the case and would make noises when moving, which really isn't something you want to hear in any electronic.

Thanks, I'll check my email.

---

