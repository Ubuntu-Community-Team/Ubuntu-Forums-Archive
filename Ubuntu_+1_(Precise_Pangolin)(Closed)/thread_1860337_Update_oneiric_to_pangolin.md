---
title: "Update oneiric to pangolin"
date: 2011-10-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by novatillasku on 2011-10-14
How can update oneiric to pangolin with terminal?

---

### Post by thatguruguy on 2011-10-14
Since there aren't even any alphas released yet, you can't.

---

### Post by ventrical on 2011-10-14
I use :

First this one:
sudo sed -i s'/oneiric/precise/g' /etc/apt/sources.list

Then this one:
sudo apt-get update && sudo apt-get dist-upgrade

Don't forget:


sudo apt-get update
sudo apt-get upgrade



  :)

---

### Post by ventrical on 2011-10-14
Here is my update today.



```
dale@ubuntu:~$ sudo apt-get update
[sudo] password for dale: 
Ign http://extras.ubuntu.com precise InRelease
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://extras.ubuntu.com precise Release.gpg                               
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://extras.ubuntu.com precise Release                                   
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://security.ubuntu.com precise-security Release                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://security.ubuntu.com precise-security/main Sources                   
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease                        
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Err http://extras.ubuntu.com precise/main Sources                              
  404  Not Found
Err http://extras.ubuntu.com precise/main i386 Packages                        
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA                    
Ign http://archive.canonical.com precise/partner Translation-en_CA             
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://extras.ubuntu.com precise/main Translation-en_CA          
Ign http://archive.canonical.com precise/partner Translation-en      
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise-updates Release.gpg
Get:2 http://archive.ubuntu.com precise Release [49.6 kB]
Hit http://archive.ubuntu.com precise-updates Release                          
Get:3 http://archive.ubuntu.com precise/main i386 Packages [1,227 kB]          
Get:4 http://archive.ubuntu.com precise/universe i386 Packages [4,468 kB]      
Get:5 http://archive.ubuntu.com precise/restricted i386 Packages [8,216 B]     
Get:6 http://archive.ubuntu.com precise/multiverse i386 Packages [119 kB]      
Get:7 http://archive.ubuntu.com precise/main TranslationIndex [74 B]           
Get:8 http://archive.ubuntu.com precise/multiverse TranslationIndex [73 B]     
Get:9 http://archive.ubuntu.com precise/restricted TranslationIndex [72 B]     
Get:10 http://archive.ubuntu.com precise/universe TranslationIndex [75 B]      
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages           
Hit http://archive.ubuntu.com precise-updates/main i386 Packages               
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Get:11 http://archive.ubuntu.com precise/main Translation-en [701 kB]          
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Get:12 http://archive.ubuntu.com precise/universe Translation-en [3,165 kB]    
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Fetched 9,739 kB in 60s (161 kB/s)                                             
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
dale@ubuntu:~$ 
```

---

### Post by ventrical on 2011-10-14
And here are the upgrades today .. but they are actually from Oneiric.

