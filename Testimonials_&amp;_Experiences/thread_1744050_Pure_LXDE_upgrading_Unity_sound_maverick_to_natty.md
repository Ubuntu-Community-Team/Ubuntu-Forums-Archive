---
title: "Pure LXDE upgrading Unity sound maverick to natty"
date: 2011-04-30
forum: Testimonials &amp; Experiences
---

### Post by vanquishedangel on 2011-04-30
Fist off I would love to thank the Ubuntu teams for a really nice job well done! good job guys. 

I am just putting my 2 cents in here but i reciently updated 3 computers to natty norwhal and i am really liking it alot. The computers I have are:
1. hp dc7100 3.8 ghz ht, ati radeon 4350 512 mb video ram, 4 gigs ram; 
2. hp dc7100 3.0 ghz ht, ati radeon 2400xt 256 mb video ram, 1.5 gigs ram; 
3. compaq presario 1.6 ghz, ati mobility radeon 7500 64 mb video ram, 1 gig ram;

First off I would like to say that the gallium drivers that natty installed are better than the mesa drivers that were on maverick. Pictures are clearer and Heroes of Newerth runs way better with no crashes on the first computer, haven't tried the second yet but it also has the gallium drivers. The third computer has the mesa drivers on it in natty. The gallium I am referencing is "Gallium 0.4 on AMD RV710". The compaq is most likely to old for that driver. I hate installing proprietary ati drivers so this is very good for me.

When I went to do the upgrade all the computers listed had ubuntu 10.10 and a pure lxde install following the guide here:

[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

I liked this set up very much, it made the old compaq run like new and the other worked really well also. No problems with any computer that ran 10.10 and pure lxde except for sound wich is solved by typing gnome-volume-control in terminal and setting some setting in output to analog mono output/amplifier as well as a few others like analog duplex stereo. The performance was excellent.

When I updated the first one, the upgrade tool never made it through installing and it stopped with an error after the sources list change when it was getting software. the error was:

/var/cache/apt/archives/libre-office_common1%3.3.3.2Lubuntu4all.deb
E:Sub-process/usr/bin/dpkg Returned an error code (1)

So then when that didn't work I booted into the recovery kernel and choose safe mode to boot in, logged in and I only had a command line, I typed:

sudo apt-get update

then:

sudo apt-get upgrade

This worked way better that the software upgrade tool (the upgrade tool has never worked right for me) and got farther than it, but still failed with another error i forgot to write down. but it installed all other parts this way despite the error and that is important for this topic. Because the "sudo apt-get upgrade" command went alot farther it made things easier. When i rebooted from that and tried to log in, I had no use of my mouse or keyboard so i could not log in.

I then decided to do a fresh install and made a live usb of natty on another computer, booted into the usb and was really not liking the fact I was going to delete all that work of installing games, my school work, etc. As I was clicking to install a fresh copy at the screen where it says usually a choice of erase disk or install along side, it also gave a choice of "upgrade from 11.04 to 11.04" and I would get to keep my files and folders with this option. OMG that was the best thing ever to have added in there and really was a surprise THANK YOU! I have never seen that before and that was a very welcome surprise. 

The other 2 computers were only slightly less difficult to install natty on the steps are as follows for a pure lxde maverick to upgrade to natty (not pure lxde)

1. get a copy of natty ( I used a usb live copy using usb creator or start up disk creator).

2. in a command line type "sudo apt-get update" then "sudo apt-get upgrade" and wait for it to finish it takes awhile.

3. if it didn't update correctly and wont boot and allow login, then boot from the natty disk, follow the steps to install Ubuntu,  and when you get to that screen with a choice of " erase disk and install" " install along side", etc. choose "upgrade from 11.04 to 11.04" ( when i tried to get that option from maverick it wouldn't give the upgrade option without erasing all my data so not sure if the Upgrade from 10.10 to 11.04 is there at all or shows up once in awhile, but it showed up when followed these steps as "11.04-11.04").

In conclusion of all of this posting, I would like to see lxde be officially supported and a pure lubuntu made if possible, I realize you guys are busy. The laptop when updated said something about the hardware it had could not run unity and booted into Ubuntu classic, but lxde runs stellar on it so i used synaptic and installed lubuntu from there. Great job with the OS and it is an awesome one, thank you for taking the time to read this, I know it is kinda long. I also hope my post helped and maybe the upgrade tool will improve, it is a real pain. Also this issue with upgrading may have been cause by an enabled repository, one error gave some thing about a newer version installed.

Here is a possible suggestion that may help take care of the hype about the desktop versions, Is there a way if the computer is connected to the internet that the installer could let you choose? Sort of like many distro's let you choose browsers. If this is possible that would be great! Again just my 2 cents :)

---

### Post by howefield on 2011-04-30
Thread moved to "*Ubuntu Testimonials & Experiences*"

---

