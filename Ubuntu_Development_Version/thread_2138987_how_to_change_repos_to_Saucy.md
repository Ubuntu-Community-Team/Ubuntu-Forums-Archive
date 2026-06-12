---
title: "how to change repos to Saucy"
date: 2013-04-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-04-25
[B]sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list

[/B][B][B]sudo apt-get update && sudo apt-get dist-upgrade

[/B][/B]**sudo apt-get upgrade**

---

### Post by craig10x on 2013-04-25
I'm new with doing the upgrades...so, all i need do is run those 3 commands in the terminal?

Also, i have 2 ppas...one is google chrome and the other is a web8 ppa for Oracle Java updates...that one does say raring on it...the chrome one does not...
anything i need do with those?

---

### Post by jinjorge on 2013-04-25
> **craig10x said:**
> I'm new with doing the upgrades...so, all i need do is run those 3 commands in the terminal?

Also, i have 2 ppas...one is google chrome and the other is a web8 ppa for Oracle Java updates...that one does say raring on it...the chrome one does not...
anything i need do with those?

yes, all you need is to run the commands in terminal.  You may have to revert the ppa to raring if they are not (yet) supported in saucy(most likely).

---

### Post by craig10x on 2013-04-25
Thank You jinjorge :)

I don't think web8 has added saucy yet but could i let it change it to saucy and then when web8 adds it then updates would come through for it?
Or should revert back to raring until i see that they have added saucy for the ppa?

---

### Post by PJs Ronin on 2013-04-25
Might need to give it a couple of hours to propagate throughout all the mirrors.   I know my mirror (mirror.aarnet.edu.au} runs about 6 hours behind.

---

### Post by kevpan815 on 2013-04-25
Thank You Ventrical, for posting that, sounds very easy to do I guess I will try it out after all.

---

### Post by pnarciso on 2013-04-25
A little warning. Changing to saucy repos, make software-properties-gtk to crash. To avoid that you must enter this line in the console: sudo gedit /usr/share/python-apt/templates/Ubuntu.info.
And add this lines:

```
Suite: saucy
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 13.10 'Saucy Salamander'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: saucy
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 13.10 'Saucy Salamander'

Suite: saucy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*13.10
MatchURI: cdrom:\[Ubuntu.*13.10
Description: Cdrom with Ubuntu 13.10 'Saucy Salamander'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: saucy
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: saucy
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: saucy-security
ParentSuite: saucy
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: saucy-security
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: saucy-updates
ParentSuite: saucy
RepositoryType: deb
Description: Recommended updates

Suite: saucy-updates
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: saucy-proposed
ParentSuite: saucy
RepositoryType: deb
Description: Pre-released updates

Suite: saucy-proposed
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: saucy-backports
ParentSuite: saucy
RepositoryType: deb
Description: Unsupported updates

Suite: saucy-backports
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates
```

---

### Post by serdotlinecho on 2013-04-25
> **ventrical said:**
> [B]sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list

[/B][B][B]sudo apt-get update && sudo apt-get dist-upgrade

[/B][/B]**sudo apt-get upgrade**


Thanks Ventrical :D

I'm in... :guitar:

[IMG]http://ubuntuone.com/1WcP2DiejOrEfZjaYgT742[/IMG]

[IMG]http://ubuntuone.com/18yk44yOKgcGXV7g5bo6SV[/IMG]

[IMG]http://ubuntuone.com/4mq3T5ZfI8cWKQgiqHSEGW[/IMG]

[IMG]http://ubuntuone.com/47yKp6NVLEr3dqrypTHg2d[/IMG]

[IMG]http://ubuntuone.com/1ZQe8QrubUTcaYaV9xCSOE[/IMG]

[IMG]http://ubuntuone.com/3AvcoX8j5Nvcg3z1fAPbgf[/IMG]

---

### Post by craig10x on 2013-04-25
@serdotlinecho: did that work just using the three commands, or did you have to do all those changes that pnarciso mentioned above your post?  
This is getting confusing...thought it was supposed to be just the three commands :confused:

I haven't done it yet...probably will do it on friday...but i wanted to get "straight" on what exactly to do (i am a newbie at upgrading)....

---

### Post by PJs Ronin on 2013-04-25
I'm in too... once I realized it was saucy and not sassy.  [COLOR=#000000]:oops:[/COLOR]

---

### Post by cflow on 2013-04-25
I've decided to update to saucy too. I've got the repos with the commands, but I've yet to get any updates. Do different mirrors vary in the timing of the updates? I don't use the main server due to download issues.

---

### Post by PJs Ronin on 2013-04-25
> **cflow said:**
> I've decided to update to saucy too. I've got the repos with the commands, but I've yet to get any updates. Do different mirrors vary in the timing of the updates? I don't use the main server due to download issues.
Yes, there can be delays.   See [here]("https://launchpad.net/ubuntu/+archivemirrors") for yours.

---

### Post by cflow on 2013-04-25
That's very good to know. Thanks! 

Looking at the page, I guess I will have wait at least a day for the server I use to update again.

---

### Post by craig10x on 2013-04-26
Didn't work for me...in fact, it reverted back to raring again...so at least it didn't break my software updater but on the hand, it didn't switch to saucy...
Is there another way to upgrade?  Otherwise i think i will have to forget about it...I really wish they had that new way to change it available, but i suspect it won't be ready for some time...

---

### Post by dino99 on 2013-04-26
As you might know, its a bit too early after Raring release to get Saucy. I suppose a week or so is needed before having Saucy packages landing into the yet created but empty repos.

[http://archive.ubuntu.com/ubuntu/dists/saucy/](http://archive.ubuntu.com/ubuntu/dists/saucy/)

So if you are so exited to upgrade to something that is not yet existant, check again your brain to know if following a fake "good howto" is clever or not.

---

### Post by roly33 on 2013-04-26
After changing the Repos to Saucy I'm unable to open the Software & Updates app through Dash or via the Software Sauces option in the Software Centre and keep getting an error when I try to open Software & Updates via the Software Sauces option in Software Centre.

[ATTACH=CONFIG]241793[/ATTACH]

How do I fix this, preferably without having to do a re-install?

Roland

---

### Post by dino99 on 2013-04-26
Read #15 above

sudo gedit /etc/apt/sources.list

you only should have "raring"

---

### Post by JMB74 on 2013-04-26
Have you changed all to saucy?

Even if you HAVE, If you do:
[B]
sudo apt-get update[/B]

in a terminal, you may see that there are a few entries in the sources.list that fail to fetch as they haven't had their saucy equivalents created on the mirrors yet.

For me that is happening with the "partner" repo.

i.e. *W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/saucy/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/saucy/partner/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.150 80]*

For now, if you comment out the sources.list entries that are failing to fetch, then should fix it.

Alternatively, just do upgrades via apt-get etc which will flag up the error, but carry on regardless.

---

### Post by roly33 on 2013-04-26
> **roly33 said:**
> After changing the Repos to Saucy I'm unable to open the Software & Updates app through Dash or via the Software Sauces option in the Software Centre and keep getting an error when I try to open Software & Updates via the Software Sauces option in Software Centre.

[ATTACH=CONFIG]241793[/ATTACH]

How do I fix this, preferably without having to do a re-install?

Roland

Fixed it by removing all reference to Raring from ubuntu.info and the Software & Update App opens with all repos replaced with Saucy and Software Sauces option in Software Centre no longer gives an error.

Roland

---

### Post by serdotlinecho on 2013-04-26
> **JMB74 said:**
> Have you changed all to saucy?

Even if you HAVE, If you do:
[B]
sudo apt-get update[/B]

in a terminal, you may see that there are a few entries in the sources.list that fail to fetch as they haven't had their saucy equivalents created on the mirrors yet.

For me that is happening with the "partner" repo.

i.e. *W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/saucy/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/saucy/partner/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.150 80]*

For now, if you comment out the sources.list entries that are failing to fetch, then should fix it.

Alternatively, just do upgrades via apt-get etc which will flag up the error, but carry on regardless.


I always get "404 Not Found" since 11.10 alpha...normal behaviour for pre-alpha. Dino99 is right, don't be an idiot like me. ( ._.)

---

### Post by JMB74 on 2013-04-26
> **serdotlinecho said:**
> I always get "404 Not Found" since 11.10 alpha...normal behaviour for pre-alpha. Dino99 is right, don't be an idiot like me. ( ._.)

Well, you would do. Especially if you just blindly replace the distro version in a sources.list at the beginning of a development cycle without checking which repos actually exist yet. Learnt that one a long long while back.

---

### Post by kevpan815 on 2013-04-26
Sorry, if I was the one Generating the Error Messages to the Developer's, went into my Sources List and Found Referrences Still Referring to Raring! I changed all to Saucy, now I'm Fully In for good.

---

### Post by ventrical on 2013-04-26
> **craig10x said:**
> @serdotlinecho: did that work just using the three commands, or did you have to do all those changes that pnarciso mentioned above your post?  
This is getting confusing...thought it was supposed to be just the three commands :confused:

I haven't done it yet...probably will do it on friday...but i wanted to get "straight" on what exactly to do (i am a newbie at upgrading)....


  Everything is working well here after putting in just those three commands. It can also be done like this:

sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

Please note that I do not advise (nor did I advise) that this proceedure be  executed on a production machine. Unless you have an extra hdd or other machines or are an experienced beta tester then stick with the safe and stable route.  I have  8 towers and 3 laptops all commited  to testing. It is conventional wisdom  that system will break in these early stages - so unless one has an extra  surplus machine then early beta testing  should be deferred.

As competition would have it , Windows 8 has far exceeded Ubutnu on various form factors and so I am looking forward to this release as being the new 'setting of the bar' which will bring ubuntu up to speed. Just in my own opinion but I see raring as a sandbox/blackboarding exercise for a much more workable Saucy Salamander :)

regards,
ventrical

---

### Post by kevpan815 on 2013-04-26
For me a sudo gedit /etc/apt/sources.list worked better than your 3 commands. I then changed all references of raring to saucy. A lsb_release -a command now shows me at 13.10 Development Branch.

---

### Post by Mathor on 2013-04-26
I'm really pumped for this Saucy cycle. It seems to be pulling updates.

---

### Post by dino99 on 2013-04-26
> **Mathor said:**
> I'm really pumped for this Saucy cycle. It seems to be pulling updates.

by now, its only the early "proposed" packages; all the others are renamed raring ones.

---

### Post by bmbaker on 2013-04-26
For any one who are still having problems with software-properties-gtk crashing
you can check this to see if the release got updated. sometimes it doesn't ;-)
 
