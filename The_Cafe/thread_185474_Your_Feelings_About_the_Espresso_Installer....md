---
title: "Your Feelings About the Espresso Installer..."
date: 2006-05-31
forum: The Cafe
---

### Post by user1397 on 2006-05-31
What do you guys think about the espresso installer?  I enjoyed it very much;  I certainly like it a lot better than the 5.10 text-mode installer (which btw deleted my windows partition!  Argh! Oh well, my mistake!).

I was especially pleased with the partitioning part of it.  It seemed a lot easier to understand it *graphically*.

---

### Post by bruce89 on 2006-05-31
They call it Ubiquity now.

---

### Post by user1397 on 2006-05-31
[quote=bruce89]They call it Ubiquity now.[/quote]Really? When did that happen?!

---

### Post by gingermark on 2006-05-31
To be honest, I would have been just as happy using the old-style installer. But I guess it's cool to surf the web while your OS is installing.

---

### Post by Personatech on 2006-05-31
I liked its ease of use but I didn't like the fact that when Flight 6 was released it didn't install GRUB properly, resulting in a non-bootable machine.  I reinstalled using the text installer and everything went fine and I haven't tried it since.

---

### Post by Jucato on 2006-05-31
Basing on my Kubuntu Desktop CD experience (haven't downloaded the Ubuntu RC), I like the Ubiquity/Espresso installer very much (I would have preferred Espresso since it's coffee related, and is very much the theme of the forums, but I guess UBiquity is closer to UBuntu). I like the fact that it takes the settings that you've configured while running the Desktop CD and uses those for installation, so you only have to setup your hardware/preferences once. It's also our first GUI installer and should help newbies to Linux in partitioning.

One thing I don't like about it, though, is that it doesn't ask where to put GRUB. It just assumes and installs itself in the MBR of hda1. Though an option that's really good for beginners (who might not want to tackle with the concepts of MBR), I just wished it offered other options.

That said, I really think it's a great step forward for Ubuntu.

---

### Post by Rackerz on 2006-05-31
Yep, it was good for me. I only found out about it by accident when I downloaded the livecd by mistake. It's a good installer and I really like it! Except in Flight7 when it was slightly broken.

---

### Post by asimon on 2006-05-31
As I make heavy use of LVM and raid I couldn't use the new installer at all but I think it will be very appealing once it gets more powerful.

---

### Post by NeoChaosX on 2006-05-31
Ubiquity works just fine for me. The only thing that bugs me is why the Kubuntu version doesn't offer a ResierFS option in the partitioning tool (though I don't mind using ext3), otherwise it works great. Love the simpilicity of the install process, and the speed of install - no longer have to wait an hour for all the packages to be copied and installed!

Now only if NetworkManager were to be included on the CD like with Ubuntu, I'd probably never have to switch to another distro again. :cool:

---

