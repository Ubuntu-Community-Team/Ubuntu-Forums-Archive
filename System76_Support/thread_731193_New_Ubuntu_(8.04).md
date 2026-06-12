---
title: "New Ubuntu (8.04)"
date: 2008-03-21
forum: System76 Support
---

### Post by roscoetuff on 2008-03-21
See that Canonical is listing 34 days until the new 8.04 is out. Should I presume to NOT touch this until System76 provides or approves or suggests the preferred "upgrade" procedure? Is this something to be expected?

---

### Post by thomasaaron on 2008-03-21
We post a "How to upgrade to..." thread on the forums once we've finished testing on all of our machines. We aim to (and have always been pretty successful at) finishing out testing just as Canonical officially releases the newest version.

Of course you are free to upgrade early if you want -- and we would be interested in hearing about any bugs you encounter if you do -- but we won't be able to provide technical support on Hardy until it is released / we are finished with the testing stage.

---

### Post by voidmage on 2008-03-21
gazp3 user here. This is everything that works without system76 drivers.

When I close or open the screen, my laptop beeps. I'm not sure if this is a new feature.

Looking into that more, it looks like a debugging thing. It can easily be turned off through power settings->general->use sound...

Cheese "just works" with the webcam at 640x480. This was something camorama had trouble doing in gutsy.

Sound works, haven't tested the mic yet.

Card reader is kind of flaky. Last time I used it (last week) it would stop working after I removed a card and wouldn't work again until a reboot.

Haven't tested suspend/hibernate.

---

### Post by reh4c on 2008-03-21
Daru2 user here:
All hardware "works" (some better than others)  out of the box, except for the UPEK fingerprint reader.  
Software:
1.  Cheese appears to hang after recording one video with the Microdia webcam--preview image not reset (bug reported).
2.  Screen dimming bug appears fixed, but I have seen a few sporadic readings of the battery by Gnome Power Manager.  (Much improved from Gutsy); many bugs reported
3.  Screenlets are awesome, but crash frequently and the applet manager appears twice in the panel tray (bug reported).
4.  Firefox 3 Beta 4 crashes frequently--numerous bugs reported
5.  Suspend and hibernate are both flaky; suspend allows lights to flash, but when I try to resume, the laptop completely shuts down; hibernate appears to work, but I get numerous HAL errors when starting hibernate

Now that the Hardy Beta is out, PLEASE HELP TEST IT!  :guitar:

---

### Post by TheBuzzSaw on 2008-03-22
I have Daru2. I plan on installing 8.04 beta in the next couple days. My primary goal is to get dual monitor support working (as I have heard claims it has been drastically improved). I will be sure to report on other aspects as well (including the microphone since I regularly use Skype now).

---

### Post by Paul-Devon-UK on 2008-03-23
Hi, Installed from the latest daily build (d/l 23rd March) and installed using Wubi. I have only been using it for a few hours but so far all seems to be working fine including wireless, 3D acceleration (needed a driver/software d/l) and added a game OK just for a test.

Unfortunately the Update Manager is not communicating correctly. I am told there are 27 updates to install. The list shows 27 entries. After clicking on Install Updates - NOTHING. It just sits there with the cursor spinning.  Connection Properties shows the interface is idle. I tried changing the process priority to -20 but all that did was to freeze the Change Priority window!

I have tried a re-boot but no change.

I did change the Host and Domain (workgroup) and rebooted but can not see that would break it as all other Network functions seem to be working. I an using FF on the machine to write this while it is all frozen on another workspace.

Update Manager must have been able to connect to find the 27 updates that it lists.

I am a total NooB to Ubuntu/Linux (1st install) so have no idea where to find a log to look for clues. If you tell me where to look I will gladly post a log if you wish.

Overall - WOW! Bye Bye M$! FREEDOM at last!!!

<Update>
I found that I could right click on the notification icon. Preferences just froze. 

Start Package Manager **worked** and I could apply the updates successfully (apart from language-pack-en - crash report sent. It worked on the second attempt after all others were applied).

The Update Manager icon has now gone. I wonder if it will have fixed itself with one of the updates? ;-)
</Update>

---

### Post by thomasaaron on 2008-03-24
Try running:
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

(That is essentially what update manager does.)
See if they work/throw an error.

---

### Post by walkeraj on 2008-03-24
DarU2 User here.  Aside from the suspend/resume not working that was reported above, my power meter doesn't work most of the time in 8.04(Hardy).  It's either not there, or displays the "charging from wall" status regardless of whether it's plugged in or not.

---

### Post by thomasaaron on 2008-03-24
Please post the output of:
cat /boot/grub/menu.lst

---

### Post by walkeraj on 2008-03-24
Here it is, trimmed of comments.

