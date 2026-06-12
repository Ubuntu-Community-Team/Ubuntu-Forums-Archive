---
title: "Setting my girlfriend up with Ubuntu this weekend"
date: 2007-02-19
forum: Testimonials &amp; Experiences
---

### Post by AusIV4 on 2007-02-19
About a year and a half ago (August of '05), I met my college roommate. He introduced me to Ubuntu Linux. At first, I thought he was torturing himself by trying to use an underpowered desktop for ideological reasons. By November, he had convinced me that Ubuntu could breathe life back into an old desktop I had lying around. I decided to try it, and sure enough it produced a very productive machine. In May, I rebuilt the machine to have a more powerful Linux Box with a TV tuner, lots of disk space, and MythTV - the ultimate DVR. All this time, I was still using Windows XP as my primary OS on my laptop.

Finally, in December I decided to go for it and dual boot my laptop. In the last two and a half months, I've booted Windows on maybe 5 occasions. Two weeks ago I ordered a new laptop from System76. My old one, while quite powerful, has a 17" monitor and weighs upwards of 10 lbs. and I needed something more portable.

All the while, my girlfriend has been watching me find an operating system that I really **like** and grown to hate Windows more and more.

This weekend, she wants me to set her up with Ubuntu and show her how to use it. I plan to give her Kubuntu, because that's what I use and it will be easier for me to step her through things remotely (we're in a long distance relationship) if we're using the same DE. I also plan to give her Beryl, because her computer should be quite capable of running it, and I think she'll enjoy some of the features.

I really think Ubuntu is ready for the average computer user. They may need some help with configuration, but I see no reason it shouldn't be manageable. I'll post an update in a while on how she likes it.

---

### Post by shane.reid on 2007-02-21
Good luck - I had my wife running it for about a year until she upgraded to a Macbook.

She loved Ubuntu and actually misses quite a few things from time to time.  

After I set the whole thing up, it worked flawlessly for her (this was Dapper beta)

---

### Post by AusIV4 on 2007-02-24
We've started the installation process. Right now we're defragmenting her windows partition so we won't lose any of her data. I plan to have her do as much of the installation as possible so I can see how easy it is for a non-computer geek.

---

### Post by Henry Rayker on 2007-02-24
Unless the 3d-acceleration video card drivers come from the repos, I'd vote against installing beryl for her, due to the fact that every kernel update will likely break her X.

---

### Post by Rinzwind on 2007-02-24
> **Henry Rayker said:**
> Unless the 3d-acceleration video card drivers come from the repos, I'd vote against installing beryl for her, due to the fact that every kernel update will likely break her X.

How does that matter?

Most likely he will be admin and she will be a user. Therefor breaking X after a kernel update equals HIM having to fix it ;)

---

### Post by Henry Rayker on 2007-02-24
> **Rinzwind said:**
> How does that matter?

Most likely he will be admin and she will be a user. Therefor breaking X after a kernel update equals HIM having to fix it ;)

Given that this is a long distance relationship issue, I'm fairly certain that it will, in fact, matter. I'd be completely shocked if he makes himself admin and her user, given the circumstances.

---

### Post by AusIV4 on 2007-02-24
> **Henry Rayker said:**
> Unless the 3d-acceleration video card drivers come from the repos, I'd vote against installing beryl for her, due to the fact that every kernel update will likely break her X.

She has an intel GMA, the necessary drivers are in the repos, otherwise I would have been more concerned about it. She seems to like Beryl pretty well.

We've got pretty much everything set up. Right now, her Linux partition is only ~10 GB, so I had hoped to be able to read her media (music, pictures, and a few videos) off of her NTFS partition, but so far Amarok hasn't been able to scan her music collection without crashing. If she likes Linux well enough to keep it, I'll resize her partitions so she can have her media on Ubuntu. She already has everything on her iPod, so she's not completely without her music.

[EDIT]
I might also note - On windows, her laptop's battery wouldn't charge. We had chalked it up to being a bad motherboard, but it was out of warranty and we weren't going to replace it. We noticed it was  charging when we first booted the live CD. The battery now has a full charge. Even if she decides she doesn't like Linux, she'll probably keep it around to reboot so she can charge her battery.

---

### Post by Henry Rayker on 2007-02-25
I'm glad to hear she's having a good experience. Because the driver is in the repos, aside from random Beryl errors, I'm sure she won't have much of a problem with that.

---

### Post by AusIV4 on 2007-02-25
I've decided to write a somewhat detailed account of the weekend.

The first thing I did to start setting my girlfriend up on Linux was let her choose a version of Ubuntu. I showed her Gnome and KDE on my laptop, emphasizing that I use KDE, so if she has trouble I'll be more help with KDE. That's what she chose.

The next thing I did was defragment her hard drive - three times before there was a significant amount of space at the end of the partition. Then I booted the Ubuntu Live CD and shrank her NTFS partition by 10 GB (which was about all there was room for). I left the remainder empty, gave her the Kubuntu Live CD, and stepped her through the installation, letting her do it on her own.

