---
title: "HOWTO: Install F-Prot with GTK frontend (anti-virus)"
date: 2005-11-10
forum: Tutorials
---

### Post by Perfect Storm on 2005-11-10
**Also works for Ubuntu 5.10, 6.06, 6.10 and 7.04**
**Does _NOT_ work on 64bit version of Ubuntu**
**[size=4][color=red]This how do not work in 7.10**[/size][/color]



Q: **Is viruses, trojans and malware a threat to a linux system as in Windows?**

A: *No, there's a very few viruses to linux and the way a Linux/unix is build up makes it difficult to do any serious damage to the system, in fact I've never heard from people who got their Linux/unix system infected.*

Q: **So why install a anti-virus application/program?**

A: *For an ordinary Linux Home user with only one OS system their's no need for Anti-virus, but people who's running network, server or dual booting with win OS this tool can be very handy to scan and delete viruses.*

Q: **I'm a home user only running Linux do I need it?**

A: *No, a firewall is way better as protection in that case.*



========================================================

**_Before Installation:_**
Make sure that your sourcelist is set up correctly before advancing further into this howto. If you're in doubt how to do that make some search on the forum.


First thing you need is to get the right tools for compiling and the right libs to make F-Prot with GTK frontend to work.
```

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential libwww-perl libgtk2.0-dev checkinstall

``` 




**_Installation:_**

Grab F-prot [here]("http://www.f-prot.com/products/home_use/linux/")  and pick the debian/gnu file. (4.6.8 ) and save it to your Desktop
Download XFPROT-1.20 [here]("http://web.tiscali.it/sharp/xfprot/") and save it to your Desktop. 

First the fp-linux-ws.deb need to be installed:
```

cd ~/Desktop
sudo dpkg -i  fp-linux-ws.deb 

``` 

Next the frontend for F-prot
```

cd ~/Desktop
tar zxvf xfprot-1.20.tar.gz
cd xfprot-1.20
./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
make
sudo checkinstall

``` 




**_Launcher:_**

Now we need to add it to 'Application launcher:
```

sudo nano /usr/share/applications/fprot.desktop

``` 

add:
```

[Desktop Entry]
Name=F-Prot
Comment=Anti-Virus Application
Exec=xfprot
Icon=/usr/local/xfprot/icons/antivirus-48x48.png
Terminal=false
Type=Application
Categories=Application;System;
```

Save and exit.


--------------------------------------------------------
**Troubleshooting**

- While configuring xfprot and it's complaining about it can't find libgtk2, open the configure file with a text editor application and change the first line to **#!/bin/bash**

---

### Post by ubuntu27 on 2005-11-29
I think it is better if you explain what and why we have to do that [following your instructions]
I mean, all you did was explain that we don't need Anti-virus in Linux [Which is true], and then you said &#8220;First thing you need to run this in the terminal&#8221;
What for? What will happened if I do that?  [Well, looks like you are showing how to install Anvirus for those who want or have a network server... but, one will not know if they are new to Linux]

I am not criticizing, by the way. :) I am just commenting. Trying to help you make a understandable &#8220;How-To&#8221; for beginners ;) hehe. 

PS: Good job

EDIT: Ah! I see that the title says " HOWTO: Install F-Prot with GTK frontend (anti-virus)" now that makes sense... haha..

---

### Post by veloct on 2005-11-29
works flawlessly, good work. thanks

---

### Post by Resin on 2005-11-29
Thanks buddy, works a treat!

---

### Post by Perfect Storm on 2005-12-18
Updated Howto. New F-prot availble (4.6.3)

---

### Post by 5-HT on 2005-12-19
***EDIT:** figured out the problem was with a symbolic link to the f-prot shell script and condensed/focused the post accordingly

Hi, wondering if someone may be able to help me out with something funny that occured after updating to the new version of f-prot?


It seems that the installation creates the directory: /usr/local/bin, and places a link there to /usr/local/f-prot/f-prot.sh.

For whatever reason, the /usr/local/bin directory that f-prot created  only has read/write/execute permissions for root (700 permissions), other users/group have absolutely no access to the directory at all.

Because of this, I cannot run f-prot as a normal user (which wasn't the case with the previous version).

Now, I'm still really new to linux and am just wondering if it's ok to give everyone read/execute permissions to /usr/local/bin (755 permission)?


It looks like /usr/bin has these permissions already, so I don't think this should be a problem from a security standpoint...but am not sure.


So I'm just wondering if any has a /usr/local/bin directory, and if so does it give read/execute permissions to anyone?

Would it be okay for me to give such permissions to the directory, or should I just put a symbolic link pointing to /usr/local/f-prot/f-prot.sh in /usr/bin?


Any suggestions/info would be greatly appreciated!

---

### Post by ArmadaEnder on 2005-12-20
Ok, I'm having a problemwhen trying to install this. Everything works fine until I hit the: 

sudo checkinstall
sudo dpkg -i xfprot-1.15_1.15-1_i386.deb

...portion of the tutorial. When entering the above, this occurs:

[I]chris@ubuntu:~/Desktop/xfprot-1.15$ sudo checkinstall
sudo: checkinstall: command not found
chris@ubuntu:~/Desktop/xfprot-1.15$ sudo dpkg -i xfprot-1.15_1.15-1_i386.deb
dpkg: error processing xfprot-1.15_1.15-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xfprot-1.15_1.15-1_i386.deb
chris@ubuntu:~/Desktop/xfprot-1.15$[/I]

I got the icon to appear in the applications tab yet if I try to open it, an error box pops up with this message:

[I]Cannot launch entry
Details: Failed to execute child process "xfprot" (No such file or directory)[/I]

Any ideas as to what may have happend?

---

### Post by veloct on 2005-12-20
looks like you don't have checkinstall installed in your system.

> sudo apt-get install checkinstall

Then try again.

---

### Post by ArmadaEnder on 2005-12-20
Ah, now I feel stupid. Thank-you very much for the help.

---

### Post by Perfect Storm on 2005-12-20
Perhaps I should include the checkinstall application in the howto.


Edit: Done.

---

### Post by Perfect Storm on 2006-01-04
Updated: New F-prot is availble

---

### Post by jaywatkins on 2006-01-10
HI,

Works great until I get to the make part.   I cannot run "make" on anything!  Where is this command located, or how could I get it?

Thanks

---

### Post by arnieboy on 2006-01-10
dont want to hijack this thread but since AI has written this howto on F-prot antivirus, he might be interested to know that AVG has recently released its free intended-for-home-use version of antivirus for linux.
It is currently released in the form of rpm binaries for Redhat, mandriva and Suse.
We might want a Ubuntu deb version or simply do an alien on the rpm to see whether the deb works or not.
the following is the link for the same:
[http://free.grisoft.com/doc/21/lng/us/tpl/v5](http://free.grisoft.com/doc/21/lng/us/tpl/v5)

For the uninitiated AVG is a commercial grade antivirus of the caliber of Norton and McAfee

---

### Post by Perfect Storm on 2006-01-10
[QUOTE=jaywatkins]HI,

Works great until I get to the make part.   I cannot run "make" on anything!  Where is this command located, or how could I get it?

Thanks[/QUOTE]

I'm not quiet sure what you mean :confused: 
You open the terminal. Make sure to **cd** the right place ( /bla/bla/bla/xfprot-1.15 ), then write make in the terminal.


@Arnieboy
Thanks I'll take a look at it.

---

### Post by 5-HT on 2006-01-13
[QUOTE=arnieboy]dont want to hijack this thread but since AI has written this howto on F-prot antivirus, he might be interested to know that AVG has recently released its free intended-for-home-use version of antivirus for linux...[/QUOTE]

Thanks for the info, didn't know about that.

---

### Post by Perfect Storm on 2006-01-14
Updated: F-prot v4.6.5 is now availble.

---

### Post by Micro Rotors on 2006-01-24
I cannot get the make file to work either, I know the makefile is there I see it in the folder,,,,,,,,, Oh I am using Gnome does this matter> anyhow this is what I get:

[PHP]bill@micro:~$ cd apps/av
bill@micro:~/apps/av$ tar zxvf xfprot-1.15.tar.gz
xfprot-1.15/
xfprot-1.15/i18n/
xfprot-1.15/i18n/pl_PL.h
xfprot-1.15/i18n/README
xfprot-1.15/i18n/es_ES.h
xfprot-1.15/i18n/en_GB.h
xfprot-1.15/i18n/fr_FR.h
xfprot-1.15/i18n/pt_BR.h
xfprot-1.15/i18n/it_IT.h
xfprot-1.15/i18n/de_DE.h
xfprot-1.15/icons/
xfprot-1.15/icons/antivirus-128x128.png
xfprot-1.15/icons/README
xfprot-1.15/icons/antivirus-48x48.png
xfprot-1.15/icons/antivirus-32x32.png
xfprot-1.15/icons/antivirus-64x64.png
xfprot-1.15/TextCommon.c
xfprot-1.15/README
xfprot-1.15/mygtk.h
xfprot-1.15/COPYING
xfprot-1.15/xfprot.h
xfprot-1.15/TextViewWindow.c
xfprot-1.15/Makefile
xfprot-1.15/eicar.com.txt
xfprot-1.15/configure
xfprot-1.15/TextEditWindow.c
xfprot-1.15/xfprot-gtk.c
xfprot-1.15/AboutWindow.c
xfprot-1.15/mylib.c
xfprot-1.15/mygtk.c
xfprot-1.15/xfprot_fedora.spec
xfprot-1.15/mylib.h
xfprot-1.15/FileSelector.c
xfprot-1.15/DialogWindow.c
xfprot-1.15/Changelog
bill@micro:~/apps/av$ cd xfprot-1.15
bill@micro:~/apps/av/xfprot-1.15$ ./configure --with-gtk2 --with-sudo --autodetect --without-debug
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....Not found
Checking for xterm.....OK
Using Gtk+ 2.8.6 libs
Adding optimization statements to Makefile.in
Setting language to en_GB, you can override this with: --with-lang=xx_XX
Supported languages are:
de_DE
en_GB
es_ES
fr_FR
it_IT
pl_PL
pt_BR
bill@micro:~/apps/av/xfprot-1.15$ make
bash: make: command not found
bill@micro:~/apps/av/xfprot-1.15$
[/PHP]

---

### Post by hen3rz on 2006-01-26
Hello,

Followed the instructions to the bone and It works great! Thank you very much!

---

### Post by Perfect Storm on 2006-01-29
Updated the howto to take care of some people have problem to compile the file.

---

### Post by ~Speed on 2006-02-02
[QUOTE=Artificial Intelligence]Updated the howto to take care of some people have problem to compile the file.[/QUOTE]

AI, tnx for your time!
:)

It works like charm\\:D/ , but as someone already said up there in this thread, what exactly did we do by this copy/paste drill?

Please, dont get me wrong, I would just like to understand what is involved in here.
<kind smile>

For sure, I am a newbie, you can probably tell.
:)

