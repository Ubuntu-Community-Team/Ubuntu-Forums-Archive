---
title: "Best solution for my 15 year-old laptop ?"
date: 2018-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by milosx72 on 2018-07-08
Hello Ubuntu forums!

I've been using Windows 98 in my childhood when I got my first PC, all the way up to Windows 10, I used every Windows that came out (even Vista, and in my honest opinion it wasn't THAT bad). For 16 years, I had lots of difficulties switching to Linux. I tried installing Linux system countless times before, but I'd switch back to Windows the next day because I was just so used to Windows environment...

[ Specs ]
Intel<3 Celeron M530 1.7GHz
2GB Ram
120 GB HDD
1336x768 ViewSonic Monitor

I had this laptop lying around in my home, and I'm using it to replace my dead PC (to think that a 150 euro power supply would backfire on me, while a 20 euro one worked flawlessly for 5 years...). I'm done with PCs, I'm switching to laptops now. I will replace this laptop in a year or so, since I'm starting software engineering colleague this year, but it should get the job done in the meantime.

A friend of mine who is a hardcore Windows junkie insisted he install me a Windows XP he had on a CD lying around. Using Windows XP after all these years felt good and nostalgic, but man, I had the hardest time finding applications that were written for XP nowadays. Took me 2 days to get the drivers, too... Only thing Windows XP excels at is the boot time.

Next thing I tried, was Ubuntu. I did a minimal install instead of standard, but still the gnome environment is kinda too demanding for this grandpa laptop, felt a little laggy. Then I found out about different flavors, and immediately installed Lubuntu. It's snappy. It's dead simple, and on top of that brings back the Windows 98 days! But I really don't like LXde... LXqt looks marginally better imo, but I had little luck trying to install it on my Lubuntu system. Switching to Xubuntu 2 months later, and I'm kind of happy. XFce actually looks more "today", but Xubuntu has too much bloatware.... All the apps I need are a lite pad, calculator, chrome and atom to write my javascript. Kind of makes me sad that Xubuntu doesn't come with minimal install like Ubuntu does (and Lubuntu's minimal install doesn't even seem to change anything?). If it did, I would never change it!

Also tried different flavors of Manjaro, and Mint but I like Ubuntu the most, so I'll stick with it. I also barely managed to install Arch, but having little experience I just got the LXqt desktop running, and got stuck there.

While I'm happy with the XFce, I still feel it's a big laggy on this machine. LXde runs perfect, so I bet LXqt will too. I don't want to wait for Lubuntu to release the new OS with LXqt. What do you guys recommend? I need a bare-bones system, preferably with LXqt desktop (or maybe some other desktop environment I don't know of yet). I'm still a newb when it comes to Linux. But I love Linux so far. Has a steep learning curve but is actually easier to manage than Windows afterwards, imo.
I was thinking of getting a Macbook as my new laptop, just so I get to try all the systems out there to see what fits best for me, but after these 3 months of using Linux I think I've found my main OS for years to come! I'm glad I poked my nose a little deeper into it, definitely worth it!

Thanks!

---

### Post by bodhin2 on 2018-07-08
sorry - just scanned the post - but you can remove some of the stuff you do not need re: apps - calculator, amazon, and some of the stuff i do not remember that comes with it..  not other misc. stuff - python, et al. synaptic works great to completely remove the said packages.  just do not start removing stuff that is integral to the actual OS and system.  hope this helps.  welcome to ubuntu!

---

### Post by milosx72 on 2018-07-08
I tried uninstalling some software from the store but it always broke my system. I haven't tried doing that through synaptic package management, as I do not fully understand the program yet. Guess I'll give it a try. Thanks for the reply, and warm welcome ^^

---

### Post by oldos2er on 2018-07-08
Please be careful uninstalling packages, and pay attention to any additional dependencies it wants to remove. It's not difficult for someone new to break their system doing this.

---

### Post by bodhin2 on 2018-07-08
I agree. that is why i said to be careful - not trying to send him down a rabbit hole.

synaptic is in the store.  install it from there.  

i am new to ubuntu18.04 but i never messed up the system removing some of the basic stuff as i explained.  same with synaptic.  i do not know what oldos2er and others know but i have been using linux for over a decade or more.  not a CL dude unfortunately.   yes i did break system in the old days when i followed people's helpo with various commands that they too knew enough to be dangerous.  and yes you can remove stuff that will break it big time.  

i removed firfox because i NEVER liked it - put in chromium.  i use thunderbird.  removed rhythmbox.  installled vlc - krtia, gimp etc. update you system too after installing stuff. :-)

---

### Post by wildmanne39 on 2018-07-08
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by kurt18947 on 2018-07-08
This isn't in the *buntu family but I have it running (slowly) on a 2000 vintage 600 Mhz. Celeron and 512 MB. RAM. I'm using this machine as a torrent box and it seems to work well. Q4OS is debian based using the Trinity desktop. (older KDE version fork as I understand it) . It seems pretty lightweight and functional, dunno if it will tickle your fancy but might be worth a look.

---

### Post by Geoffrey_Arndt on 2018-07-09
The key to uninstalling software is to read what the package manager will "remove" in addition to the software you're requesting to uninstall.   If it removes libraries, or other programs, or "anything" that you're not 100% knowledgeable about, then DON'T DO IT!    Just leave it.   Excess programs and libraries will not hurt or even slow down your system to any great extent on Linux.    The update process is what is most affected, not day to day operation of the PC.

---

### Post by milosx72 on 2018-07-11
All right y'all, thanks for the replies. As you all said, I'm new to Linux and very likely to break something if I uninstall some packages (For these 3 months I've re-installed Linux more than 10 times probably, I kind of love to play around and see what different options do). I guess the time will come when I'll be as familiar with Linux as I am with Windows, until then... Well, baby steps hehe. I wont touch anything and stick with Xubuntu for now, and wait until Lubuntu releases a version with LXqt desktop, and make my switch then. When I think about it, most of these apps I thought were bloat are actually settings for the OS itself, and LXde not being very editable (as far as my knowledge of it tells me) lacks most of them.
See you folks around.

@EDIT #1: I was having a >3 minute boot time, that's why I thought that bloatware is holding me back. Instead it was some flip_done timed out warning messages, which I managed to fix by adding some startup options for the Intel HD card, which got my boot time to less than a minute, and I'm very happy with the speed right now

---

### Post by friedchips2 on 2018-07-11
You don't need to switch distros to switch desktop environments. You can choose at login what to load. I would suggest using lightdm and openbox. Lightdm will replace login screen. Openbox is an extremely lightweight window manager. You will have to add things to it to get what you need.

To see how it will work.
```
 sudo apt-get install openbox
```

Then just log out and when loggin back in find and select openbox as your session. Screen will be blank with just a mouse pointer. Right click is where your menu is. Not much to it.

This is what I use and get only what I want. I added cairo-dock and conky. I use feh to load my background. (See attachment)

---

