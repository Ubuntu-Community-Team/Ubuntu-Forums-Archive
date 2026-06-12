---
title: "windows xp reactivation issues"
date: 2008-01-20
forum: Virtualisation
---

### Post by tjksn on 2008-01-20
I've done a bit of searching and haven't found any real insight to a couple of issues.  One is with XP reactivation.  I've setup VMware to boot the install I have on another disk which it does just fine.  I initially tested some things without doing the reactivation then did a physical reboot into XP and had to reactivate it there.  I then rebooted into Gutsy and did the activation of the VMware setup of XP.  When I rebooted into Windows I had to reactivate again!  I though that once I had done the activation in both setups I would be done.  Any ideas how to get around this?

The second item is with sound.  I don't have sound in XP in VMware and when I searched on this topic I found a post listing some commands to use to tie ALSA to OSS, which I entered, and now when I boot into Gutsy (my session uses Enlightenment with Gnome) I get and Enlightnment error about not being able to load a sound module.  I'll search again for the commands I used and add them to this post.  Any insights will be appreciated.

Tom

---

### Post by kerry_s on 2008-01-20
removed

---

### Post by tjksn on 2008-01-20
For the audio issues in Enlightment here are some of the commands I ran in terminal as recommended by another poster.  There are a couple missing as I cannot find the original post, but found these posted by someone else.

1. Install a package called "alsa-oss" either by using Synaptic or maybe "sudo aptitude install alsa-oss"
2. sudo chmod +s /usr/lib/libaoss.so.*
#!/bin/bash
LD_PRELOAD=libaoss.so exec /usr/lib/vmware/bin/vmware-vmx.real "$@"

---

### Post by dpj23 on 2008-01-21
Vista lic allows for multiple installs for virtual environment...  I believe that they revisited the xp lic and you can install multiple times as well... Microsoft had a press release about 6 months ago...

---

### Post by jakornblum on 2008-04-04
What you are trying to do should not violate the XP EULA as you have only ONE install of XP that you are trying to access natively at times and virtually at other times.  Follow the directions in this post to get around the reactivation issues:
[http://ubuntuforums.org/showthread.php?p=4644845](http://ubuntuforums.org/showthread.php?p=4644845)

---

### Post by HermanAB on 2008-04-04
Hmm, the best solution is of course on The Pirate Bay.  It is much easier to use a cracked copy on Windows  XP on a VM.  I have more legit copies of XP than I have machines running it, so I have no qualms about running cracked copies on the VMs.

---

### Post by alpaslan11 on 2008-04-04
There  cheats in the web. to solve for copy xp

---