```
dale@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-ppdc dpkg gnome-user-guide
  libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
  libdvdread4 libffi6 libncurses5 libncursesw5 libnih-dbus1 libnih1 libtinfo5
  ncurses-base ncurses-bin python python-minimal
24 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,047 kB of archives.
After this operation, 7,212 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main dpkg i386 1.16.1ubuntu1 [1,818 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise/main ncurses-bin i386 5.9-2 [149 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise/main ncurses-base all 5.9-2 [21.9 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ precise/main python-minimal all 2.7.2-7ubuntu4 [29.8 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ precise/main python all 2.7.2-7ubuntu4 [166 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ precise/main libncursesw5 i386 5.9-2 [170 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ precise/main libtinfo5 i386 5.9-2 [65.0 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ precise/main libncurses5 i386 5.9-2 [142 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ precise/main libffi6 i386 3.0.11~rc1-5 [16.4 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ precise/main libcups2 i386 1.5.0-8ubuntu1 [176 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ precise/main libcupscgi1 i386 1.5.0-8ubuntu1 [32.6 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ precise/main libcupsdriver1 i386 1.5.0-8ubuntu1 [22.4 kB]
Get:13 http://archive.ubuntu.com/ubuntu/ precise/main libcupsimage2 i386 1.5.0-8ubuntu1 [54.1 kB]
Get:14 http://archive.ubuntu.com/ubuntu/ precise/main libcupsmime1 i386 1.5.0-8ubuntu1 [16.0 kB]
Get:15 http://archive.ubuntu.com/ubuntu/ precise/main libcupsppdc1 i386 1.5.0-8ubuntu1 [55.4 kB]
Get:16 http://archive.ubuntu.com/ubuntu/ precise/main libnih-dbus1 i386 1.0.3-4ubuntu3 [15.2 kB]
Get:17 http://archive.ubuntu.com/ubuntu/ precise/main libnih1 i386 1.0.3-4ubuntu3 [53.4 kB]
Get:18 http://archive.ubuntu.com/ubuntu/ precise/main cups-common all 1.5.0-8ubuntu1 [712 kB]
Get:19 http://archive.ubuntu.com/ubuntu/ precise/main cups-bsd i386 1.5.0-8ubuntu1 [43.4 kB]
Get:20 http://archive.ubuntu.com/ubuntu/ precise/main cups-client i386 1.5.0-8ubuntu1 [161 kB]
Get:21 http://archive.ubuntu.com/ubuntu/ precise/main cups-ppdc i386 1.5.0-8ubuntu1 [31.7 kB]
Get:22 http://archive.ubuntu.com/ubuntu/ precise/main cups i386 1.5.0-8ubuntu1 [1,975 kB]
Get:23 http://archive.ubuntu.com/ubuntu/ precise/main gnome-user-guide all 3.2.0.1-1 [1,067 kB]
Get:24 http://archive.ubuntu.com/ubuntu/ precise/universe libdvdread4 i386 4.1.3-10ubuntu4.1 [54.9 kB]
Fetched 7,047 kB in 37s (188 kB/s)                                             
Preconfiguring packages ...
(Reading database ... 212523 files and directories currently installed.)
Preparing to replace dpkg 1.16.0.3ubuntu5 (using .../dpkg_1.16.1ubuntu1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
dpkg: warning: Info file /var/lib/dpkg/info/linux-generic.md5sums not associated to any package
dpkg: warning: Info file /var/lib/dpkg/info/linux-generic.list not associated to any package
Setting up dpkg (1.16.1ubuntu1) ...
(Reading database ... 212520 files and directories currently installed.)
Preparing to replace ncurses-bin 5.9-1ubuntu5 (using .../ncurses-bin_5.9-2_i386.deb) ...
Unpacking replacement ncurses-bin ...
Processing triggers for man-db ...
Setting up ncurses-bin (5.9-2) ...
(Reading database ... 212520 files and directories currently installed.)
Preparing to replace ncurses-base 5.9-1ubuntu5 (using .../ncurses-base_5.9-2_all.deb) ...
Unpacking replacement ncurses-base ...
Setting up ncurses-base (5.9-2) ...
(Reading database ... 212520 files and directories currently installed.)
Preparing to replace python-minimal 2.7.2-7ubuntu2 (using .../python-minimal_2.7.2-7ubuntu4_all.deb) ...
Unpacking replacement python-minimal ...
Processing triggers for man-db ...
Setting up python-minimal (2.7.2-7ubuntu4) ...
(Reading database ... 212520 files and directories currently installed.)
Preparing to replace python 2.7.2-7ubuntu2 (using .../python_2.7.2-7ubuntu4_all.deb) ...
Unpacking replacement python ...
Preparing to replace libncursesw5 5.9-1ubuntu5 (using .../libncursesw5_5.9-2_i386.deb) ...
Unpacking replacement libncursesw5 ...
Preparing to replace libtinfo5 5.9-1ubuntu5 (using .../libtinfo5_5.9-2_i386.deb) ...
Unpacking replacement libtinfo5 ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Setting up libtinfo5 (5.9-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 212520 files and directories currently installed.)
Preparing to replace libncurses5 5.9-1ubuntu5 (using .../libncurses5_5.9-2_i386.deb) ...
Unpacking replacement libncurses5 ...
Setting up libncurses5 (5.9-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 212520 files and directories currently installed.)
Preparing to replace libffi6 3.0.11~rc1-2 (using .../libffi6_3.0.11~rc1-5_i386.deb) ...
Unpacking replacement libffi6 ...
Preparing to replace libcups2 1.5.0-8 (using .../libcups2_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement libcups2 ...
Preparing to replace libcupscgi1 1.5.0-8 (using .../libcupscgi1_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement libcupscgi1 ...
Preparing to replace libcupsdriver1 1.5.0-8 (using .../libcupsdriver1_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement libcupsdriver1 ...
Preparing to replace libcupsimage2 1.5.0-8 (using .../libcupsimage2_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace libcupsmime1 1.5.0-8 (using .../libcupsmime1_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement libcupsmime1 ...
Preparing to replace libcupsppdc1 1.5.0-8 (using .../libcupsppdc1_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement libcupsppdc1 ...
Preparing to replace libnih-dbus1 1.0.3-4ubuntu2 (using .../libnih-dbus1_1.0.3-4ubuntu3_i386.deb) ...
Unpacking replacement libnih-dbus1 ...
Preparing to replace libnih1 1.0.3-4ubuntu2 (using .../libnih1_1.0.3-4ubuntu3_i386.deb) ...
Unpacking replacement libnih1 ...
Preparing to replace cups-common 1.5.0-8 (using .../cups-common_1.5.0-8ubuntu1_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.5.0-8 (using .../cups-bsd_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace cups-client 1.5.0-8 (using .../cups-client_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement cups-client ...
Preparing to replace cups-ppdc 1.5.0-8 (using .../cups-ppdc_1.5.0-8ubuntu1_i386.deb) ...
Unpacking replacement cups-ppdc ...
Preparing to replace cups 1.5.0-8 (using .../cups_1.5.0-8ubuntu1_i386.deb) ...
cups stop/waiting
Unpacking replacement cups ...
Preparing to replace gnome-user-guide 3.2.0.1-0ubuntu1 (using .../gnome-user-guide_3.2.0.1-1_all.deb) ...
Unpacking replacement gnome-user-guide ...
Preparing to replace libdvdread4 4.1.3-10ubuntu4 (using .../libdvdread4_4.1.3-10ubuntu4.1_i386.deb) ...
Unpacking replacement libdvdread4 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Setting up python (2.7.2-7ubuntu4) ...
Setting up libncursesw5 (5.9-2) ...
Setting up libffi6 (3.0.11~rc1-5) ...
Setting up libcups2 (1.5.0-8ubuntu1) ...
Setting up libcupscgi1 (1.5.0-8ubuntu1) ...
Setting up libcupsdriver1 (1.5.0-8ubuntu1) ...
Setting up libcupsimage2 (1.5.0-8ubuntu1) ...
Setting up libcupsmime1 (1.5.0-8ubuntu1) ...
Setting up libcupsppdc1 (1.5.0-8ubuntu1) ...
Setting up libnih1 (1.0.3-4ubuntu3) ...
Setting up libnih-dbus1 (1.0.3-4ubuntu3) ...
Setting up cups-common (1.5.0-8ubuntu1) ...
Setting up cups-client (1.5.0-8ubuntu1) ...
Setting up cups-bsd (1.5.0-8ubuntu1) ...
Setting up cups-ppdc (1.5.0-8ubuntu1) ...
Setting up cups (1.5.0-8ubuntu1) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.cupsd ...
cups start/running, process 5399
Updating PPD files for cups ...
Setting up gnome-user-guide (3.2.0.1-1) ...
Setting up libdvdread4 (4.1.3-10ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dale@ubuntu:~$ 
```

