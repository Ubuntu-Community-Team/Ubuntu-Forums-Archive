---
title: "My Ubuntu experience"
date: 2007-10-19
forum: Testimonials &amp; Experiences
---

### Post by Fred11 on 2007-10-19
I installed Gutsy Gibbon today.

All hardware worked out-of-the-box. :)

I was prompted with an optional to install the proprietary graphics card device drivers. I did so, but then I was prompted to reboot, I had hoped that a reboot wasn't necessary, this is Linux after all.

I can't sit at the computer without music, so I Rhythmbox to check if I could listen to radio. I could, I was pleased to see that there were couple radio stations available by default, so that I could just click on it, and get straight to listening, while I work with the computer, so I don't have to find music or radio stations. I am very glad that there were radio stations available, but at the same time, I wish there would be more than just 4 of them.

I did not auto-detect my computer monitor. I couldn't set the screen resolution higher than 1024x768, but then I manually picked my monitor out from the list, and I could now select a wider range of resolution. I picked 1280x1024, as I have 19" screen. It would be great if it would auto-detect my monitor, and put an resolution appropriate for my monitor size.
The screen refresh rate is 50 Hz, I can only choose 50, 51, 56 hz at 1280x1024, if I select lower resolution, I get more opptions. In Windows, I can run at 85 hz when I use 1280x1024.

I was pleased that Eye of GNOME was fast and had SVG support. I liked that I had PDF viewer installed, and didn't have to install it myself.

I tried to play a movie (an xvid one), it say I had to get a codec, I did, and it started to play audio, but not the video..

Mozilla Firefox is 2.0.0.6, it shipped with an out-dated version, 2.0.0.7 been out for a while now. I wanted to upgrade to recently released 2.0.0.8, but the "Check for Updates..." option under "Help" is for some reason grayed out. :(

I like that there is "Ubuntu Package Search" in the quicksearch-bar of Mozilla Firefox.

I tried out the "Wobbly windows" effect, but I found it to be _too_ wobbly. The wobbly thing is nice, but I think it is overdone, so it becomes annoying, I think it would be better if it was just slightly wobbly.

I also liked that you could clear the recent documents. It is a nice privacy feature.

There are no desktop icons at all. I wish there would be perhaps a trashbin or something.

The terminal is is black-on-white. I changed it to white-on-black, I don't understand why that isn't the default setting. A terminal has black background, anything else is just wrong.

In System->Preferences I have "Screen resolution", in System->Administration I have "Screens and Graphics", and Screen and Graphics, have all the functionality of the other one, so its kinda duplicate thing...

I have this "Ubofox" Firefox extension, but I have no idea what it does.

Most software I started, seemed to start at the upper-left corner. I would expect them to start a bit more in the center.

I went into the Services, and saw that Bluetooth was enabled. My computer don't have bluetooth though. I also saw that both APM and ACPI was enabled, kinda pointless to have both enabled, when I just need ACPI enabled. ACPI supersedes APM.

I really like the "Skyrocket" screensaver, it is awesome. :)
Wish the Matrix screensaves would be better and more authentic though.

---

### Post by Fred11 on 2007-10-19
I can scroll up/down. But I can't click the scrollbutton, to get this scroll thing where it scrolls when I move the mouse. This feature I have in Windows XP.

I have 2-side buttons, that were used to move forward/backward when browsing, they don't do that on Linux in Mozilla Firefox. They did do that on Mozilla Firefox in Windows XP.

I installed the "Microsoft Core Fonts", but I am not sure they're actually being used.

When I use a command such as "fdisk -l", it displays no output. It shows no indication why it fails or whats wrong. Took me a while to figure out, that its because I need to type "sudo fdisk -l". Maybe it should give me an error such as "Insufficient privileges".

In "Computer", 1 partition is not displayed.
sda1 NTFS - displayed
sda5 NTFS - displayed
sda6 NTFS - displayed
sdb1 ext3 - Ubuntu
sdb2 ext3 - not displayed

I went into "Screens and Graphics Preferences" and enabled "Widescreen monitor", now its bugged and its not possible to uncheck that option.

Now my computer time in Windows is wrong. :(

---

### Post by some_random_noob on 2007-10-21
Damn, you have some good points there. I thought that Firefox 2.0.0.6 WAS the latest... obviously not. 2.0.0.8 is very recent, but it doesn't seem to have any major changes. I was using Dapper last week, so 2.0.0.6 has been an improvement for me :)

It would be nice if the monitor settings would ALWAYS auto detect... it worked for me, but perhaps not for everyone.

Codecs still have problems? Grrrrr... I can get my DVD's to play, but the color is too dark! Definitely needs fixing.

I also agree about putting the trash bin on the desktop. *Sometimes* you have items on the desktop by default - For example, a floppy drive (If you still have one) and it also shows extra harddrives and partitions.

The idea of having white-on-black for the terminal is a great idea! It uses white-on-black if you install it as a server, so why not the same when you have a GUI? black-on-white is hard to read.

------------------------------------------------------------------------------------------------

Glad I read this, it helps me keep an open-eye that Ubuntu isn't perfect. But for me it seems to be perfect...

---

### Post by FredB on 2007-10-21
Firefox 2.0.0.7 is A WINDOWS ONLY security bug fix.

Firefox 2.0.0.8 will be released next week, as beta version of packages are being tested. Just be patient !

---

### Post by zekopeko on 2007-10-21
> **Fred11 said:**
> I can scroll up/down. But I can't click the scrollbutton, to get this scroll thing where it scrolls when I move the mouse. This feature I have in Windows XP.

I have 2-side buttons, that were used to move forward/backward when browsing, they don't do that on Linux in Mozilla Firefox. They did do that on Mozilla Firefox in Windows XP.

I installed the "Microsoft Core Fonts", but I am not sure they're actually being used.

When I use a command such as "fdisk -l", it displays no output. It shows no indication why it fails or whats wrong. Took me a while to figure out, that its because I need to type "sudo fdisk -l". Maybe it should give me an error such as "Insufficient privileges".

In "Computer", 1 partition is not displayed.
sda1 NTFS - displayed
sda5 NTFS - displayed
sda6 NTFS - displayed
sdb1 ext3 - Ubuntu
sdb2 ext3 - not displayed

I went into "Screens and Graphics Preferences" and enabled "Widescreen monitor", now its bugged and its not possible to uncheck that option.

Now my computer time in Windows is wrong. :(

fdisk -l must be run with sudo like so: sudo fdisk -l.

and you probably don't see your sdb2 ext3 partition because the disk can have only 4 primary partition. you should have made that last one a logical partition.

---