Anyway, thank you again!
:)

---

### Post by Perfect Storm on 2006-02-02
The most cut'n'paste is part of compiling XF-prot because there's no .deb package for it (ubuntu is based on debian).

A quick easy explaination:

sudo apt-get update <=== updates the sourcelist
sudo apt-get upgrade <=== upgrades/updates if there are new packages availble for already installed packages.
sudo apt-get install build-essential <=== Installs applications and libs which is important for compiling stuff.
sudo apt-get install libwww-perl <=== Installs libwww-perl which xf-prot needs to work.
sudo apt-get install libgtk2.0-dev <=== Installs libgtk2.0-dev which xf-prot needs to compile (gui interface).
sudo apt-get install checkinstall <=== an application that allow you to make it easy to install/uninstall[/code]


cd /where/you/saved/the/files/  <=== move to the right directory via terminal
sudo dpkg -i  fp-linux-ws.deb  <=== installs fp-linux-ws.deb package


cd /where/you/saved/the/files/ <=== move to the right directory via terminal
tar zxvf xfprot-1.15.tar.gz <=== extracting xf-prot (the source)
cd xfprot-1.15 <=== move you to the directory xfprot-1.15 
./configure --with-gtk2 --with-sudo --autodetect --without-debug --with-install-dir=/usr <=== checking if all the libs its needed, what kind of system you have etc. etc. plus telling what it should add or not add from the default.
make <=== puts the application together
sudo checkinstall <=== make a .deb package
sudo dpkg -i xfprot-1.15_1.15-1_i386.deb <=== install the .deb package

---

### Post by ~Speed on 2006-02-02
AI,
thank you very much. 
:)

I ran a ful scan right after install, it detected 4 "infected" files...
...test infection, I guess.

I am not on linux right now, I dont remember the names...

---

### Post by Perfect Storm on 2006-02-03
Eicar is the name of the test file.

---

### Post by mgsfan on 2006-02-06
erm for some reason my xfprot did'nt install under usr/local..it installed in /usr any reason why it would do that and if thats a problem?

---

### Post by tlaloczint on 2006-02-08
well i`m stuck for now can someone help me please
I follow every step till the make comand andthis is what I get.
thaks

tlaloc@aztlan:~/xfprot-1.15$ make
cc -DIS_LINUX -DNDEBUG -Os -pipe -fomit-frame-pointer  -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o xfprot-gtk.o xfprot-gtk.c
make: cc: Command not found
make: *** [xfprot-gtk.o] Error 127

---

### Post by r4ik on 2006-02-11
Works perfect thanks.

---

### Post by Kaobear on 2006-02-11
Worked like a charm, thanks for the how-to

---

### Post by Perfect Storm on 2006-02-12
New version of F-prot (4.6.6) is avaible.

---

### Post by Socratez on 2006-02-22
========================= Installation results ===========================
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.

Copying documentation directory...
/var/tmp/DYTiUqCHlNCBAUTneTPG/installscript.sh: line 13: 19136 Segmentation fault      mkdir -p "/usr/share/doc/xfprot-1.15"

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


This is my error and I have no clue why it is acting a fool ... I am using Dapper ...

---

### Post by Perfect Storm on 2006-02-22
This haven't been tested on Dapper yet. Since Dapper is under heavy development many things can break from one day to another. If you're looking something stable you might go back to breezy.

---

### Post by Ocxic on 2006-02-22
It seemed to do everything ok, but it didn't work??

edit: I'm dumb, I typed user instead of usr in the configure command.

---

### Post by evilc on 2006-03-13
I am having a problem installing this, I get to Next the frontend for F-prot Code:

cd /where/you/saved/the/files/ tar zxvf xfprot-1.15.tar.gz cd xfprot-1.15 ./configure --with-gtk2 --with-sudo --autodetect --without-debug --with-install-dir=/usr/local make sudo checkinstall sudo dpkg -i xfprot-1.15_1.15-1_i386.deb

But I am unable to find xf-prot.tar.gz anywhere, the only directory I can find is /usr/local/f-prot which contains ?Program files. Any suggestionsor help.

Thanks

---

### Post by Perfect Storm on 2006-03-13
Please post your teminal output.

---

### Post by evilc on 2006-03-13
[QUOTE=Artificial Intelligence]Please post your teminal output.[/QUOTE]


clive@ubuntu:~$ cd downloads
clive@ubuntu:~/downloads$ sudo dpkg -i  fp-linux-ws.deb
Password:
Selecting previously deselected package fp-linux-ws.
(Reading database ... 70922 files and directories currently installed.)
Unpacking fp-linux-ws (from fp-linux-ws.deb) ...
Setting up fp-linux-ws (4.6.6) ...
***************************************
* F-Prot Antivirus Updater            *
***************************************

There's a new version of:
"Document/Office/Macro viruses" signatures on the web.
Starting to download...
Download completed.

There's a new version of:
"Application/Script viruses and Trojans" signatures on the web.
Starting to download...
Download completed.

Preparing to install Application/Script viruses and Trojans signatures.
Application/Script viruses and Trojans signatures have successfully been installed.

Preparing to install Document/Office/Macro viruses signatures.
Document/Office/Macro viruses signatures have successfully been installed.


**********************************
* Update completed successfully. *
**********************************


clive@ubuntu:~/downloads$

Your next instruction : cd /where/you/saved/the/files/ tar zxvf xfprot-1.15.tar.gz

This is the one I can't find

---

### Post by Perfect Storm on 2006-03-14
*cd /where/you/saved/the/files/* is a browse through folder command, lets say you saved xfprot-1.15.tar.gz on your Desktop:

```
cd Desktop
tar zxvf xfprot-1.15.tar.gz

```

---

### Post by evilc on 2006-03-14
[QUOTE=Artificial Intelligence]*cd /where/you/saved/the/files/* is a browse through folder command, lets say you saved xfprot-1.15.tar.gz on your Desktop:

```
cd Desktop
tar zxvf xfprot-1.15.tar.gz

