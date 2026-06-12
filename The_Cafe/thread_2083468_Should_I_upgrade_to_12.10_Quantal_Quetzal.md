---
title: "Should I upgrade to 12.10 Quantal Quetzal?"
date: 2012-11-12
forum: The Cafe
---

### Post by JamesTheAwesomeDude on 2012-11-12
I was just wondering whether it would be a good idea to upgrade to the 12.10 release of Ubuntu. I'm not running anything mission-critical, and I do like to err on the side of new/unstable, but I was wondering what the general opinion is on it. Is is unusably crash-prone? Is it chock-full of new features? I'd kind of like this to be an open-ended discussion about 12.10 in general.

---

### Post by Karlchen on 2012-11-12
Hello, JamesTheAwesomeDude.

Which Ubuntu version are you using currently?
In case the answer is Ubuntu 12.04 then my answer will clearly be: no, do not upgrade. What good reason should there be of giving up Ubuntu 12.04 which offers 5 years' LTS and which is quite stable by now in favour of Ubuntu 12.10 which is just one more short lived interim edition (end of life after 18 months )?

Kind regards,
Karl

---

### Post by Bucky Ball on 2012-11-12
*Thread moved to **Community Cafe***

---

### Post by Mr_JMM on 2012-11-12
I don't have anything "mission critical" either so I'll always (if you're in same boat) say to upgrade, especially as you mention you like to try out the latest.

I personally think it's actually MORE stable than 12.04 especially Unity but ymmv. I also feel that Virtualbox and some other software I use a lot run better.
]If in doubt, create a new partition or image your current set up and revert back.

---

### Post by Jakin on 2012-11-12
For me, i found an upgrade to offer benifits on my laptop. I couldn't get the Quantal kernel to install in 12.04 amd64, and the 3.5 kernel seemed to offer more stability for me, and so far has certainly proved it in my eyes- thus 12.10 was the way to go.

---

### Post by Linuxratty on 2012-11-12
I'm perfectly content with 
 Ubuntu 12.04  and plan just to plod right along with it.

 But if you want to try the latest, have fun.

---

### Post by cwsnyder on 2012-11-12
If you have to ask anyone's opinion, my answer is NO.

---

### Post by drawkcab on 2012-11-12
So far there's been no clear reason for me to upgrade.  12.04 offers me everything I need and PPAs shore up the missing spots.  Of course, I don't use unity.

---

### Post by viperdvman on 2012-11-12
A part of me thinks I should've went ahead and installed Kubuntu 12.04 instead of 12.10, as the only real upgrades are the Linux kernel, X.org server, and KDE Plasma. Linux can easily be upgraded as can KDE Plasma in 12.04.

The main reason I say is because I've found that a few PPA's *(outside of Ubuntu/GNOME/Unity-specific ones)* don't have packages for 12.10... at least yet.

Unless you want bleeding-edge software that PPA's don't quite upgrade nor provide, then I'd say upgrade to 12.10.

---

### Post by Bucky Ball on 2012-11-13
If it ain't broke, don't fix it. Do you have a specific reason? I always have a stable LTS install totally tweaked and customised as my main squeeze (in this case, Xubuntu 12.04 LTS). I need this solid install for study (cos can't afford the time to fix stuff on it mid-semester so xmas break is pretty much it). I also have three other partitions for my 'playthings'. I am in the middle of getting rid of 10.10 and 11.10 to make room for 12.10 and 13.04. Doesn't matter if they break or are in various stages of disarray.

That's what suits me. 

If you have nothing 'mission critical' then it doesn't really matter what you install if you have the time to figure stuff out, tweak, and not necessarily have a stable system.

---

### Post by monkeybrain2012 on 2012-11-13
I don't see any problem using non LTS, however, I would suggest wait at least a month (perhaps 2) before you do so (that applies to LTS as well) because in my experience new Ubuntu releases tend to be buggy and it is better to wait for post release bug fixes before you install.

---

### Post by deadflowr on 2012-11-13
If you got nothing to lose, then I say go for it.
Nothing ventured, nothing gained.
Bug reports don't just fall from the sky, people make 'em happened.(And you can too!!)
If the developers don't know there are problems, then nothing gets fixed.(They're dependent on getting the software on as many system as possible, but they have limited systems. Your system could prove helpful)
If the system is totaled then reinstall 12.04.

---

### Post by Erik1984 on 2012-11-13
LTS stability is relative. If not mission critical just upgrade to QQ and see how it goes. Of course make backups and the like :P

---

### Post by kurt18947 on 2012-11-13
I'm using the gnome-shell remix of 12.10.  I find it appears to have issues with xorg on suspend/resume.  I've only tried it on one machine (AMD AthlonII/Nvidia graphics card) so have limited data.

---

### Post by jrog on 2012-11-13
> **JamesTheAwesomeDude said:**
> I was just wondering whether it would be a good idea to upgrade to the 12.10 release of Ubuntu. I'm not running anything mission-critical, and I do like to err on the side of new/unstable, but I was wondering what the general opinion is on it. Is is unusably crash-prone? Is it chock-full of new features? I'd kind of like this to be an open-ended discussion about 12.10 in general.
I'm assuming that by "Ubuntu" you mean the standard Ubuntu with Unity. If that's right, then, if you use LibreOffice regularly, I would not upgrade to 12.10. LibreOffice is currently buggy in 12.10, to the point of barely being usable in its default state.

---

