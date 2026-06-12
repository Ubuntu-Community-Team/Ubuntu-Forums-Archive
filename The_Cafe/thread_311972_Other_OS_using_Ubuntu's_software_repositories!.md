---
title: "Other OS using Ubuntu's software repositories?!"
date: 2006-12-03
forum: The Cafe
---

### Post by drucer on 2006-12-03
Hi, this is interesting. Is Nexenta OS using Ubuntu's software repositories?

Nexenta OS:
[http://www.gnusolaris.org/gswiki](http://www.gnusolaris.org/gswiki)

It sure looks like it is. This is Solaris based OS. I wonder if Mark Shuttleworth knows about this.

---

### Post by Polygon on 2006-12-03
well they could if they wanted to... i mean it is all open source...

but im sure the devs wouldnt be happy about them stealing ubuntu's repository bandwidth though.

---

### Post by IYY on 2006-12-03
This OS is almost 'Ubuntu for Sun systems', so I don't see what's wrong with it. It's not like its competing with Ubuntu.

---

### Post by drucer on 2006-12-03
> **IYY said:**
> This OS is almost 'Ubuntu for Sun systems', so I don't see what's wrong with it. It's not like its competing with Ubuntu.

No, it's not competing with Ubuntu, but I think it's wrong if they are using Canonical's bandwidth if Canonical and Ubuntu team does not know about it.

Not sure if they know about it. Maybe they do. Just wanted to let you guys know about this.

---

### Post by aysiu on 2006-12-03
I think Mepis also uses Ubuntu's repositories.

---

### Post by AndyCooll on 2006-12-03
> **Polygon said:**
> well they could if they wanted to... i mean it is all open source...

but im sure the devs wouldnt be happy about them stealing ubuntu's repository bandwidth though.

The happy or not factor depends on whether they are doing so with Canonicals' blessing. I believe MEPIS folk have such an ok.

:cool:

---

### Post by RAV TUX on 2006-12-03
KNOPPIX 5.0.1 also includes Ubuntu repositories

---

### Post by Iandefor on 2006-12-03
Nexenta is an Ubuntu-based operating system that uses the Solaris kernel. I imagine they would find it easier to use the Ubuntu repositories rather than mirror them for every single update.

Not to mention that Nexenta's userbase is probably small enough that Canonical can take the extra load without too much trouble.

---

### Post by NyquistLimit on 2006-12-03
Is this even legal?

---

### Post by Iandefor on 2006-12-03
> **NyquistLimit said:**
> Is this even legal? Why *wouldn't* it be? These are publicly accessible repositories.

---

### Post by az on 2006-12-03
[https://launchpad.net/people/nexenta](https://launchpad.net/people/nexenta)

Nexenta is a Canonical-sponsored project, AFAIK.  

I am not aware if Mepis uses Ubuntu binaries, or just bases their releases on Ubuntu sources.

---

### Post by nalmeth on 2006-12-03
Linux Mint is using ubuntu's repos aswell, though it is directly a fork, new version containing new artwork.

---

### Post by deanlinkous on 2006-12-03
OH NOOOOO.... someone is downloading something from a public server  - get out! really! Call the law!

---

### Post by Johnsie on 2006-12-04
I'm no expert but I dont think hotlinking is illegal.  It is bad mannered though unless the company providing the bandwidth are benefitting some way :-)

Anyone who uses the same software that we use can help bug fix it and improve it.

---

### Post by mips on 2006-12-04
> **azz said:**
> 
I am not aware if Mepis uses Ubuntu binaries, or just bases their releases on Ubuntu sources.

Mepis uses the ubuntu repos.

Here is the default Mepis sources.list
```
# See sources.list(5) for more information

# This file should be edited through synaptic

# MEPIS improvements, overrides and updates--the MEPIS magic
deb http://apt.mepis.org/6.0/ mepis main 


# Ubuntu foundation packages
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted 
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted 
# Security updates
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted 
# Package updates
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
# Backports of newer packages--unsupported and not thoroughly tested
# deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted 


# Free unsupported packages from Debian and beyond
deb http://archive.ubuntu.com/ubuntu/ dapper universe 
# Non-free unsupported packages from Debian and beyond
deb http://archive.ubuntu.com/ubuntu/ dapper multiverse 
# Backports of newer packages--unsupported and not thoroughly tested
# deb http://archive.ubuntu.com/ubuntu/ dapper-backports universe multiverse


# Penguin Liberation Front--some packages not available elsewhere
# deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
```

---

### Post by givré on 2006-12-04
> **deanlinkous said:**
> OH NOOOOO.... someone is downloading something from a public server  - get out! really! Call the law!
+1


:rolleyes:

---

### Post by PryGuy on 2006-12-04
Sorry for offtopic, but [what wallpaper do they have on this screenie]("http://www.gnusolaris.org/gswiki/ScreenShots?original=nexenta-mplayer-lua-lo&action=content")? Appears to be wicked to me! ;)

---

### Post by deanlinkous on 2006-12-04
I wonder how all that code gets from debian to ubuntu? Certainly they don't download it...do they?

---

### Post by Frak on 2006-12-04
Some of us use Debian repos don't we? And why? Because we support the debian software, because we are a fork of Debian esseintially, and it is downloaded off of a public server for public use. So why can't OS' that are forks or developments of Ubuntu use the same software? The software that is released is basically a gift to the world, free, open source software, that they are modest enough not to charge you for! ;)

---

### Post by mips on 2006-12-04
> **deanlinkous said:**
> I wonder how all that code gets from debian to ubuntu? Certainly they don't download it...do they?

Why not download or mirror it ? Once they have the source they rebuild it for ubuntu, it's not *really* the same as debian but similair.

---

### Post by NyquistLimit on 2006-12-04
> **Iandefor said:**
> Why *wouldn't* it be? These are publicly accessible repositories.
It's one thing for an end-user to be using the repository from the intended platform and another for a competing product to be hotlinking and potentially sapping bandwidth from another organisation without authorisation or accreditation.

---

### Post by deanlinkous on 2006-12-04
> Why not download or mirror it ? Once they have the source they rebuild it for ubuntu, it's not really the same as debian but similair.ahhh glad you cleared that up for me :)

---

### Post by deanlinkous on 2006-12-04
> **NyquistLimit said:**
> It's one thing for an end-user to be using the repository from the intended platform and another for a competing product to be hotlinking and potentially sapping bandwidth from another organisation without authorisation or accreditation.

Thats right! So Ubuntu should stop pulling from debian! How dare they!

I do think it is strange that mepis would simply point to ubuntu repos instead of providing his own. But then again it is warren we are talking about!!!

---

### Post by mips on 2006-12-04
> **NyquistLimit said:**
> It's one thing for an end-user to be using the repository from the intended platform and another for a competing product to be hotlinking and potentially sapping bandwidth from another organisation without authorisation or accreditation.

Ubuntu taking one snapshot of debian would not use nearly as much bandwidth as thousands of user.

It's a public server anyway, free for the taking and the servers/bandwidth is usually sponsored by organisations of some sort.

[http://www.debian.org/mirror/official_sponsors](http://www.debian.org/mirror/official_sponsors)
[http://www.debian.or.jp/Sponsors.html.en](http://www.debian.or.jp/Sponsors.html.en)

---

### Post by deanlinkous on 2006-12-04
> **deanlinkous said:**
> OH NOOOOO.... someone is downloading something from a public server  - get out! really! Call the law!

[COLOR="White"]just joking around okay[/COLOR]

---

### Post by givré on 2006-12-04
> **deanlinkous said:**
> 
I do think it is strange that mepis would simply point to ubuntu repos instead of providing his own. But then again it is warren we are talking about!!!
I also do think that there is some agreements behind that.

---

### Post by NyquistLimit on 2006-12-04
> **mips said:**
> Ubuntu taking one snapshot of debian would not use nearly as much bandwidth as thousands of user.

It's a public server anyway, free for the taking and the servers/bandwidth is usually sponsored by organisations of some sort.

[http://www.debian.org/mirror/official_sponsors](http://www.debian.org/mirror/official_sponsors)
[http://www.debian.or.jp/Sponsors.html.en](http://www.debian.or.jp/Sponsors.html.en)
I wasn't referring to the use of the repositories as a source of data for the developers of the distro, but rather the incorporation of those repositories in the distro for *their* end users to download packages from. e.g. if 10,000 people started using Nexenta they would saturate the Ubuntu repos.

I've just read some more and it's apparent that Nexenta is hosting its own repositories at [http://www.gnusolaris.org/archive/](http://www.gnusolaris.org/archive/). They're not linking to Ubuntu repositories at all....?

---

### Post by -Rick- on 2006-12-04
I doubt they would use ubuntu binaries for a **Solaris** system ... ;)

Anyway... [http://apt.gnusolaris.org/](http://apt.gnusolaris.org/)

---