```[/QUOTE]

Thanks, I lost the plot stored it on 2nd HDhttp://ubuntuforums.org/images/smilies/icon_confused.gif

---

### Post by Perfect Storm on 2006-03-14
Okay, glad that you solve it :)

---

### Post by evilc on 2006-03-14
F-Prot now working a treat just one querie how do I get it to check my incoming mail, I am using Thunderbird and the directory within home is .mozilla-thunderbird.

Thanks again for the help

---

### Post by Perfect Storm on 2006-03-15
I don't know, but I'll make some research and I'll post back when/if I find something useful.

---

### Post by evilc on 2006-03-15
Thanks.

---

### Post by Aussie on 2006-03-18
Hi all,

Good How-To, worked a treat straight off.  Just a quick one, I installed this so I could scan my windows NTFS partition (Which I hardly use now anyway) which is full of viruses and spyware.  

Anyway, when I ran the scan of my "/media/windows/" directory, It scans fine, but whenever it asks me to delete an infected file and I click "y" I get the error "Could not delete the file."  do I have to enable access rights to my windows partition or will that screw everything up with NTFS writing being experimental. If so how do i?

Any help would be appreciated.

Thanks.

---

### Post by int on 2006-03-21
With don't use the f-prot-installer?

> apt-get install f-prot-installer

It say that can install f-prot > 0.4

---

### Post by Perfect Storm on 2006-03-21
Well, I like the other way and it's tested in this howto. Either way if you want the gui you need to compile it nevertheless.

---

### Post by dartmusic on 2006-03-24
Thanks for the how-to...F-Prot is the easiest to get working of the three known options (AVG, F-Prot and ClamAV).  Worked flawlessly.  But I'm wondering how to get it to automatically update the defs and schedule a regular/background scan.  

Yep, I'm still pretty much a noob, so this might be kind of a "duh" question.  Sorry in advance.

Thanks!

---

### Post by Matchless on 2006-04-23
Hi AI,
       I have just installed f-prot on dapper fl6 and it seems to be working, update also works from gui. Bit of a bland gui compared to AVG and a long update.
Regards

---

### Post by Perfect Storm on 2006-04-23
Well f-prot are also my favorite. To bad you can't --enable-qt for KDE users, but you could try contacting the developer of the F-prot gui.

> 
Usage: configure [OPTION]

Options:
  -h, --help                     print this help, then exit
  --with-gtk1                    use Gtk+-1.x libraries
  --with-gtk2                    use Gtk+-2.x libraries
  --autodetect                   autodetect f-prot install directory
  --with-install-dir             prefix for  the path of the install
                                 and binaries directory (default /usr/local)
  --with-su                      use su for f-prot update function (default)
  --with-sudo                    use sudo for f-prot update function
  --with-debug                   enable debug mode
  --without-debug                disable debug mode
  --with-lang=xx_XX              set language (default en_GB)




Edit: by the way how's the KDE dapper version compared to KDE breezy? (In terms of speed and bugs)

---

### Post by LordMerlin on 2006-04-25
Is it possible to install & run fprot (or any other AV for that matter) on a samba server, which doesn't have Gnome installed? The machine doesn't have a monitor, and evertyhing it run and maintainted via SSH. When following this howto, I got this far:

root@Gimbli:/home/samba/software/source/xfprot-1.15# smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 31, in ?
    from DialogHandler import DialogHandler
  File "/usr/lib/smeg/DialogHandler.py", line 30, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
RuntimeError: could not open display


The problem is, I don't have Gnome / KDE / x, thus it won't continue. 

Any suggestions?

---

### Post by Perfect Storm on 2006-04-25
Don't install the gui then. Run F-prot by command.

```
man f-prot
```
for more information.

---

### Post by LordMerlin on 2006-04-26
[quote=Artificial Intelligence]Don't install the gui then. Run F-prot by command.

```
man f-prot
``` for more information.[/quote]

Cool, didn't know I could do that, thanx :)

---

### Post by Perfect Storm on 2006-06-01
Changed the howto to 6.06. Rewritten a part of it. But it still works for ubuntu 5.10

---

### Post by kc2eil on 2006-06-15
I'm quite a newbie to Ubuntu...but have a good understanding of computers.

I followed everything fine & when I click on the fprot icon, i get the following message:

Details: Failed to execute child process "xfprot" (Permission denied)

I may have missed the answer earlier in this thread...

Thanks for all the help... KC2IEL.

---

### Post by 1T-M0nk3y on 2006-06-21
[QUOTE=kc2eil]I'm quite a newbie to Ubuntu...but have a good understanding of computers.

I followed everything fine & when I click on the fprot icon, i get the following message:

Details: Failed to execute child process "xfprot" (Permission denied)

I may have missed the answer earlier in this thread...

Thanks for all the help... KC2IEL.[/QUOTE]

Have you missed off the sudo from the command?

---

### Post by oskvaz on 2006-06-24
I have followed your instructions and works everything perfectly.


Thank you very much!

---

### Post by Lrover on 2006-06-25
Arrgh!! I must be losing it. Dapper 6.06 here with all current updates and I'm getting this:
xmechanic@lancomp1:~$ sudo apt-get install checkinstall
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall

and if I try to do dpkg without checkinstall, I get this:

xmechanic@lancomp1:~/xfprot-1.15$ sudo checkinstall
sudo: checkinstall: command not found
xmechanic@lancomp1:~/xfprot-1.15$ sudo dpkg -i xfprot-1.15_1.15-1_i386.deb
dpkg: error processing xfprot-1.15_1.15-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xfprot-1.15_1.15-1_i386.deb


What a pain!! ](*,)

Edit: I'm not going to worry about the front-end too much since f-prot is actually working and Kontact picked up on it right away. I am curious about why checkinstall seems to be unavailable...

---

### Post by Perfect Storm on 2006-06-25
and you did enable all the stuff in your sourcelist? Tried with sudo apt-get update first? The server might be down.

---

### Post by Lrover on 2006-06-25
[QUOTE=Artificial Intelligence]and you did enable all the stuff in your sourcelist? Tried with sudo apt-get update first? The server might be down.[/QUOTE]

Yes & Yes. Other packages seemed to be downloading ok. I tried it several times. Like I said, I'm not terribly concerned with the front-end since I set the f-prot updates to run as a cron job. Right now I've got some sound issues driving me buggy, but that's another story for another part of the forum. :p 

Thanks for the quick reply anyway. I'll look into this later if it becomes an issue on another install. ;)

Lrover

---

### Post by brakmaren on 2006-07-05
Thank's a million AI. Worked like a charm.

---

### Post by redicqlus on 2006-07-30
Quick question:

Any reason why I can't use aptitude instead of apt-get ?  I heard it was easier to remove things that way.

thanks much,
-red-

---

### Post by Perfect Storm on 2006-07-30
Can you install the specific libs with apt-get without problems? Also what are you trying to atptitude?

---

### Post by redicqlus on 2006-08-01
Hi, thanks for your reply.  I was referring to what you wrote here:

> 
First thing you need to run this in the terminal:

Code:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
sudo apt-get install libwww-perl
sudo apt-get install libgtk2.0-dev
sudo apt-get install checkinstall


A lot of people have said that aptitude is a better way to get things because it's easier to clean up afterwards.   I'm also not sure if  f-prot is better then AVG.  what do you think?

thanks again,

-red-

---

### Post by jrjr on 2006-08-03
.

---

### Post by Perfect Storm on 2006-08-03
It's easy to uninstall. The .deb package are listed in the synaptic package manager. Just use the search button.

> There is an install package in Synaptic. Why not use that? Is there no way to get the gui with it?

You could do that, but it's without gui.

Live and learn ;)

---

### Post by bbabiuk on 2006-08-09
I am having a problem with this howto on an AMD64 setup.

[CENTER]bbabiuk@boris:~/Desktop/xfprot-1.15$ sudo dpkg -i xfprot*.deb
Password:
dpkg: error processing xfprot-1.15_1.15-1_x86_64.deb (--install):
 package architecture (x86_64) does not match system (amd64)
Errors were encountered while processing:
 xfprot-1.15_1.15-1_x86_64.deb
bbabiuk@boris:~/Desktop/xfprot-1.15$

[/CENTER]

---

### Post by Perfect Storm on 2006-08-09
I don't think it's working on 64bit version.
You can try with sudo make install instead of sudo checkinstall and see if it works.



Can I get some feedback from non-i386 arch people so I know if it's working besides i386.

---

### Post by bbabiuk on 2006-08-09
> **Artificial Intelligence said:**
> I don't think it's working on 64bit version.
You can try with sudo make install instead of sudo checkinstall and see if it works.



Can I get some feedback from non-i386 arch people so I know if it's working besides i386.

sudo make install yeilds the same result.  Too bad!

---

### Post by Perfect Storm on 2006-08-09
Okay, thanks. I'll add to the howto that it doesn't work on 64bit version.

On a note, people could ask the developer of xf-prot to make or help him making it compatible with 64bit.

---

### Post by bbabiuk on 2006-08-09
> **Artificial Intelligence said:**
> Okay, thanks. I'll add to the howto that it doesn't work on 64bit version.

On a note, people could ask the developer of xf-prot to make or help him making it compatible with 64bit.

If I remember correctly, wasn't there a QT frontend as well to f-prot?  Does it work in the same way?  Anyone know?

---

### Post by latebeat on 2006-08-20
Thanks for the two nice how-tos for f-prot and avg! Great work!

I just have this one thing that is annoying. X-fprot always opens Konsole instead of gnome-terminal even though gnome-terminal is the default system terminal. How can I fix this ? :rolleyes: 

thanks.

---

### Post by Perfect Storm on 2006-08-20
You have both gnome and KDE installed, that's why you have both installed?

I really don't know the answer to question.

---

### Post by latebeat on 2006-08-20
I have kubuntu-desktop installed as I like to play with KDE once in a while.
I don't see what that has to do with it though? Why XF-Prot picks konsole and not gnome-terminal?

---

### Post by rohankaikini on 2006-08-25
Hi all,
I'm new to Linux.. and i've installed dapper just a few days back.. i have a stand-alone system, and am behind a proxy...
f-prot installed perfectly well.. thanks to you all..
but i am not able to update the virus definitions... i dont know how to do it..
i'm getting the following error :confused: :

> root@rohan-laptop:/home/rohan# /usr/local/f-prot/tools/check-updates.pl
***************************************
* F-Prot Antivirus Updater            *
***************************************

Nothing to be done...

root@rohan-laptop:/home/rohan# gedit /usr/local/f-prot/tools/check-updates.pl

(gedit:8293): Gdk-WARNING **: locale not supported by Xlib

(gedit:8293): Gdk-WARNING **: cannot set locale modifiers

(gedit:8293): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
root@rohan-laptop:/home/rohan# /usr/local/f-prot/tools/check-updates.pl
Use of uninitialized value in hash element at /usr/share/perl5/LWP/Protocol.pm l ine 55.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/LWP/Protoc ol.pm line 58.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/LW P/Protocol.pm line 38.
Use of uninitialized value in string eq at /usr/share/perl5/LWP/UserAgent.pm lin e 195.
Unable to connect retrieve update info from server.
Error: No such file or directory
Exiting...
root@rohan-laptop:/home/rohan#


Please tell me what to do..
thanks a lot in advance.. you guys have made this a lot simpler...
~rohan

---

### Post by Perfect Storm on 2006-08-25
Any reason you run it as non-gui (server ofcause)?

But the first line tells you that there's no new updates. When you install F-prot it automatically downloading thte newest path.

---

### Post by Kaobear on 2006-08-25
Absolutely flawless install, no issues, no errors, nothing at all.

Nicely done and hope to see more of your work soon.

---

### Post by rohankaikini on 2006-08-26
the reason i'm using fprot is that i am working on a dual platform.. and i read from this thread that its better to have some security if you're on a dual platform..
thanks for the confirmation... i hope i'm able to download the updates soon...
Thanks again
~rohan

---

### Post by Matchless on 2006-09-09
Hi,
   Has anyone tried the F-Prot GUI at [http://linux.softpedia.com/get/Security/F-Prot-GUI-16284.shtml](http://linux.softpedia.com/get/Security/F-Prot-GUI-16284.shtml) It seems interesting, but I have no idea how to install it. Any advice?

---

### Post by LordMau on 2006-09-15
I noticed in the detailed log last time I used xfprot that rar (or maybe multi-part archives in general not just rar) files aren't scanned as they are an "unsupported format". Is there a way to make fprot scan in rar (or multi-part archives/ rar/ etc.)files?

---

### Post by Matchless on 2006-09-15
OK,
   I managed to sort it out. Here is another gui for F-prot with more options:

Howto install F-prot on dapper

1) Download 44120-fprot_gui-0.5.kmdr.tar.gz from [http://linux.softpedia.com/get/Security/F-Prot-GUI-16284.shtml](http://linux.softpedia.com/get/Security/F-Prot-GUI-16284.shtml) and fp-linux-ws.deb from f-prot [http://www.f-prot.com/download/home_user/download_fplinux.html](http://www.f-prot.com/download/home_user/download_fplinux.html)
2) Check with Synaptic that you have Kommander installed on your pc.
3) Put both the downloaded files on your Desktop
4) cd Desktop
5) Right click on fp-linux-ws.deb, Kubuntu Package Menu, Install Package
6) Right click on 44120-fprot_gui-0.5.kmdr.tar.gz, Extract here and folder called fprot_gui-0.5.kmdr will be created on the Desktop
7) If you click the file it should run.
11) Right click on menu, then go to utilities, create a new item
 named F-Prot Anti virus
 Command kdesu kmdr-executor /usr/local/f-prot/fprot_gui0.5.kmdr
 
You may have to change permissions of the folder, use Krusader in root mode

---

### Post by Portalogem on 2006-09-27
First post, woohoo :KS 

Fixed!  Thank you AI for your quick reply below ... it worked.

:-D

(original message: )
Hey AI,
I followed everything you wrote; however Xfprot 1.16 just came out and I couldn't find 1.15.  
I typed:
/Desktop/here/xfprot-1.16$ ./configure --with-gtk2 --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
configure: invalid option --with-gtk2

I read that with Xfprot 1.16 that "support for GTK+ 1.2 libraries was dropped." Unsure if this would effect the libgtk2.0-dev I installed.  I wouldn't think so. 
 
from: [http://unix.freshmeat.net/daily/2006/09/24/skip_frontpage/](http://unix.freshmeat.net/daily/2006/09/24/skip_frontpage/)

---

### Post by Perfect Storm on 2006-09-28
Just drop --with-gtk2 flag then. It's not needed anymore, it will now use it automatically.

---

### Post by oenggun on 2006-10-07
Thanks... It works perfectly on my Dapper system.
I'm dropping the --with-gtk2 flag.

~un~

---

### Post by cccc on 2006-10-21
I try to install F-Prot on dapper drake, but get this error message:```

