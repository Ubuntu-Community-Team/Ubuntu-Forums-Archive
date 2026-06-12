---
title: "I should stick to only one distro, right?"
date: 2008-10-30
forum: The Cafe
---

### Post by faraz_k86 on 2008-10-30
My problem is that there are too many distros to choose from.

And i want to use them all, and I am not that good in linux as i dont know all the advanced terminal commands, all i know are apt-get and remove commands :)

So I try ubuntu for a month and then i want to change and try opensuse and then fedora and so on.


But by doing so i dont think i am learning linux, as all of them have seperate commands.

After installing mandriva i realized that sudo apt-get does not work here and they have their own command.

Why do all of them not have the same terminal commands?

And is it true that every distro has its own terminal commands?

---

### Post by nothingspecial on 2008-10-30
No, distros have different package managers. cp, ls, mv, etc are the same.

---

### Post by Bölvaður on 2008-10-30
I was wanting to use Ubuntu + some none debian based distro, like fedora.

The terminal commands are universal, as the same commands are in BASH everywhere. I cant remember what machintosh uses, but _it is **very** similar._
The big difference is in what programs you have, like apt-get, which is a program, is not in the default fedora.

It is good to learn to use different package managers and not only apt-get, it will make you a stronger command line warrior.

---

### Post by chucky chuckaluck on 2008-10-30
here's a tutorial that will teach you some basics that apply to all linux distros - [http://linuxsurvival.com/](http://linuxsurvival.com/)

i'd also recommend the linux pocket guide from o'reilly - [http://www.amazon.com/gp/product/0596006284](http://www.amazon.com/gp/product/0596006284)

---

### Post by snowpine on 2008-10-30
Install Virtualbox, then you can try out lots of distros at the same time! :)

---

### Post by notwen on 2008-10-30
If you know apt-get already and are comfortable w/ using it, I'd recommend trying any Debian-based distro.  

ie.
Debian
sidux
Mint
Knoppix

Keep in mind you should research each to get an idea of what you're getting yourself into before installing.  =]

---

### Post by barbedsaber on 2008-10-30
Linux comes in two families
Debian and red hat
Ubuntu is from the Debian family and
(I am going to stop there, because I don't want to give the wrong info. Can someone please finish it off for me.)

---

### Post by FuturePilot on 2008-10-30
Linux is Linux. The core set of commands is the same no matter what distro it is. If you know those, they will work on any distro. The biggest difference would be anything related to the package manager, other than that, there's only minor differences.

There's nothing wrong with trying other distros. It's fun. I like to play around with other distros. But I just stick with Ubuntu because it works the best for me.

---

### Post by Dragonbite on 2008-10-30
> **faraz_k86 said:**
> My problem is that there are too many distros to choose from.

And i want to use them all, and I am not that good in linux as i dont know all the advanced terminal commands, all i know are apt-get and remove commands :)

So I try ubuntu for a month and then i want to change and try opensuse and then fedora and so on.


But by doing so i dont think i am learning linux, as all of them have seperate commands.

After installing mandriva i realized that sudo apt-get does not work here and they have their own command.

Why do all of them not have the same terminal commands?

And is it true that every distro has its own terminal commands?

I'm the same way.. I get comfortable and then want to change it. Thing is, I usually come back to Ubuntu because[LIST]
[*]I am familiar with it
[*]I can get up-and-running very easily and almost in my sleep
[/LIST]

Having gone to openSUSE and Fedora and coming from Gentoo I can say that the packaging system is the biggest difference, otherwise Linux is Linux, KDE is KDE, Gnome is Gnome, etc.

Other than that, hardware detection is not created equally and the installer can influence things quite a bit.

If you are going to try a different distro, then make sure you take the time to LEARN the other distro.  I spent time with openSUSE and it took me a while to get used to and understand Yast.  On the same line, I haven't taken enough time to learn Yum and the repositories yet to be comfortable so if I go Fedora or CentOS then I know I have to take some time to get comfortable with it.

