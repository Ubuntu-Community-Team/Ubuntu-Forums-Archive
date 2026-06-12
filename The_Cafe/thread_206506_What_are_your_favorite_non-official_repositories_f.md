---
title: "What are your favorite non-official repositories for Dapper?"
date: 2006-06-30
forum: The Cafe
---

### Post by ubuntu_demon on 2006-06-30
**I'm posting this as a forum user and not as a staff member. These repositories are not official. I just want to know whether they are used. This is not a recommendation**

Hi,

Please select which non-official repositories you use. Multiple selections are possible.

You can find more information about the repositories **I recommend** right here :
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

If you want to create your sources.list yourself you can go here :
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Here's a tiny bit explanation about the repositories from the poll :

*Cipherfunk multimedia packages*
This repository contains popular multimedia packages, such as w32codecs

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

*Penguin Liberation Front*
The Penguin Liberation Front is a team that builds litigious packages (patents covered or copyrighted stuff). For more info, visit: wiki.ubuntu-fr.org/doc/plf and [http://plf.zarb.org/](http://plf.zarb.org/)

# Penguin Liberation Front (packages)
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

*Bleeding edge wine packages*
This repository always contains the last version of the popular WINE program which is used to run MS Windows applications on a Linux platform

# Bleeding edge wine packages (packages)
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

*Skype*
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

*The Opera browser*
Opera provides their own packages here
# The Opera browser (packages)
# deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

*kubuntu.org packages for the latest KDE version*
# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
#deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

*kubuntu.org packages for the latest Koffice version*
# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
#deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

*kubuntu.org packages for the latest amaroK version*
# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
# deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

*Seveas' packages*
This is a 3rd party repository with several useful packages and backports. To find .deb lines for individual sections, go to wiki.ubuntu.com/SeveasPackages. Use with care and consider the individual sections over this one. You are advised to subscribe to the archive mailinglist mailto:packages-subscribe@ubuntu-nl.org where notices will be sent.

# Seveas' packages (packages, GPG key: 1135D466)
# deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas all

*Bazaar-NG development*
This repository contains development snapshots of the Bazaar-NG revision control system

# Bazaar-NG development (packages, GPG key: 1F44842D)
# deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

**edit :**
What kind of people use kde-latest ? How much breakage is involved ? If you use kde-latest please tell us about it.

There was no room for other repositories :(. If you use **other** repositories just mention them inside the thread. Please explain also **why** you use them.

The opera repository has become obsolete. See this post :
[http://www.ubuntuforums.org/showpost.php?p=1231795&postcount=30](http://www.ubuntuforums.org/showpost.php?p=1231795&postcount=30)

---

### Post by Engnome on 2006-06-30
I voted for the Opera repo's even though I always download their .deb and then double click. it, it's even easier than in windows :D It's good that they have a repository though, so that you get notified about updates.

---

### Post by ace2005 on 2006-06-30
[QUOTE=Engnome]I voted for the Opera repo's even though I always download their .deb and then double click. it, it's even easier than in windows :D It's good that they have a repository though, so that you get notified about updates.[/QUOTE]

But i think it sucks how they don't have a repo for the weeklies, it would be so much faster to get the new weekly that way

wait a sec. do they have a repo for the weeklies?

---

### Post by bluenova on 2006-06-30
What about Backports?

---

### Post by frodon on 2006-06-30
I believe that the backports are official.

---

### Post by ubuntu_demon on 2006-06-30
[QUOTE=frodon]I believe that the backports are official.[/QUOTE]
Yeah they are official. 

I've used all the 10 poll options so I couldn't add anything else :)

---

### Post by richbarna on 2006-06-30
I put cipherfunk for the divx codecs, wine, and seveas.
I've also got automatix repo for updates so I don't need the skype.
Nice and neat and tidy :-

> 
##Ultimate Dapper Sources List

##Standard Ubuntu Packages
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Automatix (PGP Key: 521A9C7C)

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

##Wine

##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
##deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

##Seveas Packages Not Included In Ubuntu

##deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas extras
##deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas extras

##Cipherfunk multimedia packages (PGP key: 33BAC1B3)

##deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
##deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

##Dapper PLF

##deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
##deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free









---

### Post by ubuntu_demon on 2006-06-30
What kind of people use kde-latest ? How much breakage is involved ? If you use kde-latest please tell us about it.

---

### Post by vayu on 2006-07-01
[QUOTE=ubuntu_demon]
Please select which non-official repositories you use. Multiple selections are possible.
[/QUOTE]


You forgot the best ones.  The ones that have me using Ubuntu on my desktop again instead of FreeBSD (Ubuntu never left my laptop).  The ones that have finally made my FOSS computer as beautiful, smooth and silky as my Mac.  The ones that have me using Gnome instead of KDE. 


The XGL/Compiz repositories:
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

```

---

### Post by Iandefor on 2006-07-01
Whatever happened to "other"?

Either way, I like debian-multimedia and Takis' repo.

---

### Post by gingermark on 2006-07-01
[QUOTE=ubuntu_demon]What kind of people use kde-latest ? How much breakage is involved ? If you use kde-latest please tell us about it.[/QUOTE]

I can honestly say in my experience (using the kubuntu.org repositories with Breezy & Dapper) I have had NO problems.

The kubuntu.org repositories are excellent. I've read that some people struggled upgrading from 3.4.8 to 3.5.2 back in Breezy, but I have never had a problem, and the packages are very stable.

Those repositories keep Kubuntu up to date, and I can honestly say they don't sacrifice stability.

---

### Post by ubuntu_demon on 2006-07-01
[QUOTE=Iandefor]Whatever happened to "other"?

Either way, I like debian-multimedia and Takis' repo.[/QUOTE]
There was no room for other repositories :(. If you use **other** repositories just mention them inside the thread. Please explain also **why** you use them.

---

### Post by ubuntu_demon on 2006-07-01
[QUOTE=vayu]You forgot the best ones.  The ones that have me using Ubuntu on my desktop again instead of FreeBSD (Ubuntu never left my laptop).  The ones that have finally made my FOSS computer as beautiful, smooth and silky as my Mac.  The ones that have me using Gnome instead of KDE. 


The XGL/Compiz repositories:
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

```[/QUOTE]
How stable are the packages from these repositories ? Do you think a lot of people use them ?

If you use these repositories how much work is it to enable compiz and xgl ? Is it still a power user thing ?

---

### Post by ubuntu_demon on 2006-07-01
I'm wondering are KDE people using openoffice instead of koffice or is there another reason why the koffice-latest repository is rarely used ?

I'm also wondering why seveas repository is more used than I expected. Is it because people go to source-o-matic and enable everything they might need ? Or they actually using packages from seveas such as freenx ?

Maybe skype isn't used so much because people prefer ekiga ? Or maybe VOIP isn't used much at all.

cipherfunk, plf and wine are used a lot. Which is what I expected.

---

### Post by -Rick- on 2006-07-01
[QUOTE=ubuntu_demon]I'm wondering are KDE people using openoffice instead of koffice or is there another reason why the koffice-latest repository is rarely used ?
[/QUOTE]
I need .doc files, since thats what everyone else uses. I only use KOffice on my laptop since it doesn't have much RAM. I convert the docs later with OOo to .doc.

If KOffice would support (better) read and write support I would be using it.

Also thanks for the kde-latest repos, using it now :)

---

### Post by disturbed1 on 2006-07-01
rarewares.org and debian-multimedia.org

Rarewares has some hard to find audio codecs (Monkeys Audio), and debian-multimedia because it has the newest and latest multimedia apps.

---

### Post by ubuntu_demon on 2006-07-01
[QUOTE=disturbed1]rarewares.org and debian-multimedia.org

Rarewares has some hard to find audio codecs (Monkeys Audio), and debian-multimedia because it has the newest and latest multimedia apps.[/QUOTE]
Can you give us more information ?

---

### Post by John.Michael.Kane on 2006-07-01
From what i can see the codecs on [**rarewares**]("http://rarewares.org/") seem to be more uptodate.

---

### Post by disturbed1 on 2006-07-01
[quote=ubuntu_demon]Can you give us more information ?[/quote] 
[www.rarewares.org]("http://www.rarewares.org") ;)

