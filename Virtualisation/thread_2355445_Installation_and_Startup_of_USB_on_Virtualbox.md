---
title: "Installation and Startup of USB on Virtualbox"
date: 2017-03-12
forum: Virtualisation
---

### Post by shane_faulkinbury2 on 2017-03-12
Okay, I'm kind of new to Virtualbox so bear with me.  I have Windows 10 installed on my Ubuntu 16.04.1 host.  I asked this question on the Virtualbox forum and got a very nasty response so I'm asking you guys.

I have the extension pack installed.  However, in Settings before startup I do not see anything under USB except the usual serial drive.

What I need to know is after I start Windows 10 up and plug in my flash drive it still does not show up.  What can I do to fix this?  :confused:

---

### Post by &amp;KyT$0P# on 2017-03-12
> **shane_faulkinbury2 said:**
> Okay, I'm kind of new to Virtualbox so bear with me.  I have Windows 10 installed on my Ubuntu 16.04.1 host.  I asked this question on the Virtualbox forum and 
This thread? - [https://forums.virtualbox.org/viewtopic.php?f=7&t=82203]("https://forums.virtualbox.org/viewtopic.php?f=7&t=82203")

> What I need to know is after I start Windows 10 up and plug in my flash drive it still does not show up.  What can I do to fix this?  :confused:
Make sure you've done all of the following -

1) Install the Extension Pack (you've already done this)

2) Add your user account to the [FONT=Courier New]vboxusers[/FONT] group -
```
sudo adduser <you> vboxusers
```
Log out and back in for this to take effect.

Run [FONT=Courier New]id[/FONT] in a Terminal to check if that's already done.  If you see vboxusers listed in groups, you're good here.

3) Install Guest Additions in the guest - Devices > Insert Guest Additions CD Image

4) In the VM settings, USB, add a new USB device filter.  If your flash drive is already conencted to your computer, can you make a filter specific to that flash drive?  Otherwise you can make a filter to capture all USB devices.

5) If you've already done all the above, eject/unplug your flash drive then plug it back in.

---

### Post by shane_faulkinbury2 on 2017-03-12
I take it it's alright to have USB 2.0 checked?

---

### Post by &amp;KyT$0P# on 2017-03-12
Yes, that's good.  But keep in mind that if you insert a USB 3.0 flash drive into a USB 3.0 port, the VM won't detect it.  You need an actual USB 2.0 port or USB 2.0 hub.

If you try USB 3.0 in the VM settings, **shut down and backup your VM first**.  I tried USB 3.0 once and it was a disaster.

---

### Post by shane_faulkinbury2 on 2017-03-12
Okay, what do these two statements mean?

```
adduser: The user `shaggy123' does not exist.
adduser: Only one or two names allowed.

