---
title: "Whoha! Someone had the same idea!"
date: 2014-07-17
forum: Ubuntu, Linux and OS Chat
---

### Post by RadicaX on 2014-07-17
Well, I am feeling pretty good.

[http://ubuntuforums.org/showthread.php?t=2168407](http://ubuntuforums.org/showthread.php?t=2168407)

In this link, I wanted to work on things, like Ubuntu minimal, or any kind of Linux period, but needed to be able to transport packages offline and move them. Many solutions were given to me (Thank you forums), I was thinking of making a Linux distro that would focus on package management offline. Well, seems someone has beat me to the punch, which I am totally fine with, and feeling great about.

[http://www.unixmen.com/camicri-cube-offline-portable-package-management-system/](http://www.unixmen.com/camicri-cube-offline-portable-package-management-system/)

A project I plan on keeping an eye on. This might make it over all easier for people to give programs out for an offline linux. I just really like the idea of an offline package manager. Note, you still have to download stuff from an online computer, but that makes things easier period. Having a laptop, of course you could just go to a wifi spot, and download the stuff you need, but if you want to work on say a desktop machine, that can not get net, this would help greatly. I also have a feeling that they might figure out some other things to do with it, We will see. What are your thoughts on this nifty little package manager?

---

### Post by at_first_light on 2014-07-17
Windows is happy as a smiling-clam on offline machines, but Ubuntu is a nightmare. On a side note, here's another method for offline package installation:

1. Boot up a live-cd, and download the packages you want. In this case Leafpad.
```

sudo apt-get update && sudo apt-get install leafpad

```

2. Save the packages to an archive to transfer to another system.
```

cd /var/cache/apt/archives/ && sudo tar -czf ~/leafpad.tar.gz *.deb

```

3. On the new system extract the archive.
```

sudo tar -xzf ~/leafpad.tar.gz -C /var/cache/apt/archives

```

4. Install the packages on the new system.
```

sudo apt-get install --no-download leafpad

```

---

### Post by ian-weisser on 2014-07-17
Even easier:

1) Determine what packages you need to download using apt-get's --simulate flag.:

```
$ sudo apt-get --simulate install abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  abiword-common abiword-plugin-grammar abiword-plugin-mathview fonts-lyx
  libabiword-3.0 libchamplain-0.12-0 libchamplain-gtk-0.12-0 libgdome2-0
  libgdome2-cpp-smart0c2a libgoffice-0.10-10 libgoffice-0.10-10-common
  libgsf-1-114 libgsf-1-common libgtkmathview0c2a liblink-grammar4
  libloudmouth1-0 libots0 libwv-1.2-4 link-grammar-dictionaries-en
[COLOR=#ff0000]The following NEW packages will be installed:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview
  fonts-lyx libabiword-3.0 libchamplain-0.12-0 libchamplain-gtk-0.12-0
  libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0.10-10
  libgoffice-0.10-10-common libgsf-1-114 libgsf-1-common libgtkmathview0c2a
  liblink-grammar4 libloudmouth1-0 libots0 libwv-1.2-4
  link-grammar-dictionaries-en[/COLOR]
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Inst libchamplain-0.12-0 (0.12.7-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libchamplain-gtk-0.12-0 (0.12.7-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libgsf-1-common (1.14.27-2ubuntu2 Ubuntu:14.04/trusty [all])
Inst libgsf-1-114 (1.14.27-2ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libgoffice-0.10-10-common (0.10.9-1 Ubuntu:14.04/trusty [all])
Inst libgoffice-0.10-10 (0.10.9-1 Ubuntu:14.04/trusty [i386])
Inst libwv-1.2-4 (1.2.9-3 Ubuntu:14.04/trusty [i386])
Inst libabiword-3.0 (3.0.0-4ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libloudmouth1-0 (1.4.3-10 Ubuntu:14.04/trusty [i386])
Inst libots0 (0.5.0-2.1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst abiword-common (3.0.0-4ubuntu1 Ubuntu:14.04/trusty [all])
Inst abiword (3.0.0-4ubuntu1 Ubuntu:14.04/trusty [i386])
Inst link-grammar-dictionaries-en (4.7.4-2ubuntu1 Ubuntu:14.04/trusty [all])
Inst liblink-grammar4 (4.7.4-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst abiword-plugin-grammar (3.0.0-4ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libgdome2-0 (0.8.1+debian-6 Ubuntu:14.04/trusty [i386])
Inst libgdome2-cpp-smart0c2a (0.2.6-6ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libgtkmathview0c2a (0.8.0-9ubuntu1 Ubuntu:14.04/trusty [i386])
Inst fonts-lyx (2.0.6-1build1 Ubuntu:14.04/trusty [all])
Inst abiword-plugin-mathview (3.0.0-4ubuntu1 Ubuntu:14.04/trusty [i386])

```

2) Go online and download the packages you now know that you need.

You can do it in a web browser from [http://packages.ubuntu.com](http://packages.ubuntu.com)
Or you can download from a mirror using a batch script or shell script if you feel like writing one.
(If you use Synaptic or apt-zip, or apt-offline, those applications will generate a download script for you...but the script only works on Linux machines.)

3) Move the new packages to /var/cache/apt/archives on the offline machine.

Note that the packages in this directory are owned by root. If you use a GUI package manager, you should start it using 'gksudo' so it will properly assign ownership of the packages to root instead of you.

