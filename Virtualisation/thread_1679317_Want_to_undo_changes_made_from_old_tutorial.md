---
title: "Want to undo changes made from old tutorial"
date: 2011-01-31
forum: Virtualisation
---

### Post by Deer Hunter on 2011-01-31
Hello there,

I'm running Ubuntu 10.04 32-bit, and trying to get VirtualBox to host a virtual XP machine.  Anyway, I followed some instructions, which I've pasted below, from an old tutorial.  But now I want to undo what I did, because it gives me this error message while booting up:

An error occurred while mounting /proc/bus/usb 

Here are the instructions I followed.[FONT=Times New Roman]

[SIZE=2]_VirtualBox_[/SIZE]

Thanks to [HotShotDJ]("http://ubuntuforums.org/member.php?u=196293") :

**[COLOR=blue][SIZE=2]With the latest PEUL version of virtualBox [[/SIZE][/COLOR]**[/FONT]**[COLOR=blue][SIZE=2]2.1.4 PUEL][FONT=Times New Roman],  USB devices should work "Out of the box". All you need to do is add  your user to the  vboxusers group, then log off and back on, and USB  devices should be working without any further configuration.[/FONT][/SIZE][/COLOR]**
[FONT=Times New Roman]
You will need the Personal Use End License (PUEL) version of VirtualBox.  The Open Source Edition (OSE) version that is included in the Ubuntu  Universe repository does NOT support USB.

Go to System &#8594; Administration &#8594; Users & Groups. Unlock "Users Settings" then click on “Manage Groups”

Select the “vboxusers” group then click on the “Properties” button. Write down the Group ID number.

Open a terminal and type "gksudo gedit /etc/fstab" (without the quotes). Add the following lines to the end of the file:

 	Code:
 	# For USB access with Virtualbox
none    /proc/bus/usb    usbfs    devgid=1001,devmode=664    0  0 
IMPORTANT: Replace 1001 with the Group ID number that you wrote down earlier. Save the edited file and exit gedit.

Reboot your system.

Now you can enable the USB controller in VirtualBox. Open VirtualBox and  click on your Virtual Machine then click “Settings” -- In the left  panel, click on USB. Check off “Enable USB Controller” and “Enable USB  2.0 (EHCI) Controller". Do this for each VM in which you wish to have  USB access.

Click [HERE]("http://ubuntuforums.org/showthread.php?t=1015763") for more detailed instructions and additional options.[/FONT]


If you could help with this that'd be great. Thanks all.

Deer Hunter

---

### Post by JKyleOKC on 2011-02-01
My 10.04.1 system has nothing in fstab that refers to /proc/bus/usb, so simply putting a "#" at the start of that line in your fstab file should effectively restore it to its original condition. Adding the "#" (without quotes, of course) converts the line to a comment, which will be ignored, and you ought not see the error message again.

You WILL need to be sure you are a member of the vboxusers group, but the vbox installation routines usually handle that for you.

---

### Post by Deer Hunter on 2011-02-02
Thank you sir.  What I have actually done is, to open fstab and delete the line that I put in there before.  We'll see if that makes any kind of difference.

---

### Post by JKyleOKC on 2011-02-02
It should fix things. However I usually "comment out" such lines by adding the "#" character, instead of deleting them right away, so that it will be easy to put them back into action (by just removing that character) if bad things result. Once I know things are fixed, I can go back and delete them to clean up my files.

---

### Post by Deer Hunter on 2011-02-04
Thanks for the input. It did seem to make the USB work better. Unfortunately, my computer isn't powerful enough to run the program I wanted to use in the virtual XP box (video capture and editing).  But thanks for the help at any rate.  I guess I'll just have to keep dual-booting for now.

Deer Hunter

---