```
[COLOR=#222222]gksudo gedit /etc/lsb-release[/COLOR]
```[COLOR=#333333][FONT=Ubuntu Beta]Then edit the file that opens so that it looks like this[/FONT][/COLOR]

```
[COLOR=#222222]DISTRIB_ID=Ubuntu[/COLOR]
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"
```[COLOR=#333333][FONT=Ubuntu Beta]Remember to enter which version of ubuntu you are using.[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu Beta]Then go back to the terminal after you have saved the lsb-release file and you should be able to add-apt-repository

taken from [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]http://askubuntu.com/questions/49040/apt-could-not-find-a-distribution-template-error[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
[/FONT][/COLOR]

---

### Post by kansasnoob on 2013-04-26
I don't think it's wise to do this until you know that the new toolchain has been uploaded :)

---

### Post by craig10x on 2013-04-26
Within a few weeks, wouldn't i be able to do the upgrade through the software updater? I remember someone had posted a way of putting in like 2 terminal commands that would have the software updater bring up the option of upgrade (which i guess it normally only does when a newer version goes final)...i have my software updater set to notify of any new versions...

I was glad that at least my software updater reverted back to raring (when saucy didn't come in through the terminal) when i hit "edit" and logged into the updater cause all the check boxes had blanke dout but they come back to normal with the proper settings once i logged in....

This is why we need that new simpler method the developers are working on which will enable you to simply point to the next version when it's ready for updates...that would make life simpler with this change over business...

---

### Post by ventrical on 2013-04-26
> **kevpan815 said:**
> For me a sudo gedit /etc/apt/sources.list worked better than your 3 commands. I then changed all references of raring to saucy. A lsb_release -a command now shows me at 13.10 Development Branch.

Hey .. great .. and they are not *my* three commands. They are the commands most commonly used.

If anyone wanted to know how to upgrade they could have just looked at the sticky.

[http://ubuntuforums.org/showthread.php?t=1970289](http://ubuntuforums.org/showthread.php?t=1970289)

---

### Post by serdotlinecho on 2013-04-26
```
serdotlinecho@samalander:~$ tail -n 2 /var/log/apt/history.log 
Upgrade: distro-info-data:i386 (0.13ubuntu0.1, 0.14)
End-Date: 2013-04-26  17:27:48
serdotlinecho@samalander:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu Saucy Salamander (development branch)"
```

```
serdotlinecho@samalander:~$ software-properties-gtk 
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 93, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 105, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 593, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```


I don't have or add any third party ppa :)

```
serdotlinecho@samalander:~$ ls /etc/apt/sources.list.d/*
ls: cannot access /etc/apt/sources.list.d/*: No such file or directory
```

---

### Post by grahammechanical on 2013-04-26
We will find that the extras repositories will be giving errors for weeks to come. Think about what is happening here. The Raring Repositories are now closed in the sense that the Raing code base will only receive the standard support updates. Otherwise users of 13.04 will find themselves using 13.10 in six months time and Raring will have become the daily updated kind of, sort of rolling release.

A new set of repositories have to be opened with the saucy urls and there has to be stuff to put at those locations. To start with it will be the Raring Code base. Then over time packages will be brought in that will turn the saucy development branch from a Raring code base into  a saucy code base. Oh, the images that come to mind as I use that word 'saucy!' 

There is nothing to update at the moment. There is nothing wrong with the instructions given by ventrical. The fault lies with us who are too eager (too saucy?). I will run those commands in my development Raring install on Monday or may be a bit later. Let the developers have a week-end with their families.

Edit: Perhaps we should look at the Saucy release schedule?

[https://wiki.ubuntu.com/SReleaseSchedule](https://wiki.ubuntu.com/SReleaseSchedule)

The tool chain does not get uploaded until 2nd May. Not much going on until after that.

[https://wiki.ubuntu.com/ToolChain](https://wiki.ubuntu.com/ToolChain)

> [COLOR=#333333][FONT=Ubuntu Beta]Planning and decisions for updating binutils and GCC are usually made six months before a new release cycle starts. Initial uploads are done as part of the new release cycle process[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]. GCC and binutils are updated during the release cycle.[/FONT][/COLOR]

Regards.

---

### Post by sgage on 2013-04-26
I did a saucy update about an hour ago, and got some interesting things:

Start-Date: 2013-04-26  08:52:36
Commandline: apt-get dist-upgrade
Install: gcc-4.8-base:amd64 (4.8.0-4ubuntu1, automatic), libmpc3:amd64 (1.0.1-1, automatic)
Upgrade: libstdc++6:amd64 (4.7.3-1ubuntu1, 4.8.0-4ubuntu1), base-files:amd64 (6.12ubuntu2, 6.12ubuntu3), libgomp1:amd64 (4.7.3-1ubuntu1, 4.8.0-4ubuntu1), gcc-4.7:amd64 (4.7.3-1ubuntu1, 4.7.3-2ubuntu4), libgcc-4.7-dev:amd64 (4.7.3-1ubuntu1, 4.7.3-2ubuntu4), libquadmath0:amd64 (4.7.3-1ubuntu1, 4.8.0-4ubuntu1), libgcc1:amd64 (4.7.3-1ubuntu1, 4.8.0-4ubuntu1), gcc-4.7-base:amd64 (4.7.3-1ubuntu1, 4.7.3-2ubuntu4), libitm1:amd64 (4.7.3-1ubuntu1, 4.8.0-4ubuntu1), cpp-4.7:amd64 (4.7.3-1ubuntu1, 4.7.3-2ubuntu4)
End-Date: 2013-04-26  08:53:43

---

### Post by ventrical on 2013-04-26
> **grahammechanical said:**
> We will find that the extras repositories will be giving errors for weeks to come. Think about what is happening here. The Raring Repositories are now closed in the sense that the Raing code base will only receive the standard support updates. Otherwise users of 13.04 will find themselves using 13.10 in six months time and Raring will have become the daily updated kind of, sort of rolling release.

A new set of repositories have to be opened with the saucy urls and there has to be stuff to put at those locations. To start with it will be the Raring Code base. Then over time packages will be brought in that will turn the saucy development branch from a Raring code base into  a saucy code base. Oh, the images that come to mind as I use that word 'saucy!' 

There is nothing to update at the moment. There is nothing wrong with the instructions given by ventrical. The fault lies with us who are too eager (too saucy?). I will run those commands in my development Raring install on Monday or may be a bit later. Let the developers have a week-end with their families.

Edit: Perhaps we should look at the Saucy release schedule?

[https://wiki.ubuntu.com/SReleaseSchedule](https://wiki.ubuntu.com/SReleaseSchedule)

The tool chain does not get uploaded until 2nd May. Not much going on until after that.

[https://wiki.ubuntu.com/ToolChain](https://wiki.ubuntu.com/ToolChain)



Regards.

 My apologies if I had misled anyone. That was not my intent. So far I fried a hdd and busted 2 installs of raring (while updating to saucy)  on one machine. Thing is , I have so many surplus machines that smoking one here or there is not a problem. It gives me more space :)  As I had stated earlier , I am concerned about how fast Windows 8 is splash&dabbing the market right now.  It's a tall order to make match point there. As  they say in baseball... we got caught looking...

---

### Post by kevpan815 on 2013-04-26
> **grahammechanical said:**
> We will find that the extras repositories will be giving errors for weeks to come. Think about what is happening here. The Raring Repositories are now closed in the sense that the Raing code base will only receive the standard support updates. Otherwise users of 13.04 will find themselves using 13.10 in six months time and Raring will have become the daily updated kind of, sort of rolling release.

A new set of repositories have to be opened with the saucy urls and there has to be stuff to put at those locations. To start with it will be the Raring Code base. Then over time packages will be brought in that will turn the saucy development branch from a Raring code base into  a saucy code base. Oh, the images that come to mind as I use that word 'saucy!' 

There is nothing to update at the moment. There is nothing wrong with the instructions given by ventrical. The fault lies with us who are too eager (too saucy?). I will run those commands in my development Raring install on Monday or may be a bit later. Let the developers have a week-end with their families.

Edit: Perhaps we should look at the Saucy release schedule?

[https://wiki.ubuntu.com/SReleaseSchedule](https://wiki.ubuntu.com/SReleaseSchedule)

The tool chain does not get uploaded until 2nd May. Not much going on until after that.

[https://wiki.ubuntu.com/ToolChain](https://wiki.ubuntu.com/ToolChain)



Regards.

Hey, I have some news for you guys: 3 Updates just came through that were part of Saucy Main, NOT Saucy-Proposed!

---

### Post by ventrical on 2013-04-26
+1

```

Get:1 http://ca.archive.ubuntu.com/ubuntu/ saucy/main base-files i386 6.12ubuntu3 [68.8 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ saucy/main vim-tiny i386 2:7.3.547-7ubuntu1 [325 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ saucy/main vim-common i386 2:7.3.547-7ubuntu1 [83.0 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ saucy/main distro-info-data all 0.14 [4,184 B]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ saucy/main glib-networking-common all 2.36.1-0ubuntu2 [7,832 B]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ saucy/main glib-networking i386 2.36.1-0ubuntu2 [38.3 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ saucy/main glib-networking-services i386 2.36.1-0ubuntu2 [12.6 kB]
Fetched 540 kB in 2s (180 kB/s)

```

Held back..

```

The following packages have been kept back:
  cpp cpp-4.7 g++ g++-4.7 gcc gcc-4.7 gcc-4.7-base libgcc-4.7-dev libgcc1
  libgomp1 libitm1 libquadmath0 libstdc++6 libstdc++6-4.7-dev

```

  I just have a hunch that things are going to pick up faster than usual.. schedule or no schedule.

---

### Post by dino99 on 2013-04-26
> **kevpan815 said:**
> Hey, I have some news for you guys: 3 Updates just came through that were part of Saucy Main, NOT Saucy-Proposed!

all you got, i'm afraid, is only the raring packages tagged as saucy, no more as usual

---

### Post by kevpan815 on 2013-04-26
> **ventrical said:**
> +1

```

Get:1 http://ca.archive.ubuntu.com/ubuntu/ saucy/main base-files i386 6.12ubuntu3 [68.8 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ saucy/main vim-tiny i386 2:7.3.547-7ubuntu1 [325 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ saucy/main vim-common i386 2:7.3.547-7ubuntu1 [83.0 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ saucy/main distro-info-data all 0.14 [4,184 B]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ saucy/main glib-networking-common all 2.36.1-0ubuntu2 [7,832 B]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ saucy/main glib-networking i386 2.36.1-0ubuntu2 [38.3 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ saucy/main glib-networking-services i386 2.36.1-0ubuntu2 [12.6 kB]
Fetched 540 kB in 2s (180 kB/s)

```

Held back..

```

The following packages have been kept back:
  cpp cpp-4.7 g++ g++-4.7 gcc gcc-4.7 gcc-4.7-base libgcc-4.7-dev libgcc1
  libgomp1 libitm1 libquadmath0 libstdc++6 libstdc++6-4.7-dev

```

  I just have a hunch that things are going to pick up faster than usual.. schedule or no schedule.

They were't held back for me. I did a sudo update && sudo dist-upgrade and they installed just fine for me.

---

### Post by ventrical on 2013-04-26
I got 5 of them ... looks like it is taking some time to sync the repos to the different servers.

---

### Post by Mathor on 2013-04-26
> **kevpan815 said:**
> They were't held back for me. I did a sudo update && sudo dist-upgrade and they installed just fine for me.

Same here. I've had three sets of updates in the past 6 hours.

---

### Post by sgage on 2013-04-26
> **Mathor said:**
> Same here. I've had three sets of updates in the past 6 hours.

So have I, packages NOT updated in Raring.

---

### Post by ventrical on 2013-04-26
They are now being freely updated in synaptic.

---

### Post by craig10x on 2013-04-26
sgage...did you get any updates today in your 13.04 install? (the one that isn't converted to 13.10)  I think my software updater is working ok...it said that i was up to date after checking...i am just trying to make sure my updater is still working ok after my fail with trying to convert to saucy...my software sources are showing the correct raring stuff on them...

---

### Post by sgage on 2013-04-26
> **craig10x said:**
> sgage...did you get any updates today in your 13.04 install? (the one that isn't converted to 13.10)  I think my software updater is working ok...it said that i was up to date after checking...i am just trying to make sure my updater is still working ok after my fail with trying to convert to saucy...my software sources are showing the correct raring stuff on them...

No, none today in my "stock" Raring installation. Which is normal for the day after a release...

---

### Post by JMB74 on 2013-04-26
For the record, on a non updated raring install with the sources switched to saucy, and proposed NOT enabled, I now am offered.

> Calculating upgrade... Done
The following NEW packages will be installed
   gcc-4.8-base (4.8.0-4ubuntu1)
   gcc-4.8-base:i386 (4.8.0-4ubuntu1)
   libmpc3 (1.0.1-1)

The following packages will be upgraded:
   base-files (6.12ubuntu2 => 6.12ubuntu3)
   cpp-4.7 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   debootstrap (1.0.46ubuntu1 => 1.0.46ubuntu2)
   distro-info-data (0.13ubuntu0.1 => 0.14)
   g++-4.7 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   g++-4.7-multilib (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gcc-4.7 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gcc-4.7-base (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gcc-4.7-base:i386 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gcc-4.7-multilib (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gfortran-4.7 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   glib-networking (2.36.1-0ubuntu1 => 2.36.1-0ubuntu2)
   glib-networking:i386 (2.36.1-0ubuntu1 => 2.36.1-0ubuntu2)
   glib-networking-common (2.36.1-0ubuntu1 => 2.36.1-0ubuntu2)
   glib-networking-services (2.36.1-0ubuntu1 => 2.36.1-0ubuntu2)
   lib32gcc-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   lib32gcc1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32gomp1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32itm1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32quadmath0 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32stdc++6 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32stdc++6-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libgcc-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libgcc1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libgcc1:i386 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libgfortran-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libgfortran3 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libgomp1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libitm1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libquadmath0 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libstdc++6 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libstdc++6:i386 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libstdc++6-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libx32gcc-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libx32gcc1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32gomp1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32itm1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32quadmath0 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32stdc++6 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32stdc++6-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   rocs (4.10.2-0ubuntu1 => 4.10.2-0ubuntu2)
   vim (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
   vim-common (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
   vim-doc (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
   vim-runtime (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
   vim-tiny (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
46 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 48.3 MB/48.4 MB of archives.
After this operation, 734 kB of additional disk space will be used.

---

### Post by ventrical on 2013-04-26
> **craig10x said:**
> sgage...did you get any updates today in your 13.04 install? (the one that isn't converted to 13.10)  I think my software updater is working ok...it said that i was up to date after checking...i am just trying to make sure my updater is still working ok after my fail with trying to convert to saucy...my software sources are showing the correct raring stuff on them...

Here is my history log..

---

### Post by sgage on 2013-04-26
> **ventrical said:**
> Here is my history log..

Is that from a Raring or Saucy installation?

---

### Post by craig10x on 2013-04-26
Thanks sgage...i guess i am ok then... ;)
When i ran the updater it scanned and then said i was up to date...

I guess i will have to hold off for a while to see about switching to saucy...perhaps i could try the "gui method" in about a week to do the upgrade through the software updater...
I saw an article about doing using that method...
[http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/](http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/)

Probably would be best to try AFTER the first daily builds for 13.10 go up, right?

---

### Post by sgage on 2013-04-26
> **JMB74 said:**
> For the record, on a non updated raring install with the sources switched to saucy, and proposed NOT enabled, I now am offered.

That's pretty much the story here. I know that the full-on tool chain won't be loaded for a few days, but it's interesting to see the bits and pieces make their way into the system. I'm just jumping on the bandwagon this early for educational purposes, and if it all breaks hideously and irreparably, no matter - it's just an experimental setup. In fact, I fully expect it :KS

So, right now, saucy is essentially just raring with a few opening moves being made to prepare the ground...

---

### Post by kansasnoob on 2013-04-26
> **grahammechanical said:**
> We will find that the extras repositories will be giving errors for weeks to come. Think about what is happening here. The Raring Repositories are now closed in the sense that the Raing code base will only receive the standard support updates. Otherwise users of 13.04 will find themselves using 13.10 in six months time and Raring will have become the daily updated kind of, sort of rolling release.

A new set of repositories have to be opened with the saucy urls and there has to be stuff to put at those locations. To start with it will be the Raring Code base. Then over time packages will be brought in that will turn the saucy development branch from a Raring code base into  a saucy code base. Oh, the images that come to mind as I use that word 'saucy!' 

There is nothing to update at the moment. There is nothing wrong with the instructions given by ventrical. The fault lies with us who are too eager (too saucy?). I will run those commands in my development Raring install on Monday or may be a bit later. Let the developers have a week-end with their families.

Edit: Perhaps we should look at the Saucy release schedule?

[https://wiki.ubuntu.com/SReleaseSchedule](https://wiki.ubuntu.com/SReleaseSchedule)

The tool chain does not get uploaded until 2nd May. Not much going on until after that.

[https://wiki.ubuntu.com/ToolChain](https://wiki.ubuntu.com/ToolChain)



Regards.

+1! +1! +1!

Look at the release notes:

[https://wiki.ubuntu.com/SReleaseSchedule](https://wiki.ubuntu.com/SReleaseSchedule)

May 2nd; toolchain uploaded!

Look at your calendar!

---

### Post by sgage on 2013-04-26
> **kansasnoob said:**
> +1! +1! +1!

Look at the release notes:

[https://wiki.ubuntu.com/SReleaseSchedule](https://wiki.ubuntu.com/SReleaseSchedule)

May 2nd; toolchain uploaded!

Look at your calendar!

As I said above, I'm only checking out the process for educational purposes. Why so agitated about a few people trying to see it unfold? I've been doing this for years, am well familiar with the pacing, and have no expectations of anything real happening for some time. I won't be surprised or bothered if/when it blows up in my face. But I am curious to see the early days of how the repos populate with the new stuff and all. In a word, it's just fun. Please don't worry about it.

---

### Post by JMB74 on 2013-04-26
> **kansasnoob said:**
> +1! +1! +1!

Look at the release notes:

[https://wiki.ubuntu.com/SReleaseSchedule](https://wiki.ubuntu.com/SReleaseSchedule)

May 2nd; toolchain uploaded!

Look at your calendar!

For raring most of the toolchain and first updates went up waaaaaaay ahead of the provisional dates given on the release schedule.

Saucy even has it's first kernel upload already as part of it: [https://launchpad.net/ubuntu/saucy/+source/linux/3.9.0-0.1](https://launchpad.net/ubuntu/saucy/+source/linux/3.9.0-0.1)

so things are moving. Obviously not completely there, but they are moving.

---

### Post by kansasnoob on 2013-04-26
> **sgage said:**
> As I said above, I'm only checking out the process for educational purposes. **[COLOR="#FF0000"]Why so agitated[/COLOR]** about a few people trying to see it unfold? I've been doing this for years, am well familiar with the pacing, and have no expectations of anything real happening for some time. I won't be surprised or bothered if/when it blows up in my face. But I am curious to see the early days of how the repos populate with the new stuff and all. In a word, it's just fun. Please don't worry about it.

How do you consider my comments to reflect "agitation"?

I'm simply pointing out actual facts. The new toolchain has NOT yet been uploaded, how is pointing that out a sign of "agitation"?

---

### Post by sgage on 2013-04-26
> **kansasnoob said:**
> How do you consider my comments to reflect "agitation"?

I'm simply pointing out actual facts. The new toolchain has NOT yet been uploaded, how is pointing that out a sign of "agitation"?

How did I consider your comments to reflect "agitation"! I don't know! Perhaps it was the repeated "+1! +1! +1!". Or the "read your schedule!"  In short, I think it had something to do with your excited use of exclamation points! !!!

:-)  :-)  :-)

---

### Post by kevpan815 on 2013-04-26
> **sgage said:**
> As I said above, I'm only checking out the process for educational purposes. Why so agitated about a few people trying to see it unfold? I've been doing this for years, am well familiar with the pacing, and have no expectations of anything real happening for some time. I won't be surprised or bothered if/when it blows up in my face. But I am curious to see the early days of how the repos populate with the new stuff and all. In a word, it's just fun. Please don't worry about it.

My Mirror: The Argonne National Labratory, is Fully Up To Date with the latest Saucy-Proposed Archives. I should also note that I am doing all the Testing on my NON-Primary Systems at the moment and have been putting my systems to sleep rather than shutting them down. I should also note that Technically I consider my Sprint Apple IPhone 5 my Primary System since it's 6 GB Personal Hotspot provides the 4G LTE Data Connection to all of my other toys. As a result I Technically consider all of my Personal Computers as NON-Primary Systems, as I most often use my IPhone 5 to surf the Net.

---

### Post by ventrical on 2013-04-26
> **sgage said:**
> Is that from a Raring or Saucy installation?

Saucy with Raring security repos enabled.

ventrical@ventrical-PY028AA-ABA-A1106N:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Saucy Salamander (development branch)
Release:    13.10
Codename:    saucy
ventrical@ventrical-PY028AA-ABA-A1106N:~$

---

### Post by ventrical on 2013-04-26
> **sgage said:**
> As I said above, I'm only checking out the process for educational purposes. Why so agitated about a few people trying to see it unfold? I've been doing this for years, am well familiar with the pacing, and have no expectations of anything real happening for some time. I won't be surprised or bothered if/when it blows up in my face. But I am curious to see the early days of how the repos populate with the new stuff and all. In a word, it's just fun. Please don't worry about it.

+1

I mean that's why we are here in this echo (which will soon be renamed U+1)

It's always good to stay ahead of the curve, even if they are only vanilla and infrastructure base files. As far as I am concerned, in reference to Raring Ringtail Release, it's history.  I got to move past it.

---

### Post by kevpan815 on 2013-04-26
> **sgage said:**
> How did I consider your comments to reflect "agitation"! I don't know! Perhaps it was the repeated "+1! +1! +1!". Or the "read your schedule!"  In short, I think it had something to do with your excited use of exclamation points! !!!

:-)  :-)  :-)

I agree, some people here are sounding Alarm Bells for no particular reason at all. :-)

---

### Post by kevpan815 on 2013-04-26
[ATTACH=CONFIG]241816[/ATTACH]

---

### Post by ventrical on 2013-04-26
> **sgage said:**
> How did I consider your comments to reflect "agitation"! I don't know! Perhaps it was the repeated "+1! +1! +1!". Or the "read your schedule!"  In short, I think it had something to do with your excited use of exclamation points! !!!

:-)  :-)  :-)

  It used to be weeks before we could use :

lsb_release -a

To reflect the new cycle. This time it was up the next day after the end of a cycle release. I am all for being enthusiastic and excited about this new release. I'm not going to curb my enthusiasm. :)  Then it's no fun at all and we don't discover anything and we don't get to see our machines get borked.. :)

zzzzzzz   :)

---

### Post by ventrical on 2013-04-26
> **kevpan815 said:**
> [ATTACH=CONFIG]241816[/ATTACH]

You are an Ubuntu rockstar man ! :)

---

### Post by cflow on 2013-04-26
I just updated, "proposed" updates disabled. It looks like I'm now in too:

> 
~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="13.10, Saucy Salamander"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Saucy Salamander (development branch)"
VERSION_ID="13.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


I'm  not so much in a rush about updates, and I won't go overboard in the  bleeding edge PPA's and packages. But I do think Canonical knows that  the "rolling release" model has gotten popular enough in the linux  community that they might make the development branch stabler. The  success of my theory will be if my computer survives this release cycle  from start to finish.

I felt that the rolling release model is  the most daunting - but very idealized - model in the linux world. Many  linux users desire this model to point that they use Arch and other  distros regardless of the hours they have to maintain them. If Canonical  really thinks they can make their development release better and  stabler than those alternatives, this cycle will be judgment of that. Don't get me wrong though - I'm still here to test this new release nonetheless.

Just my thoughts...

---

### Post by grahammechanical on 2013-04-26
All this saucy talk has got me all of a dither. Before I knew it I was entering those 3 commands. I just could not help it. I don't know what came over me. :)

---

### Post by sgage on 2013-04-26
> **grahammechanical said:**
> All this saucy talk has got me all of a dither. Before I knew it I was entering those 3 commands. I just could not help it. I don't know what came over me. :)

Hey, you're only human. :KS

---

### Post by kevpan815 on 2013-04-26
> **ventrical said:**
> You are an Ubuntu rockstar man ! :)

Thank You Ventrical for those kind words. Most of the time people consider me a Pest due to my Mental Disorder, and the fact that I sometimes can NOT control my Temper, and other times Butt-In to things that are none of my Business.

i plan to test the first Milestone Mainline Kernel that comes out for Saucy as well.

---

### Post by Mathor on 2013-04-26
> **grahammechanical said:**
> All this saucy talk has got me all of a dither. Before I knew it I was entering those 3 commands. I just could not help it. I don't know what came over me. :)

Once I heard what it was called I couldn't help myself :)

---

### Post by ventrical on 2013-04-26
> **cflow said:**
> I just updated, "proposed" updates disabled. It looks like I'm now in too:



I'm  not so much in a rush about updates, and I won't go overboard in the  bleeding edge PPA's and packages. But I do think Canonical knows that  the "rolling release" model has gotten popular enough in the linux  community that they might make the development branch stabler. The  success of my theory will be if my computer survives this release cycle  from start to finish.

I felt that the rolling release model is  the most daunting - but very idealized - model in the linux world. Many  linux users desire this model to point that they use Arch and other  distros regardless of the hours they have to maintain them. If Canonical  really thinks they can make their development release better and  stabler than those alternatives, this cycle will be judgment of that. Don't get me wrong though - I'm still here to test this new release nonetheless.

Just my thoughts...

That's an excellent submission.

Thanks.

---

### Post by ventrical on 2013-04-26
> **grahammechanical said:**
> All this saucy talk has got me all of a dither. Before I knew it I was entering those 3 commands. I just could not help it. I don't know what came over me. :)
hehehahe .. I actually had a dream about salamanders last night. Geesh .. boy oh boy !! I'm telling ya .. :)

---

### Post by kansasnoob on 2013-04-26
> **sgage said:**
> How did I consider your comments to reflect "agitation"! I don't know! Perhaps it was the repeated "+1! +1! +1!". Or the "read your schedule!"  In short, I think it had something to do with your excited use of exclamation points! !!!

:-)  :-)  :-)

The three "+1's" were because *grahammechanical* made three great points.

And I did NOT say, "read your schedule"! I said, "Look at the release notes", which indicates that the toolchain comes up May 2nd followed by, "Look at your calendar", meaning that it's not yet May 2nd.

But if some of you want to be deluded thinking you're using an early Saucy just knock yourselves out. OTOH I'd ask what you were doing when a few of us were sweating blood testing the final iso images and upgrades?

---

### Post by ventrical on 2013-04-26
> **kansasnoob said:**
> The three "+1's" were because *grahammechanical* made three great points.

And I did NOT say, "read your schedule"! I said, "Look at the release notes", which indicates that the toolchain comes up May 2nd followed by, "Look at your calendar", meaning that it's not yet May 2nd.

But if some of you want to be deluded thinking you're using an early Saucy just knock yourselves out. OTOH I'd ask what you were doing when a few of us were sweating blood testing the final iso images and upgrades?


We were testing our hides off  and hanging out at q&a has never been proof to indicate otherwise.

---

### Post by deadflowr on 2013-04-26
> **grahammechanical said:**
> All this saucy talk has got me all of a dither. Before I knew it I was entering those 3 commands. I just could not help it. I don't know what came over me. :)

Saucy makes me think of sauce, which makes me think of food, which makes me hungry. And people do crazy things when they're hungry.

---

### Post by JMB74 on 2013-04-26
Most of the toolchain now in place I think. glibc and binutils were already at latest versions in raring if I recall, so no need for updates on those.

> Calculating upgrade... Done

The following NEW packages will be installed

   cpp-4.8 (4.8.0-4ubuntu1)
   g++-4.8 (4.8.0-4ubuntu1)
   g++-4.8-multilib (4.8.0-4ubuntu1)
   gcc-4.8 (4.8.0-4ubuntu1)
   gcc-4.8-base (4.8.0-4ubuntu1)
   gcc-4.8-base:i386 (4.8.0-4ubuntu1)
   gcc-4.8-multilib (4.8.0-4ubuntu1)
   gfortran-4.8 (4.8.0-4ubuntu1)
   lib32asan0 (4.8.0-4ubuntu1)
   lib32atomic1 (4.8.0-4ubuntu1)
   lib32gcc-4.8-dev (4.8.0-4ubuntu1)
   lib32stdc++-4.8-dev (4.8.0-4ubuntu1)
   libasan0 (4.8.0-4ubuntu1)
   libatomic1 (4.8.0-4ubuntu1)
   libcloog-isl4 (0.18.0-2)
   libgcc-4.8-dev (4.8.0-4ubuntu1)
   libgfortran-4.8-dev (4.8.0-4ubuntu1)
   libisl10 (0.11.1-2)
   libmpc3 (1.0.1-1)
   libstdc++-4.8-dev (4.8.0-4ubuntu1)
   libtsan0 (4.8.0-4ubuntu1)
   libx32asan0 (4.8.0-4ubuntu1)
   libx32atomic1 (4.8.0-4ubuntu1)
   libx32gcc-4.8-dev (4.8.0-4ubuntu1)
   libx32stdc++-4.8-dev (4.8.0-4ubuntu1)

The following packages will be upgraded:

   base-files (6.12ubuntu2 => 6.12ubuntu3)
   cpp (4.7.3-1ubuntu10 => 4.8.0-0ubuntu13)
   cpp-4.7 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   debootstrap (1.0.46ubuntu1 => 1.0.46ubuntu2)
   distro-info-data (0.13ubuntu0.1 => 0.14)
   g++ (4.7.3-1ubuntu10 => 4.8.0-0ubuntu13)
   g++-4.7 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   g++-4.7-multilib (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   g++-multilib (4.7.3-1ubuntu10 => 4.8.0-0ubuntu13)
   gcc (4.7.3-1ubuntu10 => 4.8.0-0ubuntu13)
   gcc-4.7 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gcc-4.7-base (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gcc-4.7-base:i386 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gcc-4.7-multilib (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   gcc-multilib (4.7.3-1ubuntu10 => 4.8.0-0ubuntu13)
   gfortran (4.7.3-1ubuntu10 => 4.8.0-0ubuntu13)
   gfortran-4.7 (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   glib-networking (2.36.1-0ubuntu1 => 2.36.1-0ubuntu2)
   glib-networking:i386 (2.36.1-0ubuntu1 => 2.36.1-0ubuntu2)
   glib-networking-common (2.36.1-0ubuntu1 => 2.36.1-0ubuntu2)
   glib-networking-services (2.36.1-0ubuntu1 => 2.36.1-0ubuntu2)
   lib32gcc-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   lib32gcc1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32gomp1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32itm1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32quadmath0 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32stdc++6 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   lib32stdc++6-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libgcc-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libgcc1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libgcc1:i386 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libgcj-common (4.7.3-1ubuntu10 => 4.7.3-1ubuntu13)
   libgfortran-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libgfortran3 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libgomp1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libitm1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libquadmath0 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libstdc++6 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libstdc++6:i386 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libstdc++6-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libx32gcc-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   libx32gcc1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32gomp1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32itm1 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32quadmath0 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32stdc++6 (4.7.3-1ubuntu1 => 4.8.0-4ubuntu1)
   libx32stdc++6-4.7-dev (4.7.3-1ubuntu1 => 4.7.3-2ubuntu4)
   rocs (4.10.2-0ubuntu1 => 4.10.2-0ubuntu2)
   vim (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
   vim-common (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
   vim-doc (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
   vim-runtime (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
   vim-tiny (7.3.547-6ubuntu5 => 7.3.547-7ubuntu1)
53 upgraded, 25 newly installed, 0 to remove and 0 not upgraded.



---

### Post by sgage on 2013-04-26
> **kansasnoob said:**
> The three "+1's" were because *grahammechanical* made three great points.

And I did NOT say, "read your schedule"! I said, "Look at the release notes", which indicates that the toolchain comes up May 2nd followed by, "Look at your calendar", meaning that it's not yet May 2nd.

But if some of you want to be deluded thinking you're using an early Saucy just knock yourselves out. OTOH I'd ask what you were doing when a few of us were sweating blood testing the final iso images and upgrades?

Umm... I was testing the final iso images and upgrades, so kindly lay off the holier-than-thou.

Actually, I must admit, you said "look at the release notes", with no exclamation, admirably. But then you went on to say, and I quote, cut and pasted no less:

"May 2nd; toolchain uploaded!

Look at your calendar!"

My point is in NO way changed or diminished. 

Nobody is deluded, and I think you might consider lightening up just a tad. You are not the only one who puts in long hours of testing, installing, testing, breaking, installing, etc. Some of us have been doing this for a long long time - in my case over 6 years (that's just Ubuntu - I've been using and doing my bit for Linux since 1997, been working with computers professionally since 1982) - and we just naturally become a bit silly and exuberant around launch time. Just let it slide - no harm done.

Finally, as has been pointed out, interesting stuff often happens before the official calendar dates. Indeed, it's already happening...

In the immortal words of Mr. Shuttleworth himself:

"And we&#8217;re saucy too &#8211; life&#8217;s too short to be stodgy or stilted. Our work is our play &#8211; we make amazing things for a huge audience, we find space for pretty much every flavour of interface and do it with style.

Happy release day everyone! Here&#8217;s to a super saucy cycle.

Please, enjoy the moment! :KS

---

### Post by JMB74 on 2013-04-26
Plenty of non toolchain new packages now going into saucy as well

Builds here: [https://launchpad.net/ubuntu/saucy/+builds?build_text=&build_state=all&arch_tag=amd64](https://launchpad.net/ubuntu/saucy/+builds?build_text=&build_state=all&arch_tag=amd64)

And from the changes list:

> 
[LIST]
[*][[ubuntu/saucy-proposed] linux 3.9.0-0.1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000039.html")  *Tim Gardner * 
[*][[ubuntu/saucy-proposed] yapgvb 1.2.3-0ubuntu10 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000045.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] xsd 3.3.0.1-1.3build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000050.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] wesnoth-1.10 1:1.10.6-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000042.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] widelands 1:17-3build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000048.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] vowpal-wabbit 6.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000043.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] vera++ 1.1.1-3build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000051.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] uhd 3.4.2-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000046.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] tmfs 3-2build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000041.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] schroot 1.6.5-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000049.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] referencer 1.1.6-2build3 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000047.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] rdkit 201203-3build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000054.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] quantlib 1.2.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000052.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] python-pgmagick 0.5.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000040.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] python-visual 1:5.12-1.5build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000053.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] python-demgengeo 0.99~bzr106-1build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000044.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] pytango 7.2.3-2build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000061.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] pyopencl 2012.1-1ubuntu5 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000056.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] pp-popularity-contest 1.0.5-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000065.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] polybori 0.8.3-1~exp1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000062.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] pentobi 1.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000067.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] pokerth 1.0-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000066.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] pdfcube 0.0.4-2build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000068.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] pcb2gcode 1.1.4-git20110915-1ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000055.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] ovito 0.9.5-2build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000057.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] orthanc 0.4.0-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000069.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] mkvtoolnix 6.1.0-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000064.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] openimageio 1.1.3+dfsg0-1ubuntu3 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000063.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] mididings 0~20120419~ds0-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000059.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] lyx 2.0.3-3build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000060.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] lightspark 0.7.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000058.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] lierolibre 0.5-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000079.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] libvigraimpex 1.9.0-0ubuntu3 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000072.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] licq 1.7.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000083.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] libtorrent-rasterbar 0.16.7-0ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000085.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] librcsb-core-wrapper 1.000-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000071.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] liborigin2 2:20110117-1build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000076.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] libmpikmeans 1.5-1build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000080.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] libgdf 0.1.2-2build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000084.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] libcolumbus 0.4.0daily13.04.16~13.04-0ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000081.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] laserboy 2012.11.11-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000073.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] libcmis 0.3.1-1ubuntu3 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000077.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] kig 4:4.10.2-0ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000070.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] kcollectd 0.9-2.1build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000074.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] k3d 0.8.0.2-18build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000078.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] innoextract 1.3-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000082.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] grive 0.2.0-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000075.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] gringo 3.0.4-4build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000092.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] glogg 0.9.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000095.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] fracplanet 0.4.0-3build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000097.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] evolvotron 0.6.2-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000086.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] fife 0.3.4-2build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000098.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] encfs 1.7.4-2.4build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000089.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] enblend-enfuse 4.0+dfsg-4ubuntu4 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000100.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] easystroke 0.5.99.2-0ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000094.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] ekiga 4.0.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000090.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] dssp 2.0.4-2build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000087.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] diet 2.8.0-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000091.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] cgal 4.0.2-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000099.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] cupt 2.5.9build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000096.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] cnrun 1.1.13-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000093.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] ceph 0.56.4-0ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000088.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] cclive 0.7.9-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000101.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] btag 1.1.3-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000110.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] bitcoin 0.8.1-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000108.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] bastet 0.43-2.1build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000107.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] barada-pam 0.5-3.1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000112.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] barry 0.18.3-5ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000104.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] avogadro 1.0.3-5ubuntu5 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000102.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] autodock-vina 1.1.2-2build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000111.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] asc 2.4.0.0-3build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000105.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] anytun 0.3.4-2build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000106.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] aqsis 1.8.1-3build2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000113.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] 0ad 0.0.13-1build1 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000103.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] akonadi 1.9.1-0ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000109.html")  *Dmitrijs Ledkovs * 
[*][[ubuntu/saucy-proposed] emacs-goodies-el 35.2+nmu1ubuntu2 (Accepted) ]("https://lists.ubuntu.com/archives/saucy-changes/2013-April/000114.html")  *Iain Lane * 
[/LIST]


