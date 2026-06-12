---
title: "When will the screen res problem be solved?"
date: 2006-11-24
forum: The Cafe
---

### Post by Somenoob on 2006-11-24
Ubuntu is undoubtedly the best OS i have used but it's only drawback is the options for screen resolutions, my question is: why aren't all of them just present to begin with? One of the first things you do when you install an OS is to install drivers for the hardware and among them are video cards. After, you'll probably want to configure the resolution, for that you must go through the "dpkg-reconfigure xserver-xorg" and that thing is just ridiculous it has endless questions and I always have to back up the configurations because I'm just using it for adding resolution options, and my problem with it is that it sometimes does not appear to add all the resolutions you choose, and in some cases it adds nothing. Why is there not a command just for the screen resolutions?

---

### Post by tubasoldier on 2006-11-24
I have always found it easier to edit the xorg.conf file myself. BACK IT UP FIRST! But it is quite simple to add screen resolutions to it. 

That said, I do agree with you. Ubuntu is one of the worst distros when it comes to screen resolution.

---

### Post by Beamerboy on 2006-11-24
For Nvidia drivers there is an option for adding screen resolutions to xorg without running dpkg-reconfigure

I will see if you can find the correct method (HINT it is all in the man pages for nvidia-xconfig)

Paladine

---

### Post by Somenoob on 2006-11-24
> **Beamerboy said:**
> For Nvidia drivers there is an option for adding screen resolutions to xorg without running dpkg-reconfigure

I will see if you can find the correct method (HINT it is all in the man pages for nvidia-xconfig)

Paladine

I have a Nvidia driver, and where is this method? the man page for nvidia-xconfig is too long :( and I'm too busy.

---

### Post by John.Michael.Kane on 2006-11-24
Check the second post [http://ubuntuforums.org/showthread.php?t=289269&highlight=modeline](http://ubuntuforums.org/showthread.php?t=289269&highlight=modeline) make adjustments to fit your screen.

---

### Post by Beamerboy on 2006-11-24
I am busy too, I suggest you make the effort to read the man page, the section you want is not very far into the document.

Paladine

---