4) Use apt-get to install the packages (same install command, omitting --simulate).

```
$ sudo apt-get install abiword
```

---

### Post by mastablasta on 2014-07-18
yeah onyl then you need to search for packages and then when you get home and find one is misisng oyu get to trek back to the internet areaq :-) imagine being in some remote mounting village in 3rd world...

i htink debian has the option to download the whole repository...

---

### Post by RadicaX on 2014-07-18
Very good, it is neat, and while Linux is not just an internet only distro for sure. And really, I have only ever needed a couple programs, one does not need 5+ office suites quite often. Still, I like to see the different ways and solutions to the same thing, and how people work with it. 

@Mastablasta. I think the program, it being portable, keeps track of what you have on your machine, and thus eliminates that issue of having to go straight back out. Perhaps it uses some kind of Synchronization with it? Connect the two machines on a lan, grabs stats for offline machine, you want packages for, go to town, get packages you need, boom.

@ian-weisser

Debian's solution is great, and really sounds a lot like what this one what the first program does. I mean, you get packages for host machine, connect to host machine, download to target machine, thinking about it, guess that idea has been done many time before and tweaked only hear and there.

@at-first-sight

A great way to do it, if the liveCD has the programs you need. Which it certainly can, especially if you remix it.
And though Windows does seem easy to just install stuff offline, it certainly does make a mess of things because of it. Everyone just does their own installer, it is a pain. A pain I never want to suffer again, haha.

---

### Post by at_first_light on 2014-07-18
> **RadicaX said:**
> 

@at-first-sight

A great way to do it, if the liveCD has the programs you need. Which it certainly can, especially if you remix it.


I think you've misunderstood. The live-cd is used to download the packages on a computer that has internet access, and then you install them on the computer running Ubuntu that doesn't have internet access. In my example I downloaded Leafpad (a text editor) which isn't included on the live-cd; Ubuntu uses Gedit as it's default text editor.

---

### Post by sudodus on 2014-07-18
> **at_first_light said:**
> Windows is happy as a smiling-clam on  offline machines, but Ubuntu is a nightmare. On a side note, here's  another method for offline package installation:

1. Boot up a live-cd, and download the packages you want. In this case Leafpad.
```

sudo apt-get update && sudo apt-get install leafpad

```

2. Save the packages to an archive to transfer to another system.
```

cd /var/cache/apt/archives/ && sudo tar -czf ~/leafpad.tar.gz *.deb

```

3. On the new system extract the archive.
```

sudo tar -xzf ~/leafpad.tar.gz -C /var/cache/apt/archives

```

4. Install the packages on the new system.
```

sudo apt-get install --no-download leafpad

```

It is not very important to keep an off-line computer up to date for security reasons, so I guess it is enough to be able to install packages, according to the instructions above. I haven't tested, but it looks good to me.

Another alternative would be to carry a cloned copy (of the installed system) via a USB pendrive between the off-line computer and an on-line computer, where you can install packages. This should be possible with a reasonably sized pendrive, if you keep most personal data in a data partition, so that the home directory can be kept small. And the Ubuntu flavours are portable if you avoid proprietary drivers.

---

### Post by RadicaX on 2014-07-23
Thank you At_first_light. I have no clue why I was thinking to remix it after the fact, that little bit of extra clarification is quite helpful.

Thank you Sudodus, That is also a good idea. I do not really do much media on my computers, I mostly write, the only people that might need a proprietary driver of any sort would be my family, and even then, I doubt it. So having a copy like that on a pendrive is a wonderful idea, especially if I need something from one system onto the next.

---

### Post by varunendra on 2014-07-24
> **ian-weisser said:**
> Even easier:

1) Determine what packages you need to download using apt-get's --simulate flag...

Equally easier, but slightly better is the --print-uris option of apt-get. It pretends to install the packages, but then just prints the download URIs of the packages instead of downloading/installing them itself.

The advantages are:
1) You get the exact download URIs, so don't have to 'search' them.
2) you get the exact versions of the packages that the system requires (thus no version trouble) and can be 100% sure that what you are downloading is all you need, and is exactly what is needed.
3) the downloaded packages don't need to be in /var/cache/apt/archive directory, they can be installed from anywhere using "sudo dpkg -i <package names>" command.

Disadvantage in both --simulate and --print-uris methods is that unless the package (and its dependencies) come from default repository, the repository MUST have been updated at least once, otherwise apt-cache won't know about the package and its dependencies.

By the way, a package archived from another system will install properly on the target system ONLY if its version and architecture matches the target OS requirements. And if that condition is met, a much better and easier option is to use [AptOnCD]("https://help.ubuntu.com/community/APTonCD") instead of manually archiving > extracting > installing the packages. Acting as an offline repository, it is not standard, but is close to standard installation.

A cd/dvd created with AptOnCD is automatically detected as a software source as soon as it is inserted in a system running Ubuntu. The only condition for it to work is - the system should be running the same or compatible (version/architecture wise) version of Ubuntu (or derivatives like Mint).

---

### Post by ian-weisser on 2014-07-24
> **varunendra said:**
> Equally easier, but slightly better is the --print-uris option of apt-get. It pretends to install the packages, but then just prints the download URIs of the packages instead of downloading/installing them itself.

Many excellent tips! I have learned.
Thank you.

I have good use for --print-uris; thanks especially for that jewel.

---