---

### Post by Mathor on 2013-04-26
This is now my 10th set of updates in the past 12 hours. dist-upgrade is currently pushing me into Kernel 3.9. This should be interesting..

---

### Post by kevpan815 on 2013-04-26
> **craig10x said:**
> sgage...did you get any updates today in your 13.04 install? (the one that isn't converted to 13.10)  I think my software updater is working ok...it said that i was up to date after checking...i am just trying to make sure my updater is still working ok after my fail with trying to convert to saucy...my software sources are showing the correct raring stuff on them...

For Development Builds it is usually recommended that you use the Command Line in Terminal to update your Machine rather than using Software Updater which can also become Unstable once Ubuntu starts Applying Alpha/Beta Updates to it. By the way, my Machine has also received at least 3 different sets of Upgrades today.

I should also note that I am NOT using my computer's Primary OEM Hard Disk Drive for these Experiments. Instead, I am using a Retail 128 GB Crucial 2.5" M4 SSD (Solid State Drive) for these Experiments.

---

### Post by grahammechanical on 2013-04-26
The missing extras repositories (failed to get  error) stops Software Updater from working and also Software Sources/Software and Updates. But not the terminal and Synaptic. Nor does it stop Software Centre from installing applications. Information for those who are new to this.

---

### Post by ventrical on 2013-04-26
> **grahammechanical said:**
> The missing extras repositories (failed to get  error) stops Software Updater from working and also Software Sources/Software and Updates. But not the terminal and Synaptic. Nor does it stop Software Centre from installing applications. Information for those who are new to this.

I have this sort of endless loop on some installs with synaptic and I can't get back into the repos but it is still grabbing updates.

---

### Post by pnarciso on 2013-04-26
Does kernel 3.9 gets installed automatically, or do I have to install it manually? I see that 3.9 is available but I still have kernel 3.8 installed. And "linux-generic" package still points to 3.8.

---

### Post by sgage on 2013-04-26
> **pnarciso said:**
> Does kernel 3.9 gets installed automatically, or do I have to install it manually? I see that 3.9 is available but I still have kernel 3.8 installed. And "linux-generic" package still points to 3.8.

I think you may have to install it manually - kernel 3.x version bumps are treated as new packages, not as upgrades to kernel 3.x-1. That's why you can have different versions.

I'm not sure about that. I had already installed 3.9 from mainline. When I saw 3.9 available in the repos, I removed 3.9 (that I'd installed), but it didn't offer to install it, so I went ahead and installed it manually. All seems to be functioning nominally...

