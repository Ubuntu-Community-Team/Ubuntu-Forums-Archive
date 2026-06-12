---
title: "Ubuntu Linux Is Amazing!"
date: 2006-10-20
forum: Testimonials &amp; Experiences
---

### Post by ebozzz on 2006-10-20
I have not installed as of yet but I am running the *Live* disc right now. I am trying to obtain a copy of Partition Magic so that I can set up a dual-boot system on my existing PCs. Unfortunately, I still need to use some applications due to file sharing concerns that are not supported by Linux. :( If not for that Ubuntu would be my only OS and even after just this brief experience, I feel very confident that I am going to be happy. 

During the past few weeks I have lurked around this forum reading various threads while using the *Live* format. Several of those threads asked why a person would choose Linux over Windows. Already for my needs I can see many advantages to Linux. All of the Windows based tasks that I was regularly performing can be completed in Ubuntu. I even like the Linux based apps a lot. IMO, Linux empowers the end user by providing an OS of excellent quality, useful applications for education, productivity, ecetera, and most of them at no charge! I'm sold. The only thing I can say is, "What took me so long to switch?" :mrgreen:

---

### Post by fatsheep on 2006-10-20
I'm glad you like Ubuntu, welcome to the community. :)  But why use partition magic?  Try [GPARTED LiveCD]("http://gparted.sourceforge.net/livecd.php").

---

### Post by ReaderRat on 2006-10-20
You don't need Partition Magic, gparted is in the installer....or, you can downoad the most current copy @ [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/download.php)

---

### Post by Brownedwg89 on 2006-10-20
If the only reason you are not installing ubuntu is because you want to partition your hdd first, then just go ahead with the installation anyway, because gparted is built into the installer, so you can partition your harddrive how you want it if you click "manually change partition table" during the installation

---

### Post by Delkster on 2006-10-20
Welcome!

> **ebozzz said:**
> I have not installed as of yet but I am running the *Live* disc right now. I am trying to obtain a copy of Partition Magic so that I can set up a dual-boot system on my existing PCs.

The live CD also comes with a partition manager called GParted (found under **System > Administration** in the menu) that allows you to resize existing partitions, and the Ubuntu installer will also allow you to do that.

---

### Post by CatKiller on 2006-10-20
Welcome to the community. As fatsheep says, you don't need Partition Magic. In fact, by default (if I recall correctly) the installer will ask you if you want to resize your existing partition and install Ubuntu in the free space.

Good luck, and have fun.

EDIT: Man, I'm slow. That's what I get for thinking about guitars...

---

### Post by PriceChild on 2006-10-20
*moves to testimonials*

Welcome to the community,

Glad its working out for you :)

---

### Post by ebozzz on 2006-10-20
I forgot to mention one thing. The Ubuntu Community is also great! I can't really say that about the community related to some of the other distros. That's another reason that I became fixated with this OS.

Thanks so much for the partitioning information. Part of the reason that I have not installed is the fact that I wanted to give Ubuntu a good trial before going down that path. I've done that now so it's time to get started. I going to start with my server (Ubuntu Only) then get the two PCs that are in house. Two more desktops are in transit to me and I should receive them next week. 

The funny thing about this whole thing is that I thought that I was going to get all sorts of resistance from my wife and kids. They also got an opportunity get acquainted with Dapper and to my surprise, they are open minded about using Linux. Apps like Kalzium got the kids. My wife just wanted to be comfortable with the productivity suites.

---

### Post by ebozzz on 2006-10-20
> **CatKiller said:**
> EDIT: Man, I'm slow. That's what I get for thinking about guitars...

LOL! I often think about the **low-end** variety of those quite a bit myself. ;) Are you using Ubuntu Studio?

---

### Post by CatKiller on 2006-10-20
> **ebozzz said:**
> LOL! I often think about the **low-end** variety of those quite a bit myself. ;) Are you using Ubuntu Studio?

No, just a normally tweaked Dapper. I'm by inclination an analogue music man - I've done a small amount of computer-based music stuff previously, but I wasn't very good at it and I didn't enjoy it much. Give me some pots to turn, some faders to slide and, ideally, some tape to play with, and I'm as happy as a very happy thing surrounded by stuff that makes it happy.

---

### Post by ebozzz on 2006-10-21
> **CatKiller said:**
> No, just a normally tweaked Dapper. I'm by inclination an analogue music man.