At least the terminal commands are usually the same, just where each distro puts the config files may be different!

---

### Post by faraz_k86 on 2008-11-13
k so after reading the replies i felt confident that all the distros are the same as far as the terminal goes.

So i installed mandriva 2009 and what do i find? apt-get is not applicable there, instead i have to use a command "urmpi" or something.

Now this is what i was talking about in the first place. :/

---

### Post by igknighted on 2008-11-13
> **faraz_k86 said:**
> k so after reading the replies i felt confident that all the distros are the same as far as the terminal goes.

So i installed mandriva 2009 and what do i find? apt-get is not applicable there, instead i have to use a command "urmpi" or something.

Now this is what i was talking about in the first place. :/

"apt-get" is a package management _program_, which (as mentioned above) is the primary difference between distros.  urpm* ~ apt-*, and rpm ~ dpkg.  There are some other tools (Mandriva has an awesome toolkit called drak* that Ubuntu doesn't have, for example), but its the same kernel and all the core commands (cp, mv, etc.) are all the same.  The config files should mostly be the same to (unless you are talking about package management).

EDIT: See this page to relate what urpm* command is the equivalent for apt-* (and if you really want, alias the apt command to the urpm* one and never know the difference...) [http://distrowatch.com/weekly.php?issue=20081013#feature](http://distrowatch.com/weekly.php?issue=20081013#feature)

---

### Post by bodhi.zazen on 2008-11-13
> **faraz_k86 said:**
> k so after reading the replies i felt confident that all the distros are the same as far as the terminal goes.

So i installed mandriva 2009 and what do i find? apt-get is not applicable there, instead i have to use a command "urmpi" or something.

Now this is what i was talking about in the first place. :/

I find 80-85% of the commands are the same. Once you know how the file system works it is easier to find your way around (hint start in /etc).

The "general" advice is to install the distro with the best hardware recognition. If there is more then 1, go with the online community (that is who will be providing you support after all). Learn that one system inside and out. Then go to second distro.

I do not think there is any problem with distro hoping as long as you are doing so to learn and not trying to find the distro that "just works" without poking under the hood.

Now if you do not want to learn, go with the distro that best fits your hardware and if you have a problem, install a differnet distro untill you get it right.

---

### Post by Mardoct909 on 2008-11-13
Try a new distro. Go ahead. I've been trying distros non-stop since I started using Linux, and I now have less of a feeling that there is something better out there I'm missing, and I also have learned a lot from the likes of arch and Gentoo Linux.

---

### Post by kimda on 2008-11-13
I think its good to try out as many as you can. At least the mayor ones like Fedora (RedHat), OpenSuSe (Suse), Mandrake and Debian (which is like Ubuntu ). The biggest differences are in the packaging and locations. In RedHat for example apache configs are in /etc/httpd/ instead of /etc/apache like Debian. 

If you know a bit about the commandline try out some of the BSD's as well. With virtualbox or vmware its really easy to try them out. And the best thing with virtualisation is that if something goes wrong you can just start over. Learn also the commandline stuff. I know it takes time but once you know a bit you will be amazed at how much things you can do with it. 

I bought  Running Linux from Oreilly when I started with Linux. It coveres a lot of stuff, like commandline, X, webserver etc.. I can really recommend it.

---

### Post by init1 on 2008-11-13
> **chucky chuckaluck said:**
> here's a tutorial that will teach you some basics that apply to all linux distros - [http://linuxsurvival.com/](http://linuxsurvival.com/)

i'd also recommend the linux pocket guide from o'reilly - [http://www.amazon.com/gp/product/0596006284](http://www.amazon.com/gp/product/0596006284)
Yeah, I have that book. It's a useful reference.

---

### Post by faraz_k86 on 2008-11-14
Thx for the replies guys. 

I was thinking since mandriva is not based on debian, then .deb packages will not work on it, right? 

so playdeb.net wont work either? or getdeb.net?

what packages are used in mandriva linux in place of .deb?

---

### Post by mssever on 2008-11-14
> **faraz_k86 said:**
> what packages are used in mandriva linux in place of .deb?
Google or the Mandriva website should be able to answer that. I'm guessing RPM, but that's just a guess.

---

### Post by derekr44 on 2008-11-14
> **faraz_k86 said:**
> My problem is that there are too many distros to choose from.

And i want to use them all, and I am not that good in linux as i dont know all the advanced terminal commands, all i know are apt-get and remove commands :)

So I try ubuntu for a month and then i want to change and try opensuse and then fedora and so on.


But by doing so i dont think i am learning linux, as all of them have seperate commands.

After installing mandriva i realized that sudo apt-get does not work here and they have their own command.

Why do all of them not have the same terminal commands?

And is it true that every distro has its own terminal commands?

Arch Arch Arch :D

That's how I learned just about everything I know.  But you're talking apples and oranges here.  Terminal commands are universal in Linux.  When you are talking about apt-get, you are talking about package managers.  Package managers and terminal commands are two different things.  Most distros will use their own, but apt-get is widely known because of Debian roots.

However, if you want to learn the nuts and bolts of your basic stuff, Arch is a great way to learn it.  It has a bit of a learning curve, but the best way to learn is by immersing yourself in it.

---

### Post by derekr44 on 2008-11-14
Oh, and on another note.  The best way to try out all of them is to get VirtualBox.  That way you can test out the distros and you won't end up screwing up your existing system in the process.

---

### Post by regomodo on 2008-11-14
#

---

### Post by cariboo on 2008-11-14
I always say that once you learn how to use a computer, it doesn't matter what OS you are using. You might get frustrated at things not working the way you are used to,  but if you keep at it within a couple of hours you should be able to do most of the day to day tasks that you do on any other computer.

I think that is the problem with most educational facilities, they only teach you how to use Windows and Office and absolutely nothing about operating a computer.

Jim

---

### Post by cardinals_fan on 2008-11-14
> **faraz_k86 said:**
> 
But by doing so i dont think i am learning linux, as all of them have seperate commands.

After installing mandriva i realized that sudo apt-get does not work here and they have their own command.

Why do all of them not have the same terminal commands?

And is it true that every distro has its own terminal commands?
That's the package manager - only a couple commands.  Otherwise, it's all the same CLI-wise.

There's absolutely nothing wrong with using multiple distros.  You'll learn more from trying many, and you may even use several on a regular basis.  I dual-boot Arch (for testing/messing about) and Slackware (for getting things done).

---

### Post by jimi_hendrix on 2008-11-15
i noticed no one mentioned configuration

some distros like ubuntu take care of this automatically

others like arch want you to edit things like your xorg.conf to fit your computer

---

### Post by ssam on 2008-11-15
distrowatch made a good cheat sheet for the different package managers.
[http://distrowatch.com/weekly.php?issue=20080922](http://distrowatch.com/weekly.php?issue=20080922)

the rest of their site is good if you want to try out a range of distros.

---

### Post by fballem on 2008-11-15
apt-get is a command that is specific to a package manager (in this case Debian and its derivatives, including ubuntu). Mandriva uses a different package manager, as does Fedora, as does ...

It might be useful to think of Linux as the core operating system, to which is added a Windows Manager (GNOME, KDE, etc.), and a package manager.

The core Linux operating system commands (cp, mkdir, rm, etc.) will be the same across distros.

There may be variations in how different distros implement the Windows Manager, but most of the commands for GNOME will work in distros that use GNOME, most of the commands for KDE will work in distros that use KDE.

The commands for the package managers will be very different from one distro to another. I believe the Mandriva has its own package manager. Aptitude is one of the package managers that is used in Debian and its derivatives. Yum is one of the package managers that is used in Fedora and its derivatives.

The command that you keep trying (apt-get) is a package manager command - specifically for Debian. Since Mandriva doesn't use Aptitude, it is unlikely that apt-get will work in Mandriva. It will work in Debian.

Hope this clarifies things a bit,

---

