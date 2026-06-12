---
title: "OpenSuSE 10.3 &amp; Ubuntu 7.10"
date: 2007-10-07
forum: Testimonials &amp; Experiences
---

### Post by LuisAugusto on 2007-10-07
[CENTER][B]I'm quite a fan of OpenSuSE, but I am an Ubuntu user too. I decided to install the next Ubuntu release and compare it with OpenSuSE 10.3 (I know it isn't a completely fair comparative).

First OpenSuSE 10.3 (GNOME Edition):[/B][/CENTER]

The installation is more complicated than it should be, and the installer isn't the more user friendly out there, however, it does offer a lot more options than most installers.

The installation asked me If I wanted to add the repos before the installation ( I thought: why I would select no, I learned why a little after), I selected yes and the installers check my internet connection to add those repositories. Then I decided to make a partition for my install, the partition tool is the most user unfriendly thing I have ever use (talking about partitioning tools of course), but it does the work. Then I click install, and, OOPS surprise, adding the repos mean that I had to download 1 GB from them (it didn't ask me that, it just did it, which pissed me out a lot).

Once the installation finished, it reboot, and made me set the usual stuff, like passwords, users accounts, etc. And my hardware, almost everything set up itself, however, the screen resolution was wrong, but changing it was just a matter of select the right one.

The grub screen, it's just beautiful, but, for some rare reason, I didn't have the nice splash while everything was loading, I just saw the cli.

It boots incredibly fast, in less than 40 seconds I was on my desktop.

The default theme is nice, mixing green with blue. I liked a lot the new SLAB menu, it looks well, it works well, and it has the most use applications and tasks just one click away.

Well, then, of course I knew it wouldn't install the ATI graphical driver by default nor the broadcom firmware (until then, only sabayon did it on both cases). So I downloaded the file, and use the bcm43xx tool to enable wireless. Then the ATI driver, I went to the ATI wiki and it had a one click install package (I'll talk about that a little later), so well, I clicked it. The installation went nice so I restarted my X server.

Once I restarted it, my system look like it was working well, so I decided to enable graphical effects (aka compiz), it ask me my password to enable XGL and setting Compiz, I did it, restarted X, and OOPS, surprise again, X server died, and it didn't want to work (I tried to modify xorg.conf, with no success), so I ran: 

```
sudo gnome-xgl-switch --disable
```

To avoid using XGL, it worked again, but, of course, no compiz.

Since, I'm sure,  the problem was with the ATI driver, I removed it, for trying to use the open drivers with aiglx (which I know work with my card), but for some** weird weird reason**, it didn't (again, messed up with xorg.conf without success), for the same** weird reason** it didn't on 10.2

Then I checked the default applications. They're infinitively better selected than Ubuntu ones. Banshee works nice and it burn cd easily, when I tried to play and MP3 file it pointed me to 1 click install, and it worked perfectly, F-Spot import well my camera photos, Brasero works nice, even with audio cd and mp3. OpenOffice opens a lot faster than on **any other distro**, it include, as side from those, the usual GIMP, Pidgin, etc.

Control Center is nice, but YaST is simply godly (and featuring a new gtk front-end), It's the best configuration tool ever made, period. But when it comes to package management the **Gtk** front-end of YaST **sucks **, and it **sucks** a lot, however it's indeed a lot faster than previously releases, the Qt front-end it's a lot better, but I still find synaptic to be better.

This new release feature the, already mentioned, one click install, which is quite nice. Once you selected one of those packages it adds the needly repos, refresh them, and install them. I has the enormous advantages ,over others like services, that it aloud the user to still upgrade, remove and install new packages (from the newly added repo) in the same way he always did. 

OpenSuSE probed that it's quite stable (aside from the ATI thing, it never crash), very responsive and fast, because it's optimized for i586 (and surprisingly lightweight).

[CENTER]So:

**Pros:**

Boots fast.
Powerful installer.
Nice looking overall (subjective).
**Nice selection of applications.**
Sane interface.
Faster than Ubuntu.
Nice menu.
**One click install **
Easy codecs.[B]
Yet Another Setup Tool.[/B]
Stable. 
Fast OpenOffice

