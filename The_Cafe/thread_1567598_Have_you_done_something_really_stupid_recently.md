---
title: "Have you done something really stupid recently?"
date: 2010-09-04
forum: The Cafe
---

### Post by lovinglinux on 2010-09-04
I have installed Maverick yesterday and everything was fine, except for some akonadi issues. While troubleshooting it, I noticed my CPU usage was over 60%, sometimes 90%. So I opened htop and saw that the culprit was root. I asked myself why is root using so much CPU? It must be akonadi or something like that. Then I had a moment of enlightenment and decided to reboot. I thought...it should go back to normal. 

Then...BAM! That reboot totally screwed my system.

Then I realized I forgot I was doing some very important package upgrades in a minimized terminal, including xorg, kdm and other stuff provided by today's updates.

How could I have been so stupid?

I had to do a clean install because nothing was working. The system didn't even boot. Everything is back to normal now, but I have lost 2 hours of my life fixing this mistake.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=168426&stc=1&d=1283579003[/IMG]

---

### Post by iitywygms on 2010-09-04
yes i have.

---

### Post by Irihapeti on 2010-09-04
You won't make the same mistake again, I bet!

---

### Post by NightwishFan on 2010-09-04
Remember to try recovery mode if possible.

As for something stupid.. Depends. I suppose accidently scratching my Lucid cd was fairly stupid as I am now stuck on Maverick. Though it forces me to plow through any issues and I have conquered quite a few.

---

### Post by ranch hand on 2010-09-04
About a week ago I was doing a new install of Unity and decided that a certain pair of partitions were good victims.

Did my install, on 2 partitions as always.  Come to find out it is a ral good idea to not overwrithe the / partition of one OS and the /home partition of another.

I did however have the chance to set up 2 installs instead of just one.  What a bonus.

---

### Post by NightwishFan on 2010-09-04
That also reminds me of the time installing OpenSUSE 10.3 I forgot it does not count partitioning as a mandatory step for review (you have to pick it from a list) and it used the default setup which removed my data partition. :(

---

### Post by lovinglinux on 2010-09-04
> **Irihapeti said:**
> You won't make the same mistake again, I bet!

Indeed.

> **NightwishFan said:**
> Remember to try recovery mode if possible.

Tried that. No joy. It was really screwed :)

---

### Post by handy on 2010-09-04
I do really stupid things everyday, probably a whole lot more of them than I'm aware of... :shock:

---

### Post by honeybear on 2010-09-04
Installing windows XP !

---

### Post by sanderella on 2010-09-04
Yes, I misread my CAD knitting program a few minutes ago, and got the back of a sweater all wrong. #-o

---

### Post by papangul on 2010-09-04
Last week I was installing lucid on my friends pc and while trying to avoid installing grub into mbr(legacy habit), I accidentally overwrote the windows partition's boot sector. Neither windows cd nor any rescue disk was available.;)

After spending a day googling, I discovered testdisk and the rest was easy.

Btw, the [boot-info-script wiki page]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") that talks about this problem is amazing.

---

### Post by andymorton on 2010-09-04
I was leaving my girlfriend's place yesterday and I put her netbook charger in my bag rather than my own and took it home with me. I didn't realise until she called me. She wasn't pleased and is now without the internet until next week when I see her again. :???:

---

### Post by Naiki Muliaina on 2010-09-04
> **andymorton said:**
> I was leaving my girlfriend's place yesterday and I put her netbook charger in my bag rather than my own and took it home with me. I didn't realise until she called me. She wasn't pleased and is now without the internet until next week when I see her again. :???:

If I deprived my missus from internet shopping for a week I wudda been a dead puppy long ago...

---

### Post by lovinglinux on 2010-09-04
> **andymorton said:**
> I was leaving my girlfriend's place yesterday and I put her netbook charger in my bag rather than my own and took it home with me. I didn't realise until she called me. She wasn't pleased and is now without the internet until next week when I see her again. :???:

That's trouble :)

---

### Post by ticopelp on 2010-09-04
> **Irihapeti said:**
> You won't make the same mistake again, I bet!

Until 11.04 Negligent Narwhal

---

### Post by lovinglinux on 2010-09-04
> **ticopelp said:**
> Until 11.04 Negligent Narwhal

:lolflag:

---