root@ania:/home/support/xfprot-1.16# apt-get clean
root@ania:/home/support/xfprot-1.16# sudo ./configure --with-gtk2 --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
configure: invalid option --with-gtk2

```what's wrong ?

---

### Post by Perfect Storm on 2006-10-21
Drop the --with-gtk2 flag.

---

### Post by cccc on 2006-10-21
thanks, but get these errors:```

# sudo ./configure  --with-sudo --autode tect --without-debug --with-install-dir=/usr/local --with-lang=pl_PL
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....Not found
Checking for xterm.....OK
Found Gtk+ libs version 2.8.20
Using Gtk+ 2.8.20 libs
Adding optimization statements to Makefile.in
Using language pl_PL
# make
cc -DIS_LINUX -DNDEBUG -Os -pipe -fomit-frame-pointer  -fno-builtin -std=gnu99 - include i18n/pl_PL.h -D_pl_PL -include mylib.h -include mygtk.h -include config. h -include xfprot.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/inc lude/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2 .0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED - DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -M xfprot-gtk.c TextView Window.c TextEditWindow.c AboutWindow.c TextCommon.c DialogWindow.c FileSelector .c mygtk.c mylib.c >> .depend
cc -DIS_LINUX -DNDEBUG -Os -pipe -fomit-frame-pointer  -fno-builtin -std=gnu99 - include i18n/pl_PL.h -D_pl_PL -include mylib.h -include mygtk.h -include config. h -include xfprot.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/inc lude/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2 .0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED - DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o xfprot-gtk.o xfpro t-gtk.c
xfprot-gtk.c:787: error: syntax error before ‘STR_FILE’
xfprot-gtk.c:788: error: syntax error before ‘STR_TOOLS’
xfprot-gtk.c:793: error: syntax error before ‘STR_QUIT’
make: *** [xfprot-gtk.o] B&#322;&#261;d 1
# sudo checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
true_fopen == 0 for fopen64("/proc/mounts", "r")
cc -DIS_LINUX -DNDEBUG -Os -pipe -fomit-frame-pointer  -fno-builtin -std=gnu99 - include i18n/pl_PL.h -D_pl_PL -include mylib.h -include mygtk.h -include config. h -include xfprot.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/inc lude/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2 .0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED - DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o xfprot-gtk.o xfpro t-gtk.c
xfprot-gtk.c:787: error: syntax error before ‘STR_FILE’
xfprot-gtk.c:788: error: syntax error before ‘STR_TOOLS’
xfprot-gtk.c:793: error: syntax error before ‘STR_QUIT’
make: *** [xfprot-gtk.o] B&#322;&#261;d 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```

---

### Post by Perfect Storm on 2006-10-21
Hmmm....It seems that's are more bug in the new 1.16 version, I havn't been able to compile it on edgy yet.

I'll take contact with the make of xf-prot.

---

### Post by cccc on 2006-10-21
sorry, a mistake !
after:```

./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local --with-lang=pl_PL
```works well.

---

### Post by cccc on 2006-10-21
I've F-Prot 

Program version: 4.6.6
Engine version: 3.16.14

installed, but if I'm trying to scan a windows directory, I get the following error:```

VIRUS SIGNATURE FILES
SIGN.DEF created 20 October 2006
SIGN2.DEF created 20 October 2006
MACRO.DEF created 20 October 2006

Search: /windows
Action: Report only
Files: "Dumb" scan of all files
Switches: -ARCHIVE -PACKED -REPORT=/home/ania/.xfprot/xfprot.log

Error: /windows is not a regular file or directory.
Error on reading /windows

Results of virus scanning:

Files: 0
MBRs: 0
Boot sectors: 0
Objects scanned: 0

Time: 0:00

