---
title: "Graphical interface to erase unwanted/junk files."
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by pacsum on 2007-10-25
Why instead of having a nice app to erase all temp/junk files, you have to erase it manually with the terminal? I know Linux is not about being as Windows but this is A MUST have if Ubuntu wants to attract new users. I've seen people with heir HDD full because the root trash is full, but you can't  erase it so easily.

Also eliminate for good the system beep, people, like myself, with laptops need this.

---

### Post by mikewhatever on 2007-10-25
Do you think imitating Windows in every feature would be a good idea?

---

### Post by pacsum on 2007-10-25
I'm not that kind of guy, who wants linux to be as easy as Windows but this feature would be nice and a much simpler way to erase junk/temp files instead of installing dependencies to erase unwanted files.
I would love to help Ubuntu but I know sh*t about programing.

---

### Post by Martje_001 on 2007-10-25
Shouldn't be too hard to make.. a few commands:
```
sudo apt-get autoremove
sudo apt-get clean
sudo rm -r /root/.Trash
```
well... that's it if you ask me :?

---

### Post by pacsum on 2007-10-25
> **Martje_001 said:**
> Shouldn't be too hard to make.. a few commands:
```
sudo apt-get autoremove
sudo apt-get clean
sudo rm -r /root/.Trash
```
well... that's it if you ask me :?
...and this ones:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by aysiu on 2007-10-25
Why would the root trash be full?

If you want to delete things instead of moving them to the trash, go to Edit > Preferences > Behavior > Trash > Include a Delete command that bypasses Trash

Then, the next time you launch Nautilus as root, just delete the file instead of moving it to the trash. Or, from time to time, go to /root/.Trash and delete the files there.

---

### Post by kellemes on 2007-10-27
> **mikewhatever said:**
> Do you think imitating Windows in every feature would be a good idea?

+1

Still, this feature seems easy enough to implement.

---

### Post by tomplast on 2007-10-27
Porting Kleansweep to GTK libraries would do it?

---

### Post by derrick81787 on 2008-01-16
We should come up with a comprehensive list of where and what constitutes a *trash* file.  Do you only mean files that are actual in .Trash, or other files as well?  I'm not an Ubuntu developer, but I know how to program, and this sounds easy enough that I'm sure I could implement it if I could get some more details.

---

### Post by derrick81787 on 2008-01-16
I was thinking of possible options for files to be removed, and this is what I have come up with (some options will be more recommended than others)

[LIST]
[*]old, unused package dependencies (apt-get autoremove)
[*]old, useless packages from the apt cache (apt-get autoclean)
[*]all packages from the cache (apt-get clean)
[*]/root/.Trash
[*]~/.Trash (for your user or all users)
[*]temporary files (/tmp)
[*]log files (/var/log)
[*]do something with the localepurge utility
[*]do something with the deborphan utility
[/LIST]

Can anyone think of anything that I left out, and does anyone have a problem with any of these choices being available as possible options?

---

### Post by Neon Lights on 2008-01-17
kinda like CCleaner for linux? sounds good to me. =]

---

### Post by chrisccoulson on 2008-01-17
> **derrick81787 said:**
> I was thinking of possible options for files to be removed, and this is what I have come up with (some options will be more recommended than others)

[LIST]
[*]old, unused package dependencies (apt-get autoremove)
[*]old, useless packages from the apt cache (apt-get autoclean)
[*]all packages from the cache (apt-get clean)
[*]/root/.Trash
[*]~/.Trash (for your user or all users)
[*]temporary files (/tmp)
[*]log files (/var/log)
[*]do something with the localepurge utility
[*]do something with the deborphan utility
[/LIST]

Can anyone think of anything that I left out, and does anyone have a problem with any of these choices being available as possible options?

AFAIK, /tmp is cleaned when you boot the machine. Attempting to clean /tmp on a running system would be a bad idea as a lot of applications use it to store data whilst they are running.

---

### Post by xlinuks on 2008-01-17
I feel sorry for Ubuntu when someone suggests a good idea, like in this post - to fix the issue with trash files - and there suddenly comes out somebody who tries to dump this IMHO very useful suggestion with old fashioned words like "it's not windows" or alike.

If we wanna improve Ubuntu we first gotta admit that such issues exist, lots of them, and stop saying "it's not windows" or "don't try to make Linux like windows" or alike. Take for instance the trash files that _by default_ get stored on removable drives. The removable files tend to have _temporary_ life so practically no one needs a trash on removable drives.
Some other example - a bit off-topic though - the "ugliness" of BIG (windows95 age) buttons is used in many default apps with the excuse "for the sake of simplicity".
With thoughts of such quality (sarcasm implied) we just can't compete with the likes of MacOS or Windows (yes, oficially we might not recognize it, but in a LOT of cases we're left out just because we're too small, for there's few ppl using Linux). Thankgod the big majority doesn't use/stopped using these useless mottos.

---

### Post by derrick81787 on 2008-01-17
> **chrisccoulson said:**
> AFAIK, /tmp is cleaned when you boot the machine. Attempting to clean /tmp on a running system would be a bad idea as a lot of applications use it to store data whilst they are running.

Thanks for the heads up about /tmp.  I wasn't real sure what it would do, but I intended on testing it on my own computer to see.  I also wasn't aware that /tmp was cleaned on boot.  Is this a fairly new feature? I thought that I followed a How-To once (back in Breezy days, possibly) that showed me how to make it to where /tmp was cleaned on boot, which made be believe it wasn't by default.

Are there any problems with any of the other choices or any additions to be made?  I was sort of unsure about the effects of deleting the contents of /var/log, but I don't think it would do anything other than erase some programs' log entries, which would be okay (especially if you never look at them).