Things like different builds of vorbis, musepack, VP7, monkey's audio encoder, decoder, and K3B plugin. Not for the faint at heart though. Since items like oggenc which is linked to libvorbis.so which in /usr/lib, the *tuned* vorbis libs are installed in /usr/share/lib which you would need to call explcititly, or re-link yourself.

---

### Post by SpEcIeS on 2006-07-01
My personal favorite is:

```
# Debian Unstable
deb ftp://sunsite.cnlab-switch.ch/mirror/debian/ unstable main contrib non-free
deb-src ftp://sunsite.cnlab-switch.ch/mirror/debian/ unstable main contrib non-free
```

Hehehehe.  :D

---

### Post by Anduu on 2006-07-01
[QUOTE=ubuntu_demon]How stable are the packages from these repositories ? Do you think a lot of people use them ?

If you use these repositories how much work is it to enable compiz and xgl ? Is it still a power user thing ?[/QUOTE]

```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```

Their compiz/XGL packages are top notch.I have used them since XGL was first made to work with Dapper Beta.During the last couple months before Dapper went final they were being updated almost daily and even now a couple times a week at least.

With all those upgrades my XGL maybe broke 2 or 3 times but fixed packages would appear quickly...within hours.

Installing XGL using their repos is no more difficult than any other.In fact their ATI how-to was my first really succesful attempt at installing.

