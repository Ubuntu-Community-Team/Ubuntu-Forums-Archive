---
title: "Lost XFCE at startup"
date: 2015-09-02
forum: Ubuntu Studio
---

### Post by 33Nicolas on 2015-09-02
Newbie question. I must have installed an update that didn't agree with XFCE since it won't load anymore. I searched the forum, but didn't find anything.

I'm using an old Dell 390 with SCSI drives and the latest Ubuntu Studio and the latest updates.

Is there a way to return to a previous state or can it just get started again? Also, the computer is having a hard time updating software. It says it can't find the info, yet it says if the computer is up to date. Seems like a bit of a mess.

Thanks for your insight and input!

---

### Post by Bashing-om on 2015-09-02
33Nicolas; Hello;

The first thing is to make sure the system is stable, and that the package manager is in a happy state. Once the foundation is firm we look at what is going on in the starting of the GUI ( just another layer on top of the kernel ).

So, Can you boot to a terminal ( at login screen key combo ctl+alt+F1 ) ?

What results with terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

If/when that goes well, we see what results in starting the GUI from terminal - fix the issue.

As to "Is there a way to return to a previous state" In a standard install, NO . Such a restoration is not needed Though there are means provided to make 'backups". Given time, effort and a liveDVD ubuntu is always fixable. We fix it and go on OR backup data and re-install. A (RE-)install is considered the nuclear solution. To soon to even consider that option.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-09-02
Which release are you using?

---

### Post by v3.xx on 2015-09-02
As already stated, there is no restore.  But one thing you can try (if you had a kernel upgrade) it go back to previous kernel at the grub boot screen.

---

### Post by 33Nicolas on 2015-09-02
Tx Bashing-on. I did both in terminal, so running latest instances of latest Ubuntu Studio.

I believe the latest. I keep the computer updated regularly, daily. I did have a few problems a few days ago when the software updater app wasn't recognizing the package list it was trying to download. I terminaled the update and upgrade.

OK, a dimmer of hope here. I'll check into how to get into the grub boot screen.

Tx all.

---

### Post by v3.xx on 2015-09-02
> If/when that goes well, we see what results in starting the GUI from terminal - fix the issue.
And you tried this?

---

### Post by 33Nicolas on 2015-09-02
Nothing worked so far. I don't know what the terminal command is to start a XFCE session. Thanks

---

### Post by Bashing-om on 2015-09-02
33Nicolas; Hey ;

We will get to that:
> 
 I don't know what the terminal command is to start a XFCE session.


For now as you say nothing works. I want confirmation that the package manager is happy:
 Build a text file with all these requested outputs .
```

lsb_release -a > stuff-txt
sudo apt-get update >> stuff-txt
sudo apt-get -y upgrade >> stuff-txt
sudo apt-get -f install >> stuff-txt
sudo apt-get install pastebinit
cat stuff-txt | pastebinit

```

And one other check:
```

sudo dpkg -C

```
Any output at all ? or - a good thing - just a return to prompt ?

Give the commands plenty of time to complete.
Where the end result will be a URL back in your terminal. Pass that link back here to the thread and we will read that generated file ,

If all is in order. we look at starting the GUI.

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2015-09-02
cat stuff-txt | pastebinit

Nice touch on such a long request :)

Edit

Think I'm going to throw in inxi and use it as a standard request when I can.

Maybe a one line command.

edit2

inxi -Fxz  #that covers it all I think

---

### Post by Bucky Ball on 2015-09-03
```
startxfce4
```

Starts the xfce4 session.

---

### Post by Bashing-om on 2015-09-03
33Nicolas; Hey ...

Much much to vague :
```

The software update manager keeps on saying it can't read some of the databases 

```
to make any sort of determination. Please provide the requested information as provided by that stuff-txt file ( or install the inxi tool ) .
There can be so many things that can cause all this... ranging from config issues, /boot partition at capacity, other partitions at capacity .. running out of inodes and the list goes on and on and on .. We must start this diagnosis somewhere and the place to start is a knowing that the package manager has operating head room and is in a happy state. 

I am a simple person, with a simple mind .. I think 1 thing at a time and progress from point A to point D .
Until such time I have a firm foundation to build a process on, I do not think much.

You want to fix this system, let's get some info that will help.

If there is any difficulty, or a lack of understanding, in executing what we need to do .... Please, please ask for the guidance. We are here to help ... In lots and lots of ways.

[INDENT][INDENT]the Truth, the whole Truth
[INDENT][INDENT][INDENT]and Nothing but the Truth[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-03
Righto, I agree. I'm all ears and eyes!

Tried installing the inix tool:

```
sudo apt-get install inix
[sudo] password for suoni: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inix

When I use the Software Updater (GUI) it gives me this general can't find repository, check internet:
[code]W:Failed to fetch [http://www.bandshed.net/kernels/apt/dists/trusty/main/binary-amd64/Packages](http://www.bandshed.net/kernels/apt/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://www.bandshed.net/kernels/apt/dists/trusty/main/binary-i386/Packages](http://www.bandshed.net/kernels/apt/dists/trusty/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/main/source/Sources](http://ftp.us.debian.org/debian/dists/trusty/main/source/Sources)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/non-free/source/Sources](http://ftp.us.debian.org/debian/dists/trusty/non-free/source/Sources)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/contrib/source/Sources](http://ftp.us.debian.org/debian/dists/trusty/contrib/source/Sources)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/main/binary-amd64/Packages](http://ftp.us.debian.org/debian/dists/trusty/main/binary-amd64/Packages)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/non-free/binary-amd64/Packages](http://ftp.us.debian.org/debian/dists/trusty/non-free/binary-amd64/Packages)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/contrib/binary-amd64/Packages](http://ftp.us.debian.org/debian/dists/trusty/contrib/binary-amd64/Packages)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/main/binary-i386/Packages](http://ftp.us.debian.org/debian/dists/trusty/main/binary-i386/Packages)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/non-free/binary-i386/Packages](http://ftp.us.debian.org/debian/dists/trusty/non-free/binary-i386/Packages)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://ftp.us.debian.org/debian/dists/trusty/contrib/binary-i386/Packages](http://ftp.us.debian.org/debian/dists/trusty/contrib/binary-i386/Packages)  404  Not Found [IP: 64.50.233.100 80]
, W:Failed to fetch [http://backports.debian.org/debian-backports/dists/trusty-backports/main/binary-amd64/Packages](http://backports.debian.org/debian-backports/dists/trusty-backports/main/binary-amd64/Packages)  404  Not Found [IP: 128.31.0.62 80]
, W:Failed to fetch [http://backports.debian.org/debian-backports/dists/trusty-backports/main/binary-i386/Packages](http://backports.debian.org/debian-backports/dists/trusty-backports/main/binary-i386/Packages)  404  Not Found [IP: 128.31.0.62 80]
, W:Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/trusty/main/binary-amd64/Packages](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/trusty/main/binary-i386/Packages](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/trusty/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://security.debian.org/dists/trusty/contrib/source/Sources](http://security.debian.org/dists/trusty/contrib/source/Sources)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://security.debian.org/dists/trusty/non-free/source/Sources](http://security.debian.org/dists/trusty/non-free/source/Sources)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://security.debian.org/dists/trusty/main/source/Sources](http://security.debian.org/dists/trusty/main/source/Sources)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://security.debian.org/dists/trusty/contrib/binary-amd64/Packages](http://security.debian.org/dists/trusty/contrib/binary-amd64/Packages)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://security.debian.org/dists/trusty/non-free/binary-amd64/Packages](http://security.debian.org/dists/trusty/non-free/binary-amd64/Packages)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://security.debian.org/dists/trusty/main/binary-amd64/Packages](http://security.debian.org/dists/trusty/main/binary-amd64/Packages)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://security.debian.org/dists/trusty/contrib/binary-i386/Packages](http://security.debian.org/dists/trusty/contrib/binary-i386/Packages)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://security.debian.org/dists/trusty/non-free/binary-i386/Packages](http://security.debian.org/dists/trusty/non-free/binary-i386/Packages)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://security.debian.org/dists/trusty/main/binary-i386/Packages](http://security.debian.org/dists/trusty/main/binary-i386/Packages)  404  Not Found [IP: 128.31.0.63 80]
, W:Failed to fetch [http://www.deb-multimedia.org/dists/trusty/main/binary-amd64/Packages](http://www.deb-multimedia.org/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://www.deb-multimedia.org/dists/trusty/main/binary-i386/Packages](http://www.deb-multimedia.org/dists/trusty/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://debian.scribus.net/debian/dists/trusty/main/binary-amd64/Packages](http://debian.scribus.net/debian/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://debian.scribus.net/debian/dists/trusty/main/binary-i386/Packages](http://debian.scribus.net/debian/dists/trusty/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://repos.fds-team.de/stable/debian/dists/trusty/main/binary-amd64/Packages](http://repos.fds-team.de/stable/debian/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://repos.fds-team.de/stable/debian/dists/trusty/main/binary-i386/Packages](http://repos.fds-team.de/stable/debian/dists/trusty/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/main/source/Sources](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/main/source/Sources)  Unable to fetch file, server said '/debian/dists/trusty/main/source/Sources: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/contrib/source/Sources](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/contrib/source/Sources)  Unable to fetch file, server said '/debian/dists/trusty/contrib/source/Sources: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/non-free/source/Sources](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/non-free/source/Sources)  Unable to fetch file, server said '/debian/dists/trusty/non-free/source/Sources: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/main/binary-amd64/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/main/binary-amd64/Packages)  Unable to fetch file, server said '/debian/dists/trusty/main/binary-amd64/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/contrib/binary-amd64/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/contrib/binary-amd64/Packages)  Unable to fetch file, server said '/debian/dists/trusty/contrib/binary-amd64/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/non-free/binary-amd64/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/non-free/binary-amd64/Packages)  Unable to fetch file, server said '/debian/dists/trusty/non-free/binary-amd64/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/main/binary-i386/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/main/binary-i386/Packages)  Unable to fetch file, server said '/debian/dists/trusty/main/binary-i386/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/contrib/binary-i386/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/contrib/binary-i386/Packages)  Unable to fetch file, server said '/debian/dists/trusty/contrib/binary-i386/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/non-free/binary-i386/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty/non-free/binary-i386/Packages)  Unable to fetch file, server said '/debian/dists/trusty/non-free/binary-i386/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/contrib/source/Sources](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/contrib/source/Sources)  Unable to fetch file, server said '/debian/dists/trusty-updates/contrib/source/Sources: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/non-free/source/Sources](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/non-free/source/Sources)  Unable to fetch file, server said '/debian/dists/trusty-updates/non-free/source/Sources: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/main/source/Sources](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/main/source/Sources)  Unable to fetch file, server said '/debian/dists/trusty-updates/main/source/Sources: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/contrib/binary-amd64/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/contrib/binary-amd64/Packages)  Unable to fetch file, server said '/debian/dists/trusty-updates/contrib/binary-amd64/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/non-free/binary-amd64/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/non-free/binary-amd64/Packages)  Unable to fetch file, server said '/debian/dists/trusty-updates/non-free/binary-amd64/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/main/binary-amd64/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/main/binary-amd64/Packages)  Unable to fetch file, server said '/debian/dists/trusty-updates/main/binary-amd64/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/contrib/binary-i386/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/contrib/binary-i386/Packages)  Unable to fetch file, server said '/debian/dists/trusty-updates/contrib/binary-i386/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/non-free/binary-i386/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/non-free/binary-i386/Packages)  Unable to fetch file, server said '/debian/dists/trusty-updates/non-free/binary-i386/Packages: No such file or directory  '
, W:Failed to fetch [ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/main/binary-i386/Packages](ftp://mirror.csclub.uwaterloo.ca/debian/dists/trusty-updates/main/binary-i386/Packages)  Unable to fetch file, server said '/debian/dists/trusty-updates/main/binary-i386/Packages: No such file or directory  '
, W:Failed to fetch [http://http.debian.net/debian/dists/trusty/main/binary-amd64/Packages](http://http.debian.net/debian/dists/trusty/main/binary-amd64/Packages)  404  Not Found [IP: 54.192.138.192 80]
, W:Failed to fetch [http://http.debian.net/debian/dists/trusty/contrib/binary-amd64/Packages](http://http.debian.net/debian/dists/trusty/contrib/binary-amd64/Packages)  404  Not Found [IP: 54.192.138.192 80]
, W:Failed to fetch [http://http.debian.net/debian/dists/trusty/non-free/binary-amd64/Packages](http://http.debian.net/debian/dists/trusty/non-free/binary-amd64/Packages)  404  Not Found [IP: 54.192.138.192 80]
, W:Failed to fetch [http://http.debian.net/debian/dists/trusty/main/binary-i386/Packages](http://http.debian.net/debian/dists/trusty/main/binary-i386/Packages)  404  Not Found [IP: 54.192.138.192 80]
, W:Failed to fetch [http://http.debian.net/debian/dists/trusty/contrib/binary-i386/Packages](http://http.debian.net/debian/dists/trusty/contrib/binary-i386/Packages)  404  Not Found [IP: 54.192.138.192 80]
, W:Failed to fetch [http://http.debian.net/debian/dists/trusty/non-free/binary-i386/Packages](http://http.debian.net/debian/dists/trusty/non-free/binary-i386/Packages)  404  Not Found [IP: 54.192.138.192 80]
```
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/code]

Updating through terminal sudo apt-get update / upgrade and dist-upgrade all work (at least as far as I can see)

Hope it's enugh info. Let me know. Thanks and looking forward deciphering all this stuff.

---

### Post by Bashing-om on 2015-09-03
33Nicolas33; Well, well ...

Curious and curiouser ....
What release and distro are we working with ?
Please post back the output from terminal command:
```

lsb_release -a
cat /etc/issue

```
And a typo on my part; the tool is ' inxi '.
```

sudo apt-get install inxi

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

IF this is a debian install - rather than 'buntu - .. be aware I do not have access to a debian specific system to verify all we should verify. We do proceed with an added bit of caution.

[INDENT][INDENT]but all cats are black
[INDENT][INDENT][INDENT]in the dark
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-03
LOL, last time I checked it was Ubuntu Studio. 

lsb_release -a gives me:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

cat /etc/issue gave me:
Ubuntu 14.04.3 LTS \n \l

OK, I thought I was running 14.10... That's odd.

I normally read and write typonese very well. Didn't catch the inxi. It installed correctly.

I tried the original commands you gave me a few messages ago:

lsb_release -a > stuff-txt but it gave me this again:

lsb_release -a > stuff-txt
No LSB modules are available.

Not sure if I should try the rest?

sudo apt-get update >> stuff-txt
sudo apt-get -y upgrade >> stuff-txt
sudo apt-get -f install >> stuff-txt
sudo apt-get install pastebinit
cat stuff-txt | pastebinit

Thanks again!

---

### Post by Bashing-om on 2015-09-03
33Nicolas; Hey hey !

We do make progress. 

You are to be glad, very glad that you are up on 14.04.3 vice 14.10 . Release 14.10 was a short term release and is now End_Of_Life and no longer has support. Release 14.04 is supported until April of 2019.

But whatever have you done ? Mixing debian and ubuntu studio software repositories is a guaranteed road to disaster .
We do what we can .. when we know what to do.

The requested text file:
> 
No LSB modules are available.

Expected standard output to terminal from the error checking by bash. When you open the file in a text editor, you will see that the desired info has been written to the file.
Continue with the remainder of the requested commands and post the resulting URL.

Presently the next step is to get the software sources file(s) corrected.
Show now what we are working with:
As you do not have access to a xterm - copy and paste capability  - , to make it easier and less liable to error, again resort to using our pastebin site.
```

