---
title: "Using Xubuntu for 8 months, but scared of the Terminal, is that normal?"
date: 2013-03-28
forum: Ubuntu, Linux and OS Chat
---

### Post by argonvegell on 2013-03-28
After getting fed up with Windows and switching to Xubuntu, I loved it, instead of being paranoid about viruses and malware, waiting for Defraggler to finishing defragging my Windows system, waiting for Windows to shutdown, it takes one minute, I can now enjoy my computer and the internet without worries, no bloatware, no viruses, no fragmenting, faster start-ups and shutdown, shutting down only takes a few seconds, I can honestly say, switching to Xubuntu was the best decision I ever made.  The only thing that I'm scared of touching is the Terminal, don't get me wrong, I used it a few times, like installing and fixing a problem with Avast! Antivirus, turning on UFW firewall, but I'm still afraid of using it, I'm a novice computer user, I try to avoid using it as much as possible, I use Terminal as a last resort, I'm scared of playing around with it because I might damage my system, especially when using the sudo commands.

---

### Post by mamamia88 on 2013-03-28
It's normal to be scared of what you don't understand.  But once you understand it it's a very powerful and awesome tool.   Don't be scared just make sure you don't run commands like rm without knowing what you are removing.

---

### Post by montag dp on 2013-03-28
Also, adding the following lines to your ~/.bashrc file should help make sure you don't accidentally delete something without meaning to:

alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

This will ensure that you are always prompted before something is deleted or overwritten.  If you want to remove a bunch of files without having to answer the prompt, just use the -f option.

The best way to get over your fear of the terminal is to just use it.  Practice navigating around your file system from the terminal instead of the file manager.  Remember, tab completion is your friend!  After a little while, you'll see how useful the terminal is, and then you can start putting commands in bash scripts to do things even faster.

---

### Post by Bashing-om on 2013-03-28
argonvegell;

The command line is a tool, a tool to be respected, but nothing to fear. There are many tutorials to get you acclimated. You will not know 'till you get your feet wet, and then dive in !
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)
There is always someone here to help you over the rough spots.

---

### Post by Tamlynmac on 2013-03-29
> argonvegell

First, glad you found the light.

As  for the terminal, it's just a tool. Like any other tool, one must learn  to use it before becoming proficient with it. Take your time and become  familiar with the commands. As others have suggested, use some caution  and if your not sure ask or look it up. I can't tell you how many times  (when I first switched to Linux - Ubuntu 7.04) I crashed my system while  learning and tinkering. :smile:

Didn't  take long before I purchased an inexpensive, used, 40gig usb HDD ($20)  for testing and tinkering purposes. This kept the PC in fully functional  condition for family use, while giving me the confidence to tinker -  knowing I'd have zero impact on said family usage. Should the 40gig  crash, I simply reinstalled the OS and continued learning. Once you  become proficient, you can still use the spare HDD for beta testing new  releases, testing other distros or just use it for storage. Whatever you  decide, have fun and enjoy the learning process. Remember, one doesn't  need to become a guru over night and by taking the time to learn - it  will definitely IMO improve the Linux experience.

Good Luck

---

### Post by coldraven on 2013-03-29
if you are going to edit a config file always make a copy of the original first.
If you mess up then you can restore the original file.
I usually just add "old" to the filename. So myconfig.d would become myconfig.d.old.
Some people add "bak", short for backup, it's up to you.
Good luck, I'm glad that you're enjoying your new found freedom.

---

### Post by Elfy on 2013-03-29
> **coldraven said:**
> if you are going to edit a config file always make a copy of the original first.
If you mess up then you can restore the original file....

Agreed.

Gedit I think saves a copy by default, if not it can be set in the preferences.

If the OP starts using a terminal text editor then nano, at least, can do the same just use nano -B and it will create a backup on save

---

### Post by 3rdalbum on 2013-03-29
I'd be perfectly happy if I didn't have to use the terminal ever again.

I do use the terminal for some things that are easier - like Apt-get, adding PPAs, setting 'at' jobs. I also found myself forced to use the terminal when - (sigh) - my graphics got broken.

But I don't mind if you're scared of the terminal. It's an intimidating feature in Linux, and there are definite negative cultural connotations to the terminal too - "the hacker sits in front of scrolling white text on a black background, hacking into computer systems because he has no friends and is socially retarded". Everyone is allowed to be scared of something, and as you mention, avoiding the terminal where possible does make it a lot harder to break your system.

My father has been using Ubuntu since 2009 and couldn't apt-get, chmod or ls anything to save his life. It's actually not abnormal.

---

