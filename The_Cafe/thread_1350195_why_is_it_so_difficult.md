---
title: "why is it so difficult?"
date: 2009-12-09
forum: The Cafe
---

### Post by SLEEPER_V on 2009-12-09
Why is it so difficult to install .tar files?  Its silly hard for no reason.  Another thing that kills me is when you read the psychocats guide, there is basically nothing, but its says 'as a last resort use .tar files', rpms ahead of that and .debs preferably.  I have never even seen an .rpm . Ever.  But every damn file you download is available in one of the .tar formats.  I have searched for help numerous times and every post is like 'read the readme file' and ' you have to make install'  Those suggestions are nonsense to an idiot like me and most of them are from Dapper Drake and dont quite translate for some reason.  I'm just trying to install Thunderbird 3.0.  I have a genius level IQ, but for some reason when I type install --help into the terminal, my eyes glaze over, my mouth falls agape, I start to drool and I get an insatiable urge to drink Natural Light beer.

---

### Post by NoaHall on 2009-12-09
```
cd /home/user/location
./configure
make
make install
```

---

### Post by Crunchy the Headcrab on 2009-12-09
> **SLEEPER_V said:**
> Why is it so difficult to install .tar files?  Its silly hard for no reason.  Another thing that kills me is when you read the psychocats guide, there is basically nothing, but its says 'as a last resort use .tar files', rpms ahead of that and .debs preferably.  I have never even seen an .rpm . Ever.
.rpm = redhat/fedora/suse
.deb = debian/ubuntu/etc.

---

### Post by Hallvor on 2009-12-09
Why not make it easy and install software from the repositories instead? Installing from source is only a last resort for me.

---

### Post by SLEEPER_V on 2009-12-09
> **Hallvor said:**
> Why not make it easy and install software from the repositories instead? Installing from source is only a last resort for me.

I want the new thunderbird, 3.0.

---

### Post by NoaHall on 2009-12-09
```
gksudo gedit /etc/apt/sources.list
```
Post these in - deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Then run
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
sudo apt-get update
sudo apt-get install thunderbird-3.0 thunderbird-3.0-gnome-support
```

---

### Post by MaindotC on 2009-12-09
It's difficult because you don't have enough exposure to open-source systems, or more specifically, Ubuntu.  Everything is usually documented in the README file, but I'm betting that when you follow the directions you are receiving an error stating that something can't be found.  The README file tells you want you need installed, but finding that exact package name(s) requires you to know something about satisfying dependencies.

Installing from a tar.gz (or sometimes called installing from source) is not difficult, you're just a newb.  If you need help, show us what you are trying to install and at what point of the installation you are encountering a problem.

---

### Post by fancypiper on 2009-12-09
Here are some installation guides:

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

---

### Post by SLEEPER_V on 2009-12-09
> **NoaHall said:**
> ```
gksudo gedit /etc/apt/sources.list
```
Post these in - deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Then run
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
sudo apt-get update
sudo apt-get install thunderbird-3.0 thunderbird-3.0-gnome-support
```
thank you.  Its confusing at times what the best solution is and how to go about it.  I need a manual.

---

### Post by SLEEPER_V on 2009-12-09
> **fancypiper said:**
> Here are some installation guides:

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)thank you.  I will give these a look.

---

### Post by matthew.ball on 2009-12-09
> **SLEEPER_V said:**
> I have a genius level IQ
No you don't.

---

### Post by SunnyRabbiera on 2009-12-09
The thunderbird .tar.gz package on its website actually should have binaries in it without need to compile.

---

### Post by ZankerH on 2009-12-09
Every thread about package managment in GNU/Linux, ever:

OP: BAAWWW, windows just has you click an exe and click yes twenty times to install
community: sudo [apt-get install/pacman -S/yum install/whatever] [package name]
OP: BAAWWW, DOS TERMINAL 70s tech, ancient difficult scary etc, GNU/LINUX NEEDS A UNIFIED PACKAGE SYSTEM!!!11!1
community: There is a unified package system, it's called source code
OP: BAAWWW, but I don't want to have to learn! My PC should juust do what I want it to!