---

### Post by JMB74 on 2013-04-26
Major kernel version upgrades or ABI increases are installed automatically when a new linux-meta package is uploaded to the repos. i.e. the upgrade of that pulls in the new kernel version as a dependency on a dist-upgrade. 

Until a new matching linux-meta version is uploaded, you will have to manually select and install the newer kernel versions.

There is no new linux-meta package matching the 3.9 kernel yet, so manual upgrade/install is it.

---

### Post by sgage on 2013-04-26
> **JMB74 said:**
> Major kernel version upgrades or ABI increases are installed automatically when a new linux-meta package is uploaded to the repos. i.e. the upgrade of that pulls in the new kernel version as a dependency on a dist-upgrade. 

Until a new matching linux-meta version is uploaded, you will have to manually select and install the newer kernel versions.

There is no new linux-meta package matching the 3.9 kernel yet, so manual upgrade/install is it.

Thanks for the clarification.

---

### Post by pnarciso on 2013-04-26
> **JMB74 said:**
> Major kernel version upgrades or ABI increases are installed automatically when a new linux-meta package is uploaded to the repos. i.e. the upgrade of that pulls in the new kernel version as a dependency on a dist-upgrade. 

Until a new matching linux-meta version is uploaded, you will have to manually select and install the newer kernel versions.

There is no new linux-meta package matching the 3.9 kernel yet, so manual upgrade/install is it.

OK, I suspected that. Thanks for the confirmation.

---

### Post by kevpan815 on 2013-04-27
> **sgage said:**
> I think you may have to install it manually - kernel 3.x version bumps are treated as new packages, not as upgrades to kernel 3.x-1. That's why you can have different versions.

I'm not sure about that. I had already installed 3.9 from mainline. When I saw 3.9 available in the repos, I removed 3.9 (that I'd installed), but it didn't offer to install it, so I went ahead and installed it manually. All seems to be functioning nominally...

Unless I am mistaken, When 3.9.0.1 is available for Automatic Installation, it should still come on through even if you have the 3.9 RC8 Mainline Kernel installed. If you press a certain keyboard key at Startup, you will then be able to Boot to the Regular Kernel instead of the Mainline Kernel.

---

### Post by JMB74 on 2013-04-27
Yep. The mainline kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) are fine to be installed in parallel with the ubuntu builds in the main repos. A slightly different version numbering scheme ensures that they don't interfere with the installation each other.

---

### Post by serdotlinecho on 2013-04-27
Saucy cycle conundrum...

- Are we going to update gtk to 3.8 and follow gnome upstream?
- Or are we going to remove gtk/gnome apps(totem, eog, gnome-terminal, nautilus etc) and move to Qt/QML apps?
- Are we going to start testing Unity Next and Mir in this cycle?

---

### Post by roly33 on 2013-04-27
I'm in, but don't know how to get updates via the Terminal, if I enter **sudo apt-get update **it just says get then a number, but never shows any updates or looks like its installing.

not sure what I'm doing wrong?

[ATTACH=CONFIG]241842[/ATTACH][ATTACH=CONFIG]241843[/ATTACH]

Roland

---

### Post by jppr on 2013-04-27
Can you read OP and first post, there is... [B]sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list

sudo apt-get update && sudo apt-get dist-upgrade

... or open Synaptic and upgrade there your system...

---

### Post by deadflowr on 2013-04-27
> **roly33 said:**
> I'm in, but don't know how to get updates via the Terminal, if I enter **sudo apt-get update **it just says get then a number, but never shows any updates or looks like its installing.

apt-get update refresh the package listing, which tells the system these are the latest packages.
running apt-get upgrade, or apt-get dist-upgrade will download and install the updated packages.
Typically, it'll show you a list of packages that have updates, and a yes/no option if you don't want to install, or not.

There are other commands to look at in the man page
```
man apt-get
```

---

### Post by JMB74 on 2013-04-27
> **roly33 said:**
> I'm in, but don't know how to get updates via the Terminal, if I enter **sudo apt-get update **it just says get then a number, but never shows any updates or looks like its installing.

not sure what I'm doing wrong?

[ATTACH=CONFIG]241843[/ATTACH]Apart from large parts of the toolchain and a few other packages, 


Roland

Your second screenshot shows that you have already upgraded the base packages to saucy, otherwise it would still say "raring".

There may be nothing else to upgrade on your mirror as yet.

---

### Post by roly33 on 2013-04-27
> **deadflowr said:**
> apt-get update refresh the package listing, which tells the system these are the latest packages.
running apt-get upgrade, or apt-get dist-upgrade will download and install the updated packages.
Typically, it'll show you a list of packages that have updates, and a yes/no option if you don't want to install, or not.

There are other commands to look at in the man page
```
man apt-get
```


Thank's, looks like I'm fully up to date then.

Roland

---

### Post by JMB74 on 2013-04-27
You are already on saucy, so not much more to update at the moment.

---

### Post by serdotlinecho on 2013-04-27
> **deadflowr said:**
> Saucy makes me think of sauce, which makes me think of food, which makes me hungry. And people do crazy things when they're hungry.

Possibly, Mark Shuttleworth have been here before...:-\"
[URL="http://www.saucysalamander.com/"]
http://www.saucysalamander.com/[/URL]

---

### Post by pnarciso on 2013-04-27
Ubuntu kernel meta package is now pointing to 3.9, but it's not functional because linux-image-extra-3.9.0-0-generic is missing.

---

### Post by dino99 on 2013-04-27
Should be fixed with the coming final 3.9 kernel (not a big deal by the way, its only an issue with 1 meta-package)

---

### Post by sgage on 2013-04-27
> **pnarciso said:**
> Ubuntu kernel meta package is now pointing to 3.9, but it's not functional because linux-image-extra-3.9.0-0-generic is missing.

I don't think that's the issue - they are not using the image-extra package any more. The issue is the change from 3.9.0-0 to 3.9.0.0 (subtle, I know!). The meta package points to 3.9.0.0 vs 3.9.0-0, and its image package isn't there yet, at least not on my mirror.

---

