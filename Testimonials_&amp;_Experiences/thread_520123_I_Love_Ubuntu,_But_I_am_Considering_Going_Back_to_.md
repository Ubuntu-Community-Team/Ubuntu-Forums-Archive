---
title: "I Love Ubuntu, But I am Considering Going Back to Windows and Here Is Why....."
date: 2007-08-07
forum: Testimonials &amp; Experiences
---

### Post by Xomphos on 2007-08-07
Hi!

     Over the past two to three years, I have been expeirimenting with various distrobutions of Linux. My favorite, is the same as most people's, Ubuntu. Both of my computers are "hand-me-downs" from family members. My desktop computer is an HP Pavilion 750n with the following specs:
-1.8gHz Intel Pentium 4
-80GB HDD
-30GB HDD
-512mb Ram
-GeForce 4 Graphics Card (with 64mb ram)
While my Dell Inspiron 4150 laptop has:
-1.6gHz Intel Pentium 4 M 
-30GB HDD
-256mb Ram
-ATI Radeon Mobility 7500 (with 16mb ram)
     Recently, I decided to try and install Ubuntu 7.04 on my laptop and get it working. Over the past year or so, I have tried Linux off and on on my laptop and desktop trying to get it to work, but the problems have always come down to wireless. Thanks to the forum members, I finally have my laptop's wireless card working along with my graphics card. Now, I am experiencing Linux and moving forword without trying to solve problems-or at least that is what I thought I would be doing. 
     First off, sleep mode doesn't seem to work as I have to do a cold-reboot to get it to come out of a blank-screen state from waking from sleep mode. Secondly, I have installed several programs, including Real Player 10, and I have tried removing these and I find myself searching all around and spending *hours* uninstalling these programs (I still haven't even gotten Real Player 10 uninstalled). Additionally, I was surprised at the work it took to get my graphics card running. Once I did though, however, I can't seem to run Desktop Effects without it bugging up or some other compositor (I haven't really tried Beryl though yet). I find this unsatisfactory when I could do stuff in Windows remotely like that, but not specifically. Also for instance, I, personally love desktop customization. I downloaded that Mac-like bar to use, but couldn't use it because I didn't have a compositor running. Lo, and behold, the default compiz or whatever it is won't run on my machine. Overall, contradictory to what I believed and heard earlier, I find myself doing more work for my computer than it is doing for me. 
     However, those were just the faults I have found. Ubuntu seems to make my laptop run great. I experience a slightly faster boot and load times. Also, the system seems to run much cleaner than Windows rather than having to access the hard drive all the time due to virus scans and firewalls. I also absolutly love the package manager. Adding and removing (most) programs is a snap and is fun and enjoyable compared to Windows. However, some programs, such as commerical ones can be a pain to install and remove. Additionally, I think something else I noticed was battery life seemed better. Rather than under an hour, I believe I am getting around an hour and a half of battery life. 
     Overall, I love Ubuntu and want to like it and continue using it. But I find that I am to stressed trying to figure things out and using this operating system. I like it though, but I just wish it would "just work." I am installing Ubuntu 7.04 as a dual-boot on my desktop right now through Wubi to see if I can get my broadcom wireless card working now since my laptop used the broadcom chipset and I got that working with the help of forum members. That way I can see the improvement (if any) my graphics card brings to Desktop Effects. However, after I am done testing, I believe I might be making the switch on my laptop back to Windows.

Comments? :D

---

### Post by loell on 2007-08-07
yeah, just dual boot, you can always come back anytime to see the improvements :)  if ever your going back in xp , till then :)

---

### Post by macogw on 2007-08-07
Are you using ATI's proprietary drivers instead of the open source vesa (if you have 3D, that'd be "yes").  ATI's proprietary drivers don't work well and mess up the power management.  You have to set the ATI driver to unload when hibernating and suspending.

Real Player 10's package is just called "realplay" and should be visible in Synaptic.