No viruses or suspicious files/boot sectors were found.
```what's wrong ?

---

### Post by Perfect Storm on 2006-11-12
You need to set the specs correctly up. Try start a new tread about it.

---

### Post by Perfect Storm on 2006-11-12
Howto updated

Now works on Edgy
A face lift of the howto to make it nicer and more understandable
minor typo fixed
changed f-prot 1.15 to 1.16



If any 64 bit users can get it work on 64 bit Ubuntu, I really like to hear from them.

---

### Post by Pretzal on 2006-11-21
Thanks for the HOWTO AI but I cant get it to work on edgy. Have tried the instructions a few times with no joy. Here is the output from the terminal:

pretzal@ubuntu-desktop:~/Desktop/xfprot-1.16$ ./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
/bin/bash
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....OK
./configure: 433: gtk-config: not found
test: 433: ==: unexpected operator
/usr/bin/pkg-config
test: 433: ==: unexpected operator
test: 433: ==: unexpected operator
test: 433: ==: unexpected operator
test: 433: ==: unexpected operator
test: 433: ==: unexpected operator
test: 433: ==: unexpected operator
test: 433: ==: unexpected operator
test: 433: ==: unexpected operator
test: 433: ==: unexpected operator
You have to install the Gtk+ development (and runtime?) libraries version 2.4.x or superior.

Do you have any suggestions?

Cheers

---

### Post by Perfect Storm on 2006-11-21
Did you run this command first?
sudo aptitude install build-essential libwww-perl libgtk2.0-dev checkinstall

---

### Post by Pretzal on 2006-11-21
sure did....I ran the whole process twice with no success and same result twice.

---

### Post by Perfect Storm on 2006-11-21
Any error output when getting "sudo aptitude install build-essential libwww-perl libgtk2.0-dev checkinstall"

is pkg-config installed?

---

### Post by Pretzal on 2006-11-21
got no errors up to that point..I just did a "sudo aptitude install pkg-config" and got:

pretzal@ubuntu-desktop:~$ sudo aptitude install pkg-config
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
pretzal@ubuntu-desktop:~$ 

Dunno whats up??

---

### Post by Perfect Storm on 2006-11-21
Check and see if you have these installed:
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-cil
libgtk2.0-common
libgtk2.0-dev

---

### Post by Pretzal on 2006-11-21
yes they are all installed..... Appreciate the help though....

---

### Post by Perfect Storm on 2006-11-21
Sorry, I don't know what's wrong then.

---

### Post by Pretzal on 2006-11-21
cheers I appreciate the help anyway. I had no problems installing it using your guide for dapper. Never mind Ill just have to settle for ClamAV or AVG :)

---

### Post by Spiderdba on 2006-11-21
Well I solved this issue by simply changing the script configure.

When it reads:

[COLOR="Blue"]# Parse command line
while test $# -gt 0 ; do
case $1 in
        --help | -h )
                echo "$usage"; exit 0 ;;
#       --with-gtk1 )
#               have_libs=1; shift ;;
#        --with-gtk2 )
#                have_libs=2; shift ;;[/COLOR]

Just remove the "#" and then you have:

[COLOR="Blue"]# Parse command line
while test $# -gt 0 ; do
case $1 in
        --help | -h )
                echo "$usage"; exit 0 ;;
       --with-gtk1 )
               have_libs=1; shift ;;
        --with-gtk2 )
                have_libs=2; shift ;;[/COLOR]

After this you can go on with configure command, using also --with-gtk2 switch:

[COLOR="Blue"]./configure --with-sudo --with-gtk2 --autodetect --without-debug --with-install-dir=/usr/local
[/COLOR]

Then go on as explained in the first page.

After this the gui starts, but then I have the problem that it doesn't seem to do anything... When I click on buttons... it just doesn't do anything. Maybe it didn't autodetect f-prot correctly, but it doesn't work even if I change the configure and give it the correct f-prot path.
Any hint on this?

---

### Post by Perfect Storm on 2006-11-21
What about not uncomment gtk1 so you don't have to use the --gtk2 switch.

---

### Post by Spiderdba on 2006-11-23
> **Artificial Intelligence said:**
> What about not uncomment gtk1 so you don't have to use the --gtk2 switch.
:-k 
Well yes... using the switch or not doesn't seem a big issue... but:

Do you have any clue on the front-end not working without givin any error?

---

### Post by Perfect Storm on 2006-11-23
Not a clue. It seems it must be a bug with xf-prot, but I don't why you have and I don't.

I have attached the previous version of xf-prot, see if it works better.

---

### Post by neptune on 2006-12-10
Not sure if this has been addressed already (sorry, don't want to go through 9 pages):

Is there a similar setup for 64bit Edgy?

Thanks!

---

### Post by Perfect Storm on 2006-12-10
Not what I know. It's only tested with 32bit.

---

### Post by itoxygen on 2006-12-14
where is problem :(
@linux:~/Desktop/xfprot-1.17$ ./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
/bin/bash
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....OK
./configure: 450: gtk-config: not found
test: 450: ==: unexpected operator
/usr/bin/pkg-config
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
You have to install the Gtk+ development (and runtime?) libraries version 2.4.x or superior.

---

### Post by Chazall1 on 2006-12-21
I have the exact same out-put. I have an Updated Edgy and have used F-prot the current version, and was using xfprot v 1.15 and all was well. I removed v 1.15 to go to the new version 1.17. I have all the GTK files, and I get the same errors when running./configure?

I used F_prot in Dapper, and did an upgrade to Edgy, and Everything functioned.

Any other suggestions!

Thanks:confused:

---

### Post by matchstich on 2006-12-31
how do i uninstall it?
thanks

---

### Post by Perfect Storm on 2006-12-31
```
sudo aptitude remove xfprot fp-linux-ws
```

---

### Post by matchstich on 2007-01-05
Code:           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:





i got that error when i did the last line in this
]
cd && cd Desktop
tar zxvf xfprot-1.16.tar.gz
cd xfprot-1.16
./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
make
sudo checkinstall

any ideas

---

### Post by Perfect Storm on 2007-01-06
It's not an error. It creates a package of xf-prot so it's easely to uninstall. Just follow the default suggestion.

---

### Post by GaryUK on 2007-01-15
> **itoxygen said:**
> where is problem :(
@linux:~/Desktop/xfprot-1.17$ ./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
/bin/bash
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....OK
./configure: 450: gtk-config: not found
test: 450: ==: unexpected operator
/usr/bin/pkg-config
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
test: 450: ==: unexpected operator
You have to install the Gtk+ development (and runtime?) libraries version 2.4.x or superior.

I get this exact same error - xfprot 1.18 (latest version) will not compile against libgtk2.0
 - What I don't get is that no linux distro seems to have it in their repos and, even more strangely, distrowatch says that edgy has GTK+ 2.10 which, according to the GTK website, is the not quite latest version - ar we all missing something here ?

Anyone like to advise on what libgtk-dev package is required to build xfprot in edgy?

Thanks and Regards,

---

### Post by 01001101-01000100 on 2007-01-18
$ sudo ./configure --with-sudo --autodetect --without-debug
/bin/bash
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....OK
./configure: 447: gtk-config: not found
test: 447: ==: unexpected operator
/usr/bin/pkg-config
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
You have to install the Gtk+ development (and runtime?) libraries version 2.4.x or superior.

USING EDGY
another one with this problem. earlier versions of xfprot actually told me what version of gtk i was running which is 2.10.8 so my manual update of gtk must have worked however these errors make me think otherwise.

i also found that that if libgtk1.2 is installed from synaptic it creates the gtk-config file however version errors occur similar to the one above. the errors were slightly different though stating that there were (from what i could tell) syntax errors looking for ")" and "=" and other symbols while in the 'sudo make' process. sorry for the lack of output on that error.

oh, and i made that change to the configure file by un-commenting ONLY the gtk2 section but the errors are the same.

thx for the help, great thread, much help. bit of a n00b to the linux but have a good understanding of programming but this makes it damn simple.

*"I'm the one who has to die when its time for me to die, so let me live my life, the way I want too"*

---

### Post by 01001101-01000100 on 2007-01-19
$ locate gtk+
/usr/lib/pkgconfig/gtk+-2.0.pc
/usr/lib/pkgconfig/gtk+-unix-print-2.0.pc
/usr/lib/pkgconfig/gtk+-x11-2.0.pc
/usr/local/lib/pkgconfig/gtk+-x11-2.0.pc
/usr/local/lib/pkgconfig/gtk+-unix-print-2.0.pc
/usr/local/lib/pkgconfig/gtk+-2.0.pc
/usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk+.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk+.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk+.mo

the files located in /usr/local/lib/pkgconfig state "gtk_host=i686-pc-linux-gnu" whereas the others dont state anything at all with regards to a statement like that. im not running i686, should i remove these files or can i without detrimental effects to my system? if i do remove them would a "sudo ldconfig" fix any dependency issues? i could also do that through synaptic.

playing with configure file for xfprot-1.18 but no headway made...

---

### Post by 01001101-01000100 on 2007-01-19
heres some new output.. in the 'configure' file, i replaced all the '==' with '-eq' where 'test' is used in the process of determining what version of GTK+ is available which got me to this point. i also tested '$have_libs' to be sure it was getting set to '2' which it was. followed the rest of the instructions with no problem but i am unable to update and the scan just seems to hang. i found this out by executing './xfprot-gtk' from the terminal so i could see the output from the application. i also used 'sudo ./xfprot-gtk' with the same results.

*my line 413 in configure*
> elif test ` pkg-config  gtk+-2.0 --modversion | grep -c ^2.10` **-eq** 1  ; then

since i knew i had 2.10.8 (with proof from variable and version tests) i just commented (#) most of the other versions (if statements) instead of changing the syntax, im lazy :).

as for the error './configure: 446: gtk-config: not found', its only because 'configure' looks for it. I would imagine it could be commented out. the code that checks for it starts on my line 362 followed by a condition followed by a 'pkg-config' check which works out aok as seen below.

*my line 362 in configure*
> which gtk-config &>/dev/null

dont know if this helps any as the app doesnt work properly but if anything its a start.

> $ sudo ./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
/bin/bash
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....OK
./configure: 446: gtk-config: not found
/usr/bin/pkg-config
Found Gtk+ libs version 2.10.8
/usr/bin/pkg-config
Using Gtk+ 2.10.8 libs
Adding optimization statements to Makefile.in
Setting language to en_GB, you can override this with: --with-lang=xx_XX
Supported languages are:
de_DE
en_GB
es_ES
fr_FR
it_IT
pl_PL
pt_BR


---

### Post by CC=AC3 on 2007-01-30
Im having the same problem with this message:

./configure: 447: gtk-config: not found
test: 447: ==: unexpected operator
/usr/bin/pkg-config
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
You have to install the Gtk+ development (and runtime?) libraries version 2.4.x or superior.

Nobody has a fix? :( I didnt see it answered anywhere else...

-CC=AC3

---

### Post by pbureau on 2007-02-02
well seems that with 6.10 this x for f-prot is not going to work and I have no idea why.

here is my log if it helps,

**toshiba-4600:/home/pbureau/xfprot-1.18# locate locate gtk+**
/var/cache/locate
/var/lib/dpkg/info/slocate.conffiles
/var/lib/dpkg/info/slocate.list
/var/lib/dpkg/info/slocate.md5sums
/var/lib/dpkg/info/slocate.postinst
/var/lib/dpkg/info/slocate.postrm
/var/lib/dpkg/info/slocate.preinst
/var/lib/dpkg/info/slocate.prerm
/var/lib/slocate
/var/lib/slocate/slocate.db
/etc/cron.daily/find.notslocate
/etc/cron.daily/slocate
/usr/bin/locate
/usr/bin/locate.notslocate
/usr/bin/slocate
/usr/bin/updatedb.notslocate
/usr/lib/locate
/usr/lib/locate/bigram
/usr/lib/locate/code
/usr/lib/locate/frcode
/usr/share/apps/ksgmltools2/docbook/xsl/params/htmlhelp.button.locate.xml
/usr/share/doc/slocate
/usr/share/doc/slocate/Changelog.gz
/usr/share/doc/slocate/README.Debian
/usr/share/doc/slocate/README.gz
/usr/share/doc/slocate/changelog.Debian.gz
/usr/share/doc/slocate/changelog.gz
/usr/share/doc/slocate/copyright
/usr/share/man/man1/locate.1.gz
/usr/share/man/man1/locate.notslocate.1.gz
/usr/share/man/man1/slocate.1.gz
/usr/share/man/man1/updatedb.notslocate.1.gz
/usr/share/man/man3/XdbeAllocateBackBufferName.3.gz
/usr/share/man/man3/XdbeDeallocateBackBufferName.3.gz
/usr/share/man/man3/XtAllocateGC.3.gz
/usr/share/man/man5/locatedb.5.gz
/usr/share/snmp/mib2c-data/generic-data-allocate.m2i
/usr/src/linux-headers-2.6.17-10-generic/include/config/mtd/redboot/parts/unallocated.h
/usr/lib/pkgconfig/gtk+.pc
/usr/lib/pkgconfig/gtk+-2.0.pc
/usr/lib/pkgconfig/gtk+-unix-print-2.0.pc
/usr/lib/pkgconfig/gtk+-x11-2.0.pc
/usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk+.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk+.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk+.mo


**toshiba-4600:/home/pbureau/xfprot-1.18#: sudo apt-get upgrade**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9527kB of archives.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtk2.0-dev 2.10.6-0ubuntu3.1 [2572kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtk2.0-common 2.10.6-0ubuntu3.1 [4454kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtk2.0-bin 2.10.6-0ubuntu3.1 [22.4kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtk2.0-0 2.10.6-0ubuntu3.1 [2479kB]
Fetched 9527kB in 1m8s (139kB/s)                                               
(Reading database ... 139298 files and directories currently installed.)
Preparing to replace libgtk2.0-dev 2.10.6-0ubuntu3 (using .../libgtk2.0-dev_2.10.6-0ubuntu3.1_i386.deb) ...
Unpacking replacement libgtk2.0-dev ...
Preparing to replace libgtk2.0-common 2.10.6-0ubuntu3 (using .../libgtk2.0-common_2.10.6-0ubuntu3.1_all.deb) ...
Unpacking replacement libgtk2.0-common ...
Preparing to replace libgtk2.0-bin 2.10.6-0ubuntu3 (using .../libgtk2.0-bin_2.10.6-0ubuntu3.1_i386.deb) ...
Unpacking replacement libgtk2.0-bin ...
Preparing to replace libgtk2.0-0 2.10.6-0ubuntu3 (using .../libgtk2.0-0_2.10.6-0ubuntu3.1_i386.deb) ...
Unpacking replacement libgtk2.0-0 ...
Setting up libgtk2.0-common (2.10.6-0ubuntu3.1) ...
Setting up libgtk2.0-bin (2.10.6-0ubuntu3.1) ...
Updating the IM modules list for GTK+-2.10.0...done.
Updating the gdk-pixbuf loaders list for GTK+-2.10.0...done.

Setting up libgtk2.0-0 (2.10.6-0ubuntu3.1) ...

Setting up libgtk2.0-dev (2.10.6-0ubuntu3.1) ...


**toshiba-4600:/home/pbureau/xfprot-1.18# ./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local**

Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
/bin/bash
Retrying...
found: /home/pbureau/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....OK
/usr/bin/gtk-config
test: 447: ==: unexpected operator
/usr/bin/pkg-config
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
You have to install the Gtk+ development (and runtime?) libraries version 2.4.x or superior.
**:/home/pbureau/xfprot-1.18#**

---

### Post by thorekk on 2007-02-03
It worked for me on Edgy. You need libgtk2.0-dev

sudo apt-get install libgtk2.0-dev

and you should edit the configure file, the first line should be #!/bin/bash.

I've found this solution here:
[http://www.ubuntugeek.com/f-prot-antivirus-with-xfprot-web-interface.html]("http://www.ubuntugeek.com/f-prot-antivirus-with-xfprot-web-interface.html")

---

### Post by GaryUK on 2007-02-03
> **thorekk said:**
> It worked for me on Edgy. You need libgtk2.0-dev

sudo apt-get install libgtk2.0-dev

and you should edit the configure file, the first line should be #!/bin/bash.

I've found this solution here:
[http://www.ubuntugeek.com/f-prot-antivirus-with-xfprot-web-interface.html]("http://www.ubuntugeek.com/f-prot-antivirus-with-xfprot-web-interface.html")

I can confirm that this fix for the libgtk2.0-dev problem works on Edgy - just tried it myself and have now got fprot working.

Big Thanks to thorekk and Artificial Intelligence for their sterling efforts here:KS :KS :KS 

Thanks a bunch and regards.

---

### Post by lukew on 2007-02-06
This works in edgy with xfprot-1.18.

Had to use sudo ./configure

Also have to run as root to allow updates becuase it seems to use su and not sudo!!!

---

### Post by kpatz on 2007-02-06
I ran into the same issues with no gtk-config, so I uncommented the with-gtk2 option and ran with that.  I was able to compile, install, and run, but I can't get a scan to do anything.  I can run a test and it works (and finds the EICAR_Test_File), but when I hit "scan" nothing happens.  In the terminal that I launched xfprot from it displays "xfprot: executing scan on: (directory)" where directory is the path to scan, but I never get any scan results, reports, or logs.  Virus List works, as does Info, but nothing from Scan.

Any ideas?

---

### Post by 01001101-01000100 on 2007-02-06
> **thorekk said:**
> It worked for me on Edgy. You need libgtk2.0-dev

sudo apt-get install libgtk2.0-dev

and you should edit the configure file, the first line should be #!/bin/bash.

I've found this solution here:
[http://www.ubuntugeek.com/f-prot-antivirus-with-xfprot-web-interface.html]("http://www.ubuntugeek.com/f-prot-antivirus-with-xfprot-web-interface.html")

that bin/bash line did it for me, works like a charm, much thx

if installing fprot, xfprot in edgy, my uneducated advice is to use the instructions then edit the configure file as above, then continue through the instructions

---

### Post by Perfect Storm on 2007-03-03
Howto updated

added howto solve dependency problem with libgtk2
new version of F-prot is out.

---

### Post by Man_Beach on 2007-03-04
> **Artificial Intelligence said:**
> Howto updated

added howto solve dependency problem with libgtk2
new version of F-prot is out.

Is the dependency problem to do with the frontend or f-prot itself?
(i.e. if you don't need the frontend, is there any need to resolve the dependency problem?)

---

### Post by Perfect Storm on 2007-03-04
It's the frontend. You don't need GTK2-dev if you decide not to use the frotend.

---

### Post by qprfact on 2007-03-10
Looking back at previous posts, there's this:

> 
Quote:
Originally Posted by thorekk View Post
It worked for me on Edgy. You need libgtk2.0-dev

sudo apt-get install libgtk2.0-dev

and you should edit the configure file, the first line should be #!/bin/bash.

I've found this solution here:
[http://www.ubuntugeek.com/f-prot-ant...interface.html](http://www.ubuntugeek.com/f-prot-ant...interface.html)
that bin/bash line did it for me, works like a charm, much thx


As I am also getting the error message below:

> steve@steve-desktop:~/Desktop/xfprot-1.18$ sudo ./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....OK
/bin/bash
/usr/bin/konsole
/usr/bin/gtk-config
test: 447: ==: unexpected operator
/usr/bin/pkg-config
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
You have to install the Gtk+ development (and runtime?) libraries version 2.4.x or superior.


But I don't really understand - change what config file? And how? I've installed libgtk2.0-dev, checkinstall, gcc and libwww-perl!

Thanks!

---

### Post by Perfect Storm on 2007-03-10
When you extracting the tarball, you'll find a file called **configure** change it as described in the howto troubleshooting.

---

### Post by qprfact on 2007-03-10
Ah!!! That ching you hear is the penny dropping!

Thanks very much!

---

### Post by qprfact on 2007-03-10
An additional question - which sort of has been asked further up in this thread, but I couldn't see the resolution - I'm looking to scan from root, and get these sorts of messages:

> Error on scanning /etc/X11/.xorg.conf.swp (access denied)


How can I change things so the access is available, or do I need to sign in as root?

(also - when running F2 update - I get the message
 > ***************************************
* F-Prot Antivirus Updater            *
***************************************

Nothing to be done...


I presume that means there are no updates to be had, rather than something else?!

---

### Post by Perfect Storm on 2007-03-10
Not advisable, only if you are sure something suspious are going on;
```
gksudo xfprot
```

about the update:
When you install the F-prot file it's updating by itself, so you won't see any updates right away.

---

### Post by tiepolo on 2007-03-13
hello!

I would like to add the complete list of dependencies that i got from Tito Ragusa, author of xf-prot for xf-prot 1.18

grep
textutils
unzip
libnet-perl
libwww-perl
libgtk2.0-0 
libgtk2.0-dev
gcc
pkg-config

i had many problems trying to work without the list................

Paolo

---

### Post by Perfect Storm on 2007-03-17
> **tiepolo said:**
> hello!

I would like to add the complete list of dependencies that i got from Tito Ragusa, author of xf-prot for xf-prot 1.18

grep
textutils
unzip
libnet-perl
libwww-perl
libgtk2.0-0 
libgtk2.0-dev
gcc
pkg-config

i had many problems trying to work without the list................

Paolo

It's actually the same that is list in the howto

libwww-perl depends on libnet-perl
gcc comes with build-essential
pkg-config is installed by default on Ubuntu and only used if for automake and autoconfig.
libgtk2.0-dev is mentions, libgtk2.0-0 is installed by default.
Textutils is only a transit package and is not needed.
grep is installed by default.

---

### Post by iClouseau88 on 2007-03-28
Hi,

I just installed Feisty Fawn, and was following your tutorial on installing F-Prot.  Somehow I am not able to do this, since it appears libgtk2.0 files are currently not available for installation.  Any idea how and when one can install gtk+ engine?

:confused:

---

### Post by Perfect Storm on 2007-03-28
I havn't tried feisty yet (I  need something stable), but you can try the .deb package from their homepage, they now support .deb (but I havn't tried yet).

---

### Post by iClouseau88 on 2007-03-28
Hi,

Thanks for your reply. I went to F-Prot's homepage but didn't find any .deb package other than the debian/gnu file version 4.6.7.  By the way, the latest version of the front end, XFPROT, is 1.19.

---

### Post by iClouseau88 on 2007-04-03
Hi,

I still need help.  Just installed libgtk2.0-dev (the rest are already installed).

I am unable to install the front end for F-prot, and by the way, there's a mistake in the tutorial where "zxvf" should have read "xzvf":

Code:

hoe1@hoe1-laptop:~/Desktop$ sudo tar xzvf xfprot-1.**19**.tar.gz
xfprot-1.19/
xfprot-1.19/i18n/
xfprot-1.19/i18n/pl_PL.h
xfprot-1.19/i18n/README
xfprot-1.19/i18n/es_ES.h
xfprot-1.19/i18n/en_GB.h
xfprot-1.19/i18n/pt_BR.h
xfprot-1.19/i18n/it_IT.h
xfprot-1.19/i18n/de_DE.h
xfprot-1.19/i18n/fr_FR.h
xfprot-1.19/icons/
xfprot-1.19/icons/antivirus-128x128.png
xfprot-1.19/icons/README
xfprot-1.19/icons/antivirus-48x48.png
xfprot-1.19/icons/antivirus-32x32.png
xfprot-1.19/icons/antivirus-64x64.png
xfprot-1.19/mygtk.c
xfprot-1.19/README
xfprot-1.19/mygtk.h
xfprot-1.19/COPYING
xfprot-1.19/Makefile
xfprot-1.19/eicar.com.txt
xfprot-1.19/configure
xfprot-1.19/xfprot-gtk.c
xfprot-1.19/dialog_window.c
xfprot-1.19/mylib.c
xfprot-1.19/mylib.h
xfprot-1.19/xfprot_fedora.spec
xfprot-1.19/text_common.c
xfprot-1.19/file_selector.c
xfprot-1.19/Changelog
xfprot-1.19/about_window.c
xfprot-1.19/description-pak
xfprot-1.19/xfprot.desktop
xfprot-1.19/text_edit_window.c
xfprot-1.19/text_view_window.c
hoe1@hoe1-laptop:~/Desktop$ **cd xfprot-1.19**
[B]bash: cd: xfprot-1.19: Permission denied
[/B]

Any idea why permission denied, and how can I go around this?  Thanks in advance.

:confused:

---

### Post by iClouseau88 on 2007-04-06
Hi,

I am the owner and only user of this machine.  Somehow, ownership of the directory or file xfprot-1.19 is assigned to root, and as a result,I don't have permission to read, write or execute this file.  Today I got into the terminal, became root, but still cannot change file permission of xfprot-1.19 so that I can complete installing it.

Could you show me how to change file permission for this?  Really need your help.  Thanks.

:confused:

---

### Post by lukew on 2007-04-07
> **iClouseau88 said:**
> Hi,

I am the owner and only user of this machine.  Somehow, ownership of the directory or file xfprot-1.19 is assigned to root, and as a result,I don't have permission to read, write or execute this file.  Today I got into the terminal, became root, but still cannot change file permission of xfprot-1.19 so that I can complete installing it.

Could you show me how to change file permission for this?  Really need your help.  Thanks.

:confused:

Sounds like you need to make is executable.

```
sudo chmod +x xfrot-1.19
```

---

### Post by lukew on 2007-04-26
Hay AI! Works in Feisty a treat (again)


Thanks!!

Luke

---

### Post by TTime on 2007-05-04
HI all I am a 3 day Virgin with this operating system, and was installing Fprot  but I think I did some thing wrong with setting up the application launcher. 
when I enter this code ( sudo nano /usr/share/applications/fprot.desktop) into the terminal , the terminal changes and has sudo nano /usr/share/applications/fprot.desktop in black with nothing in it.
which seems to tell me that the code

[Desktop Entry]
Name=F-Prot
Comment=Anti-Virus Application
Exec=xfprot
Icon=/usr/local/xfprot/icons/antivirus-48x48.png
Terminal=false
Type=Application
Categories=Application;System;

was not saved. Is there any way of editing , or deleting this launcher and recreating it ?
Please help this newbe as I have no idea about linux code

many thanks

---

### Post by Perfect Storm on 2007-05-04
You save with [ctrl] + [o] and exit with [ctrl] + [x]

Just sudo nano /usr/share/applications/fprot.desktop again and fill in the information.

---

### Post by TTime on 2007-05-05
> **Artificial Intelligence said:**
> You save with [ctrl] + [o] and exit with [ctrl] + [x]

Just sudo nano /usr/share/applications/fprot.desktop again and fill in the information.

thanks that worked - but now when I click the fprot icon I get this message

" could not launch menu item - failed to execute child process "xfprot' (permission denied) "

so now I'm stuck again
fyi
I had uninstalled it previously then re-installed it and it through up this error "mkdir: cannot create directory `/usr/local/xfprot/icons': File exists
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK"


