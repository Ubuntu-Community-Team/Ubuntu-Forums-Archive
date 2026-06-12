---
title: "Request: baegle 0.0.11"
date: 2005-06-16
forum: Ubuntu Backports
---

### Post by Majlo on 2005-06-16
Hi..

Beagle 0.0.11 is out.

Changelog  [http://ftp.gnome.org/pub/GNOME/sources/beagle/0.0/beagle-0.0.11.news](http://ftp.gnome.org/pub/GNOME/sources/beagle/0.0/beagle-0.0.11.news)

And package is in Breezy Repos [http://packages.ubuntu.com/breezy/gnome/beagle](http://packages.ubuntu.com/breezy/gnome/beagle)

---

### Post by dlpfmVfH on 2005-06-16
can you also make the new muine package...in the repositories it is 0.82 and 0.83 at the website...

---

### Post by Majlo on 2005-06-16
Yes also Muine 0.8.3 is in Breezy repos
Thanks

---

### Post by jdong on 2005-06-16
I'll grab both.

---

### Post by jdong on 2005-06-16
Both are built and uploaded... caught an upstream bug in the process, too :)

---

### Post by Majlo on 2005-06-16
Waw this is speed :-)
Thanks i go testing ;-)

---

### Post by dlpfmVfH on 2005-06-16
didn't work...

started beagled with debug and found :

> ioctl: Bad address

did a goolge and found out:

You are using the wrong version of Inotify.  Beagle 0.0.9 requires
Inotify 0.21 or better.

I'm using the new 2.6.11 kernel...

trying with noinotify...

just rebooted, and it works..!!! woopie beagle -fb -debug works

 [HTML]NFO: Starting Beagle Daemon (version 0.0.11.1)
DEBUG: Command Line: /usr/lib/beagle/BeagleDaemon.exe --fg --debug
DEBUG: Starting main loop
DEBUG: Starting messaging server
DEBUG: Starting QueryDriver
DEBUG: worker added: name=server 'socket' refcount=1
DEBUG: Found index helper at /usr/lib/beagle/beagled-index-helper
WARN: Could not open /dev/inotify
DEBUG: Starting FileSystemWatcher Backend
DEBUG: Pre-populated UniqueIdStore cache with 0 items in ,00s
INFO: Loaded 0 records from /home/aboe/.beagle/FileSystemIndex/FileAttributesStore.db in 0,000s
INFO: Loaded 0 records from /home/aboe/.beagle/LauncherIndex/FileAttributesStore.db in 0,000s
DEBUG: Found 11 types in BeagleDaemonLib, Version=1.4.3.3, Culture=neutral
INFO: Starting Evolution mail backend
INFO: FileSystemQueryable start-up thread finished
INFO: Starting launcher backend
INFO: Scanning Launchers
INFO: Starting Evolution mail backend
INFO: Starting Gaim log backend
DEBUG: Starting mail crawl

[/HTML]

---

### Post by jdong on 2005-06-16
As far as inotify, there's really nothing I can do about it... sorry.

---

### Post by dlpfmVfH on 2005-06-16
I know have to wait till 2.6.12 comes out...or 2.6.11 comes out universe...so it will be patched..correctly...

tested, muine it runs perfectly...thanks for the tray-icon...was missing that one...

Could you also look into the muine tagger??

[http://www.public.asu.edu/~bnickel/MuineTagger/](http://www.public.asu.edu/~bnickel/MuineTagger/)

with that plugin muine will rock!!

don't know enough do do it myself...checked,, taglib 1.31 but couldn't find it in the repositories..maybe under a different name...

thanks again..for the speed you are building packages...

Backports..are what makes ubuntu special for me..

---

### Post by Slo Mo Snail on 2005-06-17
uploaded for ppc

---

### Post by manicka on 2005-06-17
[QUOTE=jdong]Both are built and uploaded... caught an upstream bug in the process, too :)[/QUOTE]
where can I find this package? It doesn't seem to be on the mirrors yet

---

### Post by Majlo on 2005-06-17
[QUOTE=manicka]where can I find this package? It doesn't seem to be on the mirrors yet[/QUOTE]

Is in Staging .
Add this into /etc/apt/sources.list

[I]## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted[/I] 

Then

*sudo apt-get update*

---

### Post by manicka on 2005-06-17
[QUOTE=Majlo]Is in Staging .
Add this into /etc/apt/sources.list

[I]## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted[/I] 

Then

*sudo apt-get update*[/QUOTE]
 Thanks :)

What is the staging repo mainly used for?

---

### Post by Majlo on 2005-06-17
[QUOTE=manicka]Thanks :)

What is the staging repo mainly used for?[/QUOTE]

Staging repo is for testing. If is application stable then go to stable branche.

---

### Post by davidsf on 2005-06-17
Hi,

I have one issue with beagle 0.0.11.1 and Evoution backend:

WARN: Could not open Evolution addressbook.  Addressbook searching is disabled.
DEBUG: System.DllNotFoundException: libebook-1.2.so.0
in (wrapper managed-to-native) Evolution.Book:e_book_new_system_addressbook (intptr&)
in <0x00016> Evolution.Book:NewSystemAddressbook ()
in <0x00024> Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable:Start ()

Maybe a discordance with libevolution-cil and beagled ?

Thanks in advanced

---

### Post by Majlo on 2005-06-17
[QUOTE=davidsf]Hi,

I have one issue with beagle 0.0.11.1 and Evoution backend:

WARN: Could not open Evolution addressbook.  Addressbook searching is disabled.
DEBUG: System.DllNotFoundException: libebook-1.2.so.0
in (wrapper managed-to-native) Evolution.Book:e_book_new_system_addressbook (intptr&)
in <0x00016> Evolution.Book:NewSystemAddressbook ()
in <0x00024> Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable:Start ()

Maybe a discordance with libevolution-cil and beagled ?

Thanks in advanced[/QUOTE]

Hi

Try this .Wrote in console

*sudo ln -s /usr/lib/libebook-1.2.so /usr/lib/libebook-1.2.so.0*

---

### Post by jdong on 2005-06-17
It's a packaging bug. I'll go in and patch the name tonight.

---

### Post by manicka on 2005-06-17
File indexing is still very slow and purging each startup for me.... sigh

---