---

### Post by alphacrucis2 on 2011-10-14
> **thatguruguy said:**
> Since there aren't even any alphas released yet, you can't.

You can upgrade as soon as the tool chain is loaded by editing sources. That occurred much faster than I recall for previous releases.

---

### Post by jerrylamos on 2011-10-14
I'd recommend a fresh install of Ocelot latest level in a test partition.
I just sudo gedit /etc/apt/sources.list and replace all oneiric with precise, then sudo apt-get update, apt-get upgrade, reboot.

It booted up O.K.  That means not much done with incompatible packages yet.

Do note leave Software Sources alone after this...

Have fun.

I just did a fresh Ocelot USB install on this IBM Thinkpad T40 which failed on "configuring apt".  After that, grub busted big time.  See launchpad bug #874216.  No fun.  Installed again from CD O.K. 

Good luck, Jerry

---

### Post by ventrical on 2011-10-14
> **jerrylamos said:**
> I'd recommend a fresh install of Ocelot latest level in a test partition.
I just sudo gedit /etc/apt/sources.list and replace all oneiric with precise, then sudo apt-get update, apt-get upgrade, reboot.

It booted up O.K.  That means not much done with incompatible packages yet.

Do note leave Software Sources alone after this...

Have fun.

I just did a fresh Ocelot USB install on this IBM Thinkpad T40 which failed on "configuring apt".  After that, grub busted big time.  See launchpad bug #874216.  No fun.  Installed again from CD O.K. 

