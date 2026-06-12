---
title: "my recommended Dapper sources.list (dicussion)"
date: 2006-06-01
forum: Ubuntu Customization Guide
---

### Post by ubuntu_demon on 2006-06-01
This is the discussion thread for this sticky :

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

This is the source.list which I recommend for the average desktop user running Dapper. 
[B]
I'm posting this as a forum user and not as a staff member. First read the entire post before doing anything. Not all of these repositories are official. This is all on your own risk. Please be careful[/B]

The average desktop user has no ppc or amd64. So this sources.list isn't intended for those architectures. 

If you are still using breezy then you should **upgrade to Dapper first before using this sources.list**. You should take a look here prior to upgrading :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

That being said here it is :

Sometimes people also post their sources.list don't let that confuse you.

---

### Post by sudomania4 on 2006-06-01
Here is mine:
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## MAIN REPOSITORIES
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PROPOSED REPOSITORY
deb http://us.archive.ubuntu.com/ubuntu dapper-proposed main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free

## SEVEAS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://mirror.ubuntulinux.nl/ dapper-seveas all

# CIPHERFUNK REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## WINE REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://wine.budgetdedicated.com/apt dapper main

## OPERA REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://deb.opera.com/opera/ etch non-free

## XGL/COMPIZ REPOSITORIES (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

## DEBIAN REPOSITORIES (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb ftp://ftp.nerim.net/debian-marillat/ etch main
## deb ftp://ftp.nerim.net/debian-marillat/ sid main
## deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```

What is the "proposed" repository? When do we get Dapper-Backports? Can i use the country code "us" for backports? When will we get a Dapper PLF repo?

---

### Post by MetalMusicAddict on 2006-06-01
2 questions U-G. What do you use the "Cipherfunk" repo for and Does your list open up all the Ubuntu repos? Ive used Synaptic to add the universe and multiverse lines before and got errors. I guess I added them to repos that didnt have 'em?

---

### Post by sudomania4 on 2006-06-01
the cipherphunk is a multimedia repo (i think). i have all the official dapper repos...

---

### Post by ubuntu_demon on 2006-06-01
[QUOTE=sudomania4]
What is the "proposed" repository? 
[/QUOTE]

**edit :**
[http://ubuntuforums.org/showpost.php?p=1138989&postcount=17](http://ubuntuforums.org/showpost.php?p=1138989&postcount=17)

[QUOTE=sudomania4]
When do we get Dapper-Backports? 
[/QUOTE]

A while after the first packages enter edgy. Probably at least a month from now. Go to the backports forum if you want a better answer since I'm not part of the backport team.

[QUOTE=sudomania4]
Can i use the country code "us" for backports? 
[/QUOTE]

Yes.

[QUOTE=sudomania4]
When will we get a Dapper PLF repo?[/QUOTE]

I hope soon. I have no idea. If you really need PLF packages you can include the breezy PLF repo **on your own risk**. I have uncommented this repository on my own installation without problems.

---

### Post by frodon on 2006-06-01
I saw in the ubuntu fr forum that some users has used the breezy PLF repository with dapper without any problems. However the dapper PLF repository is coming soon, it's a matter of weeks now.

---

### Post by ubuntu_demon on 2006-06-01
[QUOTE=MetalMusicAddict]2 questions U-G. 
[/QUOTE]

I'm ubuntu_demon. Don't confuse me with ubuntu-geek who started this forum and is our leader :).

[QUOTE=MetalMusicAddict]
What do you use the "Cipherfunk" repo for 
[/QUOTE]

It has some multimedia packages. You can point your browser here to see which ones :
[ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-i386/Packages](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-i386/Packages)

currently it has :
gstreamer0.10-pitfdll
w32codecs
libdvdcss2-dev
libdvdcss2

[QUOTE=MetalMusicAddict]
and Does your list open up all the Ubuntu repos? Ive used Synaptic to add the universe and multiverse lines before and got errors. I guess I added them to repos that didnt have 'em?[/QUOTE]

AFAIK all official Ubuntu repos are opened by my sources.list.

---

### Post by MetalMusicAddict on 2006-06-01
[QUOTE=ubuntu_demon]I'm ubuntu_demon. Don't confuse me with ubuntu-geek who started this forum and is our leader :).[/QUOTE]
Yea I noticed after I sent it but didnt change since I had to go to work. Thanx for the info. ;)

---

### Post by ubuntu_demon on 2006-06-01
[QUOTE=MetalMusicAddict]Yea I noticed after I sent it but didnt change since I had to go to work. Thanx for the info. ;)[/QUOTE]
np :p

---