### Post by inobe on 2010-09-04
> **NightwishFan said:**
> That also reminds me of the time installing OpenSUSE 10.3 I forgot it does not count partitioning as a mandatory step for review (you have to pick it from a list) and it used the default setup which removed my data partition. :(

sounds familiar.

---

### Post by Rubi1200 on 2010-09-04
> **NightwishFan said:**
> That also reminds me of the time installing OpenSUSE 10.3 I forgot it does not count partitioning as a mandatory step for review (you have to pick it from a list) and it used the default setup which removed my data partition. :(
I came this..close to doing the same thing until I realized something was not quite right.
As far as stupidity, tried installing Slackware recently which for some reason messed up the UUID of the swap partition and was unable to boot into Karmic afterwards.
GParted on the LiveCD and some fiddling got fstab fixed; all is well with Karmic ;)

---

### Post by Spice Weasel on 2010-09-04
Pulled out my USB drive half way during reformatting it because it was making too much noise...

---

### Post by andymorton on 2010-09-04
> **Naiki Muliaina said:**
> If I deprived my missus from internet shopping for a week I wudda been a dead puppy long ago...

> **lovinglinux said:**
> That's trouble :)

I think I'll be getting a stern telling off when I see her. I think perhaps some good old fashioned bribery via chocolate shall be employed! :D

---

### Post by Rubi1200 on 2010-09-04
> **andymorton said:**
> I think I'll be getting a stern telling off when I see her. I think perhaps some good old fashioned bribery via chocolate shall be employed! :D
And roses, don't forget the roses! ;)

---

### Post by Denis Krajnc on 2010-09-04
I'm trying not to make something stupid, but unsucessfully so far.

---

### Post by toupeiro on 2010-09-04
2 nights ago, I was working on a very extensive mindmap in Fremind of a new VM process I want to write which will dynamically throttle up and down CPU cores on demand of the application workload, and if necessary grow the amount of physical RAM without taking the OS down.  About 1.5 hours into it, I realized I was using the windows port of Freemind, and thought I should try to save it, and it wouldn't save, in any way, shape or form, including exporting it.  Worked fine when I tried to recreate it in Linux, but the whole mindmap was lost.  Hope I still remembered all the details. :P

---

### Post by lovinglinux on 2010-09-04
> **Spice Weasel said:**
> Pulled out my USB drive half way during reformatting it because it was making too much noise...

Ouch.

> **toupeiro said:**
> 2 nights ago, I was working on a very extensive mindmap in Fremind of a new VM process I want to write which will dynamically throttle up and down CPU cores on demand of the application workload, and if necessary grow the amount of physical RAM without taking the OS down.  About 1.5 hours into it, I realized I was using the windows port of Freemind, and thought I should try to save it, and it wouldn't save, in any way, shape or form, including exporting it.  Worked fine when I tried to recreate it in Linux, but the whole mindmap was lost.  Hope I still remembered all the details. :P

That is really frustrating.

---

### Post by NCLI on 2010-09-04
Yep, just now. I was reading through this thread, and forgot to keep an eye on an auction I was bidding in for a very cheap, good lens. 

I was outbid :(

Also, the day before yesterday, I accidentally ran 'crontab -r' instead of 'crontab -e' on my server... I had no backup :(

---

### Post by bobpress on 2010-09-04
> **Naiki Muliaina said:**
> If I deprived my missus from internet shopping for a week I wudda been a dead puppy long ago...

Yes, that would make it miserable for me too!

---

### Post by oldos2er on 2010-09-05
> **iitywygms said:**
> yes i have.

Nuff said.  ;)

---

### Post by TNT1 on 2010-09-05
I was painting the one bathroom yesterday, and it was a bit windy, so I closed the windows, didn't want dust all over the fresh paint... Whoa! Bad idea. I haven't been that high since 'varsity...

---

### Post by Khakilang on 2010-09-05
Yeah! Every night playing Facebook game.

---

### Post by lisati on 2010-09-05
A few days ago I was messing around with some forum software and mailing list software for my server. I noticed an error message when looking at my server's logs but didn't think much of it at the time. This afternoon I noticed that some emails sent internally hadn't got through properly, and that there were error messages galore when trying to retrieve them. Turns out that I'd somehow borked the permissions on one set of folders - most likely by not paying attention when (un)installing something. A quick bit of research here on the forum turned up a quick two-command solution that restored the proper permissions, and things are now working properly, touch wood!

---

### Post by linux18 on 2010-09-05
I secretly have puppy 5 dual booting on four computers at the local  community college, but a three months ago when I was young and stupid :)  I thought it would be a good idea to secretly dual boot ubuntu on two  of the computers. Well I partitioned the first one 2GB and everything  worked fine, for the next one I wanted to go 8GB and when I rebooted  windows...."DLL ERROR!!! registry Failure!!! 'this computer already  exists on network'" the registry fixed itself (which fixed the network  error) by going to defaults but I needed to run a diagnostic to find the  dll problem. Once the dll was isolated I copied it onto a flash drive  and started my ubuntu live cd (the computers are running deepfreeze so  you can't install the dll from windows) In a terminal, I navigated to  the proper folder and deposited the dll. After rebooting, everything  seemed okay and even faster since I deleted the startup links in the  startup folder. It only was a 1 hour diversion and a great learning  experience.....but I didn't learn well enough, after a few minutes of  celebration I decided to perform that ubuntu installation. I sped  through the installation and only after formating the drive did I  realize that .........it was the wrong partition. I ran to the  cafeteria, bought a monster energy drink, and came up with a plan of  action...I cloned the installation of windows from one computer to  another through a 4GB flash drive. So after 4 hours I ended up right  back where I wanted to be 3 hours and 45 minutes ago, 2 partitioned  computers ready for a ubuntu install. You would think I'd have learned  by then, but I actually managed to successfully installed ubuntu, hide  grub, and dual boot with windows. I was waaaay late to do any more and  left for the weekend. so when I came back next week, the school had  'upgraded' the computers to windows 7 and all of that hard work was for  nothing. Now that I'm three months wiser, I use puppy 5 which installs  alongside windows, doesn't need partitioning, and has deb support... win  win and win. 

The lession is to not secretly install anything on anything, but if you do, use puppy linux 5 and know when your community college decides to upgrade the software.

---

### Post by lovinglinux on 2010-09-05
> **linux18 said:**
> I secretly have puppy 5 dual booting on four computers at the local  community college, but a three months ago when I was young and stupid :)  I thought it would be a good idea to secretly dual boot ubuntu on two  of the computers. Well I partitioned the first one 2GB and everything  worked fine, for the next one I wanted to go 8GB and when I rebooted  windows...."DLL ERROR!!! registry Failure!!! 'this computer already  exists on network'" the registry fixed itself (which fixed the network  error) by going to defaults but I needed to run a diagnostic to find the  dll problem. Once the dll was isolated I copied it onto a flash drive  and started my ubuntu live cd (the computers are running deepfreeze so  you can't install the dll from windows) In a terminal, I navigated to  the proper folder and deposited the dll. After rebooting, everything  seemed okay and even faster since I deleted the startup links in the  startup folder. It only was a 1 hour diversion and a great learning  experience.....but I didn't learn well enough, after a few minutes of  celebration I decided to perform that ubuntu installation. I sped  through the installation and only after formating the drive did I  realize that .........it was the wrong partition. I ran to the  cafeteria, bought a monster energy drink, and came up with a plan of  action...I cloned the installation of windows from one computer to  another through a 4GB flash drive. So after 4 hours I ended up right  back where I wanted to be 3 hours and 45 minutes ago, 2 partitioned  computers ready for a ubuntu install. You would think I'd have learned  by then, but I actually managed to successfully installed ubuntu, hide  grub, and dual boot with windows. I was waaaay late to do any more and  left for the weekend. so when I came back next week, the school had  'upgraded' the computers to windows 7 and all of that hard work was for  nothing. Now that I'm three months wiser, I use puppy 5 which installs  alongside windows, doesn't need partitioning, and has deb support... win  win and win. 

The lession is to not secretly install anything on anything, but if you do, use puppy linux 5 and know when your community college decides to upgrade the software.

:lolflag:

---

### Post by linux18 on 2010-09-05
> **lovinglinux said:**
> :lolflag:
which part? :)

---

### Post by Naiki Muliaina on 2010-09-05
> **linux18 said:**
> which part? :)

