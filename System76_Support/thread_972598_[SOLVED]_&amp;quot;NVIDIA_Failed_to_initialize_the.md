---
title: "[SOLVED] &amp;quot;NVIDIA Failed to initialize the NVIDIA kernal module!&amp;quot;"
date: 2008-11-05
forum: System76 Support
---

### Post by Cori on 2008-11-05
Hello all.  I just recently upgraded from 8.04 to 8.10, and like so many other folks, I'm getting the above error message.

I've tried changing the drivers (I have 173 and 177 available in Hardware Drivers), and I've tried the System76 driver (from [http://knowledge76.com/index.php/IntrepidUpgrade](http://knowledge76.com/index.php/IntrepidUpgrade)).  Still getting the error message.

I have a serp4.  Version 2.2.7 on the driver.  Any help is greatly appreciated!

---

### Post by Cori on 2008-11-05
PS:  When trying to add System76 repository as mentioned in [http://ph.ubuntuforums.com/showthread.php?t=962793](http://ph.ubuntuforums.com/showthread.php?t=962793), I'm getting the following error:
[INDENT]W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 176A5C84ED67C9ED[/INDENT] :confused:

---

### Post by Lee_Machine on 2008-11-05
I have found the Envy program to work better for me when installing the proprietary drivers.

[https://launchpad.net/envy](https://launchpad.net/envy)

---

### Post by Vadi on 2008-11-06
Please see [http://ubuntuforums.org/showthread.php?t=962793](http://ubuntuforums.org/showthread.php?t=962793) for the key error - they changed it.

In regards to nvidia, I'm not sure. Did you try disabling and enabling it in the hardware drivers?

Envy is great, but once you use it, you're stuck forever with it until a reinstall. Same with nvidia drivers from their website.

---

### Post by thomasaaron on 2008-11-06
We've run into problems with envy, primarily because if something gets hosed with nVidia, most of the standard fixes no longer seem to apply.

As the above poster said: go to System > Admin > Hardware Drivers and see if you can enable nVidia from there.

---

### Post by Cori on 2008-11-08
Vadi: Thanks for the info!  I was able to update the keys.

Thomasaaron:  Unfortunately, the 177 driver for NVIDIA is already active.  Any other ideas?  :(

---

### Post by Vadi on 2008-11-08
Try enabling the 173, and it that works, back to 177. Also make sure to reboot after each activation like it says (logging out and back in won't work.)

---

### Post by Cori on 2008-11-09
I've enabled 173 and it's still not working properly.  8.04 is looking better and better.  :)

---

### Post by Vadi on 2008-11-09
Well, ok, give Envy a try (you can find it in Add/Remove).

---

### Post by thomasaaron on 2008-11-10
When are you getting that error message? Is it only in the logs?

What happens when you enable 177 in System > Admin > Hardware Drivers? Are you getting error messages there?

Do you have desktop effects? (Because if you do, your nVidia is working.) Try Ctrl > Alt > Left Arrow and Ctrl > Alt > Right Arrow to find out.

---

### Post by Cori on 2008-11-10
Q: When are you getting that error message? Is it only in the logs?
A: I get the error message between the startup and the login page.

Q: What happens when you enable 177 in System > Admin > Hardware Drivers?  Are you getting error messages there?
A: No error messages until I reboot.

Q: Do you have desktop effects? (Because if you do, your nVidia is working.) Try Ctrl > Alt > Left Arrow and Ctrl > Alt > Right Arrow to find out.
A: Yes, I can flip between my two desktops.

---

### Post by thomasaaron on 2008-11-10
> Yes, I can flip between my two desktops.

Sorry, I wasn't clear on that one. 

Does it *slide* from desktop to desktop, or does it just instantaneously switch from desktop to desktop.

If it *slides*, desktop effects is enabled and nvidia is working correctly, and, consequently, the error message is probably nothing to worry about.

If it instantaneously switches, desktop effects is not enabled, and we still have a problem.

---

### Post by Cori on 2008-11-11
Thanks for the clarification, Thomasaaron.  The desktops do *not* slide, but they switch instantaneously.  
Back to the drawing board!

---

### Post by thomasaaron on 2008-11-11
OK. Let's try this:

#Back up your xorg.conf file
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#Re-create your xorg.conf file. Use all defaults.
sudo dpkg-reconfigure xserver-xorg

Now, go to System > Administration > Hardware Drivers and enable 177.

Reboot.

Fixed?

---

### Post by Cori on 2008-11-11
Not fixed yet.  Please let me know if you need any info from my system to help you out.

---

### Post by Vadi on 2008-11-11
As a last resort, you can always install nVidia drivers from their installer, which always fixes everything. One drawback is that you won't be able to upgrade it via the Update Manager anymore though.

---

### Post by thomasaaron on 2008-11-12
Whew! This one's a monster, huh?

What happened when you tried to enable 177? Did it seem to take?

Please post the output of this command:

```
cat /etc/X11/xorg.conf
```

---

### Post by Cori on 2008-11-12
The 177 driver did seem to "take" -- it went through the whole downloading and installing phase, and prompted me for a restart.  

Please see the attachment for the output.

Thanks again for dealing with my monsters!  :)

---

### Post by Vadi on 2008-11-13
Yeah, so you should be good... try enabling the desktop effects now?

---

### Post by thomasaaron on 2008-11-13
Try this: 

1. sudo gedit /etc/rc/local
-If there are any nvidia lines in there, comment them out
-Save and exit

2. sudo gedit /etc/udev/rules.d/90-modprobe.rules
- Add the following line *right above* the last line in the file.
RUN+="/sbin/modprobe nvidia"
- Save and Exit
- Reboot

Fixed?

---

### Post by Cori on 2008-11-13
I didn't see any files under "/etc/rc/local" but there was a "/etc/rc_**.**_local" so hopefully that's the one you wanted me to check out.  There was nothing in that file except a few comments and one line of code -- 0  exit.  Nothing about nVidia in there.

I ran the second command, restarted, and voila!  I have a normal resolution with sliding desktops again.  Thanks a million for saving my laptop and my office window from certain doom.  If you're ever in SE Michigan, I owe you lunch!

Thanks again!  :biggrin:

---

### Post by Vadi on 2008-11-13
Click on 'Thread Tools' and 'Mark Thread as Solved'.

Glad you guys got it =)

---

### Post by thomasaaron on 2008-11-14
Yes, I meant rc.local. Sorry about that.

Glad your up and running. I'll take you up on that lunch if I'm ever up that way. That part of the country is a little too cold for me this time of year, though.

Now, if you lived in Florida... :)

---