Good luck, Jerry


So far I have had really good luck with all installs of Oneiric. Laptop & desktops. It had got stuck on 'configuring apt' but I just waited it out and it punched itself through.  Sometimes those 'waffer' Thinkpads can get the CD laser aperture 'smudged'. I usually use a cue-tip with 99%isopropynol (I'm not worried about lanolin) but I fixed a lot of CDs this way. It's a thing one would least suspect.

---

### Post by novatillasku on 2011-10-14
Yes, i have an fresh oneiric wait for pangolin in one partition to test.

Tomorrow go!

Thank's!!

---

### Post by garvinrick4 on 2011-10-14
> I'd recommend a fresh install of Ocelot latest level in a test partition.
I just sudo gedit /etc/apt/sources.list and replace all oneiric with precise, then sudo apt-get update, apt-get upgrade, reboot.

It booted up O.K.  That means not much done with incompatible packages yet.

Do note leave Software Sources alone after this...

Have fun.

I just did a fresh Ocelot USB install on this IBM Thinkpad T40 which  failed on "configuring apt".  After that, grub busted big time.  See  launchpad bug #874216.  No fun.  Installed again from CD O.K. 

Good luck, JerryAll you did while in last distribution bug testing was moan and groan and nothing works and all is bad with Ubuntu and now you want to do it again with 12.04. 
We all get problems in Alpha's and Beta's we expect it, it is part of the testing procedure. You are going there again Jerry, you do know there will be breakage when Alpha
comes out in December right? Never usually say anything but just want to make sure you know that all is not going to be perfect for you while bug testing. See you in December Jerry. Have a nice Day.
No disrespect intended Jerry just never thought you would bug test again.
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule)

---

### Post by philinux on 2011-10-14
> **jerrylamos said:**
> I'd recommend a fresh install of Ocelot latest level in a test partition.
I just sudo gedit /etc/apt/sources.list and replace all oneiric with precise, then sudo apt-get update, apt-get upgrade, reboot.

It booted up O.K.  That means not much done with incompatible packages yet.

Do note leave Software Sources alone after this...

Have fun.

I just did a fresh Ocelot USB install on this IBM Thinkpad T40 which failed on "configuring apt".  After that, grub busted big time.  See launchpad bug #874216.  No fun.  Installed again from CD O.K. 

Good luck, Jerry

Yeah that's my usual way at this point once the toolchain is uploaded just manually change sources.list

---

### Post by Quackers on 2011-10-14
> **ventrical said:**
> I use :

First this one:
sudo sed -i s'/oneiric/pangolin/g' /etc/apt/sources.list

Then this one:
sudo apt-get update && sudo apt-get dist-upgrade

Don't forget:


sudo apt-get update
sudo apt-get upgrade



  :)

Shouldn't that be ```
sudo sed -i s'/oneiric/precise/g' /etc/apt/sources.list
```
???

---

### Post by 3vi1 on 2011-10-14
> **ventrical said:**
> Here is my update today.



```
Err http://extras.ubuntu.com precise/main Sources                              
  404  Not Found
Err http://extras.ubuntu.com precise/main i386 Packages                        
  404  Not Found