---

### Post by chrisccoulson on 2008-01-17
I'm sure /tmp has been cleaned on boot for quite a while. Certainly, anything I ever store in there always gets removed on the next reboot, and if I store several GB of data in /tmp, my boot takes longer.

There is no point in deleting stuff from /var/log. On my machine, /var/log is only 48MB, which is fairly insignificant. All the logs are rotated by a cron job already, with the oldest being removed. You shouldn't really need to go removing files from /var/log. If you really are pushed for space, the better option would be to modify the scripts that rotate your logs (you won't have to continually delete files then). You're likely to do more harm than good if you go manually deleting files from certain areas of your filesystem.

---

### Post by pacsum on 2008-01-19
> **xlinuks said:**
> **I feel sorry for Ubuntu when someone suggests a good idea**, like in this post - to fix the issue with trash files - and there suddenly comes out somebody who tries to dump this IMHO very useful suggestion with old fashioned words like "it's not windows" or alike.

If we wanna improve Ubuntu we first gotta admit that such issues exist, lots of them, and stop saying "it's not windows" or "don't try to make Linux like windows" or alike. Take for instance the trash files that _by default_ get stored on removable drives. The removable files tend to have _temporary_ life so practically no one needs a trash on removable drives.
Some other example - a bit off-topic though - the "ugliness" of BIG (windows95 age) buttons is used in many default apps with the excuse "for the sake of simplicity".
With thoughts of such quality (sarcasm implied) we just can't compete with the likes of MacOS or Windows (yes, oficially we might not recognize it, but in a LOT of cases we're left out just because we're too small, for there's few ppl using Linux). Thankgod the big majority doesn't use/stopped using these useless mottos.

That's why I'm migrating to opensuse.

---

### Post by danbh on 2008-01-19
if I may sell my own project, which is quite new, I think it could offer a simple solution to this thread:

[https://launchpad.net/climl](https://launchpad.net/climl)

If you list the commands to clean the drive, I'll make the GUI.

---

### Post by derrick81787 on 2008-01-19
I also started working on a quick GUI in glade.  I have a prototype already made (of the GUI, no backend yet).  It's sort of plain right now, but you should be able to get the general idea.  I've attached a screenshot.  Is this the type of thing you are wanting?

- Derrick

---

### Post by Xbehave on 2008-01-20
I don't think it really needs a backend just call commands.
a good option would be to remove source packages as they're often installed while somebody makes something then forgotten about.

p.s i agree with xlinuks completely, particularly the .trash on removable media.

---

### Post by chrisccoulson on 2008-01-20
> **Xbehave said:**
> I don't think it really needs a backend just call commands.
a good option would be to remove source packages as they're often installed while somebody makes something then forgotten about.

p.s i agree with xlinuks completely, particularly the .trash on removable media.

I thought that the issue with trash filling up removable media had been fixed. Certainly in Gutsy, you get a prompt when you eject removable media asking you if you want to clear the trash from the volume.

---

### Post by smartboyathome on 2008-01-20
> **chrisccoulson said:**
> I thought that the issue with trash filling up removable media had been fixed. Certainly in Gutsy, you get a prompt when you eject removable media asking you if you want to clear the trash from the volume.

That is only on Nautilus, though. Some people like me use Thunar, and in that situation we have to delete the file from the trash (not that unresonable, just a pain).

---

### Post by derrick81787 on 2008-01-28
Hey everyone.  I just finished the first version of the program.  I've attached the deb package, which should work on all architectures because it is just python and bash.  You can install it by double-clicking on the package icon.

Sometime soon I'm going to set up a website and whatnot, but for now, just get it from this attachment.  I'll let you know if I make any important changes.

- Derrick

**Edit::  By the way, you need to install localepurge and deborphan.  I sort of forgot to mention that, but if you installed it with gDebi, it should have handled that for you, anyway.

---

### Post by danbh on 2008-01-29
er, I shamelessly need help with a project I'm doing.  derrick81787: would you mind helping me with the packaging stuff?  Is it hard to explain?

---

### Post by derrick81787 on 2008-01-29
> **danbh said:**
> er, I shamelessly need help with a project I'm doing.  derrick81787: would you mind helping me with the packaging stuff?  Is it hard to explain?

Well, I don't know a lot about it... I can help you make binary packages like the one I made here, but I don't really know how to make the source .dsc packages that are needed for inclusion in Ubuntu.  I do hope to learn sometime soon, though, because I have another project that I would like to try to get included in the repositories.

The guide I followed is this one:  [http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/) . 

If you want my help, I'll try and help out, but I can't promise I'll be of much use.

- Derrick

P.S. :  Somewhere there is an official Ubuntu maintainer's guide, but I can't seem to find it.

---

### Post by 23meg on 2008-01-29
[QUOTE=derrick81787]P.S. : Somewhere there is an official Ubuntu maintainer's guide, but I can't seem to find it.[/QUOTE]

[https://wiki.ubuntu.com/PackagingGuide/](https://wiki.ubuntu.com/PackagingGuide/)

---

### Post by pacsum on 2008-04-03
> **derrick81787 said:**
> Hey everyone.  I just finished the first version of the program.  I've attached the deb package, which should work on all architectures because it is just python and bash.  You can install it by double-clicking on the package icon.

Sometime soon I'm going to set up a website and whatnot, but for now, just get it from this attachment.  I'll let you know if I make any important changes.

- Derrick

**Edit::  By the way, you need to install localepurge and deborphan.  I sort of forgot to mention that, but if you installed it with gDebi, it should have handled that for you, anyway.
Nice :-o

---

