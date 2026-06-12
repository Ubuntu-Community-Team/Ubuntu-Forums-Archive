---
title: "Make sure to edit Ubuntu.info file"
date: 2014-10-24
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-10-24
To solve the problem, insert the following text in /usr/share/python-apt/templates/Ubuntu.info: Suite: vivid
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.10 'Vivid Vervet'
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

Suite: vivid
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.10 'Vivid Vervet'

Suite: vivid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.
MatchURI: cdrom:\[Ubuntu.*14.10
Description: Cdrom with Ubuntu 14.10 'Vivid Vervet'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: vivid
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: vivid
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: vivid-security
ParentSuite: vivid
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: vivid-security
ParentSuite:vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: vivid-updates
ParentSuite: vivid
RepositoryType: deb
Description: Recommended updates

Suite:vivid-updates
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: vivid-proposed
ParentSuite: vivid
RepositoryType: deb
Description: Pre-released updates

Suite: vivid-proposed
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: vivid-backports
ParentSuite: vivid
RepositoryType: deb
Description: Unsupported updates

Suite: vivid-backports
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates**Note:**  Two days after vivid was opened for development, A new edit was added  to /usr/share/python-apt/templates/Ubuntu.info, changing the  repositories to devel, although the changes haven't been made to my  system as yet.

---

### Post by Elfy on 2014-10-24
/me should have remembered to post that for everyone earlier - but then I did the normal thing

forgot all about it :D

---

### Post by slickymaster on 2014-10-24
Thanks for posting the reminder ventrical

---

### Post by ventrical on 2014-10-24
Your welcome . Cariboo put it up on his release schedule sticky so I just grabbed it.

Regards..

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

---

### Post by slickymaster on 2014-10-24
> **ventrical said:**
> Your welcome . Cariboo put it up on his release schedule sticky so I just grabbed it.

Regards..

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)


lol, I missed cariboo's sticky. That just goes to show you how accurate is that old saying:*"The shoemaker's son always goes barefoot." *;)

---

### Post by ventrical on 2014-10-24
On another note .. if you use the /devel option instead of /vivid it will automagically edit Ubuntu.info file.

> 
[s]ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog)

Suite: devel
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
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

Suite: devel
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates[/s]



---

### Post by slickymaster on 2014-10-24
> **ventrical said:**
> On another note .. if you use the /devel option instead of /vivid it will automagically edit Ubuntu.info file.

[s]Yeaps, that's what happened to me.[/s]

---

### Post by 4zika4 on 2014-10-24
> **ventrical said:**
> On another note .. if you use the /devel option instead of /vivid it will automagically edit Ubuntu.info file.I beg to differ. Check that because I see on one machine with 15.04 (and it was the same while it was on 14.10) that devel is in that file, on the top, from vanilla install. I might be wrong (again) but I do know for sure that I did not change sources.list on that machine and I'm pretty sure that not one else could have done that... ;)

---

### Post by ventrical on 2014-10-24
> **4zika4 said:**
> I beg to differ. Check that because I see on one machine with 15.04 (and it was the same while it was on 14.10) that devel is in that file, on the top, from vanilla install. I might be wrong (again) but I do know for sure that I did not change sources.list on that machine and I'm pretty sure that not one else could have done that... ;)

 Checking .....Yes . Correct .  That file will create a gtk error. So it has to be the original file as referenced by cariboo.

Regards..

---

