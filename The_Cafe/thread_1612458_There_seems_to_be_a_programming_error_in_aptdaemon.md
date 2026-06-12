---
title: "There seems to be a programming error in aptdaemon"
date: 2010-11-03
forum: The Cafe
---

### Post by mrebanza on 2010-11-03
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry. HELP!

---

### Post by CharlesA on 2010-11-03
Er, what?

Filing a bug report with no information is useless.

---

### Post by Red_Steve on 2010-11-03
??

could you be at least a bit more specific about this bug?

---

### Post by The Thunder Chimp on 2010-11-19
I've got the same problem on my machine. You can't install anything at all. What the first guy wrote is exactly the error message that pops up (except for his HELP).

This is a fresh install, but I accepted the installation of updates during the installation.

---

### Post by slixz85 on 2010-11-21
damn my laptop does the same thing trying to install wifi for meerkat. i am running lucid on the same machine just been using it. the meerkat was a fresh install for me too. all of us with this problem wtf. in response to last post it doesnt matter i installed mine without the updates from net

---

### Post by slixz85 on 2010-11-21
[http://ubuntuforums.org/showthread.php?t=1610154](http://ubuntuforums.org/showthread.php?t=1610154)

hopefully this works for you all too. fixed

---

### Post by CharlesA on 2010-11-23
> **slixz85 said:**
> [http://ubuntuforums.org/showthread.php?t=1610154](http://ubuntuforums.org/showthread.php?t=1610154)

hopefully this works for you all too. fixed
So the only way to get around the problem is to install from source?

Has anyone filed a bug report on it with some details on what packages are causing the problem?

---

### Post by cariboo on 2010-11-23
There already is a bug filed for the problem, have a look at bug# [lpbug]665218[/lpbug]

---

### Post by slixz85 on 2010-11-23
yeah i've googled alot and that is only solution i found seems they aint in no hurry to fix such a bad problem especially for the number of new users that just use gui

---

### Post by dustrho on 2010-12-10
I'm unable to install the synergy-plus-1.3.4-Linux-i686.deb file on my computer running Ubuntu 10.10, as it's giving me the same aptdaemon error message. I'm not familiar with installing by source code or with the TAR files, so this is a big problem for me. Has there been any resolution to this mess? Guess I'll have to put 10.04 back on my computer and hope it's back to working order.

:(

---

### Post by cariboo on 2010-12-10
If you check the bug report I linked to there is a work-around in the last post., If you manually install the package in a terminal using the following command:

```
sudo dpkg -i synergy-plus-1.3.4-Linux-i686.deb
```

You won't have to spend a couple of hours doing a re-install and setting up your desktop again.

---

### Post by dustrho on 2010-12-10
Cariboo, I tried your suggestion and received an error...

```
me@here:~/Desktop$ sudo dpkg -i synergy-plus-1.3.4-Linux-i686.deb
[sudo] password for me: 
(Reading database ... 134891 files and directories currently installed.)
Unpacking synergy-plus (from synergy-plus-1.3.4-Linux-i686.deb) ...
dpkg: error processing synergy-plus-1.3.4-Linux-i686.deb (--install):
 trying to overwrite '/usr/bin/synergyc', which is also in package synergy 1.3.1-6ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 synergy-plus-1.3.4-Linux-i686.deb

```

Any ideas on what's going on with that mess?

---

### Post by Sixdown on 2010-12-10
I am also getting these error messages.  I cannot install without the aptdaemon errors, and I also cant install manually without errors.

```
me@Q430:~$ sudo dpkg -i ath9k_htc-installer_1-0_all.deb
[sudo] password for thierry: 
(Reading database ... 142074 files and directories currently installed.)
Unpacking ath9k-htc-installer (from ath9k_htc-installer_1-0_all.deb) ...
dpkg: error processing ath9k_htc-installer_1-0_all.deb (--install):
 trying to overwrite '/lib/firmware/ar9271.fw', which is also in package linux-firmware 1.38
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
**Errors were encountered while processing:**
 ath9k_htc-installer_1-0_all.deb
thierry@Q430:~$ 

```

---

### Post by cariboo on 2010-12-10
> **dustrho said:**
> Cariboo, I tried your suggestion and received an error...

```
me@here:~/Desktop$ sudo dpkg -i synergy-plus-1.3.4-Linux-i686.deb
[sudo] password for me: 
(Reading database ... 134891 files and directories currently installed.)
Unpacking synergy-plus (from synergy-plus-1.3.4-Linux-i686.deb) ...
dpkg: error processing synergy-plus-1.3.4-Linux-i686.deb (--install):
 trying to overwrite '/usr/bin/synergyc', which is also in package synergy 1.3.1-6ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 synergy-plus-1.3.4-Linux-i686.deb

```

Any ideas on what's going on with that mess?

i would suggest you purge the version of synergy you already have installed:

```
sudo apt-get purge synergy
```

the try install the newer synergy package.

@Sixdown, try purging the previous driver befroe installing the new one.

---

### Post by 2sondad on 2010-12-12
Use Synaptic Package Manager to search for broken packages.  Then use it to fix/upgrade the packages.  After I did that, the error disappeared.  It seemed there was a broken package that was missing required files and somehow affected aptdaemon.

---

### Post by Peanuts123 on 2010-12-18
I have been using Ubuntu for a week now and I am starting to get the hang of things here. I had this same problem so I restarted the computer and see if the problem was still occurring. It was so I went to my updates. you have to hit check before trying to install them or it will not allow you to do it. After hitting check then click the install button. After installation it will say something like firefox needs to restart. Click okay and it should close that dialog box. Near the top right box of the current screen there will be a restart button. Click it and once it restarts you should be good to go. (It seems that I was missing updates)

---

### Post by soad6 on 2011-01-08
ok this issue is still present and trust me no simple fixes so far... also 
seems that its not just apt-daemon that is borked!! seems dpkg is borked also... when running the dpkg command as stated above after do sudo apt-get purge pidgin-facebookchat it still shows error has occurred. when sudo apt-get purge is ran it says facebookchat plugin isnt installed does this with other programs too. I'm to believe that this is another issue similar to the one before when they accidently pushed a natty package update into meerkat which screwed up the acpi and rendered wifi and graphics useless.

++ IF I WANTED ISSUES EVERYDAY OF MY LIFE I WOULD'VE JUST STUCK WITH WINDOWS!! ++

---

### Post by soad6 on 2011-01-08
Sorry was just pointing out that this issue is a big issue and if the linux community isnt goin to fix it then id be better of not using linux til its fixed... also its not just apt-daemon thats borked, theres alot of issues with 10.10 from kernel update 2.6.35-24 to pidgin 2.7.9 not working anymore, to libglitz-1 gone and cant be reinstalled, to gnome-power-manager not working with hibernate and sleep not working right, also totem/VLC/Mplayer all movie players wont auto close so sleep can be invoked automatically after a movie, and now the fact that I can't install anything cuz the whole system is borked... and the only suggestions ive gotten is to do a fresh install, well this is a fresh install, and i can't run 10.04 cuz it has ACPI issues with my toshiba satellite a505-s6033... so from what I can see is that 10.04 was a joke and 10.10 is junk! what happened to the stability I was so used to back in Gusty and Karmic... Wish I could run either of those but thats right those have ACPI issues also with my system so no point there.... Guess its back to some horrible third rate company named Windows... 

++ BTW it'd be nice of your staff to check stuff before they push it along for updates cuz this isnt the first time ive had broken packages ++

---

### Post by soad6 on 2011-01-08
Ok so seems i figured my own little work around this issue... turns out apt-daemon may or may not be totally borked... not sure why, but my issue was to go and uninstall pidgin and pidgin ppa then do sudo apt-get update
it told me that i had a no_pubkey error...which i then responded with the correct key to remove the error then did sudo apt-get update again and installed empathy to replace pidgin for now. As of now no issues yet... hope nothing else goes wrong. Can't wait til 11.04 comes out and it better work smoothly!

---

### Post by koenn on 2011-01-08
> **soad6 said:**
> 
++ IF I WANTED ISSUES EVERYDAY OF MY LIFE I WOULD'VE JUST STUCK WITH WINDOWS!! ++

Excellent use of CONSTRUCTIVE CAPS. 
I'm  sure the problem will get fixed soon, now.

---

### Post by ckryger on 2011-03-26
I was installing an application when I stumbled upon the "There seems to be a programming error in aptdaemon" error msg. Fairly new to Ubuntu I googled and found this thread which didn't help me out immediately. 
However, after trying a few things out, I found out that there was something wrong with my par2 installation. How? I issued this command  
```
sudo apt-get install
```

and got back this answer
```
The following extra packages will be installed:
  par2
The following packages will be upgraded:
  par2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/98.3kB of archives.
After this operation, 266kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

Hopefully I pressed y, new sources was downloaded and installed and I got rid of the aptdaemon problem.

I hope this helps out some newbies like my self out there :)

Cheers.

---

### Post by Sammiye on 2011-03-31
bumping this up a bit,

Just done a whole load of searching and it seems im having similar troubles to ALOT of people. tried downloading and installing Opera and Skype using the gui software centre and dpkg on terminal. Neither works for these programs. i have done the 'sudo apt-get clean' sudo apt-get update and sudo apt-get install stages and whilst things happened, it hasnt solved the problem for me. but when i tried installing a simple game from software centre - one that was already a choice- it worked fine.

Fairly new to linux, i had 7.10 before windows 7 came out and got on fine with that. seems like there's a big issue here with 10.10.

Anyone got any idea how to solve this one??? reeeally could do with the help!!

cheers!

---

### Post by Sammiye on 2011-04-01
bump!! please sont make me go back to windows 7!! :D

---

### Post by koenn on 2011-04-01
> **Sammiye said:**
> bump!! please sont make me go back to windows 7!! :D
open a thread in a support forum. 
this forum here is "for lighthearted and enjoyable discussions, like you might find around a water cooler at work."


Or just go back to windows 7.

---

### Post by Sammiye on 2011-04-01
i have bumped up a couple of threads in beginner talk and general help.

simply asking here too as this seems to have most replies. 

cheers for the help :(

---

### Post by dbcomics on 2011-05-11
On my system (quite a fresh Narwhal installation) it seems to have been caused by a crash in the middle of a previous install.The 

> sudo apt-get install

trick mentioned above fixed it nicely for me.

---

### Post by aeathb on 2011-08-22
This is my first post and I've solved a lot of problems on this forum but none have been this annoying with a positive end result. apt-get install seemed to fix it. I don't understand why but I'm pleased with the result. Thanks!

---

