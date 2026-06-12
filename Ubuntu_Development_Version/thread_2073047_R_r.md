---
title: "R r"
date: 2012-10-18
forum: Ubuntu Development Version
---

### Post by cecilpierce on 2012-10-18
Wow that was super fast, lets get it on, thanks..:)

---

### Post by wojox on 2012-10-18
[IMG]http://www.networkworld.com/community/files/user11778/scooby_ruh_roh.jpg[/IMG]

---

### Post by sammiev on 2012-10-18
Raring Ringtail <----- Love the name of the next release. Bring it on! :popcorn:

---

### Post by dino99 on 2012-10-19
I hope to see e4rat landing into ubuntu, why not into RR ?

[http://e4rat.sourceforge.net/](http://e4rat.sourceforge.net/)
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1063673](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1063673)

if that wish makes sense to you, then post your comment on this report.

---

### Post by MikeCyber on 2012-10-19
Raring Ringtail...is that the same animal as the king in TV-movie: "Penguins from Madagascar"?

---

### Post by raja.genupula on 2012-10-19
yes that one

---

### Post by ventrical on 2012-10-19
We have Rambunctious Racoons here in Canada. :) They are related to the Raring Ringtail. I broke the news to one of my *customers* and, after Quantal Quetzel they seem to be desensitized and so it's not a real shocker. :)

  Still got some beta test jet lag from the last run :)hehehe

---

### Post by Cheesemill on 2012-10-19
Someone needs to update the forum description, I'm going to report this post and see if I can get a mods attention.

---

### Post by VinDSL on 2012-10-19
Ubu RR. 

I'm in...  :D

---

### Post by VinDSL on 2012-10-19
Looks like this is the timeline:

[LIST]
[*]Raring Ringtail ToolChain on October 25
[*]Feature(s) Freeze on November 22
[*]Alpha 1 on December 6
[*]Alpha 2 on February 7
[*]Beta 1 on March 7
[*]Beta 2 on March 28
[*]Ubuntu 13.04 Release on April 25
[/LIST]

---

### Post by cecilpierce on 2012-10-19
> **VinDSL said:**
> Looks like this is the timeline:

[LIST]
[*]Raring Ringtail ToolChain on October 25
[*]Feature(s) Freeze on November 22
[*]Alpha 1 on December 6
[*]Alpha 2 on February 7
[*]Beta 1 on March 7
[*]Beta 2 on March 28
[*]Ubuntu 13.04 Release on April 25
[/LIST]