### Post by pnarciso on 2013-04-27
> **sgage said:**
> I don't think that's the issue - they are not using the image-extra package any more. The issue is the change from 3.9.0-0 to 3.9.0.0 (subtle, I know!). The meta package points to 3.9.0.0 vs 3.9.0-0, and its image package isn't there yet, at least not on my mirror.

If you try to install linux-image-generic, there's a dependency error that points to linux-image-extra-3.9.0-0-generic, but that package is not available anymore so, it's weird.

---

### Post by sgage on 2013-04-27
> **pnarciso said:**
> If you try to install linux-image-generic, there's a dependency error that points to linux-image-extra-3.9.0-0-generic, but that package is not available anymore so, it's weird.

Wow, that is a bug in linux-image-generic, pure and simple. The version of the metapackage 3.0.0.1, but it points to a kernel version that's 3.9.0-0, and the -extra package at that. The 'extra' package has not been used for the last couple of rc's. Just a wrong entry in the metapackage, which I'm sure will get fixed quickly.

[edit: the linux-image-server and the pae metapackage both have the correct dependencies. But the appropriate actual image packages haven't propagaged yet, at least to my mirror...]

---

### Post by JMB74 on 2013-04-27
> **sgage said:**
> Wow, that is a bug in linux-image-generic, pure and simple. The version of the metapackage 3.0.0.1, but it points to a kernel version that's 3.9.0-0

That is how it should be. That is how meta packages for the kernels work; so they can pull in new kernel versions by dependency on a dist-upgrade of the meta pack packages. 

The x.x.x.x versus x.x.x-x version in the meta packages is deliberate in order to achieve that.

> **sgage said:**
> , and the -extra package at that. The 'extra' package has not been used for the last couple of rc's. Just a wrong entry in the metapackage, which I'm sure will get fixed quickly.

That is the error here. -extra packages are no longer being built, so are not needed in the meta package. There is one wrongly there in the last meta upload, but it can't upgrade as the -image-extra package it depends on isn't there in the actual kernel build.

---

### Post by sgage on 2013-04-27
> **JMB74 said:**
> That is how it should be. That is how meta packages for the kernels work; so they can pull in new kernel versions by dependency on a dist-upgrade of the meta pack packages. 

The x.x.x.x versus x.x.x-x version in the meta packages is deliberate in order to achieve that.



That is the error here. -extra packages are no longer being built, so are not needed in the meta package. There is one wrongly there in the last meta upload, but it can't upgrade as the -image-extra package it depends on isn't there in the actual kernel build.

I get it now. Just too many 0's and such for my tired old eyes :KS

---

### Post by ventrical on 2013-04-27
Wow.

---

### Post by Mathor on 2013-04-27
> **serdotlinecho said:**
> Saucy cycle conundrum...

- Are we going to update gtk to 3.8 and follow gnome upstream?
- Or are we going to remove gtk/gnome apps(totem, eog, gnome-terminal, nautilus etc) and move to Qt/QML apps?
- Are we going to start testing Unity Next and Mir in this cycle?

I would say yes to all of the following except removing gtk/gnome apps.

Ubuntu is not as deeply worried in putting all of its efforts into following Gnome completely upstream durring this cycle, but I'd imagine 3.8 is available before 13.10, especially because of the existance of Gnomebuntu 13.10.


In other news:
```
The following packages will be REMOVED:
  linux-generic
The following NEW packages will be installed:
  linux-headers-3.9.0-0 linux-headers-3.9.0-0-generic linux-image-3.9.0-0-generic
The following packages have been kept back:
  linux-image-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 3 newly installed, 1 to remove and 1 not upgraded.
Need to get 55.1 MB of archives.
After this operation, 237 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
]
```

In recent updates. Be careful!

---

### Post by ventrical on 2013-04-27
> **Mathor said:**
> I would say yes to all of the following except removing gtk/gnome apps.

Ubuntu is not as deeply worried in putting all of its efforts into following Gnome completely upstream durring this cycle, but I'd imagine 3.8 is available before 13.10, especially because of the existance of Gnomebuntu 13.10.


In other news:
```
The following packages will be REMOVED:
  linux-generic
The following NEW packages will be installed:
  linux-headers-3.9.0-0 linux-headers-3.9.0-0-generic linux-image-3.9.0-0-generic
The following packages have been kept back:
  linux-image-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 3 newly installed, 1 to remove and 1 not upgraded.
Need to get 55.1 MB of archives.
After this operation, 237 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
]
```

In recent updates. Be careful!


I just rolled with it and no problems so far.

---

### Post by craig10x on 2013-04-27
Hmmm...i wonder if might work better for me now if i tried to switch over my repos to saucy using the terminal commands...didn't work for me when i tried on thursday...but perhaps all the mirrors and packages weren't working 100% at that time...(what happened was mine wasn't changed and the updater simply reverted back to raring on the sources)...not sure if i should "chance" it...
And it has been mentioned here that trying it through the gui method is rather risky...

---

### Post by sgage on 2013-04-27
> **craig10x said:**
> Hmmm...i wonder if might work better for me now if i tried to switch over my repos to saucy using the terminal commands...didn't work for me when i tried on thursday...but perhaps all the mirrors and packages weren't working 100% at that time...(what happened was mine wasn't changed and the updater simply reverted back to raring on the sources)...not sure if i should "chance" it...
And it has been mentioned here that trying it through the gui method is rather risky...

If you try it, be sure to add the lines to Ubuntu.info, as described in a post from pnarciso on the first page of this thread. It didn't work properly for me until I did this, and worked fine afterwards.

Also, be sure your first upgrade is a dist-upgrade...

---

### Post by ventrical on 2013-04-27
> **craig10x said:**
> Hmmm...i wonder if might work better for me now if i tried to switch over my repos to saucy using the terminal commands...didn't work for me when i tried on thursday...but perhaps all the mirrors and packages weren't working 100% at that time...(what happened was mine wasn't changed and the updater simply reverted back to raring on the sources)...not sure if i should "chance" it...
And it has been mentioned here that trying it through the gui method is rather risky...

Please check out my sig.

Thanks

---

### Post by roly33 on 2013-04-27
I'm feeling left out, I'm setup for 13.10, but not getting any updates whatsoever & other posters seem to be getting updates.  What's the trick to getting updates?

Roland

---

### Post by rtalcott on 2013-04-27
Good question...I am not seeing the 3.9 kernel....or much else.
rt

---

### Post by Mathor on 2013-04-27
> **roly33 said:**
> I'm feeling left out, I'm setup for 13.10, but not getting any updates whatsoever & other posters seem to be getting updates.  What's the trick to getting updates?

Roland

Make sure you have your sources.list pointed to saucy. Then, whenever you want to check for updates do sudo apt-get update and sudo apt-get dist-upgrade. This will pull in the newest updates from saucy-proposed and saucy.

---

### Post by ventrical on 2013-04-27
> **Mathor said:**
> Make sure you have your sources.list pointed to saucy. Then, whenever you want to check for updates do sudo apt-get update and sudo apt-get dist-upgrade. This will pull in the newest updates from saucy-proposed and saucy.


And if this does not work, synaptic will.

---

### Post by ventrical on 2013-04-27
> **rtalcott said:**
> Good question...I am not seeing the 3.9 kernel....or much else.
rt


I will often run the terminal commands and not get updates but, as soon as I run synaptic, they are all there.

---

### Post by roly33 on 2013-04-27
> **Mathor said:**
> Make sure you have your sources.list pointed to saucy. Then, whenever you want to check for updates do sudo apt-get update and sudo apt-get dist-upgrade. This will pull in the newest updates from saucy-proposed and saucy.

I fixed it by switching on Saucy Proposed in Software & Updates and did sudo apt-get update & sudo apt-get dist-upgrade while I was away from the site & didn't get your reply.

But for some reason, possibly from when I was using Daily Build & Beta of 13.04 I'd got Saucy Proposed switched off.

Roland

---

### Post by roly33 on 2013-04-27
roughly how much of the updates come from the Proposed Repo over the Main Repo at this stage of development?

Roland

---

### Post by rtalcott on 2013-04-27
Been using synaptic!
I'll try again.

---

### Post by roly33 on 2013-04-27
As of 26 Minutes ago I can say that I've finally got the upgrade to 13.10 working with the 3.9 Kernel an to say that it's still a Release Candidate and coming from Saucy Proposed it feels pretty stable.

Roland

---

### Post by ventrical on 2013-04-27
> **rtalcott said:**
> Been using synaptic!
I'll try again.


 I noticed on some install that it will untic 'proposed' repos and they have to be enabled.

---

### Post by roly33 on 2013-04-27
I've got a strange one here.

when I do sudo apt-get update I get one update

[ATTACH=CONFIG]241872[/ATTACH]

But when I do a sudo apt-get dist-upgrade it says held back

[ATTACH=CONFIG]241874[/ATTACH]

anyone else got the same update?

Roland

---

### Post by rtalcott on 2013-04-27
Took a closer look and I think I made a mess....gotta do some cleaning up....not sure how I did it but I am the only "responsible" person here.

---

### Post by pnarciso on 2013-04-27
That meta package is buggy, that's the reason you can't upgrade.

---

### Post by cariboo on 2013-04-27
All the packages go into proposed until any problems have been solved, then they are moved to main. If you are subscribed to the [saucy-changes]("https://lists.ubuntu.com/mailman/listinfo/Saucy-changes") mailing list, you'll see what's coming.

---

### Post by serdotlinecho on 2013-04-27
> **roly33 said:**
> roughly how much of the updates come from the Proposed Repo over the Main Repo at this stage of development?

Roland

Hi, Roland. Bookmark this page :)
[URL="https://lists.ubuntu.com/archives/saucy-changes/"]
https://lists.ubuntu.com/archives/saucy-changes/[/URL]
[https://launchpad.net/ubuntu/saucy](https://launchpad.net/ubuntu/saucy)

---

### Post by serdotlinecho on 2013-04-28
I'm a bit late....

[IMG]http://ubuntuone.com/0YNOfQ2HVGwwzccuuEVRnt[/IMG]

---

### Post by roly33 on 2013-04-28
> **cariboo907 said:**
> All the packages go into proposed until any problems have been solved, then they are moved to main. If you are subscribed to the [saucy-changes]("https://lists.ubuntu.com/mailman/listinfo/Saucy-changes") mailing list, you'll see what's coming.

I subscribed to the saucy-changes mailing list as soon as I  started to get updates for Saucy.

I can't see it being long before Kernel 3.9.0 goes into the Main Repo as it's pretty stable, just need to sort the meta package out for it.

Roland

---

### Post by JMB74 on 2013-04-28
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2013-April/001036.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2013-April/001036.html)

> **Saucy Salamander now open for development**

Most cycles, we have a week of breathing room where we can flip all the switches in a coordinated fashion and open everything at exactly the same time, but this archive opening sees various members of the release, archive, and toolchain teams in transit all over the globe, so we'll stagger things a bit.  

In the next day or two, you should see a followup to this email from Matthias Klose doing his usual announcement of what has changed in the default toolchain, and Colin Watson turning on autosyncs from Debian. 
 Rather than wait until we're all awake at the same time, however, I'm unfreezing the archive this morning and declaring Saucy open for active development.  

Happy merging.  

On behalf of the Release Team,  Adam Conrad


---

### Post by ventrical on 2013-04-28
> **roly33 said:**
> I've got a strange one here.

when I do sudo apt-get update I get one update

[ATTACH=CONFIG]241872[/ATTACH]

But when I do a sudo apt-get dist-upgrade it says held back

[ATTACH=CONFIG]241874[/ATTACH]

anyone else got the same update?

Roland

 I had the same thing on one install but when I ran synaptic , all of the files were installed.

---

### Post by ventrical on 2013-04-28
> **rtalcott said:**
> Took a closer look and I think I made a mess....gotta do some cleaning up....not sure how I did it but I am the only "responsible" person here.

 I borked 2 installs and a hdd already :)  I just keep on rolling. On one install it was a virgin install and I changed sources.list over first then  :

sudo apt-get update
sudo apt-get upgrade

and then I installed synaptic package manager. The trick was to  open the 'proposed' repo first using 'software sources' from the Unity dash (before upgrade) and it will not untic the proposed repo after  upgrade.

---

### Post by ventrical on 2013-04-28
> **serdotlinecho said:**
> I'm a bit late....

[IMG]http://ubuntuone.com/0YNOfQ2HVGwwzccuuEVRnt[/IMG]


Yeah .. it seems like they are getting them in the UK first because it took a little while for the 3.9.x.-x kernel  to make here to Canada.

---

### Post by ventrical on 2013-04-28
> **JMB74 said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2013-April/001036.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2013-April/001036.html)

Yep .. read this.. makes perfect sense as per any anomolous behavior in the repos.

---

### Post by Elfy on 2013-04-28
> **ventrical said:**
> Yeah .. it seems like they are getting them in the UK first because it took a little while for the 3.9.x.-x kernel  to make here to Canada.

Not seeing it here, or at least not an hour or so ago.

Not sure what's going on.

---

### Post by rtalcott on 2013-04-28
What am I doing wrong?  Help!

Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/saucy/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/saucy/main/source/Sources)  404  Not Found [IP: 91.189.88.33 80]

Is the Ubuntu.info file supposed to get updated with a set of Saucy entries?  Mine has none...
rt

---

### Post by lonniehenry on 2013-04-28
No saucy extras yet.  Go into sources and change it back to raring for a while.

---

### Post by serdotlinecho on 2013-04-28
> **rtalcott said:**
> What am I doing wrong?  Help!

Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/saucy/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/saucy/main/source/Sources)  404  Not Found [IP: 91.189.88.33 80]

Is the Ubuntu.info file supposed to get updated with a set of Saucy entries?  Mine has none...
rt

Not yet for saucy, you can check here:

[IMG]http://ubuntuone.com/2WyQKRVRtkFp5TW8XmzRsE[/IMG]

---

### Post by Elfy on 2013-04-28
> **lonniehenry said:**
> No saucy extras yet.  Go into sources and change it back to raring for a while.

IF you can get software sources to work - if not do it the easy way and edit sources.list :)

---

### Post by roly33 on 2013-04-28
New updates coming through now

[ATTACH=CONFIG]241920[/ATTACH] [ATTACH=CONFIG]241921[/ATTACH]

Roland

---

### Post by ventrical on 2013-04-28
> **Elfy said:**
> Not seeing it here, or at least not an hour or so ago.

