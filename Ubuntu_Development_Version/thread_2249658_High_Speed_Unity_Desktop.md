---
title: "High Speed Unity Desktop"
date: 2014-10-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-10-23
I was just experimenting on one of my ASUS Core 2 Quads with Ver. 3.0 Kingston SSD. I had changed over the sources.list to /devel/ then updated/upgraded. There were about 310MBs of utopic upgrades and it went just fine. I then restarted and now all the apps from the Unity panel are opening within a split second (meaning less than 1 second) which previously  apps like Libre Office Writer or Impress would  take about 1.5 to 2 seconds to fully open.

  I highly doubt it has anything with changing over the sources list - but I think the most recent utopic upgrades have either installed or upgraded somthing which previously had log-jammed  these high speed acrobatics.

Nice work.

Regards..

---

### Post by Hazzabin on 2014-10-23
I know I'm a novice at this testing stuff but what do you mean by "[COLOR=#000000]changed over the sources.list to /devel/"  yes I do know about update/upgrade :)[/COLOR]

---

### Post by ventrical on 2014-10-23
> **Hazzabin said:**
> I know I'm a novice at this testing stuff but what do you mean by "[COLOR=#000000]changed over the sources.list to /devel/"  yes I do know about update/upgrade :)[/COLOR]

```


[B]sudo sed -i 's/utopic/devel/g' /etc/apt/sources.list

[/B][B][B]sudo apt-get update && sudo apt-get dist-upgrade

[/B][/B]
```[B][B]

During the raring cycle and onwards (in the concept of rolling releases) we
are able to adjust sources.list and prepare it for next development cycle.

It is very early so only do this if you have extra hardware to experiment with.  [/B][/B]

Regards..


see also   [http://ubuntuforums.org/showthread.php?t=1970289](http://ubuntuforums.org/showthread.php?t=1970289)

                  [https://wiki.ubuntu.com/devel-tester-wiki](https://wiki.ubuntu.com/devel-tester-wiki)

---

### Post by Hazzabin on 2014-10-23
Thanks mate and yes I got plenty of space on one tower box

again thanks for your help

---

### Post by grahammechanical on 2014-10-23
Next week I shall be running this command

```
sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list
```

Then my Utopic Unicorn which has just become 14.10 will be started on the way of becoming 15.04. It will be receiving the updates going into the Vivid Vervet repositories. As I run daily updates. The alternative is to wait until the first vivid daily ISO images are made available and install one of them.

See this post

[http://ubuntuforums.org/showthread.php?t=2249645](http://ubuntuforums.org/showthread.php?t=2249645)

I think I will make the change now.

Regards

---

### Post by ventrical on 2014-10-23
> **grahammechanical said:**
> Next week I shall be running this command

```
sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list
```

Then my Utopic Unicorn which has just become 14.10 will be started on the way of becoming 15.04. It will be receiving the updates going into the Vivid Vervet repositories. As I run daily updates. The alternative is to wait until the first vivid daily ISO images are made available and install one of them.

See this post

[http://ubuntuforums.org/showthread.php?t=2249645](http://ubuntuforums.org/showthread.php?t=2249645)

I think I will make the change now.

Regards

For some reason the /devel/ doesn't work at present - so I am going to revert back to /vivid/

---

### Post by grahammechanical on 2014-10-23
> [COLOR=#000000]For some reason the /devel/ doesn't work at present - so I am going to revert back to /vivid/[/COLOR]

That is what I found the other day when I tried devel with Ubuntu Desktop Next. But I just this minute tried again putting desktop next on to devel and it updates from the vivid repositories. It did not say that it could not find devel so it was using vivid instead. 

In my tiredness did I type vivid instead of devel? Possibly. The sources.list does say vivid. It must be past my bed time.

Regards

---

### Post by rrnbtter on 2014-10-23
Greetings,
Success!
systemd
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:core-4.1-ia32:core-4.1-noarch:security-4.0-ia32:security-4.0-noarch:security-4.1-ia32:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
3.18.0-031800rc1-generic
root       831  0.2  0.7 170676 31560 tty7     Ssl+ 06:47   2:05 /usr/sbin/unity-system-compositor --disable-inactivity-policy=true --on-fatal-error-abort --file /run/mir_socket --from-dm-fd 10 --to-dm-fd 13 --vt 7
rrnbtter 20523  0.0  0.0   4484  2060 pts/2    S+   22:02   0:00 grep unity-system-compositor

---

### Post by ventrical on 2014-10-24
I'm in :) That  was fast :)

```

ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
ventrical@ventrical-MS-7798:~$ 

```

Having fun :) 

Regards..

---

### Post by Hazzabin on 2014-10-24
Yup mate me is in too, thanks again for your help ;)

---

### Post by ventrical on 2014-10-24
> **grahammechanical said:**
> That is what I found the other day when I tried devel with Ubuntu Desktop Next. But I just this minute tried again putting desktop next on to devel and it updates from the vivid repositories. It did not say that it could not find devel so it was using vivid instead. 

In my tiredness did I type vivid instead of devel? Possibly. The sources.list does say vivid. It must be past my bed time.

Regards

@graham

 /devel is now working and it automatically edits the Ubuntu.info file.

>  [s]
ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog)

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
Description: Unsupported updates
[/s]


---

### Post by zika on 2014-10-24
> **ventrical said:**
> @graham /devel is now working and it automatically edits the Ubuntu.info file.Kind-of:not: [http://ubuntuforums.org/showthread.php?t=2249736&p=13150760#post13150760](http://ubuntuforums.org/showthread.php?t=2249736&p=13150760#post13150760)

---

### Post by ventrical on 2014-10-24
> **zika said:**
> Kind-of:not: [http://ubuntuforums.org/showthread.php?t=2249736&p=13150760#post13150760](http://ubuntuforums.org/showthread.php?t=2249736&p=13150760#post13150760)

Yeah .. I heard ya already :)

---

