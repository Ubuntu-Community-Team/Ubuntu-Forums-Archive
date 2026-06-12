---
title: "Ubuntu - My humble balanced view? :)"
date: 2007-11-18
forum: Testimonials &amp; Experiences
---

### Post by hamsteroid on 2007-11-18
Hey folks,

Just to give some feedback. I installed Gutsy there 2 weeks ago and so far I am fairly happy with it. I have a few niggles with it but I am trying to flatten out the bumps as I go along.

What I like about Ubuntu is the slick responsive overall feel of OS. It's very friendly and easy to access. I still got access to the cmdline and all the tools I need are there.

Here are some positives:
1. Ubuntu detected and handle all my external usb drives perfectly.
2. I was able to turn off standby move for the Free Agent drive I had using the sdparm command. Could not do that in WinXp!
3. Able to write directly onto my ntfs partitions right out of the box. Neat!
4. Package support is great. All my retro favorites: Dosbox, ScummVm, Vice (some niggles).
5. cmdline cdrecord - perfect iso's!
6. Watching my video collection under Totem Video player out of the box.
7. Cool handling of my Nvidia 7600GT card almost right away! Kudos!
8. Firefox - used for 3 years on WinXP. Works flawlessly under Ubuntu with all my fave plugins.
9. Love the multiple screens (alt+ctrl+left/right). Is that in vista yet? :)
10. I love the debian logging system.

Here are some negatives (told you I was balanced!) :)
1. Could not get text tty working (ctrl+alt+F2 etc). Blank screen if I try to raise the res from 640x480. Even after a lot of effort with help from [linuxquestions and here]("http://www.linuxquestions.org/questions/ubuntu-63/blank-screen-during-boot-up-when-setting-vga795-600262/"). Tried the line in /boot/grub/menu.lst
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e870d1a9-e118-459c-8f23-903daa9f4b98 ro splash=verbose vga=795 (my monitor 1280x1024)

2. mikmod - my classic mod player loads up but does nothing but display "Type 'mikmod -h' for command line options!" - where initially it worked going to the player screen. Tried uninstalling/reinstalling the package. One of my niggles. :)

3. Brief moments of instability - mounted drive windows would go grey with inactivity after clicking open a few folders - Stay inactive. At least the windows can be reopened after force it shut.

But I think everything is here to make this an ideal OS. I spent two entire weekends working on my linux side of the dual PC. Hope to do this next weekend. Yeah I work weekdays. :D

---

### Post by armandh on 2007-11-18
stuck at low res problem
I found that my monitor was not communicating back to the OS and when I tried a different monitor all was well

---

### Post by erlyrisa on 2007-11-19
Don't you just love this latest Distro!!!!

-my only problem (as usual) ---PRINTER!!!! -bl#@@#y Lexmark - told dad to wait for the Brother to drop in price.

-Can't wait for XPS printers to come out - should be easy as chips than (at least I hope the manufacturers stuff the XPS decoding on the printer and not in the soft driver)

---

### Post by Rinzwind on 2007-11-19
1. Could not get text tty working (ctrl+alt+F2 etc). Blank screen if I try to raise the res from 640x480. Even after a lot of effort with help from linuxquestions and here. Tried the line in /boot/grub/menu.lst
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e870d1a9-e118-459c-8f23-903daa9f4b98 ro splash=verbose vga=795 (my monitor 1280x1024)


Do you get a splashscreen when booting? (between grub and login)
If not you need to change something in 
/etc/usplash.conf
The 2 numbers need to be changed into
1280
1024

:)

IIRC I think that solved the tty problem and the usplash not showing for me.

---

