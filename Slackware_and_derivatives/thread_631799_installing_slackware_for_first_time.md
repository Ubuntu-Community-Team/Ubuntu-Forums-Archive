---
title: "installing slackware for first time"
date: 2007-12-04
forum: Slackware and derivatives
---

### Post by jpittack on 2007-12-04
I am intent on installing slackware for the first time, but I am also needing to reinstall Ubuntu.  On the same computer is Vista.  I believe I saw that Slackware uses something other than grub by default.  I would like to reinstall Ubuntu, then install Slackware and keep grub, or will Slackware's default be sufficient, as I don't do anything with the boot loader.

I really just have first time gitters, and I always have the idea that I am going to blow up my computer by doing something new.

---

### Post by tommcd on 2007-12-05
If you plan on reinstalling Vista do that first Then install ubuntu next. Boot up ubuntu live CD and create these partitions:
a 10-12 GB partition for ubuntu's root
a 1GB swap
a 10-12 GB partition for slackware's root
whatever is left for /home.
You could make the root partitions a little smaller if you are short on space. Install Ubuntu first and put grub on MBR (master boot record). Then install Slackware. When you get to the part about installing lilo (the boot loader slackware uses) choose "do not nstall lilo".  Then add Slackware to Ubuntu's grub as per post #4 from this thread:
[http://ubuntuforums.org/showthread.php?t=393379](http://ubuntuforums.org/showthread.php?t=393379)
Choose  different user names for Slackware and Ubuntu so the hidden config files in /home don't conflict with each other. Or do what I do and create a /data partition instead of separate /home. That way the config files in /home live in each distro's root partition wothout potential for problems. If you already have a separate /home then just leave it and use a different user name for Slackware. Slackware is great for learning linux. Write back if you need more help.
You only need the first 2 Slackware CDs to install Slackware.
EDIT: don't forget to read the Slack book:
[http://slackbook.org/](http://slackbook.org/)
Here is a great podcast about slackware. It is based on slackware 11, but still lots of good info:
[http://www.linuxreality.com/podcast/special-episode-1-slackware/](http://www.linuxreality.com/podcast/special-episode-1-slackware/)

---

### Post by jpittack on 2007-12-06
Thanks for all the info.  I am installing slack to learn linux.  I don't need to reinstall Vista.  I will probably steal some more space from it.  Uninstall some games from it to free up even more space.  I have a separte /home partition already.

So hear are the steps I will be doing.

Shrink vista.
Reinstall Ubuntu, setting up partitions here. ( I have a question here)
Install Slackware, skipping installing lilo.
Boot into Ubuntu and add Slackware from following the post.

Heres the question.  Does grub install to MBR using the method I have in the past, or is there something more that I need to do?

Thanks for posting.  Lately I haven't been finding answers to my questions.  Help is very much appreciated.

---

### Post by tommcd on 2007-12-07
> **jpittack said:**
> 
Heres the question.  Does grub install to MBR using the method I have in the past, or is there something more that I need to do?


By default grub will install to MBR. You can select to install grub to ubuntu's root partition, or anywhere else, when you get to the grub part of the installation:
[http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu](http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu)
So just choose yes to install to MBR.
For everything you would ever want to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
The steps you outlined in your post look fine.
Another good thing to read is the Changes_And_Hints.txt:
[http://slackware.mirrors.tds.net/pub/slackware/slackware-12.0/CHANGES_AND_HINTS.TXT](http://slackware.mirrors.tds.net/pub/slackware/slackware-12.0/CHANGES_AND_HINTS.TXT)
You can skip the first part about upgrading slackware. 
Good luck. Also check out the official slackware forum at LQ questions.org:
[http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)

---

