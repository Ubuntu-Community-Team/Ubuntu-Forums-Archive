---
title: "last daily is really the release"
date: 2017-10-18
forum: Ubuntu Development Version
---

### Post by corradoventu on 2017-10-18
last daily in [http://cdimage.ubuntu.com/ubuntu/daily-live/](http://cdimage.ubuntu.com/ubuntu/daily-live/) is: Ubuntu 17.10 "Artful Aardvark" - Release amd64 (20171017.1)

---

### Post by ajgreeny on 2017-10-18
Is this a statement of fact or are you asking if this is the current situation?

---

### Post by flocculant on 2017-10-18
Ubuntu's desktop image has just started rebuilding (18:28:29 UTC) - so if it was a statement - it's wrong, if it's a question - no.

---

### Post by corradoventu on 2017-10-18
this a statement of fact, I just downloaded and installed and in /var/log/installer/media-info i see: Ubuntu 17.10 "Artful Aardvark" - Release amd64 (20171017.1)
while in the daily i installed few days ago it was: Ubuntu 17.10 "Artful Aardvark" - Beta amd64 (20171011)

---

### Post by flocculant on 2017-10-18
> **corradoventu said:**
> this a statement of fact, I just downloaded and installed and in /var/log/installer/media-info i see: Ubuntu 17.10 "Artful Aardvark" - Release amd64 (20171017.1)
while in the daily i installed few days ago it was: Ubuntu 17.10 "Artful Aardvark" - Beta amd64 (20171011)

Oh right - just talking about what it's called.

It's definitely rebuilding - so what you downloaded is now out of date. Obviously just will need an apt update.

---

### Post by corradoventu on 2017-10-18
just done an update. result:
```
corrado@corrado-artful-p8:~$ sudo apt update
Hit:1 http://it.archive.ubuntu.com/ubuntu artful InRelease
Hit:2 http://it.archive.ubuntu.com/ubuntu artful-updates InRelease      
Hit:3 http://security.ubuntu.com/ubuntu artful-security InRelease       
Hit:4 http://it.archive.ubuntu.com/ubuntu artful-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
corrado@corrado-artful-p8:~$ date
mer 18 ott 2017, 20.44.24, CEST
corrado@corrado-artful-p8:~$ 

```

---

### Post by corradoventu on 2017-10-18
again, to be sure, from main server:
```
corrado@corrado-artful-p8:~$ date
mer 18 ott 2017, 20.56.58, CEST
corrado@corrado-artful-p8:~$ sudo apt update
[sudo] password for corrado: 
Hit:1 http://archive.ubuntu.com/ubuntu artful InRelease
Hit:2 http://archive.ubuntu.com/ubuntu artful-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu artful-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu artful-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
corrado@corrado-artful-p8:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-shell gnome-shell-common
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 842 kB of archives.
After this operation, 12,3 kB disk space will be freed.
Do you want to continue? [Y/n] 

```

---

### Post by Chanath on 2017-10-18
It wasn't updating since morning. Just tried few mins ago. All I get is,
```
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

---

### Post by lisati on 2017-10-18
It will pay to wait for the rebuild to successfully complete and percolate through to the relevant servers. Even though today's technology is a lot better than, say, what was available 10-20 years ago, it still takes time to get some things done.

---

### Post by ventrical on 2017-10-18
On dry gnome I get:

Edit: dry gnome means gnome3 default on wayland, no ppas, no other desktops, no installed apps except default.

```

ventrical@ventrical-MS-7850:~$ sudo apt-get update
[sudo] password for ventrical: 
Get:1 http://archive.ubuntu.com/ubuntu artful InRelease [237 kB]
Hit:2 http://archive.ubuntu.com/ubuntu artful-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu artful-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu artful-security InRelease
Fetched 237 kB in 1s (166 kB/s)
Reading package lists... Done
ventrical@ventrical-MS-7850:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ventrical@ventrical-MS-7850:~$ 

```

so its all updated.

---

### Post by lisati on 2017-10-18
> **ventrical said:**
> <snip>
so its all updated.

^^^This. Seems that we're seeing some signs of progress in the update/rebuild process.

---

### Post by ventrical on 2017-10-18
> **lisati said:**
> ^^^This. Seems that we're seeing some signs of progress in the update/rebuild process.

During development I never use apt. I use default <apt-get update> and <apt-get dist-upgrade>. It has been updating since day one, for me at least.

---

### Post by Chanath on 2017-10-18
Check /etc/issue, etc/issue.net and /etc/lsb-release and /usr/lib/os-release. You'd find Ubuntu 17.10, without (development branch). And, in /usr/share/python-apt/templates, if you want.

---

### Post by corradoventu on 2017-10-19
I can confirm: the daily I installed has the same md5sum: 5eb0631f28384665b57bceffe69c29b0 *artful-desktop-amd64.iso

as the one in [http://releases.ubuntu.com/17.10/](http://releases.ubuntu.com/17.10/)
5eb0631f28384665b57bceffe69c29b0 *ubuntu-17.10-desktop-amd64.iso
be2ab38bb169ed9dddc6cd142a8b9d8b *ubuntu-17.10-server-amd64.iso
429e909e8e7a060f1149013689d62a94 *ubuntu-17.10-server-i386.iso

---

### Post by rrnbtter on 2017-10-19
Greetings,
Use zsync if you need to save bandwidth. The last daily 10/18 only had 72meg of changes (from 10/17).

---

### Post by oldfred on 2017-10-20
Sometime on 18th I zsync'd my daily which I only occassionly update as I normally update my install.
Then copied & renamed to the release and zsync'd that to my local mirror. It showed 0 updates.
I will then copy & rename to 18.04's name & zsync that.

---

### Post by Chanath on 2017-10-20
Quite a silent day for a final release day.

---

### Post by ventrical on 2017-10-20
I have 5 gnome3 installs (which 3 are dry-gnome only) on 5 separate hdds to test on 5 different machines (intel/nvidia) all updated  ready for 18.04. roll over.

Regards..

---

### Post by ventrical on 2017-10-20
> **Chanath said:**
> Quite a silent day for a final release day.

We got to come up for air eh ! :)

Regards..

---

### Post by cariboo on 2017-10-20
Once I do a fresh install, I'll be ready when the tool-chain is uploaded. I plan on using Gnome-shell without the Canonical enhancements. My laptop will be running Xubuntu.

---

### Post by ventrical on 2017-10-20
> **cariboo said:**
> Once I do a fresh install, I'll be ready when the tool-chain is uploaded. I plan on using Gnome-shell without the Canonical enhancements. My laptop will be running Xubuntu.

Thats what I refer to when I say "dry gnome3".

My apologies for any confusion.

regards..

---

### Post by Chanath on 2017-10-20
Something interesting...[https://www.youtube.com/watch?v=YiOeLiegA-k&feature=youtu.be](https://www.youtube.com/watch?v=YiOeLiegA-k&feature=youtu.be)

Another interesting place...[https://www.reddit.com/r/Ubuntu/](https://www.reddit.com/r/Ubuntu/)

---

