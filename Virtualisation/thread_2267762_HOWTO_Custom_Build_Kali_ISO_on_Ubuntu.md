---
title: "HOWTO: Custom Build Kali ISO on Ubuntu"
date: 2015-03-03
forum: Virtualisation
---

### Post by sdgiffin on 2015-03-03
First off, I will tell you that while [the official guide]("http://docs.kali.org/downloading/live-build-a-custom-kali-iso") is good, it's aimed more at straight Debian users. Even though Ubuntu is based on Debian, there are some differences that may cause problems.

That being said, I had significant trouble getting this to work, but in the end, I have a process which I believe should work.

[SIZE=4]Getting Started[/SIZE]

First off, I am using Ubuntu 14.04.1 x64 but this process **should** work on almost any version (or subversion) of Ubuntu and Mint. In order to keep your "main" system clean, I recommend creating a virtual install, so for this guide, I will be using LXC. If you haven't already, install LXC. You can use the Software Centre or Synaptic if you like. Being old school, I prefer using the terminal and everything I do will be in [FONT=courier new]~$ standard terminal command notation[/FONT]:

```
~$ sudo apt-get install -y lxc
```

[SIZE=4]Creating A Container[/SIZE]

Next, you will need to create a container to run it all in. Since Kali's baseline is much closer to Debian than Ubuntu, you will need to build a Debian environment ("Wheezy" at the time of this writing), but with some minor changes. Fortunately, I have a custom template [available here]("https://github.com/EvilSupahFly/LXC-Kali-Template") if you wish to use it. If not, create a Debian container and add the Kali sources. Important to remember is that only the root user should create containers, so I will make gratuitous use of **[FONT=courier new]sudo[/FONT]** in this guide. Once inside the container using the password LXC gives you during the container creation stage, however, you will be running as root, **SO BE CAREFUL!**

Using the Debian template:
```
~$ sudo lxc-create -n kali -t debian
~$ sudo lxc-start -n kali
```

Once it's done getting set up (it does take a little time, after all), you will need to add the Kali repositories to your container's sources in **[FONT=courier new]/etc/apt/sources.list[/FONT]**:

```
deb http://http.kali.org/kali kali main contrib non-free
deb-src http://http.kali.org/kali kali main contrib non-free
deb http://security.kali.org/kali-security kali/updates main contrib non-free
deb-src http://security.kali.org/kali-security kali/updates main contrib non-free
```

Then apply the finishing touches:

```
~# apt-key adv --keyserver pgpkeys.mit.edu --recv-keys ED444FF07D8D0BF6
~# apt-get update
~# apt-get install kali-archive-keyring
```

If you opt to use my tweaked custom install, it will do all that for you. All you have to do is run it:

```
~# sudo lxc-create -n kali -t kali
~# sudo lxc-start -n kali
```

In both cases, you may wish to add Oracle's Java instead of OpenJDK (see "Trouble In Paradise" at the end):

```
~$ su -
~# echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" | tee /etc/apt/sources.list.d/webupd8team-java.list
~# echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" | tee -a /etc/apt/sources.list.d/webupd8team-java.list
~# apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886
~# apt-get update
~# apt-get install oracle-java8-installer

```

At this point, you should have a working container with access to the current Debian baseline and the Kali repositories. If not, **[FONT=courier new]sudo lxc-destroy -n kali[/FONT]** will nuke your old container so you can go back to "Creating a Container" and try again.

[SIZE=4]Getting Ready[/SIZE]

Now we need to prepare the Kali ISO build environment:

```
~# apt-get install git live-build cdebootstrap kali-archive-keyring
~# git clone git://git.kali.org/live-build-config.git
~# cd live-build-config
~# lb config
```

[SIZE=4]Configuring the Kali ISO Build (Optional)[/SIZE]

