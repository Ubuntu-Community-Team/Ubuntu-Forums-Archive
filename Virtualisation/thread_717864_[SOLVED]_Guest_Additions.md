---
title: "[SOLVED] Guest Additions"
date: 2008-03-07
forum: Virtualisation
---

### Post by M4rotku on 2008-03-07
I'm using VirtualBox and am having problems with the Screen Resolution.

I've tried reading the other threads about Screen Resolution and they all seem to agree that i need to install the Guest Additions.  However, they just say that and then don't say how and I've tried to use the manuel, but I got an error and am really confused as how to install the Additions.  I think I can get the Screen resolution fixed if i have the additions installed.  Can anyone walk me through it?:confused:


edit: mentioned the box

---

### Post by popch on 2008-03-07
Start your virtual machine. Once it is up and running, open the menu 'Devices' in the menu bar of the window the machine is running in. Click on 'Install Guest additions'. This will mount the image of a CD in your virtual CD drive which in turn will start the installation of the additions.

If all goes well.

The menues and entries might be somewhat different from the ones I gave. I am not running the English language version right now.

---

### Post by M4rotku on 2008-03-07
Ok, I got the guest additions installed, but I still haven't been able to use them to fix the screen resolution which was the reason why I wanted to install them in the firstplace.  Can anyone tell me how to use the guest additions to fix my screen resolution to something other than 800x600?

Much thanks

---

### Post by popch on 2008-03-08
The window holding your virtual machine has a menu bar. You already used the menu 'devices' to install the additions, if you followed my instructions above.

The same menu bar of the same window also contains a menu 'VM' (or some such), The first four entries occupy themselves with how the virtual screen and its size are handled.

If you are running any kind of Windows in your VM, you can right-click on the desktop, select something like properties/display in the pop up menu. In the property window shown after that select 'settings' which should reveal a slider which lets you change the resolution.

Depending on the settings in the VM menu, you also can change the apparent size and resolution of the machine by - dragging a side or corner of its window.

---

### Post by M4rotku on 2008-03-08
I tried to change the screen resolution within the guest Ubuntu system and with every resolution I try, the screen becomes pixelated and blury and I have to restart the machine to fix it.  This happens for every resolution option I try.  I have also tried resizing it using the machine options and they are set to full screen so it is definately a problem with the Ubuntu.:confused:

---

### Post by popch on 2008-03-08
I am just an IT guy, not a soothsayer. I have no way of telling what guest OS you have, what host OS you have and what options you set for your virtual machine in VirtualBox. 

I use Ubuntu 7.10, the VirtualBox 1.5.0_OSE and several guests with Win2000 and WinXP. I can use arbitrary screen resolutions up to the resolution (pixel size) of the laptop I am running this on. I also can use the seamless window integration although I rarely do so.

---

### Post by M4rotku on 2008-03-08
I am using Windows Vista Home Premium as the Host system, VirtualBox v.1.5.6, and Ubuntu 7.10 as the Guest system.  I have read in another thread in this forum of the possible solutions that involved installing the guest additions, which I did, but from that point on the directions given on that thread didn't work.

Here is the thread: [http://ubuntuforums.org/showthread.php?t=620828](http://ubuntuforums.org/showthread.php?t=620828)

If you look at TravisFix's post, I got confused at step 6.


When I click on the <Machine> menu on the toolbar of the virtual machine, the Seamless Mode is not available and when I click on <Auto-resize Guest Display>, it doesn't do anything.

Hopefully these are enough specifics about the problem.

---

### Post by popch on 2008-03-08
Ah, ok. I have no solution for you, then, as I don't use Linux in my VirtualBox.

However, I do not quite see the difficulty in following those instructions:

>  sudo gedit /etc/X11/xorg.conf 
(space after gedit and X11 must be capital X) 

5. You now need to hunt through the text until you see the display resolutions listed. The ones you will be concerned about will be listed under bit depth 24 or bit depth 16 (as these depths are the ones that give you a large amount of colors.) 
6. Next, either replace the existing resolution, or add another listed resolution in the exact same manner. Your resolution must be equal to or less than what the host machine is capable of (see step 2).

If you add your desired resolution to /etc/X11/xorg.conf, what happens?

---

### Post by M4rotku on 2008-03-08
I went to the site that he said he got his instructions from and they explained it in an easier fashion.  To sum up: It's fixed.

Thanks for your help though, i wouldn't have thought to recheck the thread if you wouldn't have asked for details.

---

### Post by popch on 2008-03-08
Your welcome.

Please:

Mark your thread as solved. You also might provide some hints as to how you solved your problem. Perhaps another poor soul might encounter the same problem and thus might be spared the difficulties you encountered.

Thank you.

Edit. Ah, I see that you already have marked it as solved.

---

### Post by M4rotku on 2008-03-08
I would love to tell every1 how i did it, but i really have no idea.  I would advise following the link to the other thread and following the offsite link from there.

---

### Post by vahnx on 2008-03-28
I would also like to know how to do this. I'll explain my situation:

I am running a Dell Inspiron 1501 laptop (1280x800) with Windows XP as the host. I run Vista and Ubuntu 8.04 Hardy Heron Alpha 6 in a virtual machine full screen on a secondary monitor 1024x768 when I am at school. At home I just run it in a window. 

Guest add-on's in Ubuntu are installed because I can drag my mouse between the guest & host perfectly. Now on the second monitor it shows 800x600 with a black border because the native resolution is 1024x768.

Left CTRL + G or clicking the "Auto-resize Guest Display" does not work. It remains 800x600 and it does not change if I re-size the window big/small or full screen. 

Editing the xorg.conf screen res. file would most likely not work because the size is constantly changing. But I am guessing there is some value you change in the xorg.conf file other than the screen resolution. 

If the person does not remember what they did to fix this, could they please post their xorg.conf file. Thank you.

---

