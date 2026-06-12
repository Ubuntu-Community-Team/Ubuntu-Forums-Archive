---
title: "Breezy Backports Open!"
date: 2005-11-08
forum: Ubuntu Backports
---

### Post by eyebrowman92 on 2005-11-08
does anyone know when the breezy backports will be released officially?

---

### Post by kvidell on 2005-11-08
[http://ubuntuforums.org/showthread.php?t=83282](http://ubuntuforums.org/showthread.php?t=83282)

This conversation's been going on for awhile.
Boiled down: We're waiting on Ubuntu Proper to open up the repo tree.
- Kev

---

### Post by jdong on 2005-11-09
Congrats, Breezy Badger is now Backports-equipt... Let the partying begin!

---

### Post by earobinson on 2005-11-09
*party*

oh ya keep up the good work!

---

### Post by 23meg on 2005-11-09
Congrats jdong, rock on.

---

### Post by majikstreet on 2005-11-09
~party On~

---

### Post by matthew on 2005-11-09
Thanks, bro.

---

### Post by jdong on 2005-11-09
Yes, the next week or so would be a major catchup effort with all the requests... Thanks everyone for their patience, and thank the Ubuntu folks and mdz for getting the repository up!

---

### Post by rwabel on 2005-11-09
thanks a lot!

---

### Post by kashms on 2005-11-09
what is the apt line for the backports repository that goes in sources.list?

---

### Post by linkunderscore on 2005-11-09
So does this mean Hoary's backports are back online?

edit: actually....not of the repos are working for hoary atm :(

---

### Post by christooss on 2005-11-09
I praise you jdong.

Horay for backports

---

### Post by linkunderscore on 2005-11-09
apaprently im half retarded and can't read:
> Example Hoary configuration:


    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

    NOTE: This hoary-backports line is obsolete. Please don't use it:
    deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

    Hoary Extras on mirrormax is still valid, though a few notable packages were removed due to legal issues:
    deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

So does this mean I have to use the Breezy backports? or what?

Whats going on for us die-hard-holding-out-to-the-last-moment Hoary people?


EDIT: this is my source.list ```
deb ftp://mirror.mcs.anl.gov/pub/ubuntu hoary main restricted universe multiverse
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb ftp://mirror.mcs.anl.gov/pub/ubuntu hoary-updates main restricted
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu hoary-updates main restricted

deb ftp://mirror.mcs.anl.gov/pub/ubuntu hoary-security main restricted
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#deb ftp://ftp.nerim.net/debian-marillat/ stable main
#deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#deb ftp://ftp.nerim.net/debian-marillat/ testing main

#backup Mirror - FAST
##deb ftp://ftp2.caliu.info/backports hoary-backports main universe multiverse restricted
##deb ftp://ftp2.caliu.info/backports hoary-extras main universe multiverse restricted

deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main restricted universe multiverse

 ## e17 repository from Elive
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://www.vobcopy.org/mirror/elive/ elive main efl elive

```

---

### Post by jdong on 2005-11-09
Your Hoary lines are valid. See [http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291) for more information on repo URL's.

---

### Post by Kyral on 2005-11-09
Does this mean I can finally stop handling requests for VLC? :P

---

### Post by duffman25 on 2005-11-09
[QUOTE=jdong]Your Hoary lines are valid. See [http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291) for more information on repo URL's.[/QUOTE]

This is great news! Maybe someone could post it in the fridge ;)

---

### Post by meborc on 2005-11-09
good news... [/me opens a beer] :rolleyes:

---

### Post by jdong on 2005-11-09
[QUOTE=duffman25]This is great news! Maybe someone could post it in the fridge ;)[/QUOTE]

Anyone here with Fridge access? Anyone? Anyone?

---

### Post by canadianwriterman on 2005-11-09
I added the two Breezy Backports and got this message in Synaptic:

[I]W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)[/I]

---

### Post by jdong on 2005-11-09
Hit the Reload button.

---

### Post by loon on 2005-11-09
Wow, bout time!! 

Too bad the next Ubuntu goes live in like a day.




< /sarcasm>

---

### Post by Sykil on 2005-11-09
w00t!  Thanks a bunch.

---

### Post by canadianwriterman on 2005-11-09
[QUOTE=jdong]Hit the Reload button.[/QUOTE]

Perfect! Thank you. One other question: how do I keep track of what goes into the backports?

---