### Post by Jucato on 2006-05-31
Btw, the Ubiquity installer is just meant for a really very basic desktop install, using the settings you used (ok, that's a bit redundant) on the Desktop CD. I'm not sure it handles configurations for LVM and raid, and other stuff. Probably same reason why choosing where to put GRUB isn't included.

The Alternate install CD (text-based) contains more bells and whistles for the more experienced.

---

### Post by Sammi on 2006-05-31
> Now only if NetworkManager were to be included on the CD like with Ubuntu, I'd probably never have to switch to another distro again.

Is'nt it on the CD, but not installed by default??

---

### Post by aysiu on 2006-05-31
The more graphical point-and-click applications we have, the less people will complain, so I like the Espresso Installer.

On computers with 128 MB of RAM or less, it's *painfully* slow, though, so I'm glad the alternate install CD still exists.

---

### Post by NeoChaosX on 2006-05-31
[QUOTE=Sammi]Is'nt it on the CD, but not installed by default??[/QUOTE]
It's on the Ubuntu CD, but not the Kubuntu CD.

---

### Post by xXx 0wn3d xXx on 2006-05-31
I haven't used the live-cd installer yet because I heard that alot of people are having problems with it. It's nice that the live cd and install options are in one but I would much rather use the regular text-based install method. I am hoping to use the live cd after dapper becomes stable.

---

### Post by user1397 on 2006-05-31
The number one reason i liked the espresso/ubiquity installer, was the partitioning tool, since it perfectly met my needs 
160 GB hard drive
Partition 1: / ext 3 15GB
Partition 2: /home ext 3 133GB
Partition 3: swap 1GB
(thanks aysiu for the recommendation of partition sizes)

 The number 2 reason is the speed of it: it took me like 10-15 minutes to install it, no joke, while the text-mode breezy install took me more than an hour!

---

### Post by Ubunted on 2006-05-31
I love it. I don't think I'm ever going back to the old installer for primary installation. It's slicker and even seems faster.

---

### Post by vayu on 2006-06-01
I wish I could be positive, but I really don't like it.  First it is slow, other Live CDs are not anywhere near that bad on the same computer.  It would not partition my drive, I had to use the live gparted CD (which not only worked but was light years faster).  It assumed I was using DHCP and left me to figure out how to get my network up.  It just went ahead and installed grub without even asking.  From what I've read I better not attempt to try it on my machines that have FreeBSD partitions on it.

My next install is going to use the text installer.  Hopefully they will always have that option.

---

### Post by bluenova on 2006-06-01
[QUOTE=aysiu]On computers with 128 MB of RAM or less, it's *painfully* slow, though, so I'm glad the alternate install CD still exists.[/QUOTE]
Also it can't be installed with a resolution of less than 1024x768. At 800x600 you can't see the Back <> Forward buttons to work through the install and you can't resize the window to view them either. This is very bad, especially for Xubuntu which is designed for older systems. The installer should be able to work on any system that the end product can run on.

---

### Post by vayu on 2006-06-01
[QUOTE=erik1397]The number one reason i liked the espresso/ubiquity installer, was the partitioning tool, since it perfectly met my needs 
160 GB hard drive
Partition 1: / ext 3 15GB
Partition 2: /home ext 3 133GB
Partition 3: swap 1GB
(thanks aysiu for the recommendation of partition sizes)

 The number 2 reason is the speed of it: it took me like 10-15 minutes to install it, no joke, while the text-mode breezy install took me more than an hour![/QUOTE]


It's funny how people's experience can be so different.  I spent well over an hour trying to get it to partition my drive and ended up having to use gparted.  And then when you take the lack of helping me set up my static ip network into account,  I spent more than half a day getting Dapper installed.

---

### Post by awakatanka on 2006-06-01
Mixed feelings, the livecd is slow compared to other livecd's, Can't choose reiserfs. Grub install methode bothers me to. 

The goodthing i can use my wireless now on my laptop with textbase it didn't work.

But installation is going abit faster now, but it doesn't offer me the same things as textbase.

---

### Post by garba on 2006-06-01
Simply put: I love it, it's one of the coolest features ever, it really showcases what gnu/linux is capable of. Of course there's still some room for improvement, but I am happy it will be the default way to install ubuntu in the future. So cool: you can testdrive your new os without needing to install it first, you can install it in under than 10 minutes, and you can tend to your pc tasks as the installer does its thing. Great.

---

### Post by Klaidas on 2006-06-01
Well, the espresso installer is  VERY VERY cool :cool:  I liked it very much: it was pretty fast, detected my windows partition, it understood that I dont want to format hda1 and hda2, only reformat hda3 and mount it on / and hda4 as swap.
It set up a grub and I can still dual boot! WOOT woot! :)

---

