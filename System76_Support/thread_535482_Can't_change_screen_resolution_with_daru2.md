---
title: "Can't change screen resolution with daru2"
date: 2007-08-26
forum: System76 Support
---

### Post by saxamo on 2007-08-26
Hi, this is related to the external monitor thread posted a few days ago, but I think my problem may be a bit different. I have a brand new Darter Ultra and it locks up whenever the screen resolution changes. I can't change the resolution manually and I can't play any full screen games. What happens is that the screen goes blank, comes back again, goes blank again, and then brings me back to the login screen. I'm not using an external monitor or compiz or beryl or anything, i don't see why it should be doing this. It's almost like it's stuck on 1280 x 800

I'm really not sure where to check for error messages or anything, so all help would be VERY appreciated!

---

### Post by thomasaaron on 2007-08-27
I just tested this on our shop Darter both with and without an external monitor, and I can access a number of alternate resolutions with no problems whatsoever.

Three questions come to mind:

1. Is the problem specific to a particular game?

2. Are you trying to change our resolution via some utility built into the game, or are you going to System > Preferences > Screen Resolution?

3. Did you re-image your system? And, if so, what did you pick for the video driver?

---

### Post by saxamo on 2007-08-27
1. No. Any game or program that tries to induce full screen (or a resolution change) causes this bug.
'
2. Both. I'm assuming that whenever I start a game, it changes the resolution to whatever it wants. However if I go to System -> Preferences -> Screen Resolution I get the same bug

3. I messed up my partitioning yesterday so I like JUST reinstalled ubuntu (with the system76 santa rosa liveCD) and restored my system with the driver utility this morning. Same problem before and after. If I were to re image it, what video driver should I choose? (and by reimaging I assume you mean "sudo dpkg-reconfigure -phigh xserver-xorg"??)

 I'm about to submit a bug on it, but i'm waiting for a little more info to emerge. I looked in the system log and this is the only error message i've found that seems to be related to this. This is in the syslog section:

```

gconfd (user-5668): Received signal 15, shutting down cleanly
gconfd (user-5668): Exiting
gdm[5188]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

I know that's not really saying anything but i don't know where else to look. Other 3d accelerations work like google earth and such, cause they're windowed. I just can't change the screen resolution for the life of me.

---

### Post by thomasaaron on 2007-08-28
Let's not file a bug on it just yet. I've heard no other reports of this particular problem, and I've not been able to duplicate it on our shop Darter. So, for now it is much easier for us to work on it  and track it as a support issue. Once it is filed as a bug, it gets prioritized and worked on when we're not dealing with pressing support issues.

Let me know what games I can test easily here in the shop. Something in the repos would be ideal. 

Also, if there are any other DarU2 folks out there that could try to duplicate the problem, that would be very helpful.

Regarding re-imaging, I meant did you re-install Ubuntu on your system? And if so, did the problem persist after re-installation.

Now that you've re-imaged with the Santa-Rosa CD, you need to run your System 76 driver if you haven't already: System > Administration > System 76 Driver. Then reboot. Then you will not need to run sudo dpkg-reconfigure.

---

### Post by saxamo on 2007-08-28
Ah, okay. I hadn't known the difference between a bug and a support issue.

I've sent PM's to other users that have stated that they own a darter, directing their attention to this topic. 

I did restore using the system 76 driver when I re-imaged the laptop, and I did it again for the hell of it just now to no avail.

Open Arena and  tremulous are FPS's you can get via synaptic, I can't run either of them. As soon as I click the icon, X crashes on me.

---

### Post by shingalated on 2007-08-28
Yeah, same here...I can't change resolution without causing the X server to crash, which also means I can't play ANY fullscreen games...Rather disappointing as I thought this was supposed to be better than the GMA 950.

---

### Post by thomasaaron on 2007-08-29
I'm imaging a DarU2 today to test this.
Standby...

---

### Post by palintheus on 2007-08-29
I have no issue with resolution changes on my DarU2, I did use the alternate cd and had to install xserver-xorg-video-intel, though.

---

### Post by thomasaaron on 2007-08-29
You also might want to back up your xorg.conf file and then run sudo dpkg-reconfigure xserver-xorg.

#Do not ask it to auto-detect your monitor.
#Select all possible resolutions.
#Select the Intel driver

---

### Post by saxamo on 2007-08-29
> **thomasaaron said:**
> You also might want to back up your xorg.conf file and then run sudo dpkg-reconfigure xserver-xorg.


Just did this following your instructions, did not resolve the issue :(:(

---

### Post by thomasaaron on 2007-08-29
OK, this one is definitely a bug after all.

From here on out, let's work on it from here:
[https://bugs.launchpad.net/system76/+bug/135639](https://bugs.launchpad.net/system76/+bug/135639)

---

### Post by poetbeware on 2007-08-29
I can't launch OpenArea either. I get the following in syslog when I try:

```

Aug 29 12:49:15 ubuntu gdm[9327]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

```

I get the same thing when I try to use Preferences/Screen Resolution.

-Paul

---

### Post by saxamo on 2007-08-29
The darter ultra contains an intel X3100

---

### Post by shingalated on 2007-09-07
Are there any updates on this?  Has anyone found any workarounds?

---

### Post by thomasaaron on 2007-09-07
The only workaround I've found so far is a fresh install.
We're working on finding a solution here:
[https://bugs.launchpad.net/system76/+bug/135639](https://bugs.launchpad.net/system76/+bug/135639)

---

### Post by shingalated on 2007-09-12
Is there a certain package that I could install from the Alternative Install CD?  I don't really want to reinstall my whole OS.

---

### Post by thomasaaron on 2007-09-12
Not that I know of. Unless you REALLY need to change your resolution, I'd suggest holding off until we can get it figured out.

---

### Post by thomasaaron on 2007-09-12
Here is how to fix it:

Go to a terminal and type:
sudo apt-get --purge remove xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel
sudo reboot

Let me know how that works.

We'll be making the fix in our imaging system and in the system 76 driver, if necessary, soon.

---

### Post by saxamo on 2007-09-16
It worked! I can now change screen resolution to my heart's content and play a variety of full screen applications. It did change my resolution to 1024 x 768, but restoring with the system76 utility fixed that right.

Thanks again tom, for all your hard work!!

---

### Post by manchufelo on 2007-09-19
I have had this very annoying problem for a while now. I tried the above solution and it did not work for me. Any other ideas?

---

### Post by thomasaaron on 2007-09-20
It should work.
Copy and paste the commands in, and be sure to reboot your computer.

If it doesn't work, please describe your problem so we can be sure it is actually the same problem everyone else is describing.

Best,
Tom

---

### Post by osx424242 on 2007-10-16
Worked like a champ on my panv3 (Pangolin Value) on Feisty, thanks!

---