```

That's to be expected - the extras repo doesn't make sense for a version that's not frozen.  Either comment out those lines in your sources.list, or set them back to oneiric.

Something in the current updates broke Unity for me - but that's no big deal since I can still login via gnome-shell (which, if you install Docky, is quite livable).

-J

---

### Post by ranch hand on 2011-10-14
> **garvinrick4 said:**
> All you did while in last distribution bug testing was moan and groan and nothing works and all is bad with Ubuntu and now you want to do it again with 12.04. 
We all get problems in Alpha's and Beta's we expect it, it is part of the testing procedure. You are going there again Jerry, you do know there will be breakage when Alpha
comes out in December right? Never usually say anything but just want to make sure you know that all is not going to be perfect for you while bug testing. See you in December Jerry. Have a nice Day.
No disrespect intended Jerry just never thought you would bug test again.
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule)
While Jerry is quite able to defend himself, I feel that you are insulting a friend of mine.  He has been testing Ubuntu about as long as you have been a member here.

He is always working on some problem that has come up.

He is also a fellow grumpy geezer.  You may not think so but it might be a good idea for Ubuntu to listen to the fastest growing portion of the population.

---

### Post by garvinrick4 on 2011-10-15
> While Jerry is quite able to defend himself, I feel that you are insulting a friend of mineIt was not meant as an insult it was an observation on posts made in threads in and out of stable and unstable versions of Ubuntu and just took for granted he was unhappy with all phases of Ubuntu and its
directions. Jerry if you took as an insult to you personally I do apologize was not intended to be just one mans observations.
> He is also a fellow grumpy geezer.  You may not think so but it might be  a good idea for Ubuntu to listen to the fastest growing portion of the  population.Have 8 Grandchildren myself ranchhand lets leave old where it lies. There is no one that roams through
the halls of these Forums that has not read a post or two by ranch hand and we are all welcome to our own
opinions on Ubuntu and its direction and as Forest Gump says "that is all I got to say about that". You take care ranch hand.

---

### Post by jbicha on 2011-10-15
Just one comment: there's a good amount of updates that are in oneiric-proposed that haven't landed in precise yet. Perhaps you should keep oneiric-proposed and oneiric-updates in your sources for the next week or so while the new archive gets going.

---

### Post by effenberg0x0 on 2011-10-15
> **garvinrick4 said:**
> Have 8 Grandchildren myself 

So, this "computers" and Internet thing, all the kids with their "Windows", "Linux" and their videogames and damn telephones ringing everywhere. You think this is really going somewhere? Where are the good books? Kids need encyclopedias.

Effenberg

---

### Post by garvinrick4 on 2011-10-15
> So, this "computers" and Internet thing, all the kids with their  "Windows", "Linux" and their videogames and damn telephones ringing  everywhere. You think this is really going somewhere? Where are the good  books? Kids need encyclopedias.You know I saw a baby that had learned to change pages on her mothers ipad with the
flick of her little finger. She had a magazine in front of her and was trying to change pages
like it was an ipad by swiping on it. I wonder if Books are going to all be antiques in the
near future. If a baby already has the engraved notion from Mom to swipe instead of flip pages it is not to far off. 
We will have to put our copy of MobyDick and Great Expectations  in our wills.

---

### Post by philinux on 2011-10-15
> **garvinrick4 said:**
> You know I saw a baby that had learned to change pages on her mothers ipad with the
flick of her little finger. She had a magazine in front of her and was trying to change pages
like it was an ipad by swiping on it. I wonder if Books are going to all be antiques in the
near future. If a baby already has the engraved notion from Mom to swipe instead of flip pages it is not to far off. 
We will have to put our copy of MobyDick and Great Expectations  in our wills.

My girlfriend asked me to delete a few messages on her phone. I was jabbing the screen like a twit and nothing happening. Old phone no touch screen lol.

---

### Post by ventrical on 2011-10-15
> **Quackers said:**
> Shouldn't that be ```
sudo sed -i s'/oneiric/precise/g' /etc/apt/sources.list
```???


I think your right Quakers.

 I originally edited the 's to s' but I forgot the space I think.

---

### Post by cecilpierce on 2011-10-15
> **ventrical said:**
> I think your right Quakers.

 I originally edited the 's to s' but I forgot the space I think.

If I change oneiric to precise now will I still get updates for oneiric or should I wait till tool chain is uploaded ???

---

### Post by jerrylamos on 2011-10-15
> **cecilpierce said:**
> If I change oneiric to precise now will I still get updates for oneiric or should I wait till tool chain is uploaded ???

I've got a partition with Oneiric where I get updates for Oneiric.

I've got a test partition where I get updates for Precise.  These could well be different than the Oneiric updates.

Since Precise is likely to crash from time to time in development, I always use a test partition - in this case, on a USB hard drive, where even Precise's grub updates the USB grub /dev/sdb and not the grub on /dev/sda.

Bios is set to boot the USB hard drive if it is attached.

Have fun,

Jerry

---

### Post by cecilpierce on 2011-10-15
Thanks Jerry, I think i'll install another for Precise   :D

---

### Post by ventrical on 2011-10-15
> **jerrylamos said:**
> I've got a partition with Oneiric where I get updates for Oneiric.

I've got a test partition where I get updates for Precise.  These could well be different than the Oneiric updates.

Since Precise is likely to crash from time to time in development, I always use a test partition - in this case, on a USB hard drive, where even Precise's grub updates the USB grub /dev/sdb and not the grub on /dev/sda.

Bios is set to boot the USB hard drive if it is attached.

Have fun,

Jerry
  I have been thinking about this one seriously. I sometimes get overly enthusiastic :)

  Guess I should grab an old HDD and set up PP on that one. But it's working alright so far on my main disk.

---

### Post by Quackers on 2011-10-15
> **ventrical said:**
> I think your right Quakers.

 I originally edited the 's to s' but I forgot the space I think.

I was referring to the use of /precise/ rather than /pangolin/ in the command :-)

---

### Post by ventrical on 2011-10-15
> **Quackers said:**
> I was referring to the use of /precise/ rather than /pangolin/ in the command :-)


Ok.. thanks Quackers.. I think I was on a "save the pangolins" mindset when I wrote that. I think Iv'e  been dreaming about them :)

aheaheahe

---

### Post by ranch hand on 2011-10-15
> **garvinrick4 said:**
> It was not meant as an insult it was an observation on posts made in threads in and out of stable and unstable versions of Ubuntu and just took for granted he was unhappy with all phases of Ubuntu and its
directions. Jerry if you took as an insult to you personally I do apologize was not intended to be just one mans observations.
Have 8 Grandchildren myself ranchhand lets leave old where it lies. There is no one that roams through
the halls of these Forums that has not read a post or two by ranch hand and we are all welcome to our own
opinions on Ubuntu and its direction and as Forest Gump says "that is all I got to say about that". You take care ranch hand.
Good Gods above and below, the place is full of grumpy geezers.

Should have a sub-forum of our own.  If we could remember what we were talking about I am sure it would be interesting.

---

### Post by PaulInBHC on 2011-10-15
I'm 58 with 3 grandkids. Where do I sign up?

---

### Post by garvinrick4 on 2011-10-15
> Should have a sub-forum of our own.  
It is lucky we would be from all different time zones or we would all end our
sessions at 4:00 o'clock in the afternoon to eat dinner!!!
What would These Forums be without the retired and or pensioners to make sure
the young users are looked after in a proper fashion, no what I mean?

---

### Post by cecilpierce on 2011-10-16
Is it possible to have both oneiric and precise in the sources.list ?

---

### Post by jbicha on 2011-10-16
> **cecilpierce said:**
> Is it possible to have both oneiric and precise in the sources.list ?

Yes, I recommend keeping extras.ubuntu.com and partner at oneiric. And of course virtually all PPAs are oneiric or lower.

For the next week or two, it's probably good to keep oneiric-updates and oneiric-proposed as precise might not actually have the newest updates in some cases. But that's just a temporary situation. By November at least, you can drop oneiric-updates and oneiric-proposed from your sources.

---

### Post by cecilpierce on 2011-10-16
> **jbicha said:**
> Yes, I recommend keeping extras.ubuntu.com and partner at oneiric. And of course virtually all PPAs are oneiric or lower.

For the next week or two, it's probably good to keep oneiric-updates and oneiric-proposed as precise might not actually have the newest updates in some cases. But that's just a temporary situation. By November at least, you can drop oneiric-updates and oneiric-proposed from your sources.

Thanks   :)

---

### Post by ventrical on 2011-10-16
> **garvinrick4 said:**
> It is lucky we would be from all different time zones or we would all end our
sessions at 4:00 o'clock in the afternoon to eat dinner!!!
What would These Forums be without the retired and or pensioners to make sure
the young users are looked after in a proper fashion, no what I mean?


I tried to start a thread but I got bumped to cafe'  :(

I think it would be neat if some of us older geezers could discuss PP stuff like assistive technolgies  - ya know.. any new stuff ..etc.. or is all going to be hemmed in with compiz .. etc..

I'll shut-up now.

:)

---

### Post by PaulInBHC on 2011-10-16
We'll have to sneak it in to one of these normal looking threads...

---

### Post by jppr on 2011-10-18
sudo sed -i s'/oneiric/pangolin/g' /etc/apt/sources.list 

That don´t work anymore... I did fresh 11.10 installation and update sources.list but that way don´t work anymore... system is still 11.10 and program sources are pretty messed up :(

---

### Post by arpanaut on 2011-10-18
@jppr  give this fix a shot, [http://ubuntuforums.org/showpost.php?p=11347739&postcount=14](http://ubuntuforums.org/showpost.php?p=11347739&postcount=14)

My sources were a total disaster after running the sudo sed command, but this fixed things up for me.
I don't think it can cause any harm but you may want to back up you sources.list, just in case.
Run update and upgrade after changing the file, hopefully this gets you back on track.

---

### Post by garvinrick4 on 2011-10-18
```
sudo apt-get update; sudo apt-get upgrade
```> sudo sed -i s'/oneiric/pangolin/g' /etc/apt/sources.list I think as stated before me it should be
```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
```Now post 36

And now below
```
sudo aptitude update; sudo aptitude dist-upgrade
```For now anyway.

---

### Post by arpanaut on 2011-10-18
Sorry, I did not look closely enough at the command that jppr ran.
And, yes the dist-upgrade command would be appropriate also.

I had run the correct command, to change reops, yet still had a messed sources.list
I probably did run a dist-upgrade after applying the fix, and forgot that I did.

Thanks for the correction.

---

### Post by jppr on 2011-10-18
Thanks garvinrick4 and arpanaut, that works :) back in business again :)

---

### Post by jerrylamos on 2011-10-18
I don't recommend it, but on this IBM Thinkpad T40 circa 2005:
Upgraded Natty Narwhal to Oneiric Ocelot following Upgrade Manager
- surprise!  It booted O.K.!
Changed all oneiric to precise in /etc/apt/sources.list
sudp apt-get update, sudo apt-get upgrade
- surprise!  It booted O.K.!  Entering this text from it.

Why the surprise?  Oneiric Ocelot USB stick install of release image got an "error" on configuring apt leaving the pc un-bootable with an unrecoverable grub rescue>.  Luckily fixed the multi-boot with guidance from wiki community support on grub.  Yes there's a bug written, I don't expect a fix.

Jerry

p.s. Let the breakage begin....

---

### Post by zika on 2011-10-19
Did I mess something:
```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports restricted main multiverse universe
```It worked, I think, but I am not quite sure about the file above. No time to go through it again, if You see a mistake, I'll be gratefull...
```
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu precise (development branch)
Release:    12.04
Codename:    precise

```Synaptic is acting weerdly, introducing oneiric every time I try to change a repository through it...

---

### Post by williejones on 2011-11-05
> **ventrical said:**
> I use :

First this one:
sudo sed -i s'/oneiric/[COLOR=Red]pangolin/[COLOR=Black]g[/COLOR][/COLOR]' /etc/apt/sources.list

Then this one:
sudo apt-get update && sudo apt-get dist-upgrade

Don't forget:


sudo apt-get update
sudo apt-get upgrade



  :)

This is post number 3 in this thread.

Could we get a mod to change **pangolin** to **precise** before someone messes up their source list?

Thanks

---

### Post by Starks on 2011-11-06
I've always thought that "precise" was too generic compared to previous repo codenames.

---

### Post by sgage on 2011-11-06
> **philinux said:**
> My girlfriend asked me to delete a few messages on her phone. I was jabbing the screen like a twit and nothing happening. Old phone no touch screen lol.

I was working on a client's computer and while waiting for some task or other to complete, I was reading something in a (print) magazine, and tried to turn the page with the mouse! :KS

---

