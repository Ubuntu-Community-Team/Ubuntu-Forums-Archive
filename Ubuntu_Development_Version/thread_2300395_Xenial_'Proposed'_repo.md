---
title: "Xenial 'Proposed' repo"
date: 2015-10-25
forum: Ubuntu Development Version
---

### Post by sgage on 2015-10-25
I updated a fresh Ubuntu Gnome installation to Xenial, and all seems fine. I activated the 'proposed' repo, and see that there is a whopping load of packages there - haven't pulled the trigger on an upgrade yet. How many folks are running Xenial with 'proposed' packages? Anyone running it that way with Gnome? How's it working?...

---

### Post by jimmy-frydkaer on 2015-10-25
I'm not running GNOME but Unity and have full load on all repos (just renamed entries in /etc/apt/sources.list (as I usually do)) and I got no errors on updates or on upgrades -...

I'm asking for it, I know. Well let's chew that food when we get there. So far it's smooth riding.

---

### Post by fjgaude on 2015-10-25
> **jimmy-frydkaer said:**
> I'm not running GNOME but Unity and have full load on all repos (just renamed entries in /etc/apt/sources.list (as I usually do)) and I got no errors on updates or on upgrades -...

I'm asking for it, I know. Well let's chew that food when we get there. So far it's smooth riding.

I did the same without issues of any kind, on Intel graphics. Updates and upgrades all came through fine. Keeping fingers crossed.

---

### Post by VinDSL on 2015-10-25
> **sgage said:**
> How many folks are running Xenial with 'proposed' packages? Anyone running it that way with Gnome? How's it working?...

Aye !  Working fine...

---

### Post by sgage on 2015-10-25
Hello All,

Guess I'll go for it. It's not like reinstalling an Ubuntu is any big deal any more  :KS

[I did it - so far, so good...]

---

### Post by rrnbtter on 2015-10-25
Greetings,
I've been testing with proposed enabled for years now. Wouldn't have it any other way. I am running upgraded Wily to Xenial. So I still have all of the inherited breakage from Wily plus whatever breakage Xenial has to offer. Reinstall for me runs about two hours including software and I keep var/cache/apt/archives backed up to conserve bandwidth. When I hit a snag like the Network Manager problem in Wily I just manual install around the problem piecemeal style. And PS I have a Puppy Linux Boot Folder on my partition for support if I need it. Just good clean fun! So! come on into the deep water and play. No sharks around here! ............I hope!

---

### Post by sgage on 2015-10-25
> **rrnbtter said:**
> Greetings,
I've been testing with proposed enabled for years now. Wouldn't have it any other way. I am running upgraded Wily to Xenial. So I still have all of the inherited breakage from Wily plus whatever breakage Xenial has to offer. Reinstall for me runs about two hours including software and I keep var/cache/apt/archives backed up to conserve bandwidth. When I hit a snag like the Network Manager problem in Wily I just manual install around the problem piecemeal style. And PS I have a Puppy Linux Boot Folder on my partition for support if I need it. Just good clean fun! So! come on into the deep water and play. No sharks around here! ............I hope!

I have been doing this for many years myself, but I was a little shy about enabling proposed so early in the cycle. However, I've done it, and it's working fine. I stay regularly backed-up, and reinstalling is nothing to me, really. I have a nice installation of Wily for my daily driver - Xenial is on a test partition. 

Thanks for the encouragement. Not worried so much about sharks - I am more concerned about packs of rabid xeri :KS

---

### Post by sammiev on 2015-10-25
> **sgage said:**
> Hello All,

Guess I'll go for it. It's not like reinstalling an Ubuntu is any big deal any more  :KS

[I did it - so far, so good...]

I'm in, I will take the proposed.

Running gnome here.

Update:

173 upgraded and 2 new...

---

### Post by ventrical on 2015-10-26
> **sgage said:**
> I have been doing this for many years myself, but I was a little shy about enabling proposed so early in the cycle. However, I've done it, and it's working fine. I stay regularly backed-up, and reinstalling is nothing to me, really. I have a nice installation of Wily for my daily driver - Xenial is on a test partition. 

Thanks for the encouragement. Not worried so much about sharks - I am more concerned about packs of rabid xeri :KS

echo that. proposed not  misbehaving currently but I assume it will start probably sooner than later. I have one install with proposed enabled and one disabled -ubuntu-desktop and xubuntu-desktop.

---

