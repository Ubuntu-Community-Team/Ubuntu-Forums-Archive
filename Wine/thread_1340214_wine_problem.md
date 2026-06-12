---
title: "wine problem"
date: 2009-11-28
forum: Wine
---

### Post by saadlulu on 2009-11-28
hey guys,

i had wine installed but then i removed it, after that i tried installing it again but this keeps showing :
boza@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

what should i do now ?

---

### Post by Gone fishing on 2009-11-28
You need to fix the broken packages.

Try Synaptic > Edit > fix Broken packages

---

### Post by DougieFresh4U on 2009-11-28
Well let's try from terminal:
```
sudo apt-get -f install
sudo dpkg --configure -a
```
You could also check Synaptic and make sure it's completely uninstalled.

---

### Post by saadlulu on 2009-11-28
no its still not working guys 
i think the dependeces it winning about is the things i installed from 
[http://www.ocforums.com/showthread.php?t=605456](http://www.ocforums.com/showthread.php?t=605456)
and i actually think that me installing this was a bad idea after all 
i typed this in the terminal 
sh winetricks vcrun6 allfonts allcodecs dotnet11 dotnet20 directx9 comctl32 comctl32.ocx fontfix mfc40 mfc42 msls31 ole2 pdh urlmon wininet native_mdac

---

### Post by saadlulu on 2009-11-28
any help anyone ?

---

### Post by andrea000 on 2009-11-29
I don't think installing something from winetricks
is what is stoping you from installing wine again.
Go to synaptic and do a complete remove wine.
Then go to the terminal and do a update
> sudo apt-get update 
now while your still in the terminal type
> gksu nautilus
enter your password from here on be very very
careful as you now have root privilege and you can
do some real damage to ubuntu.Now go to filesystem
on the left side of your screen and home in the main
part of the window and now your user name do a ctrl h
to show hidden files,Now find the wine folder and right
click it and delete it.Same if you have a winetricks
folder and you don't need winetricks.Exit all that and
go and try to install wine again with synaptic or install
it in the terminal
> sudo apt-get install wine

---

### Post by zami on 2009-11-29
I just had this problem myself and found your post while looking for a fix.

I did the "Fix Broken Packages" through Synaptic, and it actually said broken packages were fixed, but when I tried installing Wine again, I still had the exact same error.

I'm using Ubuntu 9.10, and was getting the error when installing as per these instructions -
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
using their "ppa:ubuntu-wine/ppa" APT line (for 9.10).

To fix it, I removed the "ppa:..." APT line from Software Sources, and went with the longer "deb" entry, listed for Jaunty.  Then Wine installed lickety split, no problem!

So.... it might be worth a shot.  Only time (and people considerably more knowledgeable than me!) can say if it will screw anything up down the road, but, feh, it works for now!

Good luck!  

-zami

---

### Post by saadlulu on 2009-11-29
Andrea thanks for the post, but it didnt really work :(

i did what Zami did and it worked :) 
but here is a thing am not sure about, when i removed the APT i had for ubuntu 9.10 "ppa:ubuntu-wine/ppa" and i tried installing wine then with no APT key i got this :

boza@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  winbind wine-gecko
The following NEW packages will be installed:
  winbind wine wine-gecko
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
_**Need to get 5,744kB/17.7MB of archives.**_
_**After this operation, 73.7MB of additional disk space will be used.**_
Do you want to continue [Y/n]? n
Abort.

and when i added the APT key for 9.04, i got this :
boza@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libopenal1 winbind wine-gecko
The following NEW packages will be installed:
  libopenal1 winbind wine wine-gecko
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
_**Need to get 17.3MB/21.7MB of archives.**_
_**After this operation, 99.3MB of additional disk space will be used.**_
Do you want to continue [Y/n]? n
Abort.

why is there a change in space ? which one should i go with ?

---

### Post by alex.rayu on 2009-11-29
Hey when that happens it means that youhave installed previously some package that will conflict with the one you are tying to install. Linux has no DLL hell - but here is your price. Try this: Download the .deb manually and try installing it. See the error messages it gives - it should say either that there is some library missing, or some alternative library is installed.

---

### Post by sparky-trev on 2009-12-09
I had the same problem on my new (to Me) IBM Intel machine Karmic 9.10, after reading a few things
I did the following in the terminal as you can see I am no expert the terminal scares me!

trevor@trevor-desktop:~$ sudo winecfg
sudo: winecfg: command not found
trevor@trevor-desktop:~$ winecfg
The program 'winecfg' can be found in the following packages:
 * wine
 * wine1.2
Try: sudo apt-get install <selected package>
winecfg: command not found
trevor@trevor-desktop:~$ sudo apt-get install wine
[sudo] password for trevor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
trevor@trevor-desktop:~$ sudo apt-get install wine1.2


And away it went............
So I had to install both wine and wine1.2 (sudo apt-get install)
all working now.Cheers......... Trev

---

### Post by black28 on 2009-12-10
wow this fixed it for me too! i just made a thread asking about it. thanks! sorry for the thread. i don't know if its the forum or my ubuntu desktop but its not showing recent threads. most recent says 12 hours ago...?

---

### Post by Soulcage on 2009-12-10
On karmic your supposed to install wine1.2 not wine, also add ppa:ubuntu-wine/ppa to software sources if you haven't already.

---

### Post by joshzam on 2009-12-11
I had the same problem. I tried and tried to install wine after adding the PPA to Software Sources but kept getting dependency conflicts. Only now did I actually try to read the descriptions of the packages in Synaptic. This is what is says next to the wine package:
> This package is to ease upgrades for users of the Wine Team PPA to help them test the latest Wine packages. It can be safely removed.
I finally tried to install wine1.2 instead of plan wine and it all worked fine. Looks like it pays to actually read.

---

### Post by jmcgovern on 2009-12-12
I have Wine1.2 installed properly now, but 1.2 is multiple revisions behind current ( i think it might even be pre-Jaunty).  Whats the easiest way to get later versions?  Wine 1.2 has major sound issues, especially with WoW.

---

### Post by Soulcage on 2009-12-12
If you want the newest ver of wine on karmic follow the instructions @ [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

---

### Post by joshzam on 2009-12-14
> **Soulcage said:**
> If you want the newest ver of wine on karmic follow the instructions @ [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

That page recommends installing wine (and not wine1.2) in Karmic so it will not work with 9.10.

Installing wine1.2 via Synaptic will give you the latest version, which is currently 1.1.34.

---

### Post by r2rX on 2009-12-24
This is thoroughly annoying.....

Using the ppa for Ubuntu 9.10 didn't work...so I used the Jaunty method...which found and installed wine just fine.....but the ttf-mscorefonts-installer dependency does not install (it times out trying to connect to every server it finds),

Now, I installed the ttf-mscorefonts with another method, and they are installed. But the wine installer doesn't recognize that.

So during the installation of wine, everything except the ttf-mscorefonts-installer installs.

When I click on Applications, I see wine. But anytime I try to run any (3D accelerated) games, it just show the loading icon of the mouse....and then nothing happens.

Any ideas?

r2rX  :)

---

### Post by zami on 2009-12-24
Wine Versions clarification -

The Synaptic Package Manager has two Wine packages available, "wine" and "wine1.2".  Those names do NOT reflect the versions of Wine they will install.

When following the instructions to get the latest version of Wine direct from WineHQ 
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
[B]know this:

The ppa line for Karmic(Ubuntu 9.10) updates the Synaptic package "wine1.2".

The older deb lines update the Synaptic package "wine".[/B]



So, if you are running Karmic(Ubuntu 9.10), use the ppa line (just like the instructions say to), then go into Synaptic Package manager, uninstall the package "wine" and install the package "wine1.2".

OR, if the ppa craps out on you, use the deb line for Jaunty, then uninstall the package "wine1.2" and install the package "wine".

----------

If anyone is curious I actually tested all the combinations on my machine running Karmic (while trying to get Plants vs Zombies going for my seven year old son, with my husband asking "why not just boot into Windows?".  Aaah, good times).

In Karmic:

Synaptic package "wine" + no repo alters = 1.0.1
Synaptic package "wine" + Karmic ppa = 1.0.1
Synaptic package "wine" + Older deb line = 1.1.35

Synaptic package "wine1.2" + no repo alters = 1.1.31
Synaptic package "wine1.2" + Karmic ppa = 1.1.35
Synaptic package "wine1.2" + Older deb line = 1.1.31

-zami

---

### Post by zami on 2009-12-24
> **joshzam said:**
> I had the same problem. I tried and tried to install wine after adding the PPA to Software Sources but kept getting dependency conflicts. Only now did I actually try to read the descriptions of the packages in Synaptic. This is what is says next to the wine package:

I finally tried to install wine1.2 instead of plan wine and it all worked fine. Looks like it pays to actually read.

Just TODAY my Synaptic started giving the package "wine" that description, and it's even labeled as "dummy package".  But you posted that your system was saying this a week ago - wierd!  Umm... I guess it's been a while since I updated huh? 

hmmm... allright, that changes my previous post, though it was all still true on my system not 40 minutes ago.

-zami

edit: okay I feel a bit better, "wine" isn't labeled as a "dummy package" until you successfully add the Karmic ppa.  PHWEW!  I thought I'd either gone blind, or hadn't updated in so long it was bordering on negligence!

-zami

---

