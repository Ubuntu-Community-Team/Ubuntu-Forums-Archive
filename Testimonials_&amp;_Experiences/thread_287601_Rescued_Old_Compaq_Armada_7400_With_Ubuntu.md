---
title: "Rescued Old Compaq Armada 7400 With Ubuntu"
date: 2006-10-29
forum: Testimonials &amp; Experiences
---

### Post by dolphinsonar on 2006-10-29
I recently adopted a broken laptop that was running windows.  It was an old Compaq Armada 7400 with a broken screen.  I cracked open the case and found that the screen was basically just unplugged, but still functioning.  When I plugged it back in it was functional, but the software problems were overwhealming.  Windows was a mess, if you could get it to start, and an error message popped up every three seconds.  Not good.

I tried the Ubuntu live CD but to no avail.  It got stuck on the "booting linux Kernel" screen every time.  Deciding it would not work, I installed Debian, and deleted the windows partition that way.

After having a hard time with Debian (because I am a noob) and not being able to find the right answers to the hardware configuration questions that Debian was asking me, I decided to try the Ubuntu live CD again, mostly out of frustration.

For some reason after deleting the windows partitian the Ubuntu live CD started up.  It didn't work before, but now after installing Debian the live cd boots.

Go figure.  I installed Ubuntu, deleted the Debian partitian and now the laptop is peachy.  Thanks Ubuntu.

---

### Post by bodycoach2 on 2006-10-30
Just looked at a few specs about that computer. You got a PII laptop working with not much problems, it sounds like.

I'd suggest putting Xubuntu on that one. Use the install CD, instead of the LiveCD. Xubuntu would run much faster.

---

### Post by dolphinsonar on 2006-10-30
Actually, you hit the nail on the head.

After much frustration that is exactly what I did, I installed the Xubuntu "alternate" install CD, which requires much less RAM.

That old thing is humming now.

---

### Post by Dr. C on 2006-10-31
I have found that Ubuntu Edgy runs very well on old Laptops. I recently installed it on a Toshiba Satellite 2590 CDT, with a 400 Mhz Celeron CPU, 192 MB of RAM and 2.5 MB Video. I used the alternate CD to install. 

The user memory for the OS on boot is in the 80 - 90 MB range.

---

### Post by Blaise Vigilante on 2007-03-26
Hi,  I need some help.  
I am an extreme novice when it comes to unix, so I am pretty surprised that I was able to actually get ubuntu loaded on my Compaq Armada 7400 laptop.  It seems that everything is working except the sound.  
I have no idea how to troubleshoot this since I am a windows person.  I believe that the card is the ESS 1868.  I would have to check the web again to make sure.
How did you get the sound to work on your 7400????

Thanks for the help...

---

### Post by aldo.mateos on 2008-02-17
Hi. You should install linux-backports-modules-generic.

---

### Post by dartrunner on 2008-04-10
The linux-backports-modules-generic is not in Add/Remove... on Xubuntu and if I try to open a terminal the computer goes to the login screen.

Also the login screen is at a higher resolution than the screen supports and I can't see the bottom or right side of the screen. I was able to change the resolution of the desktop, good thing the menu buttons are on the top left.  : )

Any hints would be appreciated.

Bob

---

### Post by tracyapotter on 2008-05-29
I have been using an old Armada 7400 for the last 3 years with Ubuntu

My sound card is an es1688 and to make it work:

kdesu kate /etc/modules  (root edit the modules file)

add "snd-es1688" (sub snd-es18xx for your card)

(make sure to add a blank line under this entry)

save file and restart



Which version did you use?  I have been having problems getting my video to work on fresh installs past 7.04 Fiesty Fawn.  7.10 changed the xorg and I have yet to be able to get anything besides a text login.

Other than that I have 256M (max for 7400) and can get OpenOffice to open in about 30-40 seconds.  I am satisfied and will run it until it dies.

---

### Post by wolfen69 on 2008-05-29
you should try [PuppyLinux]("http://www.puppylinux.org/") it would probably be lightning fast. it even runs pretty fast on my 10 yr old clunker. it couldnt hurt to try the live cd. you should never limit yourself as far as what OS to use. especially on old computers. i went through 5 different os's before i settled on puppy. that's the key, to match the os to the hardware. that being said, there are many lightweight distros to try. that's the beauty of the live cd.

---

### Post by Xertz on 2008-08-24
> **tracyapotter said:**
> I have been using an old Armada 7400 for the last 3 years with Ubuntu

Which version did you use?  I have been having problems getting my video to work on fresh installs past 7.04 Fiesty Fawn.  7.10 changed the xorg and I have yet to be able to get anything besides a text login.

Other than that I have 256M (max for 7400) and can get OpenOffice to open in about 30-40 seconds.  I am satisfied and will run it until it dies.

I have 3 months since i got the armada 7400, first i tried to install Ubuntu 7.10 Live DVD (the laptop came with dvd rom), but the dvd rom doesn't read any dvd at all. Then i google for help, where i end up im the ubuntu forums. Like bodycoach2 post i try to install xubuntu but it seems that are some issues with xfce4, so thats when i install puppy linux dingo 4.x. I whas testing it for 3 weeks but the sound didn't work and its apear that there's no driver for D-Link DWA-110 wireless g usb adapter yet (like ubuntu have), but at least puppy have geany already installed, and i really need a laptop with IDE compiler software and wireless connection.

So then i found Knoppix, runs perfect like puppy but with better graph and more stuff's (of course no sound).. but got some problems with root access (it wont even let me get root permision via Sudo)... and that was the end of Knoppix.

Now and running Ubuntu 6.04 with sound and wireless connection, BUT i can't get connection with the main server of ubuntu, is like ubuntu headquarters is no longer tanking care of Dapper Drake any more.

So tracyapotter what distro are you using? any suggestion?.

Anyone is welcome to help me :)

---

### Post by Crafty Kisses on 2008-08-25
Use DSL it works perfect.

---

