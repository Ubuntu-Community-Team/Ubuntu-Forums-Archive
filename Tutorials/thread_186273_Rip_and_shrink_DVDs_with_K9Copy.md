---
title: "Rip and shrink DVDs with K9Copy"
date: 2006-06-01
forum: Tutorials
---

### Post by eqisow on 2006-06-01
It seems that there is a wiki for running [DVD Shrink]("https://wiki.ubuntu.com/DVDShrink") in [Wine]("https://wiki.ubuntu.com/Wine"), but no wiki for the excellent Linux native replacement for DVD Shrink, K9Copy, so I decided to create one.

The new wiki page can be found [here]("https://wiki.ubuntu.com/K9Copy"). I will also make this the official discussion thread. :)

---

### Post by matrooswolf on 2006-06-07
Hi thanks for the wiki.
I have a problem, I tried to make a copy of a dvd but the output file is 5,1GB, (I thought K9Copy automatically reduced the size to fit 4,7GB?)
I don't find any settings to correct this.
Any help appreciated!

---

### Post by matrooswolf on 2006-06-07
problem resolved, found the answer in another thread.

Apparently you have to first save the DVD as an iso to disk, then burn it afterwards, that way it stays 4,7GB.  

If you burn directly, size is bigger (no clue why though :-k )

---

### Post by darknuala on 2006-06-08
I've had 50/50 success rate using K9Copy.  It seems to do fine on older dvd's, but I have had Zero success on anything new.  For that, I would have to use DVDFab Decrypter for Windows.  Even DVDShrink, and DVD Decrypter are choking on anything new.

---

### Post by jamesrl on 2006-06-09
I just wanted to add, you might want to try the current version of k9copy (1.0.4).  I had problems backing-up several dvds with the 1.0.2-ubuntu dapper version in the repositories (such as not being able to copy with menus, freezing mid stream on certain dvds, not being able to shrink to the right size).  However with version 1.0.4 installed from source so far (only about 10 dvds) I have had no problem backing up dvds using version 1.0.4, even ones that had errors with k9copy 1.0.2-ubuntu (and i am copying 8.5 Gb dvds to single 4.7 Gb w/o noticable compression loss of quality).   