Most of it! Top tale of Linux heroism! Love it! :):):)

 :popcorn:

---

### Post by lovinglinux on 2010-09-05
> **Naiki Muliaina said:**
> Most of it! Top tale of Linux heroism! Love it! :):):)

 :popcorn:

Me too.

---

### Post by neu5eeCh on 2010-09-05
Something I already mentioned a couple days ago: I copied and pasted a recursive RM command and, lo and behold, it worked. It seems that I deleted my entire home directory.

Stupidest move of all time?

Dipping my glasses into the Atlantic's surf to clean them off. Huh? What? Really? There's sand in that water? DOH! - concussion-inducing face palm.

---

### Post by SoFl W on 2010-09-05
Whenever I leave my external USB drive plugged in and reboot, I get the missing boot loader error message, for a brief second I get nervous.  *Every time*.

---

### Post by Spice Weasel on 2010-09-05
> **linux18 said:**
> I secretly have puppy 5 dual booting on four computers at the local  community college, but a three months ago when I was young and stupid :)  I thought it would be a good idea to secretly dual boot ubuntu on two  of the computers. Well I partitioned the first one 2GB and everything  worked fine, for the next one I wanted to go 8GB and when I rebooted  windows...."DLL ERROR!!! registry Failure!!! 'this computer already  exists on network'" the registry fixed itself (which fixed the network  error) by going to defaults but I needed to run a diagnostic to find the  dll problem. Once the dll was isolated I copied it onto a flash drive  and started my ubuntu live cd (the computers are running deepfreeze so  you can't install the dll from windows) In a terminal, I navigated to  the proper folder and deposited the dll. After rebooting, everything  seemed okay and even faster since I deleted the startup links in the  startup folder. It only was a 1 hour diversion and a great learning  experience.....but I didn't learn well enough, after a few minutes of  celebration I decided to perform that ubuntu installation. I sped  through the installation and only after formating the drive did I  realize that .........it was the wrong partition. I ran to the  cafeteria, bought a monster energy drink, and came up with a plan of  action...I cloned the installation of windows from one computer to  another through a 4GB flash drive. So after 4 hours I ended up right  back where I wanted to be 3 hours and 45 minutes ago, 2 partitioned  computers ready for a ubuntu install. You would think I'd have learned  by then, but I actually managed to successfully installed ubuntu, hide  grub, and dual boot with windows. I was waaaay late to do any more and  left for the weekend. so when I came back next week, the school had  'upgraded' the computers to windows 7 and all of that hard work was for  nothing. Now that I'm three months wiser, I use puppy 5 which installs  alongside windows, doesn't need partitioning, and has deb support... win  win and win. 

The lession is to not secretly install anything on anything, but if you do, use puppy linux 5 and know when your community college decides to upgrade the software.

Lucky guy. My school's computers lag on the BIOS (:lol:) so I never get the chance to install anything. I do, however find a way around IE. USB stick with portable ELinks and Firefox on it ftw!

---

### Post by linux18 on 2010-09-05
> **Spice Weasel said:**
> Lucky guy. My school's computers lag on the BIOS (:lol:) so I never get the chance to install anything. I do, however find a way around IE. USB stick with portable ELinks and Firefox on it ftw!
even if they lock the bios, you can usually hit F12 a few times and change the boot device that way.

---

### Post by Spice Weasel on 2010-09-05
The BIOS isn't locked, it just frequently goes non responsive and whenever you try to change tabs the thing jumps about 20. I didn't think of the F12 thing though, thanks.

---

### Post by The Real Dave on 2010-09-05
Hmmm, recently?  

I dropped my mobile phone into a muddy puddle without realising it. It took me two minutes to realise I had dropped it, at which stage I ran back up the road to see it resting completely in the puddle, screen and keyboard flashing.

I was terrified, and quickly tried to dry and clean it on my top. It had stopped flashing...

Because the girl who was calling had hung up. The phone was fine, didn't even phase it. It's a K800i by the way :) Stupid mistake, but luckily not fatal.

