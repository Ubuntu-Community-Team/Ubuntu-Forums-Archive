---
title: "Install Kdenlive 0.7"
date: 2008-12-07
forum: Ubuntu Studio
---

### Post by wadelewis4 on 2008-12-07
Hi,

I've seen a couple posts about there not being a deb package for download at the official kdenlive homepage. I wanted to try it too, so I searched out all the dependencies and archived them together with the kdenlive installer. I uploaded it to my site - it's available here: [DOWNLOAD]("http://sites.google.com/site/virtubuntu/Home/Kdenlive0.7.tar.gz?attredirects=0").

For testing purposes, I tried to download it and install it on another ubuntu based PC. It worked & here's what I had to do:

Download the file. Save it to desktop & extract all files.
In Terminal:
```

cd /home/username/Desktop/Kdenlive0.7/dependencies/
sudo dpkg -i *.deb

```

After that, you may have a few errors with ffmpeg & mlt.
Next, to fix the broken dependencies:
```

sudo apt-get install -f

``` 

This will correct the broken depencies.
Now you can install Kdenlive either by double-clicking the "kdenlive_0.7-0.0_i386.deb" installer or in the terminal window:

```

cd ..
sudo dpkg -i kdenlive_0.7-0.0_i386.deb

```

Note: I successfully installed it on machines using Ubuntu Intrepid (8.10). 
Ubuntu (gnome) Users: To avoid complications, you'll need some KDE4 core files, such as kdebase-runtime and kdelibs5, etc.. A quick way to do that would be to install the kde4 games packages - or click: [HERE]("apt:kdegames"). But you can of course just use synaptic to do it. 

Enjoy

---

### Post by n.brenner on 2008-12-07
):P:D:D:DHOORAY followed your posting, made small adj to input on first code
.......   but....IT WORKS.....THANKYOU THANKYOU......

on first code, just do

