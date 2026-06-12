---
title: "Simple (?) Newby questions - sound &amp; security"
date: 2008-08-15
forum: Virtualisation
---

### Post by himagain on 2008-08-15
Peace!
I have Ubuntu8 running Vboxed  XP. 
1. Lotsa people seemed to be able to get sound to work with odd solutions here. But, I've tried them all and still no sound. 
Not hardware 'cos if I boot my XP alternative, all is well. 
Even the fabulous Xara Xtreme (now a freebie donated to Lux - thanks!) runs beautifully.  No video problems except for ...... no audio. 

SECURITY
What scenario could allow a nasty into my system if running XP in a box?
If I d/l a program inside the box - it will only run in that box, right? 
But the moment I t/fer it outside the Vbox I'd better have a good A/virus, right?
So at worst I might have to back up one snapshot?  
(BTW: Being paranoid - I have 16 Snapshots currently. How do I safely remove 14 of them ?) :)

Thanks for ANY  advice,

---

### Post by jualin on 2008-08-15
If you are runnning XP on a Virtual Box there is no way that a virus that you get using XP will infect your Ubuntu machine since by default Virtual Machines (guests) do not communicate with the Hosts (Your Ubuntu machine). If you still want more security consider installing an antivirus for Linux such as ClamAV. Good luck!

---

### Post by himagain on 2008-08-19
> **jualin said:**
> If you are runnning XP on a Virtual Box there is no way that a virus that you get using XP will infect your Ubuntu machine since by default Virtual Machines (guests) do not communicate with the Hosts (Your Ubuntu machine). If you still want more security consider installing an antivirus for Linux such as ClamAV. Good luck!

Hi Jualin,
As I "understood" it, even if you get a virus, the shutdown of the Guest is supposed to kill it. 
But I guess if you d/l  warez and execute later, it should still only total THAT guest copy right? 

Cheers!
(Still trying to figure out how to install a legitimate download in Lux outside the lovely Synaptic, so it shows up on the menus.)

---

### Post by jualin on 2008-08-22
> **himagain said:**
> Hi Jualin,
As I "understood" it, even if you get a virus, the shutdown of the Guest is supposed to kill it. 
But I guess if you d/l  warez and execute later, it should still only total THAT guest copy right? 

Cheers!
(Still trying to figure out how to install a legitimate download in Lux outside the lovely Synaptic, so it shows up on the menus.)

Sounds like you understood correctly. The Guest (Windows) has no communication with the Host (Ubuntu), therefore the virus cannot be transmitted. And for the installing a program that is not in Synaptic you have two choices. You can download a .deb package which installs by double clicking on it (this one should appear on the menus). The other choice is to install a package from source (not a pre-compiled deb package), for that follow [this pretty helpful guide.]("www.monkeyblog.org/ubuntu/installing") Good luck

---

### Post by himagain on 2008-09-01
Hi Jualin,
Thanks for the reply, but the url bounced :-(

---

### Post by jualin on 2008-09-01
> **himagain said:**
> Hi Jualin,
Thanks for the reply, but the url bounced :-(

Apparently the site is down. Try the [Google Cache Link]("http://209.85.215.104/search?q=cache:IfbspYjsGWIJ:www.monkeyblog.org/ubuntu/installing.html+ubuntu+install+anything&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a"), maybe it will work. If not you can run a search in Google for "How to install anything in Ubuntu" and use the "Cached" option from there. Good luck

---

### Post by himagain on 2008-09-03
Hi jualin,
Thanks again, but the only critical info I need is not in the cached list - just a 404.. :-(
It's funny how difficult it is to find out and do such a basically simple thing! 
I've got all the Sound Driver bits from ASUS, just cannot find out how to install them outside of Synaptic! 
Tried doing it from the DBS (Dreaded Black Screen) - just fails with obscure messages ... as usual. 

Cheers!

---

### Post by jualin on 2008-09-03
ok let me see if i can help you install it. What is the name of the file you are trying to install, and what is the extension (bin,sh)?

---

