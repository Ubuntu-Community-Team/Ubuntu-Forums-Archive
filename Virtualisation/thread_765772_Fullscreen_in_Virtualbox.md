---
title: "Fullscreen in Virtualbox"
date: 2008-04-24
forum: Virtualisation
---

### Post by JawsThemeSwimming428 on 2008-04-24
I just installed Hardy (final) in Virtualbox (yes I checked the md5). I installed the guest additions and they installed fine. Rebooted and hit Ctrl+F and I still have a very small screen (didn't change). I looked in the Vbox user manual and tried adding the Display subsection under the Screen section (I have done this before in Debian and DreamLinux) and rebooted and that didn't work. Not sure what I am doing wrong. Any ideas?

---

### Post by JawsThemeSwimming428 on 2008-05-05
Still having an issue. I just tried the same thing with my Ubuntu Studio VM and I got the same results. Not sure what I should do. Any advice?

---

### Post by JawsThemeSwimming428 on 2008-05-05
I looked in the Virtual Box manual and didn't have any luck doing it that way either. I am not sure why it is so difficult in Ubuntu? I was able to do it in Arch, Debian Lenny, Mepis, antiX, and a few others. I would really appreciate any help.

---

### Post by generic_idea_machine on 2008-05-05
First hit that comes up when you search for "Virtualbox full screen"

[http://ubuntuforums.org/showthread.php?t=351226](http://ubuntuforums.org/showthread.php?t=351226)

Check it out and see if it works for you

---

### Post by JawsThemeSwimming428 on 2008-05-05
Thanks, yea I already saw that. I am having an issue installing the Guest Additions. For some reason it doesn't always mount the Guest Additions .iso and when it does and I go to the mounted file and run sh ./VBoxLinuxAdditions.run to install them and it says something about the kernel version. But I can't even get it to mount anymore.

---

### Post by JawsThemeSwimming428 on 2008-05-05
Ok I figured out why I couldn't install Guest Additions. I needed to install  the kernel headers that ended in 'rt'. After I did that it worked. However, I am not sure how to add my desired screen resolution (1680x1050) to the Screen Resolution selection in Ubuntu. Does anyone know?

---

### Post by JawsThemeSwimming428 on 2008-05-12
Still having an issue, if anyone can give me a hand I would be appreciative! I just installed guest additions in antiX M7.2 and it worked in 2 min.

---

### Post by MyR on 2008-05-28
this might help...

[http://ubuntuforums.org/showthread.php?t=719126](http://ubuntuforums.org/showthread.php?t=719126)

peace

---