I should have known from your avatar. What I am looking for is putting together & storing my ideas so that I can share them with associates. Recording practice seesions with it would also be nice. Now if I can get this sever install completed installing the desktop OS should be a breeze. I've got issues on the server install.:(

---

### Post by CatKiller on 2006-10-21
> **ebozzz said:**
> I should have known from your avatar. What I am looking for is putting together & storing my ideas so that I can share them with associates. Recording practice seesions with it would also be nice. 

There's quite a bit available, from simple sound recorders and command-line encoders through to extensible multi-track things like Audacity and Ardour.

Given that I can't play keyboard or read music, I was quite pleased to notice a package in Synaptic - songwrite, I think it was called - that lets me put things in as guitar tab and can spit out sheet music, nicely formatted tab and MIDI. That's about my level.

> Now if I can get this sever install completed installing the desktop OS should be a breeze. I've got issues on the server install.:(

I've not done the server install, but if you post your specific problem I'm sure someone will be able to help you.

Good luck.

---

### Post by ebozzz on 2006-10-21
> **CatKiller said:**
> I've not done the server install, but if you post your specific problem I'm sure someone will be able to help you.

I posted two threads in two different forums (Installs & Upgrades and Servers & Security) but I have had any replies as of yet. :( It seems that a few others have had the same or similar issues with the server model that I own, a Dell PowerEdge 2300. 

> Good luck.

Thank you! I'm going to need all of the luck that I can get.

---

### Post by CatKiller on 2006-10-22
I haven't used RAID, or a Dell, or done the server install, but [the Dapper Release Notes]("http://www.ubuntu.com/download/releasenotes/606") say > **Known Issues**

    *If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer.
 Have you tried this?

---

### Post by ebozzz on 2006-10-22
> **CatKiller said:**
> I haven't used RAID, or a Dell, or done the server install, but [the Dapper Release Notes]("http://www.ubuntu.com/download/releasenotes/606") say  Have you tried this?

I have not but all that I am able to use at the moment is the *Live* disc booting from the cd-rom. Are you suggesting that I use that to disable the raid config then proceed with the install? I'm not sure what OS is currently on this server. It takes me to a screen where I have to select for three Linux choices and that's as far as I can go. The security keeps me out. I don't have a need for any of the information. I just want my Ubuntu Server Install completed! ](*,)

---

### Post by CatKiller on 2006-10-22
> **ebozzz said:**
> Are you suggesting that I use that to disable the raid config then proceed with the install?

I'm not suggesting anything: > I haven't used RAID, or a Dell, or done the server install I was just pointing out some instructions that may or may not help. There are some options on the "Install - Boot - Check" menu when you first boot up the cd too. Something there might be helpful. I've not had to use any of it.

---

### Post by ebozzz on 2006-10-22
> **CatKiller said:**
> I'm not suggesting anything:  I was just pointing out some instructions that may or may not help. There are some options on the "Install - Boot - Check" menu when you first boot up the cd too. Something there might be helpful. I've not had to use any of it.

Have you had your nicotine and tea? :mrgreen: ;) 

I finally got some feedback from the Dell forum. I've got to flash my BIOS. We'll see what happens after that. I truly appreciate any suggestions that you or anyone else are kind enough to throw my way. I just want to get this thing running. I will take a look at the ideas that you raised. Thanks!

---

### Post by CatKiller on 2006-10-22
> **ebozzz said:**
> Have you had your nicotine and tea? :mrgreen: ;) 

I'm back on the tea, but I've been cold turkey on the nicotine for about a week. Good luck on getting it installed though - I didn't mean to come across as disinterested, just ignorant :biggrin:

---

### Post by maniacmusician on 2006-10-22
oO i'm an aspiring musician, but i've never been able to record anything. I have a mixer and a tascam 4 track but thats pretty much it. never was able to find any good guides on how to learn complicated equipment, so i havnt bothered with it yet.

a little late, yeah. i've had the page open and the reply typed since yesterday afternoon, probably lol, forgot to hit the post reply button.

---

### Post by CatKiller on 2006-10-22
Oooh, 4-track. Definitely a "get your hands dirty" approach. I'd quite like to play with one of those for a big-ish project to see how flexible my mind really is. If you've ever recorded a song off the radio you can get started with a 4-track, and then the only limit is your imagination. Have fun!

---