**Cons:**

No Live CD mode
It didn't setup my wireless card (but it's just one thing, on one certain hardware, I wouldn't pay to much attentions to this).
The ATI driver doesn't work well (this is one is a little more important)
Aiglx doesn't work for some **weird reason**
It added without asking me 1 GB of downloadable packages during the install.
Complicate installer (for new users I mean).
YaST gtk package management front-end **SUCKS**.
It refresh the repos **every single time** you open the package management tool.[/CENTER] 

[CENTER]


**Ubuntu 7.10.**[/CENTER]

Once I slammed the CD, It boot to Live CD mode, which I personally love, then I clicked on the install icon.

It's a lot simpler and user friendly than OpenSuSE installer, but sadly it doesn't, in any way, aloud you to select which packages to install. Once the (very fast) installation finished it ask me If I want to reboot, and I hit yes.

The grub is an ugly black screen, but it's something irrelevant. The Splash is nice (at least is show me a splash :P), and prompted GDM asking me my user and my password, until desktop, they were around 50 seconds.

The human theme is nice, but the wallpaper is disgusting, I like the 2 bars set up (even if it consumes that much space), and I have always like the bar menu (but it isn't nearly as nice as SLAB), Ubuntu devs added deskbar, which is nice, but I don't personally like the window approach (it use to be different). And it enable compiz by default.

Restricted manager told me that my system need the use of proprietary driver (of course I already knew this feature from Ubuntu 7.04), but I was pleasant surprised when it told me that they were 3 drivers/firmware available, I knew it would tell me about my broadcom card, **but even I didn't know** about the third one, a firmware for my 56 modem (I never use it, and I will never going to, but it stills gave me a good feel) .I selected the 3, and restricted manager installed them nicely.   

I reboot to see if my new ATI driver work, and it did. I installed XGL, and it set up it by itself, I didn't have to make the old xgl entry and startxgl script (I could still use that method if I want to). Wireless worked nice, I didn't test the dial up modem, but since they surprised me, I would give Ubuntu devs my blinded faith.

Now, lets talk about default applications. Rhythmbox isn't bad (it even has a new visualization option), but I found it to be ugly and slow, as in the previous release, it downloaded the necessary codecs alone. Nautilus cd extension is pitiful at the side of Brasero. F-Spot is nice as I already pointed out. OpenOffice is slow on Ubuntu, but I do like it's human icons (since 7.04). It include the usual GIMP, Pidgin, Firefox, etc.

Ubuntu system configuration tools** felt like a toy** at the side of YaST. Ubuntu definitively lacks the existence of real distro specific tools. Synaptic, is another story, it's definitively better than YaST PM, it's faster, it's easier, and it has more packages. Ubuntu add/remove interface is nice, very user friendly.

It doesn't feel as robust as OpenSuSE 10.3, applications sometimes crashed **(rhythmbox won this price)**, and they were 2 or 3 **annoying** bugs, but it's still stable. .

  
[CENTER]**Pros:**

Live CD mode
Friendly Installer
Boots fast
**Synaptic**
Easy Codecs
Add/remove synaptic user friendly interface
Debian based
Did I mention apt?
**Very good hardware recognition **
Fast and responsive
Compiz Fusion!!!!!! :P
This forums

**Cons:**

Too simple installer
**Non powerful configuration tools**
Default Applications selection could be better
Ugly grub boot loader
Disgusting Wallpaper XD
Slow OpenOffice
Doesn't feel that professional


 

**Conclusions**[/CENTER]

One click install is impressive, it's soo easy, however, it doesn't is that good for drivers, not because it failed for me, it's because OpenSuSE doesn't point you to them in any way. YaST is godly as I already said, you won't be needing CLI. Package Management it's better than in previously releases, but Ubuntu it's still better here (a lot better), but the Gtk Front-end it's stupid, what did they thought? I believe they ran out of time. Default applications are good, the interface and the SLAB menu felt very professional and polished, and the overall look is nice.

Ubuntu, on it's side, seems to be easier to set up (thanks to Restricted Drivers Manager), it's easy to deal with. Administrative tools are quite simple, lacking a lot functionality, however, they are easier to follow, you'd probably be using once in once the CLI. Package Management is nice, as always, being debian based has it reward. Default applications are nice overall, excepting music management (very, very important one) and burning tools (which is quite lacking), but you can live with them, or, at least, install new ones easily. The interface isn't bad, however it does take more space than OpenSuSE layout, and it doesn't feel like is making my life easier or faster. The overall look is nice (and even a lot more with Compiz Fusion well integrated, with composite gksu and logout dialogs (is this an ubuntu add-on, or a GNOME 2.22 add-on?), it doesn't feel that professional, but definitively it feels very polished.

Winner: OpenSuSE 10.3 is better than Ubuntu in most aspects, I found it a lot better than Ubuntu for developers and enterprise market. Ubuntu, on it's side, is easier and it has a better package management, probably their only real advantages. OpenSUSE 10.3 is basely better (PM is not that good, but one click install somehow equilibrates it), unless you have an ATI card (or some firmware drivers), OpenSUSE definitively wons.


[SIZE="1"][SIZE="1"]
weird reason = Novell created, developed, and support XGL.[/SIZE][/SIZE]

---

### Post by rfruth on 2007-10-07
openSuse = yack, Ubuntu = APT = big difference IMO - I tried openSuSE not too long ago (ver 10.2) it installed ok but was *so * different i came running back to Ubuntu after a few days ...

---

### Post by misfitpierce on 2007-10-07
I last tried previous version to 10.3 of opensuse and did not like very much whatsoever. I prefer mandriva over opensuse and Ubuntu above all.

---

### Post by sstusick on 2007-10-07
Ubuntu > openSuSE

---

### Post by elvis on 2007-10-07
The one and only thing I prefer about the SuSE installer is the option to authenticate via a remote authentication/directory service at install time (eg: Novell eDirectory, Apple OpenDirectory, Microsoft Active Directory, NIS, YP, OpenLDAP, etc).

This is something lacking from the Ubuntu installer, particularly for business setups.

Other than that, I prefer Ubuntu from head to toe, installer included.  And anything that uses APT as it's package manager is instantly superior to anything RPM/YUM/YAST based.

---

### Post by greymongrey on 2007-10-07
I had major problems with the Ati driver in Suse. After two days I just gave up on it. I then reinstalled Ubuntu and the first thing I thought was WOW, this is so much easier and better.

---

### Post by kiran_aryan on 2007-10-08
**openSUSE 10.3 (1 cd Gnome installation):**
-----------------------------

Pros:

1. Looks great.

2. Boots fast.

3. Decent selection of tools in single CD installation.

4. 1-click install is a good change.

5. Very stable.

Cons:

1. xserver failed upon first boot. I had to edit xorg to use vesa and then install nvidia drivers using 1-click install.

2. System Update from the tray just isn't working. It doesn't tell me whether it finished updating or not. It just hangs with the progress bar moving to and fro infinitely. Damn!

3. YaST looks good in GTK theme but what really annoys me is that it keeps reloading the repositories every single time (and this takes a long time even when I have just 5 or 6 repos added).Even 1-click install is boring because of the same reason!!

4. Inserting a CD or DVD gets me an error - "org.freedesktop.Hal.Device.Volume.PermissionDenied". So, I mount an optical disc manually using mount command.

5. NTFS write support was supposed to be ready with this installation but the win32 partitions were still read only for me. It came with fuse and ntfs-3g installed. So, I had to edit fstab file for the write support.

---

### Post by localj on 2007-10-17
I have been using OpenSuse for a number of years and agree that it is quite a professional distribution.

PROS:
1) YaST - excellent administration tool (no CLI needed). 
2) Nice menu system 
3) Default choice of applications; its pretty close to best of breed.
4) Community repositories now included
5) 1-Click install of codecs etc.