Thanks for the info, just for the heck of it I tried 'raring' in the 'sources.list' and 404, :(

---

### Post by paul_in_london on 2012-10-19
Hi all.

Watching here before I update my sources list:

[http://archive.ubuntu.com/ubuntu/dists/raring/](http://archive.ubuntu.com/ubuntu/dists/raring/)

---

### Post by Cheesemill on 2012-10-19
I've got my daily cronjob for zsyncing the images all set up and ready to go....

It's just producing errors at the moment (obviously) but I'm all set.

---

### Post by xebian on 2012-10-19
Just updated now and raring to go.
```

The following NEW packages will be installed:
  libgcc-4.7-dev
The following packages will be upgraded:
  cpp-4.7 g++-4.7 gcc-4.7 gcc-4.7-base libgcc1 libgomp1 libitm1 libquadmath0
  libstdc++6 libstdc++6-4.7-dev
10 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.2 MB of archives.
After this operation, 65.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/main libitm1 amd64 4.7.2-5ubuntu1 [36.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ raring/main libgomp1 amd64 4.7.2-5ubuntu1 [27.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ raring/main gcc-4.7-base amd64
```
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libstdc++6 amd64 4.7.2-5ubuntu1 [322 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main cpp-4.7 amd64 4.7.2-5ubuntu1 [5,409 kB]

---

### Post by cariboo on 2012-10-19
> **Cheesemill said:**
> Someone needs to update the forum description, I'm going to report this post and see if I can get a mods attention.

Oops, I forgot to change the date. My excuse is that the text box to modify the description is so small, you can only see 4 words at a time. :-D

I'll update the sticky, and put it up later today.

---

### Post by zika on 2012-10-19
Oh boy! You just feed my testing addiction. Just lost one day after sudden and premature death of well serving D-Link modem/router. Put in its place Zyxel given by provider and lost all the nerves I had. Traveled some miles to obtain old Cisco and now I'm back... ;) Cisco rules, almost as good as D-Link. That is just a joke, of course, but DL worked surprisingly good for years. I hope 2009 Cisco will fill that shoes alright...
They are laying optical cable these days in my street so I hope that Cisco will be obsolete soon... ;)
What PCR to choose for CBR on 16Mb/s line?

---

### Post by paul_in_london on 2012-10-20
I'm in:

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
```

```
 sudo sed -i 's/quantal/raring/g' /etc/hosts /etc/hostname
```

---

### Post by zika on 2012-10-20
Tried just now 12.10 LiveCD. Everything that does not work on my Testing Install works on LiveCD... ;)
So, before I embark on RR I will (probably) have to reinstall or ppa-purge all the stuff that conflicts with each other... Just enough time to be ready for toolchain... ;) (25.10. as I recall)...
Or just turn all PPA's off and let RR correct all the mistakes in my install. That is, probably, a big wishful thinking of a lazy guy...

---

### Post by jbicha on 2012-10-20
Y'all should probably keep quantal-proposed, quantal-updates, and quantal-security for the next week or two until raring really gets going.

---

### Post by dino99 on 2012-10-20
> **paul_in_london said:**
> 

```
 sudo sed -i 's/quantal/raring/g' /etc/hosts /etc/hostname
```


hm, i've looked at these files on my pc, and i cant see something related to the distro name inside; in fact they are quite empty. What yours have that concern the distro name ? ( i suppose thats your tweaks; which reasons ?)

---

### Post by Cheesemill on 2012-10-20
It's just the name of your machine, paul_in_london was just changing the name of his test machine from quantal to raring.

---

### Post by paul_in_london on 2012-10-20
> **dino99 said:**
> hm, i've looked at these files on my pc, and i cant see something related to the distro name inside; in fact they are quite empty. What yours have that concern the distro name ? ( i suppose thats your tweaks; which reasons ?)

```
paul@quantal-64:~$ cat /etc/hosts
127.0.0.1       localhost.localdomain localhost raring-64
127.0.1.1       raring-64

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
paul@quantal-64:~$ 

```

```
paul@quantal-64:~$ cat /etc/hostname
raring-64
paul@quantal-64:~$
```

Haven't rebooted so prompt still says quantal. :lolflag:

---

### Post by dino99 on 2012-10-20
here are mines:

```
oem@oem-desktop:~$ cat /etc/hostname
oem-desktop

```

```
oem@oem-desktop:~$ cat /etc/hosts
127.0.0.1	localhost.localdomain localhost	
::1	oem-desktop localhost6.localdomain6 localhost6	
127.0.1.1	oem-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Oops, i've finally understood thats your host name at installation.

---

### Post by serdotlinecho on 2012-10-21
Yes.

:guitar:

---

### Post by Starks on 2012-10-21
I'm in.

Got the raring toolchain.

---

### Post by zika on 2012-10-22
OK, I'm in...
Is this OK:
```
$ cat sources.list
deb http://archive.ubuntu.com/ubuntu raring main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu raring main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu quantal-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu quantal-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted universe multiverse

#deb http://archive.canonical.com/ubuntu raring partner
deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu raring partner

deb http://archive.ubuntu.com/ubuntu raring-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu quantal-proposed restricted main multiverse universe
# deb-src http://archive.ubuntu.com/ubuntu/ raring-proposed main restricted universe multiverse

#deb http://extras.ubuntu.com/ubuntu raring main
deb http://extras.ubuntu.com/ubuntu quantal main
## deb-src http://extras.ubuntu.com/ubuntu raring main
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main

```What was a place that we should also add Raring? I always forget about that file...

I remebered:

Append ```
Suite: raring
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: raring
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.04 'Precise Pangolin'

Suite: raring
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: raring
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: raring
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: raring-security
ParentSuite: raring
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: raring-security
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: raring-updates
ParentSuite: raring
RepositoryType: deb
Description: Recommended updates

Suite: raring-updates
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: raring-proposed
ParentSuite: raring
RepositoryType: deb
Description: Pre-released updates

Suite: raring-proposed
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: raring-backports
ParentSuite: raring
RepositoryType: deb
Description: Unsupported updates

Suite: raring-backports
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates
```after the first line in /usr/share/python-apt/templates/Ubuntu.info... OK?

---

### Post by dino99 on 2012-10-22
right now i've let quantal-updates/security/proposed and only move to raring with the main archive (to get the new quantal fixes/updates, as raring does not really exist yet). Will move to complete raring in a week or so after uds.

---

### Post by cecilpierce on 2012-10-22
I tried changeing the /etc/apt/sources.list from quantal to raring and got all kinds of warnings or errors about /var/lib/apt/lists duplicates, don't remember that happining before, what did I do wrong ?

Should I wait til the 25th tool chain ?

It did update and install some python stuff though!  :confused:

---

### Post by dino99 on 2012-10-22
here is mine for now:

oem@oem-desktop:~$ cat /etc/apt/sources.list
  
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-proposed main universe restricted multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) quantal main #wine

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) quantal contrib

