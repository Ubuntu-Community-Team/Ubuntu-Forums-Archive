---
title: "repository problem"
date: 2005-10-15
forum: Repositories &amp; Backports
---

### Post by natman on 2005-10-15
hi i am kinda a newbie and have just got the badger and ran
sudo apt-get update

and i get the following

natman@centralcomputer:~$ sudo apt-get update
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports Release.gpg
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates Release
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports Release
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Sources
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found [IP: 193.1.193.69 80]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 19.8kB in 21s (919B/s)
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-amd64/Packages.gz)  404 Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  404 Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  404 Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 193.1.193.69 80]
Reading package lists... Done
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


So i think something is going wrong can anyone help?
In particular i have problems with kile dvi viewer
thanks

---

### Post by DJ_Max on 2005-10-15
There are no Breezy backports. Remove them from your sources.list.

---

### Post by natman on 2005-10-15
please can you tell me how i do that exactly?
i am really bad at this 
What is a backport , do i need them?

---

### Post by DJ_Max on 2005-10-15
Post your /etc/apt/sources.list. 

Backports are packages compiled from future versions of Ubuntu, and contain the latest software.

---

### Post by natman on 2005-10-15
here it is

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy universe main restricted
 deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by DJ_Max on 2005-10-15
You just want to comment the breezy URI's. You also won't need the CD anymore.
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src http://ie.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://ie.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ie.archive.ubuntu.com/ubuntu breezy universe main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://ie.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb-src http://ie.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe
```

---

### Post by natman on 2005-10-15
ok so all i have to do is replace 
deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy main restricted
with
deb-src "http://ie.archive.ubuntu.com/ubuntu breezy main restricted" all over the place.
Just one problem i opened the file by clicking folders and so forth, it wont let me write over the words in the file.

---

### Post by DJ_Max on 2005-10-15
You need proper privileges. BTW, it's not all over the place, there are just two lines that you can comment or remove.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by billiejoex on 2005-10-15
Here's the output of an apt-get update made on a brand new kubuntu installation. 
I decommented all the repositories listed in /etc/apt/sources.lst.
Could somebody tell me what's wrong?



root@linux:/home/billiejoex# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release.gpg
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found [IP: 82.211.81.167 80]
Fetched 191B in 0s (233B/s)
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 82.211.81.167 80]
Reading package lists... Done
W: GPG error: [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by natman on 2005-10-15
ok i typed in the command sudo gedit /etc/apt/sources..list and gave my password
and i got the following message

** (gedit:9821): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi)' failed

(gedit:9821): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BonoboMDI'

** (gedit:9821): CRITICAL **: bonobo_mdi_get_active_child: assertion `BONOBO_IS_MDI (mdi)' failed

(gedit:9821): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BonoboMDI'

** (gedit:9821): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:9821): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDOW (win)' failed

** (gedit:9821): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9821): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9821): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9821): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:9821): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(gedit:9821): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(gedit:9821): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

( i have full privaliges on the computer) , so it there something very much wrong with my computer?
or a silly mistake - sorry about the voloume questions

---

### Post by DJ_Max on 2005-10-15
Hrmm, looks like your gedit package is broken. For now do it in Synaptic.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

You will want to uncheck the backports

---

### Post by DJ_Max on 2005-10-15
Are you sure you commented them out?

[http://ubuntuforums.org/showpost.php?p=413676&postcount=10](http://ubuntuforums.org/showpost.php?p=413676&postcount=10)

---

### Post by Babets on 2005-10-21
[QUOTE=billiejoex]Here's the output of an apt-get update made on a brand new kubuntu installation. 
I decommented all the repositories listed in /etc/apt/sources.lst.
Could somebody tell me what's wrong?



root@linux:/home/billiejoex# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release.gpg
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found [IP: 82.211.81.167 80]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found [IP: 82.211.81.167 80]
Fetched 191B in 0s (233B/s)
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 82.211.81.167 80]
Reading package lists... Done
W: GPG error: [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/QUOTE]

I am italian and I have the same problem with one of my friends. Only decommenting the repos.:confused:

---

### Post by mesol on 2005-10-22
i tried many of sourcrs.list that everybody recommend to but i still get this message

connection timed out

why i get this message??
i already connected to the internet, the prove is, i got internet using firefox
and after altering or removing comment (#) in front of deb [http://.](http://.)... and deb src [http://.](http://.)..., i will get this message wheni enter synaptic package manager

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-extras/main Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-extras/universe Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-extras/multiverse Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-extras/restricted Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by aysiu on 2005-10-22
You're mixing Hoary and Breezy repositories? That doesn't sound good. Try this:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