### Post by zika on 2014-10-24
> **ventrical said:**
> On another note .. if you use the /devel option instead of /vivid it will automagically edit Ubuntu.info file.[COLOR=#000000]I beg to differ. Check that because I see on one machine with 15.04 (and it was the same while it was on 14.10) that devel is in that file, on the top, from vanilla install. I might be wrong (again) but I do know for sure that I did not change sources.list on that machine and I'm pretty sure that not one else could have done that... [/COLOR]:wink:

---

### Post by zika on 2014-10-24
> **4zika4 said:**
> I beg to differ. Check that because I see on one machine with 15.04 (and it was the same while it was on 14.10) that devel is in that file, on the top, from vanilla install. I might be wrong (again) but I do know for sure that I did not change sources.list on that machine and I'm pretty sure that not one else could have done that... ;)

> **ventrical said:**
> Checking .....Yes . Correct .  That file will create a gtk error. So it has to be the original file as referenced by cariboo.

Regards..

> **zika said:**
> [COLOR=#000000]I beg to differ. Check that because I see on one machine with 15.04 (and it was the same while it was on 14.10) that devel is in that file, on the top, from vanilla install. I might be wrong (again) but I do know for sure that I did not change sources.list on that machine and I'm pretty sure that not one else could have done that... [/COLOR]:wink:New machine tricked me (old user is too old, really) so I loged in with a username that was (I forgot) created long time ago, when UF was hacked. Sorry for that, back to my ususal username... ;)

---

### Post by grahammechanical on 2014-10-24
I have just seen this post. Thanks ventrical.

I also noticed the references to the devel repositories on this install that I am sure I never converted the software sources to devel. Anyway, I entered those lines after the devel listing. Putting in that code seems to have fixed one minor problem. Software and Updates now opens. It was broken an hour or two ago. And there is no blockage on update/upgrade.

---

### Post by ventrical on 2014-10-24
> **grahammechanical said:**
> I have just seen this post. Thanks ventrical.

I also noticed the references to the devel repositories on this install that I am sure I never converted the software sources to devel. Anyway, I entered those lines after the devel listing. Putting in that code seems to have fixed one minor problem. Software and Updates now opens. It was broken an hour or two ago. And there is no blockage on update/upgrade.


On this current install I originally had a clean install of Utopic. I then switched over from Utopic to devel and it put that file in there automatically (I did not manually change it). However, gtk-software will come up with errors (as you have said above). I had to re-edit the Ubuntu.info file on this machine and just switch back to /vivid. It (the /devel/ repo change) worked; raring/saucy. saucy/trusty and trusty/utopic .. but it isn't working now.

Regards..

---

### Post by Hazzabin on 2014-10-24
Do we delete everything in that file and then paste the list as per 
"https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work" and or post #1

---

### Post by ventrical on 2014-10-24
> **Hazzabin said:**
> Do we delete everything in that file and then paste the list as per 
"https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work" and or post #1

You do not have to delete. Just make sure it is pasted at the top. If you have the changelog URL at the very top in your sources.list you can just comment it out with :

```


##
##

```

Don't worry about the colours when you save.

Regards..

Apologies for my mistake.

Here:

> 
## ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%##](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%##) s/%s_%s/changelog

Suite: vivid
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.10 'Vivid Vervet'
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

Suite: vivid
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.10 'Vivid Vervet'

Suite: vivid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.
MatchURI: cdrom:\[Ubuntu.*14.10
Description: Cdrom with Ubuntu 14.10 'Vivid Vervet'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: vivid
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: vivid
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: vivid-security
ParentSuite: vivid
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: vivid-security
ParentSuite:vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: vivid-updates
ParentSuite: vivid
RepositoryType: deb
Description: Recommended updates

Suite:vivid-updates
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: vivid-proposed
ParentSuite: vivid
RepositoryType: deb
Description: Pre-released updates

Suite: vivid-proposed
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: vivid-backports
ParentSuite: vivid
RepositoryType: deb
Description: Unsupported updates

Suite: vivid-backports
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


---

### Post by Hazzabin on 2014-10-24
Thanks mate, one last question errr umm for now lol

to access that usr file I usually go via sudo nautilus then search for that file, is there an easier command line to get there   sorry did say b4 I was a total noob :)

---

### Post by Elfy on 2014-10-24
well I 

```
pkexec mousepad /usr/share/python-apt/templates/Ubuntu.info
```

but I use Xubuntu - replace mousepad with your text editor

---

### Post by zika on 2014-10-24
> **ventrical said:**
> If you have the changelog URL at the very top in your sources.list you can just comment it outAny good reason for disabling that (in my book usefull resource) line?

---

### Post by Hazzabin on 2014-10-24
thanks mate

---

### Post by ventrical on 2014-10-24
> **zika said:**
> Any good reason for disabling that (in my book usefull resource) line?

Because it will come up with a gtk error. I don't know why . Just does.  But I too think it is useful resource but it will give errors . At least here it did.

---

### Post by ventrical on 2014-10-24
> **Hazzabin said:**
> Thanks mate, one last question errr umm for now lol

to access that usr file I usually go via sudo nautilus then search for that file, is there an easier command line to get there   sorry did say b4 I was a total noob :)

I'm just using sudo for now , as pkexec is busted to some extent and  I don't feel like installing gksu.:)