Not sure what's going on.


Are you in Canada?

---

### Post by Elfy on 2013-04-28
Nope, I'm about 100 miles from the main servers if they're in London.

---

### Post by ventrical on 2013-04-28
> **Elfy said:**
> Nope, I'm about 100 miles from the main servers if they're in London.


Oy. My mistake. I thought the UK was first on the list.

---

### Post by serdotlinecho on 2013-04-28
63 packages for me and some systemd stuff keep coming too :)

[IMG]http://i.imgur.com/qGiNFtP.png[/IMG]

---

### Post by serdotlinecho on 2013-04-28
Saucy is now using systemd-logind.

[IMG]http://i.imgur.com/iq41hlQ.png[/IMG]

---

### Post by roly33 on 2013-04-29
65 updates for me just now.

[ATTACH=CONFIG]241945[/ATTACH]

the push to 13.05 seems well under way.

Roland

---

### Post by roly33 on 2013-04-29
> **Elfy said:**
> Nope, I'm about 100 miles from the main servers if they're in London.

> **ventrical said:**
> Oy. My mistake. I thought the UK was first on the list.

I've been getting updates here in the UK since Friday or Saturday using [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)

Roland

---

### Post by JMB74 on 2013-04-29
> **pnarciso said:**
> That meta package is buggy, that's the reason you can't upgrade.

Looks like they are going back to producing the -extra image packages rather than the single combined one.

That will fix the issue that way.

[https://launchpad.net/ubuntu/saucy/+source/linux/3.9.0-0.2](https://launchpad.net/ubuntu/saucy/+source/linux/3.9.0-0.2)

---

### Post by sgage on 2013-04-29
> **JMB74 said:**
> Looks like they are going back to producing the -extra image packages rather than the single combined one.

That will fix the issue that way.

[https://launchpad.net/ubuntu/saucy/+source/linux/3.9.0-0.2](https://launchpad.net/ubuntu/saucy/+source/linux/3.9.0-0.2)

I wonder why they went back to the 'extra' packaging. Anyway, it seems to have been successfully built, and ought to be in the repos soon...

---

### Post by ventrical on 2013-04-29
> **sgage said:**
> I wonder why they went back to the 'extra' packaging. Anyway, it seems to have been successfully built, and ought to be in the repos soon...


The following NEW packages will be installed:
  linux-image-extra-3.9.0-0-generic
The following packages will be upgraded:
  linux-headers-3.9.0-0 linux-headers-3.9.0-0-generic
  linux-image-3.9.0-0-generic linux-image-generic linux-libc-dev
5 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 57.6 MB of archives.
After this operation, 2,477 kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by sgage on 2013-04-29
> **ventrical said:**
> The following NEW packages will be installed:
  linux-image-extra-3.9.0-0-generic
The following packages will be upgraded:
  linux-headers-3.9.0-0 linux-headers-3.9.0-0-generic
  linux-image-3.9.0-0-generic linux-image-generic linux-libc-dev
5 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 57.6 MB of archives.
After this operation, 2,477 kB of additional disk space will be used.
Do you want to continue [Y/n]?

I'm all updated, too. Good to have that all sorted out...

---

### Post by ventrical on 2013-04-29
Next! ;)

---

### Post by Elfy on 2013-04-29
> **ventrical said:**
> Next! ;)

Is to start again - something's obviously up here :)

---

### Post by ventrical on 2013-04-29
> **Elfy said:**
> Is to start again - something's obviously up here :)

So far I have 2 solid installs but borked 3 already .. so I have to start on those hdds from scratch. (My mistake - I swapped them out from a nVidia based to ATi base and it borked Unity)

I also had problems with getting the updates, so, on a new install of RR,  I changed the sources list first then :
sudo apt-get update
sudo apt-get dist-upgrade

!!HardReboot!!

Ctrl+Alt+F1

sudo apt-get install synaptic

(this will give you the one chance to make sure the repos are set to proposed if you want to use synaptic) because the sources.list  seems to be blocking one of the saucy proposed repos if it is not just set right or if there is a raring repo in there. It gets pretty funky for some reason.

Basically the hard reboot is required to get some of the updates. Restarting or logging off from GUI will not reset whatever it is that has to be reset (it appears).

Persistence will pay off :)

---

### Post by sammiev on 2013-04-29
I'm in once again. :)

sam@sam-L650:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="13.10, Saucy Salamander"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Saucy Salamander (development branch)"
VERSION_ID="13.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

---

### Post by serdotlinecho on 2013-04-29
\\:D/

```
The following NEW packages will be installed: 
  linux-image-extra-3.9.0-0-generic (3.9.0-0.2)
The following packages will be upgraded:
   accountsservice (0.6.29-1ubuntu8 => 0.6.29-1ubuntu9)
   dbus (1.6.8-1ubuntu7 => 1.6.8-1ubuntu8)
   dbus-x11 (1.6.8-1ubuntu7 => 1.6.8-1ubuntu8)
   gnome-control-center (3.6.3-0ubuntu24 => 3.6.3-0ubuntu25)
   gnome-control-center-data (3.6.3-0ubuntu24 => 3.6.3-0ubuntu25)
   gnome-orca (3.8.0-0ubuntu1 => 3.8.1-0ubuntu1)
   gnome-screensaver (3.6.1-0ubuntu3 => 3.6.1-0ubuntu4)
   gnome-session (3.6.2-0ubuntu5 => 3.6.2-0ubuntu6)
   gnome-session-bin (3.6.2-0ubuntu5 => 3.6.2-0ubuntu6)
   gnome-session-common (3.6.2-0ubuntu5 => 3.6.2-0ubuntu6)
   gnome-settings-daemon (3.6.4-0ubuntu8 => 3.6.4-0ubuntu9)
   gnome-system-monitor (3.8.0-0ubuntu1 => 3.8.0-0ubuntu2)
   libaccountsservice0 (0.6.29-1ubuntu8 => 0.6.29-1ubuntu9)
   libdbus-1-3 (1.6.8-1ubuntu7 => 1.6.8-1ubuntu8)
   libgnome-control-center1 (3.6.3-0ubuntu24 => 3.6.3-0ubuntu25)
   libpolkit-agent-1-0 (0.105-1ubuntu2 => 0.105-1ubuntu3)
   libpolkit-backend-1-0 (0.105-1ubuntu2 => 0.105-1ubuntu3)
   libpolkit-gobject-1-0 (0.105-1ubuntu2 => 0.105-1ubuntu3)
   libpulse-mainloop-glib0 (3.0-0ubuntu6 => 3.0-0ubuntu7)
   libpulse0 (3.0-0ubuntu6 => 3.0-0ubuntu7)
   libpulsedsp (3.0-0ubuntu6 => 3.0-0ubuntu7)
   libtalloc2 (2.0.7+git20120207-1ubuntu1 => 2.0.8-0.1)
   libupower-glib1 (0.9.20-1 => 0.9.20-1ubuntu1)
   libwireshark-data (1.8.2-5 => 1.8.6-3)
   libwireshark2 (1.8.2-5 => 1.8.6-3)
   libwiretap2 (1.8.2-5 => 1.8.6-3)
   libwsutil2 (1.8.2-5 => 1.8.6-3)
   libzvbi-common (0.2.33-6 => 0.2.33-7)
   libzvbi0 (0.2.33-6 => 0.2.33-7)
   linux-headers-3.9.0-0 (3.9.0-0.1 => 3.9.0-0.2)
   linux-headers-3.9.0-0-generic (3.9.0-0.1 => 3.9.0-0.2)
   linux-image-3.9.0-0-generic (3.9.0-0.1 => 3.9.0-0.2)
   linux-image-generic (3.8.0.19.35 => 3.9.0.0.1)
   linux-libc-dev (3.9.0-0.1 => 3.9.0-0.2)
   policykit-1 (0.105-1ubuntu2 => 0.105-1ubuntu3)
   pulseaudio (3.0-0ubuntu6 => 3.0-0ubuntu7)
   pulseaudio-module-bluetooth (3.0-0ubuntu6 => 3.0-0ubuntu7)
   pulseaudio-module-x11 (3.0-0ubuntu6 => 3.0-0ubuntu7)
   pulseaudio-utils (3.0-0ubuntu6 => 3.0-0ubuntu7)
   python3-distupgrade (0.192.10 => 0.193)
   tshark (1.8.2-5 => 1.8.6-3)
   ubuntu-release-upgrader-core (0.192.10 => 0.193)
   upower (0.9.20-1 => 0.9.20-1ubuntu1)
   whois (5.0.20ubuntu1 => 5.0.24)
   wireshark-common (1.8.2-5 => 1.8.6-3)
   zip (3.0-6ubuntu1 => 3.0-7)
46 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.4 MB of archives.
After this operation, 2,637 kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by Mathor on 2013-04-30
3.9 works pretty well for my hardware

---

### Post by Elfy on 2013-04-30
> **Elfy said:**
> Not seeing it here, or at least not an hour or so ago.

Not sure what's going on.

Well that took it's time...

Linux hob-smaug 3.9.0-0-generic #3-Ubuntu SMP Mon Apr 29 23:13:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

working fine here.

---

### Post by JonPaul on 2013-04-30
Ouch - that last kernel upgrade has messed my video, no WiFi and extremely slow response. Back to 3.8 kernel for a while....

---

### Post by infectedorganism on 2013-04-30
I am new to running the development branch and was wondering if it was typical to accept the pre-released updates; in this case, saucy-proposed?

---

### Post by dino99 on 2013-04-30
> **infectedorganism said:**
> I am new to running the development branch and was wondering if it was typical to accept the pre-released updates; in this case, saucy-proposed?

as you says "i am new" then its quite scary for you to enable "proposed" repo if you fail into trouble; better to set it off and only wait for these packages landing into "main" repo (likely a few days only), and get a safer/stable system.

---

### Post by infectedorganism on 2013-04-30
> **dino99 said:**
> as you says "i am new" then its quite scary for you to enable "proposed" repo if you fail into trouble; better to set it off and only wait for these packages landing into "main" repo (likely a few days only), and get a safer/stable system.

Indeed. While I am not afraid to run into some problems, I will heed your advice and leave the "proposed" repo disabled. Thanks.

---

### Post by serdotlinecho on 2013-04-30
saucy-proposed enabled. \\:D/

```
The following NEW packages will be installed:   
libpackagekit-glib2-16 (0.8.7-2ubuntu1)
The following packages will be upgraded:
   acpi-support (0.141 => 0.142)
   apport (2.9.2-0ubuntu8 => 2.10-0ubuntu1)
   apport-gtk (2.9.2-0ubuntu8 => 2.10-0ubuntu1)
   bsdmainutils (9.0.4ubuntu3 => 9.0.4ubuntu4)
   colord (0.1.30-0ubuntu3 => 0.1.31-1)
   cups-browsed (1.0.34-0ubuntu1 => 1.0.34-0ubuntu2)
   cups-filters (1.0.34-0ubuntu1 => 1.0.34-0ubuntu2)
   freerdp-x11 (1.0.1-2ubuntu1 => 1.0.2-1ubuntu1)
   gir1.2-gudev-1.0 (198-0ubuntu12 => 202-0ubuntu3)
   gir1.2-packagekitglib-1.0 (0.7.6-3ubuntu1 => 0.8.7-2ubuntu1)
   hdparm (9.43-1ubuntu1 => 9.43-1ubuntu2)
   libboost-date-time1.53.0 (1.53.0-3ubuntu1 => 1.53.0-4ubuntu1)
   libclucene-contribs1 (2.3.3.4-2 => 2.3.3.4-2build1)
   libclucene-core1 (2.3.3.4-2 => 2.3.3.4-2build1)
   libcolord1 (0.1.30-0ubuntu3 => 0.1.31-1)
   libcolorhug1 (0.1.30-0ubuntu3 => 0.1.31-1)
   libcupsfilters1 (1.0.34-0ubuntu1 => 1.0.34-0ubuntu2)
   libfontembed1 (1.0.34-0ubuntu1 => 1.0.34-0ubuntu2)
   libfreerdp-plugins-standard (1.0.1-2ubuntu1 => 1.0.2-1ubuntu1)
   libfreerdp1 (1.0.1-2ubuntu1 => 1.0.2-1ubuntu1)
   libgudev-1.0-0 (198-0ubuntu12 => 202-0ubuntu3)
   libpam-systemd (198-0ubuntu12 => 202-0ubuntu3)
   libsystemd-daemon0 (198-0ubuntu12 => 202-0ubuntu3)
   libsystemd-login0 (198-0ubuntu12 => 202-0ubuntu3)
   libudev1 (198-0ubuntu12 => 202-0ubuntu3)
   lintian (2.5.11ubuntu13 => 2.5.11ubuntu14)
   linux-headers-3.9.0-0 (3.9.0-0.2 => 3.9.0-0.3)
   linux-headers-3.9.0-0-generic (3.9.0-0.2 => 3.9.0-0.3)
   linux-image-3.9.0-0-generic (3.9.0-0.2 => 3.9.0-0.3)
   linux-image-extra-3.9.0-0-generic (3.9.0-0.2 => 3.9.0-0.3)
   linux-libc-dev (3.9.0-0.2 => 3.9.0-0.3)
   python-apt (0.8.8ubuntu6 => 0.8.8.2ubuntu1)
   python-apt-common (0.8.8ubuntu6 => 0.8.8.2ubuntu1)
   python3-apport (2.9.2-0ubuntu8 => 2.10-0ubuntu1)
   python3-apt (0.8.8ubuntu6 => 0.8.8.2ubuntu1)
   python3-distupgrade (0.193 => 0.194)
   python3-problem-report (2.9.2-0ubuntu8 => 2.10-0ubuntu1)
   systemd-services (198-0ubuntu12 => 202-0ubuntu3)
   ubuntu-release-upgrader-core (0.193 => 0.194)
   udev (175-0ubuntu26 => 175-0ubuntu27)
   update-notifier-common (0.134 => 0.135)