### Post by JSchwage on 2006-06-01
[QUOTE=bluenova]Also it can't be installed with a resolution of less than 1024x768. At 800x600 you can't see the Back <> Forward buttons to work through the install and you can't resize the window to view them either. This is very bad, especially for Xubuntu which is designed for older systems. The installer should be able to work on any system that the end product can run on.[/QUOTE]
My old laptop uses 800x600 and I was able to install Dapper using Ubiquity. All you have to do is click the icon in the top left of the window and select "Move". Then you can move the window up a bit so you can use the Back and Forward buttons. Although you may not be able to see some of the top of the window.

This was my only complaint with Ubiquity so far. I enjoyed it much more than the previous installer.

---

### Post by bluenova on 2006-06-02
[QUOTE=JSchwage]My old laptop uses 800x600 and I was able to install Dapper using Ubiquity. All you have to do is click the icon in the top left of the window and select "Move". Then you can move the window up a bit so you can use the Back and Forward buttons. Although you may not be able to see some of the top of the window.

This was my only complaint with Ubiquity so far. I enjoyed it much more than the previous installer.[/QUOTE]
hmm, I didn't see that, I did look for a move button, but my point is it shouldn't be nessasery.
The dev's can't say, 'here we have this great operating system XUbuntu for running on your old boxes, but if you want to install it you're gonna have to move some windows around to see all the buttons and text.'

---

### Post by lapsey on 2006-06-02
it's absolutely brilliant for new users and installing via a live cd is a really great idea.

---

### Post by Christmas on 2006-06-02
It's just great. I've never thought of this wonderful idea, to install from the live CD. I burned the Desktop CD, then booted and chose to install to hard disk. It booted the Live CD and I was with Dapper's desktop in front of my eyes, so I'm asking myself "hey, I wanted to install it, not to see the system" but then I noticed the Install icon on the desktop and installed it from there. Very, very nice.

---

### Post by prizrak on 2006-06-02
The installer is pretty nice but I did prefer the text mode partition program it was much easier to use. Gparted is too much of a wizard for me, makes it harder to use.

---

### Post by aysiu on 2006-06-02
[QUOTE=Christmas]It's just great. I've never thought of this wonderful idea, to install from the live CD.[/QUOTE] This is new to Ubuntu, but PCLinuxOS and Mepis have had this feature for quite a while.

---

### Post by Sushi on 2006-06-07
I love the idea behind the installer. Installing the OS, and using the OS at the same time? Fantastic! If only it worked for me. Every time I try to install Dapper with the installer, it starts out fine, then, at some point during the installation, the installer simply vanishes. One second it's there, the next, it's gone.

---

### Post by ssam on 2006-06-07
i think its a good thing.

the current limitations should be worked out by the edgy release. i also expect that it can become a bit more robust. there was also talk about it displaying an animated introduction to ubuntu as it installed.

---

### Post by Kobalt on 2006-06-07
The installer just worked like a charm with me... so I think it's great. Developpers should really work on it, if it still have some fixes to be done, so that Edgy would come with the smoothest Espresso ever ;)

---

### Post by frodon on 2006-06-07
I had a wonderful experience with it, it's so sweet to navigate on internet during the install, so congratulations to the expresso devellopers =D>

---

### Post by mips on 2006-06-07
I had a horrible experience with it. qtparted did not work, grub was never installed.

The alternate install cd worked flawlessly though.

---

### Post by Jucato on 2006-06-07
I made a completely fresh reinstall (after a disastrous dist-upgrading last week) using the Desktop CD. Everything worked very well. I guess the outcomes of each install depends on so many factors, that's why we're having so many different experiences.

Btw, I can't remember exactly what happened during the installation. But the first time I made a test install of Dapper, I was connected to the internet. This time, however, I installed without an internet connection and it complained about not being able to reach the repositories. It also disabled all repositories in sources.list on the installed system.

My question: What is it trying to do by accessing the repositories during the installation? Is it trying to download some packages?

---

