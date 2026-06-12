---
title: "Pacman"
date: 2008-01-17
forum: The Cafe
---

### Post by JR Tyner on 2008-01-17
Pacman is a software package manager, developed for Arch Linux, is also used by AegeanLinux and Frugalware.

Could it also be used with various forms of Ubuntu?

---

### Post by Joeb454 on 2008-01-17
I'm not sure how installing a different package manager would work.

Out of curiosity...what's wrong with apt and synaptic?

---

### Post by JR Tyner on 2008-01-17
Nothing, just curious.

I heard of Pacman, and I was told it is capable of resolving dependencies and automatically downloading and installing all necessary packages for mutliple Lixux Operating Systems.

Got me curious, that's all.

---

### Post by Joeb454 on 2008-01-17
Ah fair enough :)

For what its worth, I believe apt/synaptic also resolve and download the dependencies as well :) Hopefully somebody with a bit more knowledge than me will come along and help you :)

---

### Post by JR Tyner on 2008-01-17
You get a gold star anyway.

I've heard that Pacman can upgrade your OS with one command.

Personally, this sounds like hipe and some people trying to pat their own backs. I came here for the truth.

---

### Post by billgoldberg on 2008-01-17
upgrading in ubuntu is done with one command, unless i'm missing something.

```
sudo apt-get update
```

---

### Post by JR Tyner on 2008-01-17
So, I was right? It is all hype?

---

### Post by Drakx on 2008-01-17
pacman -Syu does upgrade the entire system i should know I've done it already

---

### Post by Xavieran on 2008-01-17
Actually,I find that pacman installs things lightning fast!(or is that just cause I'm running Arch? :))

pacman -Syu Upgrades your entire system...Arch linux uses a rolling release cycle,that means that it doesn't have set releases, but it is continually adding new versions of things...

---

### Post by kellemes on 2008-01-17
> **billgoldberg said:**
> upgrading in ubuntu is done with one command, unless i'm missing something.

```
sudo apt-get update
```

apt-get update is for syncing the local package db..
apt-get upgrade **or**
apt-get dist-upgrade for dist upgrades.. obviously ;-)

---

### Post by meborc on 2008-01-17
actually there is only one command to update your ubuntubox also:```
sudo apt-get update && sudo apt-get dist-upgrade
``` :)

i admire what arch linux developers have done with pacman... i have used it and i can assure you it is faster than any package manager i have ever used... only thing is that when searching for something it gives 2 lines of output per one package... the first line is name and version and the second is description (correct me if i am wrong, it has been a while when i used it) so if there are more then 20 results and you are using a small terminal screen you must scroll all the time

this might be my problem of not using pacman the correct way, so please, if you are interested, you can try it... you need to install arch though :) i don't think there is a safe way to replace apt with pacman, the result would be a disaster :D

---

### Post by Onyros on 2008-01-17
It's not hype, but the fact that Pacman is able to "upgrade" the entire OS with one command has nothing to do with Pacman itself. It is related to the fact that Arch has a rolling release system, unlike Ubuntu.

Meaning, in Ubuntu, every six months you have to update your repos to reflect the fact that you're using a different release. In Arch, repos are always the same, it just keeps on updating packages on a (very) regular basis.

And that's why Arch is better installed with a simple FTP install, rather than using a "frozen" version. Chances are if you using a base install, you'll end up having to update the included packages anyway.

If I leave an Arch installation unattended for a few weeks, I'll surely have a few (not so few) MiB of updates to download whenever I "Pacman -Syu".

Months without updating will mean hundreds of MiB. Then again, if your system is stable enough, there might not be a need to update, anyway.

---

### Post by kellemes on 2008-01-17
> **Onyros said:**
> If I leave an Arch installation unattended for a few weeks, I'll surely have a few (not so few) MiB of updates to download whenever I "Pacman -Syu".


I made the mistake of doing a pacman -Syu after about 2 months of inactivity (was abroad for this period). This upgraded a hole lot of critical packages giving me crap. :)
But this is the risk of living on the bleeding edge I guess.

---

### Post by JR Tyner on 2008-01-17
](*,)

---

### Post by tehet on 2008-01-17
> **Xavieran said:**
> Actually,I find that pacman installs things lightning fast!
In my (limited) Arch experience I found pacman significantly slower than apt. But maybe the Arch repos just aren't on a fast connection.

---

### Post by K.Mandla on 2008-01-17
> **tehet said:**
> In my (limited) Arch experience I found pacman significantly slower than apt. But maybe the Arch repos just aren't on a fast connection.
It was possibly the repos, if you mean the download speed. Actual installation -- the time it takes to unpack and put into place -- is far faster than aptitude or apt-get. For me at least. :D

---

### Post by notwen on 2008-01-17
Pacman could be used for Ubuntu's package manager, but would probably have issues w/ dpkg.  You could read more about it [here]("http://www.archlinux.org/pacman/").  Here's a [wiki page]("http://en.wikipedia.org/wiki/Package_management_system") to give you an more thorough idea of how package management works.  I've used a couple different ones, Fedora's RPM, Open SUSE's Yast, CentOS' YUM(cmd line rpm), but have found I like dpkg/apt(deb) over the other options.  I currently run Debian Etch on my file servers and Ubuntu on my daily usage PCs and laptops.  Arch is a very customizable distro nearly rivaling Gentoo(as far as customizing your install), but a bit easier to get up & running.  Hope you find this useful. =]

---

### Post by forrestcupp on 2008-01-17
I'll bet that you could find more projects out there that create deb's for Ubuntu than you could that create packages for pacman.  It's great for Arch, but if you're using Ubuntu, you're better off using what's made for Ubuntu.

---

### Post by Johnsie on 2008-01-17
Awww... I thought this thread was about the game Pacman :-(

---

### Post by tehet on 2008-01-17
> **K.Mandla said:**
> It was possibly the repos, if you mean the download speed. Actual installation -- the time it takes to unpack and put into place -- is far faster than aptitude or apt-get. For me at least. :D
Yep, I meant downloading, not the actual installing, my bad :). So it probably says nothing about pacman in a technical sense, but in practice dl-ing was the bottle neck for me.

---

### Post by Drakx on 2008-01-17
> **tehet said:**
> Yep, I meant downloading, not the actual installing, my bad :). So it probably says nothing about pacman in a technical sense, but in practice dl-ing was the bottle neck for me.

Did you download from archlinux.org ? though it does say its capped at 50kb/s

---

### Post by Pandemic187 on 2008-01-17
> **meborc said:**
> this might be my problem of not using pacman the correct way, so please, if you are interested, you can try it... you need to install arch though :) i don't think there is a safe way to replace apt with pacman, the result would be a disaster :D
Gosh...I tried installing Arch once. That didn't go so well...

---

### Post by tehet on 2008-01-17
> Did you download from archlinux.org ?
I can't remeber, but if that's the default then yes.
> though it does say its capped at 50kb/s
That would explain it :) thnx for the info.

---