---

### Post by SunnyRabbiera on 2009-12-09
> **ZankerH said:**
> Every thread about package managment in GNU/Linux, ever:

OP: BAAWWW, windows just has you click an exe and click yes twenty times to install
community: sudo [apt-get install/pacman -S/yum install/whatever] [package name]
OP: BAAWWW, DOS TERMINAL 70s tech, ancient difficult scary etc, GNU/LINUX NEEDS A UNIFIED PACKAGE SYSTEM!!!11!1
community: There is a unified package system, it's called source code
OP: BAAWWW, but I don't want to have to learn! My PC should juust do what I want it to!

Then someone suggests synaptic and all is better :D
Until its killed in Lucid, blargh thats gonna make a mess of things.
I might just drop ubuntu entirely because its dropping a good sophisticated package manager (synaptic) and replacing it with a watered down package manager that might be good for beginners but leaves a lot to be desired (app center).
I hope app center gets a crapload of functionality between now and Lucid.
I hope they change their minds, or just adopt packagekit and get it over with.

---

### Post by matthew.ball on 2009-12-09
I doubt they'll remove Synaptic entirely.

Edit:
In Lucid.

---

### Post by SunnyRabbiera on 2009-12-09
> **matthew.ball said:**
> I doubt they'll remove Synaptic entirely.

There are plans for it though, appcenter is supposed to take over real soon.

---

### Post by SLEEPER_V on 2009-12-09
> **ZankerH said:**
> Every thread about package managment in GNU/Linux, ever:

OP: BAAWWW, windows just has you click an exe and click yes twenty times to install
community: sudo [apt-get install/pacman -S/yum install/whatever] [package name]
OP: BAAWWW, DOS TERMINAL 70s tech, ancient difficult scary etc, GNU/LINUX NEEDS A UNIFIED PACKAGE SYSTEM!!!11!1
community: There is a unified package system, it's called source code
OP: BAAWWW, but I don't want to have to learn! My PC should juust do what I want it to!

I dont complain about the OS, if you read, I complain that I must be an idiot lacking basic understanding of the material.

---

### Post by SLEEPER_V on 2009-12-09
> **matthew.ball said:**
> No you don't.

yes, I do.  The difference between having potential and  realizing said potential is vast.

---

### Post by fancypiper on 2009-12-09
Never mind, I found the info.

---

### Post by Jive Turkey on 2009-12-09
> **matthew.ball said:**
> No you don't.

Yes, he very well could, but is naive to linux and when reading posts and threads the ambiguities of the language and terminology we use can be interpreted in many different ways.

Also, I've met some mensa members who are incapable of doing some pretty simple things (ie moving long skinny object through doorways).

IME the tar file for thunderbird contains binaries so you could extract it to pretty much anywhere and run the main executable file therein and it will work.

Some tar, gz, or bz, archives, as you may know contain source code that needs to be compiled and the subsequent binary files are moved to various locations by the command "make install" such that the OS becomes aware of thier existence so that when you type the name of the program into the command line it runs.  Think of these packages the same way you might be familiar with zip and rar archives in Windows.  They are just different types of compressed archives.

rpm files are packaged programs intended for use on other flavors of linux, ie SUSE, Red Hat, Fedora and some others.  The debian packaging system is used by Ubuntu and Debian, and others.  I avoid rpm packages in ubuntu in favor of the archives mentioned above.

I don't claim this is appropriate in all contexts, but when I want to install a binary archive I have a folder in my home directory and I put the extracted files into thier own folder there.  I manually add it to the menus or a launcher on one of my panels (I use Gnome not KDE). 

I'm just going to end by saying the unjustified flames you got in this thread are out of line and unusual on these forums, I'm pretty disappointed to see that.