So back to the part about "ATI's proprietary drivers don't work well"... ATI has given Linux the short end of the stick for ages.  Dell (since the Ubuntu deal) has told them they'd better shape up, so at the last Red Hat Conference, they promised us better (which, given how poor the current ones are, that should just be read as "working") drivers...possibly even open source ones.  Remember, since you're using their binary blobs, we're not responsible for how crappy they are.  Ubuntu's developers can fix bugs in open source drivers just fine.  Those are closed source, though, so if ATI sucks, we can't help it.  By the way, ATI's Windows drivers are pieces of s*** too.

---

### Post by aysiu on 2007-08-07
Here's my comment: If XP is working for you without trouble, then use it. If you want to use Ubuntu in the future, wait until you are ready to buy a new computer. When you do, buy one with Ubuntu preinstalled on it. Or, start slowly replacing your incompatible parts with compatible ones. (Sell the incompatible ones; buy compatible ones.)

---

### Post by Xomphos on 2007-08-07
> **macogw said:**
> Are you using ATI's proprietary drivers instead of the open source vesa (if you have 3D, that'd be "yes").  ATI's proprietary drivers don't work well and mess up the power management.  You have to set the ATI driver to unload when hibernating and suspending.

Real Player 10's package is just called "realplay" and should be visible in Synaptic.

So back to the part about "ATI's proprietary drivers don't work well"... ATI has given Linux the short end of the stick for ages.  Dell (since the Ubuntu deal) has told them they'd better shape up, so at the last Red Hat Conference, they promised us better (which, given how poor the current ones are, that should just be read as "working") drivers...possibly even open source ones.  Remember, since you're using their binary blobs, we're not responsible for how crappy they are.  Ubuntu's developers can fix bugs in open source drivers just fine.  Those are closed source, though, so if ATI sucks, we can't help it.  By the way, ATI's Windows drivers are pieces of s*** too.

With the graphics card, I had to create a cust xorg.conf file. For RealPlayer 10, I used the Bin installer, which I later found out has apparently no uninstaller and I also installed it in the default directory-my Home directory.

I also tried:
> 
sudo apt-get remove realplay(er)

No luck.

---

### Post by wolfen69 on 2007-08-08
it's a mindset, if windows still gets it hard..... go for it. youve been bitten by commercialism. keep strokin bill. no big deal.

---

### Post by 3rdalbum on 2007-08-08
> **Xomphos said:**
> With the graphics card, I had to create a cust xorg.conf file. For RealPlayer 10, I used the Bin installer, which I later found out has apparently no uninstaller and I also installed it in the default directory-my Home directory.

I also tried:

sudo apt-get remove realplay

No luck.

Apt-get only removes things that have been installed through the Apt or dpkg systems (so, only stuff that came as a .deb file).

If you installed Realplayer just into your home directory, then you can remove it by deleting the files it put into your home directory. A fairly simple task once you actually try it.

---

### Post by Alareiks on 2007-08-08
Free software isn't a faith, it's just software. Great software, with a great philosophy behind.
All it takes is a reasonable effort at the beginning, that's all.

Hope you will remain with us, otherwise all I can say is *good luck* ):P

---

### Post by olejorgen on 2007-08-08
Yeah, lack of standby/suspend to ram drove me away from ubuntu on my laptop too. To be fair, I think this mostly an issue with buggy hardware acpi support (?)

---

### Post by wolfen69 on 2007-08-08
> **olejorgen said:**
> Yeah, **lack of standby/suspend to ram** drove me away from ubuntu on my laptop too. To be fair, I think this mostly an issue with buggy hardware acpi support (?)

you make it sound like it doesnt work for anybody. i have yet to have an issue with it. it doesnt work for **YOUR** computer. if people would put linux on compatible hardware, there wouldnt be this discussion. the average person DESERVES windows.

---

### Post by olejorgen on 2007-08-08
Sorry, I should've made that clearer.In my case I hadn't really any choice. I wanted a tablet pc with screensize > 12" and then Toshiba M7 was the only option. (well, I think it was an acer 13" too)

---