### Post by zika on 2015-10-26
Proposed is always on... ;)
```
:~$ sudo apt-get dist-upgrade Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  fonts-guru fonts-guru-extra fonts-lohit-guru gnupg-agent libpth20 python3-cffi python3-ply python3-pycparser
Use 'apt-get autoremove' to remove them.
Done
The following packages will be REMOVED:
  compiz compiz-gnome gnome-applets gnome-panel gnome-session-flashback indicator-datetime libcamel-1.2-52 libebook-contacts-1.2-1 libecal-1.2-18 libedata-cal-1.2-27 libedataserver-1.2-20 libmetacity-private3 metacity ubuntu-desktop
  unity unity-control-center unity-control-center-signon unity-tweak-tool webaccounts-extension-common xul-ext-webaccounts
The following NEW packages will be installed:
  libcamel-1.2-54 libebook-contacts-1.2-2 libecal-1.2-19 libedata-cal-1.2-28 libedataserver-1.2-21
The following packages will be upgraded:
  evolution evolution-common evolution-data-server evolution-data-server-common evolution-data-server-online-accounts evolution-plugins folks-common gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gnome-contacts
  gnome-shell gnome-shell-common libebackend-1.2-10 libebook-1.2-16 libedata-book-1.2-25 libedataserverui-1.2-1 libevolution libfolks-eds25 libfolks-telepathy25 libfolks25 metacity-common
22 upgraded, 5 newly installed, 20 to remove and 0 not upgraded.
Need to get 17,5 MB of archives.
After this operation, 23,9 MB of additional disk space will be used.
Do you want to continue? [Y/n]
``````
:~$ sudo aptitude full-upgrade The following NEW packages will be installed:
  libcamel-1.2-54{ab} libebook-contacts-1.2-2{a} libecal-1.2-19{ab} libedata-cal-1.2-28{a} libedataserver-1.2-21{ab} libmetacity-private3a{ab} 
The following packages will be REMOVED:
  libebook-contacts-1.2-1{u} libedata-cal-1.2-27{u} python3-cffi{u} python3-ply{u} python3-pycparser{u} 
The following packages will be upgraded:
  evolution evolution-common evolution-data-server evolution-data-server-common evolution-data-server-online-accounts evolution-plugins folks-common gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gnome-contacts 
  gnome-shell gnome-shell-common libebackend-1.2-10 libebook-1.2-16 libedata-book-1.2-25 libedataserverui-1.2-1 libevolution libfolks-eds25 libfolks-telepathy25 libfolks25 metacity metacity-common mtr-tiny{b} 
24 packages upgraded, 6 newly installed, 5 to remove and 0 not upgraded.
Need to get 17,8 MB of archives. After unpacking 47,0 MB will be used.
The following packages have unmet dependencies:
 libmetacity-private3a : Breaks: libmetacity-private3 (< 1:3.18) but 1:3.17.2-4ubuntu1 is installed.
 libcamel-1.2-54 : Conflicts: libcamel-1.2-52 but 3.16.5-1ubuntu3 is installed.
 mtr-tiny : Depends: libncurses5 (>= 6) but 5.9+20150516-2ubuntu1 is installed.
            Depends: libtinfo5 (>= 6) but 5.9+20150516-2ubuntu1 is installed.
 libecal-1.2-19 : Conflicts: libecal-1.2-18 but 3.16.5-1ubuntu3 is installed.
 libmetacity-private3 : Depends: metacity-common (= 1:3.17.2-4ubuntu1) but 1:3.18.1-1ubuntu1 is to be installed.
 libedataserver-1.2-21 : Conflicts: libedataserver-1.2-20 but 3.16.5-1ubuntu3 is installed.
The following actions will resolve these dependencies:


      Remove the following packages:                                                          
1)      compiz                                                                                
2)      compiz-gnome                                                                          
3)      gnome-applets                                                                         
4)      gnome-panel                                                                           
5)      gnome-session-flashback                                                               
6)      indicator-datetime                                                                    
7)      libcamel-1.2-52                                                                       
8)      libecal-1.2-18                                                                        
9)      libedataserver-1.2-20                                                                 
10)     libmetacity-private3                                                                  
11)     mtr-tiny                                                                              
12)     ubuntu-desktop                                                                        
13)     unity                                                                                 
14)     unity-control-center                                                                  
15)     unity-control-center-signon                                                           
16)     unity-tweak-tool                                                                      
17)     webaccounts-extension-common                                                          
18)     xul-ext-webaccounts                                                                   


      Leave the following dependencies unresolved:                                            
19)     indicator-session recommends unity-control-center-signon | gnome-control-center-signon
20)     libaccount-plugin-1.0-0 recommends unity-control-center-signon                        
21)     ubuntu-standard recommends mtr-tiny                                                   
22)     unity-greeter recommends indicator-datetime                                           
23)     gnome-panel recommends unity-control-center                                           
24)     gnome-panel-data recommends gnome-panel                                               
25)     indicator-applet-complete recommends indicator-datetime                               




Accept this solution? [Y/n/q/?]
```This has nothing to do with proposed but it is on-topic with Gnome... ;) It has been like that days before Xenial showed its face... ;)

