---
title: "How to learn Linux?"
date: 2010-12-01
forum: The Cafe
---

### Post by SebSmith on 2010-12-01
I have no idea how to learn linux. i am a college student information systems major but i have not started my program. i was wondering if there was anyway i could start learning how to do advanced things. i run ubuntu 10.10 solely on my notebook. luckily it is user friendly or i would be lost. any suggestions on how to learn? what is code or something?

sorry if this is a stupid post

---

### Post by thatguruguy on 2010-12-01
Buy a book or two.  Then, start experimenting with your own system.  The best way to learn about something is to break it and then fix it.

---

### Post by SebSmith on 2010-12-01
what books do you recommend?

---

### Post by matt_symes on 2010-12-01
Hi

1. Get books on Linux and Ubuntu. Both paper and electronic types.
2. Read the community help sections and surf the net.
3. Use the forums, ask questions here.
4. Download podcasts (E.G Linux reality, going Linux, etc).
5. Play, play, play on a system that you don't mind destroying. Virtual machines are excellent for this.
6. When you want to something using the GUI see if you can find out how to do it via the command line.

What is it exactly you want to learn.....?

How to use the GUI?
How to use the terminal?
Bash programming?
Programming in other languages?
Sys admin?.....

Kind regards

---

### Post by SebSmith on 2010-12-01
well idk anything about linux except terminal is used for commands. i was a proficient xp user and id like to be a proficient ubuntu user. i want to learn your entire list!!

---

### Post by matt_symes on 2010-12-01
Hi

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

How to use the GUI?