Having said that I found a few things that I expected to be fixed in 10.3.
CONS:
1) Package Management (slow / always refreshes)
2) Compiz-Fusion (even Nvidia has issues, not only ATI)
3) Green scheme is ugly (subjective)

Having said this I also dual boot into Ubuntu and I find myself using Ubuntu 7.10 more that OpenSUSE 10.3 atm. Reasons for Ubuntu 7.10.
1) Package Management (APT rocks)
2) Compiz Fusion worked out of the box
3) Community repositories included
4) Install of codecs / Firefox plugins

CONS: 
1) Administration is a little too basic
2) Default application choice needs to be improved.
3) Menu system wastes too much space
4) Colour scheme of 7.10 is ugly (subjective)

Ubuntu's look and feel bothers me - this is a distro that seems to have gotten Compiz-Fusion to work well out of the box. Given the abilities of Compiz-Fusion the potential to have Ubuntu look amazing (by default) is there. And yet 7.10 looks the same as 7.04 - OMG where is the eye-candy to make all the Vista users green with envy :)
Okay you can add it in but ......

---

### Post by rikis on 2007-10-17
Overall I agree with the pros and the cons and just wanted to share my experience.

My first (real) operating system (in 1998) was Irix 5.x which is the Unix that comes with the Silicon Graphics workstations. And since then I fell in love with unix/linux. Back there the only linux I could get my hands on was a very old red hat distribution and I had a lot of fun with it. As the time went by I got somehow disappointed that most linux distributions started to look windows-like but that is another story.