### Post by jdong on 2005-11-09
[QUOTE=canadianwriterman]Perfect! Thank you. One other question: how do I keep track of what goes into the backports?[/QUOTE]

Subscribe to the ubuntu-backports mailing list.

---

### Post by canadianwriterman on 2005-11-09
[QUOTE=jdong]Subscribe to the ubuntu-backports mailing list.[/QUOTE]

Thanks, jdong.

---

### Post by Suzan on 2005-11-09
Thanks! :-)

---

### Post by Manny C on 2005-11-09
Yeah!...This next week, I hope, will see me actually chewing up my 12Gb download limit :P

---

### Post by castrojo on 2005-11-09
[QUOTE=duffman25]This is great news! Maybe someone could post it in the fridge ;)[/QUOTE]

Done!

---

### Post by matthew on 2005-11-09
[quote=loon]Wow, bout time!! 

Too bad the next Ubuntu goes live in like a day.

< /sarcasm>[/quote] Dude, that was incredibly ungrateful. Shame on you.

---

### Post by jdong on 2005-11-09
[QUOTE=whiprush]Done![/QUOTE]

Yay! Thanks man!

---

### Post by Logic* on 2005-11-09
Thankyou jdong :D

---

### Post by Gamabunta on 2005-11-09
I get this error message after reloading:
```
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

---

### Post by idn on 2005-11-09
What is the difference between the two repos:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

Why is one hosted on the ubuntu servers and one on mirrormax?

---

### Post by Gamabunta on 2005-11-09
Backports are officially supported.

Extras are not.

---

### Post by earobinson on 2005-11-10
im getting this error:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by yhotg on 2005-11-10
same error here

---

### Post by kudu on 2005-11-10
I get this after hitting reload button:


W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


What gives ??

---

### Post by JuanC on 2005-11-10
Would backports include KDE 3.5 final for AMD64 when will be released?

---

### Post by raublekick on 2005-11-10
[QUOTE=kudu]I get this after hitting reload button:


W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


What gives ??[/QUOTE]

just click OK and then click the reload button in synaptic

---

### Post by earobinson on 2005-11-10
I tryed a reload still get > W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by souled on 2005-11-10
[QUOTE=earobinson]I tryed a reload still get[/QUOTE]

Same here... Hopefully it will be fixed soon.

---

### Post by earobinson on 2005-11-10
yup just hoping.

---

### Post by `GooZ´ on 2005-11-10
Hooray! Let's tie a fish to one's head and squeak like a mouse!

---

### Post by lonetree on 2005-11-10
can someone post a working sources.list here. I'm getting lots error

thanks

regards,

---

### Post by `GooZ´ on 2005-11-10
This one also contains plf repo's and stuff:
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


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
## team.
 deb http://archive.ubuntu.com/ubuntu breezy universe
 deb-src http://archive.ubuntu.com/ubuntu breezy universe

 deb http://archive.ubuntu.com/ubuntu breezy multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

 deb http://security.ubuntu.com/ubuntu breezy-security multiverse
 deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free

##Backports (de echte)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

```

---

### Post by Spudgun on 2005-11-10
Awesome :D

---

### Post by phanboy_iv on 2005-11-10
God bless you, jdong.

---

### Post by loon on 2005-11-10
[QUOTE=matthew]Dude, that was incredibly ungrateful. Shame on you.[/QUOTE]

A lot of you are very emotional up here.  It was was a good thing :)  And I think we all agree the backports took a lot longer than needed, but now its time to celebrate.

:KS 
-loon

---

### Post by dabear on 2005-11-10
Trying sudo apt-get update after adding backports throws:
```