# deb [http://ppa.launchpad.net/ricotz/staging/ubuntu](http://ppa.launchpad.net/ricotz/staging/ubuntu) raring main
# deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) raring main

---

### Post by cecilpierce on 2012-10-22
@dino99

Thanks, this is a new QQ install so I guess I will wait or just add the raring main universe restricted multiverse for now and I guess I have to change the 'Ubuntu.info' file to that "zika" did ?

---

### Post by dino99 on 2012-10-22
> **cecilpierce said:**
> @dino99

Thanks, this is a new QQ install so I guess I will wait or just add the raring main universe restricted multiverse for now and I guess I have to change the 'Ubuntu.info' file to that "zika" did ?

i never did (and never care, but maybe i should (who knows :( )

---

### Post by cecilpierce on 2012-10-22
> **dino99 said:**
> i never did (and never care, but maybe i should (who knows :( )

I remember haveing problems with synaptic awhile back and changeing that file fixed it, don't know eithier.

---

### Post by serdotlinecho on 2012-10-22
Just upgraded this config files this morning(well, morning here :)):

```
Setting up base-files (6.11ubuntu1) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...

Configuration file `/etc/os-release'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** os-release (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/os-release ...

serdotlinecho@raring:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="13.04, Raring Ringtail"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Raring Ringtail (development branch)"
VERSION_ID="13.04"

```Yeah!!! :guitar:

---

### Post by VinDSL on 2012-10-22
> **zika said:**
> OK, I'm in...

...after the first line in /usr/share/python-apt/templates/Ubuntu.info... OK?
Nice!

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Mon Oct 22 20:19:30 MST 2012
**[COLOR="DarkRed"]Distro Release: Ubuntu Raring Ringtail (development branch)[/COLOR]**
Kernel Release: Linux 3.6.3-030603-generic
Unity Release: unity 6.8.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.51

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0+git20120920.70e57668-0ubuntu0ricotz

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

A bunch of Python upgrades flooded in, too!  :)

---

### Post by jppr on 2012-11-07
Every time when I update system in Synaptic comes this same <snip> issue... extras/ubuntu.com/ubuntu/dist/main/source/sources ... 404 not found
ther is long sources list issues what system can´t find...

I´m only one... :confused:

---

### Post by serdotlinecho on 2012-11-07
Not there yet for RR...

[http://extras.ubuntu.com/ubuntu/dists/](http://extras.ubuntu.com/ubuntu/dists/)

---

### Post by cecilpierce on 2012-11-07
> **jppr said:**
> Every time when I update system in Synaptic comes this same f***ing issue... extras/ubuntu.com/ubuntu/dist/main/source/sources ... 404 not found
ther is long sources list issues what system can´t find...

I´m only one... :confused:

If you don't want to see the warnings just unclick the two independents in software sources or put a # in them in /etc/apt/sources.list, thats what I did for now anyhow   :P

---

### Post by cecilpierce on 2012-11-07
Just did updte and saw Wayland droped a file in, hmmm!

---

### Post by serdotlinecho on 2012-11-08
Gnome 3.8 is dropping Fallback mode.
[http://worldofgnome.org/gnome-3-8-is-dropping-fallback-mode/](http://worldofgnome.org/gnome-3-8-is-dropping-fallback-mode/)

And Unity need to do something...
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-gnome-fallback](https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-gnome-fallback)

---