### Post by gray-squirrel on 2006-06-07
> **Fenyx]I made a completely fresh reinstall (after a disastrous dist-upgrading last week) using the Desktop CD. Everything worked very well. I guess the outcomes of each install depends on so many factors, that's why we're having so many different experiences.[/quote]

I was worried about it myself, because of all the posts of difficulties, etc. during and after installation from the Desktop CD.  But, I don't have Windows NT/XP or any SATA devices installed, so I really had to try it out, just in case there were other problems which had not been discovered yet.

Fortunately, there were only two or three small issues after Dapper was installed said:**
> 
Btw, I can't remember exactly what happened during the installation. But the first time I made a test install of Dapper, I was connected to the internet. This time, however, I installed without an internet connection and it complained about not being able to reach the repositories. It also disabled all repositories in sources.list on the installed system.

My question: What is it trying to do by accessing the repositories during the installation? Is it trying to download some packages?

Strange, I've installed previous versions without having an Internet connection, but never had to worry about disabled access to repositories.  I have only two guesses as to the need for access to the repositories during installation: (a) to provide an updated list of packages available, or (b) to make sure updated packages were being installed.

This is interesting indeed.  And the installer never complained about not having an Internet connection when I installed.  I thought everything was fine until I went into sources.list to edit a line or two to get access to the backports.  After opening the file, I found out that almost all of the lines were commented out, because the installer did not have access to an Internet connection during installation.

---

### Post by dada1958 on 2006-06-07
The idea is nice but I'm using the text based installer with more success.

---

### Post by Jucato on 2006-06-07
[QUOTE=gray-squirrel]Strange, I've installed previous versions without having an Internet connection, but never had to worry about disabled access to repositories.  I have only two guesses as to the need for access to the repositories during installation: (a) to provide an updated list of packages available, or (b) to make sure updated packages were being installed.

This is interesting indeed.  And the installer never complained about not having an Internet connection when I installed.  I thought everything was fine until I went into sources.list to edit a line or two to get access to the backports.  After opening the file, I found out that almost all of the lines were commented out, because the installer did not have access to an Internet connection during installation.[/QUOTE]

Yeah, Breezy's installer doesn't check for internet connection, AFAIK. Actually the installer didn't really complain about having no internet connection. It just complained that it couldn't reach (couldn't stat, I think) the repositories or [http://archive.ubuntu.com](http://archive.ubuntu.com) or something like that. Didn't really take note of the error message because I didn't think, at that time, that it would make any difference. Only when I opened my sources.list did I realize it.

Compare it to my previous Dapper RC install (also using the Desktop CD), this time with an internet connection. Not only did I not encounter an error message like that, but also the main and restricted repositories have been enabled in sources.list.

This is a very strange behavior for an installer.

---

### Post by Arktis on 2006-06-07
The first time I used it, the partitioner would always stall and lock the computer up at 7% of loading.  It turned out this was because the cd had a burn error or something (the image I downloaded checked out fine, but the burnt cd failed integrity checking).  So I re-burned, checked integrity, and gave it another go.  This time all went well... except I ended having to open a terminal and do 'sudo gparted' to set up the partitions BEFORE running the installer.  This allowed me to format the partitions I set up (the installer did NOT allow this!  grrr!) so that they would be properly selectable in the next step of installation where you choose which partitions are mounted as what.

It's the first official incarnation, so I'm not at all upset.  Having it run within a live desktop environment is obviously a HUGE advantage in many ways, and so I love it anyways.  The only drawback is that from a text based installer you have less hurdles in many cases because there is no X session to load... if that makes sense (yes it does!  shush.).

In short, I love it but I'm glad the alternative cd is still around for people to use "just in case".

8)

---

### Post by 23meg on 2006-06-07
My only gripe is that not giving the user an option with GRUB overwriting the MBR is a bit harsh. What I like the most about it is that it's a few times faster than the old installer in my experience.

Props should go to the GuadaLinex team, since AFAIK most of the work on the installer was done by them.

---