---

### Post by Chanath on 2015-10-26
What should I write instead of wily in sources.list, proposed or devel or xenial?

---

### Post by QDR06VV9 on 2015-10-26
For me instead of Wily I changed to Xenial.

---

### Post by ventrical on 2015-10-26
Look here at original.

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

---

### Post by grahammechanical on 2015-10-26
I am glad that some of us are running with proposed enabled. When you start screaming, I will know what to avoid. :)

---

### Post by Chanath on 2015-10-26
> **ventrical said:**
> Look here at original.

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

Thanks. I knew that, but was thinking, if there was a repo called proposed. 
Thanks anyway!

---

### Post by QDR06VV9 on 2015-10-26
There is a repo called proposed but it has to be enabled.

---

### Post by rrnbtter on 2015-10-26
Greetings,

> **grahammechanical said:**
> I am glad that some of us are running with proposed enabled. When you start screaming, I will know what to avoid. :)

Think of it as a learning experience. The spirit of this section of the forum. But the dev has been better at holding back broken packages. No absolutes intended here but it's better than it used to be. 
The screaming is merely the breaking of the shell of ones understanding.

---

### Post by RockDoctor on 2015-10-26
Decided to enable xenial-proposed. What could possibly go wrong? :lolflag:

---

### Post by harry332 on 2015-10-27
Nothing if you can chroot, and reinstall the working versions of broken packages.

---

### Post by rrnbtter on 2015-11-03
Greetings,
Currently running Wily upgraded to Xenial
 with the 4.3 Kernel

I currently have Proposed disabled due to Desktop display failure due to mir display server installing from proposed and "not ready for prime time".

It is possible to piece meal the proposed updates and leave out the display libs but with 200M sitting there that would be time consuming. Hence, no 
proposed right now for me. 


If you have a failed desktop as a result of having proposed enabled. Just remember. It's a learning experience!

---

### Post by RockDoctor on 2015-11-03
So far, so good. However, I'm pretty sure that pesky law enforcer, Murphy, is lurking nearby.

---

### Post by jerrylamos on 2015-11-06
I use Synaptic.  You may have to do :
sudo apt-get install synaptic 
Select Other Software, turn on "Canonical Partners"
Select Updates, turn off Unsupported updates  I have absolutely no idea why "unsupported updates" is the default Ubuntu setting??
Personal preference, I set Automatically Check for Updates to "Never".  I update usually daily on development release like Xenial when I want to, I do not like Automatic Update crashing in on whatever I'm doing, and Automatic Update "Partial Updates" have screwed me many times.  I don't do those, I just do:
sudo apt-get update
sudo apt-get dist-upgrade
works fine for me.  Of course, in pre-release software like Xenial expect crashes...then do ubuntu-bug etc. to report problems to Launchpad.  
If you don't want crashes then stay on released Ubuntu's which is Wily or Trusty.LTS

---

### Post by rrnbtter on 2015-11-06
Greetings,
I was kind of gung-ho a couple of week ago about running "Proposed" enabled. But what I have right now is so good I think I will coast with it for a bit. Actually, the best I have ever had, and on five year old equipment no less!

---

### Post by fjgaude on 2015-11-06
> **rrnbtter said:**
> Greetings,
I was kind of gung-ho a couple of week ago about running "Proposed" enabled. But what I have right now is so good I think I will coast with it for a bit. Actually, the best I have ever had, and on five year old equipment no less!

My new box runs on 16.04 better than 14.04.4 even with Kernel 4.2. So... let the good times roll!

---

### Post by ventrical on 2015-11-07
> **rrnbtter said:**
> Greetings,
I was kind of gung-ho a couple of week ago about running "Proposed" enabled. But what I have right now is so good I think I will coast with it for a bit. Actually, the best I have ever had, and on five year old equipment no less!

I have one ubuntu-desktop system with proposed enabled and no problems so far but I would expect that somewhere down the road, unless we are familiar with the workings of some of the depends, that it will break.

regards..

---

