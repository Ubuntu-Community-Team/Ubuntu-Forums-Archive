---
title: "New Install - Size of Window/Font and other questions"
date: 2016-06-25
forum: Virtualisation
---

### Post by larry42 on 2016-06-25
I just installed a new image of Ubunto 14 under VMWARE Player on a Dell Inspiron laptop. When I bootup and log in, I get a desktop but the window that pops up on the desktop (and the fonts on it) are very tiny. 

1. How can I enlarge them? I looked around but couldn't find anything.
2. I also don't see any choices for a Linux command prompt. Any idea of where I can find one?
3. When I set up for the install, it asked me for the amount of disk space I wanted. Since I want to work with an application that requires around 200GB, I requested 250GB. When the Ubuntu installer asks for the amount of disk space I want, is that just for the OS and the root fs? Should I have just requested a smaller amount and then added another disk later on for the app?

Thank you in advanced for any help!

---

### Post by howefield on 2016-06-25
Thread moved to the "*Virtualisation*" forum for a better fit.

---

### Post by larry42 on 2016-06-25
> **howefield said:**
> Thread moved to the "*Virtualisation*" forum for a better fit.
Not sure I understand why these are Virtualization questions. Seems to me that they are specific to Ubuntu. Changing the display settings in VMWARE made no difference.

---

### Post by MAFoElffen on 2016-06-25
@ Larry42. Because, it seems everything that is virtualized somehow might be affected by being virtualized(?) Just a guess of reasons why. That way if it is or isn't, they can still get help. But the way I look at it, it does not matter.

@ the OP. Is this a question on a virtual Manager view? Resolution? Or specifically on changing the font of your guest?

I ask, because there are ways to do any of those, so it would be easier if your could narrow the focus. Do you just need to see what is there? ie Whole screen bigger?

---

### Post by larry42 on 2016-06-25
> **MAFoElffen said:**
> @ Larry42. Because, it seems everything that is virtualized somehow might be affected by being virtualized(?) Just a guess of reasons why. That way if it is or isn't, they can still get help. But the way I look at it, it does not matter.

@ the OP. Is this a question on a virtual Manager view? Resolution? Or specifically on changing the font of your guest?

I ask, because there are ways to do any of those, so it would be easier if your could narrow the focus. Do you just need to see what is there? ie Whole screen bigger?
I'm having trouble getting an accurate screen shot.

There is a small square in the middle of my screen that is the actual Ubunto screen and the icons and fonts are very tiny and almost unreadable. The rest of the area outside the smaller square is still visible on my PC, but is completely black. I've tried display settings on both VMWARE and on Ubuntu with no success. My feeling is that there is maybe a display driver missing maybe?

---

### Post by MAFoElffen on 2016-06-26
Are you using VmMware Tools with the guest VMware Workstation Player? What is the version of your Host OS and VMware player? You said the OS version of your guest was Ubuntu 14.04(?)? What flavor? (Ubuntu/Gnome/Mint/Xubuntu/Lubunuu)

In Workstation Player, are you using the Guest View > AutoSize/AuotFit? Are your trying to use View > Unity Mode?

Can you post a screen shot of you rcomplete desktop with the player shown (perspective and proportions)

---

### Post by larry42 on 2016-06-26
> **MAFoElffen said:**
> Are you using VmMware Tools with the guest VMware Workstation Player? What is the version of your Host OS and VMware player? You said the OS version of your guest was Ubuntu 14.04(?)? What flavor? (Ubuntu/Gnome/Mint/Xubuntu/Lubunuu)

In Workstation Player, are you using the Guest View > AutoSize/AuotFit? Are your trying to use View > Unity Mode?

Can you post a screen shot of you rcomplete desktop with the player shown (perspective and proportions)

Thank you. Can you suggest how to obtain a screenshot under my VMWARE Player? I've tried the "PrtScr" button on my PC alone with with "Ctrl" or with "Alt" and it doesn't work as it does under my windows host.

> **larry42 said:**
> Thank you. Can you suggest how to obtain a screenshot under my VMWARE Player? I've tried the "PrtScr" button on my PC alone with with "Ctrl" or with "Alt" and it doesn't work as it does under my windows host.

OK, I cannot get an accurate screenshot no matter what I do. So according to what I've been reading, I need to install or upgrade VMWARE Tools to get the ability to stretch the guest screen to make it large enough to use. The problem is ... I have no command prompt on the Ubuntu side and I can't find anyway to get it. Suggestions?

> **larry42 said:**
> OK, I cannot get an accurate screenshot no matter what I do. So according to what I've been reading, I need to install or upgrade VMWARE Tools to get the ability to stretch the guest screen to make it large enough to use. The problem is ... I have no command prompt on the Ubuntu side and I can't find anyway to get it. Suggestions?

Well, this is getting most frustrating. I managed to get a command prompt going and reinstall VMWARE Tools. It was working fine but after rebooting, it's back to it's old behavior of coming up with a tiny screen with low resolution. I think I am going to try CentOS.

---

### Post by MAFoElffen on 2016-06-27
If trying to get a screenshot of the whole host (to get a perspective of how it relates, in proportion to the whole desktop), or to just include the VM Player Guest Window, then...

You didn't tell me if the host was Ubuntu or Windows so will explain for both:

For Windows Host:
<Windows_Key>Snip > Select Snip Tool > New > Select what you want to show > Save As > post that file in Advavnced Post > Manage attachments.

For Ubuntu Host:
Upper Right Icon for Launcher > Screen Shot > Select Screen Shot utility > Whole screen > Save As > post that file in Advavnced Post > Manage attachments.

*** Tips ***
Usually in the VMware VM Player VM Guest Window, in the Menu, under View, there are optinos for "Fit guest to Window", "Scale". 

"Fit guest to Window" usually results in too large a window and some of it may be off the screen for most users. If using that mode, you can reset the guest resolutions to set to a bettter size that it will be at next use.

"Scale" has sub-options. I usually set to Scale > Always ... then grab and drag the lower left corner, until it is a size I want. I find this setting most useful. It doesn't always stay the same, but I can resize and what is in the windows scales to whatever the windows size is. 

I hate having to scroll a vm guest to get to different parts of a guest screen!!! That is what it does, if you don't use one of the two above options.

---