Fetched 51.3kB in 2s (19.2kB/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```
how do I avoid this?

---

### Post by bluebyt on 2005-11-10
[QUOTE=dabear]Trying sudo apt-get update after adding backports throws:
```

Fetched 51.3kB in 2s (19.2kB/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```
how do I avoid this?[/QUOTE]

I have the same error!

---

### Post by jdong on 2005-11-10
There seems to be all sorts of wacky errors with archive.ubuntu.com these past few days. I can't get universe/multiverse to refresh, and am having trouble with deb-src lines for Dapper.

It's not just Backports affected!

---

### Post by eyebrowman92 on 2005-11-10
alright thanks. what escactly do backports do anyway? i never really understood what they were for.

---

### Post by Manny C on 2005-11-10
[quote=eyebrowman92]alright thanks. what escactly do backports do anyway? i never really understood what they were for.[/quote] 
Courtesy of [Ubuntu Backports]("http://backports.ubuntuforums.org/"):
>  **About Ubuntu Backports**
 Ubuntu Linux is a great distribution, but falls short in the desktop realm to Gentoo and Fedora Core. Why? *Once a stable version is released, no new software updates are accepted.* I subscribe to the view that a distribution can be both stable *and* up-to-date, so I've taken it into my own hands to recompile *newer packages* from Hoary _(read Dapper)_...
 
Emphasis my own. Underlined serves to correctly answer your question.

---

### Post by Manny C on 2005-11-10
Comment our the deb-src lines. Unless you know what these repos do, you don't need them. ;) Half the problem solved.

---

### Post by eyebrowman92 on 2005-11-11
alright and why did you title the post breezy backports open? are they?

---

### Post by Manny C on 2005-11-11
Yes they are. I am in fact using them.

---

### Post by eyebrowman92 on 2005-11-11
alright how do i add them to my repos?

---

### Post by earobinson on 2005-11-11
I think the answer you are looking for can be found with a simple google search
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Manny C on 2005-11-11
[quote=earobinson]I think the answer you are looking for can be found with a simple google search
[http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")[/quote] 
Not the best set of instructions to use. Try [jdong's post]("http://www.ubuntuforums.org/showthread.php?t=40291") regarding this matter:
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse 
```

---

### Post by yhotg on 2005-11-11
[QUOTE=dabear]Trying sudo apt-get update after adding backports throws:
```

Fetched 51.3kB in 2s (19.2kB/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```
how do I avoid this?[/QUOTE]

i'm having the some one since like a week.
any idea how to get it solved?

---

### Post by jeremy on 2005-11-11
I have the breezy backports enabled, and can apt-get update without any errors, but as far as I can see, there is nothing there.
Is that correct?

---

### Post by Pitou on 2005-11-11
I noticed the same, it seems the backports are empty, but it shouldn't be long before we get the stuff.

Pitou!

---

### Post by jasongrieves on 2005-11-11
[QUOTE=Pitou]I noticed the same, it seems the backports are empty, but it shouldn't be long before we get the stuff.

Pitou![/QUOTE]
Thanks for clarifying this.  I was curious about this myself

---

### Post by eyebrowman92 on 2005-11-11
alright thanks. ill add them.

---

### Post by jdong on 2005-11-11
Try switching between achive.ubuntu.com and **us**.archive.ubuntu.com -- It seems like the archive.ubuntu.com server is having all kinds of MD5Sum issues.

---

### Post by denizin on 2005-11-11
I've switched between us, gb and the standard deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse repositories and do not see myth anything with a sudo apt-cache search mythtv after running an update.

I've been trying since yesterday evening to install myth.  I also installed lame but I think I may need liblame0 which I also cannot find (though I may be missing the package with another name).  Can anyone give any suggestions?  Thanks...

I've read most of the docs and websites I found in this thread and some others.  I just can't seem to find it with apt.

Kubuntu 5.10 Breezy Badger

---

### Post by jdong on 2005-11-11
Post your sources.list

---

### Post by ubuntu_demon on 2005-11-11
congratiolations to the backports team!
great news!

(oftopic : I hope the new firefox,thunderbird and gaim get released and backported soon)

---

### Post by denizin on 2005-11-11
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe 
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by jdong on 2005-11-11
[QUOTE=denizin]...

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe[/QUOTE]


replace with
```

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy  main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

```

---

### Post by eyebrowman92 on 2005-11-11
how long will it take after gaim and firefox get released for them to get backported?

---

### Post by jdong on 2005-11-11
Depends on how long it takes before it gets into Dapper and of an acceptable stability... Firefox should be pretty quick -- rc builds are currently in the works for Dapper.

I don't know about GAIM 2's speed specifically... I don't typically follow them as closely.

---

### Post by denizin on 2005-11-11
Thank you.  I was unaware mixing repositories like I had would mess up the dependencies.  Installing Myth as I type this.

---

### Post by lonetree on 2005-11-12
has anyone got openoffice updated to OO2 via the repository?

I'm still in .129 

or has it not been updated on the repository yet?

:-(

---

### Post by jdong on 2005-11-12
[QUOTE=lonetree]has anyone got openoffice updated to OO2 via the repository?

I'm still in .129 

or has it not been updated on the repository yet?

:-([/QUOTE]
It will only be officially provided through breezy-backports whenever the source gets uploaded into Dapper.

However, in the meantime, the OOo2 maintainer has provided Breezy packages for OOo2.
 Add this to sources.list:

```

deb http://people.ubuntu.com/~doko/OOo2 ./

```

---

### Post by JuanC on 2005-11-12
I have Kubuntu 5.10 for amd64.

I add breezy backport repository , but i don't find any new package.

---

### Post by jdong on 2005-11-12
[QUOTE=JuanC]I have Kubuntu 5.10 for amd64.

I add breezy backport repository , but i don't find any new package.[/QUOTE]

Nothing is in the repository yet. I've queued up at least 20 or so packages now for build, but the Ubuntu official who approves these builds (James Troup) is at the UBZ conference and likely too busy to deal with Backports for now.

Wait another week or so, and things should start showing up.

---

### Post by lonetree on 2005-11-12
[QUOTE=jdong]It will only be officially provided through breezy-backports whenever the source gets uploaded into Dapper.

However, in the meantime, the OOo2 maintainer has provided Breezy packages for OOo2.
 Add this to sources.list:

```

deb http://people.ubuntu.com/~doko/OOo2 ./

```[/QUOTE]

thanks jdong,

I got OO2 upgraded now. Great! Btw, how do I keep track on the repositories? Always have problems with backports universe multiverse etc etc. Is there no fixed official repositories and backports? I always see many changes here and there, or could I be wrong. Thanks anyway. 

Another thing, anyone got skype installed successfully via apt-get?

Thanks again.


Regards,

---

### Post by Velvet Elvis on 2005-11-12
[QUOTE=jdong]Nothing is in the repository yet. I've queued up at least 20 or so packages now for build, but the Ubuntu official who approves these builds (James Troup) is at the UBZ conference and likely too busy to deal with Backports for now.

Wait another week or so, and things should start showing up.[/QUOTE]

If I'm getting antsy I can change the source repos to dapper and use apt-get build-dep, apt-get source, and dpkg-buildpackage can't I?

---

### Post by jdong on 2005-11-12
[QUOTE=Velvet Elvis]If I'm getting antsy I can change the source repos to dapper and use apt-get build-dep, apt-get source, and dpkg-buildpackage can't I?[/QUOTE]
Absolutely :)

---

### Post by jdong on 2005-11-12
[QUOTE=lonetree]thanks jdong,

I got OO2 upgraded now. Great! Btw, how do I keep track on the repositories? Always have problems with backports universe multiverse etc etc. Is there no fixed official repositories and backports? I always see many changes here and there, or could I be wrong. Thanks anyway. [/QUOTE]

Well, we should've settled down for now, and as far as I can look into the future, we should be staying on archive.ubuntu.com. Whether or not the archives suffer from Md5sum mismatches is out of my control....


Brief History:
Warty Backports were first hosted on SF.Net, and then they basically kicked me off because it was draining the bandwidth on their Project Web Services. Then, I moved off to a 6MBit dedicated Business DSL connection (cloud9.somniumcomputing.com), but then that soon ended as the donor notified me that he was getting too saturated. Then, we moved onto backports.ubuntuforums.org, courtesy of Ubuntu-Geek. Soon enough, we realized that Backports has at least 25,000 unique IP hits per day, and could burn up a 2000GB bandwidth limit in a week if uncapped! As a result, we moved onto an rsync mirroring system and thus mirrormax and caliu were born.

After that, a combination of fast-paced development in Backports and Breezy, along with a lack of understanding of Debian intricacies on my behalf and no communication between Backports and the Ubuntu team, we were stepping all over each other, and Ubuntu devs were starting to be swamped with mysterious bug reports which eventually after a lot of frustration were rooted to Hoary Backports. After a CC meeting, it was resolved that Ubuntu Backports is a valuable service, and should be an official part of Ubuntu. Thus, achive.ubuntu.com backports were born, signalling a new era of Backports with the cooperation of Ubuntu developers.

---

### Post by Jenda on 2005-11-12
What's the best way to find out what I can get in the backports and/or extras?

---

### Post by jdong on 2005-11-12
[http://packages.ubuntu.com/breezy-backports/](http://packages.ubuntu.com/breezy-backports/)

---

### Post by idn on 2005-11-13
When are we going to start to see packages added into the repositories?

---

### Post by jdong on 2005-11-13
When James Troup gets back from the UBZ conference.

---

### Post by Jenda on 2005-11-13
[QUOTE=jdong][http://packages.ubuntu.com/breezy-backports/](http://packages.ubuntu.com/breezy-backports/)[/QUOTE]
Danke :)

---

### Post by andrewpmk on 2005-11-13
Could someone sticky this thread please?

---

### Post by jdong on 2005-11-13
What info in here isn't in the sticky already? I'd rather merge info into it.

---

### Post by Jenda on 2005-11-13
Ok - the list is rather brief, eh? 0 AFAIK.

---

### Post by jdong on 2005-11-13
Read # 84 and 85....

---

### Post by xbaez on 2005-11-13
Here is my complete /etc/apt/sources.list

This will let me add 
-Skype, Java, Realplayer (Pengiun Liberation Front)
-OpenOffice 2.0 ([http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2)) 
-w32codecs ([ftp://cipherfunk.org](ftp://cipherfunk.org))
-KDE 3.5 RC1 ([http://kubuntu.org/packages/kde35rc1](http://kubuntu.org/packages/kde35rc1))

I'll appreciate any comments since I want all my software to be managed via apt-get

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted #Kubuntu 5.10
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted #Ubuntu 5.10
# XB Download CD
#deb cdrom:[XB Extra Packages for Kubuntu 5.10 Breezy]/ /  #XB Extra Packages for Kubuntu 5.10

# Official Kubuntu Updates (KDE 3.5 RC1)
deb [http://kubuntu.org/packages/kde35rc1](http://kubuntu.org/packages/kde35rc1) breezy main

# ======================= Official Repositories 
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy main multiverse restricted universe #Breezy
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy-updates main multiverse restricted universe #Breezy Updates
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy-security main multiverse restricted universe #Breezy Security
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy-backports main multiverse restricted universe #Breezy Backports
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy-backports main multiverse restricted universe #Breezy Backports

# Official source repos. Dead weight for non-developers.
#deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy main multiverse restricted universe #Breezy Source
#deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy-updates main multiverse restricted universe #Breezy Updates Source
#deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy-security main multiverse restricted universe #Breezy Security Source
#deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu/](ftp://mirror.mcs.anl.gov/pub/ubuntu/) breezy-backports main multiverse restricted universe #Breezy Security Source
# =========================================================


# =============================== Games ==================
# taken from [http://personal.inet.fi/koti/jsiltala/juha/comp/sources.list](http://personal.inet.fi/koti/jsiltala/juha/comp/sources.list)

# MONKEY BUBBLE
deb [http://home.gna.org/monkeybubble/debian](http://home.gna.org/monkeybubble/debian) ./  #Monkey Bubble

# ================ Unofficial repositories below, till end of file. =====
# Unofficial backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

# w32codecs, taken from #[http://www.ubuntuforums.org/showthread.php?t=70815&highlight=breezy-backports](http://www.ubuntuforums.org/showthread.php?t=70815&highlight=breezy-backports)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main #w32codecs

# OpenOffice.org 2.0
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# ============================ Pengiun Liberation Front ========
# contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
# FTP mirror from [http://free.fr](http://free.fr) (french ISP)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
#deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/freecontrib/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/freecontrib/) breezy free non-free
#deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/freecontrib/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/freecontrib/) breezy free non-free

---

### Post by denisesballs on 2005-11-14
I just wanna clarify. Backports are open, but there's no packages in there yet? Is that correct? And it's normal not to have anything upgrading?

---

### Post by ubuntu_demon on 2005-11-14
information about the plf repo isn't in the sticky. But I don't know whether you want that in there because you don't have connections to plf.

The plf repo I use :

```

#plf
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

```

---

### Post by jeremy on 2005-11-14
[QUOTE=denisesballs]I just wanna clarify. Backports are open, but there's no packages in there yet? Is that correct? And it's normal not to have anything upgrading?[/QUOTE]
That is correct, it seems that there will be no backports until the end of the week or so.

---

### Post by n6mod on 2005-11-14
[QUOTE=jdong]Nothing is in the repository yet. I've queued up at least 20 or so packages now for build, but the Ubuntu official who approves these builds (James Troup) is at the UBZ conference and likely too busy to deal with Backports for now.
[/QUOTE]

Would you be so kind as to share that list?

I'm wondering if there's a newer Evolution in there, since evolution-exchange is irretrievably broken in Breezy proper.

I really don't want to deal with building Evolution. ;)

-Z

---

### Post by jdong on 2005-11-14
Look at ubuntu-backports archives on lists.ubuntu.com...

But no, evolution stuff is not in the list.

---

### Post by stevenyu on 2005-11-15
I have use the back-port rep from my ISP mirror server, however a lot of software doesn't seems to be in there any more, like java!!!

[http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/breezy-backports/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/breezy-backports/)

Is there anything wrong with it?  cause if I use the Automatix, it seems to be able to grab almost everything

---

### Post by stubby on 2005-11-15
will the sources for breezy-extra be available as well ? ever?

i tried 

```
deb-src http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```

but didn't work

---

### Post by jdong on 2005-11-15
Whenever the first Breezy Extras package is done. That'll still be a while, because of the lack of any high-enough quality packages to put in there...

---

### Post by angrykeyboarder on 2005-11-16
[quote=idn]What is the difference between the two repos:

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") breezy-extras main restricted universe multiverse

Why is one hosted on the ubuntu servers and one on mirrormax?[/quote] 
Because backports is an official Ubuntu repository.  All the programs in breezy-backports are backported from Dapper.

Extras are not part of Ubuntu at all (which is why they aren't with the rest of Ubuntu packages) but they made available because they are popular with Ubuntu users and compatible with Ubuntu. But if you use one and your feet catch fire or your monitor blows up it's not Ubuntu's problem. ;-)

Prior to last summer, backports weren't official either and were on the same servers as extras.

---

### Post by eyebrowman92 on 2005-11-21
anyone know if gaim 2.0 will be backported?

---

### Post by jdong on 2005-11-21
Anybody know if GAIM 2.0 is gonna be released? ;)

---

### Post by akurashy on 2005-11-22
well i did my own .deb of it xD, gave it to bored2k, 

[http://davidgonz.com/gaim_2.0-1_i386.deb](http://davidgonz.com/gaim_2.0-1_i386.deb) 
(Use at your own risk, works smoothly on my system, but still use AT YOUR OWN RISK)

---

### Post by adam.tropics on 2005-11-22
cheers akurashy, working smoothly.......so far!!

---

### Post by rwabel on 2005-11-22
thanks for the deb file. works fine. I had just 2 extension to removed because of incompatibility :-)
and now the system shows me that there is one newer package (the old gaim) but not upgradeable.

---

### Post by Jenda on 2005-11-22
Good work akurashy!

(And good to meet you on the forum too, mate)

---

### Post by angrykeyboarder on 2005-11-22
[quote=eyebrowman92]anyone know if gaim 2.0 will be backported?[/quote] 
Well assuming it's released it would have to make it's way to Dapper, otherwise there's nothing to backport from. :-)

---

### Post by carlosqueso on 2005-11-22
The backports have stuff in them! :-D I just got my first upgrade.  Thanks Ubuntu Backports folks!

---

### Post by jdong on 2005-11-22
Hey, today's a day of celebration for all of us! :)

---

### Post by eyebrowman92 on 2005-11-22
[QUOTE=angrykeyboarder]Well assuming it's released it would have to make it's way to Dapper, otherwise there's nothing to backport from. :-)[/QUOTE]


no i know. i was wondering if there will be a backport once it goes to dapper.

---

### Post by ubuntu_demon on 2005-11-23
[QUOTE=jdong]Hey, today's a day of celebration for all of us! :)[/QUOTE]
yeah this is great! :)

---

### Post by bored2k on 2005-11-23
[QUOTE=akurashy]well i did my own .deb of it xD, gave it to bored2k, 

[http://davidgonz.com/gaim_2.0-1_i386.deb](http://davidgonz.com/gaim_2.0-1_i386.deb) 
(Use at your own risk, works smoothly on my system, but still use AT YOUR OWN RISK)[/QUOTE]
This package broke my ability to downgrade. I wouldn't recommend it to those wanting to apt-get upgrade gaim in the future :s.

---

### Post by rwabel on 2005-11-23
[quote=bored2k]This package broke my ability to downgrade. I wouldn't recommend it to those wanting to apt-get upgrade gaim in the future :s.[/quote]

I could downgrade to the old gaim and I could upgrade again to 2.x. There were no problems in my case.
The problem is that the system wants to upgrade to the gaim version from breezy or dapper. So I just locked the version :-)

---