maybe I did something wrong ?

---

### Post by Perfect Storm on 2007-05-12
Guide updated
----------------------

xf-prot is now 1.19
tested on Feisty x86

---

### Post by Perfect Storm on 2007-08-27
Updated.

New F-prot is out.
New Xf-prot is out.

---

### Post by qprfact on 2007-10-22
I've succesfully installed F-Prot, and trying to get XFProt set up.

I've downloaded v1.20. Made directory, done ./configure. When I enter make install I get this:

```
cc -DIS_LINUX -DGTK_2_12 -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -fstrict-aliasing -Wtrigraphs -Wmissing-format-attribute  -Wcomment -Wredundant-decls  -Wformat=2 -O3 -fno-builtin -std=gnu99 -Wformat-y2k -Wno-format-extra-args -Wno-format-zero-length -Wformat-security -funsigned-char -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o xfprot-gtk.o xfprot-gtk.c
xfprot-gtk.c: In function ‘main’:
xfprot-gtk.c:1004: error: ‘GtkTooltips’ undeclared (first use in this function)
xfprot-gtk.c:1004: error: (Each undeclared identifier is reported only once
xfprot-gtk.c:1004: error: for each function it appears in.)
xfprot-gtk.c:1004: error: ‘action_tooltip’ undeclared (first use in this function)
xfprot-gtk.c:1005: error: ‘onlyheur_tooltip’ undeclared (first use in this function)
xfprot-gtk.c:1192: warning: implicit declaration of function ‘gtk_tooltips_new’
xfprot-gtk.c:1198: warning: implicit declaration of function ‘gtk_tooltips_set_tip’
xfprot-gtk.c:1198: warning: implicit declaration of function ‘GTK_TOOLTIPS’
xfprot-gtk.c:1208: warning: implicit declaration of function ‘gtk_tooltips_enable’
make: *** [xfprot-gtk.o] Error 1 
```

