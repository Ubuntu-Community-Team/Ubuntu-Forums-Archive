---
title: "Webcam in Amsn in Feisty just worked, w00t!?"
date: 2007-04-06
forum: The Cafe
---

### Post by HumanAnarchist on 2007-04-06
This is a good sign, go Feisty Fawn !


-ha-

---

### Post by SishGupta on 2007-04-07
Yup! same, my logitech quickcam finally "just works" in feisty.
The drivers are built right into the kernel apparently

---

### Post by wishyjr on 2007-04-07
thats cool!

---

### Post by FoolsGold on 2007-04-07
> **SishGupta said:**
> Yup! same, my logitech quickcam finally "just works" in feisty.
The drivers are built right into the kernel apparently
Absolutely the same story here.

---

### Post by %hMa@?b&lt;C on 2007-04-07
doesnt quite work for me, but hey, I have a hacked one time use camera as my webcam, what should I expect? :lolflag:

---

### Post by migla on 2007-04-07
> **jeffc313 said:**
> doesnt quite work for me, but hey, I have a hacked one time use camera as my webcam, what should I expect? :lolflag:

Maybe your camera worked, but you weren't watching the messenger app, and being a one time use camera, it won't work anymore? ;)

---

### Post by %hMa@?b&lt;C on 2007-04-07
> **migla said:**
> Maybe your camera worked, but you weren't watching the messenger app, and being a one time use camera, it won't work anymore? ;)

hacked for reusable. lol

---

### Post by Oblong_Cheese on 2007-04-21
Fiesty detects my webcam (Logitech Quickcam IM), loads the appropriate driver and creates the /dev/video0 device, yet aMSN tells me there are no appropriate devices installed when I try to configure the webcam.

The "configure webcam" dialogue says "Please connect first", but tells me the webcam extension is loaded and the capture extension -capture- is loaded.

Any ideas?

---

### Post by HumanAnarchist on 2007-04-21
I have had some troubles with loading the webcam in amsn, if some a flash program has used the cam, but nothing else. Check the amsn forums [http://www.amsn-project.net/forums/](http://www.amsn-project.net/forums/) maybe you can find more luck there :) 

Here's some info about my cam:

```
root@cartman:~# lsusb 
Bus 005 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro

```

this happens when I plug the camera in:

```

root@cartman:~# dmesg
[392563.461097] usb 5-1: USB disconnect, address 2
[392619.477805] usb 4-2.3: new full speed USB device using ehci_hcd and address 6
[392619.575124] usb 4-2.3: configuration #1 chosen from 1 choice
[392619.575317] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 

```

-ha-

---

### Post by Oblong_Cheese on 2007-04-21
I think I may have narrowed the scope of the issue. It appears to be some kind of permissions / user / groups problem; the user account that I setup for myself during the installation is able to access and use the camera just fine in aMSN, but the second user account I created for my dad is apparently unable to.

I've added my dad's user account to the video group using gpasswd, but that hasn't solved the problem. No doubt the security systems in place behind Fiesty are far more complicated and in-depth than my knowledge.

Any pointers anyone?

*Edit*: Well it's definitely a permissions problem. I can use gqcam to view the webcam stream, but only if I prefix the command with sudo. Otherwise it says "/dev/video0 permission denied".

The video device:
```

wayne@wayne:~$ ls -lh /dev/ | grep video0
crw-rw---- 1 root video    81,   0 2007-04-22 10:08 video0

```

rw permissions for group, group video, as it should be

```

wayne@wayne:~$ cat /etc/group | grep vid
video:x:44:owen,wayne

```

And both user accounts (owen, the account created at installation) and my dads (wayne) are in the video group.

Searching my brain I can't think of anything else I would need to do to give my dad's account full 'access' to the video group. What have I missed?

---

### Post by HumanAnarchist on 2007-04-21
I'm not sure if this is the "correct" ubuntu way to do it, but it works for me. 

It's under the philosophy that everything in Linux is a file :)

```

sudo vim /etc/group

```

and add your dad's account to those groups that you also are in, except those obviously your dad should not be in :) 

-ha-

---

### Post by HumanAnarchist on 2007-04-21
Video group should be enough, but obviosly it isn't... could try with some other groups like audio, don't know if webcam need to use the audio group as well. Just a wild guess. I'm clueless now, sorry

-ha-

---

### Post by Marsan on 2007-04-22
Worked out of the box here too on my logitech quickcam! It doesent work properly with the small resolution though in aMsn.

my cam:

Bus 002 Device 004: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

---

### Post by Cyfr on 2007-04-22
My quickcam zoom worked right away and so did my built in onboard one in my sony laptop!!

But the onboard one is awfull quality I dont think it was that bad in windows :p

---