The only problem is right now you have to install it from source, and have to install several dev packages to do so properly.  I posted a previous post 
[http://www.ubuntuforums.org/showpost.php?p=1098581&postcount=12]("http://www.ubuntuforums.org/showpost.php?p=1098581&postcount=12")
explaining how i got installing the source to work in dapper 6.06.

Cheers.

---

### Post by jamesrl on 2006-06-09
I just added a section to the wiki on installation from source.  I found a changelog online at [http://www.kde-apps.org/content/show.php?content=23885](http://www.kde-apps.org/content/show.php?content=23885) that lists some of the improvements of version 1.0.4-2 over 1.0.2 (dapper version) and 1.0.3 (breezy repos.knit.it version) including: 
> 
v1.0.4-2
- fixed freezes problems with FC5

v1.0.4
- improved compatibility
- take benefit of MMX, SSE, SSE2 for memcpy
- fixed reading of empty titles
- input device combo is editable
- Integration of vamps and requant in k9copy as QThread classes
- fixed size problems
- added video in backup progress dialog
- fixed several issues in multi-angle DVD copy
- Improved the backup speed

v1.0.3b
- fixed compil issue on Suse,FC4....

v 1.0.3 bis
- fixed compil issue with libdvdread 0.9.5

v 1.0.3
- compression of menus
- improved compatibility
- selection by titleset
- fixed ifo update bugs
- added possibility to enter the size of dvd
-...


---

### Post by darknuala on 2006-06-11
When I compile from source I run into these problems.  Installing the dependencies first i get most of them except the following pasted below:

navyn@navyn-desktop:~$ sudo apt-get install kdebase-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-dev: Depends: kdelibs4-dev (>= 4:3.5-rc1) but it is not going to be installed
E: Broken packages
navyn@navyn-desktop:~$ sudo apt-get install kdelibs4-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs4-dev: Depends: libavahi-client-dev but it is not going to be installed
E: Broken packages
navyn@navyn-desktop:~$ sudo apt-get install libavahi-client-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavahi-client-dev: Depends: libdbus-1-dev (>= 0.60) but it is not going to be installed
E: Broken packages
navyn@navyn-desktop:~$ sudo apt-get install lidbus-1-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package lidbus-1-dev
navyn@navyn-desktop:~$

---

### Post by mandragor on 2006-06-13
Although it could be a typo I have to ask: Did you try lidbus-1-dev or libdbu-1-dev?
In the log you pasted you are trying to install the wrong/misspelled package.

---

### Post by zenwhen on 2006-06-13
This application is AMAZING. I'll have to add this app to my short list of KDE applications I prefer. 

1. K3B

2. K9copy

---

### Post by geetarista on 2006-06-13
This has been something that I was looking trying to find for quite some time now.  After reading the wiki and the forum, I've found this program to be perfect.  I have dvdxcopy for windows, but it takes two hours to copy a dvd.  With k9copy it took 30 mins flat and it was *so* easy.  I love it!

---

### Post by nalmeth on 2006-06-13
I'm very happy to have a native DVD Shrinker, but I already have some problems with it, usability wise.

Let me say first, that so far, the thing works, I have successfully shrunk 2/3 DVD's to .iso

K9Copy (repository version)
1. The interface is clean, but it's too stripped down. The open button should be more clearly reserved for reading the CD. There must be a better icon to use for that, and it should be called READ DISK or something, to be more obvious.

2. When I tried to save the file to my media drive, I was told that I can only save files locally, and the window closed. There was no way of bringing the read DVD back into the k9copy interface. I saw what would seem to be the right folder in /tmp/kde-nalmeth, but the files were way to small to be right.
The work was lost effectively. I'll try to file a bug if this isn't fixed in the newer version.

3. When I went through copying the disk again, I saved it "locally" in my /home. Then to my suprise a window pops up saying "Burning to DVD". 
:confused::confused:
This threw me off, because typically that would mean you're burning to a DVD. Or so I would think.
I saw that my drive wasn't trying to do anything, and knew I already had a written disk in the drive, so I left it. At the end, the .iso is sitting where I wanted it.

Suffice to say, I really think the wording of the saving window should be "Ripping to .iso", or just "ripping". Anything but burning, you're doing the opposite. And as I said I think the Open button should be more clearly related to READING THE DISK. I guess all in all it's just a bit of an immature interface. The important thing is that it does the job. 

I like how you can *burn* the shrunken image right in the same interface, but since I don't have a working burner ATM I haven't been able to test it. 

I'd like to try the new one out to see if anything with the interface has changed.

Anyone else a little confused by k9copy at first?

---

### Post by eqisow on 2006-06-13
Hey guys, sorry about neglecting the thread for awhile. I have gone back to the wiki and compiled a .deb for the new version of K9Copy. Hopefully this will save the time and effort of compiling while resolving the issues you guys are having.

Enjoy! :D

Edit: The .deb is located at [http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb](http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb)

---

### Post by Kouya on 2006-06-22
[QUOTE=eqisow]Hey guys, sorry about neglecting the thread for awhile. I have gone back to the wiki and compiled a .deb for the new version of K9Copy. Hopefully this will save the time and effort of compiling while resolving the issues you guys are having.

Enjoy! :D

Edit: The .deb is located at [http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb](http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb)[/QUOTE]

eh i dl the deb and installed it but how do i run k9copy in gnome ubuntu?

---

### Post by foxy123 on 2006-06-22
[QUOTE=eqisow]Hey guys, sorry about neglecting the thread for awhile. I have gone back to the wiki and compiled a .deb for the new version of K9Copy. Hopefully this will save the time and effort of compiling while resolving the issues you guys are having.

Enjoy! :D

Edit: The .deb is located at [http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb](http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb)[/QUOTE]
there are two problems with this deb for me.
1. To run it after install I have to do
```
/usr/local/kde/bin/k9copy
```
it is not in the PATH because I am on Ubuntu.

Secondly, I have an error regarding vamps:
```
An error occured while running DVDAuthor:
vamps: Fatal: write to stdout: No such file or directory
```

---

### Post by rado_london on 2006-06-22
Thanks mate it works great. I just want to know does it work when I rip a Blockbuster DVD to ISO file as I tested it with home made dvd.
Thanks again!

---

### Post by eqisow on 2006-07-03
rado_london, it will work for commercial (Blockbuster) DVD's if you follow the instructions under the "Activate support for encrypted DVDs" section of the wiki.
__________________________________________________

Kouya and foxy123, to fix the issue with running K9Copy in Gnome, run the following command:
```
sudo ln -s /usr/local/kde/bin/k9copy /usr/local/bin/k9copy
```
I updated the wiki to address this problem.
__________________________________________________

foxy123, I'm afraid I'm not sure about your error message. I will have to look into it.

---

### Post by foxy123 on 2006-07-04
[QUOTE=eqisow]foxy123, I'm afraid I'm not sure about your error message. I will have to look into it.[/QUOTE]

Thanks a lot. Though it is solved by running k9copy with sudo. But still I would prefer to run it as a normal user.

---

### Post by stonefeet on 2006-07-04
THAT is beautiful

dvdshrink is about the only reason i'm still keeping windows around
+1 for ubuntu

---

### Post by learning on 2006-07-04
I just re-installed ubuntu and can't get k9copy working again.

I followed the instructions on the wiki to get the latest version.

Here is what appears to be my problem:

Please send bug report - no VTS_TMAPT ??

Any ideas what that is all about, or what I may be doing wrong?
I could copy the entire output if I needed to, but didn't want to fill up the thread with it.

---

### Post by eighty734 on 2006-07-04
Hey all, nice wiki and thread.  But I am having a problem burning.  I have dapper and all the latest software for k9copy.  I save to an iso then go to burn and I get an error saying that there is not enough space on the disk.  This can not be the dvd's are 4.7 gb and the iso is only 4.4 gb.  I also tryed to use k3b to burn and I get the same problem.  Does any one know how to fix this?

---

### Post by learning on 2006-07-04
Not 100% sure but this thread may help you out.

[http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=16769&forum=9&post_id=115969&PHPSESSID=07157f25b0436fa7338124df15fea226](http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=16769&forum=9&post_id=115969&PHPSESSID=07157f25b0436fa7338124df15fea226)

---

### Post by eighty734 on 2006-07-04
Thanks for the link learning but I have tried 'overburning' with no luck.

Edit:
I have had luck with dvdshrink under wine, I save to an iso then burn with k3b.  I am guessing that k9copy is  saving the iso file just over the limit so it will not let me burn.

---

### Post by GMachine_24 on 2006-07-05
[QUOTE=darknuala]I've had 50/50 success rate using K9Copy.  It seems to do fine on older dvd's, but I have had Zero success on anything new.  For that, I would have to use DVDFab Decrypter for Windows.  Even DVDShrink, and DVD Decrypter are choking on anything new.[/QUOTE]


I have found this, too, re: DVDShrink and Decrypter. So, and this is on a Windows machine obviously, .... I use AnyDVD and Nero to just copy the DVD. It is remarkably fast and simple.

---

### Post by ubu-for on 2006-07-27
> **eqisow said:**
> Hey guys, sorry about neglecting the thread for awhile. I have gone back to the wiki and compiled a .deb for the new version of K9Copy. Hopefully this will save the time and effort of compiling while resolving the issues you guys are having.

Enjoy! :D

Edit: The .deb is located at [http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb](http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb)

Your link is broken! :(

---

### Post by pharmd24 on 2006-07-27
Exellent work!

Thanks

---

### Post by eqisow on 2006-07-31
> **ubu-for said:**
> Your link is broken! :(

[http://thepiratecove.org/files/k9copy-1.0.4-2_i386.deb](http://thepiratecove.org/files/k9copy-1.0.4-2_i386.deb)

Sorry about that.

---

### Post by jackkerouac on 2006-08-01
Awesome work!

Kudos!

One question - is K9copy ever going to remove Prohibited User Operations, etc., ala AnyDVD and DVD Decrypter?

---

### Post by ykpaiha on 2006-08-01
great new hopefully it works 
BUT YOUR VERSION INSTALL IN /USR/LOCAL/KDE/ !
whenever you use this folder you get a crash in the system !!
even with a link
so is it possible to build it on an easier usable way
thanks

---

### Post by foxy123 on 2006-08-01
> **ykpaiha said:**
> great new hopefully it works 
BUT YOUR VERSION INSTALL IN /USR/LOCAL/KDE/ !
whenever you use this folder you get a crash in the system !!
even with a link
so is it possible to build it on an easier usable way
thanks

it is easy to build it on your own. Just use --prefix=/usr/local option.

---

### Post by ubu-for on 2006-08-02
> **eqisow said:**
> [http://thepiratecove.org/files/k9copy-1.0.4-2_i386.deb](http://thepiratecove.org/files/k9copy-1.0.4-2_i386.deb)

Sorry about that.

THX! :D

---

### Post by dougwesson on 2006-08-05
O.K. I got K9copy installed and working......(somewhat):-? . I have Ubuntu 6.06 and was trying to compare how well a DVD copy would go under Linux as compared to Windows. I found out about K9Copy and installed it. The first time I ran it and had it scan a DVD it appeared to be reading it, but then the whole program just shut down:-k . I restarted it and got a little further this time. It scanned the DVD and I selected the whole movie with a check mark for copying. I then selected the gear icon to copy the disk and it shut down again](*,) . I am not sure what is going on or how to go about fixing this. Any help would be appreciated and thanks in advance;) .

---

### Post by foxy123 on 2006-08-05
> **dougwesson said:**
> O.K. I got K9copy installed and working......(somewhat):-? . I have Ubuntu 6.06 and was trying to compare how well a DVD copy would go under Linux as compared to Windows. I found out about K9Copy and installed it. The first time I ran it and had it scan a DVD it appeared to be reading it, but then the whole program just shut down:-k . I restarted it and got a little further this time. It scanned the DVD and I selected the whole movie with a check mark for copying. I then selected the gear icon to copy the disk and it shut down again](*,) . I am not sure what is going on or how to go about fixing this. Any help would be appreciated and thanks in advance;) .

I do not know if it helps but for me it works properly only with 'sudo'.

---

### Post by grimmson on 2006-08-08
Any way we could update the repositories to install 1.04 or 1.1? I'd loive to do it myself but I try to stick to only screwing up my system, not everybody elsed (don't know how.)

---

### Post by srunni on 2006-08-08
> **darknuala said:**
> I've had 50/50 success rate using K9Copy.  It seems to do fine on older dvd's, but I have had Zero success on anything new.  For that, I would have to use DVDFab Decrypter for Windows.  Even DVDShrink, and DVD Decrypter are choking on anything new.

This is because of some of the new forms of copy protection on DVDs, such as ARccOS and RipGuard. Many Windows users have also run into this problem, and have turned to AnyDVD as their solution, as it is frequently updated. However, the excellent method by which AnyDVD operates unfortunately makes it more difficult to emulate than DVD Shrink or DVD Decrypter. In fact, AnyDVD is not even listed in the Wine Application Database. I guess we'll just have to wait and see what happens.

---

### Post by gargoyle on 2006-08-14
I am attempting to follow the instruction in the Wiki for installation of the new version.
However I have run into a problem.

If I enter in the following something does not work.
> ed100@ed100-desktop:~$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found


I looked into the above directory but there is no **install-css.sh**, I also did  a search for it but did not find anything. 
What is the problem here?  Was it not copied to the correct folder during installation?
What do I do now?

---

### Post by betty on 2006-08-19
I've got k9copy 1.1 beta working nicely-

One irritation that I always had with DVD Shrink, and it seemed to have made its way to this beta version:  THe Auto-eject 'feature' after it finishes encoding a dvd.  I don't see any option to turn this off... do you know how to do it?

I've got a case with a door in front of the drive, and I like to have it closed.  Can't do that with this auto-ejecting..

Thanks!
betty

---

### Post by stoer on 2006-08-20
Tried installing as described in the wiki.
(Am using Ubuntu and Gnome desktop)
Chose for the Latest Stable Version and installation seemed to go without a hitch...
Except kpcopy doesn't run and i get the following...
XX Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
(cputest.cpp) available multimedia extensions: sse2
k9copy: /dev/hdc resolved to /dev/hdc
k9copy: /dev/hdc is block device (0)
k9copy: /dev/hdc seems to be cdrom
k9copy: (K3bDevice::Device) /dev/hdc: init()
k9copy: (K3bDevice::Device) /dev/hdc feature: CD Mastering
k9copy: (K3bDevice::Device) /dev/hdc feature: CD Track At Once
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD Read
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+R
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+RW
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+R Double Layer
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD-R/-RW Write
k9copy: (K3bDevice::Device) /dev/hdc feature: Rigid Restricted Overwrite
k9copy: (K3bDevice::Device) /dev/hdc: dataLen: 60
k9copy: (K3bDevice::Device) /dev/hdc: checking for TAO
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO_R96P
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO_R96R
k9copy: (K3bDevice::Device) /dev/hdc: checking for RAW_R16
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    MODE SELECT (55)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        26
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: checking for RAW_R96P
k9copy: (K3bDevice::ScsiCommand) failed: 

and much much more!

Plus if i try updating my system at present i am also getting the following...
 E: /var/cache/apt/archives/libk9copy0_1.0.3.2-1_i386.deb: trying to overwrite `/usr/lib/libk9copy.la', which is also in package k9copy

Any ideas? This is one "noobie" thats getting a headache real fast ;)

---

### Post by brm on 2006-08-20
I have installed the Debian package of the 1.1 beta ([http://thepiratecove.org/files/k9copy-1.1.0-beta1_i386.deb](http://thepiratecove.org/files/k9copy-1.1.0-beta1_i386.deb))

After specifying the files I want to save to an .iso, I click on the "save to DVD" icon and am prompted to enter a path and file name. I do so and the process consistently aborts with the message;

```
Insuffisant disk space on
4400 mb expected
```

```
bruce@Thucydides:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             10581552   4248424   5795616  43% /
varrun                  772828       104    772724   1% /var/run
varlock                 772828         4    772824   1% /var/lock
udev                    772828       128    772700   1% /dev
devshm                  772828         0    772828   0% /dev/shm
/dev/sda7              5052504     77292   4718552   2% /home
tmpfs                   772828         0    772828   0% /dev/shm
/dev/sda10            42851776   2341680  40510096   6% /mnt/dmz
bruce@Thucydides:~$
```

On the / and /home partitions, there is not much room over 4400MB. The /mnt/dmz has 40GB free, but it is formatted vfat. Is this genuinely a disk space problem or a program error?

---

### Post by foxy123 on 2006-08-21
try to run it as sudo...

---

### Post by brm on 2006-08-21
I did and the results were not pretty.

Remember that running a graphical application in an X-session is the only circumstance to my knowledge where an unprivileged user has to give permission to root: xhost +localhost.

Awkwardly, in Ku/Ubuntu, such sessions fail anyway; I have seen this with several other applications besides k9copy. There is a problem with MIME registrations: first, one gets an error box stating that the MIME type application/octet-stream is not registered, and then another error box stating that there are no MIME types registered.

So I went hunting for where to turn on root logins to XWindows. Brought up k9copy and tried saving to /tmp as before. Same error (Insuffisant ...; the author, clearly, is French). Only this time, k9copy unmounted my two data partitions /home and /mnt/dmz (which is a >40GB FAT32 partition for transferring between Linux and a paid-for operating system, one which I try never to use). Running as root, k9copy was able to unmount those partitions; at least, it didn't trash them as well.

As I said, not pretty.

---

### Post by nrayever on 2006-08-22
> **eqisow said:**
> It seems that there is a wiki for running [DVD Shrink]("https://wiki.ubuntu.com/DVDShrink") in [Wine]("https://wiki.ubuntu.com/Wine"), but no wiki for the excellent Linux native replacement for DVD Shrink, K9Copy, so I decided to create one.

The new wiki page can be found [here]("https://wiki.ubuntu.com/K9Copy"). I will also make this the official discussion thread. :)

thanks a lost eqisow. i was looking for a howto like this one!! i will try in a few days. continue making more howto's like this!!

:D :D :D 

nrayever

---

### Post by andiii on 2006-08-22
I can't get k9copy running (beta 1.1.0)

DVD Copy won't work, it says "dvdauthor error" after doing 
libdvdread: Using libdvdcss version 1.2.5 for DVD access

---------

To make an mpg4 seems to work, but there is no file produced.

When I run k9copy from terminal I get:

```
libdvdnav: Unable to find map file '/home/abcdefg/.dvdnav/CATCH_ME_IF_YOU_CAN.map'

libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012f

libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000235ff

libdvdread: Elapsed time 0

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00049052

libdvdread: Elapsed time 0

libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003c8e58

libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003c8e5d

libdvdread: Elapsed time 1

libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003ca981

libdvdread: Elapsed time 0

libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003ca986

libdvdread: Elapsed time 0

libdvdread: Found 3 VTS's

libdvdread: Elapsed time 1

Mutex destroy failure: Device or resource busy
Mutex destroy failure: Device or resource busy

Mutex destroy failure: Device or resource busy


```

I can play the DVD in k9copy, but thats it :(


Any ideas?

---

### Post by SZF2001 on 2006-08-29
I am also getting an error and can't open k9copy.

```

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
k9copy: /dev/sr0 resolved to /dev/scd0
k9copy: /dev/scd0 is block device (0)
k9copy: /dev/scd0 seems to be cdrom
k9copy: bus: 1, id: 0, lun: 0
k9copy: (K3bDevice::Device) /dev/scd0: init()
k9copy: (K3bDevice::Device) /dev/scd0 feature: CD Mastering
k9copy: (K3bDevice::Device) /dev/scd0 feature: CD Track At Once
k9copy: (K3bDevice::Device) /dev/scd0 feature: CD-RW Media Write Support
k9copy: (K3bDevice::Device) /dev/scd0 feature: DVD+R
k9copy: (K3bDevice::Device) /dev/scd0 feature: DVD+RW
k9copy: (K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
k9copy: (K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
k9copy: (K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
k9copy: (K3bDevice::Device) /dev/scd0: dataLen: 60
k9copy: (K3bDevice::Device) /dev/scd0: checking for TAO
k9copy: (K3bDevice::Device) /dev/scd0: checking for SAO
k9copy: (K3bDevice::Device) /dev/scd0: checking for SAO_R96P
k9copy: (K3bDevice::Device) /dev/scd0: checking for SAO_R96R
k9copy: (K3bDevice::Device) /dev/scd0: checking for RAW_R16
k9copy: (K3bDevice::Device) /dev/scd0: checking for RAW_R96P
k9copy: (K3bDevice::Device) /dev/scd0: checking for RAW_R96R
k9copy: (K3bDevice::ScsiCommand) failed:
k9copy:                            command:    READ DVD STRUCTURE (ad)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        28
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/scd0: READ DVD STRUCTURE length det failed
k9copy: (K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 8
k9copy: (K3bDevice::Device) /dev/scd0 : 22160 KB/s
k9copy: (K3bDevice::Device) /dev/scd0 : 16620 KB/s
k9copy: (K3bDevice::Device) /dev/scd0 : 11080 KB/s
k9copy: (K3bDevice::Device) /dev/scd0 : 8310 KB/s
k9copy: (K3bDevice::Device) /dev/scd0 : 5540 KB/s
k9copy: (K3bDevice::Device) /dev/scd0 : 3324 KB/s
k9copy: (K3bDevice::Device) /dev/scd0 : 2770 KB/s
k9copy: (K3bDevice::Device) /dev/scd0 : 1385 KB/s
k9copy: (K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 22160
k9copy: /dev/scd0 resolved to /dev/scd0
k9copy: /dev/scd0 is block device (0)
k9copy: /dev/scd0 seems to be cdrom
k9copy: (K3bDevice::DeviceManager) dev /dev/scd0 already found
k9copy: /dev/hdc resolved to /dev/hdc
```
And then it just sits there forever. I end up having to restart the computer because I do it in sudo and it takes the root privilages, even after I've closed the shell.

---

### Post by BLTicklemonster on 2006-09-02
Installation was pretty straightforward, nice interface, seems to be running okay. I'll get back to you when I finish, but everything looks great so far!

So anyway, the real reason I wanted to post, other than being a jabberjaw, is that I noticed that problem with an extracted directory from an iso being larger than a target disk. I suppose there's a logical explanation... that's probably why I have no idea why it does that.

Thanks for the wiki/guide!!!

---

### Post by BLTicklemonster on 2006-09-07
My hard drive started clicking, so I loaded up on a new one, and now the wiki you like to won't load up, and k9copy.sourceforge.net won't either.

---

### Post by brm on 2006-09-07
I finally have k9copy working (very nicely). There are several issues to watch out for:

1. make sure that you have taken care of all dependencies. If you download a recent .deb from a site such as [www.thepiratecove.org](www.thepiratecove.org) and install it with sudo dpkg -i <debname>.deb, there is no dependency checking.
2. ensure that the "output" directory under |Configure|DVD has at least twice as much free space as the total size of the titles you are trying to back up. Calling this directory an "output" directory is not a happy choice; it would have been more apt to call it a "scratch" directory or "working files" or, God forbid, "t(e)mp.
3. If the partition with /tmp does not have > 10GB free (mine doesn't), do not succumb to the temptation of using a FAT32 "transfer" partition. Remember the infamous 2GB file size limit.

k9copy is simple and easy to use and produces excellent results once it is properly installed and configured

Bruce

---

### Post by BLTicklemonster on 2006-09-08
I'm getting an error that says 

dvdauthor error

Why?

---

### Post by brm on 2006-09-09
BLTicklemonster,
Because I am an experienced user rather than a code monkey, I might have the explanation wrong, but it appears to work for me. Your mileage may vary.

After installing an application manually (this includes dpkg -i ... ), it has been my experience that the new application sometimes has trouble "finding" its dependencies. Running (as root) updatedb solves the problem.

This happened to me when I installed the k9copy 1.1 beta into Dapper. I got the same dvdauthor error as you and ran updatedb after which k9copy worked exactly as advertised.

Hope this helps
Bruce

---

### Post by BLTicklemonster on 2006-09-09
Thanks. It's apparent that you're more of a monkey than I am, though. I have no idea how to implement what you suggest, unless it's to bring up terminal and ... um... could you draw this ape a picture?


*edit:

Oh, sudo updatedb

---

### Post by BLTicklemonster on 2006-09-09
Okay, it's working! Thanks a ton! Now what would a person use to shrink that puppy down to 4 gig so I can "archive" it?

*edit

No wait, it looks like it's already doing that. Titleset 1 is 4.7 gig. Huh.

---

### Post by brm on 2006-09-09
Unless you have drastically changed Ubuntu defaults (which it sounds like you probably haven't) updatedb is routinely run as part of the daily cron job --- generally at some ungodly hour of the morning. Sometimes, however, it makes sense to run it right now. In a terminal:

```
sudo updatedb
```

Hope this helps.
Bruce

---

### Post by BLTicklemonster on 2006-09-09
That worked.


Yikes.

```
libdvdread: Get key for /VIDEO_TS/VTS_27_0.VOB at 0x003f9f87
libdvdread: Elapsed time 0
libdvdread: Found 26 VTS's
libdvdread: Elapsed time 0
Mutex destroy failure: Device or resource busy

```

and it locked up.

---

### Post by emmanuel.brasil on 2006-09-11
> **foxy123 said:**
> it is easy to build it on your own. Just use --prefix=/usr/local option.

I must start saying that Im not expericed at all in any linux distribuition. It just happens that in my old computer I couldnt use win anymore. I seems that with Kubuntu is not so difficult! 
Im trying in the last few days to make a copy of DUMBO for my 3 year old doughter and I cant make it work. I tryed dvdrip but is too complex. I have installed k9copy from ad and remove progrmas but the old version did not work fine with some erros ](*,) . So I downloaded the deb packege with the 1.04 version from the link earlier in this forum but had the same problem of crashing while reading the DVD. 
I didnt understand the explanation above for a possible solution in my case.

Could give me some help? :confused: ...please:mrgreen:

---

### Post by BLTicklemonster on 2006-09-11
I gave in and went and booted to xp and used dvd to burn it in no time flat. 

That totally sucks. I really really really want to get off of xp, but like it or not, it's my failsafe.

---

### Post by foxy123 on 2006-09-12
it works fine for me, though I have to run it as sudo. the last 1.10 beta is quite nice...

---

### Post by BLTicklemonster on 2006-09-23
First off, I redid wine using this guide, then installed dvd decrypter again, and it recognizes that I have a dvd now. [http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine)

Secondly, there's this that you might want to try, I use it on windows xp:

Link to ripit4me
[http://www.ripit4me.org/download.html](http://www.ripit4me.org/download.html)

Link to fixVTS
[http://www.videohelp.com/~FixVTS/](http://www.videohelp.com/~FixVTS/)

Guide to ripit4me

[http://forums.afterdawn.com/thread_view.cfm/360110](http://forums.afterdawn.com/thread_view.cfm/360110)

once you get wine installed, double click on ripit4me and follow the instructions.

---

### Post by orb9220 on 2006-09-26
Well I thought I'd post here first. Why is k9 creating a 4.7gb disc when I try to right click burn iso there is not enough space. Same with sky captain came out as 4.5gb still can't burn. 


Now people talk about then installing  k3b with overburn checked but what is the poinst if all other programs consider a sl disk as 4464mb which is 4.38gb then why dosn't k9?

That is why I still use dvdshrink under wine.

1) It allows me to set custom size for file or iso which is great for  those cheaper disc which are not good for overburning or even filling up  to the max of 4.38gb

2) It allows me to save as a video_ts folder which allows me to save it to a fat32 hd which gets around the 4gb single file limitation.

3)It allows me to replace annoying warnings at beginning with my own  stills and maintain's dvd navigation menu's.

4) Allows me to do custom compression like max compress on extra's so main movie gets more space.

5) Click reauthor to get just the main movie and set the start and finish frames. Note: Great for taking 2-disc 2-part movies. Have ripped like cleopatra which is a two disc and reauther both to one Long movie disc. Have gotten up to 4hr long movies this way. Of course you lose quality but it  is still quite watchable.

6) Does k9 even allow opening an iso for rencoding without having to mount iso first? But dvdshrink does which is nice so I can get those stupid 4.7 yes I said stupid because this is not even an issue in the windows world  of dvd ripping programs they all know about 4.38gb disks.

Now you may think of me as a spoiled windows user whining. That is not the case. I have converted to ubuntu with glee and awe at the power of linux. 

But that dosn't mean I am going to put on rose-covered glasses and pretend that the gui linux dvd ripping programs are on par with the windows programs they are not, not yet anyways. But I have the faith they will be and hope they come in full bloom.

Until that day I recommend dvdshrink. And will keep an eye on k3b,k9 and others.

And if any can answer the question at the beginning of this post thanks.

---

### Post by BLTicklemonster on 2006-09-26
Dang, I would be in windows when you ask that. I burned one finally that worked, but I don't remember what I did. Someone will be along with the answer soon, if not I'll post tonight.

---

### Post by orb9220 on 2006-09-26
Found it repo's have 1.0.2 which does not have the ability to adjust iso final size. The latest is 1.1.0 something.

I would wish they would put a damn date on the repo's so we can determine if we need to go elsewhere to get the latest.

---

### Post by secdroid on 2006-09-28
As a Gnome user, I'm not getting anything when clicking on k9copy's "help."  Nothing at project's homepage or sourceforge.  I noticed in the .deb that there is documentation in docbook format.

Is there any easy way for me to get access this info?  Docbook is well documented, but there don't seem to be any docs for novices on how to quickly translate to .html or .pdf.

---

### Post by BLTicklemonster on 2006-09-28
> **orb9220 said:**
> Well I thought I'd post here first. Why is k9 creating a 4.7gb disc when I try to right click burn iso there is not enough space. Same with sky captain came out as 4.5gb still can't burn. 


Now people talk about then installing  k3b with overburn checked but what is the poinst if all other programs consider a sl disk as 4464mb which is 4.38gb then why dosn't k9?

That is why I still use dvdshrink under wine.

1) It allows me to set custom size for file or iso which is great for  those cheaper disc which are not good for overburning or even filling up  to the max of 4.38gb

2) It allows me to save as a video_ts folder which allows me to save it to a fat32 hd which gets around the 4gb single file limitation.

3)It allows me to replace annoying warnings at beginning with my own  stills and maintain's dvd navigation menu's.

4) Allows me to do custom compression like max compress on extra's so main movie gets more space.

5) Click reauthor to get just the main movie and set the start and finish frames. Note: Great for taking 2-disc 2-part movies. Have ripped like cleopatra which is a two disc and reauther both to one Long movie disc. Have gotten up to 4hr long movies this way. Of course you lose quality but it  is still quite watchable.

6) Does k9 even allow opening an iso for rencoding without having to mount iso first? But dvdshrink does which is nice so I can get those stupid 4.7 yes I said stupid because this is not even an issue in the windows world  of dvd ripping programs they all know about 4.38gb disks.

Now you may think of me as a spoiled windows user whining. That is not the case. I have converted to ubuntu with glee and awe at the power of linux. 

But that dosn't mean I am going to put on rose-covered glasses and pretend that the gui linux dvd ripping programs are on par with the windows programs they are not, not yet anyways. But I have the faith they will be and hope they come in full bloom.

Until that day I recommend dvdshrink. And will keep an eye on k3b,k9 and others.

And if any can answer the question at the beginning of this post thanks.

Good job hitting the nail on the head. I get tired of posting, "I can't get dvds to rip, or I can't this that and the other thing" and some yahoo posts, "I did with no problem, you obviously did something wrong", then they disappear. (I don't think they even use linux, they're just aliens from the planet Trollopia stirring up trouble)

Good points, all. I have given up on even thinking about using any of the schlockware that linux has for burning anything (even down to floppies, thank you), and will keep a dual boot to windows at all times for situations where I need to rip or burn. I have dvdshrink and decrypter for linux, both, but would rather just boot to windows and not have the possibility of problems. Besides, there's ripit4me that works in windows. I have tried it in wine in linux, and it doesn't work yet. I'll keep messing withit, but so for, no good.

And please, if anyone can make a guide for a common person that explains in detail how to make dvdrip work, mate with some humans so our gene pool will evolve...

---

### Post by secdroid on 2006-09-28
I'm running k9copy 1.1.0-beta1 on X86 Dapper.  I'm having partial success, but don't know what to do to fix my remaining problems.

The k9copy authors are obviously fine programmers, but the human factors leave something to be desired.  The "output directory" appears to be the temp directory that gets the shrunken audio/video files.

I can successfully play the k9copy "output directory" with VLC.

However, the mkisofs failed with no error information.  Suggestions?  Given that I have the full (shrunken) DVD image on hard disk, can anyone suggest the correct mkisofs options so that it can be done manually?

The video's top-level menus work, but the (chapter) menus within titles hang  VLC, so I assume that they were not correctly generated.  Ideas?

I'd love to find a way to avoid Windows or one of the more complicated Linux encoder scripts, but k9copy's human factors aren't quite up to the job at this point.  So close...

---

### Post by secdroid on 2006-09-28
> The video's top-level menus work, but the (chapter) menus within titles hang VLC, so I assume that they were not correctly generated. Ideas?

Appears to be a VLC issue.  I just made a DV-9 to DV-9 (DL) backup and VLC had the same problem.  Disc worked fine on a standalone DVD player.

None of the Linux DVD players are entirely reliable.  Mplayer, while very capable, is also quite unstable.  Totem...sigh....

Gotta give kudos to the devlopers of k3b.  Great function, stability, reliability, human factors, and documentation.  Equal or better to any commercial product on any OS.  It prompted me twice during the DV-9 backup, allowed me to fix the problems it saw, resumed to continue on to a successful backup.

---

### Post by secdroid on 2006-09-28
I've been looking at alternatives to k9copy.

The book _Linux Multimedia Hacks_ describes > Hack #65 Convert Dual-Layer DVD to Single-Layer DVD

This technique uses [http://dvdshrink.sourceforge.net/]("http://dvdshrink.sourceforge.net/")

I've spent a little time with it.  The install.sh script will identify a number of dependencies which can be satisfied with apt-get.  The script will then hang while trying to copy a named pipe.

Commenting the copy out and doing the file copy steps manually allows the script to complete.  I then configured the tool and tried running it.

Unfortunately, there are binding issues between perl and gtk2 that result in Gnome session manager authentication failure.

I'm not going to spend any more time with it.

Wine and Windows "DVD Shrink" are starting to look attractive.

---

### Post by blasco51 on 2006-10-23
When I install and run, on dapper 6.06.1 LTS, either the stable or the beta version from the deb packages at thepiratecove.org I get the following error:

/usr/local/kde/bin/k9copy: error while loading shared libraries: libkparts.so.2: cannot open shared object file: No such file or directory

I discovered this is caused because it is dependent on package kdelibs4c2a which is not installed by default

---

### Post by SZF2001 on 2006-11-16
I can't even get the program to run on my computer... I changed the file like the wiki said to be in GNOME instead of KDE, but it won't even run.

I tried it with sudo and a terminal, and this is what happens if I let it sit there for twenty minutes or so:

```
sudo k9copy
Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
```
Is it because my DVD drive is USB based? It keeps saying stuff about desktop entrys and stuff... I'm still a Linux (and Ubuntu) newb with all this, I'm not sure what to do. ](*,)

---

### Post by tchoklat on 2006-11-28
Hi,

I am also looking for a good Linux DVD ripper/copyier. On Windoze I used what I believe is the best of the best - [http://www.1clickdvdcopy.com/](http://www.1clickdvdcopy.com/) but I do not have a windows partition anymore!

This will, with 15 secs of configuration thru the great GUI, remove all the adds, menus etc (if required to fit on a 4.7 Gb DVD), then burn to DVD. If the entire DVD will already fit on a 4.7 Gb DVD it will prompt to make an exact copy. It will also copy DVD9 disks as well. It is fast and I have not found a DVD it will not copy - as long as you have Slysoft running in the background.

I have tried the two under Wine with no success as I am a little new to do it.


Tony

---

### Post by ardchoille42 on 2007-01-17
> **eqisow said:**
> Hey guys, sorry about neglecting the thread for awhile. I have gone back to the wiki and compiled a .deb for the new version of K9Copy. Hopefully this will save the time and effort of compiling while resolving the issues you guys are having.

Enjoy! :D

Edit: The .deb is located at [http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb](http://thepiratecove.org/files/k9copy-1.0.4-2_2-1_i386.deb)

Link does not work, gives a 404 error.

EDIT: Never mind, I read further in the thread and found the the link change. Perhaps fixing the link earlier in the thread? I think some folks may be finding the first link they come to doesn't work and they give up on the thread.

---

### Post by ardchoille42 on 2007-01-18
By the way, I installed k9copy on Ubuntu Dapper from the repos with: "sudo aptitude install k9copy" and the install went fine. Using k9copy to rip a DVD9 (Terminator3 Rise of the machines) to a DVD5 went without problems and the DVD plays fine in MPlayer, Xine and my set top DVD player.

I also installed xdvdshrink with these steps:

1) sudo aptitude install transcode mjpegtools subtitleripper gocr
2) Download xdvdshrink from [here]("http://sourceforge.net/project/showfiles.php?group_id=133818")
3) Unpack it and run the install.sh file as root. The installer will check for the existance of the above 4 packages (step 1) and will refuse to install if they are absent.
4) You'll need to add xdvdshrink to the gnome menus (or kde menus?). The command to use in the menu item (or launcher) is: /usr/bin/xdvdshrink.pl

Using xdvdshrink to rip a DVD9 (Terminator3 Rise of the machines) to a DVD5 went without problems and the DVD plays fine in MPlayer, Xine and my set top DVD player.

Now, there are two good DVD rippers. Goodbye Window + dvdshrink :)

---

### Post by penquin on 2007-01-19
I am new to k9copy.  Is there a difference if I use k3b or us k9 to burn it or should I just make an iso and then burn it?  I tryed it both ways (not the iso burn method) and both don't play on my home dvd player (it may be because it is a dvd burner in its own right).  please help I don't want to have to keep switching to windows to back up my movies.

---

### Post by PaJoe on 2007-03-15
My experience thus far:

I have burned several previously decrypted  iso images using K3b, NeroLinux and Gnomebaker, and the programs work 1 time then require a reboot before being able to burn another. I tried turning off auto eject and a few other things but so far no luck. I have started using the command line, which has worked  every time so far. growisofs -dvd-compat -Z /dev/hdc=filename.iso. I am happy using the command line and hate needing to reboot, so burring the image to the dvd using  the command line is fine with me.

Most recently I used k9copy to shrink a dvd9 to dvd5 iso, complete with menus and it worked OK after using 
growisofs -dvd-compat -Z /dev/hdc=filename.iso I have yet to try ripping a previously purchased dvd. 

Other than dvdshrink and dvd decrytper, I have yet to find anything that works well in wine. I tried several versions of Slysoft AnyDvd and a few other programs to handle the dvd decryption.   I have been unable to find any really good methods in linux to make a backup of a recently purchased dvd, but still looking.

---

### Post by Bias on 2007-03-24
Looks like I'm running a bit behind the rest of you :)

Having a bit of trouble with this but a simple question:-

When K9 is creating an ISO image does it create a single ISO file? That's what I would expect but all I get is a directory with video_ts and audio_ts directories in. In the video_ts directory there are the files found in the same directory on the DVD. Seems I could do that by just copying them!

Thanks,

Nick.

---

### Post by BLTicklemonster on 2007-03-24
I've given up, put a new install of ubuntu on, and found a way to get to reiser fs partitions from XP, and haven't put the first thing relating to dvd writing on here, and don't intend to. I'll just relegate myself to keeping that xp partition for ripping dvds.

---

### Post by splendid on 2007-04-06
How would you install K9 for AMD 64 version of 5.10?

---

### Post by andyanderso on 2007-04-08
I love this application when it is working on my machine.  However, it seems to "break" sometimes.  I have made backups of about 10 of my dvds and then I started getting an error message:
An error occured while running DVDAuthor:
dvdauthor: dvdvob.c:1297: FindVobus: Assertion `p>=s->vi[i-1].sectpts[1]' failed.
I tried reinstalling all the packages that k9copy uses and k9copy and it started working again for 3-4 more dvds then i am back to the same message.  

Anyone have any thoughts?

this is apparently happening to other people as well see this post:
[http://ubuntuforums.org/showthread.php?t=357813&highlight=k9copy](http://ubuntuforums.org/showthread.php?t=357813&highlight=k9copy)

no one has answered him so I thought I would try posting in this topic since you guys seem to know alot about k9copy.  

andy

---

### Post by jmervyn on 2007-05-05
Unfortunately, I've stumbled into some trouble with k9copy.  The program is fantastic, but as noted it sometimes can lack integration - for those of us who aren't true wizards, it can be a challenge.

After a new install of Ubuntu 7.04, I receive errors as noted [here](http://ubuntuforums.org/showthread.php?t=355174), but before the interface even appears.  I made the mistake of manually loading the 'stable' (non-beta) version as well as k3b.  Now I don't get the SIGSEGV error - in fact, there's no errors at all but the interface simply closes.

> **BLTicklemonster said:**
> I'll just relegate myself to keeping that xp partition for ripping dvds.Don't give up! It worked a treat in my previous FC5 existence, and I had it work a few times before I moved up to Feisty.  I suspect my problem lies in trying to outsmart

---

### Post by futsoulja on 2007-05-15
Hello,

 I'm having a problem with K9Copy and thought someone here might be able to help. Iv'e searched the forums, google, all over the net and can't seem to find an answer.

When I copy a DVD using K9Copy, I check the boxes next to subtitles and select the audio and video tracks that I want. However when the process is finished and I watch the movie, there are no subtitles.

I've tried several ways of doing this, just selecting the english subtitle, selecting all subtitles, selecting everything on the entire DVD and burning to a Dual Layer DVD.... still no subtitles.

Am I missing anything? Is is a dependency issue? In the software it looks like everything is working, but at playback I get nothing. The disk I'm trying to copy is BABEL. It has many scenes with different languages and without subtitles it's pointless to watch.

Does anyone know why this isn't working?

Here is the output when I run K9Copy from a terminal

-------------------------------------------------------------

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode: 147
  Minor opcode: 3
  Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode: 147
  Minor opcode: 3
  Resource id: 0x0
Failed to open device
libdvdnav: Using dvdnav version 1.1.1-3 from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: BABEL_DOMESTIC
libdvdnav: DVD Serial Number: 35938B9D
libdvdnav: DVD Title (Alternative): BABEL_DOMESTIC
libdvdnav: Unable to find map file '/home/kyle/.dvdnav/BABEL_DOMESTIC.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Using dvdnav version 1.1.1-3 from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: BABEL_DOMESTIC
libdvdnav: DVD Serial Number: 35938B9D
libdvdnav: DVD Title (Alternative): BABEL_DOMESTIC
libdvdnav: Unable to find map file '/home/kyle/.dvdnav/BABEL_DOMESTIC.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

---------------------------------------------------------------------------------

I'm using K9copy version 1.1.1-3 under Gnome on Ubuntu 7.04 Feisty Fawn.

Thanks!

---

### Post by Useff on 2007-05-16
> **futsoulja said:**
> Hello,

 I'm having a problem with K9Copy and thought someone here might be able to help. Iv'e searched the forums, google, all over the net and can't seem to find an answer.

When I copy a DVD using K9Copy, I check the boxes next to subtitles and select the audio and video tracks that I want. However when the process is finished and I watch the movie, there are no subtitles.

I've tried several ways of doing this, just selecting the english subtitle, selecting all subtitles, selecting everything on the entire DVD and burning to a Dual Layer DVD.... still no subtitles.

Am I missing anything? Is is a dependency issue? In the software it looks like everything is working, but at playback I get nothing. The disk I'm trying to copy is BABEL. It has many scenes with different languages and without subtitles it's pointless to watch.

Does anyone know why this isn't working?

Here is the output when I run K9Copy from a terminal

-------------------------------------------------------------

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode: 147
  Minor opcode: 3
  Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode: 147
  Minor opcode: 3
  Resource id: 0x0
Failed to open device
libdvdnav: Using dvdnav version 1.1.1-3 from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: BABEL_DOMESTIC
libdvdnav: DVD Serial Number: 35938B9D
libdvdnav: DVD Title (Alternative): BABEL_DOMESTIC
libdvdnav: Unable to find map file '/home/kyle/.dvdnav/BABEL_DOMESTIC.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Using dvdnav version 1.1.1-3 from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: BABEL_DOMESTIC
libdvdnav: DVD Serial Number: 35938B9D
libdvdnav: DVD Title (Alternative): BABEL_DOMESTIC
libdvdnav: Unable to find map file '/home/kyle/.dvdnav/BABEL_DOMESTIC.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

---------------------------------------------------------------------------------

I'm using K9copy version 1.1.1-3 under Gnome on Ubuntu 7.04 Feisty Fawn.

Thanks!

I'm having a problem similar to this where I choose certain subtitles and they're either not there or classified under different languages. For example, I would select English and Spanish subtitles for a DVD. When playing the DVD and choosing English subtitles, I'd get nothing. If I chose Spanish subtitles, I'd get the English subtitles. Any suggestions?

---

### Post by BLTicklemonster on 2007-05-19
> **eqisow said:**
> It seems that there is a wiki for running [DVD Shrink]("https://wiki.ubuntu.com/DVDShrink") in [Wine]("https://wiki.ubuntu.com/Wine"), but no wiki for the excellent Linux native replacement for DVD Shrink, K9Copy, so I decided to create one.

The new wiki page can be found [here]("https://wiki.ubuntu.com/K9Copy"). I will also make this the official discussion thread. :)

There are sites for using dvdshrink, dvddecryptor, etc, that have exact instructions from step one all the way to the end, with images. Can you do this on your wiki for people who may not be linux savvy and may not quite get how to do things, or for people who just never tried anything like this? A guide is a great tool to have. 

I'm trying this again. It looks to me like things are right now, and I can use k9 to make an iso, then burn it in k3b and have an archived copy of new dvds, is this right? Or does the new version allow me to do a straight rip to dvd? Does this work with new dvds? I hate buying a dvd and leaving it to the whims of nature, i.e. letting other humans touch it, knowing full well that they will scratch it. 

I sure hope this works, as I'm tired of wasting an entire hard drive on XP, and ripping dvds is about the only thing that is keeping me with a foot in the door of XP.

---

### Post by yabbadabbadont on 2007-05-19
> **BLTicklemonster said:**
> There are sites for using dvdshrink, dvddecryptor, etc, that have exact instructions from step one all the way to the end, with images. Can you do this on your wiki for people who may not be linux savvy and may not quite get how to do things, or for people who just never tried anything like this? A guide is a great tool to have. 

I'm trying this again. It looks to me like things are right now, and I can use k9 to make an iso, then burn it in k3b and have an archived copy of new dvds, is this right? Or does the new version allow me to do a straight rip to dvd? Does this work with new dvds? I hate buying a dvd and leaving it to the whims of nature, i.e. letting other humans touch it, knowing full well that they will scratch it. 

I sure hope this works, as I'm tired of wasting an entire hard drive on XP, and ripping dvds is about the only thing that is keeping me with a foot in the door of XP.

In the past I was able to rip and burn backups of DVDs using win2k running inside of vmware.  I just had to make the VM large enough to have the necessary space.  Just something to consider if you can't get the native apps to work.  (most of the native apps can't handle the newest copy protection schemes used by Sony)

---

### Post by goodtimetribe on 2007-06-07
k9copy consistently crashes or aborts during the shrinking to dvd for me, saying that DVDAuthor was the cause. It does fine to create XVid. Anyone else have any suggestions for this kind of issue?

Thanks,

---

### Post by shanerdaner on 2007-06-09
Same here I have a 64bit processor could that be the problem?


:popcorn:

---

### Post by jackkerouac on 2007-06-27
> **goodtimetribe said:**
> k9copy consistently crashes or aborts during the shrinking to dvd for me, saying that DVDAuthor was the cause. It does fine to create XVid. Anyone else have any suggestions for this kind of issue?

Thanks,

Try upgrading to 1.1.1-3. I had the same problem with 1.1.0-beta, but once I upgraded, it went away.

---

### Post by barunio on 2007-07-01
Is it possible to listen to audio while previewing tracks in K9copy? The video appears fine in the preview for me, but no audio..  Is this a configuration problem on my system or a known limitation of k9copy?

---

### Post by penquin on 2007-07-20
does anyone know how to switch the default output from pal to ntsc?  I can't seem to watch any backup I make with k9copy on most of my dvd players.

---

### Post by Foxmike on 2007-07-20
Just for you guys to know, here's a little guide to compile k9copy from source.  It worked without a flaw for me and the lastest version is working much better IMHO.  Here it is:[http://doc.gwos.org/index.php/K9copy](http://doc.gwos.org/index.php/K9copy)

---

### Post by toecutter on 2007-08-08
Your compilation instructions worked great for me Foxmike, thanks very much! I was worried when I saw 'i386' in your instructions but however the compiler works it detected my AMD64 and made it work.

I was able to start copying a DVD but unfortunately I experienced the same crash I had before I upgraded from 1.1.0. I can't even report it on bugs.kde.org like the crash handler requests because k9copy isn't one of the programs you can report! Does anyone have a clue? 

Before I installed Ubuntu on the hard drive I'm using now I was using 6.10 and k9copy and k3b to backup dvd's with zero problems. Now it's nothing but crashes. k9copy is the easiest method I found before, I'd rather not have to configure Wine and loads of other programs to get a copy...but I suppose if I have to I must.

---

### Post by andyanderso on 2007-08-15
I have been using K9copy for sometime now and thought it was working great.  I went to play one of my DVD's that I made with K9copy in a set top dvd player and it will not play.  After some experiments I found that the DVD's i made will only reliably play in my Ubuntu machine - not my wife's mac, no set top dvd players and only a few random windows computers?  I don't know where to start looking for how to fix this problem.  Anyone have any ideas?

andy

---

### Post by SycloneMedia on 2007-08-20
How do you clear your preferences or any config changes to default?

I installed the k9copy package and its dependents. It started up fine. I went into the config window and checked off like only 2 or 3 boxes pertaining to burning options or something and now it will not start up.

It crashes automatically on launch. ???

I uninstalled the package and then reinstalled it, but still the same thing. Help!

Here is the log:

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1240941936 (LWP 5688)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x00000000 in ?? ()
#7  0x08071a16 in ?? ()
#8  0x00000000 in ?? ()

```

It's installed on my AMD pc with Xubuntu, not my Powerbook.

---

### Post by azwli on 2007-08-27
Hello, I have been trying to get k9copy to shrink and copy but I must be missing something in the process.  If I set it to burn with KB3, it copies for about half an hour then KB3 tells me to put in a double layered DVD.  So It didn't shrink it.  If I set it to burn with k9copy, it gets to 99% in the read process and stalls indefinitely without starting the burn.  I read somewhere that I need to make an ISO image first, so I tried that and got the same results. 

could someone point me to some clear instructions or tell me what I am doing wrong?

I am using k9copy 1.1.0 and kde 3.5.6

Thanks,

Jason

I solved this  by using kdesu k9copy and checking "keep original menus" The copy did not come with menu, subtitles, or commentary, but at least the movie is there and I am sure the rest is possible.

---

### Post by Prometheus28 on 2007-12-25
this program works really reeally good. I have installed the latest k9copy from website, and i can backup dvd very easily :P


Although, i am very curious as to how it compresses a dvd to half the size with no difference in quality. extremely good compression ?????????











Also it took me four days to figure out how to work this ::::::::

Activate support for encrypted DVDs

You need to install libdvdcss2 to have support for encrypted DVD playback. To do this, enter the following, one line at a time, in the terminal:

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/examples/install-css.sh


from [https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

---

### Post by John_T on 2008-02-05
I've made about a dozen  ISOs using K9copy so far, and must say that I've found it generally quite straightforward.

My aim is to create iso's of my kids DVDs to the hard disk, so that I can play them from my Ubuntu media center without searching for and loading disks.  I'm using VLC to play the ISO files, which works fine.  I've no desire at this point to burn to disc.

I've noticed, however, that ISOs made this way are still smaller than the original disk.  I just tried k9copy on a 5GB DVD movie, with the DVD size set to 8800 MB, selected all of the features, menu's, etc and ended up with an ISO of 3.9 GB, which make me think there's some sort of compression going on.  I'm wondering if there's some way of ensuring that there is no compression performed.

Any comments would be appreciated.

---

### Post by BLTicklemonster on 2008-02-07
My son got Mr Woodcock, and not only can't play it on his linux partition, but I tried to archive it, and nothing I throw at it works. They all nut up.

Anybody have any luck with this one? If the littlest one gets hold of this disk, I don't think the dvd player upstairs will be able to read through crayon and tooth marks. 

Just a guess, but that's what I think based on  prior experience.

---

### Post by wjston on 2008-02-07
> **John_T said:**
> I've made about a dozen  ISOs using K9copy so far, and must say that I've found it generally quite straightforward.

My aim is to create iso's of my kids DVDs to the hard disk, so that I can play them from my Ubuntu media center without searching for and loading disks.  I'm using VLC to play the ISO files, which works fine.  I've no desire at this point to burn to disc.

I've noticed, however, that ISOs made this way are still smaller than the original disk.  I just tried k9copy on a 5GB DVD movie, with the DVD size set to 8800 MB, selected all of the features, menu's, etc and ended up with an ISO of 3.9 GB, which make me think there's some sort of compression going on.  I'm wondering if there's some way of ensuring that there is no compression performed.

Any comments would be appreciated.

John_T
After setting the ISO file size to 8800, make sure you close  K9copy and then restart it. For some reason, the change does not take affect unless you restart.

---

### Post by yabbadabbadont on 2008-02-07
> **BLTicklemonster said:**
> My son got Mr Woodcock, and not only can't play it on his linux partition, but I tried to archive it, and nothing I throw at it works. They all nut up.

Anybody have any luck with this one? If the littlest one gets hold of this disk, I don't think the dvd player upstairs will be able to read through crayon and tooth marks. 

Just a guess, but that's what I think based on  prior experience.

DVDFabHDDecrypter  (I think I suggested it earlier)

It works under WINE and has not yet failed to backup a disc (for me).

---

### Post by John_T on 2008-02-07
> **wjston said:**
> John_T
After setting the ISO file size to 8800, make sure you close  K9copy and then restart it. For some reason, the change does not take affect unless you restart.
Thanks for that, but I've re-started it multiple times, and it still seems to be compressing for some reason.

I know this because I've copied discs greater than the origin 4400 MB limit. For example, I've backed up a 6 GB disc and had the result be around 5 GB (form memory, may not be exact). The DVD size was set to 8800 MB in this case, so I don't know why it felt it had to compress.

---

### Post by yabbadabbadont on 2008-02-07
> **John_T said:**
> Thanks for that, but I've re-started it multiple times, and it still seems to be compressing for some reason.

I know this because I've copied discs greater than the origin 4400 MB limit. For example, I've backed up a 6 GB disc and had the result be around 5 GB (form memory, may not be exact). The DVD size was set to 8800 MB in this case, so I don't know why it felt it had to compress.

If your kids don't notice the difference, don't worry about it.  :D

(OK, as geeks, it is required that we worry about it, as it is unexplained behavior...  :lol:)

---

### Post by BLTicklemonster on 2008-02-07
> **yabbadabbadont said:**
> DVDFabHDDecrypter  (I think I suggested it earlier)

It works under WINE and has not yet failed to backup a disc (for me).

Thanks, Yab, but too late. Mr Woodcock is a coaster now.

:guitar: <---- playing taps, you know...

We'll get it again some day and try it, but in the meantime, I installed the program, and have it saved on a shared drive.

---

### Post by nebu on 2008-02-08
> **eqisow said:**
> It seems that there is a wiki for running [DVD Shrink]("https://wiki.ubuntu.com/DVDShrink") in [Wine]("https://wiki.ubuntu.com/Wine"), but no wiki for the excellent Linux native replacement for DVD Shrink, K9Copy, so I decided to create one.

The new wiki page can be found [here]("https://wiki.ubuntu.com/K9Copy"). I will also make this the official discussion thread. :)

this is gr8..... thx!!!

---

### Post by John_T on 2008-02-09
> **yabbadabbadont said:**
> If your kids don't notice the difference, don't worry about it.  :D
The kids certainly don't notice at the moment. But they're 3 .8 and 1.6 YO at the moment, and we've only got a crappy  63 cm CRT TV connected on a composite output.   However, what happens when I get my 40-50" LCD connected on HDMI? It could be an underage rebellion!

:o

> **yabbadabbadont said:**
> (OK, as geeks, it is required that we worry about it, as it is unexplained behavior...  :lol:)

Not only that, my ripping to hard disk serves 2 purposes:
1. Start the movie within a few seconds without having to hunt for and load discs.
2. Backup, in case we one of the critters gets their grubby hands on an original and decides to use it as a frisbee!

Mostly because of #2, I'd like to get a non-compressed digital copy.  How do others manage this, can it be done with K9Copy?

---

### Post by yabbadabbadont on 2008-02-09
> **John_T said:**
> Mostly because of #2, I'd like to get a non-compressed digital copy.  How do others manage this, can it be done with K9Copy?

See my earlier post [here](http://ubuntuforums.org/showthread.php?p=4289708#post4289708).

;)

---

### Post by myke on 2008-02-17
OK.   I really like this program but am having one annoying problem that I can not figure out how to get solved.  I've seen the problem mentioned in a thread or two including over at the Kubuntu forums but no suggestions as to what to do to fix the issues ... which, btw, is:

I have a partitioned drive between Kubuntu and WinXP that is only 40gb total so it's split approximately half to both.  So, after all programs installed on each side, there's not a lot of room left.  As it's my laptop and I needed the space but still wanted portability, I bought a 160gb Western Digital Passport usb drive.   I have it formatted in NTFS and it mounts excellently under ntfs-3g.

I have my settings under k9copy for the output directory to default to a folder on the portable passport drive.  That is fine.  However, when I direct k9copy to burn the resulting iso anywhere on my portable drive, it gives the following error:

> remote files not accepted
you can only select local files

I barely have enough space left on either the winxp or kubuntu partitions of my main drive to save such a large iso but it will save to either including the ntfs winxp side.   So I know it's not having my portable usb drive formatted in ntfs.

So what gives?  Why does it call my portable drive "remote" like I'm trying to save it over a network or something?     All my other programs recognize the drive as just another drive hooked up to my system so why is k9copy blocking me from saving the final iso to my portable drive?   It won't even start the rip if I try to do so.

Is there any fix to this?   It really doesn't seem to make any sense at all why it's acting this way.  

help??

---

### Post by myke on 2008-02-17
OH ... and now yet another problem.   I can at least get k9copy to begin the ripping process as long as I send the iso save to the main hard drive but it crashes after just a few minutes in the process with a SIGSEGV error.    Someone on the Kubuntu boards suggested deleting the k9copy config file so that it'd recreate it from scratch which I did but it didn't help.

This program worked GREAT up until about a week ago and the only things that have happened to my system since then is a few upgrades thru the update manager. 

Seems like EVERY single time K/Ubuntu issues an update of some sort, it breaks something else.  And it gets worse with each version.  Gutsy has by far been the buggiest and most crash prone.   It actually rather sucks.   And I'm no K/Ubuntu basher.  I've used it faithfully since Breezy.   I'm simply tired of doing clean installs due to messes created by updates.

---

### Post by crypt0shite on 2008-02-25
Hi Myke,
I was having similar problems at the save dialog in k9copy after recent updates.  Did you try running k9copy from a command line as sudo?  This resolved the problem for me, but I am still working on the why of it.  Perhaps it has to do with the k9copy/kde files in /tmp.  Hope this helps.

---

### Post by johnnybirdman on 2008-03-19
I've been using k9 with good results for a while to create backups of dvd's as iso files.  I'm wondering now, how does one go about burning the ISO file to a dvd that will play in a DVD player?  k9 in combination with k3b worked fine when I was doing the burn right after the copy, but with saved dvd iso files I'm drawing a blank.  Any help?

Thanks,
J.

---

### Post by BLTicklemonster on 2008-03-19
When K3B comes up, click on burn DVD ISO image, then navigate to the file or drag and drop, and burn.

---

### Post by johnnybirdman on 2008-03-22
> **BLTicklemonster said:**
> When K3B comes up, click on burn DVD ISO image, then navigate to the file or drag and drop, and burn.

Thanks.  that is way to easy.  for some reason I figured I had to extract or otherwise manipulate the file first.
Brilliant.

J.

---

### Post by BLTicklemonster on 2008-03-23
No prob, and if you run into any problems, like I did with my birthday presents, fantastic 4 and rise of the silver surfer, dvdfab hd decrypter is a great tool. It does a full scale decrypt, then you run k9copy on it.

the things I have to go through to keep my store bought disks in pristine condition!

(run it in wine, btw)

---

### Post by mailforbiz on 2008-05-08
Hi

Maybe a basic question but I don't see how to reauthor a DVD ala DVDShrink or DVDDecryptor which allows me to include individual chapters etc. Am I missing something? When I choose the reauthor menuitem, it doesn't allow me to add individual chapters/sets.

Thanks in advance.

---

### Post by BLTicklemonster on 2008-05-08
I think qdvdauthor is what you are looking for. You're wanting to basically form the structure of the dvd yourself?

---

### Post by RSparker on 2008-05-12
Hi,

Does k9copy allow you to also compress the audio when you're mastering a DVD? (i.e. creating a full directory structure with chapter stops and menus ready to be burned into a DVD)

My objective is to reduce audio quality in order to maximize the video quality, and this particular DVD I want to compress doesn't have a 2.0 audio track. So want to do is to take the 5.1 audio track and reduce it to 2.0, is that even possible with k9copy?

---

### Post by BLTicklemonster on 2008-05-12
Some DVDs have several audio options. 5.1 as well as just plain stereo. If so, then yes, just uncheck the ones you don't want, and let 'er rip.

---

### Post by RSparker on 2008-05-12
> **BLTicklemonster said:**
> Some DVDs have several audio options. 5.1 as well as just plain stereo. If so, then yes, just uncheck the ones you don't want, and let 'er rip.

I understand that, but what about DVDs that *don't* have a 2.0 track? Is it possible to have K9copy take a 5.1 track and downmix it to 2 channels, similar to what a dvd player does?

---

### Post by BLTicklemonster on 2008-05-12
I don't know the full capabilities of k9copy, so I can't say for sure, but I don't think you can do that in it. I'm afraid you'd have to remaster it in avidemux and change the settings for the audio in there.

Hopefully someone will come along with a better answer?

Or perhaps kdenlive is the answer? I don't know much at all about it, but here's a wiki on it [http://en.wikibooks.org/wiki/Kdenlive](http://en.wikibooks.org/wiki/Kdenlive)

---

### Post by John_T on 2008-05-13
> **RSparker said:**
> I understand that, but what about DVDs that *don't* have a 2.0 track? Is it possible to have K9copy take a 5.1 track and downmix it to 2 channels, similar to what a dvd player does?

I don't think k9copy does that.

However, if your original disc only has a surround track (unusual, but certainly not out of the question), why not let k9copy do it's thing, and let the DVD player, beit hardware or software, figure out how to downmix it, which is the way it's supposed to happen.

Exactly what is required of DVD content producers varies from region to region, but I'm pretty sure the primary audio track has to be encoded for MPEG1 compatibility, which means the stereo channel information is always extractable by the player.

Of course, if you're trying to downmix prior to copying to save space, that sounds reasonable enough, but I'm afraid that I can't help out with a simple solution.

---

### Post by RSparker on 2008-05-13
I suspected k9copy didn't do the kind of downmixing I had in mind, but maybe I was missing something obvious.

I wanted to avoid going to more complex A/V editing packages since the whole point of k9copy is to make it simple to strip a DVD down to the essentials.

One would think that, since it compresses the video, it would also be handy to convert the audio to 2 channels. I'm assuming this would save quite a bit of space when compared to a full blown multichannel track.

> **John_T said:**
> However, if your original disc only has a surround track (unusual, but certainly not out of the question), why not let k9copy do it's thing, and let the DVD player, beit hardware or software, figure out how to downmix it, which is the way it's supposed to happen.
...
Of course, if you're trying to downmix prior to copying to save space, that sounds reasonable enough, but I'm afraid that I can't help out with a simple solution.

Yes, saving space would pretty much be the whole point here. Many of the DVDs I own, especially asian ones (for some reason), only offer multichannel audio tracks. If I know the movies are only going to be watched on a stereo capable setup it seems like such a waste to include a full blown 6.1 track at the expense of video quality.

Thanks for the clarifications.

---

### Post by BLTicklemonster on 2008-12-26
Bummer. I have a slew of dvds waiting to burn, but when I start the rip:

Unable to open file /media/sdc6/movie name/dvd/VIDEO_TS/VTS_05_1.VOB

I have permissions to that folder, by the way.

---

### Post by wordsmyth on 2010-12-24
Hi there:

K9copy working fine with Ubuntu 10.10/64 bit....but not working at all with 
Mint 10/64 bit - no application window appears and DVD in drive isn't opened. All codecs etc. installed, as with Ubuntu 10.10. No other problems with Mint applications. Anyone else having the same problem?

---

### Post by bogyman57 on 2012-12-11
Hi all - I hope this thread isn't dead...

I had K9Copy/VLC/K3b working perfectly on Ubuntu 11.10

BUT when I upgraded <?> to Ubuntu 12.04, K9Copy has a big problem.

I can rip a DVD to an 4400 MB .iso with it just fine (or so it seems)
(other than a new error: "No VTS_TMAPT Available - skipping")

1. VLC crashes when I try to play the .iso file.
(VLC : vm.c 1167 : play_Cell : assertion '0' failed)

2. I can burn the .iso to a DVD+R with K3B and it will play just fine on my stand-alone DVD player.

3. VLC crashes when I try to play that same DVD.

Anybody having the same problems????

---

### Post by mörgæs on 2012-12-11
The thread concerns old software and is not relevant today. Development is fast, and information for old releases might be misleading.

If you have problems with the latest version of a package, please open a new thread. Closing this one.

---