cat -n /etc/apt/sources.list | pastebinit
tail -v -n +1 /etc/apt/sources.list.d/* | pastebinit

```
Where the result is a URL back in terminal. Pass that complete link back here .
Then we address the cause of all those '404 Not Found' advisories.
Soon now we find out what it takes to get the GUI satisfied . I am concerned what 'debian' may have done to 'buntu's xfce .

-------------------------
Of topic:
Setting here in front of this terminal sure saves a lot of gasoline. If I were not here, no telling what I would be up to .. and in the past such situations have led to stays in the cross-bar hotel. This is the preferred manner to keep me occupied. And who knows what I might learn to the good !
---------------------------------

[INDENT][INDENT]ain't nobody happy
[INDENT][INDENT][INDENT]'til the package manager is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-03
Holly crap, I remember trying to install things to make this silly M-Audio USB interface for my guitars. I think I installed a Debian app thinking it was OK. OK then, not OK, will never do that again. I hope one day we can unify structures.

Weird. talk about unstable. I typed: sudo apt-get update >> stuff-txt

It hung for a long time until I exited out. I retried and got the following.
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

sudo apt-get -y upgrade >> stuff-txt seems to have worked, but no text or output on the terminal.

sudo apt-get -f install >> stuff-txt same as above

sudo apt-get install pastebinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pastebinit is already the newest version.
The following packages were automatically installed and are no longer required:
  attr blender-data bve-route-cross-city-south bve-train-br-class-323
  bve-train-br-class-323-3dcab csound-data fonts-horai-umefont
  gcc-4.8-base:i386 hyphen-en-us libasn1-8-heimdal:i386 libasound2:i386
  libasound2-plugins:i386 libasyncns0:i386 libaudclient2 libaudcore1
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libboost-filesystem1.54.0 libboost-locale1.54.0 libboost-regex1.54.0
  libcapi20-3 libcapi20-3:i386 libcmis-0.4-4 libcups2:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libedit2:i386 libelf1:i386
  libexif12:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgcrypt11:i386 libgd3:i386 libgif4:i386
  libgl1-mesa-dri-lts-vivid:i386 libgl1-mesa-glx-lts-vivid:i386
  libglapi-mesa-lts-vivid:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libgnutls26:i386 libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-port10:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libhcrypto4-heimdal:i386 libhdb9-heimdal libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libice6:i386
  libieee1284-3:i386 libimlib2 libjack-jackd2-0:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkdc2-heimdal
  libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libllvm3.6:i386
  libltc11 libltdl7:i386 liblua5.1-0 libmowgli2 libmpg123-0:i386
  libnss-winbind libogg0:i386 libopenal1:i386 libopenimageio1.3
  liborc-0.4-0:i386 libp11-kit-gnome-keyring:i386 libp11-kit0:i386
  libpam-winbind libpciaccess0:i386 libpulse0:i386 libquvi-scripts libquvi7
  librhino-java libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386
  libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsigc++-1.2-5c2 libsm6:i386 libsmf0 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libswt-cairo-gtk-3-jni
  libswt-gtk-3-java libswt-gtk-3-jni libswt-webkit-gtk-3-jni libsynfig0
  libtasn1-6:i386 libtiff5:i386 libtxc-dxtn-s2tc0:i386 libusb-1.0-0:i386
  libv4l-0:i386 libv4lconvert0:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvpx1:i386 libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386
  libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386
  libxslt1.1:i386 libxt6:i386 libxxf86vm1:i386 linux-image-3.19.0-25-generic
  linux-image-3.19.0-25-lowlatency linux-image-extra-3.19.0-25-generic
  live-config-doc mencoder mythes-en-au ocl-icd-libopencl1:i386
  openoffice.org-hyphenation openshot-doc p11-kit-modules:i386
  python-dnspython python-mididings python-mlt python-pygoocanvas samba
  samba-dsdb-modules samba-vfs-modules synfig-examples tdb-tools transcode
  twolame winbind wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
  wine1.4-i386:i386 wine1.6 wine1.6-amd64 wine1.6-i386:i386 winetricks
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

cat stuff-txt | pastebinit
[http://paste.ubuntu.com/12268860/](http://paste.ubuntu.com/12268860/)

Impressive information. I'm not adverse to reinstalling from scratch if you think it's hopeless, but I'm enjoying the learning part. My documents are on another drive.

---

### Post by Bashing-om on 2015-09-03
33Nicolas; Yup;

Sorry about the delay in responding, life gets in the way.

Those outputs do confirm we need to look at the sources.list files, for what the update-manager is attempting to do.
And the list of 'orphaned' files is so great it is scary what is going to be removed when we get around to cleaning up the system.

So now let us look at those sources:
```

cat -n /etc/apt/sources.list | pastebinit
tail -v -n +1 /etc/apt/sources.list.d/* | pastebinit

``` As I need to be working from the source.
As there is no point yet in trying to start the GUI until we have that means to retrieve any files we may want .

Nope not at all a hopeless case, so long as we can reach a terminal we can fix it ! All it takes is time and effort. and a good internet connection -
Speaking of time, upfront will be much quicker to just re-install than to isolate/repair . But we learn nothing from that expedient; And it is not advocated. But it is an option at YOUR discretion . I am all for fixing this install .

[INDENT][INDENT]it's a thing
[INDENT][INDENT][INDENT]we can do it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2015-09-03
I don't think pastebin installed on his system.

---

### Post by Bashing-om on 2015-09-03
v3.xx; :) 

Could be that you do have a strong point !

> **v3.xx said:**
> I don't think pastebin installed on his system.
Our OP had used pastebinit once, so yeah he got it .
@ 33Nicolas; ^^

Our lives will be a lot simpler and easier using these great tools at our disposal.
That too includes using code tags for the terminal's outputs. 

Again, I say we are here to help and as well teach; If at anytime you fail to understand a directive by all and any means ask us for clarification.

[INDENT][INDENT][INDENT]when it is a mess
[INDENT][INDENT][INDENT]roll the sleeves up and
[INDENT][INDENT][INDENT][INDENT]start cleaning it up
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-09-04
@33Nicolas: PLEASE use code tags for terminal output rather than posting massive chunks of output. Neater and space saving. See the last link in my signature. Thanks. (Please advise in future bashing and others). ;)

---

### Post by 33Nicolas on 2015-09-04
Hey Bashing-Om,

No problem, I get that part about life taking over your reality part. I appreciate the info, and swear I won't corrupt a system as much as I did in the future, or less hopefully ;)

cat -n /etc/apt/sources.list | pastebinit
[http://paste.ubuntu.com/12272790/](http://paste.ubuntu.com/12272790/)

tail -v -n +1 /etc/apt/sources.list.d/* | pastebinit
[http://paste.ubuntu.com/12272806/](http://paste.ubuntu.com/12272806/)

So if I get it right, the pastebinit pipes whatever results you have, in this case to an https site? Pretty cool.

I agree. I started messing around with Linux back in the Red Hat 5.1 days. I was tough, but I kept on reinstalling and now I realized I never learned much. So let's fix it if you can. I'll enjoy the learning process.

Hey Bucky Ball, I searched your previous message signature but didn't find anything on code tags. I'll do a search in case. Tx.

> **Bashing-om said:**
> 33Nicolas33; Well, well ...

Curious and curiouser ....
What release and distro are we working with ?
Please post back the output from terminal command:
```

lsb_release -a
cat /etc/issue

```
And a typo on my part; the tool is ' inxi '.
```

sudo apt-get install inxi

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

IF this is a debian install - rather than 'buntu - .. be aware I do not have access to a debian specific system to verify all we should verify. We do proceed with an added bit of caution.[INDENT][INDENT]but all cats are black[INDENT][INDENT][INDENT]in the dark
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```

Finally got the code tag thingy!

```

---

### Post by Bashing-om on 2015-09-04
33Nicolas; Hey ->

It is all to the good. This too is a process in learning.

OK here goes the work to get the source files compatible with 'buntu.
If it is a debian source, we want to remove it - I bet there is nothing in debian that is not also available in our software repository ! Keep in mind that ubuntu is a spin off of debian .

The normal fetch control file - /etc/apt/sources.list :
Debian and 'trusty' do not correlate . debian would not be aware of 'trusty'. These sources are to be removed. Any source referencing debian.
1) Lines 1 through 37 all are of debian, remove them .

2) [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) <- very old, see no reason to maintain it . Do not see any activity in years.

3) 39 through 42 	deb [http://security.debian.org/](http://security.debian.org/) trusty contrib non-free main <- Again debian, remove them.
---------------------
The 3rd party PPA directory /etc/apt/sources.list.d/
1) [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) <- lines lines 18 through 23 are duplicates of line 10 .

2) [https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu) precise <- Software for the 12.04 (precise release) I can not access the site as I am not authorized. IF this site does not support 'trusty'; remove it also.


Once all these sources have been removed. now lets see the state of the package management system.
Once more:
```

sudo apt-get update
sudo apt-get upgrade

```

Once these run clean we then address starting the desktop.

[INDENT][INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-04
> **Bashing-om said:**
> 33Nicolas; Hey ->

I bet there is nothing in debian that is not also available in our software repository ! Keep in mind that ubuntu is a spin off of debian .



Hence the mistake I made to think it would be compatible.

Just to make sure we're on the same wavelength, do I remove all Debian reference from the Software Updater app repository. I just wanted to make sure which line numbers you are referring to. I suppose a previous email of mine. Thanks for clarify this.

---

### Post by Bashing-om on 2015-09-04
33Nicolas; Yeah ;

Sorry,  my communications skills reek some times. If it is a debian source, remove it. I expect that as the debian/trusty is not valid no harm to your system has been done.
I am using your "cat -n /etc/apt/sources.list | pastebinit and tail -v -n +1 /etc/apt/sources.list.d/* | pastebinit " as the common reference .

safety is no accident ->

[INDENT][INDENT]better safe than sorry
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-05
No problems Bashing-Om,

We are going one step further, I can see. The Updater complains about maybe having an Internet connection issue, but once it refreshes its database, it gives me updates. So it's one step further!

When update through the terminal, I get this error message:

```

W: Failed to fetch http://www.bandshed.net/kernels/apt/dists/trusty/main/binary-i386/Packages  404  Not Found

```

I don't see any "i386" in the repository list, unless it's hidden.

---

### Post by Bucky Ball on 2015-09-05
> **33Nicolas said:**
> 

```

W: Failed to fetch http://www.bandshed.net/kernels/apt/dists/trusty/main/binary-i386/Packages  404  Not Found

```



Kill the bandshed PPA as well. It is either down or dead. Then run:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If you get another dud PPA which has been manually added kill that and repeat.

---

### Post by Bashing-om on 2015-09-05
Bucky Ball; 33Nicolas33 .....

:)

---

### Post by 33Nicolas on 2015-09-05
I removed the Bandshed PPAs and updated via the terminal. 

Cool! Computer is up to date. That's out of the way? What's next? Thanks,

---

### Post by Bashing-om on 2015-09-05
33Nicolas; Hey hey !

Progress made . let's take a look and see what the system is set for starting the GUI.
Post back:
```

cat .xinitrc

```
See what then results when we start the GUI from terminal . 
Hoping all we have to do is remove the .config files and restart the system.

[INDENT][INDENT]maybe all there is to it
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-07
Hey Bashing-om,

I don't have xinitrc installed. I'm not sure if it should already be installed, or should I do it? I'd rather ask now than regret later. Tx!

---

### Post by Bashing-om on 2015-09-07
33Nicolas; Well'

No,
> 
I don't have xinitrc installed. I'm not sure if it should already be installed, or should I do it?

.xinitrc is but one way to start the GUI, I too run xfce and that is how I start my desktop environment.
I bet yours is from a display manager configuration file. I- I do not need or run a DM -

As I do not know ubuntustudio, we will have to fumble our way to find out.
What returns from terminal commands:
```

env | grep -i DESKTOP_SESSION
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
ps -ef | grep '/[X]'
cat /etc/X11/default-display-manager

```

Yeah, yeah, we could just see what happens if we attempt to start xfce4 from terminal, but I do prefer to know how the system starts the desk top .

[INDENT][INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]othertimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-09-07
> **Bashing-om said:**
> 

Yeah, yeah, we could just see what happens if we attempt to start xfce4 from terminal, but I do prefer to know how the system starts the desk top .


I'm thinking the same way as Xubuntu as Ubuntu Studio is a spin on that nowadays I believe. Don't quote me.

---

### Post by 33Nicolas on 2015-09-08
I'm all game trying to see if the foundations work. I hope I retain a fraction of everything you've done!

```

env | grep -i DESKTOP_SESSION
DESKTOP_SESSION=ubuntustudio

```

```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP

```

```

ps -ef | grep '/[X]'
root      1713  1647  9 03:48 tty7     00:10:51 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
suoni     1888  1733  0 03:48 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc


```

and finally,

```

cat /etc/X11/default-display-manager
/usr/sbin/lightdm


```

Thanks Bashing=om

Hey Bucky, where can you get the synopsis of all the Unbuntu x's. I have no idea what the difference is between Xubuntu, Ubuntu, L, K, etc. Same thing as the Unix world, different targeted audience? Tx.

---

### Post by PaulW2U on 2015-09-08
Hopefully I can answer for Bucky Ball as I don't think he's online at the moment but a good place to start is [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors).

There's a brief summary of each flavour and a link to each flavour's web-site. Hope that helps. :)

---

### Post by 33Nicolas on 2015-09-08
Thanks Paulw2u, on it!

---

### Post by Bucky Ball on 2015-09-08
> **33Nicolas said:**
> Thanks Paulw2u, on it!

+1. You can have fun and build hybrids by mix and matching various bit and pieces you like. I generally go for the [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") and then add xfce4, the desktop environment from Xubuntu which is light and fast, and then only the software I need/want. No bloat and a speedster. :)

I'd been using Xubuntu solely for about four years before I started using the minimal install for every install I did, included for other people. I knew by then exactly what suited me. I need a stable workhorse for my main system and it don't break. I figure the fewer  moving parts and all that ...

Anyhow, apologies. Getting rather off-topic. :D

---

### Post by Bashing-om on 2015-09-08
33Nicolas; Hummmm ....

Sorta floundering here, as this is my 1st encounter with 'lightdm' as a Display Manager in a xfce4 environment. Not a thing inherently wrong with this arrangement, just never seen it before and gonna be a learning experience.
So let's "look and see". 
Is the :
> 
cat /etc/X11/default-display-manager
/usr/sbin/lightdm

THE control file we are seeking ?
Post back :
```

file /usr/sbin/lightdm

```
IF it comes back that it is reported as an ASCII text executable file, we take a look at it and see how the desktop is started.
```

cat /usr/sbin/lightdm

```

I am prepared to be totally surprised at how the Desk Top is started.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-08
Makes perfect sense. I'm a green transportation efficiency "expert" of some sort, so I can relate to that philosophy very well. Thinkin' about it... thinkin' about it.

That's something I guess I still don't grasp coming from a Mac world is the interaction between a Display Manager and a Desktop Environment. I understand the superficial differences, but it seems mixing and matching is not really recommended. Like I said, I'm not hungup on XFCE. If there is something better. Years ago there was the Enlightment desktop system. That was great, simple, elegant and pure.

In the meantime...

```

file /usr/sbin/lightdm
/usr/sbin/lightdm: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=239630bb43990db7c81ed0010774fbac547a4794, stripped

```

```

cat /usr/sbin/lightdm

```

So if you are ```
I am prepared to be totally surprised at how the Desk Top is started.
```I wonder what I am, ravelling and delighting in being lost and learning?

---

### Post by Bashing-om on 2015-09-08
33Nicolas; Welp;

That my friend was a road that led to nowhere... " /usr/sbin/lightdm" is a binary executable - not the control file we seek.
What I am looking to find ( point A) is the file that leads us to point D (/etc/X11/xinit/xserverrc) .

How about we take an educated guess and see if it is:
```

cat /etc/lightdm/lightdm.conf

```
------------------
Off topic:
> 
That's something I guess I still don't grasp coming from a Mac world is the interaction between a Display Manager and a Desktop Environment. I understand the superficial differences, but it seems mixing and matching is not really recommended. Like I said, I'm not hungup on XFCE. If there is something better. Years ago there was the Enlightment desktop system. That was great, simple, elegant and pure.

The display manager ( when used ) has it's fingers in a number of places and it does control starting and managing the desktop ( along with a whole bunch of other interactive files). and the ability to mix and match is what makes linux such a great operating system. YOU can have it exactly your way. " great, simple, elegant ( can be ) and pure " is how I feel about xfce4 . I am a simple man and I work real hard to keep it simple. xfce4 meets my criteria for everything I want in a Desk Top environment; where I personally do most of my computing from the (C)ommand (L)ine (I)interface .
--------------------------
Our goal continues to learn how the Desktop is started in the ubuntu studio operating system. We now know it is lightdm that is the display manager. Now it is but trying to find where it is started and what file actually activates the Desk Top . 

And Yes we could take a stab at starting it and see what errors the system reports, but in this instance I really do want to know the where and how .

We can do that !

[INDENT][INDENT][INDENT]it is a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-08
Excellent. This is what it returned:

```

cat /etc/lightdm/lightdm.conf
[SeatDefaults]
autologin-guest=false
autologin-user=suoni
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

Makes sense the display manager would have its tentacles between hardware and software, while the desktop manager would be more organizational. Should have those those command promts.

---

### Post by Bashing-om on 2015-09-08
33Nicolas; Welp:

Autologin sorta complicates the matter, Still do not know what is starting the desktop.
For lack of a better thing, let's start it and see what results.
From the terminal execute the command:
```

sudo service lightdm start

```

And let's see what the system screams and hollers about.

[INDENT][INDENT]back up 4 yards and punt
[/INDENT][/INDENT]

------------
done for this session, Will pick this back up on my morrow.

---

### Post by 33Nicolas on 2015-09-09
After reading what you wrote, I realize that there is a dialogue box that asks me if I want to restore the last session. I've never seen it before, but assumed it was one of those programs I installed. So I no longer have access to the right-clicking features on the desktop, but instead have a different dialogue box.

Hope that makes sense.

```

sudo service lightdm start
[sudo] password for xxx: 
start: Job is already running: lightdm

```

I do update the computer via terminal everyday. Hope that doesn't complicate things.

---

### Post by v3.xx on 2015-09-09
@Bashing

Just thinking out loud.  Would "dpkg --reconfigure" the DM be a good option?

---

### Post by 33Nicolas on 2015-09-09
Synaptic isn't able to repair broken dependencies. I'm sure it influences a few things also.

---

### Post by Bashing-om on 2015-09-09
33Nicolas; Morning;

It is rare that I get stonewalled by my own ignorance. This seems to be the case here.
Believe me I will continue to seek to learn.

In the meantime v3.xx's suggestion has merit and will in the least garner us some additional info.
go to a text terminal using alt-ctrl-F1
Stop the Xserver:
```

sudo service lightdm stop

```
reset lightdm :
```

sudo dpkg-reconfigure lightdm

```
Restart :
```

sudo service lightdm start

```
Reboot and let's see what happens, now might be a good time to read the logs and see what the system reports .

[INDENT][INDENT]if I know better
[INDENT][INDENT][INDENT]I would do better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-09
I guess this is not the best time to say I use an Apple keyboard?

```

sudo service lightdm stop

```

Stopped the desktop manager and eventually I got to a command prompt that took over the entire page. Unfortunately, I forgot the following command you wanted me to take, so I exited out of it and rebooted. When I tried a second time, i.e. stop lightdm, it got me to a blank screen with a blinking orange thick cursor.

I understand the sequence you are trying to do and will give it another shot later.

---

### Post by Bashing-om on 2015-09-09
33Nicolas; Hummm ...

Something here just does not feel right.
How are you activating a terminal ?
Maybe X is never started and "stopping lightdm" is not required ?

I say
[INDENT][INDENT] gazing into the crystal ball
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-10
The terminal is activated clicking on the top left hand drop down start menu, or from the dock, below. If you;re asking how did that terminal session start? No idea. I don't know if X is started. It's like I have a very incapacitated desktop manager.

---

### Post by Bashing-om on 2015-09-10
33Nicolas; K;

Tell ya what, let's take a different tack so that we know that X is not started and see what we can do about starting it. See what errors the system then reports.
By the way .. I do now have a glimmer of how the desktop is starting. We may return to these scripts at a later time.

For now let's try and start the GUI :
Reboot the system, as soon as the bios screen clears depress the right shift key -> grub boot menu; press the 'e' key for edit mode -> boot parameters screen;
Arrow down to the line starting with linux, and arrow across to the terms "quiet splash", replace these terms and all after with the term text . Key combo ctl+x to continue the boot process to TTY1.
Login here at this terminal with your credentials ( no response to the screen when pass word is entered - enter password blindly and hit the enter key )

OK now we have a stand alone terminal .. X has not to this time been started.
Now let's try and reconfigure 'lightdm'
```

sudo dpkg-reconfigure lightdm

```
which launches a wizard. When you come out the other side:
```

sudo service lightdm start

```
Which will launch the GUI in TTY7. To return to the terminal key combo ctl+alt+F1. 

If there is no GUI and you need to restart the system :
```

sudo shutdown -r now

```
to reboot.
To shut the system down completely and turn it off:
```

sudo shutdown -h now

```

Depending on what happens is what we do ... I have in mind that this could also be a graphics driver issue !

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-11
Wow, that was an interesting ride. It got me to the prompt. Once there, I was able to do everything you said, however, I souldn't see the first 3 lines. I removed the Linux part.

Then I tried to restart X and it spit out a long and lengthy error message ending with not sure if X has started, waiting for X shutdown. I apologize. I had to leave and I thought once I would restart I would get to the same error.

Now, ```

sudo dpkg-reconfigure lightdm

```

Nothing happens. Back to prompt.

```

sudo service lightdm start
start: Job is already running: lightdm

```

Not sure if I follow here:

> Which will launch the GUI in TTY7. To return to the terminal key combo ctl+alt+F1.


Can you clarify? Tx

---

### Post by Bucky Ball on 2015-09-11
When you get that it is already running, hold control+alt and hit F7. There should be a desktop there. If not, back to it. :)

---

### Post by Bashing-om on 2015-09-11
33Nicolas; Hey !

Maybe all to the good .
What now happens when you boot the system normally ? Can you get to your desktop ?
Yep; once lightdm is started, starting it again will get the advisory "start: Job is already running: lightdm ".
If one is to restart lighdm .. then the command becomes:
```

sudo service lightdm restart

```

as the switching between "terminals" .. well .. in tty7 is the default location of the GUI, there are many other terminals available. By default there are 8 terminals, linux is a multi-process multi-user operating system. If one wants there is no limit to the number of terminals one can make - memory permitting.
For our case the GUI is in TTY7, when we start a terminal from grub we start in the 1st terminal, TTY1. One can switch the terminals with ctl+alt+fX, where 'X" is the terminal number you want to go to. ( once X is running to return to the X (GUI) terminal alt+F7 is all that is needed) .

Try it and see ! Once you know what you are doing, one can even have additional GUI in other terminals . I sometimes start an additional GUI in terminal 8 . My set up .. in terminal 7 is the GUI and here I have 4 work spaces ( think it is a max of 20 that one can have ), in terminal 8 I have an additional 4 work spaces - all 8 are doing some things . As I have started the GUI from terminal1 it is running as a child of terminal1 and as I then do not have access to a command line in 1, I activate as many additional terminals as I need ( ctl+alt+F2-6) . Keep in mind in the GUI's I do have terminal emulators active !

linux is an amazing 
[INDENT][INDENT][INDENT]piece of programming[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-12
Tx Bucky Ball, I will do next time. Learning a lot here. Fun stuff. Wonder how much I will retain ;)

Wow, you always here how smart the command prompt is, but you never realize it until you start to flex its muscles beyond a few file look ups.

OK, now that I know how to do this, more or less, to answer your questions.

> 
What now happens when you boot the system normally ? Can you get to your desktop ?


I can see the desktop, but it is stuck on the default image background. When I right-click, I get a dialogue box I've never seen before, but with much less choices then when I had before. It also looks different (the dialogue box) then what I'm accustomed to see on the default desktop.

Thanks,

---

### Post by Bashing-om on 2015-09-14
33Nicolas; Hey !

Seems we have a config issue with the desktop. As you can reach a desktop I no longer think of this as a driver issue.
Let's verify that the system it's self is intact.
Boot to the login screen, can you activate a console with ctl+alt+F1 ?
In this console, let's set up to revert this desk top to defaults ->

What results from terminal commands:
```

ls -al ~/.config/xfce4/panel/
ls -al ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
ls -al /etc/xdg/xfce4

```

As I do not know ubuntustudio-xfce-lightdm, let's compare yours to mine ( standard xfce4) and make sure the procedure I would do in my xfce4 to revert to defaults ( I have done this) is the same as in ubuntustudio.

[INDENT]safety is no accident
[INDENT][INDENT][INDENT][INDENT]look before we leap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-16
OK, so the reboot and Control Alt F1 didn't do anything at any moment.

Although I'm assuming I should do the following after the successful first step, which didn't happen for me.

```

ls -al ~/.config/xfce4/panel/
total 36
drwxrwxr-x 8 suoni suoni 4096 Sep 16 12:14 .
drwxrwxr-x 7 suoni suoni 4096 Sep 14 17:50 ..
drwx------ 2 suoni suoni 4096 Aug 23 13:11 launcher-13
drwx------ 2 suoni suoni 4096 Aug 23 09:16 launcher-15
drwx------ 2 suoni suoni 4096 Aug 23 09:17 launcher-16
drwx------ 2 suoni suoni 4096 Aug 23 09:17 launcher-17
drwx------ 2 suoni suoni 4096 Aug 23 09:17 launcher-18
drwx------ 2 suoni suoni 4096 Aug 23 09:17 launcher-19
-rw-rw-r-- 1 suoni suoni  142 Sep 16 12:14 xfce4-orageclock-plugin-7.rc
suoni@SuoniStudio:~$ ls -al ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
-rw-rw-r-- 1 suoni suoni 8795 Sep 16 12:32 /home/suoni/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
suoni@SuoniStudio:~$ ls -al /etc/xdg/xfce4

```

Aug 23 might have been the time when I fiddle with Numix and all of these things.

---

### Post by Bashing-om on 2015-09-16
33Nicolas; Ouch !

Now I do have some reservations .
You do not have ? :
```

sysop@1404mini:~$ ls -al /etc/xdg/xfce4
total 32
drwxr-xr-x 4 root root 4096 Mar 18 11:56 .
drwxr-xr-x 7 root root 4096 Jul  6  2014 ..
-rw-r--r-- 1 root root  242 Mar  4  2013 helpers.rc
drwxr-xr-x 2 root root 4096 Jul  6  2014 panel
drwxr-xr-x 3 root root 4096 May 19  2013 xfconf
-rw-r--r-- 1 root root  221 Nov  9  2012 Xft.xrdb
-rwxr-xr-x 1 root root 5827 Mar 20  2014 xinitrc
sysop@1404mini:~$ 

```

And Why is :
> 
suoni@SuoniStudio:~$ ls -al ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
-rw-rw-r-- 1 suoni suoni [color=red]8795[/color] Sep 16 12:32 /home/suoni/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

so much larger than mine ? - maybe you have a very busy desktop ! -
```

sysop@1404mini:~$ ls -al ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
-rw-rw-r-- 1 sysop sysop [color=blue]2230[/color] Sep 14 14:55 /home/sysop/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
sysop@1404mini:~$

``` 

Sure would be nice if we had this cheap insurance to fall back on ; if there were any problem in reverting the desktop to the defaults....

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-16
Hum, do you suggest a reinstall, or is there a way to reinstall only XCFE?

---

### Post by Bashing-om on 2015-09-16
33Nicolas; No No !

A (Re-)install of the operating system is the means of last resort, that nuclear solution.
And nor do I see at this point re-installing xfce as a requiremnet.

What I am concerned about is if we revert to the defaults, then you loose all the changes and additions you have made. A lot of time and effort to re-do.

I would prefer to take the time to find the particular fault and correct it. The operative word here is time.

To that end of hunting up the fault, let's look at the log files and see what is reported.
Boot to TTY1 from the grub boot menu.
Once logged in from the terminal execute terminal commands:
```

sudo service lightdm start
cat /var/log/Xorg.0.log
cat ~/.xsession-errors

```
Any errors back in terminal from the "start lightdm" command ?

If we do not look, we do not learn
[INDENT][INDENT]if we do not learn, we do not know
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-17
Hey Bashing Om,

[HTML]
if we revert to the defaults, then you loose all the changes and additions you have made.
[/HTML]

I don't think I did much, but maybe don't know the extent of what I did.

The other problem is that I don't have a regular keyboard, but an Apple. It doesn't look like the F1 key combo works. I can't get into the Grub menu, unless it's something I can access from a regular session?

If I ```
 cat /var/log/Xorg.0.log 
``` I get a lot of feedback, but not sure if you want me to post it here.

Thanks!

---

### Post by Bashing-om on 2015-09-17
33Nicolas; Morning.

Well we need to find a means to read those logs, and "we" have one .
Reboot the system, as soon as the bios screen clears depress and hold the right shift key -> grub boot menu.
With the latest ubuntu kernel selected, press the 'e' key for edit mode -> boot parameters screen. In this screen arrow down to the line starting with linux, and arrow across to the terms "quiet splash" replace thesse terms and all after with the term "text" with out the quotes. key combo ctl+x to continue the boot process to TTY1 .
Log in here with your credentials.
Once logged in install our pastebinit tool .
```

sudo apt-get install pastebinit

```

Now we have a means to see those log files.
do:
```

sudo service lightdm start
cat /var/log/Xorg.0.log | pastebinit
cat ~/.xsession-errors | pastebinit

```
the result is URL's back to your terminal. Pass those complete links back to this thread and we can access these files to read them. Maybe get an idea of what is not taking place.
Considering what might be, we can think about reverting the desktop back to defaults - with the caveat that we do not have backups in the event of a catastrophic failure.

[INDENT][INDENT]more than one way
[INDENT][INDENT][INDENT]to skin a cat
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by flocculant on 2015-09-18
Have you tried removing the configs ? 

Log out to vt1, login there and then remove. Then log back in on vt7 and see where you are.

rm -r ~/.config/xfce4

Also, though not something I've advocated often in the last 7 or 8 years, after 2 weeks perhaps it's time to make sure you have _good backups of your data_ and take the 20 minutes or so to reinstall. You can just get on with using the system then ...

---

### Post by 33Nicolas on 2015-09-18
Hi Flocculent,

I'll look into it after I try the previous method. Thanks.

As far as back ups, no problem here. My data is on another drive, OS on one, data on another, backed up locally and stored on my local network.

Weird and weirder.

I got to the Grub screen, pressed e and go to the boot parameter screen. I remember having gone there previously as you suggested and replace that quiet with text, however, I might have left the quotes in. However, I couldn't find it this time. When I pressed Crt X, it booted back into a regular session.

---

### Post by Bashing-om on 2015-09-19
33Nicolas; Ouch !

All I can advise is reboot and try again. reboot gracefully !
If your setup supports it key combo ctl+alt+delete may be effective.
Then there is the magic sys-rq sequence to control the system resources.
key combo alt + SysRq + r s e i u b - slowly - For systems without a SysRq label on the key, it's the Prt Scr key.
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)
[http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)

IF you can not reach a terminal, we then must boot up a liveDVD(USB) and (RE-)install grub - after a file system check completes successfully .

I do hope you get satisfaction progressing on this learning curve; remember if the frustration level becomes excessive one can always back up personal data and (RE-)install. In a matter of minutes your world is all rosy again. But we learn little from taking that expedient .

Me, I am all for what we can learn.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-09-21
Thanks Bashing Om, will do, but I will be away from the computer for three weeks. Do you mind if we continue middle of Oct.? Thanks for your help. Looking forward figuring it out.

---

### Post by Bashing-om on 2015-09-21
33Nicolas; Hey !

Sure, we work at this in your pace. I will still be here in 3 weeks, Lord willing and my graphic's card holds up .

Just post back in this thread when you are ready to continue.

[INDENT][INDENT]A time and a place
[INDENT][INDENT][INDENT]for all things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-15
Hey Bashing-Om, I'm back. I see an Ubuntu upgrade. I was wondering if I should upgrade now?

Thanks and happy to be back.

---

### Post by Bashing-om on 2015-10-15
33Nicolas; Welp;

I am not a proponent of updating/upgrading a broke system. May just make the problem worse.

Presently, what are you able to boot to ?

[INDENT][INDENT]gots to have the tools to work with
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-18
33Nicolas; Hey ...

Status ? Are we still working this issue ?

[INDENT][INDENT]holding my thoughts
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-18
My apologies, I'm still jetlagged and not all there. Thanks for your patience.

I can boot up but get greeted with a dialog box I've never seen before. I'm pasting the picture I took here:

[ATTACH=CONFIG]265029[/ATTACH]

After that, I'm back on the desktop, as normal.

I have something called Adaptor Online, which helped with the suspend, hybernate and shut down features, but I can remove it.

There you go. Thanks for your help.

---

### Post by Bashing-om on 2015-10-18
33Nicolas; Uh Huh ..

I too have never encountered nor aware if it's ( the dialog box) existence . Do not have a clue.
Some ad-on that I am unaware of ?

I take it thought that in all other respects the desktop is functional ?

[INDENT][INDENT]a know-it-all
[INDENT][INDENT][INDENT]I am not
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-18
It came about when I was installing Debian apps. Oh, how I regret, but enjoying the learning curve. The last updates (security and drivers) have crippled my video card to a lowly 1024x768, but short of that, working, computer is :)

I just remember where it all started. It was when I started installing Numix features.

---

### Post by Bashing-om on 2015-10-18
33Nicolas; Yuk ! Yukkie !!

I hate to say it ... mixing distribution repositories is a sure path to disaster, It is time now to decide on which distro you prefer and (RE-)install.
We will never be able to determine all that may have changed/be different in the supporting libraries and config files . There will always  be that uncertainty of update failure and where the fault lies !

[INDENT][INDENT]there just is not a nice way
[INDENT][INDENT][INDENT]to say it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-18
Agreed. I'm going to stick with Ubuntu Studio so far and stay in the Ubuntu family. If I start to think about distros, I'll get too tempted.

Do you think it's gotten to far into the system? I'm not sure what to do next. Thanks.

---

### Post by Bashing-om on 2015-10-19
33Nicolas; Welp;

> 
Do you think it's gotten to far into the system?

That is hard to say ... It is your time and effort. I am more than willing to see what we can do to revert back to pure 'buntu - but I have my doubts.
I am willing to take this opportunity to learn also.
We can start with the sources you are fetching and go from there .
Post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Maybe just maybe "debian" will support a ppa-purge in ubuntu ??

[INDENT][INDENT]hey,
it is a thought
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-19
Thanks Bashing-Om, I certainly appreciate the time and effort. Let's plough at it for a week and see if we're.. erh, I mean you're making any headway. I feel like a kid in front of a Ferrari, but can't drive it properly.

[HTML]
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu-Studio 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main multiverse restricted universe
     2    #SQUEEZE-CANADIAN-MIRROR
     3    
     4    #SQUEEZE-BACKPORTS
     5    
     6    #Wheezy/Testing
     7    
     8    #DEBIAN MULTIMEDIA
     9    
    10    #SCRIBUS
    11    
    12    #AV LINUX KERNEL REPO
    13    
    14    #WXWidgets
    15    # deb http://apt.wxwidgets.org/ squeeze-wx main
    16    # deb-src http://apt.wxwidgets.org/ squeeze-wx main
    17    
    18    
    19    
    20    
    21    
    22    
    23    
    24    
    25    
    26    
    27    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    28    # newer versions of the distribution.
    29    deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted multiverse
    30    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted multiverse
    31    
    32    ## Major bug fix updates produced after the final release of the
    33    ## distribution.
    34    
    35    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    36    ## team. Also, please note that software in universe WILL NOT receive any
    37    ## review or updates from the Ubuntu security team.
    38    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    39    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    40    
    41    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    42    ## team, and may not be under a free licence. Please satisfy yourself as to 
    43    ## your rights to use the software. Also, please note that software in 
    44    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    45    ## security team.
    46    
    47    ## N.B. software from this repository may not have been tested as
    48    ## extensively as that contained in the main release, although it includes
    49    ## newer versions of some applications which may provide useful features.
    50    ## Also, please note that software in backports WILL NOT receive any review
    51    ## or updates from the Ubuntu security team.
    52    
    53    deb http://security.ubuntu.com/ubuntu trusty-security main restricted multiverse
    54    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted multiverse
    55    deb http://security.ubuntu.com/ubuntu trusty-security universe
    56    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    57    
    58    ## Uncomment the following two lines to add software from Canonical's
    59    ## 'partner' repository.
    60    ## This software is not part of Ubuntu, but is offered by Canonical and the
    61    ## respective vendors as a service to Ubuntu users.
    62    deb http://archive.canonical.com/ubuntu trusty partner
    63    deb-src http://archive.canonical.com/ubuntu trusty partner
    64    
    65    ## Uncomment the following two lines to add software from Ubuntu's
    66    ## 'extras' repository.
    67    ## This software is not part of Ubuntu, but is offered by third-party
    68    ## developers who want to ship their latest software.
    69    deb http://extras.ubuntu.com/ubuntu trusty main
    70    deb-src http://extras.ubuntu.com/ubuntu trusty main
    71    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe main restricted multiverse
    72    deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed universe main restricted multiverse

[/HTML]

and 

[HTML]
tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-4-trusty.list <==

==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-4-trusty.list.save <==

==> /etc/apt/sources.list.d/libreoffice-libreoffice-5-0-trusty.list <==
deb http://ppa.launchpad.net/libreoffice/libreoffice-5-0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-0/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-libreoffice-5-0-trusty.list.save <==
deb http://ppa.launchpad.net/libreoffice/libreoffice-5-0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-0/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.save <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

==> /etc/apt/sources.list.d/noobslab-deepin-sc-trusty.list <==
deb http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main

==> /etc/apt/sources.list.d/numix-ppa-trusty.list <==
deb http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/numix-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf

[/HTML]

Seems to see ppa.

---

### Post by Bashing-om on 2015-10-19
33Nicolas; Well ..

Maybe things are not as bad as I feared, maybe;
Please explain:
> 
# deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) squeeze-wx main
16    # deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) squeeze-wx main

from the sources.list file . I do not see this as a valid format for ubuntu . Has any damage been done is the question from these sources .
I hold this link as a reference to what we are doing:
[https://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu](https://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu)

And next is "numix-ppa-" is this:
> 
Seems to see ppa.

in respect to that PPA as THE reference ?

[INDENT][INDENT]I think
clean things up
make the package manager happy
[INDENT][INDENT][INDENT]then see where we go from a clean slate 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-19
Bashing-Om, not sure I can explain:

[HTML]# deb http://apt.wxwidgets.org/ squeeze-wx main
16    # deb-src http://apt.wxwidgets.org/ squeeze-wx main[/HTML]

Are you asking me how this above got unto my computer? Then, I don't know how to explain that short of I must have tried to install a widget of some sort. I usually don't use widget, especially on a limited resource computer like this one. I can remove all widgets if that helps.

I don't understand the following:

[HTML]in respect to that PPA as THE reference ?[/HTML]

At this stage it's probably more a question of lingo than anything. I don't understand which THE reference you are mentioning here. I wrote it seems to see PPAs, because I saw it in the terminal.

Best I interpret nothing :/

---

### Post by Bashing-om on 2015-10-19
33Nicolas; Well ..

Let's not bother over spilled beans . Start again and know what we have.
Let's see what we are going to do with the sources, if anything.
Run :
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install

```
post those results and let's see where our focus of attention gets directed to .

When we come out swinging
[INDENT][INDENT]nothing like a firm foundation
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-20
Here we go. I haven't updated the computer in two days via the update manager. Here is what got updated with sudo apt update:

[HTML]sudo apt update
[sudo] password for suoni: 
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Ign http://dl.google.com stable InRelease                                      
Get:2 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Ign http://archive.canonical.com trusty InRelease                              
Get:3 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://archive.canonical.com trusty Release.gpg [933 B]                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Get:6 http://dl.google.com stable/main amd64 Packages [1,209 B]                
Get:7 http://us.archive.ubuntu.com trusty-proposed InRelease [212 kB]          
Get:8 http://archive.canonical.com trusty Release [9,359 B]                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Get:9 http://dl.google.com stable/main i386 Packages [1,212 B]                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:10 http://security.ubuntu.com trusty-security/main Sources [97.6 kB]       
Get:11 http://archive.canonical.com trusty/partner Sources [10.0 kB]           
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:12 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:13 http://archive.canonical.com trusty/partner amd64 Packages [5,637 B]    
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:14 http://archive.canonical.com trusty/partner i386 Packages [6,301 B]     
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net precise InRelease                        
Get:15 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [323 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit https://private-ppa.launchpad.net precise Release                          
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.canonical.com trusty/partner Translation-en                 
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:16 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [635 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:17 http://ppa.launchpad.net trusty/main amd64 Packages [3,422 B]           
Get:18 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B] 
Get:19 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B] 
Get:20 http://ppa.launchpad.net trusty/main i386 Packages [3,422 B]            
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Get:21 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]   
Get:22 http://ppa.launchpad.net trusty/main Translation-en [1,579 B]           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:23 http://security.ubuntu.com trusty-security/main amd64 Packages [356 kB] 
Get:24 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:25 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:26 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [325 kB]
Get:27 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [616 kB] 
Get:28 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:29 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:30 http://us.archive.ubuntu.com trusty-updates/main Translation-en [308 kB]
Get:31 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:32 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,569 B]
Get:33 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [170 kB]
Get:34 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Get:35 http://us.archive.ubuntu.com trusty-proposed/universe amd64 Packages [28.8 kB]
Get:36 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Get:37 http://us.archive.ubuntu.com trusty-proposed/main amd64 Packages [135 kB]
Get:38 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:39 http://us.archive.ubuntu.com trusty-proposed/restricted amd64 Packages [28 B]
Get:40 http://us.archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [28 B]
Get:41 http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages [28.8 kB]
Get:42 http://us.archive.ubuntu.com trusty-proposed/main i386 Packages [132 kB]
Get:43 http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Get:44 http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:45 http://us.archive.ubuntu.com trusty-proposed/main Translation-en [53.8 kB]
Get:46 http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Get:47 http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en [28 B]
Get:48 http://us.archive.ubuntu.com trusty-proposed/universe Translation-en [22.5 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages            
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages            
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages             
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages              
Hit http://us.archive.ubuntu.com trusty/main Translation-en                 
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Get:49 http://security.ubuntu.com trusty-security/main i386 Packages [338 kB]  
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Get:50 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Get:51 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:52 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:53 http://security.ubuntu.com trusty-security/main Translation-en [194 kB] 
Get:54 http://security.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Get:55 http://security.ubuntu.com trusty-security/restricted Translation-en [3,076 B]
Get:56 http://security.ubuntu.com trusty-security/universe Translation-en [68.3 kB]
Fetched 4,603 kB in 49s (92.4 kB/s)                                            
Reading package lists... Done

[/HTML]

sudo apt upgrade:

[HTML]sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  attr blender-data bve-route-cross-city-south bve-train-br-class-323
  bve-train-br-class-323-3dcab csound-data fonts-horai-umefont hyphen-en-us
  libatk-bridge2.0-0:i386 libatspi2.0-0:i386 libaudclient2 libaudcore1
  libboost-filesystem1.54.0 libboost-locale1.54.0 libboost-regex1.54.0
  libcairo-gobject2:i386 libcapi20-3 libcapi20-3:i386 libcmis-0.4-4
  libcolord1:i386 libdbusmenu-gtk3-4:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libedit2:i386 libelf1:i386
  libexif12:i386 libgd3:i386 libgif4:i386 libgl1-mesa-dri-lts-vivid:i386
  libgl1-mesa-glx-lts-vivid:i386 libglapi-mesa-lts-vivid:i386
  libglu1-mesa:i386 libgphoto2-6:i386 libgphoto2-port10:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk-3-0:i386
  libhdb9-heimdal libice6:i386 libieee1284-3:i386 libimlib2 libkdc2-heimdal
  liblcms2-2:i386 libllvm3.6:i386 libltc11 libltdl7:i386 liblua5.1-0
  libmowgli2 libmpg123-0:i386 libnss-winbind libopenal1:i386 libopenimageio1.3
  liborc-0.4-0:i386 libp11-kit-gnome-keyring:i386 libpam-winbind
  libpciaccess0:i386 libquvi-scripts libquvi7 librhino-java libsane:i386
  libsigc++-1.2-5c2 libsm6:i386 libsmf0 libswt-cairo-gtk-3-jni
  libswt-gtk-3-java libswt-gtk-3-jni libswt-webkit-gtk-3-jni libsynfig0
  libtxc-dxtn-s2tc0:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386
  libvpx1:i386 libwayland-client0:i386 libwayland-cursor0:i386
  libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-sync1:i386 libxkbcommon0:i386 libxml2:i386
  libxpm4:i386 libxshmfence1:i386 libxslt1.1:i386 libxt6:i386 libxxf86vm1:i386
  linux-image-3.13.0-63-lowlatency linux-image-3.19.0-25-generic
  linux-image-3.19.0-25-lowlatency linux-image-extra-3.19.0-25-generic
  live-config-doc mencoder mythes-en-au ocl-icd-libopencl1:i386
  openoffice.org-hyphenation openshot-doc p11-kit-modules:i386
  python-dnspython python-mididings python-mlt python-pygoocanvas samba
  samba-dsdb-modules samba-vfs-modules synfig-examples tdb-tools transcode
  twolame winbind wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
  wine1.4-i386:i386 wine1.6 wine1.6-amd64 wine1.6-i386:i386 winetricks
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  libav-tools libavdevice53 libavfilter3 libavformat54
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flash-properties-kde adobe-flashplugin
  libminiupnpc8 lsb-base lsb-release oxideqt-codecs-extra tzdata tzdata-java
9 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 11.5 MB of archives.
After this operation, 23.6 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main lsb-base all 4.1+Debian11ubuntu6.1 [13.0 kB]
Get:2 http://archive.canonical.com/ubuntu/ trusty/partner adobe-flash-properties-kde amd64 1:20151016.2-0trusty1 [146 kB]
Get:3 http://security.ubuntu.com/ubuntu/ trusty-security/main tzdata-java all 2015g-0ubuntu0.14.04 [69.6 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main lsb-release all 4.1+Debian11ubuntu6.1 [11.5 kB]
Get:5 http://security.ubuntu.com/ubuntu/ trusty-security/main tzdata all 2015g-0ubuntu0.14.04 [164 kB]
Get:6 http://archive.canonical.com/ubuntu/ trusty/partner adobe-flash-properties-gtk amd64 1:20151016.2-0trusty1 [113 kB]
Get:7 http://archive.canonical.com/ubuntu/ trusty/partner adobe-flashplugin amd64 1:20151016.2-0trusty1 [10.1 MB]
Get:8 http://security.ubuntu.com/ubuntu/ trusty-security/main libminiupnpc8 amd64 1.6-3ubuntu2.14.04.2 [20.3 kB]
Get:9 http://security.ubuntu.com/ubuntu/ trusty-security/main oxideqt-codecs-extra amd64 1.10.3-0ubuntu0.14.04.1 [866 kB]
Fetched 11.5 MB in 7s (1,641 kB/s)                                             
Preconfiguring packages ...
(Reading database ... 658767 files and directories currently installed.)
Preparing to unpack .../lsb-base_4.1+Debian11ubuntu6.1_all.deb ...
Unpacking lsb-base (4.1+Debian11ubuntu6.1) over (4.1+Debian11ubuntu6) ...
Setting up lsb-base (4.1+Debian11ubuntu6.1) ...
(Reading database ... 658768 files and directories currently installed.)
Preparing to unpack .../tzdata-java_2015g-0ubuntu0.14.04_all.deb ...
Unpacking tzdata-java (2015g-0ubuntu0.14.04) over (2015f-0ubuntu0.14.04) ...
Preparing to unpack .../tzdata_2015g-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2015g-0ubuntu0.14.04) over (2015f-0ubuntu0.14.04) ...
Setting up tzdata (2015g-0ubuntu0.14.04) ...

Current default time zone: 'America/Los_Angeles'
Local time is now:      Tue Oct 20 18:26:36 PDT 2015.
Universal Time is now:  Wed Oct 21 01:26:36 UTC 2015.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 658772 files and directories currently installed.)
Preparing to unpack .../lsb-release_4.1+Debian11ubuntu6.1_all.deb ...
Unpacking lsb-release (4.1+Debian11ubuntu6.1) over (4.1+Debian11ubuntu6) ...
Preparing to unpack .../adobe-flash-properties-kde_1%3a20151016.2-0trusty1_amd64.deb ...
Unpacking adobe-flash-properties-kde (1:20151016.2-0trusty1) over (1:20151013.1-0trusty1) ...
Preparing to unpack .../adobe-flash-properties-gtk_1%3a20151016.2-0trusty1_amd64.deb ...
Unpacking adobe-flash-properties-gtk (1:20151016.2-0trusty1) over (1:20151013.1-0trusty1) ...
Preparing to unpack .../adobe-flashplugin_1%3a20151016.2-0trusty1_amd64.deb ...
Unpacking adobe-flashplugin (1:20151016.2-0trusty1) over (1:20151013.1-0trusty1) ...
Preparing to unpack .../libminiupnpc8_1.6-3ubuntu2.14.04.2_amd64.deb ...
Unpacking libminiupnpc8 (1.6-3ubuntu2.14.04.2) over (1.6-3ubuntu2.14.04.1) ...
Preparing to unpack .../oxideqt-codecs-extra_1.10.3-0ubuntu0.14.04.1_amd64.deb ...
Unpacking oxideqt-codecs-extra:amd64 (1.10.3-0ubuntu0.14.04.1) over (1.9.5-0ubuntu0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up tzdata-java (2015g-0ubuntu0.14.04) ...
Setting up lsb-release (4.1+Debian11ubuntu6.1) ...
Setting up adobe-flashplugin (1:20151016.2-0trusty1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-kde (1:20151016.2-0trusty1) ...
Setting up adobe-flash-properties-gtk (1:20151016.2-0trusty1) ...
Setting up libminiupnpc8 (1.6-3ubuntu2.14.04.2) ...
Setting up oxideqt-codecs-extra:amd64 (1.10.3-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...

[/HTML]

and finally, sudo apt-get -f install

[HTML]sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  attr blender-data bve-route-cross-city-south bve-train-br-class-323
  bve-train-br-class-323-3dcab csound-data fonts-horai-umefont hyphen-en-us
  libatk-bridge2.0-0:i386 libatspi2.0-0:i386 libaudclient2 libaudcore1
  libboost-filesystem1.54.0 libboost-locale1.54.0 libboost-regex1.54.0
  libcairo-gobject2:i386 libcapi20-3 libcapi20-3:i386 libcmis-0.4-4
  libcolord1:i386 libdbusmenu-gtk3-4:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libedit2:i386 libelf1:i386
  libexif12:i386 libgd3:i386 libgif4:i386 libgl1-mesa-dri-lts-vivid:i386
  libgl1-mesa-glx-lts-vivid:i386 libglapi-mesa-lts-vivid:i386
  libglu1-mesa:i386 libgphoto2-6:i386 libgphoto2-port10:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk-3-0:i386
  libhdb9-heimdal libice6:i386 libieee1284-3:i386 libimlib2 libkdc2-heimdal
  liblcms2-2:i386 libllvm3.6:i386 libltc11 libltdl7:i386 liblua5.1-0
  libmowgli2 libmpg123-0:i386 libnss-winbind libopenal1:i386 libopenimageio1.3
  liborc-0.4-0:i386 libp11-kit-gnome-keyring:i386 libpam-winbind
  libpciaccess0:i386 libquvi-scripts libquvi7 librhino-java libsane:i386
  libsigc++-1.2-5c2 libsm6:i386 libsmf0 libswt-cairo-gtk-3-jni
  libswt-gtk-3-java libswt-gtk-3-jni libswt-webkit-gtk-3-jni libsynfig0
  libtxc-dxtn-s2tc0:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386
  libvpx1:i386 libwayland-client0:i386 libwayland-cursor0:i386
  libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-sync1:i386 libxkbcommon0:i386 libxml2:i386
  libxpm4:i386 libxshmfence1:i386 libxslt1.1:i386 libxt6:i386 libxxf86vm1:i386
  linux-image-3.13.0-63-lowlatency linux-image-3.19.0-25-generic
  linux-image-3.19.0-25-lowlatency linux-image-extra-3.19.0-25-generic
  live-config-doc mencoder mythes-en-au ocl-icd-libopencl1:i386
  openoffice.org-hyphenation openshot-doc p11-kit-modules:i386
  python-dnspython python-mididings python-mlt python-pygoocanvas samba
  samba-dsdb-modules samba-vfs-modules synfig-examples tdb-tools transcode
  twolame winbind wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
  wine1.4-i386:i386 wine1.6 wine1.6-amd64 wine1.6-i386:i386 winetricks
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

[/HTML]

I can't wait till I understand better all this information.

The software updater is also asking if I want to update the following. I'm uploading a screenshot. I'm no using it. Just FYI.

Thanks!

---

### Post by Bashing-om on 2015-10-20
33Nicolas; Wellllll !

A lot to digest .. at 1st look, looks good .. 
My eyes are crossing as I have been at this terminal now for several hours ; let me look again in my refreshed AM state .
We will then take this back up ..
But for now sure looks promising .

[INDENT][INDENT]to tired to trust 
[INDENT][INDENT][INDENT]cogitation
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-21
33Nicolas; Welp ..

Refreshed, and looked over the thread .. and I do think ...
We are at the point we should clean up the system from old orphaned files and such and install those "0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded."

There is a moderate amount of risk -- there is a lot of cruft, and I have only given a cursory look at it .. and it is a bunch .. let's however bite the bullet, see what happens when we remove what the system "thinks" is cruft .

Keeping in mind our present task is a consistent happy package manager before changing our focus back to starting the desktop.

With fingers and toes crossed, do in terminal:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

sudo apt-get -f install
sudo dpkg -C

```
-------------------------
Bet this is the 1st time you have used the revamped 'apt' . Note how 'apt' is now updated and the difference in how it interacts from that of 'apt-get' . 'apt' is now smarter, and I do trust it .
-------------------------------------

Hoping that the package manager does not remove things that we want to keep . I think to remove the cruft to enhance our view, the risk is warranted .
We want a record of what happens, and I really want to see what happens - so yeah .. post those outputs back to the thread OR to the pastebin site .

[INDENT][INDENT]the foundation remains
[INDENT][INDENT][INDENT]a happy package management system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MartyBuntu on 2015-10-21
I've learned quite a bit from this thread...

---

### Post by Bashing-om on 2015-10-21
Marty; :)

> **MartyBuntu said:**
> I've learned quite a bit from this thread...

That - IMHO - is the great thing about this operating system and this forum . Never stop learning.

[INDENT]major motivation
[INDENT][INDENT][INDENT]why I am here
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-22
Glad to know I'm not the only one learning, although at this stage, it's way over my head. Bashing-Om, you rock.

I'll get to it this afternoon.

So, here we go:
sudo apt-get clean, nothing happens. It asked me for my password, then nothing. I sudo apt-get clean again, and still nothing. Moving on to next.

```
sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

Not sure if you want me to post everything sudo apt-get autoremove has done, but it was impressive.

sudo apt update

```

Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable Release.gpg                                    
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:2 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Ign http://archive.canonical.com trusty InRelease                              
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:3 http://us.archive.ubuntu.com trusty-proposed InRelease [212 kB]          
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner Sources                        
Get:4 http://security.ubuntu.com trusty-security/main Sources [97.6 kB]        
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:5 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [323 kB]
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign https://private-ppa.launchpad.net precise InRelease                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B]  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [635 kB] 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B]  
Hit https://private-ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net trusty/main Sources                               
Get:9 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]    
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://dl.google.com stable/main Translation-en                            
Get:10 http://security.ubuntu.com trusty-security/main amd64 Packages [356 kB] 
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [324 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:14 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:15 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [615 kB] 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:16 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:17 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:19 http://security.ubuntu.com trusty-security/main i386 Packages [338 kB]  
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Get:21 http://us.archive.ubuntu.com trusty-proposed/universe amd64 Packages [27.3 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:22 http://us.archive.ubuntu.com trusty-proposed/main amd64 Packages [121 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Get:23 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:24 http://us.archive.ubuntu.com trusty-proposed/restricted amd64 Packages [28 B]
Get:25 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:26 http://us.archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [28 B]
Get:27 http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages [27.3 kB]
Get:28 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:29 http://us.archive.ubuntu.com trusty-proposed/main i386 Packages [117 kB]
Get:30 http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Get:31 http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en      
Hit http://us.archive.ubuntu.com trusty-proposed/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-proposed/universe Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty Release                          
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 3,681 kB in 9s (378 kB/s)                                              
Reading package lists... Done

```


sudo apt upgrade

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.13.0-67 linux-headers-3.13.0-67-lowlatency
  linux-image-3.13.0-67-lowlatency
The following packages have been kept back:
  libav-tools libavdevice53 libavfilter3 libavformat54
The following packages will be upgraded:
  gir1.2-vte-2.90 google-chrome-stable:i386 libvte-2.90-9 libvte-2.90-common
  linux-headers-lowlatency linux-image-lowlatency linux-libc-dev
  linux-lowlatency
8 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 109 MB of archives.
After this operation, 270 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable i386 46.0.2490.80-1 [46.8 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-image-3.13.0-67-lowlatency amd64 3.13.0-67.109 [51.9 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main libvte-2.90-9 amd64 1:0.34.9-1ubuntu2 [265 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main libvte-2.90-common all 1:0.34.9-1ubuntu2 [24.0 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main gir1.2-vte-2.90 amd64 1:0.34.9-1ubuntu2 [6,554 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-headers-3.13.0-67 all 3.13.0-67.109 [8,897 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-headers-3.13.0-67-lowlatency amd64 3.13.0-67.109 [701 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-lowlatency amd64 3.13.0.67.73 [1,780 B]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-image-lowlatency amd64 3.13.0.67.73 [2,388 B]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-headers-lowlatency amd64 3.13.0.67.73 [2,374 B]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main linux-libc-dev amd64 3.13.0-67.109 [774 kB]
Fetched 109 MB in 1min 24s (1,299 kB/s)                                        
(Reading database ... 632795 files and directories currently installed.)
Preparing to unpack .../google-chrome-stable_46.0.2490.80-1_i386.deb ...
Unpacking google-chrome-stable (46.0.2490.80-1) over (46.0.2490.71-1) ...
Selecting previously unselected package linux-image-3.13.0-67-lowlatency.
Preparing to unpack .../linux-image-3.13.0-67-lowlatency_3.13.0-67.109_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-67-lowlatency (3.13.0-67.109) ...
Preparing to unpack .../libvte-2.90-9_1%3a0.34.9-1ubuntu2_amd64.deb ...
Unpacking libvte-2.90-9 (1:0.34.9-1ubuntu2) over (1:0.34.9-1ubuntu1) ...
Preparing to unpack .../libvte-2.90-common_1%3a0.34.9-1ubuntu2_all.deb ...
Unpacking libvte-2.90-common (1:0.34.9-1ubuntu2) over (1:0.34.9-1ubuntu1) ...
Preparing to unpack .../gir1.2-vte-2.90_1%3a0.34.9-1ubuntu2_amd64.deb ...
Unpacking gir1.2-vte-2.90 (1:0.34.9-1ubuntu2) over (1:0.34.9-1ubuntu1) ...
Selecting previously unselected package linux-headers-3.13.0-67.
Preparing to unpack .../linux-headers-3.13.0-67_3.13.0-67.109_all.deb ...
Unpacking linux-headers-3.13.0-67 (3.13.0-67.109) ...
Selecting previously unselected package linux-headers-3.13.0-67-lowlatency.
Preparing to unpack .../linux-headers-3.13.0-67-lowlatency_3.13.0-67.109_amd64.deb ...
Unpacking linux-headers-3.13.0-67-lowlatency (3.13.0-67.109) ...
Preparing to unpack .../linux-lowlatency_3.13.0.67.73_amd64.deb ...
Unpacking linux-lowlatency (3.13.0.67.73) over (3.13.0.66.72) ...
Preparing to unpack .../linux-image-lowlatency_3.13.0.67.73_amd64.deb ...
Unpacking linux-image-lowlatency (3.13.0.67.73) over (3.13.0.66.72) ...
Preparing to unpack .../linux-headers-lowlatency_3.13.0.67.73_amd64.deb ...
Unpacking linux-headers-lowlatency (3.13.0.67.73) over (3.13.0.66.72) ...
Preparing to unpack .../linux-libc-dev_3.13.0-67.109_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.13.0-67.109) over (3.13.0-66.108) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Setting up google-chrome-stable (46.0.2490.80-1) ...
Setting up linux-image-3.13.0-67-lowlatency (3.13.0-67.109) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
update-initramfs: Generating /boot/initrd.img-3.13.0-67-lowlatency
live-boot: core filesystems devices utils memdisk udev wget blockdev.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-64-lowlatency...
P: Writing config for /boot/vmlinuz-3.12.19avl2-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-27-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-26-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-66-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-66-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-64-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-64-lowlatency
Found linux image: /boot/vmlinuz-3.12.19avl2-pae
Found initrd image: /boot/initrd.img-3.12.19avl2-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Setting up libvte-2.90-common (1:0.34.9-1ubuntu2) ...
Setting up libvte-2.90-9 (1:0.34.9-1ubuntu2) ...
Setting up gir1.2-vte-2.90 (1:0.34.9-1ubuntu2) ...
Setting up linux-headers-3.13.0-67 (3.13.0-67.109) ...
Setting up linux-headers-3.13.0-67-lowlatency (3.13.0-67.109) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
Setting up linux-image-lowlatency (3.13.0.67.73) ...
Setting up linux-headers-lowlatency (3.13.0.67.73) ...
Setting up linux-lowlatency (3.13.0.67.73) ...
Setting up linux-libc-dev:amd64 (3.13.0-67.109) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...

```


sudo apt upgrade

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libav-tools libavdevice53 libavfilter3 libavformat54
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

sudo apt full-upgrade
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libav-tools libavdevice53 libavfilter3 libavformat54

```

sudo apt-get -f install

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

sudo dpkg -C didn't do anything.

Another thing I noticed is even though I ignored the Sofware Updater, it seems to have updated on its own and is asking me to reboot. I'll put the computer on hybernation in the meantime.

---

### Post by Bashing-om on 2015-10-22
33Nicolas; Gonna have

to think on this:
> 
(sudo apt full-upgrade) >>
The following packages have been kept back:
  libav-tools libavdevice53 libavfilter3 libavformat54

As I had fully expected them to be installed using "full-upgrade" !

Meanwhile What resulted :
sudo apt-get autoremove

??

Maybe that will help the kept back situation.

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-23
There's the apt-get autoremove

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  attr blender-data bve-route-cross-city-south bve-train-br-class-323
  bve-train-br-class-323-3dcab csound-data fonts-horai-umefont hyphen-en-us
  libatk-bridge2.0-0:i386 libatspi2.0-0:i386 libaudclient2 libaudcore1
  libboost-filesystem1.54.0 libboost-locale1.54.0 libboost-regex1.54.0
  libcairo-gobject2:i386 libcapi20-3 libcapi20-3:i386 libcmis-0.4-4
  libcolord1:i386 libdbusmenu-gtk3-4:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libedit2:i386 libelf1:i386
  libexif12:i386 libgd3:i386 libgif4:i386 libgl1-mesa-dri-lts-vivid:i386
  libgl1-mesa-glx-lts-vivid:i386 libglapi-mesa-lts-vivid:i386
  libglu1-mesa:i386 libgphoto2-6:i386 libgphoto2-port10:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk-3-0:i386
  libhdb9-heimdal libice6:i386 libieee1284-3:i386 libimlib2 libkdc2-heimdal
  liblcms2-2:i386 libllvm3.6:i386 libltc11 libltdl7:i386 liblua5.1-0
  libmowgli2 libmpg123-0:i386 libnss-winbind libopenal1:i386 libopenimageio1.3
  liborc-0.4-0:i386 libp11-kit-gnome-keyring:i386 libpam-winbind
  libpciaccess0:i386 libquvi-scripts libquvi7 librhino-java libsane:i386
  libsigc++-1.2-5c2 libsm6:i386 libsmf0 libswt-cairo-gtk-3-jni
  libswt-gtk-3-java libswt-gtk-3-jni libswt-webkit-gtk-3-jni libsynfig0
  libtxc-dxtn-s2tc0:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386
  libvpx1:i386 libwayland-client0:i386 libwayland-cursor0:i386
  libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-sync1:i386 libxkbcommon0:i386 libxml2:i386
  libxpm4:i386 libxshmfence1:i386 libxslt1.1:i386 libxt6:i386 libxxf86vm1:i386
  linux-image-3.13.0-63-lowlatency linux-image-3.19.0-25-generic
  linux-image-3.19.0-25-lowlatency linux-image-extra-3.19.0-25-generic
  live-config-doc mencoder mythes-en-au ocl-icd-libopencl1:i386
  openoffice.org-hyphenation openshot-doc p11-kit-modules:i386
  python-dnspython python-mididings python-mlt python-pygoocanvas samba
  samba-dsdb-modules samba-vfs-modules synfig-examples tdb-tools transcode
  twolame winbind wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
  wine1.4-i386:i386 wine1.6 wine1.6-amd64 wine1.6-i386:i386 winetricks
0 upgraded, 0 newly installed, 120 to remove and 5 not upgraded.
After this operation, 1,331 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 658771 files and directories currently installed.)
Removing attr (1:2.4.47-1ubuntu1) ...
Removing blender-data (2.69-4ubuntu2) ...
Removing bve-route-cross-city-south (1.31.08-0ubuntu2) ...
Removing bve-train-br-class-323-3dcab (20100711-0ubuntu2) ...
Removing 'diversion of /usr/share/games/bve/Train/BR_Class_323/train.dat to /usr/share/games/bve/Train/BR_Class_323/train.dat.2dcab by bve-train-br-class-323-3dcab'
Removing bve-train-br-class-323 (4.0.1809-0ubuntu3) ...
Removing csound-data (1:6.02~dfsg-1) ...
Removing fonts-horai-umefont (460-1) ...
Removing hyphen-en-us (2.8.6-3ubuntu2) ...
Removing libgtk-3-0:i386 (3.10.8-0ubuntu1.6) ...
Removing libatk-bridge2.0-0:i386 (2.10.2-2ubuntu1) ...
Removing libatspi2.0-0:i386 (2.10.2.is.2.10.1-0ubuntu1) ...
Removing libaudclient2:amd64 (3.4.3-1) ...
Removing libaudcore1:amd64 (3.4.3-1) ...
Removing libopenimageio1.3 (1.3.12~dfsg0-1ubuntu1) ...
Removing libboost-filesystem1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-locale1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-regex1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libcairo-gobject2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Removing libcapi20-3:amd64 (1:3.25+dfsg1-3.3ubuntu2) ...
Removing libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2) ...
Removing libcmis-0.4-4 (0.4.1-3ubuntu4) ...
Removing libcolord1:i386 (1.0.6-1) ...
Removing libdbusmenu-gtk3-4:i386 (12.10.3+14.04.20140612-0ubuntu1) ...
Removing wine1.4-i386 (1:1.6.2-0ubuntu4) ...
Removing libsane:i386 (1.0.23-3ubuntu3.1) ...
Removing libgif4:i386 (4.1.6-11) ...
Removing libpam-winbind:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Removing libnss-winbind:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Removing winbind (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
winbind stop/waiting
Removing samba (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
nmbd stop/waiting
smbd stop/waiting
Removing libkdc2-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libhdb9-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libxt6:i386 (1:1.1.4-1) ...
Removing libsm6:i386 (2:1.2.1-2) ...
Removing libice6:i386 (2:1.0.8-2) ...
Removing libieee1284-3:i386 (0.2.11-12) ...
Removing libimlib2 (1.4.6-2) ...
Removing libltc11:amd64 (1.1.3-1) ...
Removing liblua5.1-0:amd64 (5.1.5-5ubuntu0.1) ...
Removing libmowgli2:amd64 (1.0.0-1ubuntu1) ...
Removing libp11-kit-gnome-keyring:i386 (3.10.1-1ubuntu4.2) ...
Removing libquvi7:amd64 (0.4.1-1ubuntu3) ...
Removing libquvi-scripts (0.4.21-1) ...
Removing librhino-java (1.7R4-2) ...
Removing libsigc++-1.2-5c2 (1.2.7-2ubuntu1) ...
Removing python-mididings (0~20120419~ds0-4) ...
Removing libsmf0 (1.3-2ubuntu1) ...
Removing libswt-cairo-gtk-3-jni (3.8.2-3) ...
Removing libswt-gtk-3-java (3.8.2-3) ...
Removing libswt-webkit-gtk-3-jni (3.8.2-3) ...
Removing libswt-gtk-3-jni (3.8.2-3) ...
Removing libsynfig0 (0.64.1-2) ...
Removing libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1) ...
Removing libv4l-0:i386 (1.0.1-1) ...
Removing libv4lconvert0:i386 (1.0.1-1) ...
Removing libwayland-cursor0:i386 (1.4.0-1ubuntu1) ...
Removing libwayland-client0:i386 (1.4.0-1ubuntu1) ...
Removing libxkbcommon0:i386 (0.4.1-0ubuntu1) ...
Removing libxslt1.1:i386 (1.1.28-2build1) ...
Removing linux-image-3.13.0-63-lowlatency (3.13.0-63.103) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-63-lowlatency /boot/vmlinuz-3.13.0-63-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-63-lowlatency /boot/vmlinuz-3.13.0-63-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.13.0-63-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-63-lowlatency /boot/vmlinuz-3.13.0-63-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.19.0-25-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-64-lowlatency...
P: Writing config for /boot/vmlinuz-3.12.19avl2-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-63-lowlatency /boot/vmlinuz-3.13.0-63-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-27-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-26-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-25-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-66-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-66-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-64-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-64-lowlatency
Found linux image: /boot/vmlinuz-3.12.19avl2-pae
Found initrd image: /boot/initrd.img-3.12.19avl2-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
Found Mac OS X on /dev/sdc2
Found Mac OS X on /dev/sdc5
done
Removing linux-image-extra-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/virtualbox-dkms.0.crash'
Error! Bad return status for module build on kernel: 3.19.0-25-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.3.10/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-25-generic
live-boot: core filesystems devices utils memdisk udev wget blockdev.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.19.0-25-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-64-lowlatency...
P: Writing config for /boot/vmlinuz-3.12.19avl2-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-27-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-26-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-25-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-66-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-66-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-64-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-64-lowlatency
Found linux image: /boot/vmlinuz-3.12.19avl2-pae
Found initrd image: /boot/initrd.img-3.12.19avl2-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
Found Mac OS X on /dev/sdc2
Found Mac OS X on /dev/sdc5
done
Removing linux-image-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
dkms: removing: nvidia-304 304.128 (3.19.0-25-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-304
Version: 304.128
Kernel:  3.19.0-25-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_304.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.19.0-25-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-64-lowlatency...
P: Writing config for /boot/vmlinuz-3.12.19avl2-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-27-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-26-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-25-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-66-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-66-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-64-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-64-lowlatency
Found linux image: /boot/vmlinuz-3.12.19avl2-pae
Found initrd image: /boot/initrd.img-3.12.19avl2-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
Found Mac OS X on /dev/sdc2
Found Mac OS X on /dev/sdc5
done
Removing linux-image-3.19.0-25-lowlatency (3.19.0-25.26~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.19.0-25-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-64-lowlatency...
P: Writing config for /boot/vmlinuz-3.12.19avl2-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-27-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-26-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-66-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-66-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-64-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-64-lowlatency
Found linux image: /boot/vmlinuz-3.12.19avl2-pae
Found initrd image: /boot/initrd.img-3.12.19avl2-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
Found Mac OS X on /dev/sdc2
Found Mac OS X on /dev/sdc5
done
Removing live-config-doc (3.0.23-1+deb8u1) ...
Removing mencoder (2:1.1+dfsg1-0ubuntu3) ...
Removing mythes-en-au (2.1-5.4) ...
Removing openoffice.org-hyphenation (0.7.1) ...
Removing openshot-doc (1.4.3-1.1) ...
Removing p11-kit-modules:i386 (0.20.2-2ubuntu2) ...
Removing python-dnspython (1.11.1-1build1) ...
Removing python-mlt (0.9.0-3) ...
Removing python-pygoocanvas (0.14.1-1ubuntu8) ...
Removing samba-dsdb-modules (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Removing samba-vfs-modules (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Removing synfig-examples (0.64.1-2) ...
Removing tdb-tools (1.2.12-1) ...
Removing transcode (3:1.1.7-8) ...
Removing twolame (0.3.13-1ubuntu1) ...
Removing wine-gecko2.21:amd64 (2.21-0ubuntu1) ...
Removing wine-gecko2.21:i386 (2.21-0ubuntu1) ...
Removing wine-mono0.0.8 (0.0.8-0ubuntu1) ...
Removing winetricks (0.0+20140302-0ubuntu2) ...
Removing wine1.6-amd64 (1:1.6.2-0ubuntu4) ...
Removing wine1.6-i386 (1:1.6.2-0ubuntu4) ...
Removing wine1.6 (1:1.6.2-0ubuntu4) ...
update-binfmts: warning: no executable /usr/bin/wine found, but continuing anyway as you request
Removing libglu1-mesa:i386 (9.0.0-2) ...
Removing libgl1-mesa-glx-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Removing libgl1-mesa-dri-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Removing libdrm-intel1:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libdrm-nouveau2:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libdrm-radeon1:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libllvm3.6:i386 (1:3.6-2ubuntu1~trusty1) ...
Removing libedit2:i386 (3.1-20130712-2) ...
Removing libelf1:i386 (0.158-0ubuntu5.2) ...
Removing libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libexif12:i386 (0.6.21-1ubuntu1) ...
Removing libgd3:i386 (2.1.0-3) ...
Removing libglapi-mesa-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Removing libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2) ...
Removing libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3) ...
Removing liblcms2-2:i386 (2.6-3ubuntu1~trusty1) ...
Removing libltdl7:i386 (2.4.2-1.7ubuntu1) ...
Removing libmpg123-0:i386 (1.16.0-1ubuntu1) ...
Removing libopenal1:i386 (1:1.14-4ubuntu1) ...
Removing liborc-0.4-0:i386 (1:0.4.18-1ubuntu1) ...
Removing libpciaccess0:i386 (0.13.2-1) ...
Removing libusb-1.0-0:i386 (2:1.0.17-1ubuntu2) ...
Removing libvpx1:i386 (1.3.0-2) ...
Removing libx11-xcb1:i386 (2:1.6.2-1ubuntu2) ...
Removing libxcb-dri2-0:i386 (1.10-2ubuntu1) ...
Removing libxcb-dri3-0:i386 (1.10-2ubuntu1) ...
Removing libxcb-glx0:i386 (1.10-2ubuntu1) ...
Removing libxcb-present0:i386 (1.10-2ubuntu1) ...
Removing libxcb-sync1:i386 (1.10-2ubuntu1) ...
Removing libxml2:i386 (2.9.1+dfsg1-3ubuntu4.4) ...
Removing libxpm4:i386 (1:3.5.10-1) ...
Removing libxshmfence1:i386 (1.1-2) ...
Removing libxxf86vm1:i386 (1:1.1.3-1) ...
Removing ocl-icd-libopencl1:i386 (2.1.3-4) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 1 removed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...

```

The OSX partition was from an external drive I forgot to unplug. Thanks.

I haven't restarted the computer because the Software Updater asked me to reboot. Not sure what it did, nor how I can check.

---

### Post by Bashing-om on 2015-10-23
33Nicolas; Looks good !

I do not see anything removed that scares me a lot.
As /boot was re-configured, the system wants a re-boot to activate the latest kernel.

Go ahead, reboot , cross fingers, and let's see what the result really is .
Now what does not work after playing with the system for a spell ...
Graphics OK ?
Wine OK ?

If all is acceptable .. we do a final cleanup of old orphaned files .

And then ... we pick up this fight where we started about Oh-so-long-ago .

[INDENT][INDENT]maybe all is pretty
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-23
Seems like nothing has changed. I have the same log on dialog box. Software Updater is finding updates, such as Generic Linux Kernel and headers, latency kernel, Sudio Base GTK+ and Python Libraries. Multimedia things have been checked off or are not available. Let me know if you feel I should update. Thanks!

---

### Post by Bashing-om on 2015-10-23
33Nicolas; Sure !

Update .. we when that completes.
Let's see what results when we revert the desktop to  defaults .

[INDENT][INDENT]what I think
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-24
It's updating and now asking me to reboot, which I'll do. The Crash  Report is also showing the following problems, Virtualbox, Problem Type  Package, Apport Version 2.14.1-Ubuntu3.17, Archgitecture amd64,  DKMSBuildLog a ton of things there related to Virtualbox,  DKMSKernelVersion 3.19.0-32-generic, tons of dependencies, Ubuntu 14.04,  duplicate of launchpad, Duplicate Signature Virtualbox, Installation  date from 61 days ago, Installation nMedia Ubuntu-Studio 14.04.3 LTS, LS  Mod tons of things in there, Package Architecture all, Package Version  4.3.10, ProcVersionSignature, related package version dpkg  1.17.5ubuntu5.4 and apt 1.0ubuntu2.10, SourcePackage Virtualbox, Tags  trrusty, Uname Linux 3.19.0-31-lowlatency, and 2 other Virutalbox. 

I can't get a text reading out of that dialogbox. Restarting now at last!

I still have that weird session dialog box and my screen resolution is back to normal squint-my-eyes. 

Softweare Updateer says I'm up to date but that 15.04 is available. Let me know if I should update. Thanks.

---

### Post by Bashing-om on 2015-10-24
33Nicolas; Welp;

A lot going on yet ... OK 
1) Virtual Box .. I know nothing about it .. No experience to say from;
2) Kernel issues .. we best look:
```

df -h
df -i
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot
ls -al /vmlinuz*
ls -al /initrd*
dpkg -l | grep linux

``` to make sure all matches up and we are set to boot the latest kernel ( 3.13.0-66-generic ) and so forth .


3) DKMS is (D)ynamic (K)ernel (M)ode (S)etting .. most often in relation to the graphics driver. It is a thought to (RE-) install the driver . The log file /var/log/Xorg.0.log may tell us a bunch.

4) Update .. Not at this time . Release 15.04 goes End_Of_Life in January .. whereas the Long_Term_Support release 14.04 is supported 'till April 2019 ! If you value stability stay on 14.04 ! ... In software sources uncheck " next available release" so you are not "reminded" that a release upgrade is available.

5) "I still have that weird session dialog box" I bet some 3rd party add on. Still no idea of how to find what it is or where it comes from. I bet when we get back to examining the desktop startup files we will find it .

6) apport. we will return to what and why it is reporting at a later time. These reports may or may not be of any import . Generally, apport reporting is a active function in the 'testing' phase and is disabled once the operating system is released as "stable" . We will look at it - later - and see if the default 'disabled' is set.
-----------------------------
Still, after all this time .... working to establish a sound consistent base operating system. I am not going to be too concerned with the X layer (GUI) until the kernel is consistent and there are no errors reported from the kernel . Always keep in mind, I am not looking over your shoulder, nor do I see your terminal; You have to tell me what is going on .. I can only relate as you tell me what is . My crystal ball sometimes gets real hazy .

Let's work on the installed kernels and see what we are going to do in that respect ... the above will tell us the tale and we see then what we do next .  Hey, how did such a simple thing ( start the desktop) get so complex ?

[INDENT][INDENT][INDENT]we beat on it 
[INDENT][INDENT][INDENT]'til it is whooped into shape
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-24
Cool, here go with: 

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       147G   22G  118G  16% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            988M  4.0K  988M   1% /dev
tmpfs           200M  1.3M  199M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1000M   76K 1000M   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sdc3       3.8G   25M  3.8G   1% /media/suoni/4ceaa62f-f0d1-3496-b5d4-95d5dd828422


```

```
df -i
Filesystem         Inodes  IUsed      IFree IUse% Mounted on
/dev/sda1         9773056 826603    8946453    9% /
none               255804      2     255802    1% /sys/fs/cgroup
udev               252853    598     252255    1% /dev
tmpfs              255804    609     255195    1% /run
none               255804      1     255803    1% /run/lock
none               255804      4     255800    1% /run/shm
none               255804     24     255780    1% /run/user
/dev/sdc3      4294967295     40 4294967255    1% /media/suoni/4ceaa62f-f0d1-3496-b5d4-95d5dd828422


```

```
ls -al /usr/src/
total 4140
drwxr-xr-x 36 root root    4096 Oct 24 07:15 .
drwxr-xr-x 11 root root    4096 Aug 23 08:41 ..
-rw-r--r--  1 root root 4091128 Feb 13  2013 alsa-driver.tar.bz2
drwxr-sr-x  5 root src     4096 Nov 28  2010 aufs2-util
lrwxrwxrwx  1 root src       21 Jan 20  2011 linux -> /usr/src/linux-2.6.36
drwxr-xr-x 23 root root    4096 Jun 19  2014 linux-headers-3.12.19avl2-pae
drwxr-xr-x 24 root root    4096 Aug 23 13:12 linux-headers-3.13.0-63
drwxr-xr-x  7 root root    4096 Aug 23 13:12 linux-headers-3.13.0-63-lowlatency
drwxr-xr-x 24 root root    4096 Sep 11 09:31 linux-headers-3.13.0-64
drwxr-xr-x  7 root root    4096 Sep 11 09:31 linux-headers-3.13.0-64-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:44 linux-headers-3.13.0-66
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.13.0-66-lowlatency
drwxr-xr-x 24 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67
drwxr-xr-x  7 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67-lowlatency
drwxr-xr-x 24 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25
drwxr-xr-x  7 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25-generic
drwxr-xr-x  7 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25-lowlatency
drwxr-xr-x 24 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26
drwxr-xr-x  7 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26-generic
drwxr-xr-x  7 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26-lowlatency
drwxr-xr-x 24 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27
drwxr-xr-x  7 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27-generic
drwxr-xr-x  7 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27-lowlatency
drwxr-xr-x 24 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28
drwxr-xr-x  7 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28-generic
drwxr-xr-x  7 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28-lowlatency
drwxr-xr-x 24 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29
drwxr-xr-x  7 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29-generic
drwxr-xr-x  7 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31
drwxr-xr-x  7 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31-generic
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.19.0-31-lowlatency
drwxr-xr-x 24 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-generic
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-lowlatency
drwxr-xr-x  4 root root    4096 Oct 19  2009 modules
drwxr-xr-x  3 root root    4096 Oct 15 09:48 nvidia-304-304.128
drwxr-xr-x 12 root root    4096 Sep 14 17:57 virtualbox-4.3.10


```

```
ls -al /lib/modules/
total 80
drwxr-xr-x 20 root root 4096 Oct 24 07:14 .
drwxr-xr-x 27 root root 4096 Aug 29 07:26 ..
drwxr-xr-x  2 root root 4096 Oct 22 12:45 3.13.0-63-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:44 3.13.0-64-lowlatency
drwxr-xr-x  6 root root 4096 Oct 15 09:52 3.13.0-66-lowlatency
drwxr-xr-x  6 root root 4096 Oct 22 13:18 3.13.0-67-lowlatency
drwxr-xr-x  2 root root 4096 Oct 22 12:51 3.19.0-25-generic
drwxr-xr-x  2 root root 4096 Oct 22 12:54 3.19.0-25-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:45 3.19.0-26-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:45 3.19.0-26-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-27-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-27-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-28-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:47 3.19.0-28-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:47 3.19.0-29-generic
drwxr-xr-x  6 root root 4096 Oct 15 10:11 3.19.0-29-lowlatency
drwxr-xr-x  6 root root 4096 Oct 15 10:12 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  6 root root 4096 Oct 24 07:21 3.19.0-32-generic
drwxr-xr-x  6 root root 4096 Oct 24 07:20 3.19.0-32-lowlatency


```

```
ls -al /boot
total 510212
drwxr-xr-x  4 root root     4096 Oct 24 07:22 .
drwxr-xr-x 26 root root     4096 Oct 24 07:19 ..
-rw-r--r--  1 root root  1165968 Sep  9 07:31 abi-3.13.0-64-lowlatency
-rw-r--r--  1 root root  1166024 Oct  7 10:16 abi-3.13.0-66-lowlatency
-rw-r--r--  1 root root  1166024 Oct 20 09:27 abi-3.13.0-67-lowlatency
-rw-r--r--  1 root root  1270654 Aug 12 08:26 abi-3.19.0-26-generic
-rw-r--r--  1 root root  1271418 Aug 12 09:14 abi-3.19.0-26-lowlatency
-rw-r--r--  1 root root  1271100 Aug 15 20:06 abi-3.19.0-27-generic
-rw-r--r--  1 root root  1271864 Aug 15 20:50 abi-3.19.0-27-lowlatency
-rw-r--r--  1 root root  1271100 Sep  1 04:08 abi-3.19.0-28-generic
-rw-r--r--  1 root root  1271864 Sep  1 04:58 abi-3.19.0-28-lowlatency
-rw-r--r--  1 root root  1271869 Sep 10 04:00 abi-3.19.0-29-generic
-rw-r--r--  1 root root  1272633 Sep 10 04:55 abi-3.19.0-29-lowlatency
-rw-r--r--  1 root root  1271689 Oct  8 05:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root  1272453 Oct  8 06:07 abi-3.19.0-31-lowlatency
-rw-r--r--  1 root root  1271689 Oct 22 05:14 abi-3.19.0-32-generic
-rw-r--r--  1 root root  1272453 Oct 22 07:10 abi-3.19.0-32-lowlatency
-rw-r--r--  1 root root   145952 Jun 16  2014 config-3.12.19avl2-pae
-rw-r--r--  1 root root   165765 Sep  9 07:31 config-3.13.0-64-lowlatency
-rw-r--r--  1 root root   165765 Oct  7 10:16 config-3.13.0-66-lowlatency
-rw-r--r--  1 root root   165765 Oct 20 09:27 config-3.13.0-67-lowlatency
-rw-r--r--  1 root root   177632 Aug 12 08:26 config-3.19.0-26-generic
-rw-r--r--  1 root root   177562 Aug 12 09:14 config-3.19.0-26-lowlatency
-rw-r--r--  1 root root   177651 Aug 15 20:06 config-3.19.0-27-generic
-rw-r--r--  1 root root   177581 Aug 15 20:50 config-3.19.0-27-lowlatency
-rw-r--r--  1 root root   177651 Sep  1 04:08 config-3.19.0-28-generic
-rw-r--r--  1 root root   177581 Sep  1 04:58 config-3.19.0-28-lowlatency
-rw-r--r--  1 root root   177732 Sep 10 04:00 config-3.19.0-29-generic
-rw-r--r--  1 root root   177662 Sep 10 04:55 config-3.19.0-29-lowlatency
-rw-r--r--  1 root root   177790 Oct  8 05:01 config-3.19.0-31-generic
-rw-r--r--  1 root root   177720 Oct  8 06:07 config-3.19.0-31-lowlatency
-rw-r--r--  1 root root   177790 Oct 22 05:14 config-3.19.0-32-generic
-rw-r--r--  1 root root   177720 Oct 22 07:10 config-3.19.0-32-lowlatency
drwxr-xr-x  3 root root     4096 Oct 24 07:22 extlinux
drwxr-xr-x  5 root root     4096 Oct 24 07:23 grub
-rw-r--r--  1 root root 15218042 Aug 22 06:50 initrd.img-3.12.19avl2-pae
-rw-r--r--  1 root root 21547729 Sep 11 09:33 initrd.img-3.13.0-64-lowlatency
-rw-r--r--  1 root root 21546926 Oct 15 09:52 initrd.img-3.13.0-66-lowlatency
-rw-r--r--  1 root root 21545659 Oct 22 13:19 initrd.img-3.13.0-67-lowlatency
-rw-r--r--  1 root root 22200403 Aug 23 09:29 initrd.img-3.19.0-26-generic
-rw-r--r--  1 root root 22160581 Aug 23 09:27 initrd.img-3.19.0-26-lowlatency
-rw-r--r--  1 root root 22200153 Aug 23 09:55 initrd.img-3.19.0-27-generic
-rw-r--r--  1 root root 22161561 Aug 23 09:54 initrd.img-3.19.0-27-lowlatency
-rw-r--r--  1 root root 22198060 Sep  2 20:03 initrd.img-3.19.0-28-generic
-rw-r--r--  1 root root 22159001 Sep 11 09:37 initrd.img-3.19.0-28-lowlatency
-rw-r--r--  1 root root 22204423 Sep 11 20:38 initrd.img-3.19.0-29-generic
-rw-r--r--  1 root root 22164209 Oct 15 10:10 initrd.img-3.19.0-29-lowlatency
-rw-r--r--  1 root root 22204563 Oct 15 10:06 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root 22162744 Oct 15 10:13 initrd.img-3.19.0-31-lowlatency
-rw-r--r--  1 root root 22204297 Oct 24 07:22 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 22161990 Oct 24 07:21 initrd.img-3.19.0-32-lowlatency
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-r--r--  1 root root  1568236 Jun 16  2014 System.map-3.12.19avl2-pae
-rw-------  1 root root  3389803 Sep  9 07:31 System.map-3.13.0-64-lowlatency
-rw-------  1 root root  3390076 Oct  7 10:16 System.map-3.13.0-66-lowlatency
-rw-------  1 root root  3390140 Oct 20 09:27 System.map-3.13.0-67-lowlatency
-rw-------  1 root root  3626965 Aug 12 08:26 System.map-3.19.0-26-generic
-rw-------  1 root root  3629495 Aug 12 09:14 System.map-3.19.0-26-lowlatency
-rw-------  1 root root  3626779 Aug 15 20:06 System.map-3.19.0-27-generic
-rw-------  1 root root  3629309 Aug 15 20:50 System.map-3.19.0-27-lowlatency
-rw-------  1 root root  3626779 Sep  1 04:08 System.map-3.19.0-28-generic
-rw-------  1 root root  3629309 Sep  1 04:58 System.map-3.19.0-28-lowlatency
-rw-------  1 root root  3627906 Sep 10 04:00 System.map-3.19.0-29-generic
-rw-------  1 root root  3630436 Sep 10 04:55 System.map-3.19.0-29-lowlatency
-rw-------  1 root root  3628177 Oct  8 05:01 System.map-3.19.0-31-generic
-rw-------  1 root root  3630708 Oct  8 06:07 System.map-3.19.0-31-lowlatency
-rw-------  1 root root  3628149 Oct 22 05:14 System.map-3.19.0-32-generic
-rw-------  1 root root  3630711 Oct 22 07:10 System.map-3.19.0-32-lowlatency
-rw-r--r--  1 root root  2473280 Jun 16  2014 vmlinuz-3.12.19avl2-pae
-rw-------  1 root root  5823200 Sep  9 07:31 vmlinuz-3.13.0-64-lowlatency
-rw-------  1 root root  5822688 Oct  7 10:16 vmlinuz-3.13.0-66-lowlatency
-rw-------  1 root root  5822848 Oct 20 09:27 vmlinuz-3.13.0-67-lowlatency
-rw-------  1 root root  6570192 Aug 12 08:26 vmlinuz-3.19.0-26-generic
-rw-------  1 root root  6585552 Aug 12 09:14 vmlinuz-3.19.0-26-lowlatency
-rw-------  1 root root  6569552 Aug 15 20:06 vmlinuz-3.19.0-27-generic
-rw-------  1 root root  6583984 Aug 15 20:50 vmlinuz-3.19.0-27-lowlatency
-rw-------  1 root root  6568848 Sep  1 04:08 vmlinuz-3.19.0-28-generic
-rw-------  1 root root  6583184 Sep  1 04:58 vmlinuz-3.19.0-28-lowlatency
-rw-------  1 root root  6572880 Sep 10 04:00 vmlinuz-3.19.0-29-generic
-rw-------  1 root root  6587280 Sep 10 04:55 vmlinuz-3.19.0-29-lowlatency
-rw-------  1 root root  6572336 Oct  8 05:01 vmlinuz-3.19.0-31-generic
-rw-------  1 root root  6584720 Oct  8 06:07 vmlinuz-3.19.0-31-lowlatency
-rw-------  1 root root  6572944 Oct 22 05:14 vmlinuz-3.19.0-32-generic
-rw-------  1 root root  6584112 Oct 22 07:10 vmlinuz-3.19.0-32-lowlatency


```

```
ls -al /vmlinuz*
lrwxrwxrwx 1 root root 33 Oct 24 07:19 /vmlinuz -> boot/vmlinuz-3.19.0-32-lowlatency
lrwxrwxrwx 1 root root 30 Oct 24 07:16 /vmlinuz.old -> boot/vmlinuz-3.19.0-32-generic


```

```
ls -al /initrd*
lrwxrwxrwx 1 root root 36 Oct 24 07:19 /initrd.img -> boot/initrd.img-3.19.0-32-lowlatency
lrwxrwxrwx 1 root root 33 Oct 24 07:16 /initrd.img.old -> boot/initrd.img-3.19.0-32-generic


```

```
dpkg -l | grep linux
ii  extlinux                                                    3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders (ext2/3/4 and btrfs bootloader)
ii  fonts-linuxlibertine                                        5.3.0-2                                             all          Linux Libertine family of fonts
ii  ladspa-sdk                                                  1.13-2                                              amd64        sample tools for linux-audio-dev plugin architecture
ii  libselinux1:amd64                                           2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                            2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                              1.0.1-1                                             amd64        Collection of video4linux support libraries
rc  libv4l-0:i386                                               1.0.1-1                                             i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                        1.0.1-1                                             amd64        Video4linux frame format conversion library
rc  libv4lconvert0:i386                                         1.0.1-1                                             i386         Video4linux frame format conversion library
ii  linux-firmware                                              1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-vivid                                     3.19.0.32.19                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-63                                     3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-lowlatency                          3.13.0-63.103                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-64                                     3.13.0-64.104                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-64-lowlatency                          3.13.0-64.104                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                                     3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-lowlatency                          3.13.0-66.108                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                                     3.13.0-67.109                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-lowlatency                          3.13.0-67.109                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-25                                     3.19.0-25.26~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-25-generic                             3.19.0-25.26~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-25-lowlatency                          3.19.0-25.26~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26                                     3.19.0-26.28~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                             3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26-lowlatency                          3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-27                                     3.19.0-27.29~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-27-generic                             3.19.0-27.29~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-27-lowlatency                          3.19.0-27.29~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                                     3.19.0-28.30~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                             3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28-lowlatency                          3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-29                                     3.19.0-29.31~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-29-generic                             3.19.0-29.31~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-29-lowlatency                          3.19.0-29.31~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                                     3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                             3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31-lowlatency                          3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32                                     3.19.0-32.37~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-32-generic                             3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32-lowlatency                          3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                             3.19.0.32.19                                        amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                                    3.13.0.67.73                                        amd64        lowlatency Linux kernel headers
ii  linux-headers-lowlatency-lts-vivid                          3.19.0.32.19                                        amd64        lowlatency Linux kernel headers
rc  linux-image-3.13.0-63-lowlatency                            3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-64-lowlatency                            3.13.0-64.104                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-lowlatency                            3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-lowlatency                            3.13.0-67.109                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic                               3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-lowlatency                            3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                               3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-lowlatency                            3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-27-generic                               3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-27-lowlatency                            3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                               3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-lowlatency                            3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-29-generic                               3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-29-lowlatency                            3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-lowlatency                            3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-lowlatency                            3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-27-generic                         3.19.0-27.29~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-29-generic                         3.19.0-29.31~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                               3.19.0.32.19                                        amd64        Generic Linux kernel image
ii  linux-image-lowlatency                                      3.13.0.67.73                                        amd64        lowlatency Linux kernel image
ii  linux-image-lowlatency-lts-vivid                            3.19.0.32.19                                        amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-67.109                                       amd64        Linux Kernel Headers for development
ii  linux-lowlatency                                            3.13.0.67.73                                        amd64        Complete lowlatency Linux kernel
ii  linux-lowlatency-lts-vivid                                  3.19.0.32.19                                        amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-wlan-ng                                               0.2.9+dfsg-5                                        amd64        utilities for wireless prism2 cards
ii  linux-wlan-ng-doc                                           0.2.9+dfsg-5                                        all          documentation for wlan-ng
ii  linux-wlan-ng-firmware                                      0.2.9+dfsg-5                                        all          firmware files used by the linux-wlan-ng driver
ii  pptp-linux                                                  1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                                    3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)
ii  util-linux                                                  2.20.1-5.1ubuntu20.7                                amd64        Miscellaneous system utilities


```

I can uninstall Virtualbox without hesitation.

Thanks,

---

### Post by Bashing-om on 2015-10-24
33Nicolas; Ouch !

When it comes to kernels - you have been a busy little boy - !
What in the world is the  :
> 
3.12.19avl2-pae
 kernel ? Is that for the virtual box ?? I have never ever encountered that series .
I am taken aback that 'auteremove' did address these old kernels. Will take me a bit to look over what all is installed .. I do hope we can get the old kernels removed using the package manager .

We have some additional issues at play here as the .old (backup) symlins link to the current kernel . Maybe in the process of cleaning up the old kernels, will straighten it's self up (?) maybe .

[INDENT][INDENT]again, we may
[INDENT][INDENT][INDENT]have our work cut out for us
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-24
Sadly, I can't imagine why I would have installed kernels, short of low latency for the audio work I was tring to do.

I'll remove Virtualbox.

Maybe time to do an autoremove again?

Promise, I'll be much more careful in the future :)

---

### Post by Bashing-om on 2015-10-24
33Nicolas;  In addition ->

To me last ...As I have gone to work on this:
What in the world :
in your /usr/src/ directory
> 
lrwxrwxrwx  1 root src       21 Jan 20  2011 linux -> /usr/src/linux-2.6.36

is this ? 
It does not hurt my feelngs one bit to say " I do not know " when I do not know ..
What have you been doing ???
I have no clue what created this symlink to a now no longer installed kernel version  > I do not know how you got into this situation with that particular symlink, what would call it or the more important - how do we remove it ? Pondering here the best course of action ... Now this might take a real long time . I am very much so open to a learning situation here .. What would create this symbolic link, when and how ?? It sure is not standard or default !

[INDENT][INDENT]it is getting deep
[INDENT][INDENT][INDENT]but not over our heads, yet
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-24
Scary to hear. 

I promise you I didn't create any simlinks, at least consciously and I have no problem telling you I don't know when I don't know, which is all the time :)

I'm up for learning as well, even if it's over my head. I guess this is one way to give back to the community :\

Judging by the date, this must have been the first time I installed Linux on this machine. It had XP on it previously. It's a weird Dell configuration with scsi drives dating back to 2007 I believe. It's not my computer or even my choice. I think I went to Studio very quickly.

Does this help, even somewhat?

---

### Post by Bashing-om on 2015-10-24
33Nicolas; Well ...

Still think'n on what the consequences might be for what I have in mind to clean up the old kernels.

Once virtual box is removed , is there a change in /boot ?
Show a new :
```

ls -al /boot

```
What kernel are you now booting ?
show :
```

uname -r

```
So I do not do a no-no .

Going to do this;
[INDENT][INDENT][INDENT]nothing risked
[INDENT][INDENT][INDENT]nothing gained
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-25
Hey Bashing-Om,

I removed Virtualbox through the Ubuntu Software Center.

One thing I noticed is that my desktop doesn't seem to remember in which workspace my browser was. It defaults to workspace 2, if that is relevant at all.

```
ls -al /boot
total 510212
drwxr-xr-x  4 root root     4096 Oct 24 07:22 .
drwxr-xr-x 26 root root     4096 Oct 24 07:19 ..
-rw-r--r--  1 root root  1165968 Sep  9 07:31 abi-3.13.0-64-lowlatency
-rw-r--r--  1 root root  1166024 Oct  7 10:16 abi-3.13.0-66-lowlatency
-rw-r--r--  1 root root  1166024 Oct 20 09:27 abi-3.13.0-67-lowlatency
-rw-r--r--  1 root root  1270654 Aug 12 08:26 abi-3.19.0-26-generic
-rw-r--r--  1 root root  1271418 Aug 12 09:14 abi-3.19.0-26-lowlatency
-rw-r--r--  1 root root  1271100 Aug 15 20:06 abi-3.19.0-27-generic
-rw-r--r--  1 root root  1271864 Aug 15 20:50 abi-3.19.0-27-lowlatency
-rw-r--r--  1 root root  1271100 Sep  1 04:08 abi-3.19.0-28-generic
-rw-r--r--  1 root root  1271864 Sep  1 04:58 abi-3.19.0-28-lowlatency
-rw-r--r--  1 root root  1271869 Sep 10 04:00 abi-3.19.0-29-generic
-rw-r--r--  1 root root  1272633 Sep 10 04:55 abi-3.19.0-29-lowlatency
-rw-r--r--  1 root root  1271689 Oct  8 05:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root  1272453 Oct  8 06:07 abi-3.19.0-31-lowlatency
-rw-r--r--  1 root root  1271689 Oct 22 05:14 abi-3.19.0-32-generic
-rw-r--r--  1 root root  1272453 Oct 22 07:10 abi-3.19.0-32-lowlatency
-rw-r--r--  1 root root   145952 Jun 16  2014 config-3.12.19avl2-pae
-rw-r--r--  1 root root   165765 Sep  9 07:31 config-3.13.0-64-lowlatency
-rw-r--r--  1 root root   165765 Oct  7 10:16 config-3.13.0-66-lowlatency
-rw-r--r--  1 root root   165765 Oct 20 09:27 config-3.13.0-67-lowlatency
-rw-r--r--  1 root root   177632 Aug 12 08:26 config-3.19.0-26-generic
-rw-r--r--  1 root root   177562 Aug 12 09:14 config-3.19.0-26-lowlatency
-rw-r--r--  1 root root   177651 Aug 15 20:06 config-3.19.0-27-generic
-rw-r--r--  1 root root   177581 Aug 15 20:50 config-3.19.0-27-lowlatency
-rw-r--r--  1 root root   177651 Sep  1 04:08 config-3.19.0-28-generic
-rw-r--r--  1 root root   177581 Sep  1 04:58 config-3.19.0-28-lowlatency
-rw-r--r--  1 root root   177732 Sep 10 04:00 config-3.19.0-29-generic
-rw-r--r--  1 root root   177662 Sep 10 04:55 config-3.19.0-29-lowlatency
-rw-r--r--  1 root root   177790 Oct  8 05:01 config-3.19.0-31-generic
-rw-r--r--  1 root root   177720 Oct  8 06:07 config-3.19.0-31-lowlatency
-rw-r--r--  1 root root   177790 Oct 22 05:14 config-3.19.0-32-generic
-rw-r--r--  1 root root   177720 Oct 22 07:10 config-3.19.0-32-lowlatency
drwxr-xr-x  3 root root     4096 Oct 24 07:22 extlinux
drwxr-xr-x  5 root root     4096 Oct 24 07:23 grub
-rw-r--r--  1 root root 15218042 Aug 22 06:50 initrd.img-3.12.19avl2-pae
-rw-r--r--  1 root root 21547729 Sep 11 09:33 initrd.img-3.13.0-64-lowlatency
-rw-r--r--  1 root root 21546926 Oct 15 09:52 initrd.img-3.13.0-66-lowlatency
-rw-r--r--  1 root root 21545659 Oct 22 13:19 initrd.img-3.13.0-67-lowlatency
-rw-r--r--  1 root root 22200403 Aug 23 09:29 initrd.img-3.19.0-26-generic
-rw-r--r--  1 root root 22160581 Aug 23 09:27 initrd.img-3.19.0-26-lowlatency
-rw-r--r--  1 root root 22200153 Aug 23 09:55 initrd.img-3.19.0-27-generic
-rw-r--r--  1 root root 22161561 Aug 23 09:54 initrd.img-3.19.0-27-lowlatency
-rw-r--r--  1 root root 22198060 Sep  2 20:03 initrd.img-3.19.0-28-generic
-rw-r--r--  1 root root 22159001 Sep 11 09:37 initrd.img-3.19.0-28-lowlatency
-rw-r--r--  1 root root 22204423 Sep 11 20:38 initrd.img-3.19.0-29-generic
-rw-r--r--  1 root root 22164209 Oct 15 10:10 initrd.img-3.19.0-29-lowlatency
-rw-r--r--  1 root root 22204563 Oct 15 10:06 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root 22162744 Oct 15 10:13 initrd.img-3.19.0-31-lowlatency
-rw-r--r--  1 root root 22204297 Oct 24 07:22 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 22161990 Oct 24 07:21 initrd.img-3.19.0-32-lowlatency
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-r--r--  1 root root  1568236 Jun 16  2014 System.map-3.12.19avl2-pae
-rw-------  1 root root  3389803 Sep  9 07:31 System.map-3.13.0-64-lowlatency
-rw-------  1 root root  3390076 Oct  7 10:16 System.map-3.13.0-66-lowlatency
-rw-------  1 root root  3390140 Oct 20 09:27 System.map-3.13.0-67-lowlatency
-rw-------  1 root root  3626965 Aug 12 08:26 System.map-3.19.0-26-generic
-rw-------  1 root root  3629495 Aug 12 09:14 System.map-3.19.0-26-lowlatency
-rw-------  1 root root  3626779 Aug 15 20:06 System.map-3.19.0-27-generic
-rw-------  1 root root  3629309 Aug 15 20:50 System.map-3.19.0-27-lowlatency
-rw-------  1 root root  3626779 Sep  1 04:08 System.map-3.19.0-28-generic
-rw-------  1 root root  3629309 Sep  1 04:58 System.map-3.19.0-28-lowlatency
-rw-------  1 root root  3627906 Sep 10 04:00 System.map-3.19.0-29-generic
-rw-------  1 root root  3630436 Sep 10 04:55 System.map-3.19.0-29-lowlatency
-rw-------  1 root root  3628177 Oct  8 05:01 System.map-3.19.0-31-generic
-rw-------  1 root root  3630708 Oct  8 06:07 System.map-3.19.0-31-lowlatency
-rw-------  1 root root  3628149 Oct 22 05:14 System.map-3.19.0-32-generic
-rw-------  1 root root  3630711 Oct 22 07:10 System.map-3.19.0-32-lowlatency
-rw-r--r--  1 root root  2473280 Jun 16  2014 vmlinuz-3.12.19avl2-pae
-rw-------  1 root root  5823200 Sep  9 07:31 vmlinuz-3.13.0-64-lowlatency
-rw-------  1 root root  5822688 Oct  7 10:16 vmlinuz-3.13.0-66-lowlatency
-rw-------  1 root root  5822848 Oct 20 09:27 vmlinuz-3.13.0-67-lowlatency
-rw-------  1 root root  6570192 Aug 12 08:26 vmlinuz-3.19.0-26-generic
-rw-------  1 root root  6585552 Aug 12 09:14 vmlinuz-3.19.0-26-lowlatency
-rw-------  1 root root  6569552 Aug 15 20:06 vmlinuz-3.19.0-27-generic
-rw-------  1 root root  6583984 Aug 15 20:50 vmlinuz-3.19.0-27-lowlatency
-rw-------  1 root root  6568848 Sep  1 04:08 vmlinuz-3.19.0-28-generic
-rw-------  1 root root  6583184 Sep  1 04:58 vmlinuz-3.19.0-28-lowlatency
-rw-------  1 root root  6572880 Sep 10 04:00 vmlinuz-3.19.0-29-generic
-rw-------  1 root root  6587280 Sep 10 04:55 vmlinuz-3.19.0-29-lowlatency
-rw-------  1 root root  6572336 Oct  8 05:01 vmlinuz-3.19.0-31-generic
-rw-------  1 root root  6584720 Oct  8 06:07 vmlinuz-3.19.0-31-lowlatency
-rw-------  1 root root  6572944 Oct 22 05:14 vmlinuz-3.19.0-32-generic
-rw-------  1 root root  6584112 Oct 22 07:10 vmlinuz-3.19.0-32-lowlatency

```

```
uname -r
uname -r
3.19.0-32-lowlatency


```

So Doc, how bad is it? ;)

---

### Post by Bashing-om on 2015-10-25
33Nicolas; Well, well ..

No nasty surprises there .
Let's see what we can find out about that 2.6 kernel !
Any return from :
```

sudo find / -name linux-2.6.36

```
Will take a bit of time to search the file system, give the command time to complete. Depending on what the return is, is what we do in this respect.

And see IF/What we can do to remove the 3.12 kernel
```

sudo dpkg -P linux-image-3.12.19avl2-pae
sudo dpkg -P linux-headers-3.12.19avl2-pae

``` which I expect will fail - as it is not fully installed, but give the package manager a chance as see what it can do .  IF/When it fails, we get dirty, and go behind the package manager's back. Not a good thing to do as it will break the package manager and we then must have the package manager heal it's self.

Get these 2 removed, and the package manager back consistent, then we tackle the remainder of the old installed kernels.
Again .. need to be sure of what kernel is booted:
show me what you are booting from the output of terminal command:
```

uname -r

```

As to :
> 
my desktop doesn't seem to remember in which workspace my browser was. It defaults to workspace 2, if that is relevant at all.

Not relevant to what we are doing at this time. Must be a config issue - somewhere - we will get to the desktop eventually. Presently we are just cleaning things up so that there are no side issues affecting starting the desktop.

small steps;
[INDENT][INDENT]my little mind copes better in small small stages .[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-25
Bashing-On,

So nothing happens with sudo find / -name linux-2.6.36 It just goes blank after a long time. It asked me for my password and then nothing.
```
sudo dpkg -P linux-image-3.12.19avl2-pae
dpkg: warning: ignoring request to remove linux-image-3.12.19avl2-pae which isn't installed


```


```
sudo dpkg -P linux-headers-3.12.19avl2-pae
dpkg: warning: ignoring request to remove linux-headers-3.12.19avl2-pae which isn't installed


```

As you suspected.

```
uname -r
3.19.0-32-lowlatency


```

I feel like I'm sitting next to a pilot in a 747 with technical difficulties... except we're not crashing. It's Linux!

---

### Post by Bashing-om on 2015-10-25
33Nicolas; Yowsaa ..

except in this case instead of a 747 .. we fly by the seat of our pants.
 OK, lets delete the 2.6 kernel stuff, as we can find no use for it being there:
```

sudo rm /usr/src/linux-2.6.36
sudo rm /usr/src/linux

```

Next is that pesky 3.12 kernel partial install:
```

sudo rm -rf /usr/src/linux-headers-3.12.19avl2-pae
sudo rm /boot/*-3.12.19avl2-pae
sudo apt-get -f install
sudo apt-get purge linux-{headers,image}-3.12.19avl2-pae

```

If when that runs clean .. next we remove all those other old kernels. - booting 3.19.0-32-lowlatency !!!
Then I pause, look over the thread, see what I have forgotten ,, ---->
Then see about starting the desktop from terminal to get any errors the system may generate .

[INDENT][INDENT]I love a good plan
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-25
Bashing-Om,

Gulp!

```

rm: cannot remove &#8216;/usr/src/linux-2.6.36&#8217;: No such file or directory

```

```

sudo rm /usr/src/linux

```

Nothing happens here.

```
sudo rm -rf /usr/src/linux-headers-3.12.19avl2-pae
```

Nothing happens

```
sudo rm /boot/*-3.12.19avl2-pae
```

Ditto

Should I go on with: sudo apt-get -f install?

I just checked the usr/src/ and it only shows 3.13 or 3.19

Bizarre?

Thanks

---

### Post by Bashing-om on 2015-10-25
33Nicolas; Huh ?

It "WAS" there at one time:
> 
ls -al /usr/src/ >> lrwxrwxrwx  1 root src       21 Jan 20  2011 linux -> /usr/src/linux-2.6.36
drwxr-xr-x 23 root root    4096 Jun 19  2014 linux-headers-3.12.19avl2-pae

Maybe, just maybe .. that was the virtual box install ??

Naw .. on any other commands. Let's back up regroup and see what is now !
A new look;
Post back:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```

And we hit the ground running.
[INDENT][INDENT]no biggy
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-25
Bashing-On, indeed, the only thing I did was to remove Virtualbox, which might have removed those old kernels?

In the meantime:

```
ls -al /usr/src/
total 4132
drwxr-xr-x 34 root root    4096 Oct 25 17:40 .
drwxr-xr-x 11 root root    4096 Aug 23 08:41 ..
-rw-r--r--  1 root root 4091128 Feb 13  2013 alsa-driver.tar.bz2
drwxr-sr-x  5 root src     4096 Nov 28  2010 aufs2-util
drwxr-xr-x 24 root root    4096 Aug 23 13:12 linux-headers-3.13.0-63
drwxr-xr-x  7 root root    4096 Aug 23 13:12 linux-headers-3.13.0-63-lowlatency
drwxr-xr-x 24 root root    4096 Sep 11 09:31 linux-headers-3.13.0-64
drwxr-xr-x  7 root root    4096 Sep 11 09:31 linux-headers-3.13.0-64-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:44 linux-headers-3.13.0-66
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.13.0-66-lowlatency
drwxr-xr-x 24 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67
drwxr-xr-x  7 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67-lowlatency
drwxr-xr-x 24 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25
drwxr-xr-x  7 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25-generic
drwxr-xr-x  7 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25-lowlatency
drwxr-xr-x 24 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26
drwxr-xr-x  7 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26-generic
drwxr-xr-x  7 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26-lowlatency
drwxr-xr-x 24 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27
drwxr-xr-x  7 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27-generic
drwxr-xr-x  7 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27-lowlatency
drwxr-xr-x 24 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28
drwxr-xr-x  7 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28-generic
drwxr-xr-x  7 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28-lowlatency
drwxr-xr-x 24 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29
drwxr-xr-x  7 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29-generic
drwxr-xr-x  7 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31
drwxr-xr-x  7 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31-generic
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.19.0-31-lowlatency
drwxr-xr-x 24 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-generic
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-lowlatency
drwxr-xr-x  4 root root    4096 Oct 19  2009 modules
drwxr-xr-x  3 root root    4096 Oct 15 09:48 nvidia-304-304.128


```

```
ls -al /lib/modules/
total 80
drwxr-xr-x 20 root root 4096 Oct 24 07:14 .
drwxr-xr-x 27 root root 4096 Aug 29 07:26 ..
drwxr-xr-x  2 root root 4096 Oct 22 12:45 3.13.0-63-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:44 3.13.0-64-lowlatency
drwxr-xr-x  5 root root 4096 Oct 24 12:08 3.13.0-66-lowlatency
drwxr-xr-x  6 root root 4096 Oct 24 12:08 3.13.0-67-lowlatency
drwxr-xr-x  2 root root 4096 Oct 22 12:51 3.19.0-25-generic
drwxr-xr-x  2 root root 4096 Oct 22 12:54 3.19.0-25-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:45 3.19.0-26-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:45 3.19.0-26-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-27-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-27-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-28-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:47 3.19.0-28-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:47 3.19.0-29-generic
drwxr-xr-x  6 root root 4096 Oct 15 10:11 3.19.0-29-lowlatency
drwxr-xr-x  6 root root 4096 Oct 15 10:12 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  6 root root 4096 Oct 24 07:21 3.19.0-32-generic
drwxr-xr-x  6 root root 4096 Oct 24 07:20 3.19.0-32-lowlatency


```

```
ls -al /boot/
total 491256
drwxr-xr-x  4 root root     4096 Oct 25 17:40 .
drwxr-xr-x 26 root root     4096 Oct 24 07:19 ..
-rw-r--r--  1 root root  1165968 Sep  9 07:31 abi-3.13.0-64-lowlatency
-rw-r--r--  1 root root  1166024 Oct  7 10:16 abi-3.13.0-66-lowlatency
-rw-r--r--  1 root root  1166024 Oct 20 09:27 abi-3.13.0-67-lowlatency
-rw-r--r--  1 root root  1270654 Aug 12 08:26 abi-3.19.0-26-generic
-rw-r--r--  1 root root  1271418 Aug 12 09:14 abi-3.19.0-26-lowlatency
-rw-r--r--  1 root root  1271100 Aug 15 20:06 abi-3.19.0-27-generic
-rw-r--r--  1 root root  1271864 Aug 15 20:50 abi-3.19.0-27-lowlatency
-rw-r--r--  1 root root  1271100 Sep  1 04:08 abi-3.19.0-28-generic
-rw-r--r--  1 root root  1271864 Sep  1 04:58 abi-3.19.0-28-lowlatency
-rw-r--r--  1 root root  1271869 Sep 10 04:00 abi-3.19.0-29-generic
-rw-r--r--  1 root root  1272633 Sep 10 04:55 abi-3.19.0-29-lowlatency
-rw-r--r--  1 root root  1271689 Oct  8 05:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root  1272453 Oct  8 06:07 abi-3.19.0-31-lowlatency
-rw-r--r--  1 root root  1271689 Oct 22 05:14 abi-3.19.0-32-generic
-rw-r--r--  1 root root  1272453 Oct 22 07:10 abi-3.19.0-32-lowlatency
-rw-r--r--  1 root root   165765 Sep  9 07:31 config-3.13.0-64-lowlatency
-rw-r--r--  1 root root   165765 Oct  7 10:16 config-3.13.0-66-lowlatency
-rw-r--r--  1 root root   165765 Oct 20 09:27 config-3.13.0-67-lowlatency
-rw-r--r--  1 root root   177632 Aug 12 08:26 config-3.19.0-26-generic
-rw-r--r--  1 root root   177562 Aug 12 09:14 config-3.19.0-26-lowlatency
-rw-r--r--  1 root root   177651 Aug 15 20:06 config-3.19.0-27-generic
-rw-r--r--  1 root root   177581 Aug 15 20:50 config-3.19.0-27-lowlatency
-rw-r--r--  1 root root   177651 Sep  1 04:08 config-3.19.0-28-generic
-rw-r--r--  1 root root   177581 Sep  1 04:58 config-3.19.0-28-lowlatency
-rw-r--r--  1 root root   177732 Sep 10 04:00 config-3.19.0-29-generic
-rw-r--r--  1 root root   177662 Sep 10 04:55 config-3.19.0-29-lowlatency
-rw-r--r--  1 root root   177790 Oct  8 05:01 config-3.19.0-31-generic
-rw-r--r--  1 root root   177720 Oct  8 06:07 config-3.19.0-31-lowlatency
-rw-r--r--  1 root root   177790 Oct 22 05:14 config-3.19.0-32-generic
-rw-r--r--  1 root root   177720 Oct 22 07:10 config-3.19.0-32-lowlatency
drwxr-xr-x  3 root root     4096 Oct 24 07:22 extlinux
drwxr-xr-x  5 root root     4096 Oct 24 07:23 grub
-rw-r--r--  1 root root 21547729 Sep 11 09:33 initrd.img-3.13.0-64-lowlatency
-rw-r--r--  1 root root 21546926 Oct 15 09:52 initrd.img-3.13.0-66-lowlatency
-rw-r--r--  1 root root 21545659 Oct 22 13:19 initrd.img-3.13.0-67-lowlatency
-rw-r--r--  1 root root 22200403 Aug 23 09:29 initrd.img-3.19.0-26-generic
-rw-r--r--  1 root root 22160581 Aug 23 09:27 initrd.img-3.19.0-26-lowlatency
-rw-r--r--  1 root root 22200153 Aug 23 09:55 initrd.img-3.19.0-27-generic
-rw-r--r--  1 root root 22161561 Aug 23 09:54 initrd.img-3.19.0-27-lowlatency
-rw-r--r--  1 root root 22198060 Sep  2 20:03 initrd.img-3.19.0-28-generic
-rw-r--r--  1 root root 22159001 Sep 11 09:37 initrd.img-3.19.0-28-lowlatency
-rw-r--r--  1 root root 22204423 Sep 11 20:38 initrd.img-3.19.0-29-generic
-rw-r--r--  1 root root 22164209 Oct 15 10:10 initrd.img-3.19.0-29-lowlatency
-rw-r--r--  1 root root 22204563 Oct 15 10:06 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root 22162744 Oct 15 10:13 initrd.img-3.19.0-31-lowlatency
-rw-r--r--  1 root root 22204297 Oct 24 07:22 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 22161990 Oct 24 07:21 initrd.img-3.19.0-32-lowlatency
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389803 Sep  9 07:31 System.map-3.13.0-64-lowlatency
-rw-------  1 root root  3390076 Oct  7 10:16 System.map-3.13.0-66-lowlatency
-rw-------  1 root root  3390140 Oct 20 09:27 System.map-3.13.0-67-lowlatency
-rw-------  1 root root  3626965 Aug 12 08:26 System.map-3.19.0-26-generic
-rw-------  1 root root  3629495 Aug 12 09:14 System.map-3.19.0-26-lowlatency
-rw-------  1 root root  3626779 Aug 15 20:06 System.map-3.19.0-27-generic
-rw-------  1 root root  3629309 Aug 15 20:50 System.map-3.19.0-27-lowlatency
-rw-------  1 root root  3626779 Sep  1 04:08 System.map-3.19.0-28-generic
-rw-------  1 root root  3629309 Sep  1 04:58 System.map-3.19.0-28-lowlatency
-rw-------  1 root root  3627906 Sep 10 04:00 System.map-3.19.0-29-generic
-rw-------  1 root root  3630436 Sep 10 04:55 System.map-3.19.0-29-lowlatency
-rw-------  1 root root  3628177 Oct  8 05:01 System.map-3.19.0-31-generic
-rw-------  1 root root  3630708 Oct  8 06:07 System.map-3.19.0-31-lowlatency
-rw-------  1 root root  3628149 Oct 22 05:14 System.map-3.19.0-32-generic
-rw-------  1 root root  3630711 Oct 22 07:10 System.map-3.19.0-32-lowlatency
-rw-------  1 root root  5823200 Sep  9 07:31 vmlinuz-3.13.0-64-lowlatency
-rw-------  1 root root  5822688 Oct  7 10:16 vmlinuz-3.13.0-66-lowlatency
-rw-------  1 root root  5822848 Oct 20 09:27 vmlinuz-3.13.0-67-lowlatency
-rw-------  1 root root  6570192 Aug 12 08:26 vmlinuz-3.19.0-26-generic
-rw-------  1 root root  6585552 Aug 12 09:14 vmlinuz-3.19.0-26-lowlatency
-rw-------  1 root root  6569552 Aug 15 20:06 vmlinuz-3.19.0-27-generic
-rw-------  1 root root  6583984 Aug 15 20:50 vmlinuz-3.19.0-27-lowlatency
-rw-------  1 root root  6568848 Sep  1 04:08 vmlinuz-3.19.0-28-generic
-rw-------  1 root root  6583184 Sep  1 04:58 vmlinuz-3.19.0-28-lowlatency
-rw-------  1 root root  6572880 Sep 10 04:00 vmlinuz-3.19.0-29-generic
-rw-------  1 root root  6587280 Sep 10 04:55 vmlinuz-3.19.0-29-lowlatency
-rw-------  1 root root  6572336 Oct  8 05:01 vmlinuz-3.19.0-31-generic
-rw-------  1 root root  6584720 Oct  8 06:07 vmlinuz-3.19.0-31-lowlatency
-rw-------  1 root root  6572944 Oct 22 05:14 vmlinuz-3.19.0-32-generic
-rw-------  1 root root  6584112 Oct 22 07:10 vmlinuz-3.19.0-32-lowlatency


```

```
dpkg-l | grep linux-
dpkg-l: command not found


```

---

### Post by Bashing-om on 2015-10-25
33Nicolas; Erraaa ,,

Typo on my part ;
correct to be :
```

dpkg -l | grep linux-

```

And YES now looks doable, all those pesky partials are no longer extent .
silly little space

---

### Post by 33Nicolas on 2015-10-25
Drats! Didn't see an extra page had been added by your response. Why don't they show everything?

```
dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                              amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                                              1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-vivid                                     3.19.0.32.19                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-63                                     3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-lowlatency                          3.13.0-63.103                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-64                                     3.13.0-64.104                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-64-lowlatency                          3.13.0-64.104                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                                     3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-lowlatency                          3.13.0-66.108                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                                     3.13.0-67.109                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-lowlatency                          3.13.0-67.109                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-25                                     3.19.0-25.26~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-25-generic                             3.19.0-25.26~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-25-lowlatency                          3.19.0-25.26~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26                                     3.19.0-26.28~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                             3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26-lowlatency                          3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-27                                     3.19.0-27.29~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-27-generic                             3.19.0-27.29~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-27-lowlatency                          3.19.0-27.29~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                                     3.19.0-28.30~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                             3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28-lowlatency                          3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-29                                     3.19.0-29.31~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-29-generic                             3.19.0-29.31~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-29-lowlatency                          3.19.0-29.31~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                                     3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                             3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31-lowlatency                          3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32                                     3.19.0-32.37~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-32-generic                             3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32-lowlatency                          3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                             3.19.0.32.19                                        amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                                    3.13.0.67.73                                        amd64        lowlatency Linux kernel headers
ii  linux-headers-lowlatency-lts-vivid                          3.19.0.32.19                                        amd64        lowlatency Linux kernel headers
rc  linux-image-3.13.0-63-lowlatency                            3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-64-lowlatency                            3.13.0-64.104                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-lowlatency                            3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-lowlatency                            3.13.0-67.109                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic                               3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-lowlatency                            3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                               3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-lowlatency                            3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-27-generic                               3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-27-lowlatency                            3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                               3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-lowlatency                            3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-29-generic                               3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-29-lowlatency                            3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-lowlatency                            3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-lowlatency                            3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-27-generic                         3.19.0-27.29~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-29-generic                         3.19.0-29.31~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                               3.19.0.32.19                                        amd64        Generic Linux kernel image
ii  linux-image-lowlatency                                      3.13.0.67.73                                        amd64        lowlatency Linux kernel image
ii  linux-image-lowlatency-lts-vivid                            3.19.0.32.19                                        amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-67.109                                       amd64        Linux Kernel Headers for development
ii  linux-lowlatency                                            3.13.0.67.73                                        amd64        Complete lowlatency Linux kernel
ii  linux-lowlatency-lts-vivid                                  3.19.0.32.19                                        amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-wlan-ng                                               0.2.9+dfsg-5                                        amd64        utilities for wireless prism2 cards
ii  linux-wlan-ng-doc                                           0.2.9+dfsg-5                                        all          documentation for wlan-ng
ii  linux-wlan-ng-firmware                                      0.2.9+dfsg-5                                        all          firmware files used by the linux-wlan-ng driver
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)


```

I'll be back tomorrow. Thanks Bashing-Om. This is a really cool and fruitful experience.

---

### Post by Bashing-om on 2015-10-25
33Nicolas; Hey .. Is All Good ..

We manage .
Now the latest 'problem'; if ya look over the directories you see that in the /boot directory is missing 3.13.0-63 and 3.19.0-25 files .
One has to wonder if that is not some of the root of some of our problems !

I had in mind to in bulk remove these old kernels.. but now I think I best think on it.

I am tired and my eyes are crossing .. will look this over again in my AM .. See what I think might be in our best interest at that time.

[INDENT][INDENT]to err is human
[INDENT][INDENT][INDENT]to really foul things up
[INDENT][INDENT][INDENT]takes a tired mind
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-26
Thanks Bashing-Om,

I also wanted to aim and shoot, but there might be problems doing that. I can't imagine Virtualbox doing all this, but I also remember installing from the Ubuntu Software Installer, and at times from the command prompt. Maybe that is what messed things up?

Am revising how to go forward from now on. The Mint on my laptop has been stable, but I haven't tortured it as much as the U-Studio here. I'll stick with Ubuntu.

---

### Post by Bashing-om on 2015-10-26
33Nicolas; Morning ...

Much refreshed and with a plan.
> 
I also wanted to aim and shoot, but there might be problems doing that. 

Not a thing wrong with that notion ... the great thing about 'buntu .. it is always fixable ... one way or another !

Equally surprised at how deep virtual box had it fingers in the system .

To our immediate goal to clean up the system . Best practice is always to remain within the realm of the package management system. It do exist for a reason.
Let us take a gentle poke at removing a partial kernel, see how the package manager responds:
```

sudo apt-get purge linux-image-3.13.0-63-lowlatency
sudo apt-get purge linux-headers--3.13.0-63-lowlatency
sudo apt-get purge linux-headers--3.13.0-63

```
Then, depending this outcome, is what we do next in this odyssey .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-26
Bashing-Om,

```
I also wanted to aim and shoot, but there might be problems doing that.                            

 Not a thing wrong with that notion ... the great thing about 'buntu .. it is always fixable ... one way or another !
```
True dat!

```
sudo apt-get purge linux-image-3.13.0-63-lowlatency
[sudo] password for ...: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-63-lowlatency*
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 706370 files and directories currently installed.)
Removing linux-image-3.13.0-63-lowlatency (3.13.0-63.103) ...
Purging configuration files for linux-image-3.13.0-63-lowlatency (3.13.0-63.103) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-63-lowlatency /boot/vmlinuz-3.13.0-63-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-63-lowlatency /boot/vmlinuz-3.13.0-63-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-64-lowlatency...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-63-lowlatency /boot/vmlinuz-3.13.0-63-lowlatency


```

Is it normal it still says 5 not upgradable?

```
sudo apt-get purge linux-headers--3.13.0-63-lowlatency
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers--3.13.0-63-lowlatency
E: Couldn't find any package by regex 'linux-headers--3.13.0-63-lowlatency'


```

```

sudo apt-get purge linux-headers--3.13.0-63
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers--3.13.0-63
E: Couldn't find any package by regex 'linux-headers--3.13.0-63'


```

Holding breath...

---

### Post by Bashing-om on 2015-10-26
33Nicolas; Welp; Humm ,, 

yeah 5 not upgraded is unexpected ... wonder where that came from as we had just updated .. and on my system there is no new updates ( 14.04.3 ) we will return to this.

As to :
> 
sudo apt-get purge linux-headers--3.13.0-63-lowlatency >> E: Unable to locate package linux-headers--3.13.0-63-lowlatency

somewhat irked but not surprised, as we knew it is a partial install ..just hoping that the package manager would save us the dirty work .

So to the dirty way:
```

sudo rm -rf /usr/src/linux-headers-3.13.0-63-lowlatency
sudo rm -rf /usr/src/linux-headers-3.13.0-63
sudo rm -rf /lib/modules/3.13.0-63-lowlatency
sudo apt-get -f install
sudo apt-get purge linux-{headers,image}-3.13.0-63.*

```

see how that goes, and then we tackle the 3.19.0-25 partial install in a similar fashion .


[INDENT][INDENT]there is that way that seems right
[INDENT][INDENT][INDENT][INDENT]but sometimes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-26
Bashing-Om,

Yup, I feel out of the 747 cockpit and right into Star Trek's Voyager. Defiant is next, and then the Enterprise?

In the meantime:

```
sudo rm -rf /usr/src/linux-headers-3.13.0-63-lowlatency


```

Asked for my password. Put it in and nothing happened. I came back to the prompt.

I tried it again. It didn't ask for the password, and nothing happened.

```
sudo rm -rf /usr/src/linux-headers-3.13.0-63
```

This time I heard the computer churn and back at prompt without indication anything happened.

```
sudo rm -rf /lib/modules/3.13.0-63-lowlatency
```

Likewise.

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.


```

```
sudo apt-get purge linux-{headers,image}-3.13.0-63.*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-3.13.0-63-generic' for regex 'linux-headers-3.13.0-63.*'
Note, selecting 'linux-headers-3.13.0-63' for regex 'linux-headers-3.13.0-63.*'
Note, selecting 'linux-headers-3.13.0-63-lowlatency' for regex 'linux-headers-3.13.0-63.*'
Note, selecting 'linux-image-3.13.0-63-generic' for regex 'linux-image-3.13.0-63.*'
Note, selecting 'linux-image-3.13.0-63-lowlatency' for regex 'linux-image-3.13.0-63.*'
Package 'linux-headers-3.13.0-63-generic' is not installed, so not removed
Package 'linux-image-3.13.0-63-generic' is not installed, so not removed
Package 'linux-image-3.13.0-63-lowlatency' is not installed, so not removed
The following packages will be REMOVED:
  linux-headers-3.13.0-63* linux-headers-3.13.0-63-lowlatency*
0 upgraded, 0 newly installed, 2 to remove and 5 not upgraded.
After this operation, 76.8 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 706370 files and directories currently installed.)
Removing linux-headers-3.13.0-63-lowlatency (3.13.0-63.103) ...
Removing linux-headers-3.13.0-63 (3.13.0-63.103) ...


```

That last one seemed to have worked, no?

---

### Post by Bashing-om on 2015-10-26
33Nicolas; Hey ...

Good thing is that with all the flying .. we do have good navigators .

I think we did well on that last with only the bits and pieces we are working with;
But, let's get a new look at things before proceeding.
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

``` a bit of insurance is a good thing.

[INDENT][INDENT]flying low
[INDENT][INDENT][INDENT]not too fast
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-26
Hey Bashing-Om,

Good to hear.

```
 ls -al /usr/src/
total 4124
drwxr-xr-x 32 root root    4096 Oct 26 14:33 .
drwxr-xr-x 11 root root    4096 Aug 23 08:41 ..
-rw-r--r--  1 root root 4091128 Feb 13  2013 alsa-driver.tar.bz2
drwxr-sr-x  5 root src     4096 Nov 28  2010 aufs2-util
drwxr-xr-x 24 root root    4096 Sep 11 09:31 linux-headers-3.13.0-64
drwxr-xr-x  7 root root    4096 Sep 11 09:31 linux-headers-3.13.0-64-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:44 linux-headers-3.13.0-66
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.13.0-66-lowlatency
drwxr-xr-x 24 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67
drwxr-xr-x  7 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67-lowlatency
drwxr-xr-x 24 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25
drwxr-xr-x  7 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25-generic
drwxr-xr-x  7 root root    4096 Aug  4 22:19 linux-headers-3.19.0-25-lowlatency
drwxr-xr-x 24 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26
drwxr-xr-x  7 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26-generic
drwxr-xr-x  7 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26-lowlatency
drwxr-xr-x 24 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27
drwxr-xr-x  7 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27-generic
drwxr-xr-x  7 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27-lowlatency
drwxr-xr-x 24 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28
drwxr-xr-x  7 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28-generic
drwxr-xr-x  7 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28-lowlatency
drwxr-xr-x 24 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29
drwxr-xr-x  7 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29-generic
drwxr-xr-x  7 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31
drwxr-xr-x  7 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31-generic
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.19.0-31-lowlatency
drwxr-xr-x 24 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-generic
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-lowlatency
drwxr-xr-x  4 root root    4096 Oct 19  2009 modules
drwxr-xr-x  3 root root    4096 Oct 15 09:48 nvidia-304-304.128


```

-rw-r--r--  1 root root 4091128 Feb 13  2013 alsa-driver.tar.bz2 is listed in red.

```
ls -al /lib/modules/
total 76
drwxr-xr-x 19 root root 4096 Oct 26 14:34 .
drwxr-xr-x 27 root root 4096 Aug 29 07:26 ..
drwxr-xr-x  5 root root 4096 Oct 15 09:44 3.13.0-64-lowlatency
drwxr-xr-x  5 root root 4096 Oct 24 12:08 3.13.0-66-lowlatency
drwxr-xr-x  6 root root 4096 Oct 24 12:08 3.13.0-67-lowlatency
drwxr-xr-x  2 root root 4096 Oct 22 12:51 3.19.0-25-generic
drwxr-xr-x  2 root root 4096 Oct 22 12:54 3.19.0-25-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:45 3.19.0-26-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:45 3.19.0-26-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-27-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-27-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-28-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:47 3.19.0-28-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:47 3.19.0-29-generic
drwxr-xr-x  6 root root 4096 Oct 15 10:11 3.19.0-29-lowlatency
drwxr-xr-x  6 root root 4096 Oct 15 10:12 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  6 root root 4096 Oct 24 07:21 3.19.0-32-generic
drwxr-xr-x  6 root root 4096 Oct 24 07:20 3.19.0-32-lowlatency


```

```
ls -al /boot/
total 491256
drwxr-xr-x  4 root root     4096 Oct 25 17:40 .
drwxr-xr-x 26 root root     4096 Oct 24 07:19 ..
-rw-r--r--  1 root root  1165968 Sep  9 07:31 abi-3.13.0-64-lowlatency
-rw-r--r--  1 root root  1166024 Oct  7 10:16 abi-3.13.0-66-lowlatency
-rw-r--r--  1 root root  1166024 Oct 20 09:27 abi-3.13.0-67-lowlatency
-rw-r--r--  1 root root  1270654 Aug 12 08:26 abi-3.19.0-26-generic
-rw-r--r--  1 root root  1271418 Aug 12 09:14 abi-3.19.0-26-lowlatency
-rw-r--r--  1 root root  1271100 Aug 15 20:06 abi-3.19.0-27-generic
-rw-r--r--  1 root root  1271864 Aug 15 20:50 abi-3.19.0-27-lowlatency
-rw-r--r--  1 root root  1271100 Sep  1 04:08 abi-3.19.0-28-generic
-rw-r--r--  1 root root  1271864 Sep  1 04:58 abi-3.19.0-28-lowlatency
-rw-r--r--  1 root root  1271869 Sep 10 04:00 abi-3.19.0-29-generic
-rw-r--r--  1 root root  1272633 Sep 10 04:55 abi-3.19.0-29-lowlatency
-rw-r--r--  1 root root  1271689 Oct  8 05:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root  1272453 Oct  8 06:07 abi-3.19.0-31-lowlatency
-rw-r--r--  1 root root  1271689 Oct 22 05:14 abi-3.19.0-32-generic
-rw-r--r--  1 root root  1272453 Oct 22 07:10 abi-3.19.0-32-lowlatency
-rw-r--r--  1 root root   165765 Sep  9 07:31 config-3.13.0-64-lowlatency
-rw-r--r--  1 root root   165765 Oct  7 10:16 config-3.13.0-66-lowlatency
-rw-r--r--  1 root root   165765 Oct 20 09:27 config-3.13.0-67-lowlatency
-rw-r--r--  1 root root   177632 Aug 12 08:26 config-3.19.0-26-generic
-rw-r--r--  1 root root   177562 Aug 12 09:14 config-3.19.0-26-lowlatency
-rw-r--r--  1 root root   177651 Aug 15 20:06 config-3.19.0-27-generic
-rw-r--r--  1 root root   177581 Aug 15 20:50 config-3.19.0-27-lowlatency
-rw-r--r--  1 root root   177651 Sep  1 04:08 config-3.19.0-28-generic
-rw-r--r--  1 root root   177581 Sep  1 04:58 config-3.19.0-28-lowlatency
-rw-r--r--  1 root root   177732 Sep 10 04:00 config-3.19.0-29-generic
-rw-r--r--  1 root root   177662 Sep 10 04:55 config-3.19.0-29-lowlatency
-rw-r--r--  1 root root   177790 Oct  8 05:01 config-3.19.0-31-generic
-rw-r--r--  1 root root   177720 Oct  8 06:07 config-3.19.0-31-lowlatency
-rw-r--r--  1 root root   177790 Oct 22 05:14 config-3.19.0-32-generic
-rw-r--r--  1 root root   177720 Oct 22 07:10 config-3.19.0-32-lowlatency
drwxr-xr-x  3 root root     4096 Oct 26 13:29 extlinux
drwxr-xr-x  5 root root     4096 Oct 24 07:23 grub
-rw-r--r--  1 root root 21547729 Sep 11 09:33 initrd.img-3.13.0-64-lowlatency
-rw-r--r--  1 root root 21546926 Oct 15 09:52 initrd.img-3.13.0-66-lowlatency
-rw-r--r--  1 root root 21545659 Oct 22 13:19 initrd.img-3.13.0-67-lowlatency
-rw-r--r--  1 root root 22200403 Aug 23 09:29 initrd.img-3.19.0-26-generic
-rw-r--r--  1 root root 22160581 Aug 23 09:27 initrd.img-3.19.0-26-lowlatency
-rw-r--r--  1 root root 22200153 Aug 23 09:55 initrd.img-3.19.0-27-generic
-rw-r--r--  1 root root 22161561 Aug 23 09:54 initrd.img-3.19.0-27-lowlatency
-rw-r--r--  1 root root 22198060 Sep  2 20:03 initrd.img-3.19.0-28-generic
-rw-r--r--  1 root root 22159001 Sep 11 09:37 initrd.img-3.19.0-28-lowlatency
-rw-r--r--  1 root root 22204423 Sep 11 20:38 initrd.img-3.19.0-29-generic
-rw-r--r--  1 root root 22164209 Oct 15 10:10 initrd.img-3.19.0-29-lowlatency
-rw-r--r--  1 root root 22204563 Oct 15 10:06 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root 22162744 Oct 15 10:13 initrd.img-3.19.0-31-lowlatency
-rw-r--r--  1 root root 22204297 Oct 24 07:22 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 22161990 Oct 24 07:21 initrd.img-3.19.0-32-lowlatency
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389803 Sep  9 07:31 System.map-3.13.0-64-lowlatency
-rw-------  1 root root  3390076 Oct  7 10:16 System.map-3.13.0-66-lowlatency
-rw-------  1 root root  3390140 Oct 20 09:27 System.map-3.13.0-67-lowlatency
-rw-------  1 root root  3626965 Aug 12 08:26 System.map-3.19.0-26-generic
-rw-------  1 root root  3629495 Aug 12 09:14 System.map-3.19.0-26-lowlatency
-rw-------  1 root root  3626779 Aug 15 20:06 System.map-3.19.0-27-generic
-rw-------  1 root root  3629309 Aug 15 20:50 System.map-3.19.0-27-lowlatency
-rw-------  1 root root  3626779 Sep  1 04:08 System.map-3.19.0-28-generic
-rw-------  1 root root  3629309 Sep  1 04:58 System.map-3.19.0-28-lowlatency
-rw-------  1 root root  3627906 Sep 10 04:00 System.map-3.19.0-29-generic
-rw-------  1 root root  3630436 Sep 10 04:55 System.map-3.19.0-29-lowlatency
-rw-------  1 root root  3628177 Oct  8 05:01 System.map-3.19.0-31-generic
-rw-------  1 root root  3630708 Oct  8 06:07 System.map-3.19.0-31-lowlatency
-rw-------  1 root root  3628149 Oct 22 05:14 System.map-3.19.0-32-generic
-rw-------  1 root root  3630711 Oct 22 07:10 System.map-3.19.0-32-lowlatency
-rw-------  1 root root  5823200 Sep  9 07:31 vmlinuz-3.13.0-64-lowlatency
-rw-------  1 root root  5822688 Oct  7 10:16 vmlinuz-3.13.0-66-lowlatency
-rw-------  1 root root  5822848 Oct 20 09:27 vmlinuz-3.13.0-67-lowlatency
-rw-------  1 root root  6570192 Aug 12 08:26 vmlinuz-3.19.0-26-generic
-rw-------  1 root root  6585552 Aug 12 09:14 vmlinuz-3.19.0-26-lowlatency
-rw-------  1 root root  6569552 Aug 15 20:06 vmlinuz-3.19.0-27-generic
-rw-------  1 root root  6583984 Aug 15 20:50 vmlinuz-3.19.0-27-lowlatency
-rw-------  1 root root  6568848 Sep  1 04:08 vmlinuz-3.19.0-28-generic
-rw-------  1 root root  6583184 Sep  1 04:58 vmlinuz-3.19.0-28-lowlatency
-rw-------  1 root root  6572880 Sep 10 04:00 vmlinuz-3.19.0-29-generic
-rw-------  1 root root  6587280 Sep 10 04:55 vmlinuz-3.19.0-29-lowlatency
-rw-------  1 root root  6572336 Oct  8 05:01 vmlinuz-3.19.0-31-generic
-rw-------  1 root root  6584720 Oct  8 06:07 vmlinuz-3.19.0-31-lowlatency
-rw-------  1 root root  6572944 Oct 22 05:14 vmlinuz-3.19.0-32-generic
-rw-------  1 root root  6584112 Oct 22 07:10 vmlinuz-3.19.0-32-lowlatency


```

```
dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                              amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                                              1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-vivid                                     3.19.0.32.19                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-64                                     3.13.0-64.104                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-64-lowlatency                          3.13.0-64.104                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                                     3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-lowlatency                          3.13.0-66.108                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                                     3.13.0-67.109                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-lowlatency                          3.13.0-67.109                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-25                                     3.19.0-25.26~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-25-generic                             3.19.0-25.26~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-25-lowlatency                          3.19.0-25.26~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26                                     3.19.0-26.28~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                             3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26-lowlatency                          3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-27                                     3.19.0-27.29~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-27-generic                             3.19.0-27.29~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-27-lowlatency                          3.19.0-27.29~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                                     3.19.0-28.30~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                             3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28-lowlatency                          3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-29                                     3.19.0-29.31~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-29-generic                             3.19.0-29.31~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-29-lowlatency                          3.19.0-29.31~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                                     3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                             3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31-lowlatency                          3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32                                     3.19.0-32.37~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-32-generic                             3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32-lowlatency                          3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                             3.19.0.32.19                                        amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                                    3.13.0.67.73                                        amd64        lowlatency Linux kernel headers
ii  linux-headers-lowlatency-lts-vivid                          3.19.0.32.19                                        amd64        lowlatency Linux kernel headers
ii  linux-image-3.13.0-64-lowlatency                            3.13.0-64.104                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-lowlatency                            3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-lowlatency                            3.13.0-67.109                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic                               3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-lowlatency                            3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                               3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-lowlatency                            3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-27-generic                               3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-27-lowlatency                            3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                               3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-lowlatency                            3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-29-generic                               3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-29-lowlatency                            3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-lowlatency                            3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-lowlatency                            3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-27-generic                         3.19.0-27.29~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-29-generic                         3.19.0-29.31~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                               3.19.0.32.19                                        amd64        Generic Linux kernel image
ii  linux-image-lowlatency                                      3.13.0.67.73                                        amd64        lowlatency Linux kernel image
ii  linux-image-lowlatency-lts-vivid                            3.19.0.32.19                                        amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-67.109                                       amd64        Linux Kernel Headers for development
ii  linux-lowlatency                                            3.13.0.67.73                                        amd64        Complete lowlatency Linux kernel
ii  linux-lowlatency-lts-vivid                                  3.19.0.32.19                                        amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-wlan-ng                                               0.2.9+dfsg-5                                        amd64        utilities for wireless prism2 cards
ii  linux-wlan-ng-doc                                           0.2.9+dfsg-5                                        all          documentation for wlan-ng
ii  linux-wlan-ng-firmware                                      0.2.9+dfsg-5                                        all          firmware files used by the linux-wlan-ng driver
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)


```

The first "linux" words are highlighted in red.

root root, indeed!

Be back in an hour.

---

### Post by Bashing-om on 2015-10-26
33Nicolas; Yepper;

Looks promising ... the -63 kernel and files are gone gone now .. let's attack the 3.19.0-25 kernel :
```

sudo rm -rf /usr/src/linux-headers-3.19.0-25-lowlatency
sudo rm -rf /usr/src/linux-headers-3.19.0-25-generic
sudo rm -rf /usr/src/linux-headers-3.19.0-25
sudo rm -rf /lib/modules/3.19.0-25-lowlatency
sudo apt-get -f install
sudo apt-get purge linux-{headers,image}-3.19.0-25.*

```

and the color red for a file:
> 
-rw-r--r-- 1 root root 4091128 Feb 13 2013 alsa-driver.tar.bz2 is listed in red.

a very nice 'nicety' of your terminal .. a quick glance way to know that file is a compressed file. Lots of colors as defined - by alias - in your .bashrc file.

And in this instance:
> 
The first "linux" words are highlighted in red.

is showing you what 'grep' matched .

root root ... means "you" and no one else other than "root' is going to touch these files .. getting a glimmer now of why linux is secure - no virus ! ? 

[INDENT][INDENT]as we move merrily on our way
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-26
Hey Bashing-Om,

Armed with this:

```
sudo rm -rf /usr/src/linux-headers-3.19.0-25-lowlatency
```

Nothing happened but I heard the computer... compute

```
sudo rm -rf /usr/src/linux-headers-3.19.0-25-generic
```

Ditto.

```
sudo rm -rf /usr/src/linux-headers-3.19.0-25
```

Same.

```
sudo rm -rf /lib/modules/3.19.0-25-lowlatency
```

Same, except no hard drive spinning sounds.

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.


```

and 

```
sudo apt-get purge linux-{headers,image}-3.19.0-25.*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-3.19.0-25-generic' for regex 'linux-headers-3.19.0-25.*'
Note, selecting 'linux-headers-3.19.0-25-lowlatency' for regex 'linux-headers-3.19.0-25.*'
Note, selecting 'linux-headers-3.19.0-25' for regex 'linux-headers-3.19.0-25.*'
Note, selecting 'linux-image-3.19.0-25-generic' for regex 'linux-image-3.19.0-25.*'
Note, selecting 'linux-image-3.19.0-25-lowlatency' for regex 'linux-image-3.19.0-25.*'
The following packages will be REMOVED:
  linux-headers-3.19.0-25* linux-headers-3.19.0-25-generic*
  linux-headers-3.19.0-25-lowlatency* linux-image-3.19.0-25-generic*
  linux-image-3.19.0-25-lowlatency*
0 upgraded, 0 newly installed, 5 to remove and 5 not upgraded.
After this operation, 94.8 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 681558 files and directories currently installed.)
Removing linux-headers-3.19.0-25-lowlatency (3.19.0-25.26~14.04.1) ...
Removing linux-headers-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Removing linux-headers-3.19.0-25 (3.19.0-25.26~14.04.1) ...
Removing linux-image-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Purging configuration files for linux-image-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-64-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Removing linux-image-3.19.0-25-lowlatency (3.19.0-25.26~14.04.1) ...
Purging configuration files for linux-image-3.19.0-25-lowlatency (3.19.0-25.26~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-64-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency


```

Good to know about the red highlight for compressed and GREP. I guess you differentiate according to which command you input?

I remember sudo from my early years... but that was a long, long time ago before MS and Apple corrupted me :/

---

### Post by Bashing-om on 2015-10-26
33Nicolas; Looks good ;

But, let's check that the -25 kernel is history.
once more:
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```
and I craft us up a handy dandy to remove all the old kernels we no longer want/need.

I think we can
[INDENT][INDENT][INDENT]I think we can[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-26
Bashing-Om, good idea.

```
uname -r
3.19.0-32-lowlatency


```

```
 ls -al /usr/src/
total 4112
drwxr-xr-x 29 root root    4096 Oct 26 17:15 .
drwxr-xr-x 11 root root    4096 Aug 23 08:41 ..
-rw-r--r--  1 root root 4091128 Feb 13  2013 alsa-driver.tar.bz2
drwxr-sr-x  5 root src     4096 Nov 28  2010 aufs2-util
drwxr-xr-x 24 root root    4096 Sep 11 09:31 linux-headers-3.13.0-64
drwxr-xr-x  7 root root    4096 Sep 11 09:31 linux-headers-3.13.0-64-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:44 linux-headers-3.13.0-66
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.13.0-66-lowlatency
drwxr-xr-x 24 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67
drwxr-xr-x  7 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67-lowlatency
drwxr-xr-x 24 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26
drwxr-xr-x  7 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26-generic
drwxr-xr-x  7 root root    4096 Aug 23 09:23 linux-headers-3.19.0-26-lowlatency
drwxr-xr-x 24 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27
drwxr-xr-x  7 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27-generic
drwxr-xr-x  7 root root    4096 Aug 23 09:50 linux-headers-3.19.0-27-lowlatency
drwxr-xr-x 24 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28
drwxr-xr-x  7 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28-generic
drwxr-xr-x  7 root root    4096 Sep  2 19:53 linux-headers-3.19.0-28-lowlatency
drwxr-xr-x 24 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29
drwxr-xr-x  7 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29-generic
drwxr-xr-x  7 root root    4096 Sep 11 20:29 linux-headers-3.19.0-29-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31
drwxr-xr-x  7 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31-generic
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.19.0-31-lowlatency
drwxr-xr-x 24 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-generic
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-lowlatency
drwxr-xr-x  4 root root    4096 Oct 19  2009 modules
drwxr-xr-x  3 root root    4096 Oct 15 09:48 nvidia-304-304.128


```

So why would the ASLA drier be compressed? The system doesn't need it?

```
ls -al /lib/modules/
total 68
drwxr-xr-x 17 root root 4096 Oct 26 17:17 .
drwxr-xr-x 27 root root 4096 Aug 29 07:26 ..
drwxr-xr-x  5 root root 4096 Oct 15 09:44 3.13.0-64-lowlatency
drwxr-xr-x  5 root root 4096 Oct 24 12:08 3.13.0-66-lowlatency
drwxr-xr-x  6 root root 4096 Oct 24 12:08 3.13.0-67-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:45 3.19.0-26-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:45 3.19.0-26-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-27-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-27-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:46 3.19.0-28-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:47 3.19.0-28-lowlatency
drwxr-xr-x  5 root root 4096 Oct 15 09:47 3.19.0-29-generic
drwxr-xr-x  6 root root 4096 Oct 15 10:11 3.19.0-29-lowlatency
drwxr-xr-x  6 root root 4096 Oct 15 10:12 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  6 root root 4096 Oct 24 07:21 3.19.0-32-generic
drwxr-xr-x  6 root root 4096 Oct 24 07:20 3.19.0-32-lowlatency


```

```
ls -al /boot/
total 491256
drwxr-xr-x  4 root root     4096 Oct 25 17:40 .
drwxr-xr-x 26 root root     4096 Oct 24 07:19 ..
-rw-r--r--  1 root root  1165968 Sep  9 07:31 abi-3.13.0-64-lowlatency
-rw-r--r--  1 root root  1166024 Oct  7 10:16 abi-3.13.0-66-lowlatency
-rw-r--r--  1 root root  1166024 Oct 20 09:27 abi-3.13.0-67-lowlatency
-rw-r--r--  1 root root  1270654 Aug 12 08:26 abi-3.19.0-26-generic
-rw-r--r--  1 root root  1271418 Aug 12 09:14 abi-3.19.0-26-lowlatency
-rw-r--r--  1 root root  1271100 Aug 15 20:06 abi-3.19.0-27-generic
-rw-r--r--  1 root root  1271864 Aug 15 20:50 abi-3.19.0-27-lowlatency
-rw-r--r--  1 root root  1271100 Sep  1 04:08 abi-3.19.0-28-generic
-rw-r--r--  1 root root  1271864 Sep  1 04:58 abi-3.19.0-28-lowlatency
-rw-r--r--  1 root root  1271869 Sep 10 04:00 abi-3.19.0-29-generic
-rw-r--r--  1 root root  1272633 Sep 10 04:55 abi-3.19.0-29-lowlatency
-rw-r--r--  1 root root  1271689 Oct  8 05:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root  1272453 Oct  8 06:07 abi-3.19.0-31-lowlatency
-rw-r--r--  1 root root  1271689 Oct 22 05:14 abi-3.19.0-32-generic
-rw-r--r--  1 root root  1272453 Oct 22 07:10 abi-3.19.0-32-lowlatency
-rw-r--r--  1 root root   165765 Sep  9 07:31 config-3.13.0-64-lowlatency
-rw-r--r--  1 root root   165765 Oct  7 10:16 config-3.13.0-66-lowlatency
-rw-r--r--  1 root root   165765 Oct 20 09:27 config-3.13.0-67-lowlatency
-rw-r--r--  1 root root   177632 Aug 12 08:26 config-3.19.0-26-generic
-rw-r--r--  1 root root   177562 Aug 12 09:14 config-3.19.0-26-lowlatency
-rw-r--r--  1 root root   177651 Aug 15 20:06 config-3.19.0-27-generic
-rw-r--r--  1 root root   177581 Aug 15 20:50 config-3.19.0-27-lowlatency
-rw-r--r--  1 root root   177651 Sep  1 04:08 config-3.19.0-28-generic
-rw-r--r--  1 root root   177581 Sep  1 04:58 config-3.19.0-28-lowlatency
-rw-r--r--  1 root root   177732 Sep 10 04:00 config-3.19.0-29-generic
-rw-r--r--  1 root root   177662 Sep 10 04:55 config-3.19.0-29-lowlatency
-rw-r--r--  1 root root   177790 Oct  8 05:01 config-3.19.0-31-generic
-rw-r--r--  1 root root   177720 Oct  8 06:07 config-3.19.0-31-lowlatency
-rw-r--r--  1 root root   177790 Oct 22 05:14 config-3.19.0-32-generic
-rw-r--r--  1 root root   177720 Oct 22 07:10 config-3.19.0-32-lowlatency
drwxr-xr-x  3 root root     4096 Oct 26 17:17 extlinux
drwxr-xr-x  5 root root     4096 Oct 24 07:23 grub
-rw-r--r--  1 root root 21547729 Sep 11 09:33 initrd.img-3.13.0-64-lowlatency
-rw-r--r--  1 root root 21546926 Oct 15 09:52 initrd.img-3.13.0-66-lowlatency
-rw-r--r--  1 root root 21545659 Oct 22 13:19 initrd.img-3.13.0-67-lowlatency
-rw-r--r--  1 root root 22200403 Aug 23 09:29 initrd.img-3.19.0-26-generic
-rw-r--r--  1 root root 22160581 Aug 23 09:27 initrd.img-3.19.0-26-lowlatency
-rw-r--r--  1 root root 22200153 Aug 23 09:55 initrd.img-3.19.0-27-generic
-rw-r--r--  1 root root 22161561 Aug 23 09:54 initrd.img-3.19.0-27-lowlatency
-rw-r--r--  1 root root 22198060 Sep  2 20:03 initrd.img-3.19.0-28-generic
-rw-r--r--  1 root root 22159001 Sep 11 09:37 initrd.img-3.19.0-28-lowlatency
-rw-r--r--  1 root root 22204423 Sep 11 20:38 initrd.img-3.19.0-29-generic
-rw-r--r--  1 root root 22164209 Oct 15 10:10 initrd.img-3.19.0-29-lowlatency
-rw-r--r--  1 root root 22204563 Oct 15 10:06 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root 22162744 Oct 15 10:13 initrd.img-3.19.0-31-lowlatency
-rw-r--r--  1 root root 22204297 Oct 24 07:22 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 22161990 Oct 24 07:21 initrd.img-3.19.0-32-lowlatency
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389803 Sep  9 07:31 System.map-3.13.0-64-lowlatency
-rw-------  1 root root  3390076 Oct  7 10:16 System.map-3.13.0-66-lowlatency
-rw-------  1 root root  3390140 Oct 20 09:27 System.map-3.13.0-67-lowlatency
-rw-------  1 root root  3626965 Aug 12 08:26 System.map-3.19.0-26-generic
-rw-------  1 root root  3629495 Aug 12 09:14 System.map-3.19.0-26-lowlatency
-rw-------  1 root root  3626779 Aug 15 20:06 System.map-3.19.0-27-generic
-rw-------  1 root root  3629309 Aug 15 20:50 System.map-3.19.0-27-lowlatency
-rw-------  1 root root  3626779 Sep  1 04:08 System.map-3.19.0-28-generic
-rw-------  1 root root  3629309 Sep  1 04:58 System.map-3.19.0-28-lowlatency
-rw-------  1 root root  3627906 Sep 10 04:00 System.map-3.19.0-29-generic
-rw-------  1 root root  3630436 Sep 10 04:55 System.map-3.19.0-29-lowlatency
-rw-------  1 root root  3628177 Oct  8 05:01 System.map-3.19.0-31-generic
-rw-------  1 root root  3630708 Oct  8 06:07 System.map-3.19.0-31-lowlatency
-rw-------  1 root root  3628149 Oct 22 05:14 System.map-3.19.0-32-generic
-rw-------  1 root root  3630711 Oct 22 07:10 System.map-3.19.0-32-lowlatency
-rw-------  1 root root  5823200 Sep  9 07:31 vmlinuz-3.13.0-64-lowlatency
-rw-------  1 root root  5822688 Oct  7 10:16 vmlinuz-3.13.0-66-lowlatency
-rw-------  1 root root  5822848 Oct 20 09:27 vmlinuz-3.13.0-67-lowlatency
-rw-------  1 root root  6570192 Aug 12 08:26 vmlinuz-3.19.0-26-generic
-rw-------  1 root root  6585552 Aug 12 09:14 vmlinuz-3.19.0-26-lowlatency
-rw-------  1 root root  6569552 Aug 15 20:06 vmlinuz-3.19.0-27-generic
-rw-------  1 root root  6583984 Aug 15 20:50 vmlinuz-3.19.0-27-lowlatency
-rw-------  1 root root  6568848 Sep  1 04:08 vmlinuz-3.19.0-28-generic
-rw-------  1 root root  6583184 Sep  1 04:58 vmlinuz-3.19.0-28-lowlatency
-rw-------  1 root root  6572880 Sep 10 04:00 vmlinuz-3.19.0-29-generic
-rw-------  1 root root  6587280 Sep 10 04:55 vmlinuz-3.19.0-29-lowlatency
-rw-------  1 root root  6572336 Oct  8 05:01 vmlinuz-3.19.0-31-generic
-rw-------  1 root root  6584720 Oct  8 06:07 vmlinuz-3.19.0-31-lowlatency
-rw-------  1 root root  6572944 Oct 22 05:14 vmlinuz-3.19.0-32-generic
-rw-------  1 root root  6584112 Oct 22 07:10 vmlinuz-3.19.0-32-lowlatency


```

One thing: 

```
drwxr-xr-x  3 root root     4096 Oct 26 17:17 extlinux
drwxr-xr-x  5 root root     4096 Oct 24 07:23 grub
```

extlinus and grub are highlighted in blue.

```
dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                              amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                                              1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-vivid                                     3.19.0.32.19                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-64                                     3.13.0-64.104                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-64-lowlatency                          3.13.0-64.104                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                                     3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-lowlatency                          3.13.0-66.108                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                                     3.13.0-67.109                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-lowlatency                          3.13.0-67.109                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26                                     3.19.0-26.28~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                             3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26-lowlatency                          3.19.0-26.28~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-27                                     3.19.0-27.29~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-27-generic                             3.19.0-27.29~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-27-lowlatency                          3.19.0-27.29~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                                     3.19.0-28.30~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                             3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28-lowlatency                          3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-29                                     3.19.0-29.31~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-29-generic                             3.19.0-29.31~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-29-lowlatency                          3.19.0-29.31~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                                     3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                             3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31-lowlatency                          3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32                                     3.19.0-32.37~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-32-generic                             3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32-lowlatency                          3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                             3.19.0.32.19                                        amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                                    3.13.0.67.73                                        amd64        lowlatency Linux kernel headers
ii  linux-headers-lowlatency-lts-vivid                          3.19.0.32.19                                        amd64        lowlatency Linux kernel headers
ii  linux-image-3.13.0-64-lowlatency                            3.13.0-64.104                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-lowlatency                            3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-lowlatency                            3.13.0-67.109                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                               3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-lowlatency                            3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-27-generic                               3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-27-lowlatency                            3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                               3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-lowlatency                            3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-29-generic                               3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-29-lowlatency                            3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-lowlatency                            3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-lowlatency                            3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-27-generic                         3.19.0-27.29~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-29-generic                         3.19.0-29.31~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                               3.19.0.32.19                                        amd64        Generic Linux kernel image
ii  linux-image-lowlatency                                      3.13.0.67.73                                        amd64        lowlatency Linux kernel image
ii  linux-image-lowlatency-lts-vivid                            3.19.0.32.19                                        amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-67.109                                       amd64        Linux Kernel Headers for development
ii  linux-lowlatency                                            3.13.0.67.73                                        amd64        Complete lowlatency Linux kernel
ii  linux-lowlatency-lts-vivid                                  3.19.0.32.19                                        amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-wlan-ng                                               0.2.9+dfsg-5                                        amd64        utilities for wireless prism2 cards
ii  linux-wlan-ng-doc                                           0.2.9+dfsg-5                                        all          documentation for wlan-ng
ii  linux-wlan-ng-firmware                                      0.2.9+dfsg-5                                        all          firmware files used by the linux-wlan-ng driver
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)


```

```
and I craft us up a handy dandy to remove all the old kernels we no longer want/need.
```

Cool, getting into sorcery now!

Be back in the AM.

---

### Post by Bashing-om on 2015-10-26
33Nicolas; Yepper, again ..

-25 kernel is gone gone .

onto bigger things:
```

sudo dpkg -P linux-image-3.13.0-{64,66,67}-lowlatency
sudo dpkg -P linux-headers-3.13.0-{64,66,67}-lowlatency
sudo dpkg -P linux-headers-3.13.0-{64,66,67}

sudo dpkg -P linux-image-3.19.0-{26,27,28,29}-generic
sudo dpkg -P linux-image-3.19.0-{26,27,28,29}-lowlatency
sudo dpkg -P linux-headers-3.19.0-{26,27,28,29}-generic
sudo dpkg -P linux-headers-3.19.0-{26,27,28,29}-lowlatency
sudo dpkg -P linux-headers-3.19.0-{26,27,28,29}
sudo dpkg -P linux-image-extra-3.19.0-{26,27,28,29}-generic

sudo apt-get purge linux-image-lowlatency
sudo apt-get purge linux-libc-dev:amd64
sudo apt-get purge linux-lowlatency

```

Could be handier dandier, but tired now and this suits my cognitive powers.

When these run, we do a final cleanup and call it good.

As to :
> 
So why would the ASLA drier be compressed? The system doesn't need it?

You probably downloaded the driver at some point and the installer chose to put the tar in this directory (??) .

> 
extlinus and grub are highlighted in blue.

Yep .. niceity that in your terminal, directories are highlighted in blue .
" drwxr-xr-x " the leading 'd' denotes too that this is a directory .
------------------
Now may we return to the original question ? starting  the desktop .

[INDENT][INDENT]we make it so
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-27
Bashing-Om, here we go again,

```
sudo dpkg -P linux-image-3.13.0-{64,66,67}-lowlatency
(Reading database ... 647469 files and directories currently installed.)
Removing linux-image-3.13.0-64-lowlatency (3.13.0-64.104) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-64-lowlatency /boot/vmlinuz-3.13.0-64-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-64-lowlatency /boot/vmlinuz-3.13.0-64-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.13.0-64-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-64-lowlatency /boot/vmlinuz-3.13.0-64-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-64-lowlatency /boot/vmlinuz-3.13.0-64-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-27-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-26-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-66-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-66-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.13.0-64-lowlatency (3.13.0-64.104) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-64-lowlatency /boot/vmlinuz-3.13.0-64-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-64-lowlatency /boot/vmlinuz-3.13.0-64-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-66-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-64-lowlatency /boot/vmlinuz-3.13.0-64-lowlatency
Removing linux-image-3.13.0-66-lowlatency (3.13.0-66.108) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-66-lowlatency /boot/vmlinuz-3.13.0-66-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-66-lowlatency /boot/vmlinuz-3.13.0-66-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.13.0-66-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-66-lowlatency /boot/vmlinuz-3.13.0-66-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-66-lowlatency /boot/vmlinuz-3.13.0-66-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-27-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-26-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.13.0-66-lowlatency (3.13.0-66.108) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-66-lowlatency /boot/vmlinuz-3.13.0-66-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-66-lowlatency /boot/vmlinuz-3.13.0-66-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-66-lowlatency /boot/vmlinuz-3.13.0-66-lowlatency
dpkg: dependency problems prevent removal of linux-image-3.13.0-67-lowlatency:
 linux-image-lowlatency depends on linux-image-3.13.0-67-lowlatency.

dpkg: error processing package linux-image-3.13.0-67-lowlatency (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.13.0-67-lowlatency


```

So something's still hanging on to the 3.13 kernel?

```
sudo dpkg -P linux-headers-3.13.0-{64,66,67}-lowlatency
(Reading database ... 637841 files and directories currently installed.)
Removing linux-headers-3.13.0-64-lowlatency (3.13.0-64.104) ...
Removing linux-headers-3.13.0-66-lowlatency (3.13.0-66.108) ...
dpkg: dependency problems prevent removal of linux-headers-3.13.0-67-lowlatency:
 linux-headers-lowlatency depends on linux-headers-3.13.0-67-lowlatency.

dpkg: error processing package linux-headers-3.13.0-67-lowlatency (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.13.0-67-lowlatency
```

```
sudo dpkg -P linux-headers-3.13.0-{64,66,67}
(Reading database ... 618731 files and directories currently installed.)
Removing linux-headers-3.13.0-64 (3.13.0-64.104) ...
Removing linux-headers-3.13.0-66 (3.13.0-66.108) ...
dpkg: dependency problems prevent removal of linux-headers-3.13.0-67:
 linux-headers-3.13.0-67-lowlatency depends on linux-headers-3.13.0-67.

dpkg: error processing package linux-headers-3.13.0-67 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.13.0-67


```

```
sudo dpkg -P linux-image-3.19.0-{26,27,28,29}-generic
dpkg: dependency problems prevent removal of linux-image-3.19.0-26-generic:
 linux-image-extra-3.19.0-26-generic depends on linux-image-3.19.0-26-generic.

dpkg: error processing package linux-image-3.19.0-26-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.19.0-27-generic:
 linux-image-extra-3.19.0-27-generic depends on linux-image-3.19.0-27-generic.

dpkg: error processing package linux-image-3.19.0-27-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.19.0-28-generic:
 linux-image-extra-3.19.0-28-generic depends on linux-image-3.19.0-28-generic.

dpkg: error processing package linux-image-3.19.0-28-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.19.0-29-generic:
 linux-image-extra-3.19.0-29-generic depends on linux-image-3.19.0-29-generic.

dpkg: error processing package linux-image-3.19.0-29-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.19.0-26-generic
 linux-image-3.19.0-27-generic
 linux-image-3.19.0-28-generic
 linux-image-3.19.0-29-generic


```

```
sudo dpkg -P linux-image-3.19.0-{26,27,28,29}-lowlatency
(Reading database ... 588217 files and directories currently installed.)
Removing linux-image-3.19.0-26-lowlatency (3.19.0-26.28~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-26-lowlatency /boot/vmlinuz-3.19.0-26-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-lowlatency /boot/vmlinuz-3.19.0-26-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.19.0-26-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-26-lowlatency /boot/vmlinuz-3.19.0-26-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-lowlatency /boot/vmlinuz-3.19.0-26-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-27-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-26-lowlatency (3.19.0-26.28~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-lowlatency /boot/vmlinuz-3.19.0-26-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-26-lowlatency /boot/vmlinuz-3.19.0-26-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-lowlatency /boot/vmlinuz-3.19.0-26-lowlatency
Removing linux-image-3.19.0-27-lowlatency (3.19.0-27.29~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-27-lowlatency /boot/vmlinuz-3.19.0-27-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-27-lowlatency /boot/vmlinuz-3.19.0-27-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.19.0-27-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-27-lowlatency /boot/vmlinuz-3.19.0-27-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-27-lowlatency /boot/vmlinuz-3.19.0-27-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-28-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-27-lowlatency (3.19.0-27.29~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-27-lowlatency /boot/vmlinuz-3.19.0-27-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-27-lowlatency /boot/vmlinuz-3.19.0-27-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-27-lowlatency /boot/vmlinuz-3.19.0-27-lowlatency
Removing linux-image-3.19.0-28-lowlatency (3.19.0-28.30~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-28-lowlatency /boot/vmlinuz-3.19.0-28-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-lowlatency /boot/vmlinuz-3.19.0-28-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.19.0-28-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-28-lowlatency /boot/vmlinuz-3.19.0-28-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-lowlatency /boot/vmlinuz-3.19.0-28-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-29-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-28-lowlatency (3.19.0-28.30~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-lowlatency /boot/vmlinuz-3.19.0-28-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-28-lowlatency /boot/vmlinuz-3.19.0-28-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-lowlatency /boot/vmlinuz-3.19.0-28-lowlatency
Removing linux-image-3.19.0-29-lowlatency (3.19.0-29.31~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-29-lowlatency /boot/vmlinuz-3.19.0-29-lowlatency
dkms: removing: nvidia-304 304.128 (3.19.0-29-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-304
Version: 304.128
Kernel:  3.19.0-29-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_304.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-29-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-29-lowlatency /boot/vmlinuz-3.19.0-29-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.19.0-29-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-29-lowlatency /boot/vmlinuz-3.19.0-29-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-29-lowlatency /boot/vmlinuz-3.19.0-29-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-29-lowlatency (3.19.0-29.31~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-29-lowlatency /boot/vmlinuz-3.19.0-29-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-29-lowlatency /boot/vmlinuz-3.19.0-29-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-29-lowlatency /boot/vmlinuz-3.19.0-29-lowlatency


```

```
sudo dpkg -P linux-headers-3.19.0-{26,27,28,29}-generic
(Reading database ... 567323 files and directories currently installed.)
Removing linux-headers-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
Removing linux-headers-3.19.0-27-generic (3.19.0-27.29~14.04.1) ...
Removing linux-headers-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Removing linux-headers-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...


```

That looks like good news, no?

```
sudo dpkg -P linux-headers-3.19.0-{26,27,28,29}-lowlatency
(Reading database ... 530779 files and directories currently installed.)
Removing linux-headers-3.19.0-26-lowlatency (3.19.0-26.28~14.04.1) ...
Removing linux-headers-3.19.0-27-lowlatency (3.19.0-27.29~14.04.1) ...
Removing linux-headers-3.19.0-28-lowlatency (3.19.0-28.30~14.04.1) ...
Removing linux-headers-3.19.0-29-lowlatency (3.19.0-29.31~14.04.1) ...


```

```
sudo dpkg -P linux-headers-3.19.0-{26,27,28,29}
(Reading database ... 494279 files and directories currently installed.)
Removing linux-headers-3.19.0-26 (3.19.0-26.28~14.04.1) ...
Removing linux-headers-3.19.0-27 (3.19.0-27.29~14.04.1) ...
Removing linux-headers-3.19.0-28 (3.19.0-28.30~14.04.1) ...
Removing linux-headers-3.19.0-29 (3.19.0-29.31~14.04.1) ...


```

```
sudo dpkg -P linux-image-extra-3.19.0-{26,27,28,29}-generic
(Reading database ... 430987 files and directories currently installed.)
Removing linux-image-extra-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Error! Your kernel headers for kernel 3.19.0-26-generic cannot be found.
Please install the linux-headers-3.19.0-26-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-26-generic
live-boot: core filesystems devices utils memdisk udev wget blockdev.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-extra-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
Removing linux-image-extra-3.19.0-27-generic (3.19.0-27.29~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
Error! Your kernel headers for kernel 3.19.0-27-generic cannot be found.
Please install the linux-headers-3.19.0-27-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-27-generic
live-boot: core filesystems devices utils memdisk udev wget blockdev.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-extra-3.19.0-27-generic (3.19.0-27.29~14.04.1) ...
Removing linux-image-extra-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Error! Your kernel headers for kernel 3.19.0-28-generic cannot be found.
Please install the linux-headers-3.19.0-28-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-28-generic
live-boot: core filesystems devices utils memdisk udev wget blockdev.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-extra-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Removing linux-image-extra-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
Error! Your kernel headers for kernel 3.19.0-29-generic cannot be found.
Please install the linux-headers-3.19.0-29-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-29-generic
live-boot: core filesystems devices utils memdisk udev wget blockdev.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.13.0-67-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-67-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-extra-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...


```

```
sudo apt-get purge linux-image-lowlatency
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-lowlatency linux-image-3.13.0-67-lowlatency
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-lowlatency* linux-lowlatency*
0 upgraded, 0 newly installed, 2 to remove and 5 not upgraded.
After this operation, 59.4 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 414049 files and directories currently installed.)
Removing linux-lowlatency (3.13.0.67.73) ...
Removing linux-image-lowlatency (3.13.0.67.73) ...
```

```
sudo apt-get purge linux-libc-dev:amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  docbook-to-man gir1.2-gtk-2.0 libcairo-script-interpreter2 libffi-dev
  libgvpr2 libharfbuzz-dev libharfbuzz-gobject0 libice-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev linux-headers-lowlatency
  linux-image-3.13.0-67-lowlatency sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  build-essential* dh-autoreconf* dh-buildinfo* g++* g++-4.8* gnome-common*
  graphviz-dev* gtk-doc-tools* kernel-package* libatk1.0-dev* libc6-dev*
  libcairo2-dev* libexpat1-dev* libfontconfig1-dev* libfreetype6-dev*
  libgdk-pixbuf2.0-dev* libglib2.0-dev* libgraphviz-dev* libgtk2.0-dev*
  libpango1.0-dev* libpcre3-dev* libpng12-dev* libpython-dev*
  libpython2.7-dev* libstdc++-4.8-dev* libtool* libxft-dev* linux-libc-dev*
  linux-wlan-ng-firmware* nvidia-304* python-dev* python-gi-dev*
  python-gobject-2-dev* python-gobject-dev* python-gtk2-dev* python-qt4-dev*
  python-sip-dev* python2.7-dev* tcl-dev* tcl8.6-dev* tk-dev* tk8.6-dev*
  zlib1g-dev*
0 upgraded, 0 newly installed, 43 to remove and 5 not upgraded.
After this operation, 325 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 414043 files and directories currently installed.)
Removing linux-wlan-ng-firmware (0.2.9+dfsg-5) ...
Removing kernel-package (12.036+nmu3) ...
Purging configuration files for kernel-package (12.036+nmu3) ...
Removing dh-autoreconf (9) ...
Removing dh-buildinfo (0.10ubuntu1) ...
Removing gtk-doc-tools (1.20-1ubuntu1) ...
Purging configuration files for gtk-doc-tools (1.20-1ubuntu1) ...
Removing gnome-common (3.10.0-1) ...
Removing graphviz-dev (2.36.0-0ubuntu3.1) ...
Removing python-gtk2-dev (2.24.0-3ubuntu3) ...
Removing libgtk2.0-dev (2.24.23-0ubuntu1.3) ...
Removing libatk1.0-dev (2.10.0-2ubuntu2) ...
Removing libpango1.0-dev (1.36.3-1ubuntu1.1) ...
Removing libcairo2-dev (1.13.0~20140204-0ubuntu1.1) ...
Removing nvidia-304 (304.128-0ubuntu0.0.1) ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-304
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-304 (304.128-0ubuntu0.0.1) ...
update-initramfs: deferring update (trigger activated)
Removing python-qt4-dev (4.10.4+dfsg-1ubuntu1) ...
Removing python-sip-dev (4.15.5-1build1) ...
Removing tk-dev:amd64 (8.6.0+6ubuntu3) ...
Removing tk8.6-dev:amd64 (8.6.1-3ubuntu2) ...
Removing libxft-dev (2.3.1-2) ...
Removing libgdk-pixbuf2.0-dev (2.30.7-0ubuntu1.2) ...
Removing python-gobject-dev (3.12.0-1ubuntu1) ...
Removing python-gi-dev (3.12.0-1ubuntu1) ...
Removing python-gobject-2-dev (2.28.6-12build1) ...
Removing libglib2.0-dev (2.40.2-0ubuntu1) ...
Removing libgraphviz-dev (2.36.0-0ubuntu3.1) ...
Removing libpcre3-dev:amd64 (1:8.31-2ubuntu2.1) ...
Removing libtool (2.4.2-1.7ubuntu1) ...
Removing tcl-dev:amd64 (8.6.0+6ubuntu3) ...
Removing tcl8.6-dev:amd64 (8.6.1-4ubuntu1) ...
Removing build-essential (11.6ubuntu6) ...
Removing g++ (4:4.8.2-1ubuntu6) ...
Removing g++-4.8 (4.8.4-2ubuntu1~14.04) ...
Removing libstdc++-4.8-dev:amd64 (4.8.4-2ubuntu1~14.04) ...
Removing libfontconfig1-dev (2.11.0-0ubuntu4.1) ...
Removing libfreetype6-dev (2.5.2-1ubuntu2.5) ...
Removing python-dev (2.7.5-5ubuntu3) ...
Removing python2.7-dev (2.7.6-8ubuntu0.2) ...
Removing libpng12-dev (1.2.50-1ubuntu2) ...
Removing libpython-dev:amd64 (2.7.5-5ubuntu3) ...
Removing libpython2.7-dev:amd64 (2.7.6-8ubuntu0.2) ...
Removing zlib1g-dev:amd64 (1:1.2.8.dfsg-1ubuntu1) ...
Removing libexpat1-dev:amd64 (2.1.0-4ubuntu1.1) ...
Removing libc6-dev:amd64 (2.19-0ubuntu6.6) ...
Removing linux-libc-dev:amd64 (3.13.0-67.109) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-32-lowlatency
live-boot: core filesystems devices utils memdisk udev wget blockdev.
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for doc-base (0.10.5) ...
Processing 3 removed doc-base files...
Registering documents with scrollkeeper...
```

```
sudo apt-get purge linux-lowlatency
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-lowlatency' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev linux-headers-lowlatency
  linux-image-3.13.0-67-lowlatency nvidia-settings screen-resolution-extra
  sip-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.


```

One step closer?

Software Updater wants me to update. It's not showing me what. Should I?

I won;t be back till this afternoon. Thanks again Bashing-Om.

---

### Post by Bashing-om on 2015-10-27
33Nicolas; Yuk .. or YaH !

As the case may be.


Give me a bit of time to look over this latest development . Not at all happy !

However .. it do give us a huge glimmer of what is going on with the desktop and where that unknown dialog box is comming from:
> 
dpkg -l | grep linux- >>
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy

bk
P: Installing debian theme... done.



Now huh ?? the -26 kernel should be long gone ... why then:
> 
P: Writing config for /boot/vmlinuz-3.19.0-26-lowlatency...

Ditto ^^
P: Writing config for /boot/vmlinuz-3.13.0-67-lowlatency...


Huh ?? removing the nvidia driver ... why ?
> 
dkms: removing: nvidia-304 304.128 (3.19.0-29-lowlatency) (x86_64)

I must wonder --- what have you been doing ??

--------------------
> 
One step closer?

Honestly .... I do not know... 

Back up and regroup .. see where we stand:
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux
sudo apt-get -f install
sudo dpkg -C

```
And for the graphics driver situation:
```

sudo lshw -C display
dpkg -l | grep -i nvidia
sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```

A lot is going on here to address .. the 1st order is always the kernel and how the system relates with the kernel.
We keep our focus on getting the kernel situation correct.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-27
Bashing-Om, yup, dunno!

My only thought is I must have been intoxicated one night playing music and downloaded some things? I noticed Mint has a roll back feature. Not sure it is on my U-Studio distribution, but I would like to look into this before I become proficient enough to use the comman prompt, if ever. I think learning Chinese in school was easier ;)

I do remember looking into other desktop managers, which was the ceginning of the problems, hence the Debian I wrongly thought were compatible with U-Studio.

```
Huh ?? removing the nvidia driver ... why ?
```

Even weirder, I don't think I have an nvidea card on this dinosaur.

I'll be back in the pm to tackle the rest.

Thanks again!

Bashing-Om, and now for the display weirdness:

```
sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: NV44 [Quadro NVS 285]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:30 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff memory:efe00000-efe1ffff


```

I guess I do have an Nvidea card. Go figure. And all 33MHz of it!

```
dpkg -l | grep -i nvidia
ii  libcuda1-304                                                304.128-0ubuntu0.0.1                                amd64        NVIDIA CUDA runtime library
rc  nvidia-libopencl1-304                                       304.125-0ubuntu0.0.2                                amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304                                       304.128-0ubuntu0.0.1                                amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                             331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver


```

```
sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000165sv000010DEsd00000334bc03sc00i00
vendor   : NVIDIA Corporation
model    : NV44 [Quadro NVS 285]
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304 - distro non-free recommended
driver   : nvidia-304-updates - distro non-free


```

Free and non-free, that's weird, but I remember using all the suggested updates from Ubuntu, including commercial, if applicable.

```
sudo ubuntu-drivers list
nvidia-304
nvidia-304-updates


```

That's it. I'm afraid to ask...

---

### Post by Bashing-om on 2015-10-27
33Nicolas; Well, well .. all so far 

all is well ..
The outputs tell the graphic's card (Nvidia NVS 285), that presently you are running on the open source 'nouveau' driver and that at some time  the proprietary 304 driver was installed and in use.
under " ubuntu-drivers devices" a lot of useful info .. it also shows us all the drivers that are available for the card.
I am real happy to remain on nouveau if the system likes it and you are satisfied. Looks good to me !

Now how 'bout we return to the kernel situation ... see if we can find out what is not up with the kernels. 
From square 1, one more time:
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux
sudo apt-get -f install
sudo dpkg -C

```

If 'dpkg -C' has nothing but good to say, in this case it will say nothing. Will just get a return to prompt .

'cause; we got to have that firm foundation
[INDENT][INDENT]to come out swinging from
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-27
Bashing-Om,

I'm happy using open source software and drivers. The more, the happier, so we can stay with nouveau.

```
uname -r
3.19.0-32-lowlatency


```

I'm not sure which is the latest kernel. 4.2?

```
ls -al /usr/src/
total 4044
drwxr-xr-x 12 root root    4096 Oct 27 08:30 .
drwxr-xr-x 11 root root    4096 Aug 23 08:41 ..
-rw-r--r--  1 root root 4091128 Feb 13  2013 alsa-driver.tar.bz2
drwxr-sr-x  5 root src     4096 Nov 28  2010 aufs2-util
drwxr-xr-x 24 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67
drwxr-xr-x  7 root root    4096 Oct 22 13:16 linux-headers-3.13.0-67-lowlatency
drwxr-xr-x 24 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31
drwxr-xr-x  7 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31-generic
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.19.0-31-lowlatency
drwxr-xr-x 24 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-generic
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-lowlatency
drwxr-xr-x  4 root root    4096 Oct 19  2009 modules


```

```
ls -al /lib/modules/

```

```
ls -al /boot/
total 240788
drwxr-xr-x  4 root root     4096 Oct 27 08:31 .
drwxr-xr-x 26 root root     4096 Oct 24 07:19 ..
-rw-r--r--  1 root root  1166024 Oct 20 09:27 abi-3.13.0-67-lowlatency
-rw-r--r--  1 root root  1270654 Aug 12 08:26 abi-3.19.0-26-generic
-rw-r--r--  1 root root  1271100 Aug 15 20:06 abi-3.19.0-27-generic
-rw-r--r--  1 root root  1271100 Sep  1 04:08 abi-3.19.0-28-generic
-rw-r--r--  1 root root  1271869 Sep 10 04:00 abi-3.19.0-29-generic
-rw-r--r--  1 root root  1271689 Oct  8 05:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root  1272453 Oct  8 06:07 abi-3.19.0-31-lowlatency
-rw-r--r--  1 root root  1271689 Oct 22 05:14 abi-3.19.0-32-generic
-rw-r--r--  1 root root  1272453 Oct 22 07:10 abi-3.19.0-32-lowlatency
-rw-r--r--  1 root root   165765 Oct 20 09:27 config-3.13.0-67-lowlatency
-rw-r--r--  1 root root   177632 Aug 12 08:26 config-3.19.0-26-generic
-rw-r--r--  1 root root   177651 Aug 15 20:06 config-3.19.0-27-generic
-rw-r--r--  1 root root   177651 Sep  1 04:08 config-3.19.0-28-generic
-rw-r--r--  1 root root   177732 Sep 10 04:00 config-3.19.0-29-generic
-rw-r--r--  1 root root   177790 Oct  8 05:01 config-3.19.0-31-generic
-rw-r--r--  1 root root   177720 Oct  8 06:07 config-3.19.0-31-lowlatency
-rw-r--r--  1 root root   177790 Oct 22 05:14 config-3.19.0-32-generic
-rw-r--r--  1 root root   177720 Oct 22 07:10 config-3.19.0-32-lowlatency
drwxr-xr-x  3 root root     4096 Oct 27 08:10 extlinux
drwxr-xr-x  5 root root     4096 Oct 27 08:30 grub
-rw-r--r--  1 root root 21545659 Oct 22 13:19 initrd.img-3.13.0-67-lowlatency
-rw-r--r--  1 root root  7967729 Oct 27 08:09 initrd.img-3.19.0-26-generic
-rw-r--r--  1 root root  7968801 Oct 27 08:09 initrd.img-3.19.0-27-generic
-rw-r--r--  1 root root  7968718 Oct 27 08:10 initrd.img-3.19.0-28-generic
-rw-r--r--  1 root root  7967640 Oct 27 08:10 initrd.img-3.19.0-29-generic
-rw-r--r--  1 root root 22204563 Oct 15 10:06 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root 22162744 Oct 15 10:13 initrd.img-3.19.0-31-lowlatency
-rw-r--r--  1 root root 22204297 Oct 24 07:22 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 22164123 Oct 27 08:31 initrd.img-3.19.0-32-lowlatency
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3390140 Oct 20 09:27 System.map-3.13.0-67-lowlatency
-rw-------  1 root root  3626965 Aug 12 08:26 System.map-3.19.0-26-generic
-rw-------  1 root root  3626779 Aug 15 20:06 System.map-3.19.0-27-generic
-rw-------  1 root root  3626779 Sep  1 04:08 System.map-3.19.0-28-generic
-rw-------  1 root root  3627906 Sep 10 04:00 System.map-3.19.0-29-generic
-rw-------  1 root root  3628177 Oct  8 05:01 System.map-3.19.0-31-generic
-rw-------  1 root root  3630708 Oct  8 06:07 System.map-3.19.0-31-lowlatency
-rw-------  1 root root  3628149 Oct 22 05:14 System.map-3.19.0-32-generic
-rw-------  1 root root  3630711 Oct 22 07:10 System.map-3.19.0-32-lowlatency
-rw-------  1 root root  5822848 Oct 20 09:27 vmlinuz-3.13.0-67-lowlatency
-rw-------  1 root root  6570192 Aug 12 08:26 vmlinuz-3.19.0-26-generic
-rw-------  1 root root  6569552 Aug 15 20:06 vmlinuz-3.19.0-27-generic
-rw-------  1 root root  6568848 Sep  1 04:08 vmlinuz-3.19.0-28-generic
-rw-------  1 root root  6572880 Sep 10 04:00 vmlinuz-3.19.0-29-generic
-rw-------  1 root root  6572336 Oct  8 05:01 vmlinuz-3.19.0-31-generic
-rw-------  1 root root  6584720 Oct  8 06:07 vmlinuz-3.19.0-31-lowlatency
-rw-------  1 root root  6572944 Oct 22 05:14 vmlinuz-3.19.0-32-generic
-rw-------  1 root root  6584112 Oct 22 07:10 vmlinuz-3.19.0-32-lowlatency


```

```
dpkg -l | grep linux
ii  extlinux                                                    3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders (ext2/3/4 and btrfs bootloader)
ii  fonts-linuxlibertine                                        5.3.0-2                                             all          Linux Libertine family of fonts
ii  ladspa-sdk                                                  1.13-2                                              amd64        sample tools for linux-audio-dev plugin architecture
ii  libselinux1:amd64                                           2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                            2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                              1.0.1-1                                             amd64        Collection of video4linux support libraries
rc  libv4l-0:i386                                               1.0.1-1                                             i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                        1.0.1-1                                             amd64        Video4linux frame format conversion library
rc  libv4lconvert0:i386                                         1.0.1-1                                             i386         Video4linux frame format conversion library
ii  linux-firmware                                              1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-vivid                                     3.19.0.32.19                                        amd64        Complete Generic Linux kernel and headers
pi  linux-headers-3.13.0-67                                     3.13.0-67.109                                       all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-67-lowlatency                          3.13.0-67.109                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                                     3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                             3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31-lowlatency                          3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32                                     3.19.0-32.37~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-32-generic                             3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32-lowlatency                          3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                             3.19.0.32.19                                        amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                                    3.13.0.67.73                                        amd64        lowlatency Linux kernel headers
ii  linux-headers-lowlatency-lts-vivid                          3.19.0.32.19                                        amd64        lowlatency Linux kernel headers
pi  linux-image-3.13.0-67-lowlatency                            3.13.0-67.109                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
pi  linux-image-3.19.0-26-generic                               3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
pi  linux-image-3.19.0-27-generic                               3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
pi  linux-image-3.19.0-28-generic                               3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
pi  linux-image-3.19.0-29-generic                               3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-lowlatency                            3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-lowlatency                            3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                               3.19.0.32.19                                        amd64        Generic Linux kernel image
ii  linux-image-lowlatency-lts-vivid                            3.19.0.32.19                                        amd64        lowlatency Linux kernel image
ii  linux-lowlatency-lts-vivid                                  3.19.0.32.19                                        amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-wlan-ng                                               0.2.9+dfsg-5                                        amd64        utilities for wireless prism2 cards
ii  linux-wlan-ng-doc                                           0.2.9+dfsg-5                                        all          documentation for wlan-ng
ii  pptp-linux                                                  1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                                    3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)
ii  util-linux       

```

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev linux-headers-lowlatency
  linux-image-3.13.0-67-lowlatency nvidia-settings screen-resolution-extra
  sip-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.


```

```
sudo dpkg -C
```

Nothing happened with the last command.

On the flipside, I'm starting to remember ls and some of the extensions (?)

---

### Post by Bashing-om on 2015-10-27
33Nicolas; YuK !!!

Tell me it ain't so !
that the directory " ls -al /lib/modules/ " no longer has our modules of all the installed kernels ! You mean it is empty ?

Recheck ... 
Do not reboot or shut this system down !!!

[INDENT][INDENT]I shudder to think[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-27
Oh crap, that's scary.

```
ls -al /lib/modules/ 
total 44
drwxr-xr-x 11 root root 4096 Oct 27 08:07 .
drwxr-xr-x 26 root root 4096 Oct 27 08:30 ..
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.13.0-67-lowlatency
drwxr-xr-x  5 root root 4096 Oct 27 08:09 3.19.0-26-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:09 3.19.0-27-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-28-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-29-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-32-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:30 3.19.0-32-lowlatency


```

Looks like it's here.

Software Updater wants to update GTK, MySQL and Python.

Should I update? Nothing shows kernels.

---

### Post by Bashing-om on 2015-10-27
33Nicolas; K ...

I can rest easier now .. I was in a real fret how to recover if all the modules were no longer there.

Any way, I have had it for this session . Will look over what we now have and come up with a plan.
As is now I see no possible harm in allowing the system to update.

I am going to sleep on it.

[INDENT][INDENT]ain't gonna study 'buntu no more
[INDENT][INDENT][INDENT][INDENT]tonight
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-27
Thanks Bashing-Om, I agree. Back at it tomorrow.

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Morning !

OK, round 4 .
We have the 3.13.0-67 and 3.19.0-26 kernels with a status of "pi" - partially installed.
Let's see if the package manager will deal with them for us . Maybe yes, maybe not so yes.
But, try:
```

sudo apt-get purge linux-image-3.13.0-67-lowlatency
sudo apt-get purge linux-headers-3.13.0-67-lowlatency
sudo apt-get purge linux-headers-3.13.0-67

```

If this poke goes well, we look next at the 3.19.0-26 kernel.
When these are gone gone, what ever it may take, then we must address :
> 
pi  linux-image-3.19.0-27-generic                               3.19.0-27.29~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
pi  linux-image-3.19.0-28-generic                               3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
pi  linux-image-3.19.0-29-generic
 and also get them gone gone,

Which I "thought" we had formerly removed. - If we had removed them ... why have they re-appeared ? - But we go back to the fight, now in very small steps and get these removed from the system, and the package manager in a happy state.

as around and 'round we go
[INDENT][INDENT][INDENT]where it stops
[INDENT][INDENT][INDENT][INDENT]we will find out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Morning Bashing-Om,

Multitasking is the name of the game today.

I don't get the bootup screen anymore, but it boots into that weird desktop session manager.

```
sudo apt-get purge linux-image-3.13.0-67-lowlatency
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev linux-headers-lowlatency nvidia-settings
  screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.13.0-67-lowlatency*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 194 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 408741 files and directories currently installed.)
Removing linux-image-3.13.0-67-lowlatency (3.13.0-67.109) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.13.0-67-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.13.0-67-lowlatency (3.13.0-67.109) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Writing config for /boot/vmlinuz-3.19.0-26-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-67-lowlatency /boot/vmlinuz-3.13.0-67-lowlatency


```

```
sudo apt-get purge linux-headers-3.13.0-67-lowlatency
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.13.0-67-lowlatency* linux-headers-lowlatency*
0 upgraded, 0 newly installed, 2 to remove and 14 not upgraded.
After this operation, 13.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 403927 files and directories currently installed.)
Removing linux-headers-lowlatency (3.13.0.67.73) ...
Removing linux-headers-3.13.0-67-lowlatency (3.13.0-67.109) ...


```

```
sudo apt-get purge linux-headers-3.13.0-67
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.13.0-67*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 63.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 394369 files and directories currently installed.)
Removing linux-headers-3.13.0-67 (3.13.0-67.109) ...


```

For good measure, I'm also learning and doing my due diligence:

```
ls -al /lib/modules/ 
total 40
drwxr-xr-x 10 root root 4096 Oct 28 10:58 .
drwxr-xr-x 26 root root 4096 Oct 27 08:30 ..
drwxr-xr-x  5 root root 4096 Oct 27 08:09 3.19.0-26-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:09 3.19.0-27-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-28-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-29-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-32-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:30 3.19.0-32-lowlatency
```

I read it said removing, is that true? Could it be? Please, please...

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Yeah !

That looks to have done well .. next - in small steps .. as my last sledge hammer approach ended in disaster,, lets attack the 3.19.0 26 kernel.
```

sudo apt-get purge linux-image-3.19.0-26-generic 

```

As we do not have the headers, I can foresee that the package manager is going to balk and again we get dirty.

As to the desktop getting crazy ...
A quick look about - what we have been doing - I do not see anything that affects the desktop .. Hummm ...

[INDENT][INDENT]anyway, small steps
[INDENT][INDENT][INDENT]to the issue at hand
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Hey Bashing-Om,

I could have made a mistake in the sequence of commands, so not necessarily your hammer.

```
sudo apt-get purge linux-image-3.19.0-26-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.19.0-26-generic*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 47.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 379112 files and directories currently installed.)
Removing linux-image-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic


```

And for good measures again:

```
sudo apt-get purge linux-image-3.19.0-26-generic
[sudo] password for suoni: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.19.0-26-generic*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 47.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 379112 files and directories currently installed.)
Removing linux-image-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-27-generic
Found initrd image: /boot/initrd.img-3.19.0-27-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-26-generic (3.19.0-26.28~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Writing config for /boot/vmlinuz-3.19.0-27-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic


```

And that software updater is getting real antsy about updating the system :)

In the meantime, I'm suspending the computer and putting offline to avoid p[roblems.

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Hey;

If what we have to do is interfering with what you have to so ... we can hasten things up .. but I sure feel better in slow easy steps and observe the individual results ...
next -- oooppps I missed the -25 kernel:
Let's back up and try and take care of it .
```

sudo apt-get purge linux-image-extra-3.19.0-25-generic

```

And hope we 
[INDENT][INDENT][INDENT]move merrily on along
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Bashing-On, thanks, but it's not interfering and I welcome the break. 

Let's keep this pace if you're OK. I'm comfortable with it. Promise you I don't take discomfort graciously.

```
sudo apt-get purge linux-image-extra-3.19.0-25-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-extra-3.19.0-25-generic*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 378117 files and directories currently installed.)
Removing linux-image-extra-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...


```

```
ls -al /lib/modules/ 
total 36
drwxr-xr-x  9 root root 4096 Oct 28 13:20 .
drwxr-xr-x 26 root root 4096 Oct 27 08:30 ..
drwxr-xr-x  5 root root 4096 Oct 27 08:09 3.19.0-27-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-28-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-29-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-32-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:30 3.19.0-32-lowlatency


```

.25 is gone, does this mean we move up to .27, etc,? Just curious.

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Yepper ... 

look'n good and we progress right merrily along .. at my slow pace ..
We CAN do this !

Yeah next up is the -27 kernel 
```

sudo apt-get purge linux-image-3.19.0-27-generic

```

still to go is the 28 and 29 kernels .. then we rake a look and verify that all directories match . And if all match we are ready for that final clean up of the system,.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Bashing-Om, thanks for your patience and persistence.

```
sudo apt-get purge linux-image-3.19.0-27-generic
[sudo] password for suoni: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.19.0-27-generic*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 47.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 378117 files and directories currently installed.)
Removing linux-image-3.19.0-27-generic (3.19.0-27.29~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-27-generic (3.19.0-27.29~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Writing config for /boot/vmlinuz-3.19.0-28-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic


```

Indeed, it is gone.

```
ls -al /lib/modules/ 
total 32
drwxr-xr-x  8 root root 4096 Oct 28 14:47 .
drwxr-xr-x 26 root root 4096 Oct 27 08:30 ..
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-28-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-29-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-32-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:30 3.19.0-32-lowlatency


```

I haven't rebooted the computer yet, but will do at the end of the day. I'll look at the module directory to see if by some weird chance they don't appear there.

I haven't updated with the software updater either.

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Yepper;

That too looked good .
Moving on along :
```

sudo apt-get purge linux-image-3.19.0-28-generic

```

and remaining is the -29 kernel. then we can take a looksee, clean up update and reboot .

[INDENT][INDENT]look'n good
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Hey Bashing-Om,

```
sudo apt-get purge linux-image-3.19.0-28-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.19.0-28-generic*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 47.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 377122 files and directories currently installed.)
Removing linux-image-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-29-generic
Found initrd image: /boot/initrd.img-3.19.0-29-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Writing config for /boot/vmlinuz-3.19.0-29-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic


```

```
ls -al /lib/modules/ 
total 28
drwxr-xr-x  7 root root 4096 Oct 28 15:39 .
drwxr-xr-x 26 root root 4096 Oct 27 08:30 ..
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-29-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-32-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:30 3.19.0-32-lowlatency


```

Next, 29, an then 31?

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Hey !

Maybe we get to the end of this after all .
as to :
> 
Next, 29, an then 31?

Yes and NO ; we want to keep the -31 version ( all intact and consistent ) as the backup kernel if it is required for some reason .,.. very cheap insurance .

So let's :
```

sudo apt-get purge linux-image-3.19.0-28-generic

```

And when that completes; now a new look and I do hope we see all versions in all the places match exactly .
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```

IF all matches, we can wipe the sweat off ;
clean up .. update .. and reboot and see what the system has to say now .

[INDENT][INDENT]progress
[INDENT][INDENT][INDENT]even a snail moves
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Bashing-Om, got it.

```
sudo apt-get purge linux-image-3.19.0-28-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-3.19.0-28-generic' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.


```

```
ls -al /usr/src/
total 4036
drwxr-xr-x 10 root root    4096 Oct 28 10:59 .
drwxr-xr-x 11 root root    4096 Aug 23 08:41 ..
-rw-r--r--  1 root root 4091128 Feb 13  2013 alsa-driver.tar.bz2
drwxr-sr-x  5 root src     4096 Nov 28  2010 aufs2-util
drwxr-xr-x 24 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31
drwxr-xr-x  7 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31-generic
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.19.0-31-lowlatency
drwxr-xr-x 24 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-generic
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-lowlatency
drwxr-xr-x  4 root root    4096 Oct 19  2009 modules


```

```
ls -al /lib/modules/
total 28
drwxr-xr-x  7 root root 4096 Oct 28 15:39 .
drwxr-xr-x 26 root root 4096 Oct 27 08:30 ..
drwxr-xr-x  5 root root 4096 Oct 27 08:10 3.19.0-29-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-32-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:30 3.19.0-32-lowlatency


```

```
ls -al /boot/
total 151944
drwxr-xr-x  4 root root     4096 Oct 28 15:39 .
drwxr-xr-x 26 root root     4096 Oct 24 07:19 ..
-rw-r--r--  1 root root  1271869 Sep 10 04:00 abi-3.19.0-29-generic
-rw-r--r--  1 root root  1271689 Oct  8 05:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root  1272453 Oct  8 06:07 abi-3.19.0-31-lowlatency
-rw-r--r--  1 root root  1271689 Oct 22 05:14 abi-3.19.0-32-generic
-rw-r--r--  1 root root  1272453 Oct 22 07:10 abi-3.19.0-32-lowlatency
-rw-r--r--  1 root root   177732 Sep 10 04:00 config-3.19.0-29-generic
-rw-r--r--  1 root root   177790 Oct  8 05:01 config-3.19.0-31-generic
-rw-r--r--  1 root root   177720 Oct  8 06:07 config-3.19.0-31-lowlatency
-rw-r--r--  1 root root   177790 Oct 22 05:14 config-3.19.0-32-generic
-rw-r--r--  1 root root   177720 Oct 22 07:10 config-3.19.0-32-lowlatency
drwxr-xr-x  3 root root     4096 Oct 28 15:39 extlinux
drwxr-xr-x  5 root root     4096 Oct 28 15:39 grub
-rw-r--r--  1 root root  7967640 Oct 27 08:10 initrd.img-3.19.0-29-generic
-rw-r--r--  1 root root 22204563 Oct 15 10:06 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root 22162744 Oct 15 10:13 initrd.img-3.19.0-31-lowlatency
-rw-r--r--  1 root root 22204297 Oct 24 07:22 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 22164123 Oct 27 08:31 initrd.img-3.19.0-32-lowlatency
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3627906 Sep 10 04:00 System.map-3.19.0-29-generic
-rw-------  1 root root  3628177 Oct  8 05:01 System.map-3.19.0-31-generic
-rw-------  1 root root  3630708 Oct  8 06:07 System.map-3.19.0-31-lowlatency
-rw-------  1 root root  3628149 Oct 22 05:14 System.map-3.19.0-32-generic
-rw-------  1 root root  3630711 Oct 22 07:10 System.map-3.19.0-32-lowlatency
-rw-------  1 root root  6572880 Sep 10 04:00 vmlinuz-3.19.0-29-generic
-rw-------  1 root root  6572336 Oct  8 05:01 vmlinuz-3.19.0-31-generic
-rw-------  1 root root  6584720 Oct  8 06:07 vmlinuz-3.19.0-31-lowlatency
-rw-------  1 root root  6572944 Oct 22 05:14 vmlinuz-3.19.0-32-generic
-rw-------  1 root root  6584112 Oct 22 07:10 vmlinuz-3.19.0-32-lowlatency


```

```
dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                              amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                                              1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-vivid                                     3.19.0.32.19                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-31                                     3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                             3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31-lowlatency                          3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32                                     3.19.0-32.37~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-32-generic                             3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32-lowlatency                          3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                             3.19.0.32.19                                        amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency-lts-vivid                          3.19.0.32.19                                        amd64        lowlatency Linux kernel headers
pi  linux-image-3.19.0-29-generic                               3.19.0-29.31~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-lowlatency                            3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-lowlatency                            3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                               3.19.0.32.19                                        amd64        Generic Linux kernel image
ii  linux-image-lowlatency-lts-vivid                            3.19.0.32.19                                        amd64        lowlatency Linux kernel image
ii  linux-lowlatency-lts-vivid                                  3.19.0.32.19                                        amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-wlan-ng                                               0.2.9+dfsg-5                                        amd64        utilities for wireless prism2 cards
ii  linux-wlan-ng-doc                                           0.2.9+dfsg-5                                        all          documentation for wlan-ng
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)


```

Looking good, I think?

[HTML]IF all matches, we can wipe the sweat off ;
clean up .. update .. and reboot and see what the system has to say now .[/HTML]

I'm cancelling the updater in the meantime.

---

### Post by Bashing-om on 2015-10-28
33Nicolas; OOppps ... 

on my last ... 
should have been:
```

sudo apt-get purge linux-image-3.19.0-29-generic

```
We did -28 twice .. had me going to still see the -29 kernel still present .. looked and seen my uh oh .
Remove -29 and now verify:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```

Now can we clean up ?
so close ->
[INDENT][INDENT]yet so far a way
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Bashing-Om, my bad, I should have seen.

```
sudo apt-get purge linux-image-3.19.0-29-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.19.0-29-generic*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 47.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 376127 files and directories currently installed.)
Removing linux-image-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-32-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-31-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb6
done
Purging configuration files for linux-image-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.19.0-32-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-32-generic...
P: Writing config for /boot/vmlinuz-3.19.0-31-lowlatency...
P: Writing config for /boot/vmlinuz-3.19.0-31-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
```

```
ls -al /usr/src/
total 4036
drwxr-xr-x 10 root root    4096 Oct 28 10:59 .
drwxr-xr-x 11 root root    4096 Aug 23 08:41 ..
-rw-r--r--  1 root root 4091128 Feb 13  2013 alsa-driver.tar.bz2
drwxr-sr-x  5 root src     4096 Nov 28  2010 aufs2-util
drwxr-xr-x 24 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31
drwxr-xr-x  7 root root    4096 Oct 15 09:43 linux-headers-3.19.0-31-generic
drwxr-xr-x  7 root root    4096 Oct 15 09:44 linux-headers-3.19.0-31-lowlatency
drwxr-xr-x 24 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-generic
drwxr-xr-x  7 root root    4096 Oct 24 07:15 linux-headers-3.19.0-32-lowlatency
drwxr-xr-x  4 root root    4096 Oct 19  2009 modules


```

```
ls -al /lib/modules/
total 24
drwxr-xr-x  6 root root 4096 Oct 28 16:39 .
drwxr-xr-x 26 root root 4096 Oct 27 08:30 ..
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-31-generic
drwxr-xr-x  5 root root 4096 Oct 15 09:59 3.19.0-31-lowlatency
drwxr-xr-x  5 root root 4096 Oct 27 08:29 3.19.0-32-generic
drwxr-xr-x  5 root root 4096 Oct 27 08:30 3.19.0-32-lowlatency


```

```
ls -al /boot/
total 132776
drwxr-xr-x  4 root root     4096 Oct 28 16:39 .
drwxr-xr-x 26 root root     4096 Oct 24 07:19 ..
-rw-r--r--  1 root root  1271689 Oct  8 05:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root  1272453 Oct  8 06:07 abi-3.19.0-31-lowlatency
-rw-r--r--  1 root root  1271689 Oct 22 05:14 abi-3.19.0-32-generic
-rw-r--r--  1 root root  1272453 Oct 22 07:10 abi-3.19.0-32-lowlatency
-rw-r--r--  1 root root   177790 Oct  8 05:01 config-3.19.0-31-generic
-rw-r--r--  1 root root   177720 Oct  8 06:07 config-3.19.0-31-lowlatency
-rw-r--r--  1 root root   177790 Oct 22 05:14 config-3.19.0-32-generic
-rw-r--r--  1 root root   177720 Oct 22 07:10 config-3.19.0-32-lowlatency
drwxr-xr-x  3 root root     4096 Oct 28 16:39 extlinux
drwxr-xr-x  5 root root     4096 Oct 28 16:39 grub
-rw-r--r--  1 root root 22204563 Oct 15 10:06 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root 22162744 Oct 15 10:13 initrd.img-3.19.0-31-lowlatency
-rw-r--r--  1 root root 22204297 Oct 24 07:22 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 22164123 Oct 27 08:31 initrd.img-3.19.0-32-lowlatency
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3628177 Oct  8 05:01 System.map-3.19.0-31-generic
-rw-------  1 root root  3630708 Oct  8 06:07 System.map-3.19.0-31-lowlatency
-rw-------  1 root root  3628149 Oct 22 05:14 System.map-3.19.0-32-generic
-rw-------  1 root root  3630711 Oct 22 07:10 System.map-3.19.0-32-lowlatency
-rw-------  1 root root  6572336 Oct  8 05:01 vmlinuz-3.19.0-31-generic
-rw-------  1 root root  6584720 Oct  8 06:07 vmlinuz-3.19.0-31-lowlatency
-rw-------  1 root root  6572944 Oct 22 05:14 vmlinuz-3.19.0-32-generic
-rw-------  1 root root  6584112 Oct 22 07:10 vmlinuz-3.19.0-32-lowlatency


```

```
dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                              amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                                              1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-vivid                                     3.19.0.32.19                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-31                                     3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                             3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31-lowlatency                          3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32                                     3.19.0-32.37~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-32-generic                             3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32-lowlatency                          3.19.0-32.37~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                             3.19.0.32.19                                        amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency-lts-vivid                          3.19.0.32.19                                        amd64        lowlatency Linux kernel headers
ii  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-lowlatency                            3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-lowlatency                            3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                               3.19.0.32.19                                        amd64        Generic Linux kernel image
ii  linux-image-lowlatency-lts-vivid                            3.19.0.32.19                                        amd64        lowlatency Linux kernel image
ii  linux-lowlatency-lts-vivid                                  3.19.0.32.19                                        amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-wlan-ng                                               0.2.9+dfsg-5                                        amd64        utilities for wireless prism2 cards
ii  linux-wlan-ng-doc                                           0.2.9+dfsg-5                                        all          documentation for wlan-ng
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)


```

So close, yet so far away... That seems to be a recurring theme these days.

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Yeah !

But we creep closer ! Wow ! they all agree ... Good work !

Now for cleanup:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt update
sudo apt full-upgrade
sudo apt-get -f install

```

Now when all that rums clean .. an no sass and back talk .. we remove no longer required system config files:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package and  purge all removed but not yet purged packages with the following command.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

OK, finally .. reboot
and tell me what the story is.

[INDENT][INDENT][INDENT]are we there yet ?
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Bashing-Om, here we go!

```
sudo apt-get clean

```

Nothing happened, back at prompt.

```
sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done


```

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms docbook-to-man gir1.2-gtk-2.0 lib32gcc1 libc-dev-bin libc6-i386
  libcairo-script-interpreter2 libcuda1-304 libffi-dev libgvpr2
  libharfbuzz-dev libharfbuzz-gobject0 libice-dev libltdl-dev libpcrecpp0
  libpixman-1-dev libsm-dev libxcb-render0-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdot4 libxext-dev
  libxfixes-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  libxss-dev libxt-dev nvidia-settings screen-resolution-extra sip-dev
0 upgraded, 0 newly installed, 34 to remove and 14 not upgraded.
After this operation, 43.2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 375132 files and directories currently installed.)
Removing dkms (2.2.0.3-1.1ubuntu5.14.04.5) ...
Removing docbook-to-man (1:2.0.0-31) ...
Removing gir1.2-gtk-2.0 (2.24.23-0ubuntu1.3) ...
Removing lib32gcc1 (1:4.9.1-0ubuntu1) ...
Removing libc-dev-bin (2.19-0ubuntu6.6) ...
Removing libc6-i386 (2.19-0ubuntu6.6) ...
Removing libcairo-script-interpreter2:amd64 (1.13.0~20140204-0ubuntu1.1) ...
Removing libcuda1-304 (304.128-0ubuntu0.0.1) ...
Removing libffi-dev:amd64 (3.1~rc1+r3.0.13-12) ...
Removing libgvpr2 (2.36.0-0ubuntu3.1) ...
Removing libharfbuzz-dev (0.9.27-1ubuntu1) ...
Removing libharfbuzz-gobject0:amd64 (0.9.27-1ubuntu1) ...
Removing libxt-dev:amd64 (1:1.1.4-1) ...
Removing libsm-dev:amd64 (2:1.2.1-2) ...
Removing libice-dev:amd64 (2:1.0.8-2) ...
Removing libltdl-dev:amd64 (2.4.2-1.7ubuntu1) ...
Removing libpcrecpp0:amd64 (1:8.31-2ubuntu2.1) ...
Removing libpixman-1-dev (0.30.2-2ubuntu1) ...
Removing libxcb-render0-dev:amd64 (1.10-2ubuntu1) ...
Removing libxcb-shm0-dev:amd64 (1.10-2ubuntu1) ...
Removing libxcomposite-dev (1:0.4.4-1) ...
Removing libxcursor-dev:amd64 (1:1.1.14-1) ...
Removing libxdamage-dev:amd64 (1:1.1.4-1ubuntu1) ...
Removing libxdot4 (2.36.0-0ubuntu3.1) ...
Removing libxi-dev (2:1.7.1.901-1ubuntu1.1) ...
Removing libxss-dev:amd64 (1:1.2.2-1) ...
Removing libxfixes-dev:amd64 (1:5.0.1-1ubuntu1.1) ...
Removing libxinerama-dev:amd64 (2:1.1.3-1) ...
Removing libxrandr-dev:amd64 (2:1.4.2-1) ...
Removing libxrender-dev:amd64 (1:0.9.8-1build0.14.04.1) ...
Removing nvidia-settings (331.20-0ubuntu8) ...
Removing screen-resolution-extra (0.17.1) ...
Removing sip-dev (4.15.5-1build1) ...
Removing libxext-dev:amd64 (2:1.3.2-1ubuntu0.0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for doc-base (0.10.5) ...
Processing 1 removed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...


```

```
sudo apt update
Ign http://dl.google.com stable InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                              
Get:1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Get:2 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Get:3 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://security.ubuntu.com trusty-security/main Sources [98.0 kB]        
Hit http://extras.ubuntu.com trusty Release.gpg                                
Get:6 http://dl.google.com stable/main amd64 Packages [1,211 B]                
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Get:7 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [326 kB]
Get:8 http://dl.google.com stable/main i386 Packages [1,184 B]                 
Hit http://extras.ubuntu.com trusty Release                                    
Get:9 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B]  
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:10 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B] 
Get:11 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]   
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:12 http://security.ubuntu.com trusty-security/main amd64 Packages [357 kB] 
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:13 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [638 kB]
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Ign http://dl.google.com stable/main Translation-en_US                         
Get:14 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.canonical.com trusty/partner Sources                        
Get:15 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Get:16 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:17 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Get:18 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Ign https://private-ppa.launchpad.net precise InRelease                        
Get:19 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [327 kB]
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Get:20 http://security.ubuntu.com trusty-security/main i386 Packages [338 kB]  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit https://private-ppa.launchpad.net precise Release                          
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:21 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [618 kB] 
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://archive.canonical.com trusty/partner Translation-en                 
Get:22 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:23 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:24 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:25 http://security.ubuntu.com trusty-security/main Translation-en [194 kB] 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:26 http://security.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:27 http://security.ubuntu.com trusty-security/restricted Translation-en [3,076 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:28 http://security.ubuntu.com trusty-security/universe Translation-en [68.4 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:29 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:30 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:31 http://us.archive.ubuntu.com trusty-updates/main Translation-en [309 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:32 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:33 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,569 B]
Get:34 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [172 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty Release                                
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://ppa.launchpad.net trusty/main i386 Packages             
Hit http://us.archive.ubuntu.com trusty/restricted Sources         
Ign https://private-ppa.launchpad.net precise/main Translation-en  
Hit http://ppa.launchpad.net trusty/main Translation-en            
Hit http://us.archive.ubuntu.com trusty/multiverse Sources               
Hit http://ppa.launchpad.net trusty Release                      
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages        
Hit http://ppa.launchpad.net trusty/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages 
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages   
Hit http://us.archive.ubuntu.com trusty/main i386 Packages        
Hit http://ppa.launchpad.net trusty/main Translation-en           
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages  
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 3,951 kB in 9s (422 kB/s)                                              
Reading package lists... Done


```

```
sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libsctp1 lksctp-tools
The following packages have been kept back:
  libav-tools libavdevice53 libavfilter3 libavformat54
The following packages will be upgraded:
  apport apport-gtk libaudiofile1 libmysqlclient18 mysql-common ntpdate
  openjdk-7-jre openjdk-7-jre-headless python3-apport python3-problem-report
10 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 40.9 MB of archives.
After this operation, 350 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://security.ubuntu.com/ubuntu/ trusty-security/main ntpdate amd64 1:4.2.6.p5+dfsg-3ubuntu2.14.04.5 [57.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main libsctp1 amd64 1.0.15+dfsg-1 [9,226 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/main lksctp-tools amd64 1.0.15+dfsg-1 [51.3 kB]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main libaudiofile1 amd64 0.3.6-2ubuntu0.14.04.1 [93.2 kB]
Get:5 http://security.ubuntu.com/ubuntu/ trusty-security/main mysql-common all 5.5.46-0ubuntu0.14.04.2 [14.1 kB]
Get:6 http://security.ubuntu.com/ubuntu/ trusty-security/main libmysqlclient18 amd64 5.5.46-0ubuntu0.14.04.2 [597 kB]
Get:7 http://security.ubuntu.com/ubuntu/ trusty-security/main openjdk-7-jre amd64 7u85-2.6.1-5ubuntu0.14.04.1 [171 kB]
Get:8 http://security.ubuntu.com/ubuntu/ trusty-security/main openjdk-7-jre-headless amd64 7u85-2.6.1-5ubuntu0.14.04.1 [39.6 MB]
Get:9 http://security.ubuntu.com/ubuntu/ trusty-security/main python3-problem-report all 2.14.1-0ubuntu3.18 [9,926 B]
Get:10 http://security.ubuntu.com/ubuntu/ trusty-security/main python3-apport all 2.14.1-0ubuntu3.18 [75.2 kB]
Get:11 http://security.ubuntu.com/ubuntu/ trusty-security/main apport all 2.14.1-0ubuntu3.18 [182 kB]
Get:12 http://security.ubuntu.com/ubuntu/ trusty-security/main apport-gtk all 2.14.1-0ubuntu3.18 [9,548 B]
Fetched 40.9 MB in 1min 1s (664 kB/s)                                          
(Reading database ... 373903 files and directories currently installed.)
Preparing to unpack .../ntpdate_1%3a4.2.6.p5+dfsg-3ubuntu2.14.04.5_amd64.deb ...
Unpacking ntpdate (1:4.2.6.p5+dfsg-3ubuntu2.14.04.5) over (1:4.2.6.p5+dfsg-3ubuntu2.14.04.4) ...
Preparing to unpack .../libaudiofile1_0.3.6-2ubuntu0.14.04.1_amd64.deb ...
Unpacking libaudiofile1:amd64 (0.3.6-2ubuntu0.14.04.1) over (0.3.6-2) ...
Preparing to unpack .../mysql-common_5.5.46-0ubuntu0.14.04.2_all.deb ...
Unpacking mysql-common (5.5.46-0ubuntu0.14.04.2) over (5.5.44-0ubuntu0.14.04.1) ...
Preparing to unpack .../libmysqlclient18_5.5.46-0ubuntu0.14.04.2_amd64.deb ...
Unpacking libmysqlclient18:amd64 (5.5.46-0ubuntu0.14.04.2) over (5.5.44-0ubuntu0.14.04.1) ...
Selecting previously unselected package libsctp1:amd64.
Preparing to unpack .../libsctp1_1.0.15+dfsg-1_amd64.deb ...
Unpacking libsctp1:amd64 (1.0.15+dfsg-1) ...
Preparing to unpack .../openjdk-7-jre_7u85-2.6.1-5ubuntu0.14.04.1_amd64.deb ...
Unpacking openjdk-7-jre:amd64 (7u85-2.6.1-5ubuntu0.14.04.1) over (7u79-2.5.6-0ubuntu1.14.04.1) ...
Preparing to unpack .../openjdk-7-jre-headless_7u85-2.6.1-5ubuntu0.14.04.1_amd64.deb ...
Unpacking openjdk-7-jre-headless:amd64 (7u85-2.6.1-5ubuntu0.14.04.1) over (7u79-2.5.6-0ubuntu1.14.04.1) ...
Preparing to unpack .../python3-problem-report_2.14.1-0ubuntu3.18_all.deb ...
Unpacking python3-problem-report (2.14.1-0ubuntu3.18) over (2.14.1-0ubuntu3.17) ...
Preparing to unpack .../python3-apport_2.14.1-0ubuntu3.18_all.deb ...
Unpacking python3-apport (2.14.1-0ubuntu3.18) over (2.14.1-0ubuntu3.17) ...
Preparing to unpack .../apport_2.14.1-0ubuntu3.18_all.deb ...
apport stop/waiting
Unpacking apport (2.14.1-0ubuntu3.18) over (2.14.1-0ubuntu3.17) ...
Preparing to unpack .../apport-gtk_2.14.1-0ubuntu3.18_all.deb ...
Unpacking apport-gtk (2.14.1-0ubuntu3.18) over (2.14.1-0ubuntu3.17) ...
Selecting previously unselected package lksctp-tools.
Preparing to unpack .../lksctp-tools_1.0.15+dfsg-1_amd64.deb ...
Unpacking lksctp-tools (1.0.15+dfsg-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up ntpdate (1:4.2.6.p5+dfsg-3ubuntu2.14.04.5) ...
Setting up libaudiofile1:amd64 (0.3.6-2ubuntu0.14.04.1) ...
Setting up mysql-common (5.5.46-0ubuntu0.14.04.2) ...
Setting up libmysqlclient18:amd64 (5.5.46-0ubuntu0.14.04.2) ...
Setting up libsctp1:amd64 (1.0.15+dfsg-1) ...
Setting up openjdk-7-jre-headless:amd64 (7u85-2.6.1-5ubuntu0.14.04.1) ...
Installing new version of config file /etc/java-7-openjdk/security/java.policy ...
Installing new version of config file /etc/java-7-openjdk/security/java.security ...
Setting up openjdk-7-jre:amd64 (7u85-2.6.1-5ubuntu0.14.04.1) ...
Setting up python3-problem-report (2.14.1-0ubuntu3.18) ...
Setting up python3-apport (2.14.1-0ubuntu3.18) ...
Setting up apport (2.14.1-0ubuntu3.18) ...
apport start/running
Setting up apport-gtk (2.14.1-0ubuntu3.18) ...
Setting up lksctp-tools (1.0.15+dfsg-1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...


```

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.


```

Looks like a victory, even if 5 not upgraded. 

```
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
(Reading database ... 373925 files and directories currently installed.)
Removing bve-train-br-class-323-3dcab (20100711-0ubuntu2) ...
Purging configuration files for bve-train-br-class-323-3dcab (20100711-0ubuntu2) ...
No diversion 'diversion of /usr/share/games/bve/Train/BR_Class_323/train.dat by bve-train-br-class-323-3dcab', none removed.
Removing dkms (2.2.0.3-1.1ubuntu5.14.04.5) ...
Purging configuration files for dkms (2.2.0.3-1.1ubuntu5.14.04.5) ...
Removing flashplugin-installer (11.2.202.508ubuntu0.14.04.1) ...
Purging configuration files for flashplugin-installer (11.2.202.508ubuntu0.14.04.1) ...
Removing indicator-application (12.10.1+14.04.20140407-0ubuntu1) ...
Purging configuration files for indicator-application (12.10.1+14.04.20140407-0ubuntu1) ...
Removing jamin (0.97.14~cvs~81203-4) ...
Purging configuration files for jamin (0.97.14~cvs~81203-4) ...
Removing lib32gcc1 (1:4.9.1-0ubuntu1) ...
Purging configuration files for lib32gcc1 (1:4.9.1-0ubuntu1) ...
Removing libatk-bridge2.0-0:i386 (2.10.2-2ubuntu1) ...
Purging configuration files for libatk-bridge2.0-0:i386 (2.10.2-2ubuntu1) ...
Removing libatspi2.0-0:i386 (2.10.2.is.2.10.1-0ubuntu1) ...
Purging configuration files for libatspi2.0-0:i386 (2.10.2.is.2.10.1-0ubuntu1) ...
Removing libaudclient2:amd64 (3.4.3-1) ...
Purging configuration files for libaudclient2:amd64 (3.4.3-1) ...
Removing libaudcore1:amd64 (3.4.3-1) ...
Purging configuration files for libaudcore1:amd64 (3.4.3-1) ...
Removing libboost-filesystem1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-filesystem1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-locale1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-locale1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-regex1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-regex1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libc6-i386 (2.19-0ubuntu6.6) ...
Purging configuration files for libc6-i386 (2.19-0ubuntu6.6) ...
Removing libcairo-gobject2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Purging configuration files for libcairo-gobject2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Removing libcairo-script-interpreter2:amd64 (1.13.0~20140204-0ubuntu1.1) ...
Purging configuration files for libcairo-script-interpreter2:amd64 (1.13.0~20140204-0ubuntu1.1) ...
Removing libcapi20-3:amd64 (1:3.25+dfsg1-3.3ubuntu2) ...
Purging configuration files for libcapi20-3:amd64 (1:3.25+dfsg1-3.3ubuntu2) ...
Removing libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2) ...
Purging configuration files for libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2) ...
Removing libcmis-0.4-4 (0.4.1-3ubuntu4) ...
Purging configuration files for libcmis-0.4-4 (0.4.1-3ubuntu4) ...
Removing libcolord1:i386 (1.0.6-1) ...
Purging configuration files for libcolord1:i386 (1.0.6-1) ...
Removing libcsound64-6.0 (1:6.02~dfsg-1) ...
Purging configuration files for libcsound64-6.0 (1:6.02~dfsg-1) ...
Removing libcuda1-304 (304.128-0ubuntu0.0.1) ...
Purging configuration files for libcuda1-304 (304.128-0ubuntu0.0.1) ...
Removing libdbusmenu-gtk3-4:i386 (12.10.3+14.04.20140612-0ubuntu1) ...
Purging configuration files for libdbusmenu-gtk3-4:i386 (12.10.3+14.04.20140612-0ubuntu1) ...
Removing libdrm-intel1:i386 (2.4.60-2~ubuntu14.04.1) ...
Purging configuration files for libdrm-intel1:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libdrm-nouveau2:i386 (2.4.60-2~ubuntu14.04.1) ...
Purging configuration files for libdrm-nouveau2:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libdrm-radeon1:i386 (2.4.60-2~ubuntu14.04.1) ...
Purging configuration files for libdrm-radeon1:i386 (2.4.60-2~ubuntu14.04.1) ...
Removing libedit2:i386 (3.1-20130712-2) ...
Purging configuration files for libedit2:i386 (3.1-20130712-2) ...
Removing libelf1:i386 (0.158-0ubuntu5.2) ...
Purging configuration files for libelf1:i386 (0.158-0ubuntu5.2) ...
Removing libexif12:i386 (0.6.21-1ubuntu1) ...
Purging configuration files for libexif12:i386 (0.6.21-1ubuntu1) ...
Removing libgd3:i386 (2.1.0-3) ...
Purging configuration files for libgd3:i386 (2.1.0-3) ...
Removing libgif4:i386 (4.1.6-11) ...
Purging configuration files for libgif4:i386 (4.1.6-11) ...
Removing libgl1-mesa-dri-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Purging configuration files for libgl1-mesa-dri-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Removing libgl1-mesa-glx-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Purging configuration files for libgl1-mesa-glx-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Removing libglapi-mesa-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Purging configuration files for libglapi-mesa-lts-vivid:i386 (10.5.9-2ubuntu1~trusty3) ...
Removing libglu1-mesa:i386 (9.0.0-2) ...
Purging configuration files for libglu1-mesa:i386 (9.0.0-2) ...
Removing libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) ...
Purging configuration files for libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Purging configuration files for libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgsoap4:amd64 (2.8.16-2) ...
Purging configuration files for libgsoap4:amd64 (2.8.16-2) ...
Removing libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2) ...
Purging configuration files for libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2) ...
Removing libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3) ...
Purging configuration files for libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3) ...
Removing libgtk-3-0:i386 (3.10.8-0ubuntu1.6) ...
Purging configuration files for libgtk-3-0:i386 (3.10.8-0ubuntu1.6) ...
Removing libgvpr2 (2.36.0-0ubuntu3.1) ...
Purging configuration files for libgvpr2 (2.36.0-0ubuntu3.1) ...
Removing libharfbuzz-gobject0:amd64 (0.9.27-1ubuntu1) ...
Purging configuration files for libharfbuzz-gobject0:amd64 (0.9.27-1ubuntu1) ...
Removing libhdb9-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libhdb9-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libice6:i386 (2:1.0.8-2) ...
Purging configuration files for libice6:i386 (2:1.0.8-2) ...
Removing libieee1284-3:i386 (0.2.11-12) ...
Purging configuration files for libieee1284-3:i386 (0.2.11-12) ...
Removing libimlib2 (1.4.6-2) ...
Purging configuration files for libimlib2 (1.4.6-2) ...
Removing libkdc2-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libkdc2-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing liblcms2-2:i386 (2.6-3ubuntu1~trusty1) ...
Purging configuration files for liblcms2-2:i386 (2.6-3ubuntu1~trusty1) ...
Removing libllvm3.6:i386 (1:3.6-2ubuntu1~trusty1) ...
Purging configuration files for libllvm3.6:i386 (1:3.6-2ubuntu1~trusty1) ...
Removing libltc11:amd64 (1.1.3-1) ...
Purging configuration files for libltc11:amd64 (1.1.3-1) ...
Removing libltdl7:i386 (2.4.2-1.7ubuntu1) ...
Purging configuration files for libltdl7:i386 (2.4.2-1.7ubuntu1) ...
Removing liblua5.1-0:amd64 (5.1.5-5ubuntu0.1) ...
Purging configuration files for liblua5.1-0:amd64 (5.1.5-5ubuntu0.1) ...
Removing libmowgli2:amd64 (1.0.0-1ubuntu1) ...
Purging configuration files for libmowgli2:amd64 (1.0.0-1ubuntu1) ...
Removing libmpg123-0:i386 (1.16.0-1ubuntu1) ...
Purging configuration files for libmpg123-0:i386 (1.16.0-1ubuntu1) ...
Removing libopenal1:i386 (1:1.14-4ubuntu1) ...
Purging configuration files for libopenal1:i386 (1:1.14-4ubuntu1) ...
Removing libopenimageio1.3 (1.3.12~dfsg0-1ubuntu1) ...
Purging configuration files for libopenimageio1.3 (1.3.12~dfsg0-1ubuntu1) ...
Removing liborc-0.4-0:i386 (1:0.4.18-1ubuntu1) ...
Purging configuration files for liborc-0.4-0:i386 (1:0.4.18-1ubuntu1) ...
Removing libp11-kit-gnome-keyring:i386 (3.10.1-1ubuntu4.2) ...
Purging configuration files for libp11-kit-gnome-keyring:i386 (3.10.1-1ubuntu4.2) ...
Removing libpciaccess0:i386 (0.13.2-1) ...
Purging configuration files for libpciaccess0:i386 (0.13.2-1) ...
Removing libpcrecpp0:amd64 (1:8.31-2ubuntu2.1) ...
Purging configuration files for libpcrecpp0:amd64 (1:8.31-2ubuntu2.1) ...
Removing libquvi7:amd64 (0.4.1-1ubuntu3) ...
Purging configuration files for libquvi7:amd64 (0.4.1-1ubuntu3) ...
Removing libsane:i386 (1.0.23-3ubuntu3.1) ...
Purging configuration files for libsane:i386 (1.0.23-3ubuntu3.1) ...
Removing directory /etc/sane.d/ ...
Removing libsdl-gfx1.2-4:amd64 (2.0.23-3) ...
Purging configuration files for libsdl-gfx1.2-4:amd64 (2.0.23-3) ...
Removing libsdl-net1.2:amd64 (1.2.8-4) ...
Purging configuration files for libsdl-net1.2:amd64 (1.2.8-4) ...
Removing libsigc++-1.2-5c2 (1.2.7-2ubuntu1) ...
Purging configuration files for libsigc++-1.2-5c2 (1.2.7-2ubuntu1) ...
Removing libsm6:i386 (2:1.2.1-2) ...
Purging configuration files for libsm6:i386 (2:1.2.1-2) ...
Removing libsmf0 (1.3-2ubuntu1) ...
Purging configuration files for libsmf0 (1.3-2ubuntu1) ...
Removing libsmpeg0:amd64 (0.4.5+cvs20030824-5ubuntu4) ...
Purging configuration files for libsmpeg0:amd64 (0.4.5+cvs20030824-5ubuntu4) ...
Removing libsynfig0 (0.64.1-2) ...
Purging configuration files for libsynfig0 (0.64.1-2) ...
Removing libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1) ...
Purging configuration files for libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1) ...
Removing libusb-1.0-0:i386 (2:1.0.17-1ubuntu2) ...
Purging configuration files for libusb-1.0-0:i386 (2:1.0.17-1ubuntu2) ...
Removing libv4l-0:i386 (1.0.1-1) ...
Purging configuration files for libv4l-0:i386 (1.0.1-1) ...
Removing libv4lconvert0:i386 (1.0.1-1) ...
Purging configuration files for libv4lconvert0:i386 (1.0.1-1) ...
Removing libvncserver0:amd64 (0.9.9+dfsg-1ubuntu1.1) ...
Purging configuration files for libvncserver0:amd64 (0.9.9+dfsg-1ubuntu1.1) ...
Removing libvpx1:i386 (1.3.0-2) ...
Purging configuration files for libvpx1:i386 (1.3.0-2) ...
Removing libwayland-client0:i386 (1.4.0-1ubuntu1) ...
Purging configuration files for libwayland-client0:i386 (1.4.0-1ubuntu1) ...
Removing libwayland-cursor0:i386 (1.4.0-1ubuntu1) ...
Purging configuration files for libwayland-cursor0:i386 (1.4.0-1ubuntu1) ...
Removing libx11-xcb1:i386 (2:1.6.2-1ubuntu2) ...
Purging configuration files for libx11-xcb1:i386 (2:1.6.2-1ubuntu2) ...
Removing libxcb-dri2-0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-dri2-0:i386 (1.10-2ubuntu1) ...
Removing libxcb-dri3-0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-dri3-0:i386 (1.10-2ubuntu1) ...
Removing libxcb-glx0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-glx0:i386 (1.10-2ubuntu1) ...
Removing libxcb-present0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-present0:i386 (1.10-2ubuntu1) ...
Removing libxcb-sync1:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-sync1:i386 (1.10-2ubuntu1) ...
Removing libxdot4 (2.36.0-0ubuntu3.1) ...
Purging configuration files for libxdot4 (2.36.0-0ubuntu3.1) ...
Removing libxkbcommon0:i386 (0.4.1-0ubuntu1) ...
Purging configuration files for libxkbcommon0:i386 (0.4.1-0ubuntu1) ...
Removing libxml2:i386 (2.9.1+dfsg1-3ubuntu4.4) ...
Purging configuration files for libxml2:i386 (2.9.1+dfsg1-3ubuntu4.4) ...
Removing libxpm4:i386 (1:3.5.10-1) ...
Purging configuration files for libxpm4:i386 (1:3.5.10-1) ...
Removing libxshmfence1:i386 (1.1-2) ...
Purging configuration files for libxshmfence1:i386 (1.1-2) ...
Removing libxslt1.1:i386 (1.1.28-2build1) ...
Purging configuration files for libxslt1.1:i386 (1.1.28-2build1) ...
Removing libxt6:i386 (1:1.1.4-1) ...
Purging configuration files for libxt6:i386 (1:1.1.4-1) ...
Removing libxxf86vm1:i386 (1:1.1.3-1) ...
Purging configuration files for libxxf86vm1:i386 (1:1.1.3-1) ...
Removing muse (2.1.2-1) ...
Purging configuration files for muse (2.1.2-1) ...
Removing nvidia-libopencl1-304 (304.125-0ubuntu0.0.2) ...
Purging configuration files for nvidia-libopencl1-304 (304.125-0ubuntu0.0.2) ...
Removing nvidia-settings (331.20-0ubuntu8) ...
Purging configuration files for nvidia-settings (331.20-0ubuntu8) ...
Removing ocl-icd-libopencl1:i386 (2.1.3-4) ...
Purging configuration files for ocl-icd-libopencl1:i386 (2.1.3-4) ...
Removing openbve (1.4.0.9-1) ...
Purging configuration files for openbve (1.4.0.9-1) ...
Removing openoffice.org-hyphenation (0.7.1) ...
Purging configuration files for openoffice.org-hyphenation (0.7.1) ...
Removing petri-foo (0.1.87-2) ...
Purging configuration files for petri-foo (0.1.87-2) ...
Removing samba (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Purging configuration files for samba (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Removing samba-dsdb-modules (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Purging configuration files for samba-dsdb-modules (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Removing screen-resolution-extra (0.17.1) ...
Purging configuration files for screen-resolution-extra (0.17.1) ...
Removing sooperlooper (1.7.0~dfsg0-2) ...
Purging configuration files for sooperlooper (1.7.0~dfsg0-2) ...
Removing virtualbox (4.3.10-dfsg-1ubuntu5) ...
Purging configuration files for virtualbox (4.3.10-dfsg-1ubuntu5) ...
Removing virtualbox-qt (4.3.10-dfsg-1ubuntu5) ...
Purging configuration files for virtualbox-qt (4.3.10-dfsg-1ubuntu5) ...
Removing winbind (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Purging configuration files for winbind (2:4.1.6+dfsg-1ubuntu2.14.04.10) ...
Removing wine1.6 (1:1.6.2-0ubuntu4) ...
Purging configuration files for wine1.6 (1:1.6.2-0ubuntu4) ...
Removing wine1.6-amd64 (1:1.6.2-0ubuntu4) ...
Purging configuration files for wine1.6-amd64 (1:1.6.2-0ubuntu4) ...
Removing wine1.6-i386 (1:1.6.2-0ubuntu4) ...
Purging configuration files for wine1.6-i386 (1:1.6.2-0ubuntu4) ...
Removing xjadeo (0.7.6-1build1) ...
Purging configuration files for xjadeo (0.7.6-1build1) ...
Processing triggers for menu (2.1.46ubuntu1) ...


```

All I can say here is wow. I heard how powerful the command prompt is, but that is pretty amazing! Why are people on Windoze?

Rebooting... hopefully.

Bashing-Om, all in one piece!

I actually got to see the bootup screen also.

Very impressive. What's next? I'm feeling hungry to learn more about command prompts. Oh boy...

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Uh Huh ...

linux is pretty impressive !
I left Windows behind - never did like it - years back, and have never looked back .

OK .. I am surprised those 5 did not get upgraded .. overall I am happy with our results. That system is squeaky clean .
let's see what we can find out .
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
No, "distribution upgrade" will not release upgrade, just upgrade installed packages using apt's smart mode to install anything 'new' and resolve stubborn dependency issues.

[INDENT][INDENT]how now brown cow ?
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Bashing-Om,

Yeah, saw that and wondered what it was about. But looks good, none the less.

```
sudo apt-get update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Ign https://private-ppa.launchpad.net precise InRelease                        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Ign http://dl.google.com stable/main Translation-en_US                         
Hit https://private-ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://dl.google.com stable/main Translation-en                            
Get:2 http://security.ubuntu.com trusty-security/main Sources [98.0 kB]        
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:3 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B]  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:4 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B]  
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:5 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:6 http://security.ubuntu.com trusty-security/main amd64 Packages [357 kB]  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:7 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Get:8 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Hit http://us.archive.ubuntu.com trusty Release.gpg                   
Get:9 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Get:10 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [326 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:11 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:12 http://security.ubuntu.com trusty-security/main i386 Packages [338 kB]  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:13 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [638 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:14 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Hit http://ppa.launchpad.net trusty Release                                    
Get:15 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:16 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:17 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:18 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:19 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [327 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Get:20 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [618 kB] 
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:21 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:22 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:23 http://us.archive.ubuntu.com trusty-updates/main Translation-en [309 kB]
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:25 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,569 B]
Get:26 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [172 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 3,680 kB in 13s (277 kB/s)                                             
Reading package lists... Done


```

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libav-tools libavcodec-extra-54 libavdevice53 libavfilter3 libavformat54
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libav-tools libavdevice53 libavfilter3 libavformat54
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


```

Well, now at least, it's only 4.

[HTML]how now brown cow ?[/HTML]

No comprede. I lived elsewhere as a teenager, so a few things go over my head...

---

### Post by Bashing-om on 2015-10-28
33Nicolas; Umph ...

Will have to dig deeper and see why those packages are "held back" . Might be a good thing .
Can we save that for the morrow  ? ... eyes are crossing and I have developed a bit of a headache that interferes with the think'n.

As to "how now brown cow" the thing was .. bull hung up on a barbed wire fence looking over at the herd of heifers .

Also not to be forgotten ... graphics driver. Are you satisfied with your current performance ?

all on all ....
[INDENT][INDENT][INDENT]look'n good
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-28
Bashing-Om, you must live near us. Wife and I are suffering from a headache today, as many others.

Looks like I picked the wrong day to quit caffeine and tea!

See you tomorrow.

---

### Post by Bashing-om on 2015-10-29
33Nicolas; I'm Back ....

On to this next ... why are these :
> 
The following packages have been kept back:
  libav-tools libavdevice53 libavfilter3 libavformat54
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

packages held ... ?? hummmm  multimedia stuff ..

Let's look at what the repo has :
```

apt-cache show libav-tools libavdevice53 libavfilter3 libavformat54

```

And what have we installed, and what does the system want to install :
```

apt-cache policy libav-tools libavdevice53 libavfilter3 libavformat54

```


Then we look at the dependencies .. figure out what is not going on here that should be.

When this little issue is settled, it is back to: 
> 
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)

and figure out what is going on with the desktop. This will still be a process in learning as I do not know the ubuntustudio system.

The good thing here ->
[INDENT][INDENT][INDENT]we do this and no jail time involved
[/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-29
Bashing-Om, morning.

Yes, the multimedia stuff is my fault. I was testing a lot of devices and was looking for Apple-like software for my music. Can't say I was very successful either.

```
apt-cache show libav-tools libavdevice53 libavfilter3 libavformat54
Package: libav-tools
Source: ffmpeg
Priority: extra
Section: oldlibs
Installed-Size: 103
Maintainer: Jon Severinsson <jon@severinsson.net>
Architecture: all
Version: 7:1.2.5-1~trusty1
Depends: ffmpeg (>= 7:0.10~)
Filename: pool/main/f/ffmpeg/libav-tools_1.2.5-1~trusty1_all.deb
Size: 55772
MD5sum: e12291bc95cb88bfb665d20ab6b30b88
SHA1: ecf1a209855a2643790cd653d7fe51fbdec1a20f
SHA256: 777fb9c007571ac781ceee6ce8b00de8e8f3ed3855c25e62e8b71fe2b7d8c213
Description-en: Multimedia player, server, encoder and transcoder (transitional package)
 FFmpeg is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This package is only used for transitional purposes and can be safely
 removed when no other packages depend on this package.
Description-md5: f66fe767e075577a96654581cca13443
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>

Package: libav-tools
Priority: optional
Section: universe/video
Installed-Size: 9176
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libav
Version: 6:9.18-0ubuntu0.14.04.1
Replaces: libavcodec-extra-53 (<< 4:0.6~)
Depends: libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18), libavdevice53 (>= 6:9.1-1), libavfilter3 (>= 6:9.1-1), libavformat54 (>= 6:9.1-1), libavresample1 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libbz2-1.0, libc6 (>= 2.14), libgnutls26 (>= 2.12.17-0), libgsm1 (>= 1.0.13), libmp3lame0, libopenjpeg2, libopus0 (>= 1.0.3), librtmp0 (>= 2.3), libschroedinger-1.0-0 (>= 1.0.7), libsdl1.2debian (>= 1.2.11), libspeex1 (>= 1.2~beta3-1), libswscale2 (>= 6:9.1-1), libtheora0 (>= 1.0), libva1 (>> 1.3.0~), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libvpx1 (>= 1.0.0), libx264-142, libxvidcore4 (>= 1.2.2), zlib1g (>= 1:1.2.0)
Pre-Depends: dpkg (>= 1.15.7.2~)
Suggests: frei0r-plugins (>= 1.3)
Conflicts: ffprobe
Filename: pool/universe/liba/libav/libav-tools_9.18-0ubuntu0.14.04.1_amd64.deb
Size: 3304210
MD5sum: 2ac55f7380b6da8601c05800710d9d71
SHA1: a1da12f80ac6bbb3563008648ff98790399a3891
SHA256: bf39b6f6b315723046a01508b771e0364c9e62e06203e603f061aa3c7f7e4ab5
Description-en: Multimedia player, server, encoder and transcoder
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This package contains the avplay multimedia player, the avserver
 streaming server, the avconv audio and video encoder, and the avprobe
 stream analyzer.  They support most existing file formats (AVI, MPEG,
 OGG, Matroska, ASF...) and encoding formats (MPEG, DivX, MPEG4, AC3,
 DV...). Additionally, it contains the qt-faststart utility which
 rearranges Quicktime files to facilitate network streaming.
 .
 This package also serves as a replacement for the former 'ffmpeg'
 package.
Description-md5: f018bb360296d7ddca9599e21148ae21
Homepage: http://libav.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntustudio-video

Package: libav-tools
Priority: optional
Section: universe/video
Installed-Size: 9170
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libav
Version: 6:9.11-2ubuntu2
Replaces: libavcodec-extra-53 (<< 4:0.6~)
Depends: libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.11), libavdevice53 (>= 6:9.1-1), libavfilter3 (>= 6:9.1-1), libavformat54 (>= 6:9.1-1), libavresample1 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libbz2-1.0, libc6 (>= 2.14), libgnutls26 (>= 2.12.17-0), libgsm1 (>= 1.0.13), libmp3lame0, libopenjpeg2, libopus0 (>= 1.0.3), librtmp0 (>= 2.3), libschroedinger-1.0-0 (>= 1.0.7), libsdl1.2debian (>= 1.2.11), libspeex1 (>= 1.2~beta3-1), libswscale2 (>= 6:9.1-1), libtheora0 (>= 1.0), libva1 (>> 1.2.0~), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libvpx1 (>= 1.0.0), libx264-142, libxvidcore4 (>= 1.2.2), zlib1g (>= 1:1.2.0)
Pre-Depends: dpkg (>= 1.15.7.2~)
Suggests: frei0r-plugins (>= 1.3)
Conflicts: ffprobe
Filename: pool/universe/liba/libav/libav-tools_9.11-2ubuntu2_amd64.deb
Size: 3307596
MD5sum: b8c2820190815b5e27665c0748e80775
SHA1: 5a2492d8f3d8b61c9c4578b070241bff311786c7
SHA256: 86621597dfca1d866591dac171adf9b7f19d92102fc993c73f29fdda296224df
Description-en: Multimedia player, server, encoder and transcoder
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This package contains the avplay multimedia player, the avserver
 streaming server, the avconv audio and video encoder, and the avprobe
 stream analyzer.  They support most existing file formats (AVI, MPEG,
 OGG, Matroska, ASF...) and encoding formats (MPEG, DivX, MPEG4, AC3,
 DV...). Additionally, it contains the qt-faststart utility which
 rearranges Quicktime files to facilitate network streaming.
 .
 This package also serves as a replacement for the former 'ffmpeg'
 package.
Description-md5: f018bb360296d7ddca9599e21148ae21
Homepage: http://libav.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntustudio-video

Package: libavdevice53
Source: ffmpeg
Priority: optional
Section: libs
Installed-Size: 193
Maintainer: Jon Severinsson <jon@severinsson.net>
Architecture: amd64
Version: 7:1.2.5-1~trusty1
Replaces: libavdevice-extra-53
Depends: libasound2 (>= 1.0.16), libavcodec54 (>= 7:1.2.5~) | libavcodec-extra-54 (>= 7:1.2.5~), libavfilter3 (>= 7:1.2.5~), libavformat54 (>= 7:1.2.5~), libavutil52 (>= 7:1.2.5~), libc6 (>= 2.17), libcdio-cdda1 (>= 0.83), libcdio-paranoia1 (>= 0.83), libdc1394-22, libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116, libpulse0 (>= 1:0.99.1), libsdl1.2debian (>= 1.2.11), libx11-6 (>= 2:1.4.99.1), libxext6, libxfixes3
Pre-Depends: dpkg (>= 1.15.6~), multiarch-support
Breaks: bino (<= 1.4.2-1), blender (<= 2.63a-1), ffmpeg2theora (<= 0.29-2), libavdevice-extra-53 (<< 7:0.10~), libmlt5 (<= 0.8.8-2), libopenscenegraph80 (<= 3.0.1-4.1), zoneminder (<= 1.25.0-4)
Filename: pool/main/f/ffmpeg/libavdevice53_1.2.5-1~trusty1_amd64.deb
Size: 85430
MD5sum: 8a7803bf026516762d6e396280154f41
SHA1: cac9a9cfc966973e5c7b14043d045e08ee0af599
SHA256: 8389661c555beb72a94eafacc8c3512001b6dc1e5fd1bebfcddc2c5eaf9819ba
Description-en: FFmpeg device handling library
 FFmpeg is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the device handling library from FFmpeg.
Description-md5: 2354a8a261ed87f867cafac04d2360aa
Multi-Arch: same
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>

Package: libavdevice53
Priority: optional
Section: universe/libs
Installed-Size: 185
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libav
Version: 6:9.18-0ubuntu0.14.04.1
Replaces: libavdevice-extra-53
Depends: libasound2 (>= 1.0.16), libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18), libavformat54 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libc6 (>= 2.14), libcdio-cdda1 (>= 0.83), libcdio-paranoia1 (>= 0.83), libdc1394-22, libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116, libpulse0 (>= 1:0.99.1), libx11-6 (>= 2:1.4.99.1), libxext6, libxfixes3
Pre-Depends: multiarch-support
Breaks: libavdevice-extra-53 (<< 5:0.8.1-2)
Filename: pool/universe/liba/libav/libavdevice53_9.18-0ubuntu0.14.04.1_amd64.deb
Size: 32304
MD5sum: 541d8c265f121662367d4b92dd9b129f
SHA1: 6218b4a39994d8145c4330c71c357d7d5df67b7d
SHA256: b13f8649dc76a17313b1c05a990539e4e1d9df031c46695c098d4609fe22081e
Description-en: Libav device handling library
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the device handling library from Libav.
Description-md5: 749c8f83866b20c4cc64ea76a0e145de
Multi-Arch: same
Homepage: http://libav.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntustudio-video, ubuntustudio-audio

Package: libavdevice53
Priority: optional
Section: universe/libs
Installed-Size: 181
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libav
Version: 6:9.11-2ubuntu2
Replaces: libavdevice-extra-53
Depends: libasound2 (>= 1.0.16), libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.11), libavformat54 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libc6 (>= 2.14), libcdio-cdda1 (>= 0.83), libcdio-paranoia1 (>= 0.83), libdc1394-22, libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116, libpulse0 (>= 1:0.99.1), libx11-6 (>= 2:1.4.99.1), libxext6, libxfixes3
Pre-Depends: multiarch-support
Breaks: libavdevice-extra-53 (<< 5:0.8.1-2)
Filename: pool/universe/liba/libav/libavdevice53_9.11-2ubuntu2_amd64.deb
Size: 32156
MD5sum: 3beb01f7581710a81ee443853442b443
SHA1: 053a5a1f61b110b9347f06227f5a6c2693ee7b73
SHA256: 64ca52a50d0f6444b8ef10fc284b2f5652cdea26d6dee7fb366b647b96209284
Description-en: Libav device handling library
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the device handling library from Libav.
Description-md5: 749c8f83866b20c4cc64ea76a0e145de
Multi-Arch: same
Homepage: http://libav.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntustudio-video, ubuntustudio-audio

Package: libavfilter3
Source: ffmpeg
Priority: optional
Section: libs
Installed-Size: 929
Maintainer: Jon Severinsson <jon@severinsson.net>
Architecture: amd64
Version: 7:1.2.5-1~trusty1
Replaces: libavfilter-extra-3
Suggests: frei0r-plugins
Depends: libavcodec54 (>= 7:1.2.5~) | libavcodec-extra-54 (>= 7:1.2.5~), libavformat54 (>= 7:1.2.5~), libavresample1 (>= 7:1.2.5~), libavutil52 (>= 7:1.2.5~), libc6 (>= 2.14), libfreetype6 (>= 2.2.1), libopencv-core2.4, libopencv-imgproc2.4, libpostproc52 (>= 7:1.2.5~), libswresample0 (>= 7:1.2.5~), libswscale2 (>= 7:1.2.5~)
Pre-Depends: dpkg (>= 1.15.6~), multiarch-support
Breaks: libavfilter-extra-3 (<< 7:0.10~)
Filename: pool/main/f/ffmpeg/libavfilter3_1.2.5-1~trusty1_amd64.deb
Size: 328656
MD5sum: 7a28a03011ddf57a5a34aef70694c6eb
SHA1: 23d0266bd74591690999e648197d665accc0d0de
SHA256: 67f4a1354f2e096696131da93ed9d5c13b91e2bd8047b3030a7d780cf90b4b8e
Description-en: FFmpeg video filtering library
 FFmpeg is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the video filtering library from FFmpeg.
Description-md5: 73d44731d08ccf8a08b71565d5dd280b
Multi-Arch: same
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>

Package: libavfilter3
Priority: optional
Section: universe/libs
Installed-Size: 367
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libav
Version: 6:9.18-0ubuntu0.14.04.1
Replaces: libavfilter-extra-3
Depends: libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18), libavformat54 (>= 6:9.1-1), libavresample1 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libc6 (>= 2.14), libfreetype6 (>= 2.2.1), libswscale2 (>= 6:9.1-1)
Pre-Depends: multiarch-support
Suggests: frei0r-plugins (>= 1.3)
Breaks: libavfilter-extra-3 (<< 5:0.8.1-2)
Filename: pool/universe/liba/libav/libavfilter3_9.18-0ubuntu0.14.04.1_amd64.deb
Size: 93540
MD5sum: bd927d2bbb4fac21ef1cb513ef0640c2
SHA1: 201555144dec17055591ac26317011e6db56b487
SHA256: 683ce78de61909f64144cc55274ba31e4fe447bae6e3a15b82a8f8458cf4b25e
Description-en: Libav video filtering library
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the video filtering library from Libav.
Description-md5: b3ffe3ea2238f3fde78a2d51145467fc
Multi-Arch: same
Homepage: http://libav.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntustudio-video, ubuntustudio-audio

Package: libavfilter3
Priority: optional
Section: universe/libs
Installed-Size: 363
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libav
Version: 6:9.11-2ubuntu2
Replaces: libavfilter-extra-3
Depends: libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.11), libavformat54 (>= 6:9.1-1), libavresample1 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libc6 (>= 2.14), libfreetype6 (>= 2.2.1), libswscale2 (>= 6:9.1-1)
Pre-Depends: multiarch-support
Suggests: frei0r-plugins (>= 1.3)
Breaks: libavfilter-extra-3 (<< 5:0.8.1-2)
Filename: pool/universe/liba/libav/libavfilter3_9.11-2ubuntu2_amd64.deb
Size: 93652
MD5sum: 016039fb363ada55f5204b2af6c12f3f
SHA1: e5f1d13b8aeca925c26220d479849cf0e5dc7cbf
SHA256: f315a405d62cb29f0777a609dd58123c9c74221474adab56d8804a476fde224b
Description-en: Libav video filtering library
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the video filtering library from Libav.
Description-md5: b3ffe3ea2238f3fde78a2d51145467fc
Multi-Arch: same
Homepage: http://libav.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntustudio-video, ubuntustudio-audio

Package: libavformat54
Source: ffmpeg
Priority: optional
Section: libs
Installed-Size: 1531
Maintainer: Jon Severinsson <jon@severinsson.net>
Architecture: amd64
Version: 7:1.2.5-1~trusty1
Replaces: libavformat-extra-54
Depends: libavcodec54 (>= 7:1.2.5~) | libavcodec-extra-54 (>= 7:1.2.5~), libavutil52 (>= 7:1.2.5~), libbz2-1.0, libc6 (>= 2.14), libgnutls26 (>= 2.12.17-0), librtmp0 (>= 2.3), zlib1g (>= 1:1.1.4)
Pre-Depends: dpkg (>= 1.15.6~), multiarch-support
Breaks: libavformat-extra-54 (<< 7:0.10~)
Filename: pool/main/f/ffmpeg/libavformat54_1.2.5-1~trusty1_amd64.deb
Size: 630986
MD5sum: 14fe53cff1150c7a257a43244b788be7
SHA1: 07f6310241c5e96168d1d224d5cd7e23856c8407
SHA256: 549986c14af821bcc0f6ef88cf3e1104fc82c3573e72273164b8e4665bf4bd5f
Description-en: FFmpeg file format library
 FFmpeg is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the library for handling file formats from FFmpeg.
 .
 It supports most existing file formats (AVI, MPEG, OGG, Matroska,
 ASF...).
Description-md5: 8d11eddab39569330765363ea0b872b4
Multi-Arch: same
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>

Package: libavformat54
Priority: optional
Section: universe/libs
Installed-Size: 1277
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libav
Version: 6:9.18-0ubuntu0.14.04.1
Replaces: libavformat-extra-54
Depends: libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18), libavutil52 (>= 6:9.1-1), libbz2-1.0, libc6 (>= 2.14), libgnutls26 (>= 2.12.17-0), librtmp0 (>= 2.3), zlib1g (>= 1:1.1.4)
Pre-Depends: multiarch-support
Breaks: libavformat-extra-54 (<< 5:0.8.1-2)
Filename: pool/universe/liba/libav/libavformat54_9.18-0ubuntu0.14.04.1_amd64.deb
Size: 480974
MD5sum: 4cacccb33a289abe4d822487aa70a78e
SHA1: 9f5e10c403be0fe98428dff140163671bd1a39b6
SHA256: a590299c51fe926e99b9c1de2ec96d3feaa81f776c70c3f9b898a6c5e02db913
Description-en: Libav file format library
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the library for handling file formats from Libav.
 .
 It supports most existing file formats (AVI, MPEG, OGG, Matroska,
 ASF...).
Description-md5: 464655e4bb8f0f07e6e1f702e07fb04c
Multi-Arch: same
Homepage: http://libav.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: kubuntu-desktop, kubuntu-full, kubuntu-active, kubuntu-active-desktop, kubuntu-active-full, kubuntu-active, xubuntu-desktop, mythbuntu-frontend, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-desktop, ubuntustudio-video, ubuntustudio-audio

Package: libavformat54
Priority: optional
Section: universe/libs
Installed-Size: 1269
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libav
Version: 6:9.11-2ubuntu2
Replaces: libavformat-extra-54
Depends: libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.11), libavutil52 (>= 6:9.1-1), libbz2-1.0, libc6 (>= 2.14), libgnutls26 (>= 2.12.17-0), librtmp0 (>= 2.3), zlib1g (>= 1:1.1.4)
Pre-Depends: multiarch-support
Breaks: libavformat-extra-54 (<< 5:0.8.1-2)
Filename: pool/universe/liba/libav/libavformat54_9.11-2ubuntu2_amd64.deb
Size: 479838
MD5sum: e6893490e8e2b80c888f7b9bb464ba2a
SHA1: 3fc7d7c5f8b8cf60899d81689b04afd6bd3ea454
SHA256: 20fe2b67c699cb172eaa3d89202890ff20851a3edaeda57cd2722f62c53eb3b7
Description-en: Libav file format library
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This is the library for handling file formats from Libav.
 .
 It supports most existing file formats (AVI, MPEG, OGG, Matroska,
 ASF...).
Description-md5: 464655e4bb8f0f07e6e1f702e07fb04c
Multi-Arch: same
Homepage: http://libav.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: kubuntu-desktop, kubuntu-full, kubuntu-active, kubuntu-active-desktop, kubuntu-active-full, kubuntu-active, xubuntu-desktop, mythbuntu-frontend, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-desktop, ubuntustudio-video, ubuntustudio-audio


```

```
apt-cache policy libav-tools libavdevice53 libavfilter3 libavformat54
libav-tools:
  Installed: 6:9.18-0ubuntu0.14.04.1
  Candidate: 7:1.2.5-1~trusty1
  Version table:
     7:1.2.5-1~trusty1 0
        500 http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu/ trusty/main amd64 Packages
 *** 6:9.18-0ubuntu0.14.04.1 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libavdevice53:
  Installed: 6:9.18-0ubuntu0.14.04.1
  Candidate: 7:1.2.5-1~trusty1
  Version table:
     7:1.2.5-1~trusty1 0
        500 http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu/ trusty/main amd64 Packages
 *** 6:9.18-0ubuntu0.14.04.1 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libavfilter3:
  Installed: 6:9.18-0ubuntu0.14.04.1
  Candidate: 7:1.2.5-1~trusty1
  Version table:
     7:1.2.5-1~trusty1 0
        500 http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu/ trusty/main amd64 Packages
 *** 6:9.18-0ubuntu0.14.04.1 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libavformat54:
  Installed: 6:9.18-0ubuntu0.14.04.1
  Candidate: 7:1.2.5-1~trusty1
  Version table:
     7:1.2.5-1~trusty1 0
        500 http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu/ trusty/main amd64 Packages
 *** 6:9.18-0ubuntu0.14.04.1 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
```

Very nifty that policy command.

I'm actually considering returning to Ubuntu. I figured all the Studio applications can be installed on a regular Ubuntu, unless there is a better musician distro out there?

---

### Post by Bashing-om on 2015-10-29
33Nicolas; Welp ... 

Chores caught up and back to this ...
As to the system you want to run.
> 
I'm actually considering returning to Ubuntu. I figured all the Studio applications can be installed on a regular Ubuntu, unless there is a better musician distro out there?

The kernel is the kernel is the kernel ... The only difference between any and all distros is how one relates to the kernel and what else is installed on the system.

If you know what you want, and some idea of how to get around with 'buntu ... then one installs minimal -core- package ... and on this core install ONLY what you want . The result is very light and very very fast ! And as a bonus, you really know your system. Hey, you built it to your specifications, you should know it !

All that said, ya want to keep on resurrecting this present install ? Or install anew ?

Presently we can point our finger at ppa.launchpad.net/noobslab/deepin-sc/ubuntu/ as what is most likely holding these versions down.
So - again, what are we working with ?
Show a new sources:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Where I expect we find that PPA disabled.

---------------------
To be honest ... I am prejudiced ... I do prefer
[INDENT][INDENT][INDENT]fast, light and configurable 
[INDENT][INDENT][INDENT]we do as you please
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-29
Hey Bashing-Om, 

I hear you about chores, still multitasking with mine!

```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu-Studio 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main multiverse restricted universe
     2    #SQUEEZE-CANADIAN-MIRROR
     3    
     4    #SQUEEZE-BACKPORTS
     5    
     6    #Wheezy/Testing
     7    
     8    #DEBIAN MULTIMEDIA
     9    
    10    #SCRIBUS
    11    
    12    #AV LINUX KERNEL REPO
    13    
    14    #WXWidgets
    15    # deb http://apt.wxwidgets.org/ squeeze-wx main
    16    # deb-src http://apt.wxwidgets.org/ squeeze-wx main
    17    
    18    
    19    
    20    
    21    
    22    
    23    
    24    
    25    
    26    
    27    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    28    # newer versions of the distribution.
    29    deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted multiverse
    30    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted multiverse
    31    
    32    ## Major bug fix updates produced after the final release of the
    33    ## distribution.
    34    
    35    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    36    ## team. Also, please note that software in universe WILL NOT receive any
    37    ## review or updates from the Ubuntu security team.
    38    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    39    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    40    
    41    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    42    ## team, and may not be under a free licence. Please satisfy yourself as to 
    43    ## your rights to use the software. Also, please note that software in 
    44    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    45    ## security team.
    46    
    47    ## N.B. software from this repository may not have been tested as
    48    ## extensively as that contained in the main release, although it includes
    49    ## newer versions of some applications which may provide useful features.
    50    ## Also, please note that software in backports WILL NOT receive any review
    51    ## or updates from the Ubuntu security team.
    52    
    53    deb http://security.ubuntu.com/ubuntu trusty-security main restricted multiverse
    54    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted multiverse
    55    deb http://security.ubuntu.com/ubuntu trusty-security universe
    56    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    57    
    58    ## Uncomment the following two lines to add software from Canonical's
    59    ## 'partner' repository.
    60    ## This software is not part of Ubuntu, but is offered by Canonical and the
    61    ## respective vendors as a service to Ubuntu users.
    62    deb http://archive.canonical.com/ubuntu trusty partner
    63    deb-src http://archive.canonical.com/ubuntu trusty partner
    64    
    65    ## Uncomment the following two lines to add software from Ubuntu's
    66    ## 'extras' repository.
    67    ## This software is not part of Ubuntu, but is offered by third-party
    68    ## developers who want to ship their latest software.
    69    deb http://extras.ubuntu.com/ubuntu trusty main
    70    deb-src http://extras.ubuntu.com/ubuntu trusty main
    71    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe main restricted multiverse


```

```
tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-4-trusty.list <==

==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-4-trusty.list.save <==

==> /etc/apt/sources.list.d/libreoffice-libreoffice-5-0-trusty.list <==
deb http://ppa.launchpad.net/libreoffice/libreoffice-5-0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-0/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-libreoffice-5-0-trusty.list.save <==
deb http://ppa.launchpad.net/libreoffice/libreoffice-5-0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-0/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.save <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

==> /etc/apt/sources.list.d/noobslab-deepin-sc-trusty.list <==
deb http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main

==> /etc/apt/sources.list.d/noobslab-deepin-sc-trusty.list.save <==
deb http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main

==> /etc/apt/sources.list.d/numix-ppa-trusty.list <==
deb http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/numix-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf


```

I like that idea of getting a really fast distro and then adding what I need on top of it. 

as to: 

```
All that said, ya want to keep on resurrecting this present install ? Or install anew ?
```

I see the pros and cons and am open to siggestions. Since you're the experience brain here, what would do in this case?

In the meantime, I think you're right, the ppas seem to not be working.

---

### Post by Bashing-om on 2015-10-29
33Nicolas; Welp;

The PPA is there, however, my thought that it being disabled as the root of the problem is in error; the PPA is enabled.
Gonna have to think and scratch what to check/where ..
While I am floundering ..
What returns:
```

apt-cache depends libavformat54
apt-cache rdepends libavformat54

```

As to "rolling your own" ... upfront it is a steep learning curve - figuring out what you want, and what it takes to support what you want . 95% of the time the package manager will make up your mind for you . I did the minimal install a few years back, and I have not gone back to a traditional desktop system . Nor will I ever . I like the control . That is just my take. I am a strong advocate of making your system "your" system. Tailored to "your" use case only .
I have an old old 2007 dual core Athlon system - 4 Gigs of ram, I can cold boot in 5 seconds on old spinning hard drives. 'Nuff said ?

[INDENT][INDENT]it is 'buntu
[INDENT][INDENT][INDENT]we can do it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-29
Bashing-Om,

Hum, enticing, enticing. That's why I ran away from MS to Apple, and now a decade later, Apple to Linux. I also have a similar machine and it does not boot up in 5 seconds.

Am I wrong to think I could install a minimalist distro and install only the apps I want and only after I've gone into forums to see what dependencies there are? I've undedicated this computer as my main one and will use the backup laptop I have. I also have an aging 2008 iMac I'm itching to put a proper Linux distribution on. I also have a MacBook Air, whose screen has cracked (amongst other MoBo problems), thank you Apple for your denial that things don't brake on their own and pushing me back to Linux. This apple became sour... There I said it, feels better... Grumble!

In the meantime: 

```
apt-cache depends libavformat54
libavformat54
 |Depends: libavcodec54
  Depends: libavcodec-extra-54
  Depends: libavutil52
  Depends: libbz2-1.0
  Depends: libc6
  Depends: libgnutls26
  Depends: librtmp0
  Depends: zlib1g
  PreDepends: dpkg
    dpkg:i386
  PreDepends: multiarch-support
    multiarch-support:i386
  Breaks: libavformat-extra-54
  Breaks: <libavformat-extra-54:i386>
  Replaces: libavformat-extra-54
  Replaces: <libavformat-extra-54:i386>
  Replaces: libavformat54:i386
  Breaks: libavformat54:i386
```

and 

```
apt-cache rdepends libavformat54
libavformat54
Reverse Depends:
  libavformat54:i386
  libavformat54:i386
  libavfilter3
  libavformat-extra-54
  libavdevice53
  ffmpeg-dbg
  libavformat-dev
  ffmpeg
  audacious-plugins
  libopenscenegraph99
  gstreamer1.0-libav
  ffmpegthumbs
  audacity
  libavformat54:i386
  libavformat54:i386
  vlc-nox
  nepomuk-core-ffmpegextractor
  libkfilemetadata4
  libavformat-extra-54
  libavformat-dev
  libavfilter3
  libavdevice53
  libav-tools
  libav-dbg
  libavformat54:i386
  libavformat54:i386
  zoneminder
  yorick-av
  xbmc-bin
  vlc-nox
  tupi
  survex-aven
  squeezelite-pa
  squeezelite
  spek
  silan
  shotdetect
  python-renpy
  python-libavg
  performous
  paraview
  nepomuk-core-ffmpegextractor
  mpv
  mplayer2
  mplayer-gui
  mplayer
  mpd
  motion
  moc-ffmpeg-plugin
  miro
  mencoder
  mediatomb-common
  lynkeos.app
  lives
  lightspark-common
  libwxsvg0
  libvxl1.17
  libvtk6
  libvtk5.8
  libvisp2.8
  libqmmp-misc
  libphash0
  libopenscenegraph99
  libopencv-highgui2.4
  libmrpt-hwdrivers1.0
  libmrpt-dbg
  libmlt6
  libkfilemetadata4
  libk3b6-extracodecs
  libjitsi-jni
  libgmerlin-avdec1
  libffms2-3
  libffmpegthumbnailer4
  libdlna0
  libchromaprint-tools
  libavifile-0.7c2
  libavformat-extra-54
  libavformat-dev
  libavfilter3
  libavdevice53
  libavbin0
  libav-tools
  libav-dbg
  libaubio4
  kradio4
  kino
  kid3-core
  hedgewars
  harvid
  handbrake-cli
  handbrake
  gstreamer1.0-libav
  gpac-modules-base
  goldendict
  gnash-common
  gmerlin-encoders-ffmpeg
  fuse-emulator-utils
  forked-daapd
  ffmpegthumbs
  ffmpeg2theora
  ffdiaporama
  dvdstyler
  dvbcut
  dff
  cmus-plugin-ffmpeg
  cantata
  bombono-dvd
  blender
  bino
  audacious-plugins
  aubio-tools
  acoustid-fingerprinter
  xjadeo
  transcode
  idjc


```

I'll be away for the next 2 hours but will continue when I get back. Tx

---

### Post by Bashing-om on 2015-10-29
33Nicolas; Yuk;

That did not point me to anything useful in and of it's self.
Tall ya what, let's disable the /noobslab/deepin-sc/ PPA and update/upgrade the system.
Then cogitate what we can do about the PPA depenency .

If ya want to install a "roll your own" we can open a new thread .. and make that happen. Can be a very satisfying experience. You will never stop learning.

[INDENT][INDENT]there is that too
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-29
Bashing-Om, I'm game for the perfect install. After all, that's why I'm here, to get away from the infernal trio and learn to use what I want, when I want it, how I need it. Gulp, scary!

Now, for another backup.

Thanks,

---

### Post by Bashing-om on 2015-10-29
33Nicolas; Evening;

When ya want to begin that "perfect install" download the .iso and burn a CD - it will fit on a CD :
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

In the tutorial - one does not really need a windows manager .. single user system is just more un-needed overhead .

Open a new thread and we take that matter up there.

[INDENT][INDENT]we can do that too[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-30
Bashing-Om,

Holy cow, 34MB only? That is amazing. I'm downloading 15.10 32-bit. I will read the instruction tomorrow, burn a CD and will then create a new thread. Should I just create any thread, as in: How to create the perfect install and that's it? Thanks for clarifying this point.

34MB really?

---

### Post by Bashing-om on 2015-10-30
33Nicolas; Considerations.


Release 14.04 is the current Long Term Support release. Supported 'til April 2019; whereas 15.10 is a interim release of only 9 months before a upgrade to 16.04 is required. Install the current stable 14.04 ... older hardware you want the 14.04.1 release -- that .1 will not utilize HWE and the needless overhead to maintain (H)ard(W)are (E)nablement stack .

32 bit ? why ? less than 2 gigs of ram .. yeah ... it is doable and in most cases better .

As to the title of the new thread .. how about " minimal install guidance " ?? or something along those lines.

Something I did forget to mention, that is important .. Ya got a wired connection to the internet ? There is no initial support for WIFI in this minimalistic install ! All you will have upon the intial install is a bootable kernel and a wired access .

 Then you start building ... as to what you want .. What - if any - Desktop Environment, a web browser ? What special applications ?  ( going to serve files, better served to install a server release ). We will try and stay away from PPAs and stay with managing the softwares with our software repository and our package management system. Some real smart guys developed this system and it do work very well ... makes live much easier in our own cyber world.

[INDENT][INDENT]leaner and faster is better
[/INDENT][/INDENT]

---

### Post by 33Nicolas on 2015-10-30
Bashing-Om, will do my friend.

---

