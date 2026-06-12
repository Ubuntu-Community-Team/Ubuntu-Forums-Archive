---
title: "hello everybody.."
date: 2009-10-02
forum: The Cafe
---

### Post by nothingman02 on 2009-10-02
Am an absolute newbie and just wanted to get in here and say hello....

Although from a mech engg background, I have recently opted to change my career to the field of Computers...Unfortunately, the only thing I have now is the interest and enthusiasm backed by very little knowledge.I have learnt the basics of OS, h/w  and programing etc myself and have just installed ubuntu (jaunty) and completely removed vista on my lenovo g550 (works right out of the box including wireless - for anybody curious about distros for lenovos).

ANyway, I am seriously contemplating a career as a Sys admin but am aware that I would have to start off at a lower level. I am planning on some certs such as LPIC-1 or RHCT. THe problem is that I am very new and having trouble figuring out WHAT to learn and what to IGNORE. Its vast and time consuming and looks like a continuous learning process. Are there any steps in this learning process? As in what to learn and when?

As mentioend, I have learnt the basics of OS, basic linux commands nad and am trying to understand the file structure and this is where I am getting stuck. I cant seem to understand -
1) Most of the directories and their sub directories. Ex: etc, usr, var etc.
The trouble especially is with respect to the outputs the shell spits out for any commands. Cant understand these outputs.

SO, do I need to know programming? Do I need to study 'linux internals'? ANything in particular? I need some procedure. Some sort of a guide/steps for studying and any help would be really appreciated.

Thanks for the help.

---

### Post by LowSky on 2009-10-02
Welcome to the forums.

Why do you want to be a system administrator? 

If you want to be certified in Linux the RHCT is a better way to go and I think more repected as a certification. Getting certification in Microsft products would be a good idea as well. Regardless of what you think of them the world still relies on their software as well, and when starting out its best to have a broad knowlege.

---

### Post by NightwishFan on 2009-10-02
Hi, and welcome! :P

About the file structure, though on some distros it is a bit different I think:
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

A good thing to learn is the bash shell and shell scripting. You can control a Linux system from the command line doing so.
Beginner: [http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)
Advanced: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Many commands do not give output whenever they run. Those that do generally give you plain english.

Some commands to know:
[LIST]
[*]man *commandname* - Help about a command
[*]apropos *searchterm* - Search for a command
[*]cd *directory* - change to a directory
[/LIST]

You can use CTRL+C to interrupt and cancel a command whist in a terminal. You can also use TAB to autocomplete a directory or command you are typing.

As for programming, I have heard python is easy, and it is installed by default in Ubuntu.

Have fun, and please ask if you have any questions. There are Ubuntu links and tutorials in my signature.

---

### Post by nothingman02 on 2009-10-02
HI lowsky and nightwishfan,
Thanks for the quick replies. 
Thanks for the info about RHCT and also the links. I have already seen the first link. In fact I have a bunch of saved links and a bunch of books and material downloaded from scribd.

THe later two links are great. I am gonna start learning shell scripting and also on python. Is it just ubuntu or are all Linux distros written in python? or C? 
I also am looking right now at 'linux internals' from linux  over here;

[http://learnlinux.tsf.org.za/courses/build/internals/](http://learnlinux.tsf.org.za/courses/build/internals/)

Do I really need to learn all that? WHat I am looking to achieve for now is to be able to handle myself as a junior sys admin. Install, configure, troubleshoot s/ws, workstation to the n/ws and such...I am looking for a preparation path (for a non IT guy) to get to that point.

Im afraid I am not from a CS background and the outputs are not in plain english to me and how I wish they were! For instance, I am clueless when I look at the o/p for :
 - less /etc/passwd
So I was wondering if I shuld learn;
1) programming language (in which the kernel/shell etc are written)
2) Linux internals

I am trying to pick out each and every dir and sub dir in linux and study and understand each and every file out there ! BUt it keeps taking me back to 1) and 2) above. I mean how do I understand all these files in these directories. 

Once again thanks for the help. You can tell I am pretty clueless I suppose but watch me in the future..:)

---

### Post by Kaizzer on 2009-10-02
Nice thread by the way ... im also a newbie in Linux world and im looking forward of what people with more experience and knowledge can guide to people like us with more enthusiasm of learning than anything else.

---

### Post by cariboo on 2009-10-02
One of the requirements of the job is that you get to know the terminal really well, most admin functions need to be done in the terminal.

> less /etc/passwd

the above commands has an output that looks like this:
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
me:x:1000:1000:Me,,,:/home/me:/bin/bash
gdm:x:103:111:Gnome Display Manager:/var/lib/gdm:/bin/false
```

pressing the space bar will give you more output.

---

### Post by HarrisonNapper on 2009-10-02
> **cariboo907 said:**
> One of the requirements of the job is that you get to know the terminal really well, most admin functions need to be done in the terminal.



the above commands has an output that looks like this:
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
me:x:1000:1000:Me,,,:/home/me:/bin/bash
gdm:x:103:111:Gnome Display Manager:/var/lib/gdm:/bin/false
```pressing the space bar will give you more output.