She was able to get Kubuntu installed fairly easily - I had to tell her to choose "Use the largest empty space" for the installation, but she figured everything else out on her own.

Once everything was set up, we plugged her laptop into the router to download new packages. First, I set up /etc/default/bluetooth, and got her mouse working. Then I showed her Adept Installer, and told her to install Knetworkmanager. She saw Firefox and Gaim while she was looking for it, and chose to install those, since she was familiar with them from Windows.

Once Knetworkmanager was installed, I stepped her through making changes to her /etc/network/interfaces file so knetworkmanager would start up properly. Then I read off her WEP key from my computer (which was on her wireless network), and had her log on to her wireless network, then unplug her cat-5 cable. I also showed her how to add knetworkmanager to her .kde/Autostart/ folder. I might also note that she was fortunate enough to have an Intel wireless card, which has the best Linux drivers of any wireless card I've found to date (I've also tried Broadcom and Aetheros, with some success but a few bugs). 

Then I let her loose for a while. She wanted to find some desktop images, so I suggested she look at kde-look.org. She found a pony in a bottle against a green background, and set it as her wallpaper. Then she found the System Settings > Appearance tab, and turned all of her colors to various shades of green - she's something of an artist so it actually looked pretty good.

While she was playing around with colors, I had installed SSH on her box, and was busy installing some media codecs, flash, java, and adding her windows partition to /etc/fstab so she could copy files over as she needed them.

Once she had things configured as she wanted them, I told her where to find her xorg.conf file, and then stepped her through the changes she'd need to make in order to get beryl running. Her laptop has Intel GMA drivers, which are in the repositories, so I'm not concerned about a kernel update breaking X - if her card had needed new drivers for beryl, I wouldn't have set it up.

I ran the commands to install beryl and added it to her Autostart folder, set her default window decorator as Aquamarine (she'd just spent so much time configuring her window decorator, so I figured I'd let her keep it), and then showed her how to configure it. She decided the fade animation was pretty but not too obnoxious, played around with some different options, and eventually had some things configured the way she wanted. I also made it clear that beryl is not the most stable software, and might do weird things on occasion.

A few hours later, she decided she wanted a notifier for when she got mail to her Gmail account. She'd seen one on my computer, so she knew they existed for Linux. I told her it was in Adept Installer, and she'd need to search "Any Suite" and "Unsupported Software". She found it without a problem.

The only thing we didn't get working was Amarok. We were trying to play her music from her read-only windows partition, and Amarok kept crashing when building the collection. If she decides to keep Kubuntu (which I bet she will), we'll have to juggle things around, resize partitions, and put her music on her Linux partition.

By the end of the weekend, she was quite impressed. She felt that even without beryl, Kubuntu was far prettier than Windows, and with beryl, there was no contest. She loves the ease of use of the Adept Installer. She's appropriately cautious about typing in her password to run a command as root. While she'd initially been afraid of the command line, she found that it's quite useful, as it allows me to give her exact instructions for performing tasks - rather than having to describe icons and menu locations.

I'm quite pleased that the transition has gone so smoothly. In fact, there were a few things that went more smoothely than I expected. Her media buttons worked out of the box. On one of my laptops, I've never gotten the volume buttons to work, but she accidentally leaned against them and turned the volume up.

The most amazing part of the whole deal was her laptop's battery. A few months ago, she told me that her laptop was no longer charging its battery. I tried a few things - swapping out batteries (she had two), tried to see if it would charge while it was off, nothing worked. I did some research, and everything I saw pointed towards a motherboard issue. I had assumed there was no hope for her battery, and was thinking about getting her an external battery for her birthday. When I popped in the Ubuntu Live CD so I could do repartitioning, I noticed the battery gained a bar while it was repartitioning. Amazingly, her battery is now fully charged, and it seems to charge under Windows as well Linux. I'm still scratching my head on this one.

The only disappointment was that her laptop doesn't suspend or hibernate properly. This was no real surprise, as neither of those features worked consistently under windows.

Only time will tell for sure, but I suspect she'll be a happy Ubuntu user for years to come.

---

### Post by Hendrixski on 2007-02-25
:) I've ported my girlfriend to Ubuntu a while back.  She loves it, but for different reasons than me.  I'm a developer so I appreciate the stability,  she likes thecolors, LOVES the mascot, tux.   Now she's got like 100 cute tux icons everywhere.  Loves Beryl!  It does break fromtime to time but she'd rather have it than not.   She's even started showing some of her friends, who promptly want to switch as well.

Keep up the good work of spreading LINUX. :)

---

### Post by geakMonkey on 2007-02-26
My partner and I spent the week going to the book store to research which Ubuntu books we both needed that we could both share. We chose Ubuntu Linux for Non-Geeks and Linux Phrasebook. We spent several hours on the Ubuntu LiveCD. I was amazed and dazed that she was interested in watching me troubleshoot my installation issues for Sun Java 6 on my Dapper server. After doing some excercises from the Non-Geeks book, she was fascinated with troubleshooting.

---

### Post by matt_risi on 2007-02-26
Hendrixski: You're a lucky man.

---

