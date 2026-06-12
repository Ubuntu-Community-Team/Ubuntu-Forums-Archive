---
title: "a repository with flashplayer-mozilla"
date: 2005-10-07
forum: Ubuntu Backports
---

### Post by Josef K. on 2005-10-07
I know this question was made hundred times, but since ubuntuguide is out of date, mirrormax is gone, official backports doesn't have it, debian search engine doesn't either know it and google point to (**old** message in) this forum maybe is time to ask it again :) 

[SIZE="3"]in which repository may i find flashplayer-mozilla?![/SIZE] ](*,)

---

### Post by az on 2005-10-07
[QUOTE=Josef K.]I know this question was made hundred times, but since ubuntuguide is out of date, mirrormax is gone, official backports doesn't have it, debian search engine doesn't either know it and google point to (**old** message in) this forum maybe is time to ask it again :) 

[SIZE="3"]in which repository may i find flashplayer-mozilla?![/SIZE] ](*,)[/QUOTE]


multiverse.


Flashplugin-nonfree fetches the lates flash from macromedia....

---

### Post by Josef K. on 2005-10-07
in my sources.list I've

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-extras main universe multiverse restricted
deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-backports-staging main universe multiverse restricted

and I cannot find any flash player plugin in :confused:

---

### Post by aysiu on 2005-10-07
I don't know. According [to this packages search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=flash&searchon=names&subword=1&version=hoary&release=all), it's in multiverse.

Are you installing via apt-get or Synaptic?

---

### Post by Josef K. on 2005-10-07
I've tried both :confused: 
oh, well, I'll download it directly via web :roll:

---

### Post by Mustard on 2005-10-08
Post your complete source.list Josef K.   Your missing something in your source.list for sure I would say.  The links to the repositories you have posted are not the relevant ones for the software you are after.  It's in the hoary multiverse, not the hoary-extras multiverse, nor the hoary-backports multiverse.

---

### Post by laltopi on 2005-10-08
What architecture are you using? Flash is available only for 32 bit intel platform

---

### Post by Josef K. on 2005-10-09
I use an athlonXP barton (32bit) on a nforce2 mobo

here's my sources.list

[INDENT]

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hoary main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

## backports

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-backports main universe multiverse restricted 
deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-extras main universe multiverse restricted 
deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-backports-staging main universe multiverse restricted 

## amule repository (disableb vollstreckernet cause amule CVS need missing libc)

deb [http://amule-debian.dyndns.org/](http://amule-debian.dyndns.org/) debian/ 
# deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule  
# deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing wx  

## klibido repository

deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main 
deb-src [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main 

[/INDENT]

---

### Post by Mustard on 2005-10-09
I think these entries are not in your sources list...

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

# or you might even have an Italian mirror?

#deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary multiverse
#deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary multiverse

```

Here is a copy of my current sources.list, which I am pretty sure I just got working properly yesterday. :)

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports and extras
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

Looking at my sources list now, I wonder why I shouldn't just add the word 'multiverse' to the end of the two prior links to the same url which point to universe, if you know what I mean.  It seems they are seperate and working atm, so I won't tinker. :)

I should probably be using Australian mirrors of some of the links, but I get a bit confused over which ones have mirrors and which don't sometimes....

-edit-

Are you still getting hits from your link to the  backports staging?
```

deb http://mirror.brianpuccio.net/ubuntu...ts-repository/ hoary-backports-staging main universe multiverse restricted 
```

---

### Post by Josef K. on 2005-10-10
[QUOTE=Mustard]I think these entries are not in your sources list...
#deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary multiverse
#deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary multiverse
[/QUOTE]

I've added them and now everything work fine :D 
but I don't understand: if I browse those directories with firefox they look empty :confused: 

[QUOTE=Mustard]
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
[/QUOTE]

I thought mirrormax was shut off...

> 
deb [http://mirror.brianpuccio.net/ubuntu...ts-repository/](http://mirror.brianpuccio.net/ubuntu...ts-repository/) hoary-backports-staging main universe multiverse restricted [/code]

not every directory, but I haven't check which one isn't working

---

### Post by Mustard on 2005-10-10
I thought mirrormax was closed too, but I think it was the mirrormax 'hoary-backports' that were closed and the mirrormax 'hoary-extras' is still open.  That's my take on the situation.

---

