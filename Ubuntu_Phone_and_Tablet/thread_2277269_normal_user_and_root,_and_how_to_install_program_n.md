---
title: "normal user and root, and how to install program not in the store"
date: 2015-05-07
forum: Ubuntu Phone and Tablet
---

### Post by Yaowang_Li on 2015-05-07
Hi guys,

I just received my ubuntu phone, and I have some questions. 

one, why it is not need to set password for user

two, how to add normal user into sudoers file.

three, how to install google-chrome browser.

---

### Post by lgd on 2015-05-07
Hello,

I started my registration here to give you some answers - all in my opinion:

> **Yaowang_Li said:**
> Hi guys,
one, why it is not need to set password for user

two, how to add normal user into sudoers file.

three, how to install google-chrome browser.
1. Because many phone users don't want to enter a code on a mobil device. Technical it could be solved by the group nopasswdlogin.

2. The normal user is already in the group sudo for sudo permissions. Is this that what you want? Or does it not really work without password set? So you should maybe set one but in the system settings and NOT with passwd - in the German forum there was someone who had to reset his device after a password chance with passwd because it is not the normal way to set a password on the phone.

3. Other programs not in the store you can install by the command click with some options like install. Many informations you find by open reading on the ubuntu phone mailing list as a webview here: [https://lists.launchpad.net/ubuntu-phone/maillist.html](https://lists.launchpad.net/ubuntu-phone/maillist.html)

The preinstalled browser has a chrome rendering engine for websites. At the moment there is no official way to use grafical programs from a Ubuntu pc like chrome. And chrome is not open source so you have to use the open source variant chromium. Only this one you can compile for ARM cpu on ubuntu phones like the BQ: [https://code.google.com/p/chromium/wiki/LinuxChromiumArm](https://code.google.com/p/chromium/wiki/LinuxChromiumArm) But there is a compiled version available in at least the channel vivid-devel for experienced users. More information at a parallel new topic for all: 

[http://ubuntuforums.org/showthread.php?t=2277300&p=13281133#post13281133](http://ubuntuforums.org/showthread.php?t=2277300&p=13281133#post13281133)

Greetings, lgd

---

### Post by Yaowang_Li on 2015-05-08
wow, thanks a lot for giving so detail information. I just received my Bq ubuntu phone yesterday, so lots of things do not know.  

the reasons why I asked these questions are
When I tried to install a program, like htop, by using apt-get install htop, it said: W: not using locking for read only lock file /var/lib/dpkg/lock. 
I also want to install google-chrome browser, it help me to install some apps I used frequently through arc-welder. 

now I try to find useful information in mailing list and test chromium instead of google-chrome. 

thanks again.

cheers,

yaowang

---

### Post by lgd on 2015-05-08
In my last link there you will find the information you need. It's a wiki construction side around Ubuntu Touch. What you first need is to make the system writable. But before that make sure that you have backups and know how to use them with fastboot if the handy will some day or hour not boot again for several times.

---

### Post by Yaowang_Li on 2015-05-09
do you know how to search chromium-browser in vivid-devel channel? I did not find the complied version of it.

---

### Post by lgd on 2015-05-09
Simply install chromium-browser with apt-get and follow my translated German wiki link under construction.

---

### Post by Yaowang_Li on 2015-05-09
well, yes, this time I found it and also did as the construction in wiki. but there is an error,

[13229:13229:0509/195443:ERROR:browser_main_loop.cc(216)] Gtk: cannot open display: 

I checked the variable DISPLAY, it is empty,

as the instruction in wiki, we need to created a bash script. I did it for chromium-browser

#!/bin/bash

DISP=$1
Xmir $DISP --desktop_file_hint=/home/phablet/.local/share/applications/chromium-
browser.desktop &
sleep 0.5
DISPLAY=$DISP chromium-browser &

so what do you think the problem is ? should I define the content of variable DISPLAY? I think this bash script has already done.

---

### Post by lgd on 2015-05-09
Have you created the desktop file as explained above the script? There you need for Exec= to set the script followed by the display " :1" like described in the example. Then you have to start it with the new icon in your apps dash after you have scrolled down it to update it.

But notice that the resolution is not fine in this basic setup. But you can enhance it like the multitasking setup below after you have success and gone your first steps. You will need a extra keyboard too or a keyboard extension for chromium which someone had found and tried with success. Because the normal keyboard doesn't work in graphical pc programs (X11 programs over Xmir).

---

### Post by Yaowang_Li on 2015-05-09
yes, I did it.

at the end of chromium-browser.desktop 

Exec=/home/phablet/.local/share/applications/chromium-browser.sh :1
X-Ubuntu-Touch=true

---

### Post by lgd on 2015-05-09
Maybe there are missing some steps. What's the output of
```

/home/phablet/.local/share/applications/chromium-browser.sh :1

```
Please use CODE tag for your output answer like in my command.

---

### Post by Yaowang_Li on 2015-05-09
```

phablet@ubuntu-phablet:~/.local/share/applications$ ./chromium-browser.sh :1
[1431201228.303542] Loader: Loading modules from: /usr/lib/arm-linux-gnueabihf/mir/client-platform/
[1431201228.304837] Loader: Loading module: /usr/lib/arm-linux-gnueabihf/mir/client-platform/dummy.so
[1431201228.308302] Loader: Loading module: /usr/lib/arm-linux-gnueabihf/mir/client-platform/mesa.so.2
[1431201228.311185] Loader: Loading module: /usr/lib/arm-linux-gnueabihf/mir/client-platform/android.so.2
(EE) 
Fatal server error:
(EE) Failed to connect to Mir: Failed to send message to server: Broken pipe
(EE)
[13157:13157:0509/215351:ERROR:browser_main_loop.cc(216)] Gtk: cannot open display: :1

```

I did it.

I used wrong channel.
it is vivid-proposed, not vivid.

thanks so much for your help.

yaowang

---

### Post by lgd on 2015-05-09
Sorry, I had no time until now because of doing research and documentation work on this project in the forum here and so on. Great - you seem to be the first one here from the community (not as for example Xmir developer or trying it without publicity). :guitar:

In the German forum we are now (only) 2 and a third has temporary gone because of less time for waiting for my later followed keyboard optimizations. We will grow and hopefully perhaps help each other to get things to work and to include more people in this fine stuff. :KS

---

### Post by Yaowang_Li on 2015-05-10
yeah, understand. 

now I have another problem.

it does not show the whole pop-up window when I tried to add apps in chromium-browser through "load unpacked extension...". 
so even I select the correct apps folder, I cannot find the ''open'' button on the bottom-right of window.

---

### Post by lgd on 2015-05-10
Please attach a screenshot. You get it by pressing both volume keys at the same time and looking in the folder Pictures/Screenshots. And for this and more reasons try switching the handy for 90 degrees and try the multitasking setup from my link. Written from my Ubuntu phone.

---

### Post by Yaowang_Li on 2015-05-10
> **lgd said:**
> Please attach a screenshot. You get it by pressing both volume keys at the same time and looking in the folder Pictures/Screenshots. And for this and more reasons try switching the handy for 90 degrees and try the multitasking setup from my link. Written from my Ubuntu phone.

Yes, I tried multitasking, and this is the screenshot 
[ATTACH=CONFIG]261893[/ATTACH]

this is the content of chromium-browser.sh

```

#!/bin/bash


DISP=$1
Xmir $DISP --desktop_file_hint=/home/phablet/.local/share/applications/chromium-
browser.desktop &
DISPLAY=$DISP chromium-browser &
DISPLAY=$DISP fluxbox &
DISPLAY=$DISP xterm &
sleep 5
#DISPLAY=$DISP xvkbd -geometry 540x320+0+640 -compact -nonexitable
DISPLAY=$DISP xvkbd -geometry 540x320+0+620 -compact -nonexitable



```

or like this
[ATTACH=CONFIG]261899[/ATTACH]
[ATTACH=CONFIG]261900[/ATTACH]

---

### Post by lgd on 2015-05-10
The second picture looks right! The third one happens to me only when I start Firefox without Fluxbox. In all cases I start in high location and when I see the panel I rotate the display fast to a broad format. Try something like this. Maybe you need some tries and a little exercise for this.

Which problems do you have with the second picture? There you could try to click the square for maximizing the window. And there the used screen is broad enough for a file open dialog. Or does it starts in high format? This would be surprising to me.

Do you have configured your Fluxbox panel at the bottom away?

---

### Post by Yaowang_Li on 2015-05-10
there is no problem with the second picture, the reason I posted here just show you what is it before the wired window(picture 3).

---

### Post by lgd on 2015-05-10
Ok, then you need to try to displace the window on it's title bar in high format.

---

### Post by Yaowang_Li on 2015-05-12
> **lgd said:**
> Ok, then you need to try to displace the window on it's title bar in high format.

I solved this problem, it is the problem of fluxbox and x windows.

because I did not set the default resolution in x windows.
what I did:

[COLOR=#000000][FONT=verdana]echo "Xft.dpi: 96" > ~/.Xdefaults

then restart x windows.

[/FONT][/COLOR]

---

### Post by lgd on 2015-05-13
Thanks for your advice.

---

