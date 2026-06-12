---
title: "Trusty now officially open for development"
date: 2013-10-21
forum: Ubuntu Development Version
---

### Post by JMB74 on 2013-10-21
Just had by email.

[https://lists.ubuntu.com/archives/ubuntu-devel/2013-October/037724.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-October/037724.html)

> Trusty is now open for development, with syncs from unstable currently running.
The development version starts with a new port and with minor updates to the
toolchain and some transitions.

 - GCC 4.8 was updated to the GCC 4.8.2 release and the GCC Linaro
   4.8-2013-10 release.  Binutils is built from the 2.24 release branch.

 - An glibc update will follow later during this cycle.

 - Perl was updated from v5.14 to to v5.18.

 - Berkeley DB was updated from v5.1 to v5.3.

 - boost was updated from v1.53 to v1.54.

Please check your uploads in a trusty chroot, don't just test in a saucy
environment. See [1] how to setup such a development chroot.

Trusty is the first development version that sees the AArch64 (arm64) port from
the start of the cycle.  Buildd resources are still somewhat limited compared to
the other architectures, so please ask first on #ubuntu-devel before giving back
a build for this port (e.g. compiler complaining about an unreproducible ICE).

[1] [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)



---

### Post by sgage on 2013-10-21
I'm downloading today's build as we speak.

---

### Post by OGpmpdog on 2013-10-21
> **sgage said:**
> I'm downloading today's build as we speak.

Let's Do This!!  LTS Breakage Time!!

---

### Post by sgage on 2013-10-21
No breakage yet!  :-)  But there have been a plethora of updates throughout the day, so breakage soon, no doubt...

---

### Post by sammiev on 2013-10-21
Yes, the updates are surely in. :p
Time to play.

---

### Post by VinDSL on 2013-10-21
> **OGpmpdog said:**
> Let's Do This!!  LTS Breakage Time!!

> **sgage said:**
> No breakage yet!  :-)  But there have been a plethora of updates throughout the day, so breakage soon, no doubt...
Music to my ears!  :D

But, wait.  You said LTS?!?!?

They're usually a snooze.

Oh, well.  We can always hope...

---

### Post by lonniehenry-gmail on 2013-10-22
I have tried 2 different installs of the 64 bit daily iso and the first problem is that if I try to open software sources from software center, synaptic, or software-properties-gtk I get a crash.  From terminal I get 
trusty@trusty-HP-G72-Notebook-PC:~$ software-properties-gtkTraceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 98, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/trusty

This means I can't change repositories, servers,  and add ppas.  I got a system problem, but can't get it to send a report.  Even though my profile shows that I am a noob, actually I have been around since Dapper.   
Thanks in advance for any help.

---

### Post by cariboo on 2013-10-22
@lonniehenry, the solution to your problem is located in [this]("http://ubuntuforums.org/showthread.php?t=2181414&p=12821131&viewfull=1#post12821131") post.

I'll be adding it to the Common Problems wiki page in the next day or two.

---

### Post by cecilpierce on 2013-10-23
@cariboo907

Thanks I had the same problem.

---

### Post by zika on 2013-10-23
> **cariboo907 said:**
> @lonniehenry, the solution to your problem is located in [this]("http://ubuntuforums.org/showthread.php?t=2181414&p=12821131&viewfull=1#post12821131") post.

I'll be adding it to the Common Problems wiki page in the next day or two.That is, among other more serious things just point I was making in several threads about just sed-ing sources.list is not a right and secure way of getting into U+1 wagon...
For those interested key words are: Debian way... You have to prepare that transition and (hopefully) wait for the toolchain... Yes, I was restless couple of times with this transition and I've learned my lesson... Nothing big but, it could make Your perception of transition quite different...
Funny to read that I (of all) am preaching for patience, even I myself can not believe... ;)
It would be nice if complete solution for transition would be put on CPWikiPage...

---

### Post by lonniehenry-gmail on 2013-10-23
Cariboo907,  thank you.  I had this problem years ago and had forgotten how to get by the problem.

---

### Post by ventrical on 2013-10-23
Working great here.
+1

---

### Post by Cavsfan on 2013-10-23
I performed Zitka's fix but, I still get an error about extras:
```
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Err http://extras.ubuntu.com trusty/main Sources
  404  Not Found
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Err http://extras.ubuntu.com trusty/main amd64 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Err http://extras.ubuntu.com trusty/main i386 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com trusty/universe Sources

```
Any ideas?

---

### Post by zika on 2013-10-23
> **Cavsfan said:**
> I performed Zitka's fix but, I still get an error about extras:
```
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Err http://extras.ubuntu.com trusty/main Sources
  404  Not Found
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Err http://extras.ubuntu.com trusty/main amd64 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Err http://extras.ubuntu.com trusty/main i386 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com trusty/universe Sources

```
Any ideas?Of course You do since they are not open yet...
Previously I would use U+0 extras repos... In this case saucy...
Now, I wait... ;)

---

### Post by Cavsfan on 2013-10-23
> **zika said:**
> Of course You do since they are not open yet...
Previously I would use U+0 extras repos... In this case saucy...
Now, I wait... ;)

Figured as much and I already did it. ;) Got a whole bunch of updates. I guess I'll put saucy in it's place.
I tried not to jump into this but, could not help myself.
Thanks for the tip.

---

