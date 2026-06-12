---
title: "Linux friendly laptops?"
date: 2005-12-13
forum: The Cafe
---

### Post by Nequeo on 2005-12-13
Greetings Ubunteros,

I'm currently in the market for a new laptop. Mostly I'll be using it for working on my University assignments during lunch-breaks at work, after hours, on the bus, etc.

Was just wondering if anyone here had any good reccomendations for Linux friendly laptops. Ideally tested with Ubuntu. If you happen to live in Australia, and know a place that sells 'em, I'd be interested in hearing about that, too. Or if you live in America and know a place that will ship internationally. Laptops are either ridiculously cheap in America, or ridiculously expensive in Australia!

I'd mostly I'd be compiling stuff. So processor is important. No Celeron's for me, thank you very much! I don't really care about RAM. 256MB should be fine. If Gnome performs poorly with that, I'll just switch to Xfce, or even Fluxbox. I'd like built in - working - wireless and ethernet, and at least a 15" screen. Sound and working hibernation would be a bonus, but aren't necessary. Apart from that, I don't care, and would prefer to save costs by leaving out features if possible.

Any ideas?

---

### Post by 23meg on 2005-12-13
Check these out for a start:

[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by Nequeo on 2005-12-13
Thanks... Those are excellent links to check for Ubuntu compatibility in a laptop. But the question about where to buy laptops without Windows still stands.

I happen to be a reseller for Ingram Micro Australia, as well as several other IT distributers, and none of them stock laptops without Windows pre-installed! 

Cheers,

---

### Post by 23meg on 2005-12-13
In theory (read: EULA) you should be able to give back your unused copy of Windows and get a refund. You might consider talking in advance to your OEM about this and if they do accept the deal, go ahead and buy from them. 

Also check out the [Community Market Place]("http://ubuntuforums.org/forumdisplay.php?f=38") forum here, where laptops preinstalled with Ubuntu are on offer.

---

### Post by ubuntu_demon on 2005-12-13
see also :
[http://www.tuxmobil.org/](http://www.tuxmobil.org/)
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

I'm speaking as a forum user instead of as a staff member. AFAIK if you want a laptop by a big manufacturer HP offers the best Ubuntu compatibility.

[http://www.ubuntulinux.org/support/custom/hplaptops](http://www.ubuntulinux.org/support/custom/hplaptops)
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)

---

### Post by Mr. Electric Wizard on 2005-12-13
I have a HP ze2308wm (wal-mart special) and it works wonderfully with Ubuntu [after some initial tweaking :) ]

---

### Post by yukikimura on 2005-12-24
How did you get the walmart laptop to run with ubuntu. Can you please give me steps to install?
I have the same laptop but the screen just turns black when i try to install.
Thanks in advance.

---

### Post by kaamos on 2005-12-24
Just a guess: try installing with the parameters "linux vga=771"

---

### Post by The Warlock on 2005-12-24
I've heard IBM/Levono is pretty good, but I haven't tried myself.

Oh, and whatever you do, don't buy systems from bargain-basement internet sites like ibuypower.com. They will **** with you on every turn when hardware fails (and it will). Trust me.

---

### Post by Deaf_Head on 2005-12-24
@the warlock .. so will anybody else. There is a reason why dell laptops come so cheap =P

Anyhow, I have an Alienware Area51m (766/5500 model) and everything works perfect .. I ahven't tried playing ut2k4 or anything in ubuntu though .. I use windows for that.

---

### Post by Havoc on 2005-12-24
The ASUS Z71v is powerful, fast, fairly small & light and has a good battery life.Plus, it works GREAT with Ubuntu.
It probably has features you don't need, and a price tag you don't want, but hey! It's a start!

Check [Here]("http://www.notebookreview.com/default.asp?newsID=2346") for a review of the Asus Z71v.

---

### Post by phen on 2005-12-24
HP supports ubuntu on their nc6120 nc6220 nc8xxx etc notebooks. for more info see:
[http://www.ubuntuforums.org/showthread.php?t=35244](http://www.ubuntuforums.org/showthread.php?t=35244)

i use it on one, with breezy installed. it works very well. i like to support hp because of their effort for open source. i've heard that they don't sell these laptops windows-free in the states, though :-(

these laptops are kinda business laptops, nothing for gaming, a little more expensive than others, but they look good, feel good, work well and hp's service is superb. i use it for university and i am satisfied. i dont work for hp :-)

merry christmas!

---

### Post by yukikimura on 2005-12-24
i was able to install unbuntu using linux vga= 776, but for some reason i can't get into x windows.

---

### Post by kaamos on 2005-12-24
[QUOTE=yukikimura]i was able to install unbuntu using linux vga= 776, but for some reason i can't get into x windows.[/QUOTE]

So loading the login screen fails?
When this occurs, press ctrl+alt+F1 (or F2-F6..) and try this command:
```
sudo dpkg-reconfigure xserver-xorg
```
And then:
```
sudo /etc/init.d/gdm restart
```
Hope this gets X running. If not, try the command "startx" and post the errors here. Help will probably be available. :)

---

### Post by infoseeker on 2005-12-24
You should boot straight into the login screen and then Gnome (or KDE, whichever you installed).

---

### Post by yukikimura on 2005-12-24
oops...posted wrong

---

### Post by afhp on 2005-12-24
Running Kubuntu (Hoary, upgraded to Breezy) with no problem on an old Thinkpad T21. Thinkpads are usually well-supported, but you'll definitely want a more recent model. The linux-thinkpad mailing list might be of help :
[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/)

---

### Post by John.Michael.Kane on 2005-12-24
[http://www.linuxcertified.com/linux_laptops.html](http://www.linuxcertified.com/linux_laptops.html)
[http://system76.com/index.php/cPath/1?gclid=COrj-NjGloICFTsuGgodn1hCuQ](http://system76.com/index.php/cPath/1?gclid=COrj-NjGloICFTsuGgodn1hCuQ)
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)
[http://www.emperorlinux.com/](http://www.emperorlinux.com/)

---

### Post by yukikimura on 2005-12-24
i looked at other forums and saw that i could use vesa, tried that out and it worked. I am not working on getting the wireless to work

---

