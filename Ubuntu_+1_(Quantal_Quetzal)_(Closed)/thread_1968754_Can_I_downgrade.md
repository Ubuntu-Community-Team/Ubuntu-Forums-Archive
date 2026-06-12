---
title: "Can I downgrade?"
date: 2012-04-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by codingman on 2012-04-29
I've got QQ on my computer but I was wondering if I could go to Precise from Quantal without reinstallation.

---

### Post by jppr on 2012-04-29
> **codingman said:**
> I've got QQ on my computer but I was wondering if I could go to Precise from Quantal without reinstallation.

Yep Yep and Hoh-hoi

---

### Post by codingman on 2012-04-29
But, how?

---

### Post by 2F4U on 2012-04-29
In my opinion, it is the same as for 12.04 vs. 11.10, you can't downgrade.

[http://ubuntuforums.org/showthread.php?t=1903087](http://ubuntuforums.org/showthread.php?t=1903087)

But maybe there is a way I don't know of.

---

### Post by Harry33 on 2012-04-29
At this early point of development (only a couple of Quantal packages published) it is possible to downgrade to Precise.
You need to manually download the Precise version of every single package you have upgraded to Quantal. Perhaps from 10 to 20 packages.
Then, (for example with terminal) go to the folder they were downloaded to and run this:
```
sudo dpkg -i *.deb
```

---

### Post by codingman on 2012-04-29
I'm no expert, so I have no idea how to locate the upgraded packages and then install the Precise version of each of those.

---

### Post by ronacc on 2012-04-29
if you know when you upgraded , open synaptic , then go to file>history that should tell you the names of the upgraded packages . You would probably be better off backing up your /home and doing a reinstall though , downgrades can get really messy . back up your /home anyway .

---

### Post by Harry33 on 2012-04-29
> **codingman said:**
> I'm no expert, so I have no idea how to locate the upgraded packages and then install the Precise version of each of those.

Well, after all, sorry to say this but you should have upgraded to Quantal only if you were an expert.

---

### Post by grahammechanical on 2012-04-29
This suggestion is entirely experimental. I have never done it. You might be the first to try.

First of all, do you have another version of Ubuntu that you can boot into if something goes wrong.

I have an 11.10 that I use a standby. I have 12.04 on another partition that I have now begun converting to 12.10.

In a few days, when the rush has died down, I shall upgrade my 11.10 to 12.04 and it will be my standby as I use this 12.04/12.10.

These were the two commands that I used to convert a 12.04 to 12.10

```
sudo sed -i 's/precise/quantal/g' /etc/apt/sources.list
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

You could reverse the first command to

```
sudo sed -i 's/quantal/precise/g' /etc/apt/sources.list
```

and then run 

```
[CODE]sudo apt-get update
```

if that don't work try

```
sudo apt-get upgrade
```

By changing the repositories to quantal and then updating and upgrading we brought in the packages that were available in the quantal repositories.

Now, by changing the repositories back to precise you may find that what was brought in is removed. I am sure that you will need to put your repositories back to precise.

But as I say, none of this is based upon experience.

Regards.

---

### Post by codingman on 2012-04-29
> **Harry33 said:**
> Well, after all, sorry to say this but you should have upgraded to Quantal only if you were an expert.

I've only been testing future releases once before, and that was for 12.04,in which you could not downgrade unless you reinstalled, therefore i never learned how to downgrade. On the other hand I do know some shell, and everyone has to start somewhere.

---

### Post by haqking on 2012-04-29
backup your personal data and the do a fresh installation of Precise.

Less hassle and since the start of this thread you could have been back up and running in precise ;)

Also it is less likely to cause issues.

Peace

---

### Post by codingman on 2012-04-29
> **grahammechanical said:**
> This suggestion is entirely experimental. I have never done it. You might be the first to try.

First of all, do you have another version of Ubuntu that you can boot into if something goes wrong.

I have an 11.10 that I use a standby. I have 12.04 on another partition that I have now begun converting to 12.10.

In a few days, when the rush has died down, I shall upgrade my 11.10 to 12.04 and it will be my standby as I use this 12.04/12.10.

These were the two commands that I used to convert a 12.04 to 12.10

```
sudo sed -i 's/precise/quantal/g' /etc/apt/sources.list
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

You could reverse the first command to

```
sudo sed -i 's/quantal/precise/g' /etc/apt/sources.list
```

and then run 

```
[CODE]sudo apt-get update
```

if that don't work try

```
sudo apt-get upgrade
```

By changing the repositories to quantal and then updating and upgrading we brought in the packages that were available in the quantal repositories.

Now, by changing the repositories back to precise you may find that what was brought in is removed. I am sure that you will need to put your repositories back to precise.

But as I say, none of this is based upon experience.

Regards.
I don't have another ubuntu but i do have windows.

---

### Post by codingman on 2012-04-29
Aw, man. There should be an easy up/downgrade, I think i'll just edit root instead.

---

### Post by MacUntu on 2012-04-29
Take a look at this: [Downgrade from one version to a previous version](http://askubuntu.com/q/3659/3037)

---

### Post by xebian on 2012-04-29
> **codingman said:**
> Aw, man. There should be an easy up/downgrade, I think i'll just edit root instead.

There is.  Backup whatever you want, and then take your yy.mm.iso and then do a fresh install.  There is nothing else as easy and simple as that.

---

### Post by codingman on 2012-04-29
Thanks for everyone's input, it's just that a bunch of applications won't install or won't work because i'm in 12.10, I guess i'll just stay in QQ.

---

### Post by xyzzyman on 2012-04-30
There is going to be breakage, especially being the first release after an LTS release. If this is your daily use system and you aren't at least multibooting, you are probably going to regret staying.

---

### Post by MacUntu on 2012-04-30
Really, try the pinning approach from my link. The earlier you start, the higher the chance of success.

---

### Post by effenberg0x0 on 2012-04-30
@codingman
There are other visual methods, like Software Center, Synaptics, etc. But you can get the list of all installed packages in specific dates and ranges by regexp matching against your dpkg log.

Example: This will list all packages you have installed from Apr. 26th to today.

Name of packages in the range
```
[03:26:49] ahsl@AL-DESK01:[~]: cat /var/log/dpkg.log | grep "^2012-04-\(26\|27\|28\|29\|30\).*\ installed\ "
```

Number of packages in the range
```
[03:27:52] ahsl@AL-DESK01:[~]: cat /var/log/dpkg.log | grep "^2012-04-\(26\|27\\|28\|29\|30\).*\ installed\ " | wc -l
139
```

In my case, there are 139 packages. But I installed optional stuff. A normal update will likely have less updated packages.

Looking at the installed packages, I can easily see stuff I can remove without causing any system impact. Probably half of it. 

If you're not sure how a package impacts your setup, you can see what packages depend on it, what it depends on, what it provides, using dpkg-query. Example (for package smbfs):
```
[03:29:20] ahsl@AL-DESK01:[~]: dpkg-query -W -f='Depends:${Depends}\nPre-Depends:${Pre-Depends}\nProvides:${Provides}\n' smbfs
Depends:cifs-utils (= 2:5.1-1ubuntu1)
Pre-Depends:
Provides:
```

Then you could even put in all together and automatically get the list of depends, pre-depends, provides for each of the packages you have installed in the date range:
```
[03:31:48] ahsl@AL-DESK01:[~]: for PACKAGE in $(cat /var/log/dpkg.log | grep "^2012-04-\(26\|27\\|28\|29\|30\).*\ installed\ " | awk 'BEGIN {FS=" "} {print $5}'); do echo "${PACKAGE}"; dpkg-query -W -f='Depends:${Depends}\nPre-Depends:${Pre-Depends}\nProvides:${Provides}\n\n' ${PACKAGE}; done
```

That can probably help a little.

Regards,
Effenberg

---

### Post by MacUntu on 2012-04-30
Probably also working: ```
dpkg --get-selections | grep -P "\tinstall$" | awk '{print $1}' | sed "s/$/\/precise/" | tr '\n' ' '
``` to get a list of installed packages that I can feed to ```
sudo apt-get install
```

This will throw errors like ```
E: Release 'precise' for '<PACKAGE>' was not found
``` - just remove those packages from the list and you should be good to go.

---

### Post by effenberg0x0 on 2012-04-30
> **MacUntu said:**
> Probably also working: ```
dpkg --get-selections | grep -P "\tinstall$" | awk '{print $1}' | sed "s/$/\/precise/" | tr '\n' ' '
``` to get a list of installed packages that I can feed to ```
sudo apt-get install
```

This will throw errors like ```
E: Release 'precise' for '<PACKAGE>' was not found
``` - just remove those packages from the list and you should be good to go.

Good idea. I was also thinking about aptitude. If he tries to remove the packages installed from release day to today via Aptitude, but keep only precise repos in sources.list, wouldn't aptitude provide those "options" to solve dependencies (using --full-resolver)?

Regards,
Effenberg

---

### Post by jerrylamos on 2012-04-30
This is a "development" forum and "unstable" Quantal is still very much in flux and will be for months.

Expect to re-install frequently (!) I use test partitions for development and have a stable release partition for recovery.

On one pc where I don't want the Windoze....7 to be blasted I use a USB hard drive for testing.  It's a left over laptop hard drive in a $10 case from Tiger Direct.  Once the "unstable" release settles down I'll take the risk and try multibooting "unstable" to see if Grub xx will still allow booting the Windoze....7. 

Better get into practice on install.  And install.  And re-install.

Good luck,

Jerry

---

### Post by ventrical on 2012-04-30
> **grahammechanical said:**
> This suggestion is entirely experimental. I have never done it. You might be the first to try.

First of all, do you have another version of Ubuntu that you can boot into if something goes wrong.

I have an 11.10 that I use a standby. I have 12.04 on another partition that I have now begun converting to 12.10.

In a few days, when the rush has died down, I shall upgrade my 11.10 to 12.04 and it will be my standby as I use this 12.04/12.10.

These were the two commands that I used to convert a 12.04 to 12.10

```
sudo sed -i 's/precise/quantal/g' /etc/apt/sources.list
``````
sudo apt-get update && sudo apt-get dist-upgrade
```You could reverse the first command to

```
sudo sed -i 's/quantal/precise/g' /etc/apt/sources.list
```and then run 

```
[CODE]sudo apt-get update
```if that don't work try

```
sudo apt-get upgrade
```By changing the repositories to quantal and then updating and upgrading we brought in the packages that were available in the quantal repositories.

Now, by changing the repositories back to precise you may find that what was brought in is removed. I am sure that you will need to put your repositories back to precise.

But as I say, none of this is based upon experience.

Regards.


 I'll be back !   :)

---

### Post by ventrical on 2012-04-30
so far ...

```
ventrical@ventrical1ME051:~$ sudo sed -i 's/quantal/precise/g' /etc/apt/sources.list
[sudo] password for ventrical: 
ventrical@ventrical1ME051:~$ sudo apt-get update
Ign http://extras.ubuntu.com precise InRelease
Ign http://archive.canonical.com precise InRelease         
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]   
Get:2 http://archive.canonical.com precise Release.gpg [198 B]
Get:3 http://extras.ubuntu.com precise Release [11.9 kB]    
Get:4 http://archive.canonical.com precise Release [7,078 B]                   
Get:5 http://archive.canonical.com precise/partner i386 Packages [4,957 B]     
Get:6 http://extras.ubuntu.com precise/main i386 Packages [555 B]              
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main Translation-en_CA                    
Ign http://archive.canonical.com precise/partner Translation-en_CA             
Ign http://extras.ubuntu.com precise/main Translation-en     
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://archive.ubuntu.com precise InRelease              
Ign http://archive.ubuntu.com precise-updates InRelease
Ign http://archive.ubuntu.com precise-backports InRelease
Ign http://archive.ubuntu.com precise-security InRelease
Ign http://archive.ubuntu.com precise-proposed InRelease
Get:7 http://archive.ubuntu.com precise Release.gpg [198 B]
Get:8 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:9 http://archive.ubuntu.com precise-backports Release.gpg [198 B]
Get:10 http://archive.ubuntu.com precise-security Release.gpg [198 B]
Get:11 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]
Get:12 http://archive.ubuntu.com precise Release [49.6 kB]
Get:13 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Get:14 http://archive.ubuntu.com precise-backports Release [49.6 kB]           
Get:15 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Get:16 http://archive.ubuntu.com precise-proposed Release [49.6 kB]            
Get:17 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Get:18 http://archive.ubuntu.com precise/restricted Sources [5,470 B]          
Get:19 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Get:20 http://archive.ubuntu.com precise/multiverse Sources [155 kB]           
Get:21 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:22 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:23 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:24 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]     
Get:25 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]       
Get:26 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B] 
Get:27 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:28 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:29 http://archive.ubuntu.com precise-updates/main Sources [5,093 B]
Get:30 http://archive.ubuntu.com precise-updates/restricted Sources [765 B]    
Get:31 http://archive.ubuntu.com precise-updates/universe Sources [1,032 B]    
Get:32 http://archive.ubuntu.com precise-updates/multiverse Sources [14 B]     
Get:33 http://archive.ubuntu.com precise-updates/main i386 Packages [20.3 kB]  
Get:34 http://archive.ubuntu.com precise-updates/restricted i386 Packages [770 B]
Get:35 http://archive.ubuntu.com precise-updates/universe i386 Packages [2,088 B]
Get:36 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [14 B]
Get:37 http://archive.ubuntu.com precise-updates/main TranslationIndex [72 B]  
Get:38 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [70 B]
Get:39 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [71 B]
Get:40 http://archive.ubuntu.com precise-updates/universe TranslationIndex [72 B]
Get:41 http://archive.ubuntu.com precise-backports/main Sources [700 B]        
Get:42 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]   
Get:43 http://archive.ubuntu.com precise-backports/universe Sources [14 B]     
Get:44 http://archive.ubuntu.com precise-backports/multiverse Sources [14 B]   
Get:45 http://archive.ubuntu.com precise-backports/main i386 Packages [559 B]  
Get:46 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:47 http://archive.ubuntu.com precise-backports/universe i386 Packages [14 B]
Get:48 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]
Get:49 http://archive.ubuntu.com precise-backports/main TranslationIndex [71 B]
Get:50 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [70 B]
Get:51 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:52 http://archive.ubuntu.com precise-backports/universe TranslationIndex [70 B]
Get:53 http://archive.ubuntu.com precise-security/main Sources [1,550 B]       
Get:54 http://archive.ubuntu.com precise-security/restricted Sources [14 B]    
Get:55 http://archive.ubuntu.com precise-security/universe Sources [2,143 B]   
Get:56 http://archive.ubuntu.com precise-security/multiverse Sources [14 B]    
Get:57 http://archive.ubuntu.com precise-security/main i386 Packages [11.9 kB] 
Get:58 http://archive.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:59 http://archive.ubuntu.com precise-security/universe i386 Packages [2,571 B]
Get:60 http://archive.ubuntu.com precise-security/multiverse i386 Packages [14 B]
Get:61 http://archive.ubuntu.com precise-security/main TranslationIndex [72 B] 
Get:62 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [70 B]
Get:63 http://archive.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:64 http://archive.ubuntu.com precise-security/universe TranslationIndex [72 B]
Get:65 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [770 B]
Get:66 http://archive.ubuntu.com precise-proposed/main i386 Packages [63.2 kB] 
Get:67 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [14 B]
Get:68 http://archive.ubuntu.com precise-proposed/universe i386 Packages [19.7 kB]
Get:69 http://archive.ubuntu.com precise-proposed/main TranslationIndex [73 B] 
Get:70 http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex [70 B]
Get:71 http://archive.ubuntu.com precise-proposed/restricted TranslationIndex [71 B]
Get:72 http://archive.ubuntu.com precise-proposed/universe TranslationIndex [73 B]
Get:73 http://archive.ubuntu.com precise/main Translation-en_CA [10.4 kB]      
Get:74 http://archive.ubuntu.com precise/main Translation-en [726 kB]          
Get:75 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]   
Get:76 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]   
Get:77 http://archive.ubuntu.com precise/universe Translation-en_CA [663 B]    
Get:78 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]    
Get:79 http://archive.ubuntu.com precise-updates/main Translation-en [9,154 B] 
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Get:80 http://archive.ubuntu.com precise-updates/restricted Translation-en [267 B]
Get:81 http://archive.ubuntu.com precise-updates/universe Translation-en [1,200 B]
Get:82 http://archive.ubuntu.com precise-backports/main Translation-en [308 B] 
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en 
Get:83 http://archive.ubuntu.com precise-security/main Translation-en [3,575 B]
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Get:84 http://archive.ubuntu.com precise-security/universe Translation-en [1,499 B]
Get:85 http://archive.ubuntu.com precise-proposed/main Translation-en [29.1 kB]
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en       
Get:86 http://archive.ubuntu.com precise-proposed/restricted Translation-en [267 B]
Get:87 http://archive.ubuntu.com precise-proposed/universe Translation-en [11.1 kB]
Fetched 17.0 MB in 1min 48s (157 kB/s)                                         
Reading package lists... Done
ventrical@ventrical1ME051:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gnome-session gnome-session-common gnome-session-fallback linux-generic
  linux-headers-generic linux-headers-generic-pae linux-image-generic shotwell
  ubuntu-wallpapers usb-creator-common usb-creator-gtk xubuntu-desktop
The following packages will be upgraded:
  apport apport-gtk at-spi2-core compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default cpp-4.6 dmsetup firefox
  firefox-globalmenu firefox-gnome-support firefox-locale-en fonts-opensymbol
  gcc-4.6 gcc-4.6-base gdb gir1.2-atspi-2.0 gir1.2-unity-5.0 glib-networking
  glib-networking-common glib-networking-services gnome-games-data gnome-orca
  gnome-sudoku gnomine gwibber gwibber-service gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter libatspi2.0-0
  libdecoration0 libdevmapper-event1.02.1 libdevmapper1.02.1 libgcc1
  libgfortran3 libgomp1 libgwibber-gtk2 libgwibber2 liblvm2app2.2 libnux-2.0-0
  libnux-2.0-common liborbit2 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtgui4
  libquadmath0 libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-impress libreoffice-java-common libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-math libreoffice-style-human
  libreoffice-style-tango libreoffice-writer libssl1.0.0 libstdc++6
  libunity-2d-private0 libunity-core-5.0-5 libunity9 libutouch-geis1
  linux-libc-dev lxc mahjongg nux-tools openssl python-apport
  python-problem-report python-software-properties python-uno qdbus
  quadrapassel remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc
  sessioninstaller software-center software-properties-common
  software-properties-gtk ttf-opensymbol unity unity-2d unity-2d-common
  unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-shell
  unity-2d-spread unity-common unity-lens-applications unity-lens-music
  unity-scope-musicstores unity-services uno-libs3 update-manager
  update-manager-core upstart ure xserver-common xserver-xorg-core
  xserver-xorg-input-synaptics xul-ext-ubufox xvfb
132 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Need to get 178 MB of archives.
After this operation, 2,392 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```
yes

I'll be back.

---

### Post by ventrical on 2012-04-30
So far .. just amazing..

Setting up gcc-4.6-base (4.6.3-1ubuntu5) ...
(Reading database ... 613581 files and directories currently installed.)
Preparing to replace libstdc++6 4.6.3-1ubuntu3 (using .../libstdc++6_4.6.3-1ubuntu5_i386.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.6.3-1ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 613581 files and directories currently installed.)
Preparing to replace cpp-4.6 4.6.3-1ubuntu3 (using .../cpp-4.6_4.6.3-1ubuntu5_i386.deb) ...
Unpacking replacement cpp-4.6 ...
Preparing to replace gcc-4.6 4.6.3-1ubuntu3 (using .../gcc-4.6_4.6.3-1ubuntu5_i386.deb) ...
Unpacking replacement gcc-4.6 ...
Preparing to replace libgcc1 1:4.6.3-1ubuntu3 (using .../libgcc1_1%3a4.6.3-1ubuntu5_i386.deb) ...
Unpacking replacement libgcc1 ...

Edit .. whoops .. 
re_1%3a3.5.2-2ubuntu3_i386.deb) ...
rmdir: failed to remove `/var/lib/libreoffice/basis3.4/program/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice/basis3.4': No such file or directory


...still unpacking..

---

### Post by ventrical on 2012-04-30
Ok.. time for re-boot.

```
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for fontconfig ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
Setting up libgomp1 (4.6.3-1ubuntu5) ...
Setting up libquadmath0 (4.6.3-1ubuntu5) ...
Setting up libgfortran3 (4.6.3-1ubuntu5) ...
Setting up cpp-4.6 (4.6.3-1ubuntu5) ...
Setting up gcc-4.6 (4.6.3-1ubuntu5) ...
Setting up libatspi2.0-0 (2.4.1-0ubuntu0.1) ...
Setting up liborbit2 (1:2.14.19-0.1ubuntu1) ...
Setting up libqtcore4 (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-sql (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-sql-sqlite (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-sql-mysql (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-xml (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-dbus (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-script (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-network (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-xmlpatterns (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-test (4:4.8.1-0ubuntu4.1) ...
Setting up qdbus (4:4.8.1-0ubuntu4.1) ...
Setting up fonts-opensymbol (2:102.2+LibO3.5.2-2ubuntu3) ...
Setting up ttf-opensymbol (2:102.2+LibO3.5.2-2ubuntu3) ...
Setting up libutouch-geis1 (2.2.9-0ubuntu2) ...
Setting up upstart (1.5-0ubuntu7) ...
Installing new version of config file /etc/logrotate.d/upstart ...
Setting up openssl (1.0.1-4ubuntu5) ...
Setting up update-manager-core (1:0.156.14.1) ...
Setting up update-manager (1:0.156.14.1) ...
Setting up python-problem-report (2.0.1-0ubuntu7) ...
Setting up python-apport (2.0.1-0ubuntu7) ...
Setting up apport (2.0.1-0ubuntu7) ...
apport start/running
Setting up apport-gtk (2.0.1-0ubuntu7) ...
Setting up at-spi2-core (2.4.1-0ubuntu0.1) ...
Installing new version of config file /etc/xdg/autostart/at-spi-dbus-bus.desktop ...
Setting up xserver-common (2:1.11.4-0ubuntu10.1) ...
Setting up xserver-xorg-core (2:1.11.4-0ubuntu10.1) ...
Setting up libunity9 (5.12.0-0ubuntu1) ...
Setting up libnux-2.0-common (2.12.0-0ubuntu1) ...
Setting up libnux-2.0-0 (2.12.0-0ubuntu1) ...
Setting up compiz-core (1:0.9.7.8-0ubuntu1) ...
Setting up libdecoration0 (1:0.9.7.8-0ubuntu1) ...
Setting up compiz-plugins-default (1:0.9.7.8-0ubuntu1) ...
Setting up compiz-plugins (1:0.9.7.8-0ubuntu1) ...
Setting up compiz-gnome (1:0.9.7.8-0ubuntu1) ...
Setting up unity-services (5.12-0ubuntu1) ...
Setting up libunity-core-5.0-5 (5.12-0ubuntu1) ...
Setting up unity-common (5.12-0ubuntu1) ...
Setting up compiz (1:0.9.7.8-0ubuntu1) ...
Setting up nux-tools (2.12.0-0ubuntu1) ...
Setting up unity (5.12-0ubuntu1) ...
Setting up firefox (12.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (12.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-gnome-support (12.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (12.0+build1-0ubuntu0.12.04.1) ...
Setting up gdb (7.4-2012.04-0ubuntu1) ...
Setting up gir1.2-atspi-2.0 (2.4.1-0ubuntu0.1) ...
Setting up gir1.2-unity-5.0 (5.12.0-0ubuntu1) ...
Setting up glib-networking-common (2.32.1-1ubuntu1) ...
Setting up glib-networking-services (2.32.1-1ubuntu1) ...
Setting up glib-networking (2.32.1-1ubuntu1) ...
Setting up gnome-games-data (1:3.4.1-0ubuntu2) ...
Setting up quadrapassel (1:3.4.1-0ubuntu2) ...
Setting up mahjongg (1:3.4.1-0ubuntu2) ...
Setting up gnomine (1:3.4.1-0ubuntu2) ...
Setting up gnome-sudoku (1:3.4.1-0ubuntu2) ...
Setting up gnome-orca (3.4.1-0ubuntu0.1) ...
Setting up gwibber-service (3.4.1-0ubuntu1) ...
Setting up libgwibber2 (3.4.1-0ubuntu1) ...
Setting up libgwibber-gtk2 (3.4.1-0ubuntu1) ...
Setting up gwibber (3.4.1-0ubuntu1) ...
Setting up gwibber-service-facebook (3.4.1-0ubuntu1) ...
Setting up gwibber-service-identica (3.4.1-0ubuntu1) ...
Setting up gwibber-service-twitter (3.4.1-0ubuntu1) ...
Setting up libreoffice-l10n-en-gb (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-l10n-en-za (1:3.5.2-2ubuntu3) ...
Setting up unity-2d-common (5.12.0-0ubuntu1) ...
Setting up linux-libc-dev (3.2.0-24.37) ...
Setting up lxc (0.7.5-3ubuntu53) ...
Setting up python-software-properties (0.82.7.1) ...
Setting up remmina-common (1.0.0-1ubuntu6) ...
Setting up remmina (1.0.0-1ubuntu6) ...
Setting up remmina-plugin-vnc (1.0.0-1ubuntu6) ...
Setting up remmina-plugin-rdp (1.0.0-1ubuntu6) ...
Setting up software-center (5.2.1) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Setting up software-properties-common (0.82.7.1) ...
Setting up software-properties-gtk (0.82.7.1) ...
Setting up unity-lens-applications (5.12.0-0ubuntu1) ...
Setting up unity-lens-music (5.12.0-0ubuntu1) ...
Setting up unity-scope-musicstores (5.12.0-0ubuntu1) ...
Setting up xserver-xorg-input-synaptics (1.5.99.902-0ubuntu5.1) ...
Setting up xul-ext-ubufox (2.0.3-0ubuntu1) ...
Setting up xvfb (2:1.11.4-0ubuntu10.1) ...
Setting up sessioninstaller (0.20+bzr128-0ubuntu1) ...
Setting up ure (3.5.2-2ubuntu3) ...
Setting up uno-libs3 (3.5.2-2ubuntu3) ...
Setting up libreoffice-style-human (1:3.5.2-2ubuntu3) ...
Setting up libdevmapper1.02.1 (2:1.02.48-4ubuntu7.1) ...
Setting up dmsetup (2:1.02.48-4ubuntu7.1) ...
update-initramfs: deferring update (trigger activated)
Setting up libdevmapper-event1.02.1 (2:1.02.48-4ubuntu7.1) ...
Setting up liblvm2app2.2 (2.02.66-4ubuntu7.1) ...
Setting up libqtgui4 (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-declarative (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-designer (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-qt3support (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-help (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-svg (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-scripttools (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-opengl (4:4.8.1-0ubuntu4.1) ...
Setting up libreoffice-style-tango (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-common (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-core (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-base-core (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-writer (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-calc (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-draw (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-impress (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-gtk (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-gnome (1:3.5.2-2ubuntu3) ...
Setting up python-uno (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-math (1:3.5.2-2ubuntu3) ...
Setting up libqtbamf1 (0.2.4-0ubuntu1) ...
Setting up libreoffice-help-en-gb (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-help-en-us (1:3.5.2-2ubuntu3) ...
Setting up libreoffice-java-common (1:3.5.2-2ubuntu3) ...
Setting up libunity-2d-private0 (5.12.0-0ubuntu1) ...
Setting up unity-2d-shell (5.12.0-0ubuntu1) ...
Setting up unity-2d-panel (5.12.0-0ubuntu1) ...
Setting up unity-2d-spread (5.12.0-0ubuntu1) ...
Setting up unity-2d (5.12.0-0ubuntu1) ...
Setting up unity-2d-launcher (5.12.0-0ubuntu1) ...
Setting up unity-2d-places (5.12.0-0ubuntu1) ...
Processing triggers for libreoffice-common ...
Setting up libreoffice-emailmerge (1:3.5.2-2ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-20-generic
ventrical@ventrical1ME051:~$ 

```

---

### Post by ventrical on 2012-04-30
Graham, your a genius !!

 Only prob is:

ventrical@ventrical1ME051:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu quantal (development branch)
Release:    12.10
Codename:    quantal
ventrical@ventrical1ME051:~$ 

and Quantal still comes up hard coded in System Monitor.. thing is .. it's Precise !!!  That was a brilliant suggestion. I'm going to spend some time on this one

but I think that is because I used those template codes that Arpanaut put up. It certainly didn't do any harm. I'm just curious if this proceedure can be used as a "system restore" tool that when a end_user has a big prob and can get to terminal and wants to save important stuff, that he can restore his system by using the back-grade process you have suggested.

---

### Post by ventrical on 2012-04-30
This is the only bug so far. Synaptic will not let me see the repos. I tried to uninstall synaptic and then re-install it .. but still not go. It just keeps looping after I press re-load. I got an idea.!

---

### Post by ventrical on 2012-04-30
Here's sources.list

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20111129.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by ronacc on 2012-04-30
> **ventrical said:**
> Graham, your a genius !!

 
I'm just curious if this proceedure can be used as a "system restore" tool that when a end_user has a big prob and can get to terminal and wants to save important stuff, that he can restore his system by using the back-grade process you have suggested.

I think the safest thing to do BEFORE ANY attempt at recovery ( and actualy before starting to try U+1 ) is to back up your /home and any other important files to some form of OFFLINE storage like a usb stick or drive or cd/dvd . I learned that the hard way when feisty formated all 4 drives on my box .

to have a good offline B/U should be the first sticky on U+1 .

---

### Post by teward on 2012-04-30
You should back up your information that you need and reinstall Precise from scratch

Downgrading is near impossible given issues with reverse compatibilities in packages after upgrading.  It will save time and effort.

---

### Post by CharlesA on 2012-04-30
> **haqking said:**
> backup your personal data and the do a fresh installation of Precise.

Less hassle and since the start of this thread you could have been back up and running in precise ;)

Also it is less likely to cause issues.

Peace

This.

> **xebian said:**
> There is.  Backup whatever you want, and then take your yy.mm.iso and then do a fresh install.  There is nothing else as easy and simple as that.

And this.

> **codingman said:**
> Thanks for everyone's input, it's just that a bunch of applications won't install or won't work because i'm in 12.10, I guess i'll just stay in QQ.

It would be easier to just see what packages are installed on the current version and reinstall them after reinstalling PP.

Just use dpkg --get-selections > somefile to get a list of packages installed and:

dpkg --set-selections < somefile to set those same packages to be installed.

---

### Post by arpanaut on 2012-04-30
@ventrical

since you are experimenting here you might want to reverse this process 
[http://ubuntuforums.org/showpost.php?p=11877873&postcount=38](http://ubuntuforums.org/showpost.php?p=11877873&postcount=38)

and see if it restores synaptics behavior, as it seemed to me that it uses this template in addition to sources.list as reference  to sources.  #This I do not know as fact.

EDIT: +1 to CharlesA et. al.  
I totally agree that backup & reinstall is the most expedient method to downgrade.

---

### Post by oshirowanen on 2012-04-30
> **codingman said:**
> I've got QQ on my computer but I was wondering if I could go to Precise from Quantal without reinstallation.

You're a brave person to upgrade to 12.04 without testing it first!  As for your question, no idea, sorry.

---

### Post by ventrical on 2012-04-30
@Arpanaut

When I ran the suggested by Grahamechanical it automatically removed that cut&paste.

---

### Post by ventrical on 2012-04-30
> **ronacc said:**
> I think the safest thing to do BEFORE ANY attempt at recovery ( and actualy before starting to try U+1 ) is to back up your /home and any other important files to some form of OFFLINE storage like a usb stick or drive or cd/dvd . I learned that the hard way when feisty formated all 4 drives on my box .

to have a good offline B/U should be the first sticky on U+1 .

Thanks ronacc.. I have 8 machines going here. 6 towers and 3 laptops... ...oh . thats 9   :) I love doing this stuff.  I'm so bored.. and so when I seen Greymechs suggestion I thought I'd give it a whirl. It is working great after all the update . Just synaptic and repos not reporting.  Synaptic does download stuff but won't let me into the repos.


 So I am going to  restore back to Quantal and see what happens.

  I'm not worried about backups because this is beta testing and I do not use my stable data installs. I have tons of hdds that I just swap in & out.

---

### Post by rg4w on 2012-04-30
I've found it handy to have /home in a separate partition, making installation of both upgrades and downgrades much easier.  Note though that downgrading may mean you have some settings which could be incompatible with another system.  Better still to evaluate upgrades carefully via USB before install.

---

### Post by arpanaut on 2012-04-30
> **ventrical said:**
> @Arpanaut

When I ran the suggested by Grahamechanical it automatically removed that cut&paste.
Interesting  Maybe try:
```
sudo dpkg-reconfigure synaptic
```

If you haven't already moved on.

---

### Post by ventrical on 2012-04-30
@arpanaut

Heres what happened. I re-loaded the Quantal sources.list, template, etc and then got an Apport error on "software sources". It asked me to relaunch, yes and then <send a report> yes. After 10 seconds the Software Sources came back up in synaptic. :)

  I plan to go back down there to Precise and then try your code , but , also I had the same error when I reverted back to Precise so I am going to try and use the 're-launch' in Apport also.

 The really neat thing is that to come back up to QQ I only had to download 33MBs of files.

  I may go all the way back to Maveric and then come back up.  It's a lot faster than doing backups. I am in no way saying that this proceedure is "stable" but I'm have a great time :) - and we are in beta testing :)

---

### Post by arpanaut on 2012-04-30
> and we are in beta testing :smile:actually pre-alpha:biggrin:

---

### Post by tekstr1der on 2012-04-30
> **jerrylamos said:**
> Expect to re-install frequently...
Better get into practice on install.  And install.  And re-install.

Nah, almost never necessary. I ran the same install of Intrepid Alpha 2 all the way through Lucid 10.04.2. 

Four full dev cycles, some very rocky, and the system was stable as heck at the end. It's just a matter of keeping things clean and addressing issues as they arise.

---

### Post by ventrical on 2012-04-30
Synaptic will work if I put in those Quantal templates (with Precise) but  it does not work properly. When I remove the template then the Software Sources will just not come up yet  update/upgrade  works just great from terminal.

So now I am going to try to downgrade to Maveric and the back up to Precise then Quantal.

hehehe .. Maveric did not work very well.. Most of the repos are not active. I was , however , able to successfully get back to Quantal and a good working Synaptic.

But I think there is really something to all of this back-grading theory. It may help some who have lots of data that have borked system , get them back up and with all the data too.

---

### Post by ventrical on 2012-04-30
> **tekstr1der said:**
> Nah, almost never necessary. I ran the same install of Intrepid Alpha 2 all the way through Lucid 10.04.2. 

Four full dev cycles, some very rocky, and the system was stable as heck at the end. It's just a matter of keeping things clean and addressing issues as they arise.

  It's amazing how rock-solid some of the alphas are, only to update to final release and totally destroy the system.

---

### Post by Mathor on 2012-04-30
> **ventrical said:**
> Synaptic will work if I put in those Quantal templates (with Precise) but  it does not work properly. When I remove the template then the Software Sources will just not come up yet  update/upgrade  works just great from terminal.

So now I am going to try to downgrade to Maveric and the back up to Precise then Quantal.

hehehe .. Maveric did not work very well.. Most of the repos are not active. I was , however , able to successfully get back to Quantal and a good working Synaptic.

But I think there is really something to all of this back-grading theory. It may help some who have lots of data that have borked system , get them back up and with all the data too.

I think the problem here is trying to go from Gnome 3 to Gnome 2 to Gnome 3. That's painful even as a pure LTS to LTS upgrade, and rarely works for most users. Broken dependencies galore.

---

### Post by tekstr1der on 2012-04-30
> **ventrical said:**
> It's amazing how rock-solid some of the alphas are, only to update to final release and totally destroy the system.

Lately there's been increased focus on packaging "stability" during the testing phase. I'd posted about this initiative at the beginning of 12.04 dev cycle:
[http://ubuntuforums.org/showpost.php?p=11501157&postcount=19](http://ubuntuforums.org/showpost.php?p=11501157&postcount=19)

In my case, each of those alphas evolved into betas, rc's and eventually releases... until the subsequent toolchain upload... then back to dev. ZERO re-installs (my point in posting a response @jerrylamos), just lots of updating/fixing along the way. I've never had an experience where a final Ubuntu release would "destroy the system"!

It was essentially a rolling release of development, but eventually settled out on the Lucid release due to aging hardware. I used it daily (was my work laptop) all the way till after the 2nd point-release of Lucid(about a year past Lucid release) without any issues whatsoever. Rock-solid stable that final year.

Also, of course, it would be stupid to use a constantly-in-dev install for a work machine...I dual-boot with Arch so I always have a functional system available when things get rocky in Ubuntu alpha world :)

---

### Post by ventrical on 2012-04-30
> **tekstr1der said:**
> Lately there's been increased focus on packaging "stability" during the testing phase. I'd posted about this initiative at the beginning of 12.04 dev cycle:
[http://ubuntuforums.org/showpost.php?p=11501157&postcount=19](http://ubuntuforums.org/showpost.php?p=11501157&postcount=19)

In my case, each of those alphas evolved into betas, rc's and eventually releases... until the subsequent toolchain upload... then back to dev. ZERO re-installs (my point in posting a response @jerrylamos), just lots of updating/fixing along the way. I've never had an experience where a final Ubuntu release would "destroy the system"!

It was essentially a rolling release of development, but eventually settled out on the Lucid release due to aging hardware. I used it daily (was my work laptop) all the way till after the 2nd point-release of Lucid(about a year past Lucid release) without any issues whatsoever. Rock-solid stable that final year.

Also, of course, it would be stupid to use a constantly-in-dev install for a work machine...I dual-boot with Arch so I always have a functional system available when things get rocky in Ubuntu alpha world :)


Thats fair enough. I guess I can rephrase myself and not be so disparging towards Ubuntu. I think it was a Natty Install on an Acer Aspire 3620 and something happened during an update , lost the wireless, couldn't get it back .. I wrote something to the effect that if the wireless is not provided for or obsoleted by an upgrade then I was going elsewhere (Fedora) [which btw worked just beautiful on that laptop]. So which brings us back to the topic of  downgrading to be able to restore a system that was once working really well. I have a Dell B130. I have one hdd with the alpha 2 (updated onwards to about three weeks before release and then not updated) that works just excellently. Not a glitch at all. Then I have another hdd with a full release, post beta 2, updated, sideXside with WinXP and it sort of has lost a certain type of smoothness and ambiance.. but then perhaps that is just me. I had to manually install the broadcom drivers.. but the alpha II just pulled them right up from the start.

'destroy a system' .. perhaps my statement is too harsh and un Ubuntu_like. or I'm just plain embellishing a minor problem. I should choose my words more carefully.

---

### Post by Mathor on 2012-04-30
> **ventrical said:**
> Thats fair enough. I guess I can rephrase myself and not be so disparging towards Ubuntu. I think it was a Natty Install on an Acer Aspire 3620 and something happened during an update , lost the wireless, couldn't get it back .. I wrote something to the effect that if the wireless is not provided for or obsoleted by an upgrade then I was going elsewhere (Fedora) [which btw worked just beautiful on that laptop]. So which brings us back to the topic of  downgrading to be able to restore a system that was once working really well. I have a Dell B130. I have one hdd with the alpha 2 (updated onwards to about three weeks before release and then not updated) that works just excellently. Not a glitch at all. Then I have another hdd with a full release, post beta 2, updated, sideXside with WinXP and it sort of has lost a certain type of smoothness and ambiance.. but then perhaps that is just me. I had to manually install the broadcom drivers.. but the alpha II just pulled them right up from the start.

'destroy a system' .. perhaps my statement is too harsh and un Ubuntu_like. or I'm just plain embellishing a minor problem. I should choose my words more carefully.

Well, in my experience (I've only used N,O, and P) with Ubuntu releases, major showstopper bugs like that almost always resolve.  Oneiric was rather buggy, but as I updated, all of my bugs became nonexistent. 

In Fedora and OpenSUSE, however, I've never been able to get any sort of wireless configuration working.

But back to the original point, I think this method of downgrading can work, but only if there are few changes. In the case of Quantal to Precise, obviously the changes are so minute that a downgrade would be pretty simple. From Precise to Oneiric, still there were not a large amount of changes compared to in some releases.  I think downgrading from 12.04 to 10.04 would be pretty impossible, because of the major file type changes from gnome3 to gnome2 gtk3 to gtk2  lightdm gdm etc etc etc.   

I was really into Linux Mint Debian at one point, and upon my Debian Testing upgrading all of their repos to Gnome3 and GTK3, there was a lot of mess on my system.

---

### Post by ventrical on 2012-04-30
I am very pleased how Precise has turned out, Ubuntu in general for that matter.  I'm not belly aching and I hope it doesn't sound like that. Oneiric also. Just some natty installs. This particular install that I am working from (among 9 different PCs) was originally installed with Edubuntu 11.04(natty). Now, thats the thing, Edubuntu 11.04dvd installed great but other versions of Ubuntu Straight Up Natty had some big problems .Why?  I don't know.  Just reporting in .  Iv'e run this system through the mill .. doing everything I can to smoke it flat - but it is very resilient. In fact, all the Ubuntus are resilient and I want to explore all the different possibilities. Thats what keeps me interested.

  My training tells me the same thing that any stuffed shirt IT would dispense to their customers - declare your assumptions, document your work and do frequent back-ups. But this is 2012 and when this stuffed shirt IT (me) tells a customer to back up their system then I might as well be speaking some 5,000 year old dialect of neanthradal cave code to them because perfectly good English fails it seems. I would be better off using sign language:)

I started with Hardy Heron. It was fun. :) Then other versions of Linux and back to Ubuntu.  I came back to Ubuntu because I wanted to see Unity 3D and 2D succeed (and still do) [and it is]!  I still do Mint on certain PCs. It is,... elegant. Ubuntu is fun and flexible. I can do things with Ubuntu that you can't do with other OSes. You can bend it, shake it, rock it, roll it, hammer it, swear at it and it still gets up in the morning ready to serve my internet needs.

  So even in our questions and our critisisms, it sparks interest and inspires innovation.  We are all standing on the shoulders of giants here I think.... and .. , and YOU become that giant. What you contribute makes YOU an Ubuntu Rock Star.. and then others too can be an integral part of it all.

---

### Post by xyzzyman on 2012-05-01
> **ventrical said:**
> So even in our questions and our critisisms, it sparks interest and inspires innovation.  We are all standing on the shoulders of giants here I think.... and .. , and YOU become that giant. What you contribute makes YOU an Ubuntu Rock Star.. and then others too can be an integral part of it all.

But in the end it's just an operating system. A simple tool that's a means to an end.

---

### Post by ventrical on 2012-05-01
> **xyzzyman said:**
> But in the end it's just an operating system. A simple tool that's a means to an end.


 And remember my friend, your playing the piano, the piano is not playing you! Thats all the difference.

---

### Post by ventrical on 2012-05-01
I did , just for experimental purposes, re-break a system with a bad libx file and tried this process for recovery and it did not work. The file had to be manually downgraded even after the downgrade from Quantal to Presice.

 So still much more work in progress for a streamlined system restore tool for noobs :)

---

### Post by williejones on 2012-05-03
> So even in our questions and our critisisms, it sparks interest and  inspires innovation.  We are all standing on the shoulders of giants  here I think.... and .. , and YOU become that giant. What you contribute  makes YOU an Ubuntu Rock Star.. and then others too can be an integral  part of it all.Well said **[COLOR=black]Vertical[/COLOR]**

---

### Post by ventrical on 2012-05-04
> **williejones said:**
> Well said **[COLOR=black]Vertical[/COLOR]**

Even the proof readers and the documentarians deserve a star on there foreheads.Generally speaking, I am not sure how many times I have taken all that work for granted in the past.
:)

---

### Post by postmaxin on 2012-08-29
> **ventrical said:**
> Graham, your a genius !!

 Only prob is:

ventrical@ventrical1ME051:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu quantal (development branch)
Release:    12.10
Codename:    quantal
ventrical@ventrical1ME051:~$ 

and Quantal still comes up hard coded in System Monitor.. thing is .. it's Precise !!!  That was a brilliant suggestion. I'm going to spend some time on this one

but I think that is because I used those template codes that Arpanaut put up. It certainly didn't do any harm. I'm just curious if this proceedure can be used as a "system restore" tool that when a end_user has a big prob and can get to terminal and wants to save important stuff, that he can restore his system by using the back-grade process you have suggested.

Huh. I tried the exact same thing tonight. My video card has issues in Precise... I thought I'd see if they were better in Quantal... turns out the card doesn't work at *all* in Quantal or on a 3.5.0 kernel!

Anyway, at the end my lsb_release says it's 12.04 again.

I wonder if there's a way to optimize this more -- I downgraded everything to precise -- then I had to re-upgrade in order to apply all of the precise-security updates. The security updates were >400MB. If I had preferred precise-security, then fell back on precise, that would have been a huge savings.

---

### Post by grahammechanical on 2012-08-29
@postmaxin

Are you saying that one of my crazy suggestions actually works? You are joking me. Yes? Well I never. May be I will get up the nerve to test this myself. Once I recover from all the Quantal breakage that has been going on the last few days.

Regards.

---