---

### Post by matthew.ball on 2009-12-09
> **Jive Turkey said:**
> Yes, he very well could, but is naive to linux and when reading posts and threads the ambiguities of the language and terminology we use can be interpreted in many different ways.

Also, I've met some mensa members who are incapable of doing some pretty simple things (ie moving long skinny object through doorways).  The IQ scale is not a very good measure of intelligence.
It has nothing to do with whether he can do something or not - and I never said this, God knows how you inferred it from "No you don't".

I once had Whitfield Diffie (of Sun Microsystems) stay at my house, the light in the room he was staying in blew, and he didn't know how to change the light bulb. That doesn't make him not a genius (he most certainly is).

Rather, the fact this guy had to explicitly note that he has a genius-level IQ is the reason he does not.

---

### Post by Hallvor on 2009-12-09
It is the same with IQ, sex and money; the more you talk about it the less you have.

---

### Post by fromthehill on 2009-12-09
intelligence doesn't rule out stupidity

the OP may be intelligent, but he definitely lacks Reading Comprehension skills.
and the skill to google :p

[http://lmgtfy.com/?q=linux+install+tar.gz&l=1](http://lmgtfy.com/?q=linux+install+tar.gz&l=1)

---

### Post by SLEEPER_V on 2009-12-09
> **fromthehill said:**
> intelligence doesn't rule out stupidity

the OP may be intelligent, but he definitely lacks Reading Comprehension skills.
and the skill to google :p

[http://lmgtfy.com/?q=linux+install+tar.gz&l=1](http://lmgtfy.com/?q=linux+install+tar.gz&l=1)lol, that was funny.  Command line stuff just makes me go slack jawed for some reason.  I did search, but for some reason it wouldnt work.  Normally I use synaptic or .debs, but .tars always have confounded me.  Its the lack of basic understanding of the terminology and what it symbolizes.  I readily admit to idiocy.

---

### Post by SLEEPER_V on 2009-12-09
> **matthew.ball said:**
> It has nothing to do with whether he can do something or not - and I never said this, God knows how you inferred it from "No you don't".

I once had Whitfield Diffie (of Sun Microsystems) stay at my house, the light in the room he was staying in blew, and he didn't know how to change the light bulb. That doesn't make him not a genius (he most certainly is).

Rather, the fact this guy had to explicitly note that he has a genius-level IQ is the reason he does not.
The reason for the notation wasnt to impress perfect stranger who couldnt give a rat's rear end, it was to contrast the rest of my statement of idiocy, attempting to lend a farcical and humorous feel to the overall post.

---

### Post by JBAlaska on 2009-12-09
To save yourself future headaches, you might as well get this one over with.

```
sudo apt-get install build-essential
```

---

### Post by fancypiper on 2009-12-09
Don't forget:

sudo apt-get install alien

---

### Post by SLEEPER_V on 2009-12-09
> **JBAlaska said:**
> To save yourself future headaches, you might as well get this one over with.

```
sudo apt-get install build-essential
```
already have it, thank you though.

---

### Post by SLEEPER_V on 2009-12-09
> **fancypiper said:**
> Don't forget:

sudo apt-get install alienIs that a shooting game?


I kid, I kid.  Have that one too.  Thanks though.

---

### Post by kelvin spratt on 2009-12-09
I think people once again are using classroom attitudes, just because some body does not know something that they do. 
Some people are clever with their hands some with thier brains not many are both, This person wan'ts to learn help don't take the Mick.

---

### Post by dmizer on 2009-12-09
> **SLEEPER_V said:**
> I want the new thunderbird, 3.0.

If you have just a bit of patience, there will be a ppa with a prebuilt deb.

In fact, it's already up: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Avoid installing from source at all costs. If you don't know how to do it, it's nothing but trouble. If you want to learn about it, do so on a machine you don't care about having to do a system reinstall.

Edit:
Jeez reading comprehension works: [http://ubuntuforums.org/showpost.php?p=8467320&postcount=6](http://ubuntuforums.org/showpost.php?p=8467320&postcount=6)

Sorry :(

---

### Post by JBAlaska on 2009-12-09
> **SLEEPER_V said:**
> Is that a shooting game?


I kid, I kid.  Have that one too.  Thanks though.

LOL's good one!

---

### Post by Xbehave on 2009-12-09
mozilla releases are simple to install.
system-wide
```
**1**)Get tar from mozilla website
**2**)cd /opt
**3**)sudo tar -xf <tar>
4)sudo mv /usr/bin/thunderbird{,~}
5)sudo ln -sv /opt/thunderbird/thunderbird /usr/bin/thunderbird
```
Steps after 3 only needed so you can launch the program from the CLI and existing shortcuts will work, alternatively you can just setup GUI shortcuts using you menu of choice

User-only (not what i would recommend as it's not as safe)
```
**1**)Get tar from mozilla website
**2**)cd ~
**3**)tar -xf <tar> 
4)mkdir ~/bin
5)ln -sv ~/thunderbird/thunderbird ~/bin/
6)echo 'PATH="$PATH:~/bin"' >> ~/.bash_login
7)echo '. .bashrc' >> ~/.bash_login
```
Steps after 3 only needed so you can launch the program from the CLI and existing shortcuts will work, alternatively you can just setup GUI shortcuts using you menu of choice.
step 7 is to get .bashrc to still run now you have a .bash_login, alternatively you can just append the path line to .bashrc

---

### Post by 3rdalbum on 2009-12-09
1. There's no such thing as "installing a tar file". A tar is an archive, it can contain whatever you want. It's like "installing a RAR".

2. Tarballs (.tar) usually contain the program's source code. This is handy for developers, it's handy for people who are running Linux on more obscure CPU architectures than you or me, and it's handy for people who want to package up software for their distribution. It's not much use for the everyday man in Ubuntu, because the source code is not that easy to compile and there are usually PPAs or repositories that contain the program.

3. Linux does not use "DOS-like commands". MS-DOS uses Unix-like commands. Unix predates MS-DOS by a couple of decades.

4. It's not "DOS", it's MS-DOS. DOS was Apple's operating system in the late 70s/early 80s.

---

### Post by forrestcupp on 2009-12-09
Now you know why Psychocats says to only install from a tar as a last resort.  Like dmizer said, if you don't completely know all about what your doing, don't do it unless you absolutely have to.  It's harder to uninstall software you compiled from source, and sometimes it causes dependency problems.

> **3rdalbum said:**
> 
4. It's not "DOS", it's MS-DOS. DOS was Apple's operating system in the late 70s/early 80s.
DOS is just a generic term for Disk Operating System.  It wasn't just Apple; Commodore's system for accessing disks was called DOS, too.

---

### Post by Fast_Wyvern on 2009-12-09
> **dmizer said:**
> If you have just a bit of patience, there will be a ppa with a prebuilt deb.

In fact, it's already up: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

Avoid installing from source at all costs. If you don't know how to do it, it's nothing but trouble. If you want to learn about it, do so on a machine you don't care about having to do a system reinstall.

Edit:
Jeez reading comprehension works: [http://ubuntuforums.org/showpost.php?p=8467320&postcount=6](http://ubuntuforums.org/showpost.php?p=8467320&postcount=6)

Sorry :(

These link to the daily build and will install "Shredder 3.0.1 Pre" which is an Alpha release of Thunderbird  and update your Firefox if you leave the ppa on and update to Shiretoko 3.5.7 Alpha Release of firefox. 

Not what I intended, but is working fine

---

### Post by Xbehave on 2009-12-09
> **3rdalbum said:**
> 2. Tarballs (.tar) usually contain the program's source code. This is handy for developers, it's handy for people who are running Linux on more obscure CPU architectures than you or me, and it's handy for people who want to package up software for their distribution. It's not much use for the everyday man in Ubuntu, because the source code is not that easy to compile and there are usually PPAs or repositories that contain the program.
Just to be clear there are also binary tars that you just unpack and run (like winRar or utorrent on windows) and Thunderbird is available as one of those so it's exactly the same as windows.

---

### Post by Exodist on 2009-12-09
> **SLEEPER_V said:**
> Why is it so difficult to install .tar files?  Its silly hard .......
Thats about all I read of this and realized the OP hasn't got a clue. No offense. I suggest picking up a Linux How-To book.

---

### Post by perce on 2009-12-09
> **SLEEPER_V said:**
> Why is it so difficult to install .tar files?  

.tar are difficult to install because they can be whatever... a tar file is not the equivalent of a .exe file on Windows, as most beginner seem to think, but rather the equivalent of a .zip file. So a .tar can contain a source code to compile (which is usually difficult - how often do you compile on Windows?) or a binary installer, which is usually easy to install, or even something which is not meant to be installed, like a backup of my holiday pictures. This implies that instruction to install the program which is contained in a .tar file change from time to time, because that program is not distributed in Ubuntu's standard format for installing program, which is a .deb. 

Finally, and luckily, very few programs come in .tar files, and for most of them .deb files are available. The correct workflow for installing programs is:

1) look in the repository: if the program is there, then a couple of click suffice to install it. This should cover more that 90% of software you need

2) if it is not in the repository, look is the program's download page has
a .deb compiled for Ubuntu: if yes, download it and double click on it. This should cover almost all the rest.

2b) sometimes the download page will not have the .deb file, but other respectable sites like get-deb will have it (but be careful not to install programs from dodgy sources, otherwise all Linux extra protections won't help you against malware)

3) if the program is available only in a .tar file (or .tgz or .tar.gz), download it to your desktop and extract it. That is done by right clicking on the file and choosing "extract here" from the menu. This will create a directory, usually (but not necessarily) with the same name without .tar. Navigate inside that directory and look for a file called README which will contain the instruction on how to install the program.

---

### Post by SLEEPER_V on 2009-12-09
> **Exodist said:**
> Thats about all I read of this and realized the OP hasn't got a clue. No offense. I suggest picking up a Linux How-To book.Thanks.  That hasnt been covered yet.  The part about me not having a clue I mean.

---

### Post by SLEEPER_V on 2009-12-09
> **perce said:**
> .tar are difficult to install because they can be whatever... a tar file is not the equivalent of a .exe file on Windows, as most beginner seem to think, but rather the equivalent of a .zip file. So a .tar can contain a source code to compile (which is usually difficult - how often do you compile on Windows?) or a binary installer, which is usually easy to install, or even something which is not meant to be installed, like a backup of my holiday pictures. This implies that instruction to install the program which is contained in a .tar file change from time to time, because that program is not distributed in Ubuntu's standard format for installing program, which is a .deb. 

Finally, and luckily, very few programs come in .tar files, and for most of them .deb files are available. The correct workflow for installing programs is:

1) look in the repository: if the program is there, then a couple of click suffice to install it. This should cover more that 90% of software you need

2) if it is not in the repository, look is the program's download page has
a .deb compiled for Ubuntu: if yes, download it and double click on it. This should cover almost all the rest.

2b) sometimes the download page will not have the .deb file, but other respectable sites like get-deb will have it (but be careful not to install programs from dodgy sources, otherwise all Linux extra protections won't help you against malware)

3) if the program is available only in a .tar file (or .tgz or .tar.gz), download it to your desktop and extract it. That is done by right clicking on the file and choosing "extract here" from the menu. This will create a directory, usually (but not necessarily) with the same name without .tar. Navigate inside that directory and look for a file called README which will contain the instruction on how to install the program.

Thank you for taking the time to spell it out for me

---

