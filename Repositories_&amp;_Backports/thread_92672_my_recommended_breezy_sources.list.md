---
title: "my recommended breezy sources.list"
date: 2005-11-20
forum: Repositories &amp; Backports
---

### Post by ubuntu_demon on 2005-11-20
hi,

This is the source.list which I recommend for the average desktop user running breezy. I'm advising this as a forum user and not as a staff member.

The average desktop user has no ppc or amd64. So this sources.list isn't intended for those architectures. For people who have amd64 see this post : [http://www.ubuntuforums.org/showpost.php?p=631776&postcount=65](http://www.ubuntuforums.org/showpost.php?p=631776&postcount=65)

It can't hurt to include the src repos in case you might need them later. If you are on a slow internet connection I would advise to remove them.

If you need BOINC for SETI @ Home please search the forums.

Not all of these repositories are official. Also using this sources.list is your own risk. That being said here it is :

```

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# If you get errors about missing keys follow these command's :
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
#
# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf mirror. use if primary repo is offline
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos ONLY if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## official wine apt repository
##deb http://wine.budgetdedicated.com/apt breezy main
##deb-src http://wine.budgetdedicated.com/apt breezy main


## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

## skype
## deb http://download.skype.com/linux/repos/debian/ stable non-free


```

To use this sources.list replace your sources.list with this one using your favorite editor do the following command in the terminal (without the $):
```
$sudo gedit /etc/apt/sources.list
```

Then do this command to take the new sources.list into effect do the following command in the terminal (without the $) :
```
$sudo apt-get update ; sudo apt-get upgrade
```

When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)
```

      gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

```

In the end users can and should make their own informed decision about what they put in their sources.list. Here are some links to get you started :

information about codecs :
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) (to install w32codecs just do : sudo apt-get install w32codecs)

Information about plf :
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

Information about backports :
[http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

You can also generate a sources.list here :
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

If you want to upgrade to breezy first read these :
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

which sources.list do you use for your breezy desktop ?
[http://www.ubuntuforums.org/showthread.php?t=113361](http://www.ubuntuforums.org/showthread.php?t=113361)

information about how to install software in Ubuntu :
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.beginningubuntu.com/software_1.html](http://www.beginningubuntu.com/software_1.html)
[http://doc.gwos.org/index.php/ProgramInstallBeginners](http://doc.gwos.org/index.php/ProgramInstallBeginners)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

Information about apt-get :
[http://www.ubuntuforums.org/showthread.php?t=103462](http://www.ubuntuforums.org/showthread.php?t=103462)

Information about commandline packagemanagement :
[https://wiki.ubuntu.com/CommandLinePackageManagement](https://wiki.ubuntu.com/CommandLinePackageManagement)

You can **discuss my sources.list** here :
[http://www.ubuntuforums.org/showthread.php?t=87946](http://www.ubuntuforums.org/showthread.php?t=87946)

**edit :**
unstickied. I'm not running breezy anymore as well as most Ubuntu users. IMHO you should upgrade to Dapper if you want to use a sources.list recommended by me.

[B]my recommended Dapper sources.list
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)[/B]

---

