---
title: "Request: Mobile Phone Applications (Nokia 6230): gnokii, gnocky, wammu, gammu"
date: 2005-06-12
forum: Ubuntu Backports
---

### Post by amilist on 2005-06-12
Hi!
Any of those mentioned above would be highly appreciated  \\:D/  as none of them works on  hoary.  ](*,) 

Cheers!

---

### Post by cRoMo on 2005-06-12
Every single one of these will WORK in Hoary, just as on any other Linux distribution. Your problem is that there are no proper packages in Hoary repositories, but it's not a big problem if you really need those apps - just compile them by yourself or find a deb for other distro, Most likely it won't hurt your hoary.

---

### Post by paretooptimum on 2005-06-13
Has anyone found a .deb for gnocky? I've searched and all I can find are .rpms - I want to look some more for a deb before I use alien.

[http://www.gnokii.org/screenshots.shtml](http://www.gnokii.org/screenshots.shtml)

I have a nokia phone and this thing looks great.

Alternatively if you are a MOTU please? please? please!

---

### Post by amilist on 2005-06-13
1. to install gnokii add these lines to your sources.list:

deb [http://debian.usefulinc.com/gnome](http://debian.usefulinc.com/gnome) ./
deb-src [http://debian.usefulinc.com/gnome](http://debian.usefulinc.com/gnome) ./

2. the makefile for gnocky is properly generated on my system, nevertheless is does not compile. unfortunately i could not find any debs.

if i will be able to install gammu/wammu i will leave a message.

UPDATE: 

I installed first gnokii from the above url, then downloaded the gnocky-rpm from this url:

[http://rpm.pbone.net/index.php3/stat/4/idpl/1653834/com/gnocky-0.0.3-2.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1653834/com/gnocky-0.0.3-2.i386.rpm.html)

then I changed into the download-directory and executed the following commands in a terminal:

me@notebook:~$ sudo alien gnocky-0.0.3-2.i386.rpm

and 

me@notebook:~$ sudo dpgk -i gnocky_0.0.3-3_i386.deb

(you can skip this command by adding the "install-option to the alien-command "...alien -i gnocky....")

And IT WORKS  :)  :)  :)

---

### Post by rockrhino27 on 2005-10-29
Hello, 

     Does anybody know if any of the programs mentioned work on 3rd party USB cables.  I hve a nokia 6800 and a 3220 which both are compatiable with the Nokia DKU-5 cable.  When I originally bought the 6800, about a year and a half ago.  I also bought a 3rd party USB cable.  I can get the phone to sync with a windows program called "Oxygen Phone Manager".  It would be nice to find a linux program to do the same thing.

---

### Post by rockrhino27 on 2005-10-29
Hello, 

     Does anybody know if any of the programs mentioned work on 3rd party USB cables.  I hve a nokia 6800 and a 3220 which both are compatiable with the Nokia DKU-5 cable.  When I originally bought the 6800, about a year and a half ago.  I also bought a 3rd party USB cable.  I can get the phone to sync with a windows program called "Oxygen Phone Manager".  It would be nice to find a linux program to do the same thing.

---

### Post by Nightwind on 2005-12-25
[QUOTE=rockrhino27]Hello, 

     Does anybody know if any of the programs mentioned work on 3rd party USB cables.  I hve a nokia 6800 and a 3220 which both are compatiable with the Nokia DKU-5 cable.  When I originally bought the 6800, about a year and a half ago.  I also bought a 3rd party USB cable.  I can get the phone to sync with a windows program called "Oxygen Phone Manager".  It would be nice to find a linux program to do the same thing.[/QUOTE]
Yes they do

---

### Post by rockrhino27 on 2006-01-13
That is awesome News NightWind!!  :D 

Which model Nokia and what program are you using?  I'll attempt to get my nokia 3220 working with breezy tonight or tomorrow.

---

### Post by chele on 2006-04-14
gnokki & xgnokkii are now available in Ubuntu Dapper. I have not found a deb of gnocky yet. I am using a Nokia 3600 with a bluetooth connection. It was necessary to manually create a .gnokiirc file, then install and run gnapplet on the phone, before xgnokii would connect.

However, xgnokki used a ton of memory and time to import the contacts from the phone to the PC.   ```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
10067 chele     16   0  339m  93m 4076 S  0.0 37.6   0:07.51 xgnokii
```

---

### Post by BoredByPolitics on 2006-09-18
Easy installation of gammu/gammu-python/wammu can be achieved by using the script on this page: [Wammu Installation Script for Ubuntu]("http://www.gammu.org/wiki/index.php?title=Wammu:Installation_Script_for_Ubuntu#Code")

Once you've pasted it into a file, you'll probably have to execute it using sudo:

```
sudo sh ./install_wammu.sh
```

At first I didn't think the filesystem functions of gammu would work with my phone, but it turns out that I was using the wrong connection settings:

```
[gammu]
port = /dev/ttyACM0
model = 3220
connection = dku5
```

You may also be interested in [snofs]("http://snofs.sourceforge.net/").  There's no package to download, but you can grab the cvs code, and once compiled it runs fine:

```
sudo apt-get install cvs
cvs -d:pserver:anonymous@snofs.cvs.sourceforge.net:/cvsroot/snofs login
cvs -z3 -d:pserver:anonymous@snofs.cvs.sourceforge.net:/cvsroot/snofs co -P snofs
cd ./snofs/src
make
sudo cp snofs /usr/local/bin
sudo mkdir /mnt/nokia3220
sudo modprobe coda
sudo snofs &
sudo mount -tcoda /dev/cfs0 /mnt/nokia3220
```

Example usage:

```
pete@pete-laptop:~$ ls /mnt/nokia3220/
[COLOR="Blue"]files  mms  sms  status  vcards[/COLOR]
pete@pete-laptop:~$ ls /mnt/nokia3220/files
[COLOR="Blue"]A (Permanent_memory 2)  C (Permanent_memory)[/COLOR]
pete@pete-laptop:~$ ls /mnt/nokia3220/files/A\ \(Permanent_memory\ 2\)
[COLOR="Blue"]FIM_fixed_id  HTTP                   predeffilerecieved  predefhiddenfolder  predefmessages  predefsyncml
FIM_perm_id   predeffiledownload  predefgallery       predefinfofolder    predefomadm     serviceapplication[/COLOR]
```

Have fun!

Pete

---