I've got all the dependencies listed in the HOWTO. But must be missing something else - can someone assist please?!

Thanks!

---

### Post by genbuntu on 2007-10-25
Hello guys

Can I install f-prot from synaptic (would it install the latest and satisfy all dependencies) ? I checked in synaptic and it says f-prot-installer version 0.5.22 .

Thanks

---

### Post by Perfect Storm on 2007-10-25
Yes, but it coms without xf-prot (frontend).

---

### Post by qprfact on 2007-10-25
On that subject, can you let me know the answer to my thread above about setting up xf-prot?

---

### Post by Perfect Storm on 2007-10-25
Then I need computer specs - Ubuntu version - which arch.

---

### Post by qprfact on 2007-10-25
Gutsy, 7.10. What does arch mean?

---

### Post by Perfect Storm on 2007-10-25
32 bit/64 bit/ Pcc

---

### Post by qprfact on 2007-10-25
Ah! 32 bit.

F-Prot itself is installed and working OK, it's the front end I haven't managed to figure out.

---

### Post by genbuntu on 2007-10-25
> **Artificial Intelligence said:**
> Yes, but it coms without xf-prot (frontend).

Oh, I see. Being a neophyte I thought it'll be simpler to install graphically thru synaptic. I tried looking up xf-prot in synaptic but it is not there.

