---
title: "I'm about to try Kubuntu from FC6. Some thoughts..."
date: 2007-03-24
forum: The Cafe
---

### Post by knadoor on 2007-03-24
Well just a series of questions really:

1) As of Ubuntu/Kubuntu 7.04, is there a choice on what to install and what not at the start    of the setup program like FC6 does?

2) The way I understand is it that the CD version only has the base, while the DVD version of
     Ubuntu/Kubuntu contains all of the programs like FC6 does right??

3) I had **lots **of trouble getting ATI drivers working under Fedora Core 6, and still do, so I just use VESA mode. Is Ubuntu/Kubuntu better in this aspect? Since I always got "video mode not supported" message in FC6 hence screens not found error.

4) Will the updates and internet work out of the fly? I remember in FC6 to get internet working properly I had to remove IPv6 as root. And to get YUM updates working I had to update its conf files since it couldn't access the repositories.

5) I use LINUX alot for C++ programming as my course requires of it. I've read that Ubuntu is
    poor in development tools and GCC etc. Is this true?? Since I need to use Eclipse, KDevelop
    and from memory I believe...QT designer or something like that???\

thanks :P

---

### Post by Adamant1988 on 2007-03-24
> **knadoor said:**
> Well just a series of questions really:

1) As of Ubuntu/Kubuntu 7.04, is there a choice on what to install and what not at the start    of the setup program like FC6 does?

2) The way I understand is it that the CD version only has the base, while the DVD version of
     Ubuntu/Kubuntu contains all of the programs like FC6 does right??
This is incorrect.  The LiveCD version is the complete Ubuntu distribution, the community touts this as one way that Ubuntu is way ahead of many RPM distributions. 

> 3) I had **lots **of trouble getting ATI drivers working under Fedora Core 6, and still do, so I just use VESA mode. Is Ubuntu/Kubuntu better in this aspect? Since I always got "video mode not supported" message in FC6 hence screens not found error.
 With the latest upcoming release (Feisty Fawn) Ubuntu contains a program called "restricted-manager" which will download and install closed-drivers for you.  It couldn't be any easier.  (Warning: It *is* still beta-ware and is subject to breakage) 
> 
4) Will the updates and internet work out of the fly? I remember in FC6 to get internet working properly I had to remove IPv6 as root. And to get YUM updates working I had to update its conf files since it couldn't access the repositories.
Your internet connection should be usable while you install from LiveCD.
> 
5) I use LINUX alot for C++ programming as my course requires of it. I've read that Ubuntu is
    poor in development tools and GCC etc. Is this true?? Since I need to use Eclipse, KDevelop
    and from memory I believe...QT designer or something like that???\

thanks :P

I can say that there are a lot of development tools in the repos, but as I'm not experienced as a developer I wouldn't know if they're quality.  I know Eclipse isn't in the repos right this moment, but you can get it I'm sure.

---

### Post by Nikron on 2007-03-24
> **knadoor said:**
> 
1) As of Ubuntu/Kubuntu 7.04, is there a choice on what to install and what not at the start    of the setup program like FC6 does?


The default Ubuntu install installs a lot of stuff that you probably wont use, you'll have to weed out what you can later.

---

### Post by Ancheron on 2007-03-24
I have eclipse on my comp. Used it for the lovely MBS project in APCS.

---

### Post by flossgeek on 2007-03-24
> I use LINUX alot for C++ programming as my course requires of it. I've read that Ubuntu is
poor in development tools and GCC etc. Is this true?? Since I need to use Eclipse, KDevelop
and from memory I believe...QT designer or something like that???\

It has all the tools you would have on fedora. You install build-essential for C programming, and eclipse is no issue as it is Java based and once Java is installed any Java application should run from clicking the run script.

---

### Post by qamelian on 2007-03-24
> **Adamant1988 said:**
> I can say that there are a lot of development tools in the repos, but as I'm not experienced as a developer I wouldn't know if they're quality.  I know Eclipse isn't in the repos right this moment, but you can get it I'm sure.

Actually, Eclipse is in the repos, but it doesn't include the c++ module. That needs to be installed using the built in updater in Eclipse.

---

### Post by knadoor on 2007-03-26
Okay I finally got my hands on a 700mb Kubuntu LiveCD.

Though I;m somewhat disappointed, it did detect my sound, internet and printer and they all worked. Except for the printer which is detected but never seemed to print...that's a different story.

My question to you people who say the Live CD has everything are wrong, as can be seen from the picture there is no eclipse and the amount of programs is medicore. I clicked on the unsupported and proprietory and saw no more software prop up, the next button was greyed out. Even though it says 5180 packages available for download.

---

### Post by slayerboy on 2007-03-26
> **knadoor said:**
> Okay I finally got my hands on a 700mb Kubuntu LiveCD.