Wouldn't the space bar thing only be applicable to ```
less /etc/passwd |more
``` or is it automatically piped to the more command?

---

### Post by nothingman02 on 2009-10-02
HI cariboo907,
thanks for the reply.

Not clear im afraid. My doubt wasnt so much **about** the output as much as **what the output meant.**

I cant make anything of the output of that or for that matter most commands and hence was wondering if there is something I need to study? Programming? Linux internals? 

Im used to windows and never knew what happeneed over there. Now I am trying to understand things/...
The other problem Im having for instance is, if I download a s/w;
-what are all the files that are being downloaded (packages +dependencies)
-where are they saved? 
-how do I discriminate/discern those files, which file means what etc..

thanks for the help.

---

### Post by HarrisonNapper on 2009-10-02
[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/index.htm](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/index.htm)

---

### Post by thrud00 on 2009-10-02
If you really want to get to know how linux works under the hood, a good place to start would be [http://www.linuxfromscratch.org](http://www.linuxfromscratch.org) . Alternatively check out one of the oldest distro's, Slackware which still used by purists and many of the top linux guru's cut their teeth on that. One reason Slackware is a good teach aid, is that it doesn't really try to do anything for you, you have to do it all your self.

---

### Post by unutbu on 2009-10-02
> **nothingman02 said:**
> My doubt wasnt so much **about** the output as much as **what the output meant.**

The format for the /etc/password file is 
```

login name:password:user ID:group ID:user name:home directory:command interpreter
```

Each line consists of 7 fields separated by colons.

You can read all about it by typing
```

man 5 password
```

> 
I cant make anything of the output of that or for that matter most commands and hence was wondering if there is something I need to study? Programming? Linux internals? 

man pages vary in difficulty. Some are easy to understand, some are not. Asking questions here could be helpful. Looking stuff up here: [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php) might also help.

> The other problem Im having for instance is, if I download a s/w;
-what are all the files that are being downloaded (packages +dependencies)

Using the GUI, Click System>Admin>Synaptic, then right-click on an installed package. Select "Properties">"Installed Files".

Using the command-line interface (CLI): 
```
dpkg --listfiles PACKAGE
```
will list all files installed by the package called PACKAGE.

You can find out about packages that you have not yet installed, by using the ubuntu package search engine at [http://packages.ubuntu.com/](http://packages.ubuntu.com/).
> 
-where are they saved? 

The packages themselves are saved in /var/cache/apt/archives. Ubuntu automatically cleans this directory out periodically, so it may not contain a full list of all the packages you install.

> 
-how do I discriminate/discern those files, which file means what etc..

Sometimes it will be obvious by looking inside the files, sometimes not.
There is no one place to find out this information. 
Google, ask here at the forums, read source code.
If you type
```

man hier
```
you will get an overview of what type of files is put where in a typical Linux filesystem. That might help a little.

You may also find this free book helpful orientation:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by nothingman02 on 2009-10-02
Thanks for the replies everybody. Unutbu, thanks for the detailed explanation. Its very helpful. I am going to use the information provided and do some studying. Im excited! :) I wasnt getting anywhere the last 2 days...thanks again.
im gonna look into slackware as well and thanks for the link on the lecture notes, docs at mit.

---

### Post by Firestem4 on 2009-10-02
> **nothingman02 said:**
> Thanks for the replies everybody. Unutbu, thanks for the detailed explanation. Its very helpful. I am going to use the information provided and do some studying. Im excited! :) I wasnt getting anywhere the last 2 days...thanks again.
im gonna look into slackware as well and thanks for the link on the lecture notes, docs at mit.

Your level of enthusiasm is great to see, and if you can keep with it you will learn Linux in no time! 

There is a lot to know about computers so don't be disappointed or feel overwhelmed. It takes time to learn all of this and become familiar with it. I've only been using Linux for the past 9 months, but I am already fairly advanced with it (with the exception i still have not learned much shell scripting). At the same time so much if it is still alien to me.

This link should help you understand more about the Unix File Hierarchy Standard. (/var, /root, etc).

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)
EDIT: I did not notice the previous poster's "man hier" comment. But i'll leave the link up regardless.

If you are used to windows it may help you to make direct comparisons, for example "/" (root) in Unix is the equivalent of "C:\" in windows. 

"/usr/bin/" is the equivalent to "C:\Program Files\" in windows.

Also I would recommend that you use a system that you don't care about breaking. If you will use your linux laptop for work, do not use it to test things out in because you may ruin your OS or data. This way, you can experiment and find out what things do, or don't do..or things that you don't want doing what they do, accidentally lol.

---

### Post by Junkieman on 2009-10-02
The nice thing about Ubuntu is that its elegantly simple to use, and it allows you to get as in-depth as you can handle.

In your system preferences -> keyboard shortcuts, find the 'Run Terminal' item and give it a shortcut (I like Ctrl+Alt+T) and that right there is great incentive to use the terminal more often :)

Play around by installing new software: you can do everything via the terminal that you can do with the graphical dialogs (and more!). The [apt how to]("http://www.debian.org/doc/manuals/apt-howto/") is a great reference, go through the sections that interest you, and you will pick it up in no time :)

Shell scripting is also the way to go, I still have to get stuck in that myself, the same goes for Python. 

Good luck and welcome to the forums!

---

### Post by nothingman02 on 2009-10-03
thanks for the info and replies guys. I have been studying the links and my own material. I got a bunch of stuff from scribd.com....I am looking at the debian link right now about apt howto and its a great link too. Thanks again for the help. Hopefuly, Id be somewhere in 2 weeks. I intend to take up a certification this month. Im gonna do nothing but study tilll then. And its so much easier with help from these forums.

---