```
default		0
timeout		3
hiddenmenu

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=18ae9e50-1a9b-4391-af3a-4a4b52624c13 ro quiet splash ec_intr=0
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=18ae9e50-1a9b-4391-af3a-4a4b52624c13 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18ae9e50-1a9b-4391-af3a-4a4b52624c13 ro quiet splash ec_intr=0
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18ae9e50-1a9b-4391-af3a-4a4b52624c13 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by Paul-Devon-UK on 2008-03-24
> **thomasaaron said:**
> Try running:
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

Ah, well, now you see - it's a bit like this.....
me@sandbox:~$ sudo apt-get update
sudo: unable to resolve host sandbox

I think I broke my baby :confused:

I had found this and guessed it may be the cause. I changed the host & domain after install (WHY wasn't I asked for this during the install!) I was trying to rectify this when I found your reply.

/ETC/HOSTS
127.0.0.1 localhost
127.0.1.1 sandbox.valhalla

/ETC/HOSTNAME
sandbox

/ETC/RESOLV.CONF
domain valhalla
nameserver 212.74.112.66
nameserver 212.74.112.67
<snip>

/ETC/SUDOERS
**Unable to access**. As I understand it the file should contain "%admin sandbox=(ALL) ALL" or "%admin ALL=(ALL) ALL"

I am downloading a live CD to boot from and get access to /etc/sudoers to check so I can edit if needed.

<edit>
It looks as if I am the victim of my own failings. 
1 - I installed using Wubi to a virtual drive so I am unable to mount the 'drive' to access the files.
2 - A Windoze user who should have had more faith and done a proper install in the first place.

I now have the option of trash/re-do the Wubi install or do a real install.

Either way - **Ubuntu 8.04 is not the reason for my problem.**

As a parting shot I would like to suggest that the GUI for changing the host name be made to do ALL that is needed. Also -**_ for f*** sake get rid of the need to enter a password every time you need to change anything (Vista?)._** It is MY system. If I am an Admin then trust me and let me administer MY system. I am at home in a safe environment so should not need to type a password every 20 seconds while setting up the system. 

Thanks all - Paul.
</edit>

---

### Post by thomasaaron on 2008-03-24
walkeraj,

Well, it looks like ec_intr=0 is correct. So, I'm not really sure at this point what is going on. In previous tests on Hardy here in the shop, it worked. Fine.

1. Are you running Kubuntu? If so, I don't know how well that solution works in Kubuntu/Hardy. I believe it worked OK with Kubuntu/Gutsy.

2. In Hardy/Gnome 64-bit, it worked in our shop tests. I guess it is possible that something changed between then and now that is causing problems. We will probably not be testing it again, though, for a couple of weeks.

---

### Post by walkeraj on 2008-03-24
thomasaaron,

Nope, running Ubuntu not Kubuntu.  Seems to be working now after a reboot, but I will let you know if it flakes out again.

Another issue, however, is the following: Say I turn my brightness all the way up when the computer is plugged in.  If I remove it from power and plug it in again, it sometimes randomly goes to a brightness level that is below the maximum.  Sometimes it works perfectly and goes back to maximum, but sometimes it is 1-3 settings below the maximum.

Also, the screen seems a little faint even at the maximum level (both in Gutsy and Hardy).  This could just be the model of laptop, however, as I've not had the chance to compare it to another of the same model or with a different operating system, so I couldn't say for sure.  Have any DarU2 users noted a brightness difference between Linux and Windows?  There don't seem to be any controls for the brightness in the power management settings (only the function keys can change the brightness as far as I've found), so is it possible that whatever process responsible for calculating the brightness range for an individual machine didn't configure correctly?  Do you know what setting or proc entry is modified to change the brightness?

EDIT:

Another power issue.  Just a moment ago, I closed my laptop screen and, as I closed it, I remembered I wanted to check something and opened it almost immediately.  The screen did not turn back on automatically and, when I hit a key, it turned back on, but with TWO power monitor applets.  When I removed the power cable with the screen still open, the laptop went into suspend (the closed-screen behavior for battery mode).  When I pressed the flashing power button to bring it back from suspend, the laptop turned off.  So, I decided to experiment some more.  After a restart and login, I get to my desktop, but it is at maximum brightness.  Only after plugging the power in and removing it again (presumably to raise the event), did the brightness go back down.  I plugged it in again, and it resumed its normal behavior of sometimes going to maximum, sometimes going to just below maximum.

I think I'm going back to Gutsy.  Seems like Hardy has a lot of work left to do in the month they have until release.

---

### Post by voidmage on 2008-03-24
After more using hardy, I found the same brightness issue.

Also I have trouble connecting to hidden wireless networks. I've tried with networkmanager, doing it manually through "Manual config" and iwconfig/dhclient, none have worked.

---

### Post by thomasaaron on 2008-03-24
walkeraj,

Adjustments made using function key combinations are not permanent.  For permanent adjustments, you have to use System > Prefs > Power Management.

---

### Post by walkeraj on 2008-03-24
There are no brightness levels listed in my power manager.  That was the first place I looked.  It looks like they are attempting to make the fn-key adjustments permanent in Hardy.  There are no brightness options available in AC power, and in Battery power there is merely a checkbox that says "Reduce backlight brightness", which seems to affect whether or not any brightness modification is done.

It is, unfortunately broken, though.  I've found that if I unplug the power and plug it back in again repeatedly, BOTH brightness levels decrease each time until battery level is at the minimum and AC level is two levels above that.  IT stabilizes there.

Looks like power state detection and brightness level modification are seriously broken in Hardy.  I've reported the bug.

---

### Post by agent8131 on 2008-04-24
> **Paul-Devon-UK said:**
> 
/ETC/HOSTS
127.0.0.1 localhost
127.0.1.1 sandbox.valhalla


Change:
"127.0.1.1 sandbox.valhalla"
to:
"127.0.1.1 sandbox.valhalla sandbox"

See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

---

### Post by Paul-Devon-UK on 2008-04-24
> **agent8131 said:**
> Change:
"127.0.1.1 sandbox.valhalla"
to:
"127.0.1.1 sandbox.valhalla sandbox"

See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

Thanks for that. I ended up trashing and re-installing as this happened only a day or so into trying it for the first time.

---

