---
title: "Daru1 Ibex Upgrade Issues"
date: 2008-12-13
forum: System76 Support
---

### Post by PanopticChaos on 2008-12-13
Ok, so I pulled the trigger and upgraded to Ibex yesterday - the upgrade seemed to go smoothly but since then...

Wireless doesn't seem to work - it sees all the wireless networks around, but refuses to connect (I'm using WPA Personal though the new screen seems to be "simplified")

I'm finding I get randomly logged out of my session 

The volume toggle on the side of the laptop _still_ doesn't work (didn't work in Hardy either, worked in Gutsy, everyone told me it was broken in Hardy and fixed in Ibex)

In general this one seems a lot less "stable" - I'm hovering near backing up /home and going back to Hardy or Gusty 

Any suggestions?

---

### Post by perce on 2008-12-13
> **PanopticChaos said:**
> 

Wireless doesn't seem to work - it sees all the wireless networks around, but refuses to connect (I'm using WPA Personal though the new screen seems to be "simplified")


I have a white Darter with Ibex too: my experience with WPA is that it works, in general, but sometimes it has an hard time understanding if it is supposed to interpret the passphrase as ASCII or hexadecimal. In the old Network Manager there is an option to choose it, but it has disappeared (maybe it confused some developer's grandmother?)

> 
I'm finding I get randomly logged out of my session 


Here I can't help, it never happened to me. However I did a clean install, not an upgrade.

> 
The volume toggle on the side of the laptop _still_ doesn't work (didn't work in Hardy either, worked in Gutsy, everyone told me it was broken in Hardy and fixed in Ibex)


It works in Ibex, and it worked in Hardy too. Try going to System > Preference > Sound

and choose "Master" in the scroll menu at the bottom of the window.

> 
In general this one seems a lot less "stable" - I'm hovering near backing up /home and going back to Hardy or Gusty 

Any suggestions?

It is MUCH more stable than Hardy for me, maybe something went wrong in your upgrade?

---

### Post by PanopticChaos on 2008-12-14
> **perce said:**
> I have a white Darter with Ibex too: my experience with WPA is that it works, in general, but sometimes it has an hard time understanding if it is supposed to interpret the passphrase as ASCII or hexadecimal. In the old Network Manager there is an option to choose it, but it has disappeared (maybe it confused some developer's grandmother?)


I'd believe that to be the issue (when I check the password field, it looks like a hex string) - but for me it is always not working with Ibex (whereas it worked fine before, and my other computers are still connecting fine so I know it's not the router).


> 
It works in Ibex, and it worked in Hardy too. Try going to System > Preference > Sound

and choose "Master" in the scroll menu at the bottom of the window.


There's not a "Master" option on mine, there is a PCM option - which does not seem to fix it.  When the upgrade to Hardy broke it - people told me this was a known issue which was fixed in Ibex, this was apparently incorrect.

> 
It is MUCH more stable than Hardy for me, maybe something went wrong in your upgrade?

Well that gives me hope - if I can just get some of the issues with Network Manager understood then I'll probably back up and nuke the issue from orbit.

Anybody know if there is a decent way for me to find out what packages I've installed on top of the "base" package list?

---

### Post by perce on 2008-12-14
I remember that pulse audio was broken in Gutsy and I had to set the audio output to ALSA. Now with Intrepid, I set output to pulse audio, but input is still from ALSA. You can try if this setting works on your computer. 

I attach a screenshot with my audio preferences, I hope it can help you.

---

### Post by PanopticChaos on 2008-12-14
> **perce said:**
> I remember that pulse audio was broken in Gutsy and I had to set the audio output to ALSA. Now with Intrepid, I set output to pulse audio, but input is still from ALSA. You can try if this setting works on your computer. 

I attach a screenshot with my audio preferences, I hope it can help you.

Thanks, but there's no "Master" option for me there (nothing changes when I set the options to "Pulseaudio" instead of "Autodetect")

---

### Post by perce on 2008-12-14
Try choosing "front" (it's the choice that worked up to Gutsy). If this doesn't work either, you'll have to wait for Tom.

Can you change volume with Fn-F11, Fn-F12?

---

### Post by PanopticChaos on 2008-12-14
> **perce said:**
> Try choosing "front" (it's the choice that worked up to Gutsy). If this doesn't work either, you'll have to wait for Tom.

Can you change volume with Fn-F11, Fn-F12?

Front didn't seem to work either 

The Fn-F11/12 option also doesn't seem to work

Oh well

Thanks for the help anyway - really thinking a reinstall is in the cards, the whole system is feeling really unstable

---

### Post by MorphWVUtuba on 2008-12-14
Yeah, if you just upgraded, it's always recommended to do a fresh install.

Also, it helps to have /home on a separate partition/filesystem/disk so all your stuff is automatically there even after a fresh install, as long as you don't format it during the install, of course. :lolflag:

---

### Post by PanopticChaos on 2008-12-15
> **MorphWVUtuba said:**
> Yeah, if you just upgraded, it's always recommended to do a fresh install.

Also, it helps to have /home on a separate partition/filesystem/disk so all your stuff is automatically there even after a fresh install, as long as you don't format it during the install, of course. :lolflag:


Yeah - haven't reinstalled in forever and I'm _really_ kicking myself for not putting /home on a separate partition right now ](*,)

Though this will be a good time to do so :)