sudo dpkg -i ~/desktop/Kdenlive0.7/dependencies/*.deb


Now please do the same thing for AMD64..would be very pleased..:D:D:D

---

### Post by cotcot on 2008-12-08
Your method install kdenlive. Starting kdenlive from terminal gives this error :
```
kdenlive: symbol lookup error: /usr/local/lib/libavcodec.so.52: undefined symbol: av_lfg_init

```

---

### Post by wadelewis4 on 2008-12-08
> **cotcot said:**
> Your method install kdenlive. Starting kdenlive from terminal gives this error :
```
kdenlive: symbol lookup error: /usr/local/lib/libavcodec.so.52: undefined symbol: av_lfg_init

```

Yeah, sorry it gave you a problem - It's definately something people are going to have to try at their own risk. Like I said, it worked for me using ubuntu intrepid 32bit, and hopefully it'll work for most who want to try it. It may work straight away or it may take some tinkering.. either way it's "give it a shot" or wait for the offical ubuntu deb to appear on the kdenlive site (which I too will install when it's available).

---

### Post by lovestopsfear on 2008-12-10
i tried this method letter for letter and also tried this suggestion:   sudo dpkg -i ~/desktop/Kdenlive0.7/dependencies/*.deb . but i get this error....
Error: Dependency is not satisfiable: kdebase-runtime

please help! i'm a newbie using hardy and an x86 system.

---

### Post by rylleman on 2008-12-10
There's an installer wizard you can use which worked for me.
Here's a guide for installation on Ubuntu;
[https://help.ubuntu.com/community/KdenliveSVN]("https://help.ubuntu.com/community/KdenliveSVN")

---

### Post by Ubuntiac on 2008-12-10
The installer wizard (or KBW), while taking a few more steps to get going, also keeps you up to date with the latest code changes so you can get bugs fixed straight away. There's already been a bunch of new features and fixes added since 0.7 was released.

Obviously this is all code in progress, but personally I find the SVN version to actually be more stable as so many stability fixes have gone in since 0.7 was released.

---

### Post by cotcot on 2008-12-13
I reinstalled kdenlive once again with the installer (see post #6) and I now it works.

---

### Post by Guruji on 2008-12-14
y installed kdenlive using the wizard, but when i open kdenlive there are no icons on the interface! Just the names in the menus, the buttons are there on the interface..but no icons at all!

any idea?

---

### Post by cignale on 2008-12-14
I've made some packages for Ubuntu Intrepid i386.

Look at my blog post and leave feedback

[http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/](http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/)

---

### Post by markofealing on 2008-12-14
> **cotcot said:**
> I reinstalled kdenlive once again with the installer (see post #6) and I now it works.

I've done the same on my Athlob64 3000+ using Kubuntu 8.10 although I did have to do step 2 as modules were missing.:):)

---

### Post by Chame_Wizard on 2008-12-14
Great how to

---

### Post by n.brenner on 2008-12-15
looked up all the dependencies in amd64 but didnt find libammb3, libamrwb3 or libxvidcore4.???any suggestions:

---

### Post by markofealing on 2008-12-15
> **n.brenner said:**
> looked up all the dependencies in amd64 but didnt find libammb3, libamrwb3 or libxvidcore4.???any suggestions:

Have you tried copying and pasting step 2 into terminal to ensure everything is installed?

---

### Post by wadelewis4 on 2008-12-16
Officially solved: Go Here and install via new repos

[http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages")

---

### Post by RuleMaker on 2008-12-18
But what about 8.04, these repos apply only for interpid...

---

### Post by Ubuntiac on 2008-12-19
Not sure about .deb's for Hardy, but I do know that the builder wizard instructions work perfectly to install the latest SVN on Hardy with a nice GUI.

I've since upgraded to Intrepid, but the builder wizard worked perfectly for me when I was on Hardy.

I've also found the SVN version *more* stable than the packages rather than less, and it's nice to see new features and fixes land on your desktop every day. :)

---

### Post by resander on 2008-12-19
The instructions for ubuntu install have just changed at kdenlive.org.

Put deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main in /etc/apt/sources.list and issue   (tpikalek changed to baudm)

 sudo apt-get update;
 sudo apt-get install kdenlive

after removal of old Kdenlive 0.6.

0.7 installed OK.

---

### Post by Naegling23 on 2008-12-19
I tried uninstalling 0.6, then installing 0.7, but I get the following error

Commit failed.
To continue, hit ok and we will try to recover. If you close the application now, we will not do anything and you may try to resolve the problem manually.
(If you suspect this is a bug in Adept, please also provide the following exception description in the report).

The error was: 
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --unpack, /var/cache/apt/archives/libmlt1_0.3.2-1ubuntu1~ppa5_i386.deb, /var/cache/apt/archives/inigo_0.3.2-1ubuntu1~ppa5_i386.deb, /var/cache/apt/archives/libmlt++1_0.3.2-1~ppa1_i386.deb, /var/cache/apt/archives/libmlt-data_0.3.2-1ubuntu1~ppa5_all.deb, /var/cache/apt/archives/kdenlive_0.7-0.0~ppa5_i386.deb, /var/cache/apt/archives/libcv1_1.0.0-6.1_i386.deb, /var/cache/apt/archives/libcvaux1_1.0.0-6.1_i386.deb, /var/cache/apt/archives/libhighgui1_1.0.0-6.1_i386.deb, /var/cache/apt/archives/swh-plugins_0.4.15-0.2_i386.deb, /var/cache/apt/archives/libgavl-1.0-0_1.0.1-1~ppa1_i386.deb, /var/cache/apt/archives/frei0r_1.1.22-0.1~ppa2_i386.deb ], 
    Sup-process returned error code 1, 
    Error processing /var/cache/apt/archives/kdenlive_0.7-0.0~ppa5_i386.deb : trying to overwrite `/usr/share/applications/kde/kdenlive.desktop', which is also in package kdenlive-data.

any help?

---

### Post by Ubuntiac on 2008-12-19
That's just a packaging mistake. The shortcut has been put in two different packages and it's complaining that one is trying to override the other.

You can get around it by going to the folder where you downloaded the packages in the command line and entering:

```
sudo dpkg --force-all -i *.deb
```

WARNING: Make sure that you ONLY have the packages you want installed (the Kdenlive related ones) in that folder before doing this. This command basically says "Install everything in this folder, even if it wipes over other files." Necessary in this case, but just make sure you're in the right folder with no other debs.

---

### Post by Naegling23 on 2008-12-20
> **Ubuntiac said:**
> That's just a packaging mistake. The shortcut has been put in two different packages and it's complaining that one is trying to override the other.

You can get around it by going to the folder where you downloaded the packages in the command line and entering:

```
sudo dpkg --force-all -i *.deb
```

WARNING: Make sure that you ONLY have the packages you want installed (the Kdenlive related ones) in that folder before doing this. This command basically says "Install everything in this folder, even if it wipes over other files." Necessary in this case, but just make sure you're in the right folder with no other debs.

hmmm, im trying to install it through the repo's.  Does anyone remember the apt-get force command?

---

### Post by Naegling23 on 2008-12-20
nevermind, sudo apt-get -f install kdenlive was the solution.

For anyone else having the same problem as me, it looks like kdenlive-data needed to be removed, perhaps removing that first before installing kdenlive 0.7 would be the best way to go.

Im excited, kdenlive is a great video editor, but the 0.6 version was very unstable for me, hopefully this brings some stability to it...video editing was the last area where linux really struggles.

---

### Post by Jdm111 on 2008-12-21
dpkg: dependency problems prevent configuration of kdenlive:
 kdenlive depends on libmlt++1 (>= 1:0.3.2); however:
  Version of libmlt++1 on system is 0.3.2-1.
 kdenlive depends on libmlt1 (>= 1:0.3.2); however:
  Version of libmlt1 on system is 0.3.2-1ubuntu1~ppa5.
 kdenlive depends on mlt; however:
  Package mlt is not installed.
dpkg: error processing kdenlive (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdenlive

This is my problem:(:(:(:(

---

### Post by Ubuntiac on 2008-12-21
Ah yes,

I didn't check which set of packages you're using (a couple of different sets came out, all at the same time), but I do remember that at least one of them required uninstalling all the previous Kdenlive packages first if you'd installed Kdenlive from elsewhere.

---

### Post by 4ebees on 2008-12-23
Hi Ubuntiac,

Regarding your comments below:

> **Ubuntiac said:**
> Not sure about .deb's for Hardy, but I do know that the builder wizard instructions work perfectly to install the latest SVN on Hardy with a nice GUI.


Can you let me know if this was under KDE4 or KDE3.5?

Many thanks.

---