```

---

### Post by &amp;KyT$0P# on 2017-03-12
It means you typed the wrong username.  To see your username, run in Terminal -
```
id
```
Your output will start with something along the lines of [FONT=Courier New]uid=1000(foo)[/FONT].  In that example, the username is "foo".  See what it is on your system and copy-paste it for when you run the command.

---

### Post by shane_faulkinbury2 on 2017-03-13
I thougfht you said to do this for Virtualbox?
> 2) Add your user account to the [FONT=Courier New]vboxusers[/FONT] group -

All ID shows is my computer user name.

---

### Post by &amp;KyT$0P# on 2017-03-13
And that's exactly the info you need.  This should work -
```
sudo adduser bubba vboxusers
```

---

### Post by shane_faulkinbury2 on 2017-03-13
The second I get the user setup I try to fire up Windows 10 and get these messages!

---

### Post by &amp;KyT$0P# on 2017-03-13
Is the host a EFI machine with Secure Boot enabled?

---

### Post by shane_faulkinbury2 on 2017-03-13
I'm pretty sure it's UEFI and not to sure about secure boot, but will check when I get back home.

It says UEFI mode, but Legacy mode is enabled.  Also Secure Boot is disabled.

---

### Post by &amp;KyT$0P# on 2017-03-13
What happens when you run this? -
```
sudo /sbin/vboxconfig
```

---

### Post by shane_faulkinbury2 on 2017-03-13
.

Installing that header as we speak.

I couldn't install the header because apparently mysql-server-5.7 is missing.  Somebody had previously told me I don't need that.

---

### Post by &amp;KyT$0P# on 2017-03-13
How did you get a 4.10 kernel on Ubuntu 16.04?  The latest kernel version in the repositories is 4.8.x.

What hardware do you need the 4.10 kernel for?

---

### Post by shane_faulkinbury2 on 2017-03-13
I have no idea how I got it unless it has something to do with my xbuntu install.

---

### Post by &amp;KyT$0P# on 2017-03-13
Just saw that you posted [this thread]("https://ubuntuforums.org/showthread.php?t=2355354").  I think you might need to actually get rid of that newer kernel.

Does it work after following DuckHook's instructions [here]("https://ubuntuforums.org/showthread.php?t=2355354&p=13619585&viewfull=1#post13619585")?

---

### Post by shane_faulkinbury2 on 2017-03-13
Do I have to a reboot after doing that because I'm still getting the same error in Virtualbox.

---

### Post by &amp;KyT$0P# on 2017-03-13
> **shane_faulkinbury2 said:**
> Do I have to a reboot after doing that because I'm still getting the same error in Virtualbox.
Yes, reboot afterwards.  And then run this again -
```
sudo /sbin/vboxconfig
```

---

### Post by shane_faulkinbury2 on 2017-03-13
Okay, I just figured I needed to do the reboot so I went ahead and did it.  After I did that I fired up Virtualbox with my flash drive in and it worked, nut I still couldn't see my flash drive..  So I ran that command again and here is what I got.

---

### Post by &amp;KyT$0P# on 2017-03-13
> **shane_faulkinbury2 said:**
> Okay, I just figured I needed to do the reboot so I went ahead and did it.  After I did that I fired up Virtualbox with my flash drive in and it worked, 
Great :)

> I still couldn't see my flash drive.. 
Now you'll want to go through [steps 3-5 here]("https://ubuntuforums.org/showthread.php?t=2355445&p=13619634&viewfull=1#post13619634").

---

### Post by shane_faulkinbury2 on 2017-03-13
Done and done!  Everything is working perfectly.  I want to tell you how much I appreciate you helping me!  Thanks so much for your help.

---

### Post by &amp;KyT$0P# on 2017-03-13
You're welcome! :KS

---

### Post by shane_faulkinbury2 on 2017-03-17
Okay, I got the extension pack working in Virtualbox and then for some unknown reason I downloaded Lubuntu and installed it.  After installing all my programs I fired up Virtualbox and installed Windows 10.  After installing and logging in I closed it and tried to install the extension pack.  I tried three times and got the same error.  So I deleted the extionsdion pack and re-downloaded it.  I got the same error after re-downloading.  Attached are my screen shots.  Can you please tell me whats wrong?

---

### Post by shane_faulkinbury2 on 2017-03-18
It's UEFI, but secure boot is off and like I said it was running fine on Ubuntu, but not on Xbuntu.

---

### Post by &amp;KyT$0P# on 2017-03-18
Are you running VirtualBox version 5.1.16?

In the window shown in your second screenshot, what does it say under "Details"?

---

### Post by shane_faulkinbury2 on 2017-03-18
No it's actually 5.032.  So I removed it from Software which is also where I got it from and I'm trying to install it from my terminal and this is what I get so imagine I have to remove that file it mentions before I install it.  The problem is I don't know how to remove it!

---

### Post by Cavsfan on 2017-03-18
> **shane_faulkinbury2 said:**
> No it's actually 5.032.  So I removed it from Software which is also where I got it from and I'm trying to install it from my terminal and this is what I get so imagine I have to remove that file it mentions before I install it.  The problem is I don't know how to remove it!

```
sudo apt purge virtualbox
```

---

### Post by shane_faulkinbury2 on 2017-03-18
Well I purged and auto removed it then re-installed and pretty sure I sawe it was installing 5.032.  Anyway after I re-install it I open it and Windows 10 is still showing.  So I fire it up just to see what happens and now I get the following error.

---

### Post by #&amp;thj^% on 2017-03-18
Did you run yet?
```
sudo modprobe vboxdrv
```

---

### Post by shane_faulkinbury2 on 2017-03-18
Thanks a lot, that did the trick!

---

### Post by #&amp;thj^% on 2017-03-18
That's Great! :D

---

### Post by Cavsfan on 2017-03-19
> **1fallen said:**
> Did you run yet?
```
sudo modprobe vboxdrv
```

Good catch there dude. :p

> **shane_faulkinbury2 said:**
> Thanks a lot, that did the trick!

Glad you got it worked out!. :) Please mark this thread as solved.

---