### Post by monkeybrain2012 on 2012-11-13
> **deadflowr said:**
> If you got nothing to lose, then I say go for it.
Nothing ventured, nothing gained.
Bug reports don't just fall from the sky, people make 'em happened.(And you can too!!)
If the developers don't know there are problems, then nothing gets fixed.(They're dependent on getting the software on as many system as possible, but they have limited systems. Your system could prove helpful)
If the system is totaled then reinstall 12.04.

You can test and file bug reports by installing in a test partition. No need to risk screwing up your working installation. :)

---

### Post by critin on 2012-11-13
Multiple partition and use them all.

---

### Post by Mr_JMM on 2012-11-13
> **critin said:**
> Multiple partition and use them all.

+1 

Anything else is just a waste of sectors!

---

### Post by JamesTheAwesomeDude on 2012-12-29
Wow, it's been intriguing to hear all of the different opinions on this! I've really enjoyed listening to all of the different perspectives.
After hearing about how interesting it can be, I went ahead and took the plunge.

That was probably more frustrating than the time I gave my Windows a Rootkit virus. :frown:

Drivers, GONE. The entire system was so horrifically buggy. [FONT="Courier New"]sudo apt-get install fglrx[/FONT] (to install a graphics driver) completely DESTROYED my system.
I had to use the Root Terminal to back up my files to an external.

Now I know my limits: unstable programs, **stable operating system**.

---

### Post by mJayk on 2012-12-29
> **Bucky Ball said:**
> **If it ain't broke, don't fix it. Do you have a specific reason?**...

 If only I had listened to you years ago lol :) the amount of things I've broken because I thought I'd "Give it a go".

---

### Post by mreq on 2012-12-29
> **mJayk said:**
> If only I had listened to you years ago lol :) the amount of things I've broken because I thought I'd "Give it a go".

+1

btw 12.10 also made my sony vaio unusable so I had to force reinstall the whole thing to 12.04

though I'd like to have gnome shell 3.6...

---

### Post by Alcidious on 2012-12-29
I had problems with my Samsung laptop in 12.04; specifically, my monitor would freeze. This never occurred when I was using 11.10, and I never had the issue using 12.04 on my desktop pc. 

However, my desktop pc is going on three years now, and it was jumpy and buggy.  I backed up all my stuff, and upgraded to 12.10 and now my desktop runs flawlessly! 

But I think I'm going to keep 12.04 on my laptop, since that is where i do most of my schoolwork.  I went through a large hassle reporting bugs (for the first time!!) in the middle of a semester, had some issues with the kernel and screen, and that kinda stank... I learned a lot, but i don't want to do that again with a machine for work. 

If its for play, like my desktop, i say try it out. 12.10 is really nice, from what I've seen of it.

---

### Post by Hylas de Niall on 2012-12-29
> **Bucky Ball said:**
> If it ain't broke, don't fix it.


There it is.

---

### Post by Gremlinzzz on 2012-12-29
:popcorn:If it ain't broke,then break it!
I say if ya want change try Xubuntu.

---

### Post by pqwoerituytrueiwoq on 2012-12-30
> **Gremlinzzz said:**
> :popcorn:If it ain't broke,then break it!
I say if ya want change try Xubuntu.
nothing is more boring that testing and everything just work, *must find something to fix*
*upgrades to 13.04*
*must find issue, before losing mind*

the one thing i need to fix is dust bunnies getting past my dust filters on my computer (i think that is a lost cause)

---

### Post by Bucky Ball on 2012-12-30
> **pqwoerituytrueiwoq said:**
> nothing is more boring that testing and everything just work, *must find something to fix*
*upgrades to 13.04*
*must find issue, before losing mind*

the one thing i need to fix is dust bunnies getting past my dust filters on my computer (i think that is a lost cause)

lol

---

### Post by Welly Wu on 2012-12-30
I upgraded to Ubuntu 12.10 64 bit and I messed it up so I wound up re-installing Ubuntu 12.04.1 64 bit LTS. I found that the stock Linux 3.2.0-x generic kernel to lock up my System76 Lemur Ultra Thin (lemu4) notebook PC because it has the new Intel 3rd Generation "Ivy Bridge" CPU and Intel HD Graphics 4000 integrated GPU. So, I upgraded to the Ubuntu Linux kernel 3.4.0 and it solved my problem.

The latest Ubuntu 12.04.1 64 bit LTS is the only way to go. It's not fun trying to fix broken software especially if you have only one operating system installed bare metal.

LTS may be boring, but it's the safest choice available compared to the interim releases. The interim releases are really dicey depending upon how many updates have been pushed out so you're taking a risk with your user data by upgrading or installing them bare metal especially if you only have one operating system installed on your PC.

I'd say no due to my experience. I was in your boat too and I can relate with you. It's just not worth scratching the itch because it'll bite you in the end.

---

### Post by CodyPy1 on 2012-12-31
An LTS is best to keep. I wouldn't necessarily upgrade if i were you.


Maybe you could test it out and see if you really wanna upgrade? 
Get the Iso and burn it to a disk or a flash drive and bam! Behold Ubuntu 12.10 right at your finger tips.


Although on a personal note. I was really satisfied with 12.10, 12.04 is perfect for what i do.

---

### Post by lancest on 2012-12-31
Having Ubuntu/Debian underneath can be enough.

Linux Mint 14 is a solid option.

Well designed Gnome 3 touches and quite stable on 3 machines.

An open mind about desktop environments can prove useful.

---