---

### Post by Hazzabin on 2014-10-24
yup found that out too, thanks mate

---

### Post by grahammechanical on 2014-10-24
I think that it is safer to use 

```
sudo -H gedit
```

or 

```
sudo -H nautilus
```

as the sudo manpage says the -H switch 

> sets the HOME environment variable to the homedir of the target user (root by default) as

I think that means there is less risk of inadvertently changing the permissions of system files. I may be wrong.

Regards.

---

### Post by Hazzabin on 2014-10-24
Thanks for that info to G

---

### Post by ventrical on 2014-10-24
> **grahammechanical said:**
> I think that it is safer to use 

```
sudo -H gedit
```

or 

```
sudo -H nautilus
```

as the sudo manpage says the -H switch 


I think that means there is less risk of inadvertently changing the permissions of system files. I may be wrong.

Regards.

No .. you're right. That's what zika has been saying all along (or something to that extent). Until they get pkexec fixed anyways.

Regards..

zzzzz time :)

---

### Post by zika on 2014-10-25
> **ventrical said:**
> Because it will come up with a gtk error. I don't know why . Just does.  But I too think it is useful resource but it will give errors . At least here it did.As far as I can see, no errors here due to that line. Something else might be triggering errors You might see.

---

### Post by ventrical on 2014-10-25
> **zika said:**
> As far as I can see, no errors here due to that line. Something else might be triggering errors You might see.

I will edit and retry. I may have missed because of hard boot.

---

### Post by harry332 on 2014-10-27
We have the new python-apt ([SIZE=2]0.9.3.11) in repos now, so no need to touch ubuntu.info any longer.

[/SIZE]

---

### Post by ventrical on 2014-10-27
> **harry332 said:**
> We have the new python-apt ([SIZE=2]0.9.3.11) in repos now, so no need to touch ubuntu.info any longer.

[/SIZE]


Great . Thanks for that report. Made my day ! :)

Regards..

---

### Post by Hazzabin on 2014-10-27
Ok, so that should be already in the new daily iso?

And will an update via synaptic fix the current apt

---

### Post by harry332 on 2014-10-28
Upgrading with synaptic will fix this ubuntu.info issue immediately.
If you have manually changed the file, no harm done, the file will be upgraded anyway.

---

### Post by Cavsfan on 2014-10-29
Thanks          ventrical for finding this. I had not the slightest clue as always.

One <dumb> question - my file goes all the way through many, many Ubuntu versions in addition to devel (now vivid) it has trusty, saucy, raring, quantal, precise, oneiric, natty, maverick, lucid, karmic, jaunty, intrepid, hardy, gutsy, feisty, edgy, dapper, breezy, hoary and even warty.

Pretty much back when Fred Flinstone was a kid. :p I think I started out with Jaunty.

Do I leave all of those other versions in there or have it end when vivid ends?

BTW: I used gksudo pluma (on Mate) without any errors.

---

### Post by Cavsfan on 2014-10-29
> **harry332 said:**
> We have the new python-apt ([SIZE=2]0.9.3.11) in repos now, so no need to touch ubuntu.info any longer.

[/SIZE]

