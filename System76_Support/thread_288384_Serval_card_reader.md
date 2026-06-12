---
title: "Serval card reader"
date: 2006-10-29
forum: System76 Support
---

### Post by Kaloma on 2006-10-29
I just upgraded my Serval to Edgy this weekend; it went mostly smoothly.  There was some issue with samba, and a dangling symlink to "/samba".  I had to delete that symlink manually, then run "apt-get install -f" from the terminal, then complete the upgrade.  Other than that snag, however, it everything seemed fine.  Very happy with the latest versions of various software that I use.

Unfortunately, today I tried using the card reader, but it does not work.  I tried rebooting, played around with the pccardctl command, but the computer does not seem to recognize that there is a card in the slot.

Prior to the upgrade, the card reader worked, though there were a few quirks.  The very first time I used it, the card was automatically detected, and everything was perfect.  Thereafter, plugging the card in did not always work, I would sometimes need to restart in order to have the card recognized.  But I could always get it to work by restarting if not otherwise.

So, what I am trying to figure out is:
[list][*]Is the card reader defective, and has now died after being on the fritz?
[*]Is the hardware fine, but the software support has always been sketchy, and I just got lucky at the beginning?
[*]Is the Edgy upgrade responsible in some way for my total lack of functionality that I am now experiencing?
[/list]

I wish I had more info, but I don't know much about device drivers. Thanks in advance for your help.

-Matthew-

---

### Post by crichell on 2006-10-30
Hi Matthew - With the upgrade the modules that support the card reader may have not be autoloading.  I'll check on this and get back to you.

---

### Post by Kaloma on 2006-10-30
Thanks, Carl.  Do you happen to know the module name(s)?  I don't mind manually loading them for now.

The situation is that our old compact digital camera died, so we got a new one: a Canon Powershot A630.  Unfortunately, both my desktop (running Debian 'etch')and Serval seem to have trouble communicating with this camera via USB.  So I have been using the Serval's card reader to get the pictures and then transfer them to my desktop.  So as long as I can do that somehow, even via modprobe, I won't be too troubled.

The card is a 1GB high-speed SD flash card.

-Matthew-

---

### Post by crichell on 2006-10-30
I don't know yet - I'll work on it this evening and get back to you (have to load up a Serval w/ dapper and pull lsmod).

cheers, carl

---

### Post by Kaloma on 2006-11-02
Carl, I don't know whether you've been able to make any headway on this issue, or if you've found out which modules should be loaded, but I do have another thought I want to bring up.

I have noticed with the weather changing (getting dryer), that I often experience some static discharge when removing my laptop from its case (a Targus backpack).  Are you aware of any cases where this could cause hardware damage, like frying the card reader since the slot is open and has no cover?

-Matthew-

---

### Post by crichell on 2006-11-04
Hi Matthew - I doubt it's hardware related - I'm getting the same results.  I haven't had the opportunity to get to it but it's been on our list since you brought it up.  I'm confident in this one though - regressions like this can generally be fixed (we know the driver is available so we should be able to load it).  I'm going to be hanging at the Ubuntu Dev conference through this week but I'll tackle this one as soon as I'm back in Denver.

---

### Post by Kaloma on 2006-11-05
> **crichell said:**
> I'm going to be hanging at the Ubuntu Dev conference through this week but I'll tackle this one as soon as I'm back in Denver.
I am glad to hear that my issue is most likely software-related.  Many thanks.  Enjoy the conference!

-Matthew-

---

### Post by Kaloma on 2006-11-05
I just managed to download my photos from the camera via USB using the gphoto2 command-line utility.  I don't know why that works but gphotofs and applications that use libgphoto2 (like gtkam, gthumb, f-spot, etc.) do not work.

So, while I do still want to get my card reader working again, I don't mind waiting since it is no longer an obstacle for me.

-Matthew-

---

### Post by crichell on 2006-11-06
Matthew - What type of camera are you using?  Is this a camera others should avoid (is it a lack of support?)

---

### Post by Kaloma on 2006-11-08
The camera is a Canon PowerShot A630.  It is not explicitly listed as supported by gphoto, however the A610 and A620 models are, and it is a basic PTP camera.  I found little while searching the Web for similar issues that others may have had.

Like I said, the gphoto2 command-line utility works fine.  I suspect that there is a buggy part of libgphoto2 that is not used by gphoto2 but IS used by gphotofs and other fancier applications.

The problem is not a showstopper because there is a manual workaround.  I would not urge other Linux users to steer clear of the camera, because it is a nice one and I imagine that this small glitch will work itself out in future updates.

-Matthew-

---

### Post by crichell on 2006-11-08
> I imagine that this small glitch will work itself out in future updates.

your right - they generally do - Every camera we've tested has worked out of the box.

---

### Post by Kaloma on 2006-12-18
Although I haven't figured out the card reader issue, I do have the camera working via USB.

It appears that the camera isn't listed in the "rules" file for gphoto (perhaps because it is relatively new), even though it works fine with gphoto.  The reason I was able to communicate with it via the gphoto2 command in the shell is because I was running the command as root.  (Somehow I overlooked the significance of this and forgot to mention it previously.)

The file /etc/udev/rules.d/45-libgphoto2.rules contains a list of all known supported cameras and permissions for which users can access the same.  Because my camera wasn't listed, my user identity could not access it even though I belong to plugdev group.

As long as the camera supports the protocols used by libgphoto2, adding the camera is as easy as:
[LIST=1]
[*]Connect your camera to your box via USB.
[*]Run lsusb (as root) from a shell. This will list various details about your camera, including 'idVendor' and 'idProduct'.
[*]Edit the rules file mentioned above to add a new line for your camera.  You can simply duplicate another line and change the 'idVendor' and 'idProduct' to match your camera.  (Note that if lsusb says your 'idVendor' is 0x049a' then you can drop the prefix '0x' and only type "049a" in the rules file.)
[/LIST]

This worked for me; hopefully this will be useful to anyone who has a similar problem.

-Matthew-

---