41 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 62.4 MB/62.4 MB of archives.
After this operation, 418 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
```

---

### Post by ventrical on 2013-05-01
> **serdotlinecho said:**
> saucy-proposed enabled. \\:D/

```
The following NEW packages will be installed:   
libpackagekit-glib2-16 (0.8.7-2ubuntu1)
The following packages will be upgraded:
   acpi-support (0.141 => 0.142)
   apport (2.9.2-0ubuntu8 => 2.10-0ubuntu1)
   apport-gtk (2.9.2-0ubuntu8 => 2.10-0ubuntu1)
   bsdmainutils (9.0.4ubuntu3 => 9.0.4ubuntu4)
   colord (0.1.30-0ubuntu3 => 0.1.31-1)
   cups-browsed (1.0.34-0ubuntu1 => 1.0.34-0ubuntu2)
   cups-filters (1.0.34-0ubuntu1 => 1.0.34-0ubuntu2)
   freerdp-x11 (1.0.1-2ubuntu1 => 1.0.2-1ubuntu1)
   gir1.2-gudev-1.0 (198-0ubuntu12 => 202-0ubuntu3)
   gir1.2-packagekitglib-1.0 (0.7.6-3ubuntu1 => 0.8.7-2ubuntu1)
   hdparm (9.43-1ubuntu1 => 9.43-1ubuntu2)
   libboost-date-time1.53.0 (1.53.0-3ubuntu1 => 1.53.0-4ubuntu1)
   libclucene-contribs1 (2.3.3.4-2 => 2.3.3.4-2build1)
   libclucene-core1 (2.3.3.4-2 => 2.3.3.4-2build1)
   libcolord1 (0.1.30-0ubuntu3 => 0.1.31-1)
   libcolorhug1 (0.1.30-0ubuntu3 => 0.1.31-1)
   libcupsfilters1 (1.0.34-0ubuntu1 => 1.0.34-0ubuntu2)
   libfontembed1 (1.0.34-0ubuntu1 => 1.0.34-0ubuntu2)
   libfreerdp-plugins-standard (1.0.1-2ubuntu1 => 1.0.2-1ubuntu1)
   libfreerdp1 (1.0.1-2ubuntu1 => 1.0.2-1ubuntu1)
   libgudev-1.0-0 (198-0ubuntu12 => 202-0ubuntu3)
   libpam-systemd (198-0ubuntu12 => 202-0ubuntu3)
   libsystemd-daemon0 (198-0ubuntu12 => 202-0ubuntu3)
   libsystemd-login0 (198-0ubuntu12 => 202-0ubuntu3)
   libudev1 (198-0ubuntu12 => 202-0ubuntu3)
   lintian (2.5.11ubuntu13 => 2.5.11ubuntu14)
   linux-headers-3.9.0-0 (3.9.0-0.2 => 3.9.0-0.3)
   linux-headers-3.9.0-0-generic (3.9.0-0.2 => 3.9.0-0.3)
   linux-image-3.9.0-0-generic (3.9.0-0.2 => 3.9.0-0.3)
   linux-image-extra-3.9.0-0-generic (3.9.0-0.2 => 3.9.0-0.3)
   linux-libc-dev (3.9.0-0.2 => 3.9.0-0.3)
   python-apt (0.8.8ubuntu6 => 0.8.8.2ubuntu1)
   python-apt-common (0.8.8ubuntu6 => 0.8.8.2ubuntu1)
   python3-apport (2.9.2-0ubuntu8 => 2.10-0ubuntu1)
   python3-apt (0.8.8ubuntu6 => 0.8.8.2ubuntu1)
   python3-distupgrade (0.193 => 0.194)
   python3-problem-report (2.9.2-0ubuntu8 => 2.10-0ubuntu1)
   systemd-services (198-0ubuntu12 => 202-0ubuntu3)
   ubuntu-release-upgrader-core (0.193 => 0.194)
   udev (175-0ubuntu26 => 175-0ubuntu27)
   update-notifier-common (0.134 => 0.135)