Well, since I never had enough money to buy my own computer I had to use the ones at school, back in Mexico I was able to use Linux on a regular basis but since I moved to California most of the computers are windows based (except of course the servers). Anyway so I bought a laptop a few months ago and decided to try Ubuntu 7.04. My experience was simply great, I was used to, in order to install even a little program, play around with parameters, figure out dependencies and of course COMPILE the source code. But then I met apt-get and synaptic and I was the happiest linux user in the world. 

Then after reading a few articles on the web I decided to install a tri-boot system with windows xp (since my wife is new to linux) and two linux distros sharing the /home directory. Of course one of the distros was UBUNTU, the other one I decided to go with open SUSE 10.2 ....

Ohhhh... terrible mistake. Granted, it looks more professional but for me that I use some non-standard applications all the happiness was gone each time I either wanted to install or update any application. It use to take hours... and I mean hours just to find out later on that there was a problem with "unresolved dependencies". Anyway after several tries I managed configure SUSE in a decent way and decided to keep it again because I felt my wife would feel it more like windows. 

Then Finally open SUSE 10.3 came out and i decided to give it a try again. Overall is faster but still sucks big time.... I mean, I typed most of these lines while waiting for yast to update one of my programs... and believe my connection is not at all slow.

So summarizing I still like UBUNTU better than SUSE and I will probably reconfigure my laptop to have only UBUNTU and windows. Even though 7.10RC is out I will wait a little bit to get the final version and perhaps then I can post again, of course since apt-get synaptic is faster, do not expect to see a post this long again.

Regards,

P.S. I am also mexican so please excuse if you find something that doesn't make sense.

P.S.S. UBUNTU ROCKS

---

### Post by LuisAugusto on 2007-10-18
Well, that's true. OpenSUSE 10.2 was stupidly slow in Package Management.

OpenSUSE 10.3 made a big step in this, but it's still lacking. But apart from that I find it to be better.

However, I must admit the best release Novell has ever made was SUSE Linux Enterprise Desktop 10, I really hope they make a new one. 

More than 1 year ago, SLED 10 already had an easy way to enable Compiz and XGL, to download proprietary drivers, it included all media codecs, it was very very stable and responsive, it include GNOME Control Center before GNOME folks XD, and it included App Armor, SLAB, etc.

It was, at its moment, the most advanced Linux Distro, and even being that bleeding edge, it was amazingly stable.

---

### Post by mahousaru on 2007-10-18
Nice reviews!  I just want to add my experience of this last 2 weeks.

I decided to nuke my latop and try as many different new distro's as possible before 7.10 came out.  My laptop is notoriously Linux unfriendly as it has a RT2500 wireless card and a VIA PN800 GPU.

I use my lappie for all my dirty stuff, no not naughty pics, but access to the interweb!  So security is a big must

**OpenSuSE**