[https://wiki.ubuntu.com/ubuntu-manual](https://wiki.ubuntu.com/ubuntu-manual)

How to use the terminal?

Courtesy of teobigusgeekus

[http://sourceforge.net/projects/linu...2.pdf/download]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download")

Bash programming?

[http://tldp.org/LDP/bash-Beginners-guide/bash-Beginners-guide.pdf](http://tldp.org/LDP/bash-Beginners-guide/bash-Beginners-guide.pdf)
[http://tldp.org.LDP/abs/abs-guide.pdf](http://tldp.org.LDP/abs/abs-guide.pdf)
  
 Programming in other languages?

One thing at a time. You need to pick some languages first. :)

Sys admin?.....

[https://help](https://help).**ubuntu**.com/6.10/**pdf**/**ubuntu**/C/serverguide.**pdf**

EDIT: Above is for 6.10 and might be a bit out of date. (An old bookmark of mine)

[http://www.ubuntugeek.com/download-the-gnulinux-advanced-administration-pdf-guide.html](http://www.ubuntugeek.com/download-the-gnulinux-advanced-administration-pdf-guide.html)

Podcasts

[http://www.linuxreality.com/](http://www.linuxreality.com/)
[http://goinglinux.com/](http://goinglinux.com/)

Search on podcast alley or itunes

[http://www.podcastalley.com/](http://www.podcastalley.com/)

I think that's enough to get you started.

... and _use_ these forums. There are no questions too basic here and _plenty_ of people ready to help.

Good luck. :popcorn:

Kind regards

---

### Post by Quadunit404 on 2010-12-01
Learning Linux is easy if you are capable of learning quickly. I know I am :wink:

I'll give you a rundown of some basics:

- There is no C:, D:, E:, whatever drive. Everything in Linux is mounted to the root file system, which itself is mounted to / - a forward slash (a la what you'd see in a URL.)
- Likewise, there are no folders named System32, Program Files, SysWOW64, Users and so on. The rough equivalents of Windows folders to Linux folders are:
System32/SysWOW64 - /lib (and if you're on 64-bit, add in /lib32 and /lib64 as well)
Program Files - /usr and /usr/local
Users - /home
- There is no Application Data or AppData folder hidden in your home folder as well. Every program that stores data creates a folder beginning with a dot to hold your stuff; in *NIX, files and folders beginning with a dot (e.g. .mozilla) are hidden.
- You can use relative paths such as ~, which basically is a shorter and faster way of saying /home/<username>
- Viruses for Linux DO exist, but they run with your current permissions (e.g. the most they can damage is your home folder) and many of them deactivate on reboot. There was one incident where a virus masquerading as a screensaver did some damage, but that was because it was packaged as a .deb installer and in order to install such packages you need to give the package installer root permissions to do so.
- You do not need to hack libraries in order to use custom themes. Many desktop environments and window manager support theming without hacking out of the box - just grab a theme from somewhere like GNOME-Look, open up the Appearance Preferences dialog, install the theme (you may need to install it first) and you're good to go!
- There is no registry to worry about.
- You can run Windows programs through [Wine]("http://www.winehq.org/"). Be aware that not every Windows program works yet. You can check which ones do and don't [here.]("http://appdb.winehq.org/")

Whew, that was a mouth- err, textful. And remember, the best way to learn something is to communicate with the people who know what you are trying to learn.

---

### Post by lisati on 2010-12-01
One thing I've found helpful is finding something specific to do, and then research here and elsewhere how to do it.
I started with a basic installation back in 2007 with a basic installation. Back in January 2010, I started hosting a website and an email server on one of my machines, and over the months have added various bits and pieces, including a blog, webmai, and slowing refining its handling of spam.

---

### Post by matt_symes on 2010-12-01
Hi

> **lisati said:**
> One thing I've found helpful is finding something specific to do, and then research here and elsewhere how to do it.
I started with a basic installation back in 2007 with a basic installation. Back in January 2010, I started hosting a website and an email server on one of my machines, and over the months have added various bits and pieces, including a blog, webmai, and slowing refining its handling of spam.

+1 lisati. Have a project does focus ones mind.

Kind regards

---

### Post by akand074 on 2010-12-01
Best way to learn how to use Linux, is to use Linux. Honestly. I never touched a book or anything. Just use it as your main OS for everything. Whenever you run into a problem, research and ask in the forums about it. You'll get the hang of it on your own. Just like you got the hang of Windows XP. Just reading a book doesn't help much I find. But, when you have specific things you are trying to do, then the internet and books can be helpful to learn how to get something done.

---

### Post by FuturePilot on 2010-12-01
Forget books. Set up a system that you can break and not have to worry about losing anything important. Then have at it. Find a guide on how to do something specific and follow it. Then go beyond that and start customizing it. Then go beyond that and make it secure if it's some kind of server. You can even go beyond that and figure out how to integrate it with other things to make it even more useful.

I have never touched a Linux book.

---

### Post by matt_symes on 2010-12-01
Hi

If the OP is going to study this, he will have to read books. Comes as part of the territory :o. You do learn fast with experimentation though.

@OP. Look at VMWare or Virtual box (google both). They will allow you to virtualise a system to break and fix to your hearts content.

Kind regards

---

### Post by gamebusterzade on 2010-12-01
> **akand074 said:**
> Best way to learn how to use Linux, is to use Linux. 

i agree with this.  this is how i learned how to handle Linux

but if u need to read to learn try a magazine like: Linux pro magazine or Ubuntu user 

there are more but these can get u started

---

### Post by Shining Arcanine on 2010-12-01
> **SebSmith said:**
> I have no idea how to learn linux. i am a college student information systems major but i have not started my program. i was wondering if there was anyway i could start learning how to do advanced things. i run ubuntu 10.10 solely on my notebook. luckily it is user friendly or i would be lost. any suggestions on how to learn? what is code or something?

sorry if this is a stupid post
Install a virtual machine and then install Gentoo Linux inside it. You will learn how to use Linux very quickly.

[http://www.gentoo.org/doc/en/handbook/](http://www.gentoo.org/doc/en/handbook/)

---

### Post by FuturePilot on 2010-12-01
> **matt_symes said:**
> Hi

If the OP is going to study this, he will have to read books. Comes as part of the territory :o. You do learn fast with experimentation though.

@OP. Look at VMWare or Virtual box (google both). They will allow you to virtualise a system to break and fix to your hearts content.

Kind regards

What I mean is don't rely solely on books. I see this all the time. Someone wants to learn Linux and they immediately go for books. Now maybe some people learn better though reading, but there's one shortcoming of books that you will run into regardless of how you learn. Linux books teach you things as they would happen in a pristine environment which is almost never the case in the real world.

---

### Post by t0p on 2010-12-01
The Linux Documentation Project ([tldp.org]("http://tldp.org"))is a great resource for newbies, gurus, and the rest of us!  You'll find stuff there aimed at just about every level of Linux knowledge/ignorance.

This site ([Ubuntuforums.org]("http://ubuntuforms.org"))is also a great place to learn about Linux in general and Ubuntu in particular.  The Ubuntu community is by and large very friendly and helpful.  You won't get any of those nasty "RTFM" responses here!

I'm afraid I don't agree with FuturePilot's stance on books.  I haven't touched many Linux books... but only because I have a stack of them in .pdf format!  There are countless books about Linux that you are free to copy.  I'm afraid I can't give you any specific titles as I'm not at my desktop machine right now, but one useful book that comes to mind is called something like *The Linux Dictionary*.  It explains some of those scary-sounding topics in easy-to-follow language, and helped me pierce the "mystique" that some newbies get put off by.

To really learn "about Linux", you really need to clarify in your mind what it is you want to do with Linux.  It's a vast subject, as in many ways the story of Linux encompasses the history of the internet and of computing itself!  Sit down and make a list of the subjects that you really feel you need or want to know about; then try concentrating on those subjects first.  Everything's interconnected at some level, so you'll get a pretty good general grounding even when concentrating on just a few subjects.  For example, a while back I decided I really wanted to know more about Linux in networking.  So I googled up a heap of info about Linux networks, and in the process I learned a whole heap of other stuff!

I hope all this talk about heaps of info and endless tomes hasn't scared you off!  If all you want to do is learn how to use Linux competently, there isn't really need to go anywhere near the more arcane stuff.  Nowadays there are lots of wonderful applications with clear, intuitive user interfaces that you'll be able to pick up in no time at all.  You certainly don't need to be a computer expert to use Linux!

---

### Post by linuxforartists on 2010-12-01
Here are two books that I found to be *hugely* helpful in learning Ubuntu:
[URL="http://www.amazon.com/Ubuntu-Non-Geeks-Pain-Free-Get-Things-Done-Guide/dp/159327257X/ref=sr_1_1?ie=UTF8&s=books&qid=1291255985&sr=8-1"]
Ubuntu for Non-Geeks[/URL] - This is the book I wish I had when first started with Ubuntu and didn't know how to make things work. Nicely organized around chapters for multimedia, productivity, etc.

[Ubuntu Kung Fu]("http://www.amazon.com/Ubuntu-Kung-Fu-Tricks-Hints/dp/1934356220/ref=sr_1_1?ie=UTF8&s=books&qid=1291255994&sr=8-1") - Chock-full of tips, tricks, and hacks for doing all sorts of useful and cool things in Ubuntu. It's getting a little outdated, since it was published in 2008.  But every time I open it up, I learn something interesting.  If I even applied 25% of that content, I'd feel like a power user. Bonus is that awesome title!

Like others have said, also spend a lot of time exploring the system, checking out the menus, and tweaking settings.

---

### Post by sidzen on 2010-12-01
> **SebSmith said:**
> what books do you recommend?

Try starting with Mike McGrath's [Linux in Easy Steps]("http://www.ineasysteps.com/books/details/?9781840783513").  It helped me!

---

### Post by buddyd16 on 2010-12-01
The arch linux wiki is also an excellent source of information.

---

### Post by Starks on 2010-12-01
Jumping right in.

---

### Post by zipteye on 2010-12-02
> **FuturePilot said:**
> Forget books. Set up a system that you can break and not have to worry about losing anything important. 

I have never touched a Linux book.

Or go ahead and break it.
Then crap your pants and look on the web or come back here on a different computer for help.

I'll never forget the time I locked out my permissions to the entire file system on my old iMac. (Darwin Unix, Cshell).
The poor thing wouldnt even boot.
Found a IRC channel on a different computer and someone saved my butt.

Good times! :)

Also... learn how to install programs from source (Which I had forgotten how to do when I downloaded Ubuntu recently.)
It was a common thing with Darwin unfortunately.

./configure
make
sudo make install


Check out the Ubuntu pocket guide book thats a free pdf.
Someone posted a link here. Somewhere...

---

### Post by SebSmith on 2010-12-02
Thank you all soooo much. i can not even begin to describe my gratitude. i am proud to run linux and proud to be part of this community.:D

---

### Post by Hexley on 2010-12-02
I will say that these are my favourite books:

Running Linux 5th edition (or if there is a newer one)
Linux in a nutshell 6th edition (or newer)
Linux bible (this one just shows you how to install different distros and some will follow on a dvd and cd)

It's totally worth it, good luck.

---

### Post by rg4w on 2010-12-02
One of my favorite ways to learn Linux is to read these forums.  

Almost every day I log in and review the most recent posts - any time I see something that I don't know the answer to and sounds like it might be useful to me down the road (which is often for me <g>), I read the thread to learn what I can from it.

This forum is an amazing resource.

---

### Post by kaldor on 2010-12-02
> **SebSmith said:**
> well idk anything about linux except terminal is used for commands. i was a proficient xp user and id like to be a proficient ubuntu user. i want to learn your entire list!!

First off, experiment with some distros. To get a decent grasp of how Linux distros work install Virtualbox. Virtualbox essentially an OS emulator. Just mount the downloaded .iso and you're good to go :)

I recommend installing openSUSE, Fedora and Debian in a Virtual Machine; they're major distros and learning the querks of each will help in the longrun.

Also, get used to using the Terminal. When you need to copy/paste/move/rename files, use commands; it'll familiarize you with the directory layout as well as the commands.

Or, if you're really adventurous, try Linux from Scratch ;)

None of this will turn you into a power user, but it should help you get a grasp of the OS. And another hint of advice for learning is to not use Windows when you find something difficult. When I started Linux, I got rid of Windows completely and basically forced myself to learn workarounds to issues and such.

Good luck :)

---