[http://www.compiz.net/viewforum.php?id=5](http://www.compiz.net/viewforum.php?id=5)

---

### Post by ubuntu_demon on 2006-07-02
[QUOTE=Anduu]```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```

Their compiz/XGL packages are top notch.I have used them since XGL was first made to work with Dapper Beta.During the last couple months before Dapper went final they were being updated almost daily and even now a couple times a week at least.

With all those upgrades my XGL maybe broke 2 or 3 times but fixed packages would appear quickly...within hours.

Installing XGL using their repos is no more difficult than any other.In fact their ATI how-to was my first really succesful attempt at installing.

[http://www.compiz.net/viewforum.php?id=5](http://www.compiz.net/viewforum.php?id=5)[/QUOTE]
So it's still a power user thing ;)

---

### Post by yaztromo on 2006-07-02
[QUOTE=disturbed1]rarewares.org and debian-multimedia.org

Rarewares has some hard to find audio codecs (Monkeys Audio), and debian-multimedia because it has the newest and latest multimedia apps.[/QUOTE]

Same here. Rarewares for oggenc-aotuv and lame-3.97

> 
#Rarewares
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./


@disturbed1
Although for updated ogg vorbis I have not had to re-link anything? Just installed aotuv and a few other vorbis bits from rarewares and ran?

---

### Post by mstlyevil on 2006-07-02
[QUOTE=ubuntu_demon]How stable are the packages from these repositories ? Do you think a lot of people use them ?

If you use these repositories how much work is it to enable compiz and xgl ? Is it still a power user thing ?[/QUOTE]

The majority of Compiz users on Dapper use them. They are very stable now that the dock and miniwin plugins have been removed and have a lot nicer effects than the vanilla cvs compiz. They are a lot more stable and up to date than the XGL/Compiz versions in the repos.

---

### Post by ubuntu_demon on 2006-07-03
[QUOTE=mstlyevil]The majority of Compiz users on Dapper use them. They are very stable now that the dock and miniwin plugins have been removed and have a lot nicer effects than the vanilla cvs compiz. They are a lot more stable and up to date than the XGL/Compiz versions in the repos.[/QUOTE]
Okay thnx.

---

### Post by Christmas on 2006-07-03
amaroK latest only. nice post and hard to answer? what's the matter with wine in the official repos isn't it official?

---

### Post by ubuntu_demon on 2006-07-03
[QUOTE=Christmas]what's the matter with wine in the official repos isn't it official?[/QUOTE]

That wine repository is wine's official bleeding edgy repository for Dapper. It's not an official Ubuntu repository run by canonical though. The package version in the wine repository is : 0.9.16~winehq0~ubuntu~6.06-1

Whereas Ubuntu's wine package in universe has version : 0.9.9-0ubuntu2 which is older but might be more stable.

---

### Post by ubuntu_demon on 2006-07-03
I linked to this thread on my blog : [http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

---

### Post by livingtarget on 2006-07-06
> **ubuntu_demon said:**
> What kind of people use kde-latest ? How much breakage is involved ? If you use kde-latest please tell us about it.

Not too much breakage, there probably is some but it ain't too bad. I'm running Amarok 1.4.1 as well (which I always find very stable).

I build wine from source all the time (fix regressions + quicker), so I don't think that counts.

---

### Post by ubuntu_demon on 2006-07-09
The opera repository has  become obsolete for opera users.

I added canonical commercial to my recommended Dapper sources.list right here : [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

```

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

Here's a bit more information :
[http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository](http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository)
[http://www.opera.com/pressreleases/en/2006/07/06/02/](http://www.opera.com/pressreleases/en/2006/07/06/02/)

I posted on my blog about this repository :
[http://ubuntudemon.wordpress.com/2006/07/09/dapper-commercial-repository/](http://ubuntudemon.wordpress.com/2006/07/09/dapper-commercial-repository/)

---