First I tried OpenSuSE 10.3 and I have to say I was very impressed.  Such improvement over 10.2 (I wish people who like to kick it wouldn't keep using 10.2 ZMD based updater as a brown stick to hit it with).  Had lots of issues with software not being available, but that's to be expected of those who suffer from early adopters disease.  The main thing is its Linux and I compiled nearly everything I needed apart from WASTE P2P which keeps crashing out of the make.  I liked how they are cleaning up their repos, and consolidating guru into packman, big thumbs up there.

I really liked the one click install, that is such a great idea and I've always been impressed with AppArmor.   Since I have all my home directory saved installation was a doddle.  It took it about 1 hr to install and update and about 15 mins for me to have most of my comms apps up.

My laptop worked out of the box.  Wifi straight away and even though it didn't have the OpenChrome drivers to do the fancy stuff VESA is able to let me watch movies full screen.

**Windows XP Home**
OMFG I forgotten what a pain in the **** it is installing XP.  Lucky I have multiple machines so I was able to slurp off the drivers, but with a snd card driver at 25MB it took ages to dl.  Then came Outpost firewall, nod32, avg anti-spyware, system safety monitor, the patches, firefox, thunderbird, OO, and a few IM apps.  That took a good part of 5 hours. Remember security is a must on this box so in the past I was willing to pay for all that stuff.  

Anyway even though I got 2GB memory why does XP like to swap so much for?  I start skype and it is so tinny (a sure sign that the CPU is stressed) and start up a video conference and I hit a brick wall.

All in all, it was horrible experience and I didn't even try to create multiple partitions and have the installer decide to install the D as system as it randomly likes to do sometimes.

That came off after about 30mins of me torturing myself.

**Mandriva 2008**
Installed okay but how restrictive is the partitioner.  At least give me a field to type the size in.  I normally have at least 5 partitions on my box and I'm anal about numbers.  It was a horrible experience trying to slide the bars correctly.  What a naff interface.  Anyways not much to say about the install as its pretty simple.

But boot into the GUI and what is this?  Sound and mouse conflict.  The sound stutters when I move the mouse and the mouse sticks...

It refused to see my wireless network until I hacked away for a while and then when it did see it, it would not bind to it.


**Fedora 7**
Installed fine, I would say the installer is nearly as customisable as OpenSuSE's one, but I didn't like how the partitioner would rearrange my partitions as it liked.  Also didn't like how things such as selecting the GUI was not so obvious.  Had good hopes for using it, but it killed my screen after grub launched.  Tried all the good old apci=off and nosplash etc etc and nothing worked.  Even tried to plug my monitor into the vga port but no good.

Gave up as GG 7.10 was a few hours away

**Ubuntu 7.10**

Well I grabbed the alt iso from the pool just to try it out last night.  I went for the alt because I wanted something that non of the above can do from the installer and that is full disk encryption.  I thought I got a beta so was going to give it a go and then do a proper install today.  So less then 2 hours later I had a fully installed laptop, it took me a little time to work out how to do single sign on with dm-crypt and multiple partitions.   wifi worked straight away.  Immediately impressed with how they have synced the key manager with the login password.

Again like with OpenSuSE I could import all my IM, mail and browser settings in no time and I was up and running happily.  Bonus is I found from the Ubuntu forums that WASTE needs wxGTK 2.6 so that worked.  Truecrypt was a bit of a pain with the need to tar out the source, but it was a pleasure compared to the issues i suffered with the previous 3 OS's.

Been using it for nearly 12 hours and got to say it's a pleasure to use.  Since it has better app support then OpenSuSE and more importantly the full disk encryption I have to rate it higher.

Oh even though this is my first attempt at this installation, I'm really happy with it and since it looks like the ISO i pulled last night is the correct one that is even better.

So for me I rate

Ubuntu 7.10
OpenSuSE 10.3
Windows XP Home (only beats Mandriva coz I could actually connect to the web)
Mandriva 2008
Fedora 7

This is wholly based on my past 2 week experience on my laptop.

---

### Post by khurrum1990 on 2007-10-19
Hi, I have always used both OpenSuse and Ubuntu. OpenSuse used to be my favorite distro till 10.3 came out. It just didn't work on my pc. So I downloaded Ubuntu 7.10 and it works really nice. Both these distros are awesome though, if one doesn't work then the other will.

---

### Post by julian67 on 2007-10-19
LuisAugusto I really like your comparison. It's balanced, objective where it needs to be and subjective where that is more important and makes for a very good read. I agree with pretty much everything you say. I used openSUSE 10.1 and 10.2 before switching to Ubuntu (and then Xubuntu) for various reasons. One of the big ones was the desire to run a distro that can be reliably upgraded from version to version via package manager but unfortunately neither *buntu nor openSUSE are really very reliable in this respect, though at least openSUSE make it clear that they do not officially support this despite providing the facility. I think this is as important a part of any distribution as the more routine administrative tasks, particularly for a distro with a regular 6 month release cycle.

---

### Post by LuisAugusto on 2007-10-20
> **julian67 said:**
> LuisAugusto I really like your comparison. It's balanced, objective where it needs to be and subjective where that is more important and makes for a very good read.

Thank you very much.

> **julian67 said:**
> I agree with pretty much everything you say. I used openSUSE 10.1 and 10.2 before switching to Ubuntu (and then Xubuntu) for various reasons. One of the big ones was the desire to run a distro that can be reliably upgraded from version to version via package manager but unfortunately neither *buntu nor openSUSE are really very reliable in this respect, though at least openSUSE make it clear that they do not officially support this despite providing the facility. I think this is as important a part of any distribution as the more routine administrative tasks, particularly for a distro with a regular 6 month release cycle.

I agree that none have a nice way to upgrade them with PM, but upgrading OpenSUSE with the CD or DVD, at least for me has work nicely.
In Ubuntu, I believe upgrading from the update_manager gives nice results, with some problems, but overall nice (but it works as long as you ONLY upgrade 1 installation, I mean, if you upgrade feisty to gutsy with the Update_Manager, it won't a nice idea to upgrade from Gutsy to Hardy, that's for sure).

---

### Post by generalguy on 2007-10-21
> **khurrum1990 said:**
> Hi, I have always used both OpenSuse and Ubuntu. OpenSuse used to be my favorite distro till 10.3 came out. It just didn't work on my pc. So I downloaded Ubuntu 7.10 and it works really nice. Both these distros are awesome though, if one doesn't work then the other will.


The exactly opposite thing happens with me. openSuse works great out of the box while *ubuntu's graphical installer nearly always fails because of nv, and the text installer is crap. It's a shame because I really like the cleanliness of ubuntu. (Most debian based linuxes fail for me).

---

### Post by Melcar on 2007-10-21
I love OpenSuse.  It's what I use on my main PC.  Mostly because I have had an easier time getting ATI drivers to work than in Ubuntu (although after months of "practice" it all seems simple now).  The only thing I absolutely deplore about Suse is its default package manager; APT is soooo much better.

---

### Post by CulleyS on 2007-10-22
Good comparison.  I tried installing OpenSuse over the weekend as well.  A lot of options in the installer, but very very slow.  I thought maybe it had died a couple of times. :)

Also, once I had it installed, X-server didn't work for me, as another person pointed out.  As I still haven't ironed out the wrinkles with Ubuntu 7.10, I will not pursue OpenSuse at this point.  Don't have the time to get it working correctly.

So far, the best LiveCD and installer I've tested thus far has been Sabayon.  Still, I don't use it much as it doesn't have the features and apps I'm accustomed to.  But, the Live CD environment is the only one I've tested that correctly identified my hardware and needed no restricted drivers to get them working correctly. :)

---

### Post by BOOBOOJS on 2008-04-17
OpenSuSe = 
 - Beautiful polished KDE desktop
 - Lots of options in the installer except an option to setup whole disk encryption
- Close ties to the devlopment of KDE and Linux Kernel
- Slow package manager
- **IDIOT DEAL WITH M$** -- puts a sour taste in my mouth to start off with

Ubuntu =
- Great package manager
- Easy setup via restricted driver manager and (KX)ubuntu-restricted-extras
- Fairly well integrated desktop Ubuntu default theme is **UGLY** 
- **HAS INSTALL TIME ENCRYPTION** I don't need any fancy graphical installer just results

---

### Post by stratavarious on 2008-04-18
.

---