Through the **config** directory, your ISO build supports significant customization options, which are well documented on the Debian [live build 3.x]("http://live.debian.net/manual-3.x/html/live-manual/index.en.html") page. However, for the impatient, the following configuration files are of particular interest:
**config/package-lists/kali.list.chroot**  &#8211; contains the list of packages to install in the Kali ISO. You can  choose specific packages to be installed, while dropping others. This is  also where you can [change your Kali ISO Desktop Environment]("http://docs.kali.org/live-build/customize-the-kali-desktop-environment") (KDE, Gnome, XFCE, LXDE, etc).
**hooks/** &#8211; The hooks  directory allows us to hook scripts in various stages of the Kali ISO  live build. For more information about hooks, refer to the [live build manual]("http://live.debian.net/manual/3.x/html/live-manual/index.en.html"). As an example, Kali adds its forensic menu this way:

```
~# cat config/hooks/forensic-menu.binary
#!/bin/sh

cat >>binary/isolinux/live.cfg <<END

label live-forensic
menu label ^Live (forensic mode)
linux /live/vmlinuz
initrd /live/initrd.img
append boot=live noconfig username=root hostname=kali noswap noautomount
END

```

 [SIZE=4]Building the ISO[/SIZE]

Before you generate your ISO, you can  specify your required architecture, choosing either [FONT=courier new]amd64[/FONT] or [FONT=courier new]i386[/FONT]. Also  note that [FONT=courier new]lb build[/FONT] requires root rights. If you do not specify an  architecture, live build will generate an ISO with the same architecture  as the host machine. If you want to build a 64 bit ISO on a 32 bit Kali system, make sure you enable multi-arch support:

```
~# dpkg --add-architecture amd64
~# apt-get update
```

 Configure live-build to generate with a 64 bit:

```
~# lb config --architecture amd64
~# lb build
```

 ...or 32 bit:

```
~# lb config --architecture i386 # for 32 bit
~# lb build
```

 The last command will take a while to  complete, as it downloads all of the required packages needed to create  your ISO. Good time for a coffee.

[SIZE=4]Building Kali Linux for older i386 architecture[/SIZE]

The Kali Linux i386 ISO has PAE enabled.  If you require a default kernel for older hardware, like I did, you need to rebuild  a Kali Linux ISO. The rebuilding process is much the same as above,  other than the **686-pae** parameter that needs to be changed to **486** in **auto/config**:

```
~# apt-get install git live-build cdebootstrap kali-archive-keyring
~# git clone git://git.kali.org/live-build-config.git
~# cd live-build-config
~# sed -i 's/686-pae/486/g' auto/config
~# lb clean
~# lb config --architecture i386
~# lb build
```

[SIZE=4]Speeding up future builds[/SIZE]

If you plan to build custom ISOs often,  you might want to cache kali packages locally for future builds. I didn't bother, but you might, right? This  can easily be done by installing **apt-cacher-ng**, and configuring the *http_proxy* environment variable before every build.

```
~# apt-get install apt-cacher-ng
~# /etc/init.d/apt-cacher-ng start
~# export http_proxy=http://localhost:3142/
... ### setup and configure your live build
~# lb config --apt-http-proxy http://127.0.0.1:3142/
~# lb build
```
                                                                   
[SIZE=4]Trouble In Paradise[/SIZE]

The problem I kept running into was packages failing to install or configure properly, getting message like this:

```
Adding 'diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common'
dpkg: unrecoverable fatal error, aborting:
 failed to fstat previous diversions file: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
P: Begin unmounting filesystems...
P: Saving caches...
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Not to worry. This error may pop up a few times, but it can be fixed. The problem I had when I set out on this adventure was preventing the error in the first place. Every time it stops with an error, you can fix it like this:

```
~# chroot chroot
(kali) ~# dpkg --configure -a
(kali) ~# exit
... ### Use the same lb config you used the first time: lb config --architecture i386 or lb config --architecture amd64 or just lb config ###
~# lb build
```

LiveBuild uses a chroot inside the container so I've used (kali) to show being "inside" the chroot. On my system, dpkg kept spitting out errors, so I had to keep repeating this "trouble in paradise" section until I finally got a clean build. But now it works!

On one test system, I kept running into dependency problems with OpenJDK, so I replaced it with Oracle's Java. Should dpkg fail inside the chroot, you may wish to just directly edit the chroot's sources, and there's two ways to do that. The first way involves using your favourite text editor (gedit, kate, leafpad, mousepad) as root, and editing the sources directly (it's located at [FONT=courier new]/var/lib/lxc/kali/rootfs/root/live-build-config/chroot/etc/apt/sources.list[/FONT], assuming you called your live build "kali"), or you can follow the directions below to install the command-line editor **VIM**.

```
~# chroot chroot
(kali) ~# dpkg --configure -a    ### first allow dpkg to resume and fix the initial error
(kali) ~# apt-get install -y vim    ### the chroot doesn't have a text editor installed by default so we need to install one, unless you edited from the host
(kali) ~# apt-get remove --purge openjdk*  ### clean out OpenJDK
(kali) ~# vim /etc/apt/sources.list   ### edit /etc/apt/sources.list unless you already edited from the host
 ### Use the sources.list below
(kali) ~# apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886   ### add the webupd8 java PPA key
(kali) ~# apt-get update   ### update APT so it can see and use the Java PPA
(kali) ~# apt-get install -y oracle-java8-installer   ### install Java
(kali) ~# exit
~# lb build
```

This should get you over any hurdles:

```
###### sources.list ######:

## Kali's Repositories
deb http://archive.kali.org/kali kali main contrib non-free
deb-src http://archive.kali.org/kali kali main contrib non-free
deb http://archive.kali.org/kali-security kali/updates main contrib non-free
deb-src http://archive.kali.org/kali-security kali/updates main contrib non-free

## Debian Security updates
deb http://security.debian.org/ wheezy/updates main contrib non-free
deb-src http://security.debian.org/ wheezy/updates main contrib

## Debian Regular updates
deb http://ftp.debian.org/debian/ wheezy main contrib non-free
deb-src http://ftp.debian.org/debian/ wheezy main contrib

## Debian Proposed Updates
deb http://ftp.debian.org/debian/ wheezy-proposed-updates main contrib non-free
deb-src http://ftp.debian.org/debian/ wheezy-proposed-updates main contrib

## Oracle Java Repository from Webupd8
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

```

And that's it! Good luck!

---

