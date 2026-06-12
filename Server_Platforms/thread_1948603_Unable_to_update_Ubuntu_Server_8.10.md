---
title: "Unable to update Ubuntu Server 8.10"
date: 2012-03-28
forum: Server Platforms
---

### Post by henjohn1520 on 2012-03-28
I am unable to update Ubuntu 8.10 server to latest version. 
When I run the command "sudo apt-get upgrade" there's an error saying 
 
"E: Malformed line 4 in source list /etc/apt/sources.list (dist parse)"
"E: The list of sources could not be read.'
 
I have placed a copy of the sources.list file below.
 
Thanks.
 
 
```
#tls_random_source = dev:/dev/urandom
deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid# main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
## Major bug fix updates produced after the final release of the
## distribution.
 
 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
"/etc/apt/sources.list" 65L, 3452C 1,1 Top
```

---

### Post by mörgæs on 2012-03-28
You have a looong and risky way ahead, if you want to upgrade all the way to 11.10. Better to consider a fresh install.

---

### Post by CharlesA on 2012-03-28
> **mörgæs said:**
> You have a looong and risky way ahead, if you want to upgrade all the way to 11.10. Better to consider a fresh install.
What he said. I would recommend backing up your files and reinstalling fresh. A lot has changed since 8.10.

EDIT: In order to upgrade to the latest version, you would need to hop from:
8.10 > 9.04 > 9.10 > 10.04 > (and beyond!)

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by arrrghhh on 2012-03-28
> **CharlesA said:**
> What he said. I would recommend backing up your files and reinstalling fresh. A lot has changed since 8.10.

Indeed.  You can do it, but you'd have to upgrade thru many versions even to make it to 10.04.  Each upgrade is NOT going to be easy.

If it's a server, I would either a) try to wait for 12.04, just around the corner.  Or b) fresh install of 10.04, then when 12.04 hits .1 or .2 upgrade to it.  

Then **stay on LTS releases.**  This will allow you to go longer between upgrades.  8.10 is not LTS, and therefore it went end-of-life much sooner than an LTS release.

---

### Post by CharlesA on 2012-03-28
> **arrrghhh said:**
> Indeed.  You can do it, but you'd have to upgrade thru many versions even to make it to 10.04.  Each upgrade is NOT going to be easy.

If it's a server, I would either a) try to wait for 12.04, just around the corner.  Or b) fresh install of 10.04, then when 12.04 his .1 or .2 upgrade to it.  

Then **stay on LTS releases.**  This will allow you to go longer between upgrades.  8.10 is not LTS, and therefore it went end-of-life much sooner than an LTS release.
+1. I'd go with either 10.04 or 12.04.

---

### Post by dotku on 2012-03-28
> **arrrghhh said:**
> Indeed.  You can do it, but you'd have to upgrade thru many versions even to make it to 10.04.  Each upgrade is NOT going to be easy.

We want to keep the configuration; we don't want to re-configure over again. Any better solution for move over?

---

### Post by arrrghhh on 2012-03-28
> **dotku said:**
> We want to keep the configuration; we don't want to re-configure over again. Any better solution for move over?

Backup /etc or any other custom configuration files/changes you've made.

Stay on LTS releases from here on out.  In any production environment (or even a home environment that feels like production :p), it just makes sense.

---

### Post by snowpine on 2012-03-28
To answer your specific question, this line has an extraneous # symbol:

```
deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid# main restricted
```

(But you will need to comment out the "deb cdrom" lines anyway; the 8.10 CD will not help you upgrade to a new release.)

Here are the "end of life" upgrade instructions:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I agree with the recommendation to do a fresh install of a LTS release.

---

### Post by mörgæs on 2012-03-29
> **dotku said:**
> We want to keep the configuration; we don't want to re-configure over again. Any better solution for move over?

Moving config files from a 5-6 years old Ubuntu into a new one is likely to give you problems. My guess is that the fast and safe solution is to install a new system and configure it from scratch.

---

### Post by CharlesA on 2012-03-29
> **mörgæs said:**
> Moving config files from a 5-6 years old Ubuntu into a new one is likely to give you problems. My guess is that the fast and safe solution is to install a new system and configure it from scratch.
That's what I'm thinking as well. It "might" work, but you might run into problems.

---

### Post by arrrghhh on 2012-03-29
> **mörgæs said:**
> Moving config files from a 5-6 years old Ubuntu into a new one is likely to give you problems. My guess is that the fast and safe solution is to install a new system and configure it from scratch.

Good point.

I would save a copy of the configs regardless, so you can reference them when you rebuild...

Either way, you are a) going to save yourself A LOT of time and b) begin anew and clean with a LTS release by completely reinstalling.  It sounds daunting, but it's really not bad - and well worth your time.  Upgrading thru all the releases will actually take a lot longer - trust me, **a lot** longer.  Plus, you'll probably end up with a broken system, which no body wants.

Clean install of LTS release.  Then stay on LTS releases from here on out, and watch when they go EOL.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

