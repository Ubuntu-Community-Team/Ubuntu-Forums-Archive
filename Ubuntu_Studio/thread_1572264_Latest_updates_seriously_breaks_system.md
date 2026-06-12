---
title: "Latest updates seriously breaks system"
date: 2010-09-10
forum: Ubuntu Studio
---

### Post by Cyberpro60 on 2010-09-10
I have just installed (today) the latest version of Ubuntu Studio (10.04). The initial installation completed without any errors or problems. After the first reboot the system came online and, as far as I was able to check, it worked perfectly. I was most impressed at the wealth of software provided and the professional feel everything had. 
 
The monitor was correctly identified and the screen resolution was set correctly to 1920x1080. USB mouse and keyboard worked etc. I could surf the net right from the start etc. Brilliant!
 
During this first session the o/s threw up an "automatic updates" window. I accepted all the default options and waited whilst 220 plus megs of updates were downloaded and installed. This procedure completed without error messages or notifications and a system reboot was requested. [Note: I actually watched the update process in its entirety so there were no updates that failed etc]
 
On the second reboot however major problems emerged:
 
(1) The mouse cursor disappeared
(2) The screen resolution dropped significantly
(3) The screen aspect ratio was distorted.
 
I tried replacing the mouse with a PS2 version and rebooted but there was still no mouse cursor visible.
 
It seems that this update has seriously broken my system. 
 
Without a mouse I am unable to do very much (I am new to the Linux environment) and don't have a clue how to address this problem, let alone solve it.
 
Help and advice is very much needed but please bear in mind that I am a long way from being a linux guru so please keep your instructions simple and assume that I know little.

---

### Post by JC Cheloven on 2010-09-11
Hi, and welcome!

My bets: 1) some wrong controler was installed, most likely for you graphic card. 2) a kernel issue with some piece of your hardware.

First thing to see is whether the updates installed a new kernel. If so, a menu will show up at boot time (a text b/w screen). Try choosing the lowest kernel version available to boot (normal version, not recovery), and see if that helps. Alternatively, try booting in recovery mode from this same menu, perhaps you'll have at least mouse, to facilitate the next steps. Also, could you please open a terminal (alt-F1 and navigate to Accesories-Terminal), then run this command
```
uname -a
```
and tell us what the output is?

Second thing you can test is whether proprietary drivers are installed/needed for your system or not. Alt-F1 and navigate to System-Administration-Hardware controllers. Is there anything shown as installed or needed to install? Do you have a nvidia or ati graphic card? You could use a different version of a driver, if there are options. Or disable them altogether (this will probably get you to the state at installation time: everything will work although you can't use advanced desktop effects an graphics acceleration).

Anyway, these are guesses, as too little info was provided. To have a closer idea of your setup, please post the output of the following command at terminal:
```
lspci
```

Note: you can select text with the mouse at a terminal, then copy it with Ctrl-Shift-C (pay attention to shift!). To paste it in your post, Ctrl-V as usual should work.

---

