---
title: "Linux Ubuntu 10.10 64 bits installation on HP Elitebook 8540p"
date: 2010-11-24
forum: Testimonials &amp; Experiences
---

### Post by PABlanche on 2010-11-24
[SIZE=2][FONT=Arial]Linux Ubuntu 10.10 64 bits installation on HP Elitebook 8540p[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Hardware configuration:[/FONT][/SIZE]
[SIZE=2][FONT=Arial]HP Elitebook 8540p Notebook PC Quad Core VD442AV Alternate OS.[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Processor Intel® Core™ i7-840QM Processor (1.86 GHz, 8 MB L3 cache), Up-to 3.2 GHz with Intel Turbo Boost Technology [/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Video/graphics [/FONT][/SIZE]
[SIZE=2][FONT=Arial]NVIDIA NVS 5100 graphics with 1 GB dedicated DDR3 video memory [/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Display [/FONT][/SIZE]
[SIZE=2][FONT=Arial]15.6-inch diagonal LED-backlit HD+ anti-glare (1600 x 900 resolution)[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Wireless LAN [/FONT][/SIZE]
[SIZE=2][FONT=Arial]Intel Centrino® Ultimate-N 6300 (3x3)[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]No webcam, no fingerprint sensor[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]HP 230W Docking Station VB044AV#ABA [/FONT][/SIZE]
 
 
[SIZE=2][FONT=Arial]I created a bootable USB stick with LinuxLive USB creator (LiLi): [http://old.linuxliveusb.com/](http://old.linuxliveusb.com/)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Used the iso file for Ubuntu "ubuntu-10.10-desktop-amd64.iso"[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]I plug the key into USB port of the machine before startup. Press esc key to access the BIOS menu, select boot on USB key.[/FONT][/SIZE]

[SIZE=2][FONT=Arial]WARNING: [/FONT][/SIZE]
[SIZE=2][FONT=Arial]All USB ports are not equal and the Ubuntu installation process won't start on the right USB ports or the front left ones. [/FONT][/SIZE][SIZE=2][FONT=Arial]You need to plug the key to the far left ones![/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Create partition (logical):[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Remove the FreeDOS partition [/FONT][/SIZE]
[SIZE=2][FONT=Arial]Swamp of 20MB[/FONT][/SIZE]
[SIZE=2][FONT=Arial]\ of 24MB[/FONT][/SIZE]
[SIZE=2][FONT=Arial]\home with the rest of the HD[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Ubuntu installs correctly without any further intervention.[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]WARNING:[/FONT][/SIZE]
[SIZE=2][FONT=Arial]When I restarted the computer it did not boot correctly and was stuck with the following error message:[/FONT][/SIZE]
[SIZE=2][FONT=Arial][ 6.484165] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]I found the solution on a forum ([http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/):](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/):)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Start the computer again (second time) you should access a screen that propose you different version of Linux to start with. Select the first one, but ask to edit it: "e" key.[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Add "nomodeset" at the end of the second from last line after "quiet splash". Then press <Ctrl>+<X> to boot[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]In my case, Ubuntu loads, but with a screen resolution of 800x600 instead of 1600x900. Plus, this solution is not permanent and should be redone each time if not fixed as follow:[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Use terminal [/FONT][/SIZE]
[SIZE=2][FONT=Arial]Write: "sudo nano /etc/default/grub" [/FONT][/SIZE]
[SIZE=2][FONT=Arial]edit the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" [/FONT][/SIZE]
[SIZE=2][FONT=Arial]into GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Pres <Ctrl>+<X> to save, <y> to confirm, and <Enter> to quit.[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Then you need to update grub by entering this command in the terminal:[/FONT][/SIZE]
[SIZE=2][FONT=Arial]"sudo update-grub "[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Close the terminal[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Re-boot[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]This done, the screen resolution was still 800x600 and I freak out a little bit before I realize the Nvidia driver was not installed. So: go to Système ->administration->additional driver[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]The system recognize by himself the missing driver and ask for an download. Accept. Restart. Your should be fine (so I am).[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]I run tests and results are:[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Is working:[/FONT][/SIZE]
[SIZE=2][FONT=Arial]DVD, SD reader, USB ports, Ethernet ports (both on laptop and docking station), WiFi, sound, shortcut keys at the top of the keyboard (mail, home, calculator). [/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Is NOT working:[/FONT][/SIZE]
[SIZE=2][FONT=Arial]The ambient light sensor is not working at this stage.[/FONT][/SIZE]
[SIZE=2][FONT=Arial]The shortcut key for disconnecting the touchpad.[/FONT][/SIZE]
[SIZE=2][FONT=Arial]The shortcut to use a projector <fn><f4> (though the projector can be accessed through the monitor interface).[/FONT][/SIZE]

---

### Post by PABlanche on 2010-11-30
The "Suspend" and "Hibernate" functions where not working. This is a known bug reported here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998)

The solution, also explained here:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9966400](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9966400)

fixed the problem.

> create files : /etc/pm/config.d/00sleep_module and /etc/pm/config.d/unload_module
add line to files : SUSPEND_MODULES="xhci-hcd"Hope this helps.

---

### Post by PABlanche on 2011-02-11
Microphone has a very weak input, can only hear some sound when taping the mic. can not have a conversation in VoIP.

Solution is to enter the sound preference panel, go to input, select microphone 2 as connector.

---

### Post by johntaylor1887 on 2011-02-12
Some HP computers have notoriously bad compatibility with linux. It's not necessarily the OS's fault. And if Ubuntu does not support that model, possibly another distro would fare better. And if need be, just stay with windows. Good luck.

---

### Post by rpdillon on 2011-02-14
Thanks for the detailed information!  I'm setting up the exact same model of machine this morning, and your thread really helped me work through all the issues I had (USB ports, video drivers, boot options, etc.)  Thanks.

---