Part of my question is "should these things be working better under Ibex with a Daru1" and it sounds like the answer is yes

---

### Post by thomasaaron on 2008-12-15
My DarU1 is really stable in Intrepid.

OK, where are we with this one? Did you do a fresh install? If not here's some starting points:

For your wireless, please follow these instructions:
> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).   

For the volume knob, this worked in Hardy and works in Intrepid. I think there was a fix for that in the System76 driver. However, there have been some major keymapping snafus in Intrepid, and it may be affecting that knob on your computer. Let's try the driver first, though. Here are instructions for installing/running the latest version:
> To install the System76 Driver, navigate to [http://planet76.com/repositories](http://planet76.com/repositories) and download the latest .deb package. It will be the one closest to the bottom of the page. Save the package to your Desktop and, when it has finished downloading, double-click it to launch the Gdebi installer. Then, click the install button.

Once the package has installed, you can open the System76 driver by going to System > Administration > System76 Driver. To install the drivers for your machine, Click the "Install" tab and the "Install" button. If you are restoring your machine to factory settings, Click the "Restore" tab and the "Restore" button.

When the driver has finished running, reboot your computer.

As for the random logouts, the next time it happens, log back in and open the System76 Driver and click the "Support" tab and the "Create" button. This will create an archive of log files in your home directory that you can send to us as an email attachment to support(at)system76(dot)com.

---

### Post by PanopticChaos on 2008-12-17
> **thomasaaron said:**
> My DarU1 is really stable in Intrepid.

OK, where are we with this one? Did you do a fresh install? If not here's some starting points:

For your wireless, please follow these instructions:

It eventually came up this time, but not until after making me reenter the password several times (and I wasn't mistyping it).  The only line I commented out was "auto eth0"

> 
For the volume knob, this worked in Hardy and works in Intrepid. I think there was a fix for that in the System76 driver. However, there have been some major keymapping snafus in Intrepid, and it may be affecting that knob on your computer. Let's try the driver first, though. Here are instructions for installing/running the latest version:


This didn't seem to work


> 
As for the random logouts, the next time it happens, log back in and open the System76 Driver and click the "Support" tab and the "Create" button. This will create an archive of log files in your home directory that you can send to us as an email attachment to support(at)system76(dot)com.

Honestly, this isn't the only instability I'm seeing - I figure something quietly went horribly horribly wrong with my upgrade.  I'm going to reinstall.

---

### Post by thomasaaron on 2008-12-18
That's probably a good idea. Sometimes it takes much less time to back up your files and re-install than it does to solve everything that might have gone wrong in an upgrade.

---

### Post by PanopticChaos on 2008-12-20
I did a clean install - that seemed to work out most of the issues.  Thanks!

Correction:
The wireless is _still_ only sporadically working.  I've tried the suggestions made earlier /etc/network/interfaces only has the two lines mentioned and I'm using the Network Manager icon.  It just seems to reject it over and over.  I know I'm typing the password correctly.  Every time the dialog comes back up the password field seems to be filled in with hex data.

---

### Post by thomasaaron on 2008-12-22
Wireless on my DarU1 is rock solid. So, either you have a hardware issue, or something isn't just right in your configuration. 

1. Does it act like that on *any* wireless network?
2. Describe your settings on the network that is giving you the problems.
3. Is suspend/hibernate involved in this problem in any way?

---

### Post by PanopticChaos on 2008-12-23
> **thomasaaron said:**
> Wireless on my DarU1 is rock solid. So, either you have a hardware issue, or something isn't just right in your configuration. 

1. Does it act like that on *any* wireless network?
2. Describe your settings on the network that is giving you the problems.
3. Is suspend/hibernate involved in this problem in any way?

I doubt it's a hardware issue, it's worked just fine up until this latest upgrade.  After the reinstall it's sometimes working, but only occasionally.

1) I live out in the middle of nowhere - I don't have much of an opportunity to try it out on other networks, but I'll see what I can do.
2) G network WPA-PSK TKIP encryption, nothing in the network has changed in years.  Everything else I have still can connect just fine.
3) No, I pretty much don't use suspend or hibernate on this laptop, they _never_ worked well on this machine and I finally gave up on caring as I don't end up needing it that often.

---

### Post by thomasaaron on 2008-12-23
I doubt it's a hardware issue too, but we need to rule that out so we're not spinning our wheels in the wrong direction. A good way to do that is to run from a live CD and see if you get the same behaviour. If you do, it's hardware.

You may also want to run these commands:
sudo apt-get install linux-restricted-modules-`uname -r`
sudo apt-get install linux-backports-modules-intrepid

If memory serves, those fixed some problem with the wireless LED on the DarU1 and a few other computers.

---

### Post by perce on 2008-12-23
> **PanopticChaos said:**
> 
3) No, I pretty much don't use suspend or hibernate on this laptop, they _never_ worked well on this machine and I finally gave up on caring as I don't end up needing it that often.


It's strange, they work well for me, and almost always have (some wireless issues from time to time, but no big things).

---