### Post by CHUCKYCHUCK on 2006-06-04
the plf dapper repository is available !!

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=CHUCKYCHUCK]the plf dapper repository is available !![/QUOTE]
thnx!

---

### Post by ozzie123 on 2006-06-06
What is actually PLF repository?

---

### Post by ejm on 2006-06-06
[QUOTE=ozzie123]What is actually PLF repository?[/QUOTE]

See [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by CHUCKYCHUCK on 2006-06-06
briefly, the plf ( penguin liberation front ), is a repository for packages that cannot be included in "regular" repositories because of legal issues ( ex :  tools to decrypt dvds )

---

### Post by ozzie123 on 2006-06-07
Ok guys, thanks alot for the info ;-)

---

### Post by lukew on 2006-06-08
Hi,

I know this is slightly off topic, in fact i have posted another thread asking thr same question, but there does not appear to be any takers.

The key on the plf repo I have added using apt and gpg, both of whcih appear to be ok, untill I go to install w32codecs and then it informs me that the package can not be validated. 

My question is, do you know the keys fpr the plf?

---

### Post by ubuntu_demon on 2006-06-14
Issue 2 of the Ubuntu Weekly Newsletter explains the dapper-proposed repository.

from [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue2](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue2) :

> 
Proposed Archives

A new set of package archives has been added to archive.ubuntu.com to allow proposed updates and fixes to be uploaded and tested (by those with the archive enabled) before the packages are officially released. This process will allow for the proposed updates to see wider testing helping improve the quality of the updates. Every release in the archive now has a -proposed directory which looks like:

    *

      edgy-proposed
    *

      dapper-proposed
    *

      etc...

Although these do not contain any packages at the moment, if you help test Ubuntu, you will want to keep an eye on these.


---

### Post by ubuntu_demon on 2006-06-21
I just learned that dapper-proposed probably won't be used at all. It's probably some some miscommunication issue.

---

### Post by tr333 on 2006-06-30
[quote=ubuntu_demon]Then do this command to take the new sources.list into effect do the following command in the terminal (without the $) :
```
$sudo apt-get update ; sudo apt-get upgrade
```[/quote]
this command should be replaced with:
```
sudo apt-get update && sudo apt-get upgrade
```
if the 'apt-get update' command fails, then the 'apt-get upgrade' command won't be run.

---

### Post by ubuntu_demon on 2006-06-30
[QUOTE=tr333]this command should be replaced with:
```
sudo apt-get update && sudo apt-get upgrade
```
if the 'apt-get update' command fails, then the 'apt-get upgrade' command won't be run.[/QUOTE]

apt-get update probably won't fail and if it fails it probably won't hurt to run apt-get upgrade but your solution is more clean. I'm going to change it. Thnx!

---

### Post by ubuntu_demon on 2006-07-09
I added the canonical commercial repository :

