---
title: "IPod will not mount in recovery mode to Windows XP"
date: 2010-06-20
forum: Virtualisation
---

### Post by Revolutionary101 on 2010-06-20
I am trying get my iPod touch jailbroken and I have done it many times before with a native Windows XP machine. Problem is I no longer use Windows on my home computers.

Currently, I am trying to jailbreak my iPod touch with VirtualBox. When I go through the process once my iPod touch goes into recovery mode VirtualBox will not mount it for Windows XP. VirtualBox detects the iPod touch but it will not let me mount it. Any ideas on how I could force VirtualBox to mount my iPod touch?

---

### Post by revolverXD on 2010-06-22
[http://ubuntuforums.org/showthread.php?t=1515308](http://ubuntuforums.org/showthread.php?t=1515308)
what i did for the iphone maybe it will work for the ipod too

---

### Post by Revolutionary101 on 2010-06-27
I was able to jailbreak my iPod touch. This is how VirtualBox magically detected my iPod touch in recovery mode.

1. I installed VMware Player. (The form that I had to fill out was a pain)
2. I tried to install Windows XP to no avail in VMware Player.
3. I installed VMware Tools.
4. Then suddenly when I went back to VirtualBox, it detected my iPod touch in recovery mode.

I think it might have something to do with the VMware Tools that I installed. I hope this helps anyone in the future (even though it is really vague on what I did)

---

