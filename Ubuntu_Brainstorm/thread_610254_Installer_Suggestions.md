---
title: "Installer Suggestions"
date: 2007-11-11
forum: Ubuntu Brainstorm
---

### Post by ihavenoname on 2007-11-11
LVM is very nice, and very useful, and I would imagine that it wouldn't be too hard to add to the desktop installer.  Anyone know how I would push this suggestion forward? I heard there was a forum team now that would be able to pass this on but I'm not sure.

Also, I would recommend adding system-config-samba because I think that it is by far the best tool for configuring samba.

---

### Post by Nano Geek on 2007-11-11
You should post this in the [Ubuntu Idea Pool]("http://ubuntuforums.org/forumdisplay.php?f=306").

---

### Post by RAOF on 2007-11-11
> **ihavenoname said:**
> LVM is very nice, and very useful, and I would imagine that it wouldn't be too hard to add to the desktop installer.  Anyone know how I would push this suggestion forward? I heard there was a forum team now that would be able to pass this on but I'm not sure.
...

It's been on the Ubiquity (the live cd installer) wishlist for a while.  It's technically possible to do, it just requires someone to write the code.  Probably the best way to push this forward is to write that code yourself, or failing that a bounty on launchpad might attract some interest.

Of course, you can do this with the alternate CD, and have been able to for some time.

---

### Post by 23meg on 2007-11-11
Moved there.

You don't need to "push it forward"; it's a known shortcoming of Ubiquity. The main developer has had too many other things to work on, so it's been on hold since Dapper.

---

### Post by coolen on 2007-11-12
I'd definitely go for a better Samba tool. The point of a GUI frontend is to avoid having to go to the terminal or edit the configuration file directly, but as far as I know, a working (not even favourable) configuration can't be obtained using the default GUI.
For the GUI to be usable, you need to either have a way to give users sharing priveleges (or give it to all users by default), a way to either set user passwords or enable syncing with Unix passwords, and a way to set up a public share.
I'd also like to see a way for the average user to share a directory (within their priveleges, of course), ie, no root access required. Would this require work upstream?

---

### Post by Burgundavia on 2007-11-12
Easy file sharing is coming. See the spec:
[https://blueprints.launchpad.net/ubuntu/+spec/easy-file-sharing](https://blueprints.launchpad.net/ubuntu/+spec/easy-file-sharing)

Corey

---

### Post by coolen on 2007-11-12
Good to hear. I hope to see it for Hardy, but knowing it's in the works is great news.

---

### Post by ihavenoname on 2007-11-12
> **RAOF said:**
> It's been on the Ubiquity (the live cd installer) wishlist for a while.  It's technically possible to do, it just requires someone to write the code.  Probably the best way to push this forward is to write that code yourself, or failing that a bounty on launchpad might attract some interest.

Of course, you can do this with the alternate CD, and have been able to for some time.

I just might write something to do that. It's going to take a while though because I have several important tests in the coming weeks. 

Does anyone know how to execute bash commands using python??

---

### Post by RAOF on 2007-11-12
> **ihavenoname said:**
> I just might write something to do that. It's going to take a while though because I have several important tests in the coming weeks. 

Awesome!  It's great when people help out to fix problems they run into :).

> **ihavenoname said:**
> 
Does anyone know how to execute bash commands using python??

os.system('command string') is one option, but there are a variety of other, more fully featured options in the python stdlib (I believe that the *popen* family of calls may be what you're after).

---

### Post by ihavenoname on 2007-11-12
> **RAOF said:**
> Awesome!  It's great when people help out to fix problems they run into :).



os.system('command string') is one option, but there are a variety of other, more fully featured options in the python stdlib (I believe that the *popen* family of calls may be what you're after).

Ah, yes that is what I needed, I tested this quickly and I see how I can do this it's just a matter of sitting down and getting it done. Though, I won't be implementing this directly into Ubiquity, not at first.

---

### Post by ihavenoname on 2007-11-21
just as an update, I am still working on this. Though I don't know how long it will take me since, I still have to learn a few things along the way.

---

### Post by rockyl on 2007-11-21
> **RAOF said:**
> It's been on the Ubiquity (the live cd installer) wishlist for a while.  It's technically possible to do, it just requires someone to write the code.  Probably the best way to push this forward is to write that code yourself, or failing that a bounty on launchpad might attract some interest.

Of course, you can do this with the alternate CD, and have been able to for some time.

Does it still take 5 minutes per LVM group when it starts up? I tried to install Feisty when it came out but got tired of waiting every time. Not to mention the fact that one time it wiped out my LVM info once.

---

### Post by RAOF on 2007-11-22
> **rockyl said:**
> Does it still take 5 minutes per LVM group when it starts up? I tried to install Feisty when it came out but got tired of waiting every time. Not to mention the fact that one time it wiped out my LVM info once.

You've got something strange going on, which should probably be described in a bug if you can still reproduce it.  I've used LVM since the end of hoary, and I've never seen whath you describe (and haven't had my LVM metadata wiped, either).

Apart from one point in the gutsy cycle where the initramfs magic hadn't quite been ironed out (so you needed to put break=mount as a boot option so you could unlock your crypted devices without waiting for the timeout), I haven't seen what you describe.

---

### Post by ihavenoname on 2007-12-15
Ok here it is, I wrote a very quick, very ugly script for helping you install lvm. Right now, I recommend this to be tested INSIDE  a virtual machine that has things you don't care about. You need to follow these steps to use it.

1. Install lvm2 inside the live-cd.
2. in a terminal type sudo modprobe dm-mod
3. run the attached script as root.

also, I advise you to read the script over if you can to make sure it won't mess you up. This is just a proof of concept so treat it as pre-alpha. Also, keep in mind that not all features are implemented. 

Note: If you don't know what lvm is, then this is probably not the best way to find out. In general, I take no responsibility for what this script does. However if you use it responsibly and don't do anything funky you should not have a problem, I have used this myself and it worked for me. Good luck. (please do test, and if you like it let me know. Also, if it is deemed a worthwhile venture I will need to know how to submit it as a feature . )

---

### Post by ihavenoname on 2007-12-18
uh anyone interested at all?

---