```

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

This repository makes a seperate opera repository obsolete.

I know gnome-app-install doesn't need the entry in the sources.list in order to install from it. But I think it's more clean and in this way you can also use the apt commandline tools.

Here's a bit more information :
[http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository](http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository)
[http://www.opera.com/pressreleases/en/2006/07/06/02](http://www.opera.com/pressreleases/en/2006/07/06/02)

Here's a listing of the packages :
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz)

I posted on my blog about this new dapper-commercial repository :
[http://ubuntudemon.wordpress.com/2006/07/09/dapper-commercial-repository/](http://ubuntudemon.wordpress.com/2006/07/09/dapper-commercial-repository/)

---

### Post by mojoman on 2006-08-05
I'm thinking about using ubuntu_demon's recommended dapper sourcelist. However it is recommended for desktops and I'm using Xubuntu 6.06 on a laptop.

Does anyone know if there is any need to use other repositories for laptops, and if so, what repositories should be used?

Best regards
/Mojoman

---

### Post by ubuntu_demon on 2006-08-06
> **mojoman said:**
> I'm thinking about using ubuntu_demon's recommended dapper sourcelist. However it is recommended for desktops and I'm using Xubuntu 6.06 on a laptop.

Does anyone know if there is any need to use other repositories for laptops, and if so, what repositories should be used?

Best regards
/Mojoman
You can use this sources.list. It's not intended for servers.

---

### Post by ubuntu_demon on 2006-08-06
> **ubuntu_demon said:**
> I just learned that dapper-proposed probably won't be used at all. It's probably some some miscommunication issue.
dapper-proposed is being used for testing. The last openoffice update first entered dapper-proposed. A couple of days later it entered dapper-updates. In practice this repository isn't very useful for most average users.

---

### Post by mojoman on 2006-08-06
> **ubuntu_demon said:**
> You can use this sources.list. It's not intended for servers.

Excellent! :D  I'm gonna update my sources.list and follow your multimedia HOWTO  and see if I can get my freaking video playback to work, expecially the Kernel update to linux-686 (My trident-card has been giving me grey hair, and hopefully this will do some good). Thanks! 
/Mojoman

---

### Post by ubuntu_demon on 2006-08-06
> **mojoman said:**
> Excellent! :D  I'm gonna update my sources.list and follow your multimedia HOWTO  and see if I can get my freaking video playback to work, expecially the Kernel update to linux-686 (My trident-card has been giving me grey hair, and hopefully this will do some good). Thanks! 
/Mojoman
good luck!

---

### Post by rubenturner on 2006-08-22
Paul Drain's (Cipherfunk.org) ubuntu repository is offline.
[http://64.71.152.24/]("http://64.71.152.24/")

Thanks for dozens of debs.

---

### Post by ubuntu_demon on 2006-08-23
> **rubenturner said:**
> Paul Drain's (Cipherfunk.org) ubuntu repository is offline.
[http://64.71.152.24/]("http://64.71.152.24/")

Thanks for dozens of debs.
:(

Thanks for the information.

---

### Post by dhuff on 2006-10-17
So with cipherfunk.org out of action, what's the suggested alternative for a sources.list entry ? :???:

---

### Post by ubuntu_demon on 2006-10-18
> **dhuff said:**
> So with cipherfunk.org out of action, what's the suggested alternative for a sources.list entry ? :???:
PLF is a bit more active again. But for now I recommend following my instructions in Customization Guide Quick Start to install w32codecs and dvd-support.

---

### Post by Peter The Plumber on 2006-11-23
[QUOTE=ubuntu_demon;1076241]This is the discussion thread for this sticky :

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

This is the source.list which I recommend for the average desktop user running Dapper. 
[B]
I'm posting this as a forum user and not as a staff member. First read the entire post before doing anything. Not all of these repositories are official. This is all on your own risk. Please be careful[/B]


  Thank you very much for taking the time to post this and the others in the beginners section. I installed a complete setup in one sitting carefully following your directions!!

---

### Post by flapane on 2006-12-30
I finally reached a COMPLETE source list with EVERY program that has ever been packaged:
```

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

#edgy eft
deb http://fr.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb http://fr.archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://fr.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://fr.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu edgy-commercial main

# kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest edgy main
deb http://kubuntu.org/packages/amarok-144 edgy main

#beryl
deb http://www.beerorkid.com/compiz edgy main-edgy-amd64
#deb http://media.blutkind.org/xgl/ edgy main-edgy-amd64
#deb http://ubuntu.compiz.net/ edgy main-edgy
#deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy main-edgy-amd64
deb http://ubuntu.beryl-project.org/ edgy main
#deb http://ubuntu2.beryl-project.org/ edgy main
#deb http://ubuntu2.lupine.me.uk/ edgy main
#deb http://beryl-mirror.lupine.me.uk edgy all
#deb-src http://beryl-mirror.lupine.me.uk edgy all
#svn64bit#deb http://repo.imindgames.net:8080 binary/

# milone nvidia
deb http://albertomilone.com/drivers/edgy/nonlegacy/64bit binary/

# Janvitus Amd64 Repository
#deb http://www.janvitus.netsons.org/ubuntu/ edgy-janvitus all
deb http://janvitus.interfree.it/ubuntu/ edgy-janvitus main-amd64

# Seveas’ packages (GPG key: 1135D466)
deb http://mirror.ubuntulinux.nl edgy-seveas all

# superm1’s repository (mythtv and other nonfree) (GPG: 80DF6D58)
deb http://home.eng.iastate.edu/~superm1 edgy all

# Cafuego’s edgy Stuff: Broadcom firmware, google-earth, beagle (GPG key: 969F3F57)…
deb http://au.ubuntu.cafuego.net edgy-cafuego all bcm43xx

# Automatix (GPG key: 521A9C7C)
deb http://www.getautomatix.com/apt edgy main

# Ubuntu System Administrator packages
# mirror: http://ubuntu.moshen.de
deb http://ubuntu.systemadministrator.org edgy all

#amule
deb http://amule-adunanza.marleylandia.com/ubuntu/ramko-sonne/3.11b/edgy amd64/

##### PLF #####
##(Please report any bug on https://launchpad.net/products/plf/+bugs)
#deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
#deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free

#giochi
deb http://www.zonagames.it/ubuntu64/binary/ edgy main

#alltray e altri
deb http://asher256-repository.tuxfamily.org/edgy_amd64_beta ./

```

---