---

### Post by beercz on 2010-09-05
There's quite a few [here]("http://ubuntuforums.org/showthread.php?t=1545184") - including one from me :-)

---

### Post by sxmaxchine on 2010-09-05
had to redo an entire assignment because i did it wrong and now i didnt sleep and have to go to school to submit it.

---

### Post by SoFl W on 2010-09-06
I was making backups of my home directory to another partition on the same drive, I was thinking it was a another physical drive and not just a partition.  If the drive failed I would have lost all the data.

---

### Post by Old_Grey_Wolf on 2010-09-06
Of course.

However, you will have to supply a lot of free beer before I will embarrass myself by telling what it was. 

:lolflag:

---

### Post by foxxxy on 2010-09-06
I installed gentoo, ended up throwing my keyboard through my monitor :(

---

### Post by Amilo1718 on 2010-09-06
> **lovinglinux said:**
> I have lost 2 hours of my life fixing this mistake.
only 2 hours... =D>
a full recovery of my system would take a lifetime... ;)

---

### Post by Windows Nerd on 2010-09-06
> **foxxxy said:**
> I installed gentoo, ended up throwing my keyboard through my monitor :(

Did you really or are you joking?
[IMG]http://www.nyblom.org/pub/gentoo.png[/IMG]

---

### Post by foxxxy on 2010-09-06
> **Windows Nerd said:**
> Did you really or are you joking?


HAY, who took pictures? :P

---

### Post by lovinglinux on 2010-09-06
> **Amilo1718 said:**
> only 2 hours... =D>
a full recovery of my system would take a lifetime... ;)

Well, I thought that was too much. I takes longer than usual because I install the command-line only system using the alternate CD, then install xorg, kdm, kde-minimal, kdeplasma-addons and firefox, then I login and install the rest of my applications, using my [Umarks]("https://addons.mozilla.org/en-US/firefox/addon/13153/") extension.

I have a separate partition for /home, so there is not many things to configure pos-install, only sensors and my TV card, since they require some config as root.

---

### Post by magmon on 2010-09-06
I put the wrong file on my flash drive the other day, and didn't notice until I was in the school library attempting to print it. Luckily I had an hour study hall, so I finished it again, but it was time poorly wasted.

---