---

### Post by spartan777 on 2007-10-26
why shouldn't we use f-prot version 6.0? i would assume that there are some useful things in the newest version. i can't figure out how to install f-prot 6 in a way that xfprot will detect it anyways.

trying to install as described in this how-to, i get the following error while trying to run the make command with xfprot.

```
cc -DIS_LINUX -DGTK_2_12 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o xfprot-gtk.o xfprot-gtk.c
xfprot-gtk.c: In function ‘main’:
xfprot-gtk.c:1004: error: ‘GtkTooltips’ undeclared (first use in this function)
xfprot-gtk.c:1004: error: (Each undeclared identifier is reported only once
xfprot-gtk.c:1004: error: for each function it appears in.)
xfprot-gtk.c:1004: error: ‘action_tooltip’ undeclared (first use in this function)
xfprot-gtk.c:1005: error: ‘onlyheur_tooltip’ undeclared (first use in this function)
xfprot-gtk.c:1192: warning: implicit declaration of function ‘gtk_tooltips_new’
xfprot-gtk.c:1198: warning: implicit declaration of function ‘gtk_tooltips_set_tip’
xfprot-gtk.c:1198: warning: implicit declaration of function ‘GTK_TOOLTIPS’
xfprot-gtk.c:1208: warning: implicit declaration of function ‘gtk_tooltips_enable’
make: *** [xfprot-gtk.o] Error 1

```

---

### Post by qprfact on 2007-10-26
Yep, virtually the same error message as I get, so the same thing is tripping us both up.

---

### Post by mahiyar on 2007-11-05
Same thrice here, even if you proceed to check install you get the error, trying to learn command line f-prot.

---

### Post by Perfect Storm on 2007-11-05
This howto havn't been tested on Gutsy.

---

### Post by mahiyar on 2007-11-05
Uh-Oh. Anyways F-Prot works fine with command line, its only the interface thats the problem.

---

### Post by ghostcrab on 2007-11-06
I get this error message. I installed it right 
Could not launch menu item

Failed to execute child process "xfprot" (No such file or directory)

I dont get it I done everything correct I'm lost now I did the bash script I used gedit instead of nano 
hoo well thanks for the how to AI

---

### Post by DustyinBFE on 2007-11-18
One of the rare times I've installed something from source, and nothing went wrong!!

---

### Post by chastom on 2008-03-17
I can't finish installing because I get the message that gtk+-2.0 does not exist.

---

### Post by Perfect Storm on 2008-03-17
Did you tried what the troubleshooting suggested in the guide?

---

### Post by Healey on 2008-05-01
Hi

Does this F-Prot How to work in Hardy Heron (8.04)

Thanks in advance

Healey

---

### Post by Perfect Storm on 2008-05-01
Yes, it should.

---

### Post by Healey on 2008-05-01
Hi

OK I will give it a try

Thanks

Healey

---

### Post by Healey on 2008-05-02
Hi 

I followed the instructions and I get

========================= Installation results ===========================
test: 6: /usr/bin/xfprot: unexpected operator
mkdir -p /usr/local/xfprot
chmod 0755 /usr/local/xfprot
chmod: changing permissions of `/usr/local/xfprot': No such file or directory
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


Any ideas ??

Thanks

Healey

---

### Post by Perfect Storm on 2008-05-02
Here's a .deb instead: [http://web.tiscali.it/sharp/xfprot/xfprot_1.22-1_i386.deb](http://web.tiscali.it/sharp/xfprot/xfprot_1.22-1_i386.deb)

---

### Post by Healey on 2008-05-02
Hi

I assume you meant install with GDebi Package Installer - Is that correct ???

I have done this and it appears to be working - I will try a scan and see what happens

Thanks

Healey

---

### Post by Perfect Storm on 2008-05-02
Aye.

---

### Post by Healey on 2008-05-02
Hi

That worked very well - Just did a scan and found the Eicar test virus, so I guess it must be working

Thanks

Healey

---

### Post by 8086 on 2008-05-08
XFProt doesn't work with the new improved version of f-prot.

---

### Post by Perfect Storm on 2008-05-08
Nope.

---

### Post by curr3ncychas3 on 2008-10-31
i have hardy 8 installed and i'm having problem doing the first step because f-prot has been upgraded to a new version and when i enter

sudo dpkg -i  fp-linux-ws.deb

this pops up in the terminal

dpkg: error processing fp-linux-ws.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fp-linux-ws.deb


can anyone help me out.

---

### Post by Perfect Storm on 2008-11-01
make sure you have changed directory in the terminal to where the file is.

---

### Post by curr3ncychas3 on 2008-11-01
> **Artificial Intelligence said:**
> make sure you have changed directory in the terminal to where the file is.

sorry i dont understand,i'm a newbie

can you show me how i can do that
i saved the new f-prod on the desktop.

---

### Post by Perfect Storm on 2008-11-01
> **curr3ncychas3 said:**
> sorry i dont understand,i'm a newbie

can you show me how i can do that
i saved the new f-prod on the desktop.

```
cd ~/Desktop
```

cd = change directory.

---

### Post by curr3ncychas3 on 2008-11-01
> **Artificial Intelligence said:**
> ```
cd ~/Desktop
```

cd = change directory.

this is what comes up
me@me:~$ cd ~/Desktop
me@me:~/Desktop$ sudo dpkg -i  fp-linux-ws.deb
[sudo] password for moneyintrigueme: 
dpkg: error processing fp-linux-ws.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fp-linux-ws.deb
me@me:~/Desktop$ 


is it because i downloaded fp-Linux-i686-ws.tar.gz?

---

### Post by Perfect Storm on 2008-11-01
You have to download the .deb file.

---

### Post by curr3ncychas3 on 2008-11-01
> **Artificial Intelligence said:**
> You have to download the .deb file.
i looked through the page and i don't think they have the deb files anymore.

---

### Post by Split-Skreen on 2008-12-19
I've been looking for a good anti-virus for linux so that I can ensure I do not infect other Pcs on my network or with file transfers. 
That being said I thought I had found a solution with this thread but alas there is no .deb available for f-Prot on its website. I attempted to compile and configure the tarball file that I presume replaced the .deb but it didn't work as anticipated.

I really want a solid native anti virus;
suggestions?

---

### Post by Treelvr on 2009-01-04
First I have looked everywhere for the .deb install for f prot. I do not think it exist. The best I can find is:

fp-Linux-i686-ws.tar.gz
44120-fprot_gui-0.6.kmdr.tar.gz
visual_f-prot_v2.1.tar.gz

Everytime I use this forum and search on f prot it always gives a link that is an 404.

Can someone either tell me how to install these or where to find the .deb files or am I just SOL. I have clam installed but it will only scan ubuntu install. I want to scan windows. I only use windows for frontpage but I want it clean.

---

### Post by DonaldJ on 2009-03-30
Got F-prot into Applications...

When I click it I get a popup:  "F-prot binary not found"...

---

### Post by esalnoj on 2009-03-31
I ran the following, but with the i686 tar instead of xfprot.

cd ~/Desktop
tar zxvf fp-Linux-i686-ws.tar.gz
cd f-prot
./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
make
sudo checkinstall

gives the following errors:

user@Thinkpadfore:~/Desktop$ cd f-prot
user@Thinkpadfore:~/Desktop/f-prot$ ./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
bash: ./configure: No such file or directory
user@Thinkpadfore:~/Desktop/f-prot$ make
make: *** No targets specified and no makefile found.  Stop.

What do you see wrong here? How would this be fixed?

Apparently the xfprot is now a .deb file.

---

### Post by traqedy on 2009-04-06
cd f-prot/

./install-f-prot.pl

---

### Post by esalnoj on 2009-04-06
I ran those changes, went farther, but got:

Never mind, just had to run sudo in front of ./install

It works.

---

### Post by BenB1 on 2010-03-31
> **Split-Skreen said:**
> I've been looking for a good anti-virus for linux so that I can ensure I do not infect other Pcs on my network or with file transfers. 
That being said I thought I had found a solution with this thread but alas there is no .deb available for f-Prot on its website. I attempted to compile and configure the tarball file that I presume replaced the .deb but it didn't work as anticipated.

I really want a solid native anti virus;
suggestions?

Not to hijack or derail Artificial Intelligence's thread but ClamAv can be used effectively. And it's available via Synaptic. Easy to install. Get the clamav deamon as well, that'll let you have an on demand scanner. It lets me point at a file in Nautilus and scan, just to be sure. And it will also install under the System Tools menu as Virus Scanner.

---

### Post by harbhag on 2010-07-16
How can I remove the infected file after scan is completed ? I an not using GUI , I am using commandline .

---

### Post by Perfect Storm on 2010-07-16
Before doing anything. Which file and where (before you're hosing your system).

---

### Post by mikeymike11 on 2013-01-02
clamav freezes up.
Can i not install f-prot via synaptic?

---