### Post by The Cog on 2013-03-29
Fear of the command line is quite normal although I'm not sure it's always rational. 
> I'm scared of playing around with it because I might damage my system doesn't really make sense to me - graphical programs can just as easily damage the system. gparted, regedit, resedit etc can all wreak havoc on their host systems. So can a graphical file manager.

What I think the real problem probably is, is that a command-line prompt gives very little guidance and is not "discoverable". If you don't know what to do, don't know the command needed to achieve something, all you can do is sit there and stare at the space where you have to type *something*. This can be a very intimidating feeling. At least with a GUI, there are things you can click and try - they might trash the system but at least you're doing something, and you can make a guess at what the program is for.

On the other hand, if you know the commands then using a GUI to do the same job can feel like trying to shell peas while wearing boxing gloves, or doing brain surgery with a handyman's toolkit. 

My advice is to learn just enough to look around in the command line. pwd, cd, ls, cat, less for starters. 
Maybe an editor too - many years ago I was advised to learn some basic vi because that was sure to be on any system I went to. Good advice, although if you are sticking to Ubuntu then nano will always be there and doesn't require memorising anything. For may years, the above commands (and ifconfig) were all I knew about unix and were enough to get by on.

Once you can use the above commands, learn to use man (the manual). for instance, the command **man ls** will show you all the options available such as ls -lh. Even if you don't remember the letters, you can learn a lot about what a program can do, what options are available. Looking up which letter does it when you need to is quick. From there, I don't know. I think I learned just the odd command here and there, some of which I thought "that's useful, I must remember that one".  Many years later, I thought "grep looks really useful, I'll try to learn some basics of that". Then sed. But it depends what you regularly do as to which and how many command-line programs you learn to use. 

I don't cram commands in for the sake of it. I learn the odd one every now and again because I think it may be something I will find useful repeatedly. It really is like building up your own toolbox, one at a time with "Oh, that's useful.".

The look around commands pwd, cd, ls, cat, less and an editor are enough to get you out of a hole (perhaps along with cp, mv, rm) and between them give you the capabilities that a GUI file manager gives you. Those, I strongly recommend you learn (be careful with cp, mv, rm). As for the rest, take it easy, try out interesting commands that you see on these forums, and remember the ones that you think are worth remembering. Some are awesomely powerful and tricky to get right (those two seem to come together).

---

### Post by mastablasta on 2013-03-29
not sure if you need profesional help or not. 

but i do know that learning what command does helps me understand it. and people only fear what they do not know.

once you name an object you can get control over it. ;-) [in mental sense ofcourse - you can not control something that is unknown, with no name]

---

### Post by neu5eeCh on 2013-03-29
You **should** be scared. Linux terminals are designed to sense the proficiency level of the user. The less proficient you are, the more it will prey on your naivety. Like a bad dog, it will sneak into your kitchen and eat the binary waffles from the top of your kitchen table. It will chew on the perls in the jewelry box of your hard drive. It will lap up the open source milk in your refrigerator. It will pull the stuffing out of your children's favorite plush software. Nay, I say unto you, you **should** be scared of the terminal. <--- Humor.

Just start with the easy commands. Back when dinosaurs roamed the earth, before the appearance of Homo-Linuxus, DOS ruled the earth. DOS was all command lines. Switching to Linux, for me, brought back fond memories of DOS. Just copy & paste the commands you need. I basically don't use terminal for anything other than apt-get, locate, and deb related commands. Occasionally there are the obscure, specialized and incredibly useful commands - batch converting files, burning ISOs to CDs or DVDs, changing permissions. I always have to look that stuff up.

---

### Post by linuxvstheworld on 2013-03-29
I used to be terrified of any terminal, even a Windows command prompt. If you know what exactly it is you are doing in the terminal and understand the basic commands, you feel comfortable with it. Avoid being a root user as well, unless it is absolutely needed to do something on the system, and you are very comfortable with the terminal. Once you are, it's a wonderful thing.

---

### Post by argonvegell on 2013-03-29
Thanks for the answers.  I will try learning the commands of the terminal, but I still won't be too adventurous about using it though, the threat of damaging my system is still clear in my head lol.

---

### Post by linuxvstheworld on 2013-03-29
Follow what [**[COLOR=#000000]montag dp[/COLOR]**]("http://ubuntuforums.org/member.php?u=1749357") said > Also, adding the following lines to your ~/.bashrc file should help make  sure you don't accidentally delete something without meaning to:

alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i' 
so if you are trying to delete something or move or copy something it will say are you sure, just so you can revise what it is you're doing and are absolutely sure what you're doing without messing something up without knowing.

---

### Post by oldos2er on 2013-03-29
argonvegell, click the "I want to tell you..." link in my sig, it's an introduction to and tutorial about the terminal which I've personally found very useful.

---