My question to you people who say the Live CD has everything are wrong, as can be seen from the picture there is no eclipse and the amount of programs is medicore. I clicked on the unsupported and proprietory and saw no more software prop up, the next button was greyed out. Even though it says 5180 packages available for download.


Here's the thing....out of the box, very few distros will install a complete version without more than one cd.  The only two I know of right now are PCLinuxOS and Ubuntu.  What that means is pretty much anything the average user is going to want or need is going to be installed.  Other things like eclipse and non-free stuff you'll have to install separately.  The non-free is like this with ANY distro.

So, yes, out of the box you can have a good distro without having to burn multiple CD's or one DVD.  Granted, if you want to install any other program that isn't installed from the one CD, then you'll have to connect to the repos online and download and install them, such as non-free stuff.

Unless I'm misunderstanding what you're saying, Ubuntu does indeed have everything a regular user needs out of the box with one cd.  Also, remember, Fiesty is still Beta, which means it's still going to be buggy.

---

### Post by cowlip on 2007-03-26
there are things like ubuntu ultimate (dvd) that come with a ton of programs pre-installed.  so you *can* install all those things by default.  Or you can make your own personalized live cd so that you can take it with you or install all these things by default with reconstructer: [http://reconstructor.aperantis.com/index.php](http://reconstructor.aperantis.com/index.php) or [http://ubuntudemon.wordpress.com/2006/08/09/ubuntu-customization-kit-2/](http://ubuntudemon.wordpress.com/2006/08/09/ubuntu-customization-kit-2/)  



also, unless you're using feisty (with the aforementioned restricted driver manager), envy is an easy way to get ati/nvidia drivers. [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)  BTW, as of Feisty, Ubuntu includes the build-essential metapackage so you do get gcc and friends by default

That's weird that all that stuff in Adept is greyed out.  I know in Ubuntu I could open Synaptic and install things  not in the cd from the internet with the livecd (like ntfs-3g, fuse etc)

---

### Post by Tomosaur on 2007-03-26
Obviously the LiveCD doesn't have 'everything'. If you check your /etc/apt/source.list, you will find that the LiveCD uses the CD as a repository. I don't know why they insist on doing this, because it just confuses people - as some packages dissappear and suchlike. If you install Ubuntu, you should modify the sources file post-install to remove the CD repos (or just use Synaptic and modiy them through the GUI), and then run 'sudo aptitude update'. The LiveCD should contain enough software to give you a feel for the installed version, but there are thousands more apps available. You're using the 'dumbed down' frontend for aptitude in that screenshot - the more advanced version is called Synaptic, it should be within your administration menu (but I use Gnome, I'm not sure exactly where it is in the KDE menu, or even whether it's called Synaptic in KDE). In any case, Synaptic uses the same repos, but for some reason shows more available packages. The search function is also better, and the categories are more organized (You will have three 'Development' categories for example: for standard, commercial, and unsupported). Eclipse is in the repos.

In any case - Ubuntu is poor for development right out of the box precisely because it doesn't include the necessary tools. The first package any developer should install with Ubuntu is 'build-essential'. It's a meta package which contains all of the usual development tools.

Welcome to Ubuntu anyway, hope you have fun :)

---

### Post by awakatanka on 2007-03-26
Kubuntu uses Adept to install the prg's. Youre using the simple adept-installer. Look in the sub menu's for the main adept, it can install everything else if you have the right sourcelines active.

---

### Post by knadoor on 2007-03-26
So if I were to install Kubuntu onto my hard disk, it would hopefully use the **online **repositories by default I would imagine, so then I can access the dev tools and etc? :confused: 


And I'm guessing the DVD is like the LiveCD, it'll just install a heap load of programs as one big blob. Anyway..... The real reason Im trying out Kubuntu is because from what I've read it's much easier to get the drivers (video, sound etc) working than FC6 which frustrated the living daylights out of me before I finally got most of them working. :)

Also finally in FC6 there's a tool called "switchdesk," where  you can easily switch between GNOME and KDE via a simple command line in Konsole. I was wondering if Kubuntu had the similar.

EDIT: Sourcelines??? Oh and please note that I haven't installed it yet, I'm just viewing it via the LiveCD as a "tryout". Could that be why the lack of menu items??

---

### Post by Perfect Storm on 2007-03-26
> So if I were to install Kubuntu onto my hard disk, it would hopefully use the online repositories by default I would imagine, so then I can access the dev tools and etc?  

EDIT: Sourcelines??? Oh and please note that I haven't installed it yet, I'm just viewing it via the LiveCD as a "tryout". Could that be why the lack of menu items??

Aye. Also if you decide installing Kubuntu, a good place to set up full source.list is here; [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) 
But note that the feisty setup isn't "done" yet, if you check the edgy you'll see what I'm talking about.

Yopu might want to check into /etc/apt/sources.list and uncomment stuff to enable them.

---