That is odd. I still had "devel" in the place where "vivid" should be and I have 

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy python-apt
python-apt:
  Installed: [COLOR=#ff0000]0.9.3.11[/COLOR]
  Candidate: 0.9.3.11
  Version table:
 *** 0.9.3.11 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by cariboo on 2014-10-29
> **Cavsfan said:**
> That is odd. I still had "devel" in the place where "vivid" should be and I have 

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy python-apt
python-apt:
  Installed: [COLOR=#ff0000]0.9.3.11[/COLOR]
  Candidate: 0.9.3.11
  Version table:
 *** 0.9.3.11 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status

```

I didn't do anything to the file, and I also have devel instead of vivid. I did use synaptic to do the upgrade though. Everything seems to be working as it should.

---

### Post by ventrical on 2014-10-30
> **Cavsfan said:**
> Thanks          ventrical for finding this. I had not the slightest clue as always.

One <dumb> question - my file goes all the way through many, many Ubuntu versions in addition to devel (now vivid) it has trusty, saucy, raring, quantal, precise, oneiric, natty, maverick, lucid, karmic, jaunty, intrepid, hardy, gutsy, feisty, edgy, dapper, breezy, hoary and even warty.

Pretty much back when Fred Flinstone was a kid. :p I think I started out with Jaunty.

Do I leave all of those other versions in there or have it end when vivid ends?

BTW: I used gksudo pluma (on Mate) without any errors.


That's a super good question and I don't really know why. I assume it just prepends and leaves the other distro info as a log history.

---

### Post by harry332 on 2014-10-30
> **cariboo907 said:**
> I didn't do anything to the file, and I also have devel instead of vivid. I did use synaptic to do the upgrade though. Everything seems to be working as it should.

Well it was this python-apt (0.9.3.11) changelog I was refering to.
See the last line (in bold).
     [h=2]**[SIZE=2]Changelog[/SIZE]**[/h]         python-apt (0.9.3.11) unstable; urgency=low

  [ Colin Watson ]
  * Add template for the "Ubuntu-RTM" derived distribution.
  * Detect whether a system is running Ubuntu-RTM by way of
    "system-image-cli -i".  Not perfect but close enough.

  [ Julian Andres Klode ]
  * Embed changelog entry date and time instead of build date and time
    (Closes: #762674)

  [ Michael Vogt ]
  * python/tarfile.cc: use long long in Process() for APT >= 4.14
  * Merged UbuntuRTMDistribution detection from ubuntu
  *** Add Ubuntu 15.04 (Vivid Vervet) to the template**

 -- Michael Vogt <email address hidden>  Fri, 24 Oct 2014 10:16:01 -0400

---

### Post by ventrical on 2014-10-30
> **Cavsfan said:**
> Thanks          ventrical for finding this. I had not the slightest clue as always.

One <dumb> question - my file goes all the way through many, many Ubuntu versions in addition to devel (now vivid) it has trusty, saucy, raring, quantal, precise, oneiric, natty, maverick, lucid, karmic, jaunty, intrepid, hardy, gutsy, feisty, edgy, dapper, breezy, hoary and even warty.

Pretty much back when Fred Flinstone was a kid. :p I think I started out with Jaunty.

Do I leave all of those other versions in there or have it end when vivid ends?

BTW: I used gksudo pluma (on Mate) without any errors.

@cavsfan, cariboo907

 I decided to try an experiement.

 I editied the Ubuntu.info file and cut all the info from trusty tahr downwards.  So that left me with <vivid> then <devel> then <utopic>.

 I then:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

 and it completely replaced the Ubuntu.info file with the exception (as you have both reported) with the /devel/ template file on top.!! So this is an automated process that is executed during the update process , most likely using 'apt'.  I assume then that Canonical development  incorporates the file-drectory convention... however about 2 cycles ago we were able to choose any random name in place of /devel/ and it would update to that next cycle.

Regards..

---

### Post by zika on 2014-10-30
Just follow the trail of the question: Why is Ubuntu.info file present, what is its purpose and what package do maintains it. Looking at sources is the easiest way.

---

### Post by harry332 on 2014-10-30
Ubuntu.info (ush/share/python-apt/templates/ubuntu.info) is part (one file) of the package python-apt-common.
**Python-apt-common:**
/usr/share/doc/python-apt-common/changelog.gz
/usr/share/doc/python-apt-common/copyright
/usr/share/python-apt/templates/Debian.info
/usr/share/python-apt/templates/Debian.mirrors
/usr/share/python-apt/templates/Tanglu.info
/usr/share/python-apt/templates/Tanglu.mirrors
/usr/share/python-apt/templates/Ubuntu.info
/usr/share/python-apt/templates/Ubuntu.mirrors
/usr/share/python-apt/templates/gNewSense.info
/usr/share/python-apt/templates/gNewSense.mirrors

---

### Post by ventrical on 2014-10-30
> **zika said:**
> Just follow the trail of the question: Why is Ubuntu.info file present, what is its purpose and what package do maintains it. Looking at sources is the easiest way.

That wasn't the purpose of the experiment. Why all other (not necessary) repos is experiment.

---

### Post by ventrical on 2014-10-30
> **harry332 said:**
> Ubuntu.info (ush/share/python-apt/templates/ubuntu.info) is part (one file) of the package python-apt-common.
**Python-apt-common:**
/usr/share/doc/python-apt-common/changelog.gz
/usr/share/doc/python-apt-common/copyright
/usr/share/python-apt/templates/Debian.info
/usr/share/python-apt/templates/Debian.mirrors
/usr/share/python-apt/templates/Tanglu.info
/usr/share/python-apt/templates/Tanglu.mirrors
/usr/share/python-apt/templates/Ubuntu.info
/usr/share/python-apt/templates/Ubuntu.mirrors
/usr/share/python-apt/templates/gNewSense.info
/usr/share/python-apt/templates/gNewSense.mirrors


Why include all the way back to warty?


Regards..

---

### Post by ventrical on 2014-10-30
> **Cavsfan said:**
> Thanks          ventrical for finding this. I had not the slightest clue as always.

One <dumb> question - my file goes all the way through many, many Ubuntu versions in addition to devel (now vivid) it has trusty, saucy, raring, quantal, precise, oneiric, natty, maverick, lucid, karmic, jaunty, intrepid, hardy, gutsy, feisty, edgy, dapper, breezy, hoary and even warty.

Pretty much back when Fred Flinstone was a kid. :p I think I started out with Jaunty.

Do I leave all of those other versions in there or have it end when vivid ends?

BTW: I used gksudo pluma (on Mate) without any errors.

@cavsfan
 I continued my experiment , edited (out out from trusty to warty) the Ubuntu.info file and marked it READ ONLY. I then updated /upgraded. The file did not change or was overwritten and there were no erros reported in terminal . I did research some bugs with python-apt and software-sources and there were some bugs but they were fixed. This then  appears to be a general housekeeping bug. 

Regards..

---

### Post by grahammechanical on 2014-10-30
> [COLOR=#000000]Why include all the way back to warty?[/COLOR]

It is for software archaeologists who, one day in the far distant future, may find in the long abandoned and over grown ruins of Canonical Towers a DVD of Ubuntu. 

Regards.

---

### Post by ventrical on 2014-10-30
:)

---

### Post by zika on 2014-10-30
> **ventrical said:**
> That wasn't the purpose of the experiment. Why all other (not necessary) repos is experiment.Again, read my post You've answered to. In my opinion (looking at the source and purpose of that file, it is not redundant. It might be just me, but I do understand its purpose and current format. Without any „experiment“. Whatever.

---

### Post by ventrical on 2014-10-30
> **zika said:**
> Again, read my post You've answered to. In my opinion (looking at the source and purpose of that file, it is not redundant. It might be just me, but I do understand its purpose and current format. Without any „experiment“. Whatever.

As you say "whatever".

My opinion.. housekeeping bug.

Regards..

---

### Post by Cavsfan on 2014-10-30
> **ventrical said:**
> Why include all the way back to warty?

> **grahammechanical said:**
> It is for software archaeologists who, one day in the far distant future, may find in the long abandoned and over grown ruins of Canonical Towers a DVD of Ubuntu. 

Regards.

:lol: Thanks I needed a good chuckle!

I just checked this file on Precise and it starts with Precise and goes all the way back to warty too. 
It has the **ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog)** line at the top uncommented out (no #).

```
cavsfan@cavsfan-MS-7529:/media/cavsfan/Precise/usr/share/python-apt/templates$ ls -l
total 112
-rw-r--r-- 1 root root  4295 Jan 24  2014 Debian.info
-rw-r--r-- 1 root root 27852 Jan 24  2014 Debian.mirrors
-rw-r--r-- 1 root root  1590 Jan 24  2014 gNewSense.info
-rw-r--r-- 1 root root 16349 Jan 24  2014 gNewSense.mirrors
-rw-r--r-- 1 root root 34444 Jan 24  2014 Ubuntu.info
-rw-r--r-- 1 root root 17061 Jan 24  2014 Ubuntu.mirrors

```

My Trusty install which is from a clean install ISO after it was released has the top line uncommented out and the top part has "devel" just like Vivid did and then trusty after that all the way to warty.
My Utopic Mate install also from a clean ISO is the exact same as Trusty starting with "devel".
Utopic has all of these files in that directory:

```
cavsfan@cavsfan-MS-7529:/media/cavsfan/Utopic-Mate/usr/share/python-apt/templates$ ls -l -a
total 168
drwxr-xr-x 2 root root  4096 Oct 14 08:30 .
drwxr-xr-x 3 root root  4096 Oct 14 08:30 ..
-rw-r--r-- 1 root root 11599 Sep 24 10:30 Blankon.info
-rw-r--r-- 1 root root   590 Sep 24 05:38 Blankon.mirrors
-rw-r--r-- 1 root root  5802 Sep 24 10:30 Debian.info
-rw-r--r-- 1 root root 28073 Sep 24 05:48 Debian.mirrors
-rw-r--r-- 1 root root  1590 Sep 24 10:30 gNewSense.info
-rw-r--r-- 1 root root 16349 Sep 24 05:38 gNewSense.mirrors
-rw-r--r-- 1 root root  1169 Sep 24 10:30 Tanglu.info
-rw-r--r-- 1 root root   115 Sep 24 05:38 Tanglu.mirrors
-rw-r--r-- 1 root root 55648 Sep 24 10:30 Ubuntu.info
-rw-r--r-- 1 root root 17348 Sep 24 05:48 Ubuntu.mirrors
-rw-r--r-- 1 root root  1976 Sep 24 10:30 Ubuntu-RTM.info
```


Could this file Ubuntu.info just be used for historical purposes like Graham suggests?
Also could it somehow know I was involved in the devel versions of those?

---

### Post by zika on 2014-10-30
> **Cavsfan said:**
> Could this file Ubuntu.info just be used for historical purposes like Graham suggests?
Also could it somehow know I was involved in the devel versions of those?The only thing that someone could read from Yours Ubuntu.info is (as You've pointed very nicely in Your post this qiote is part of) is the way You (if You're in U+1 testing, to presume) do your testing changelog-wise. ;)

---

### Post by Cavsfan on 2014-10-30
> **zika said:**
> The only thing that someone could read from Yours Ubuntu.info is (as You've pointed very nicely in Your post this qiote is part of) is the way You (if You're in U+1 testing, to presume) do your testing changelog-wise. ;)

Wat? I didn't quite grasp that. I didn't know I had any control over testing changelogs. :p

---

### Post by ventrical on 2014-10-30
> **Cavsfan said:**
> :lol: Thanks I needed a good chuckle!

I just checked this file on Precise and it starts with Precise and goes all the way back to warty too. 
It has the **ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog)** line at the top uncommented out (no #).

```
cavsfan@cavsfan-MS-7529:/media/cavsfan/Precise/usr/share/python-apt/templates$ ls -l
total 112
-rw-r--r-- 1 root root  4295 Jan 24  2014 Debian.info
-rw-r--r-- 1 root root 27852 Jan 24  2014 Debian.mirrors
-rw-r--r-- 1 root root  1590 Jan 24  2014 gNewSense.info
-rw-r--r-- 1 root root 16349 Jan 24  2014 gNewSense.mirrors
-rw-r--r-- 1 root root 34444 Jan 24  2014 Ubuntu.info
-rw-r--r-- 1 root root 17061 Jan 24  2014 Ubuntu.mirrors

```

My Trusty install which is from a clean install ISO after it was released has the top line uncommented out and the top part has "devel" just like Vivid did and then trusty after that all the way to warty.
My Utopic Mate install also from a clean ISO is the exact same as Trusty starting with "devel".
Utopic has all of these files in that directory:

```
cavsfan@cavsfan-MS-7529:/media/cavsfan/Utopic-Mate/usr/share/python-apt/templates$ ls -l -a
total 168
drwxr-xr-x 2 root root  4096 Oct 14 08:30 .
drwxr-xr-x 3 root root  4096 Oct 14 08:30 ..
-rw-r--r-- 1 root root 11599 Sep 24 10:30 Blankon.info
-rw-r--r-- 1 root root   590 Sep 24 05:38 Blankon.mirrors
-rw-r--r-- 1 root root  5802 Sep 24 10:30 Debian.info
-rw-r--r-- 1 root root 28073 Sep 24 05:48 Debian.mirrors
-rw-r--r-- 1 root root  1590 Sep 24 10:30 gNewSense.info
-rw-r--r-- 1 root root 16349 Sep 24 05:38 gNewSense.mirrors
-rw-r--r-- 1 root root  1169 Sep 24 10:30 Tanglu.info
-rw-r--r-- 1 root root   115 Sep 24 05:38 Tanglu.mirrors
-rw-r--r-- 1 root root 55648 Sep 24 10:30 Ubuntu.info
-rw-r--r-- 1 root root 17348 Sep 24 05:48 Ubuntu.mirrors
-rw-r--r-- 1 root root  1976 Sep 24 10:30 Ubuntu-RTM.info
```


Could this file Ubuntu.info just be used for historical purposes like Graham suggests?
Also could it somehow know I was involved in the devel versions of those?


My only point is  is that you have the option to truncate and lock down the  Ubuntu.info file (as in my experiment) with no ill effects. Then , during the next release you can unlock the file or at any time you wish but you will get all the addendum sweeps with it. It's not really an issue . I am just trying to illustrate a point about control of ones  own files and efficiency.

Regards..

---

### Post by zika on 2014-10-30
> **Cavsfan said:**
> Wat? I didn't quite grasp that. I didn't know I had any control over testing changelogs. :pYes You have, You can chooe to use them or not. Like reading newspapers. You decide their final fate.

---

### Post by Cavsfan on 2014-10-30
> **ventrical said:**
> My only point is  is that you have the option to truncate and lock down the  Ubuntu.info file (as in my experiment) with no ill effects. Then , during the next release you can unlock the file or at any time you wish but you will get all the addendum sweeps with it. It's not really an issue . I am just trying to illustrate a point about control of ones  own files and efficiency.

Regards..

Thanks for your explanation. I'm not going to worry about it. I've got bigger fish to fry. :p

Regards...

---

### Post by Cavsfan on 2014-10-30
> **zika said:**
> Yes You have, You can chooe to use them or not. Like reading newspapers. You decide their final fate.

Oh yes I read them sometimes. They come in handy.

---

### Post by ventrical on 2014-10-30
> **Cavsfan said:**
> Thanks for your explanation. I'm not going to worry about it. I've got bigger fish to fry. :p

Regards...

Hope it's halibut. Let me know when it's done ! :) lol

Regards..

---

### Post by fk-nero on 2014-10-30
hi  i got this  probelem too and  bin reading      but i dont get  it  i have  no  idear  what to do   or  how   
   maybe  can some  make  a  video or   with some pic  s

---

### Post by Elfy on 2014-10-30
> **fk-nero said:**
> hi  i got this  probelem too and  bin reading      but i dont get  it  i have  no  idear  what to do   or  how   
   maybe  can some  make  a  video or   with some pic  s

The information you need is in the first few posts - the rest is just chat.

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

---

### Post by fk-nero on 2014-10-31
thx but i can  edit the  ubuntu.info     i tryed the  above  stuff at the link but  its not working   
   frustrading

---

### Post by Elfy on 2014-10-31
> **fk-nero said:**
> thx but i can  edit the  ubuntu.info     i tryed the  above  stuff at the link but  its not working   
   frustrading

Possibly almost as frustrating as trying to help someone that only gives vague hints as to a problem?

What exactly does "it's not working" mean?

---

### Post by fk-nero on 2014-10-31
[URL="http://i.imgur.com/S6bIZnh.png"]sry about that     was  getting   bit   mad  xd 

http://i.imgur.com/S6bIZnh.png[/URL]  
    i get  that  provblem  that i can repace it  or     adit  it

---

### Post by ventrical on 2014-10-31
You have to be /root to edit.

From terminal:

```

sudo -H nautilus

```

Regards..

---

### Post by Elfy on 2014-10-31
Open it as root for edit.

Edit - if you're going to be running dev - I would suggest you get up to speed on editing things as root - both in GUI and out of it - you WILL end up in a recovery session wanting to edit with a cli editor ;)

```
pkexec gedit /usr/share/python-apt/templates/Ubuntu.info
```

```
sudo nano /usr/share/python-apt/templates/Ubuntu.info 
```

---

### Post by fk-nero on 2014-10-31
òke will try that thx

---

### Post by fk-nero on 2014-11-01
did try that  last   code   and edit  it  but  now i dont  know how too safe it     or exit the terminal

---

### Post by zika on 2014-11-01
> **fk-nero said:**
> did try that  last   code   and edit  it  but  now i dont  know how too safe it     or exit the terminalCtrl-X to exit nano. It will ask You about saving file. „exit“ od Ctrl-D to exit Terrminal (CLI).

---

### Post by fk-nero on 2014-11-04
hi  is this fix in  the new build or is it  still there  
  i try edit   it  but i still have   the same problem

---

### Post by grahammechanical on 2014-11-04
Personally, I am not sure how important an issue this is. At some point during the development cycle the ubuntu.info file will be updated and its replacement file will contain information relating to the vivid repositories. The lsb_release file has been undated already. It is is just a matter of time. And in fact it may have already happened. Are you prevented from updating?

Regards.

---

### Post by harry332 on 2014-11-05
As I already wrote 1 week ago here:
[http://ubuntuforums.org/showthread.php?t=2249736&page=3&p=13153477#post13153477](http://ubuntuforums.org/showthread.php?t=2249736&page=3&p=13153477#post13153477)

We have the new python-apt ([SIZE=2]0.9.3.11) in repos now, so no need to touch ubuntu.info any longer.[/SIZE]

---

### Post by ventrical on 2014-11-05
> **harry332 said:**
> As I already wrote 1 week ago here:
[http://ubuntuforums.org/showthread.php?t=2249736&page=3&p=13153477#post13153477](http://ubuntuforums.org/showthread.php?t=2249736&page=3&p=13153477#post13153477)

We have the new python-apt ([SIZE=2]0.9.3.11) in repos now, so no need to touch ubuntu.info any longer.[/SIZE]

Well, currently they are being planted with the /devel/ suffix .. so will there be a time when the /vivid/ suffix will replace this because I'm getting /devel/ and not /vivid.

Regards..

---

### Post by Cavsfan on 2014-11-05
I edited my file and changed devel to vivid and it's still holding but yesterday I looked at my Utopic install's file and it had devel in the top section.

---

### Post by Hazzabin on 2014-11-05
I too will confirm what Cavsfan wrote and Ventrical

---