41 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 62.4 MB/62.4 MB of archives.
After this operation, 418 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
```


It's really 'rolling' along nicely :)

---

### Post by kevpan815 on 2013-05-01
For those of you who have NOT noticed: It's still only May 1st (at least here in the United States of America) and already several Updates have already been Pushed Though on Saucy Main that are NOT being Pushed Through on Raring Main. I think that the Tool-Chain actually Started going up on Early Monday Morning (Chicago Time). It never hurts to at least try out those 3 commands! :-)

---

### Post by serdotlinecho on 2013-05-01
> **ventrical said:**
> It's really 'rolling' along nicely :)

```
The following packages will be upgraded:   
   cpp-4.8 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   g++-4.8 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   gcc-4.8 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   gcc-4.8-base (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   gir1.2-gudev-1.0 (202-0ubuntu3 => 202-0ubuntu4)
   gir1.2-soup-2.4 (2.40.3-0ubuntu1 => 2.42.0-1)
   gnome-screensaver (3.6.1-0ubuntu4 => 3.6.1-0ubuntu5)
   libasan0 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libatomic1 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libgcc-4.8-dev (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libgcc1 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libgomp1 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libgudev-1.0-0 (202-0ubuntu3 => 202-0ubuntu4)
   libharfbuzz0 (0.9.13-1 => 0.9.16-1)
   libitm1 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libpam-systemd (202-0ubuntu3 => 202-0ubuntu4)
   libpolkit-agent-1-0 (0.105-1ubuntu3 => 0.105-3ubuntu1)
   libpolkit-backend-1-0 (0.105-1ubuntu3 => 0.105-3ubuntu1)
   libpolkit-gobject-1-0 (0.105-1ubuntu3 => 0.105-3ubuntu1)
   libquadmath0 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libsoup-gnome2.4-1 (2.40.3-0ubuntu1 => 2.42.0-1)
   libsoup2.4-1 (2.40.3-0ubuntu1 => 2.42.0-1)
   libstdc++-4.8-dev (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libstdc++6 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libsystemd-daemon0 (202-0ubuntu3 => 202-0ubuntu4)
   libsystemd-login0 (202-0ubuntu3 => 202-0ubuntu4)
   libudev1 (202-0ubuntu3 => 202-0ubuntu4)
   policykit-1 (0.105-1ubuntu3 => 0.105-3ubuntu1)
   python-gi (3.8.0-2 => 3.9.1-0ubuntu1)
   python-gi-cairo (3.8.0-2 => 3.9.1-0ubuntu1)
   python-gobject (3.8.0-2 => 3.9.1-0ubuntu1)
   python3-gi (3.8.0-2 => 3.9.1-0ubuntu1)
   python3-gi-cairo (3.8.0-2 => 3.9.1-0ubuntu1)
   systemd-services (202-0ubuntu3 => 202-0ubuntu4)
   telepathy-idle (0.1.15-1 => 0.1.16-1)
35 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.5 MB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
```

---

### Post by kevpan815 on 2013-05-01
> **infectedorganism said:**
> I am new to running the development branch and was wondering if it was typical to accept the pre-released updates; in this case, saucy-proposed?

Saucy-Proposed: NOT a good idea, unless you are prepared to replace your computer at your own expense if something goes wrong!

---

### Post by kevpan815 on 2013-05-01
> **serdotlinecho said:**
> ```
The following packages will be upgraded:   
   cpp-4.8 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   g++-4.8 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   gcc-4.8 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   gcc-4.8-base (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   gir1.2-gudev-1.0 (202-0ubuntu3 => 202-0ubuntu4)
   gir1.2-soup-2.4 (2.40.3-0ubuntu1 => 2.42.0-1)
   gnome-screensaver (3.6.1-0ubuntu4 => 3.6.1-0ubuntu5)
   libasan0 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libatomic1 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libgcc-4.8-dev (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libgcc1 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libgomp1 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libgudev-1.0-0 (202-0ubuntu3 => 202-0ubuntu4)
   libharfbuzz0 (0.9.13-1 => 0.9.16-1)
   libitm1 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libpam-systemd (202-0ubuntu3 => 202-0ubuntu4)
   libpolkit-agent-1-0 (0.105-1ubuntu3 => 0.105-3ubuntu1)
   libpolkit-backend-1-0 (0.105-1ubuntu3 => 0.105-3ubuntu1)
   libpolkit-gobject-1-0 (0.105-1ubuntu3 => 0.105-3ubuntu1)
   libquadmath0 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libsoup-gnome2.4-1 (2.40.3-0ubuntu1 => 2.42.0-1)
   libsoup2.4-1 (2.40.3-0ubuntu1 => 2.42.0-1)
   libstdc++-4.8-dev (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libstdc++6 (4.8.0-4ubuntu2 => 4.8.0-4ubuntu3)
   libsystemd-daemon0 (202-0ubuntu3 => 202-0ubuntu4)
   libsystemd-login0 (202-0ubuntu3 => 202-0ubuntu4)
   libudev1 (202-0ubuntu3 => 202-0ubuntu4)
   policykit-1 (0.105-1ubuntu3 => 0.105-3ubuntu1)
   python-gi (3.8.0-2 => 3.9.1-0ubuntu1)
   python-gi-cairo (3.8.0-2 => 3.9.1-0ubuntu1)
   python-gobject (3.8.0-2 => 3.9.1-0ubuntu1)
   python3-gi (3.8.0-2 => 3.9.1-0ubuntu1)
   python3-gi-cairo (3.8.0-2 => 3.9.1-0ubuntu1)
   systemd-services (202-0ubuntu3 => 202-0ubuntu4)
   telepathy-idle (0.1.15-1 => 0.1.16-1)
35 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.5 MB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
```

After that little Reboot Problem followed by a Major Problem with a 100% Full Boot Folder that required a Clean Install of 13.10, I have finally decided to throw the White Flag and leave Saucy-Proposed Disabled! Just FYI.

---

### Post by ventrical on 2013-05-02
I got a Plymouth blip and freeze but just used Ctrl+Alt+F1 and:

sudo service lightdm restart

and it came right back up.

Also , (on this install) I had formatted it with btrfs file format and installed"

sudo apt-get install apt-btrfs-snapshot

before I did the upgrade . Whew !! :) That means I can roll back to the previous state.

---

### Post by kevpan815 on 2013-05-02
What exactly is Plymoth? I am not all that knowledgeable in Ubuntu Coding Language, as I used to be a 100% Microsoft Windows Computer Nerd, but Windows Me, Windows Vista, and now Windows 8 has changed all that, I now only use Windows 8 when I need to Update my Apple IPhone 5. :-)

---

### Post by ventrical on 2013-05-02
> **kevpan815 said:**
> What exactly is Plymoth? I am not all that knowledgeable in Ubuntu Coding Language, as I used to be a 100% Microsoft Windows Computer Nerd, but Windows Me, Windows Vista, and now Windows 8 has changed all that, I now only use Windows 8 when I need to Update my Apple IPhone 5. :-)


That is the load up routine between exiting grub-bootloader and executing lightdm. Rather than have verbose script we get the 'Ubuntu' with the purple screen while the kernel and lighdm (or other) are loading. A 'plymouth freeze' without a verbose error would be equivalent to a kernel panic or lock up.

I also experiment with Windows 8. Very fast startup and shut down on old machines. Windows 8 took a lot from the gnome-shell model and made it work for them.  You can do all with just a mouse and do not need touch on old desktops and laptops.  But I am a Unity convert since a while back.  I have MS-DOS 1.25 for my old Sanyo MBC 550 (which is now in recycle bin). That's basically where I started.

---

### Post by serdotlinecho on 2013-05-02
Yesterday, when I booted up my pc, I had blinking dash (-) and black screen after plymouth, can't load unity greeter. I had to do Alt+Sys Rq+B to reboot. After reboot, unity greeter load just fine. Here's today upgrades:

[IMG]http://i.imgur.com/tYUTBJx.png[/IMG]

---

### Post by serdotlinecho on 2013-05-03
Last night, when I shutdown, it didn't shutdown properly but kind like force poweroff and I can hear the hard disk stop spinning. This has happened twice on my machine.

```
Calculating upgrade... Done
The following NEW packages will be installed:
   libboost-iostreams1.53.0 (1.53.0-4ubuntu1)
The following packages will be upgraded:
   appmenu-qt (0.2.7daily13.03.28-0ubuntu1 => 0.2.7daily13.05.02-0ubuntu1)
   appmenu-qt5 (0.2.7daily13.03.28-0ubuntu1 => 0.2.7daily13.05.02-0ubuntu1)
   aptitude (0.6.8.1-2ubuntu2 => 0.6.8.1-2ubuntu3)
   aptitude-common (0.6.8.1-2ubuntu2 => 0.6.8.1-2ubuntu3)
   bamfdaemon (0.4.0daily13.04.03-0ubuntu1 => 0.4.0daily13.05.02-0ubuntu1)
   bc (1.06.95-4ubuntu1 => 1.06.95-6)
   cpp-4.8 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   dc (1.06.95-4ubuntu1 => 1.06.95-6)
   devscripts (2.13.1 => 2.13.1build1)
   g++-4.8 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   gcc-4.8 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   gcc-4.8-base (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   gir1.2-appindicator3-0.1 (12.10.1daily13.04.15-0ubuntu1 => 12.10.1daily13.05.02-0ubuntu1)
   gir1.2-messagingmenu-1.0 (12.10.6daily13.04.09-0ubuntu1 => 12.10.6daily13.05.02-0ubuntu1)
   gstreamer1.0-plugins-bad (1.0.6-1ubuntu1 => 1.0.7-1ubuntu1)
   gstreamer1.0-plugins-good (1.0.6-1ubuntu1 => 1.0.7-1ubuntu1)
   gstreamer1.0-pulseaudio (1.0.6-1ubuntu1 => 1.0.7-1ubuntu1)
   indicator-datetime (12.10.3daily13.03.26-0ubuntu1 => 12.10.3daily13.05.02-0ubuntu1)
   indicator-messages (12.10.6daily13.04.09-0ubuntu1 => 12.10.6daily13.05.02-0ubuntu1)
   indicator-session (12.10.5daily13.03.08-0ubuntu1 => 12.10.5daily13.05.02-0ubuntu1)
   indicator-sound (12.10.2daily13.04.12-0ubuntu1 => 12.10.2daily13.05.02-0ubuntu1)
   libappindicator1 (12.10.1daily13.04.15-0ubuntu1 => 12.10.1daily13.05.02-0ubuntu1)
   libappindicator3-1 (12.10.1daily13.04.15-0ubuntu1 => 12.10.1daily13.05.02-0ubuntu1)
   libasan0 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libatomic1 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libbamf3-1 (0.4.0daily13.04.03-0ubuntu1 => 0.4.0daily13.05.02-0ubuntu1)
   libdbusmenu-qt2 (0.9.2daily13.03.28-0ubuntu1 => 0.9.2daily13.05.02-0ubuntu1)
   libdbusmenu-qt5 (0.9.2daily13.03.28-0ubuntu1 => 0.9.2daily13.05.02-0ubuntu1)
   libdrm-intel1 (2.4.43-0ubuntu1 => 2.4.44-0ubuntu1)
   libdrm-nouveau2 (2.4.43-0ubuntu1 => 2.4.44-0ubuntu1)
   libdrm-radeon1 (2.4.43-0ubuntu1 => 2.4.44-0ubuntu1)
   libdrm2 (2.4.43-0ubuntu1 => 2.4.44-0ubuntu1)
   libgcc-4.8-dev (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libgcc1 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libgomp1 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libgstreamer-plugins-bad1.0-0 (1.0.6-1ubuntu1 => 1.0.7-1ubuntu1)
   libgstreamer-plugins-good1.0-0 (1.0.6-1ubuntu1 => 1.0.7-1ubuntu1)
   libindicator3-7 (12.10.2daily13.04.10-0ubuntu1 => 12.10.2daily13.05.02-0ubuntu1)
   libindicator7 (12.10.2daily13.04.10-0ubuntu1 => 12.10.2daily13.05.02-0ubuntu1)
   libitm1 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libmessaging-menu0 (12.10.6daily13.04.09-0ubuntu1 => 12.10.6daily13.05.02-0ubuntu1)
   libquadmath0 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libsqlite3-0 (3.7.15.2-1ubuntu1 => 3.7.16.2-1ubuntu1)
   libssh-4 (0.5.3-1ubuntu1 => 0.5.4-1)
   libstdc++-4.8-dev (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libstdc++6 (4.8.0-4ubuntu3 => 4.8.0-4ubuntu4)
   libtelepathy-logger3 (0.8.0-0ubuntu1 => 0.8.0-1)
   libvisio-0.0-0 (0.0.25-1 => 0.0.26-2)
   libwpd-0.9-9 (0.9.6-2 => 0.9.7-1)
   python-appindicator (12.10.1daily13.04.15-0ubuntu1 => 12.10.1daily13.05.02-0ubuntu1)
   python3-pyatspi (2.7.91+dfsg-0ubuntu1 => 2.8.0+dfsg-1)
   telepathy-gabble (0.16.5-0ubuntu1 => 0.16.5-1)
   telepathy-logger (0.8.0-0ubuntu1 => 0.8.0-1)
   upstart (1.8-0ubuntu1 => 1.8-0ubuntu2)
54 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.3 MB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue [Y/n]?Y
```

---

### Post by cariboo on 2013-05-03
@serdotlinecho, do you have the proposed repositories enabled, as the developers don't recommend it. Packages are moved to the proposed repositories, while waiting for dependencies to build, so things may not work as expected. 

I have just been doing regular updates twice a day without the proposed repositories enabled, and neither system running Saucy has shutdown problems.

On my netbook running Ubuntu Gnome, I thought I had a problem with suspend after installing a different wireless driver than I normally use, but I was jus being impatient :-D, it suspended when I closed the lid, as it should.

This early in the development cycle, we shouldn't be running into these types of problems yet as we are still closer to Raring, than Saucy.

---

### Post by sammiev on 2013-05-04
@serdotlinecho, I had the same problem a few days a go but after the many updates I'm good to go. My computer is Intel based across the board.

---

### Post by deadflowr on 2013-05-04
> **cariboo907 said:**
> @serdotlinecho, do you have the proposed repositories enabled, as the developers don't recommend it. Packages are moved to the proposed repositories, while waiting for dependencies to build, so things may not work as expected. 

I have just been doing regular updates twice a day without the proposed repositories enabled, and neither system running Saucy has shutdown problems.

On my netbook running Ubuntu Gnome, I thought I had a problem with suspend after installing a different wireless driver than I normally use, but I was jus being impatient :-D, it suspended when I closed the lid, as it should.

This early in the development cycle, we shouldn't be running into these types of problems yet as we are still closer to Raring, than Saucy.

I believe this translates to saucy as well

[http://ubuntuforums.org/showthread.php?t=2076448&highlight=proposed-updates+raring](http://ubuntuforums.org/showthread.php?t=2076448&highlight=proposed-updates+raring)

Unlike the stable releases( where packages in proposed can sit for weeks sometimes, getting heavy tested), the developers are taking a different approach and using the proposed as a quasi-staging area.

---

### Post by JMB74 on 2013-05-04
Correct. Unless you really know what you are doing, or as a matter of urgency need to test something specific, then it's advisable not to have "proposed" enabled on the development release.

An example during raring was where certain libraries needed for multiarch support build for some architectures but failed on others. people with proposed not enabled saw nothing, as the packages didn't move to released until they were fixed. Some people with "proposed" enabled ended up with either broken multiarch support, or by accepting upgrades from proposed that they shouldn't have caused multiarch support to be removed completely. In turn that ended up with things like googleearth, skype, crossoverlinux/wine and more etc etc being nuked or not running.

---

### Post by jppr on 2013-05-04
13.10 is a development version, how to test it fully if you don´t use in proposed updates? In fact, I've been using for 6 years from the first development version since in proposed upgrades and that is not ever been to any kind of problem.

Again, this is a development version of my full daily use, installed on own HD just as is the 13.10 Ubuntu-Gnome and Windows 8 Pro. Also, Ubuntu 13.10 Ubuntu-Gnome is used in proposed upgrades.

---

### Post by JMB74 on 2013-05-04
> **jppr said:**
> 13.10 is a development version, how to test it fully if you don´t use in proposed updates?

Of copurse you can test the development version without proposed enabled. Read the posts and links on the previous page.

The way the new packages go into the repos changed at the start of the raring cycle.

Previously the went straight into "released". Now the go into "proposed" for a _**short while**_ until they build OK for all architectures, and pass some automatic instability testing etc.

**The role of the proposed pocket has changed.**

You can still test saucy just fine without proposed enabled, as the delay for packages that build/pass the tests becoming available is short. Packages that don't make it from "proposed" to "released" in a reasonable time likely have something wrong with them, so not a good idea to let those install.

---

### Post by JMB74 on 2013-05-04
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html)

> I'm still frantically putting the bits together for this, but  it's now far enough along that I feel comfortable saying we're going to  be doing it for Raring, so:  

In the continuing cause of trying to make the development series more  usable at all times, not just around milestones, I'm rearranging the way  our uploads are processed.  For Raring, all uploads will go to  raring-proposed, and a modified instance of "britney" (the software that  handles migration from Debian unstable to testing) will copy them to  raring when they've been built everywhere and do not reduce the count of  installable packages in the archive.  

The intent of this is to come as close as possible to eliminating  transient uninstallability problems in the development release.  We  probably won't get all the way there.  It will still be possible for  uninstallability to be introduced by copies not all happening in a  single publisher run, transient uninstallability in -proposed will still  affect package builds, and it won't catch all cases where sets of  packages that used to be simultaneously installable stop being so (the  general case of this is NP-complete anyway).  Even with these  limitations, though, it should make things a lot better.and

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2012-October/000989.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2012-October/000989.html)

> As I described in [https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html), all uploads to raring will now be automatically redirected to raring-proposed by default.  

They will be automatically copied to raring once they pass various tests  such as being no less installable than the previous version, and soon I  hope to take autopkgtest results into consideration as well. 

Attempts to copy ("sync") directly into raring will be refused.  syncpackage's default will be changed in the next ubuntu-dev-tools  upload, but in the meantime please use 'syncpackage -r raring-proposed'.  

This was one of the last blockers to opening raring for general  development, so we should be able to get moving on this fairly soon.   Cheers,

---

### Post by JMB74 on 2013-05-04
And from a ubuntu developer/maintainer who know what they are talking about.

> **jbicha said:**
> Right, we strongly discourage people from running  -proposed on a development release; packages will automatically migrate  to the regular archives when they're ready.

After release, -proposed is for testing SRUs and we want people to use -proposed and help out with that testing.

---

### Post by serdotlinecho on 2013-05-04
> **cariboo907 said:**
> @serdotlinecho, do you have the proposed repositories enabled, as the developers don't recommend it. Packages are moved to the proposed repositories, while waiting for dependencies to build, so things may not work as expected. 

I have just been doing regular updates twice a day without the proposed repositories enabled, and neither system running Saucy has shutdown problems.

On my netbook running Ubuntu Gnome, I thought I had a problem with suspend after installing a different wireless driver than I normally use, but I was jus being impatient :-D, it suspended when I closed the lid, as it should.

This early in the development cycle, we shouldn't be running into these types of problems yet as we are still closer to Raring, than Saucy.

I just want to share my experience with other Ubuntu+1 members. I started testing ubuntu development branch 11.10 alpha and switch completely to ubuntu development branch since 12.04 cycle(proposed repositories enabled) and up until now the current development cycle. :)

---

### Post by jerrylamos on 2013-05-04
?    Saucy is in the daily builds already.  I didn't have to change repos.

I just copied raring....amd64.iso to saucy...amd64.iso and did a zsync to the daily build.  74.8% was the same only had to update 25.2%.  Cuts way down on the ubuntu server load.

Then just did an install went fine.

In the U+1 forum I  expect to do a lot of installs which tests for bugs in the install process.  

Also after an accumulation of updates a fresh install cleans things up and may reduce the disk space used as shown by "df" more than 10%.  apt-get clean, apt-get autoremove, and apt-get purge linux-image-....... and apt-get purge linux-headers..... help but there is still garbage left since "df" is still fatter than after install.

Ergo not at all sure about how this "rolling" release stuff will work....

BTW, installed to a USB SSD just in case the "unstable" install botched things up like sometimes.....

---

### Post by ventrical on 2013-05-04
> **jerrylamos said:**
> ?    Saucy is in the daily builds already.  I didn't have to change repos.

I just copied raring....amd64.iso to saucy...amd64.iso and did a zsync to the daily build.  74.8% was the same only had to update 25.2%.  Cuts way down on the ubuntu server load.

Then just did an install went fine.

In the U+1 forum I  expect to do a lot of installs which tests for bugs in the install process.  

Also after an accumulation of updates a fresh install cleans things up and may reduce the disk space used as shown by "df" more than 10%.  apt-get clean, apt-get autoremove, and apt-get purge linux-image-....... and apt-get purge linux-headers..... help but there is still garbage left since "df" is still fatter than after install.

Ergo not at all sure about how this "rolling" release stuff will work....

BTW, installed to a USB SSD just in case the "unstable" install botched things up like sometimes.....

Wow .. so after this did the repos actually all change to /saucy/ from the zsync??

Thanks.

ps. I wanted to start zsyncing  in this manner but I didn't know it was that easy to do so. I'm going to give it a try  with the i386..iso

---

### Post by craig10x on 2013-05-04
Just curious....but when you guys talk about using zsync to switch from raring to saucy, do you mean using a saucy daily build iso's option of "upgrading" to do it?
I had problems trying to switch over to saucy using the terminal commands and have since re-installed 13.04 from a final iso...so i was just wondering, if that method would have gone smoother...

1) Did you just select that option from the daily build and it properly switched everything over? 
 2) Also, what about any programs or files you had on raring...did they all transfer over properly too?

---

### Post by bcbc on 2013-05-04
What about 
```
sudo do-release-upgrade -d
```

---

### Post by grahammechanical on 2013-05-04
@craig10x

This is what I think that jerrylamos did.

He used the QA tracking zsyc url to update a Raring ISO image. But I am wrong. I have just tried it and I get the error message No relevent local data found - I will be downloading the whole file. Now I am sure that I did things correctly. Copied a Raring ISO image into the Downloads directory. CDed into the Downloads directory. Copied the zsync info in terminal. Yep.

So, I am as baffled as you. Any way I now have a Saucy ISO.

Edit: Re-reading jerrylamos post, I think he changed the name of the ISO image from raring-desktop-amd64.iso to saucy-desktop-amd64.iso (Assuming it was an amd64 ISO). I will have to try that.

Second Edit. It is working. Rename the raring ISO image to saucy and run the zsync download url. Target 57% complete. So, already we have a big difference between Raring and Saucy

Regards.

---

### Post by deadflowr on 2013-05-04
> **jppr said:**
> 13.10 is a development version, how to test it fully if you don´t use in proposed updates? 

The whole cycle is a proposed-update.

---

### Post by ventrical on 2013-05-04
..or simply rename :

raring-desktop-i386.iso  to   saucy-desktop-i386.iso

then

dale@dale-desktop:~$ cd Desktop
dale@dale-desktop:~/Desktop$ zsync -i ./saucy-desktop-i386.iso [http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-i386.iso.zsync)
#################### 100.0% 234.6 kBps DONE   

and it is updating now ..

thanks everybody.

Ubuntu Rocks.

Thank you Mark Shuttleworth and Linus Torvalds for uninterrupted , malware free, harassment free Ubuntu Sessions where work can actually get done!

Regards,
Ventrical

---

### Post by Curtis6767 on 2013-05-04
I updated my sources list, per the instructions at the start of this thread, for a 13.04 install in Vbox. The first few times I tried to run updates, I received error messages and no updates were downloaded. Once the Saucy ISO was available, then the updates came. I'm finding no issues so far with the addition of the 3.9 kernel and the 13.04 programs installed.  I don't have Netflix desktop installed on this particular Vbox and I'm not so sure I'll try to do so right away. It was quite a while in 13.04 before I could get that to work and once it worked then so did everything else.

My install still thinks it's 13.04, btw.

---

### Post by jerrylamos on 2013-05-05
> **grahammechanical said:**
> @craig10x

This is what I think that jerrylamos did.

He used the QA tracking zsyc url to update a Raring ISO image. .
Nope, simpler than that, just did a ```

cp raring-desktiop-amd64.iso saucy-desktip-amd64.iso
```
then did a  ```

sudo zsync http://cdimage.ubuntu.com/cdimage/daily-live/current//saucy-desktop-amd64.iso.zsync
```
zsync reported 74.8% complete, as of that date, goes ahead and completes the zsync
which gets me a saucy.iso I can boot directly from the hard drive, 
then I use an exec to do my setup....

I do this early in the U+1 when it looks like the U+1 daily build will install, using the last previous .iso.  Don't know what will happen with the next "rolling release"?

---

