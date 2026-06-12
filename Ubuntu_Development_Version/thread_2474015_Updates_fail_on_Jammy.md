---
title: "Updates fail on Jammy"
date: 2022-04-20
forum: Ubuntu Development Version
---

### Post by wildmanne39 on 2022-04-20
I installed Jammy last week and updates have failed ever since, it shows the updates are from a ppa which seems odd to me and it is considered a security risk so by default ppa's have been disabled, have other users updated from a ppa? I installed the Beta version from the official Ubuntu site, any suggestions? I can wait until tomorrow when Jammy is released and I am guessing I will be able to update then also I was not able to remove the ppa as for the remove button is grayed out this also concerns me.

Thanks

---

### Post by #&amp;thj^% on 2022-04-20
What shows on:
```
sudo apt upgrade
```
if it helps my sources;
```
 Active apt repos in: /etc/apt/sources.list
    1: deb http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
    2: deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    3: deb http://us.archive.ubuntu.com/ubuntu/ jammy universe
    4: deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
    5: deb http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
    6: deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    7: deb http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    8: deb http://security.ubuntu.com/ubuntu jammy-security main restricted
    9: deb http://security.ubuntu.com/ubuntu jammy-security universe
    10: deb http://security.ubuntu.com/ubuntu jammy-security multiverse

```

---

### Post by Frogs Hair on 2022-04-20
I just updated my U-Budgie without issue and the only PPAS  I see on my sources list are from the U-Budgie team as part of development .

---

### Post by ajgreeny on 2022-04-20
I have just updated my Xubuntu jammy and have no PPAs showing in the terminal output.
Just out of interest, what was the PPA that was so strangely enabled?

Have you tried using command line```
sudo add-apt-repository -r ppa-address
``` to try removing that PPA or simply deleting the appropriate file in /etc/apt/sources.list.d?

---

### Post by Doug S on 2022-04-20
I haven't had an issue. I installed my 22.04 desktop VM quest on a Debian server host in early December. There were a flurry of updates some days ago, but none for couple of days now.

```
doug@desk-jj:~/ubuntu-help/z$ [COLOR="#FF0000"]sudo apt update[/COLOR]
Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy InRelease [270 kB]
Hit:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:4 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease
Get:5 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 DEP-11 Metadata [423 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu jammy/universe i386 Packages [7,491 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages [14.1 MB]
Get:8 http://ca.archive.ubuntu.com/ubuntu jammy/universe Translation-en [5,651 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 DEP-11 Metadata [3,562 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu jammy/multiverse amd64 DEP-11 Metadata [42.3 kB]
Fetched 31.5 MB in 7s (4,514 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
doug@desk-jj:~/ubuntu-help/z$ [COLOR="#FF0000"]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04 LTS
Release:        22.04
Codename:       jammy
doug@desk-jj:~/ubuntu-help/z$
```

---

### Post by Claus7 on 2022-04-20
Hello,

> **wildmanne39 said:**
> I installed Jammy last week and updates have failed ever since, it shows the updates are from a ppa which seems odd to me and it is considered a security risk so by default ppa's have been disabled, have other users updated from a ppa? I installed the Beta version from the official Ubuntu site, any suggestions? I can wait until tomorrow when Jammy is released and I am guessing I will be able to update then also I was not able to remove the ppa as for the remove button is grayed out this also concerns me.

Thanks

I'm getting issues with updates from ppa from the very beginning I upgraded. The OS Name under settings is jammy without the word development for a couple of days now. I have just disabled ppa's thinking that still, officially, jammy is not released yet, that's why there is an issue with them.

Regards!

---

### Post by wildmanne39 on 2022-04-20
This is the site I downloaded Jammy beta from:

[https://releases.ubuntu.com/22.04/](https://releases.ubuntu.com/22.04/)

it looks like the official site but I could be wrong.

This is the ppa:

[https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/](https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/)

Notice the date of the last modification:

2020-10-25 21:26 	

His launchpad page:

[https://launchpad.net/~micahflee](https://launchpad.net/~micahflee)

No Karma at all, I believe this needs to be reported, it does look like I can remove the ppa's now, when you click on the parent directory it takes you to his launchpad page.

Looks like he may have been active at one time but not now and the fact that it says Jammy clear back from 2020 is puzzling, unless they already knew what the name was going to be then.

---

### Post by #&amp;thj^% on 2022-04-20
> **wildmanne39 said:**
> This is the site I download Jammy beta from:

[https://releases.ubuntu.com/22.04/](https://releases.ubuntu.com/22.04/)

it looks like the official site but I could be wrong.



Same page I used for the DL.
> **wildmanne39 said:**
> 

This is the ppa:

[https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/](https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/)

Notice the date of the last modification:

2020-10-25 21:26 	

His launchpad page:

[https://launchpad.net/~micahflee](https://launchpad.net/~micahflee)

No Karma at all, I believe this needs to be reported, it does look like I can remove the ppa's now, when you click on the parent directory it takes you to his launchpad page.

Looks like he may have been active at one time but not now and the fact that it says Jammy clear back from 2020 is puzzling, unless they already knew what the name was going to be then.
Yep I'd report that one.
_No shown version for Jammy_ 
current mods were done on 2021-02-26 08:06
> Sorry, there's no software in this PPA at the moment.

If you're looking for OnionShare, install using Snapcraft at: [https://snapcraft.io/onionshare](https://snapcraft.io/onionshare) or Flatpak at: [https://flathub.org/apps/details/org.onionshare.OnionShare](https://flathub.org/apps/details/org.onionshare.OnionShare)

If you're looking for Tor Browser Launcher, install using Flatpak at: [https://flathub.org/apps/details/com.github.micahflee.torbrowser-launcher](https://flathub.org/apps/details/com.github.micahflee.torbrowser-launcher)

If you're looking for PDF Redact Tools, it's no longer maintained. Use Dangerzone instead: [https://dangerzone.rocks/](https://dangerzone.rocks/)

---

### Post by wildmanne39 on 2022-04-20
I'm not real sure the best place to report this, the dev M/L? / CC M/L? I can email the CC, I would usually ping them on irc also but my laptop crashed and I have not got irc back to running yet.

---

### Post by #&amp;thj^% on 2022-04-20
PM"jbicha"

---

### Post by wildmanne39 on 2022-04-20
> **1fallen said:**
> PM jerrmy "jbicha"

Great minds, I saw him online and just finished a pm to him.

---

### Post by #&amp;thj^% on 2022-04-20
> **wildmanne39 said:**
> Great minds, I saw him online and just finished a pm to him.

Us old farts rock. :lolflag:

---

### Post by jbicha on 2022-04-20
Please provide more details. What is the exact error message you are getting?

I think we need the output of a command like this too:
```

cat /etc/apt/sources.list.d/*

```

---

### Post by wildmanne39 on 2022-04-20
The out put of:
```
cat /etc/apt/sources.list.d/*

deb https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/ jammy main
deb-src https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/ jammy main
deb https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/ jammy main
# deb-src https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/ jammy main


```
The errors when I try to update are:
```
Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease               

Get:2 http://us.archive.ubuntu.com/ubuntu jammy InRelease [270 kB]             

Ign:3 https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu jammy InRelease    

Hit:4 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease              

Hit:5 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease

Get:6 http://us.archive.ubuntu.com/ubuntu jammy/universe i386 Packages [7,476 kB]

Err:7 https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu jammy Release      

  404  Not Found [IP: 91.189.95.85 443]

Get:8 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages [14.1 MB]

Get:9 http://us.archive.ubuntu.com/ubuntu jammy/universe Translation-en [5,651 kB]

Get:10 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 c-n-f Metadata [286 kB]

Get:11 http://us.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages [217 kB]

Reading package lists... Done                                                  

E: The repository 'https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu jammy Release' does not have a Release file.

N: Updating from such a repository can't be done securely, and is therefore disabled by default.

```
I should be able to remove the ppa's I believe and resolve the issue but my concerns is also if you look at the ppa's the users launchpad page that there may be some nefarious intentions going on here or at the very least a user that is not active anymore and his ppa's are causing update issues.

Edit:

This information is from a previous post of mine.

This is the ppa:

[https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/](https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu/)

Notice the date of the last modification:

2020-10-25 21:26 	

His launchpad page:

[https://launchpad.net/~micahflee](https://launchpad.net/~micahflee)

No Karma at all, I believe this needs to be reported, it does look like I can remove the ppa's now, when you click on the parent directory it takes you to his launchpad page.

Looks like he may have been active at one time but not now and the fact that it says Jammy clear back from 2020 is puzzling, unless they already knew what the name was going to be then.

Thank you for your reply.

---

### Post by jbicha on 2022-04-20
All the error is saying that it wasn't updated for jammy. Very few PPAs are. There's nothing suspicious about that.

Apparently, you enabled the PPA, maybe a long time ago. Perhaps you forgot about it or maybe not.

If you just remove that file, the errors should go away.


I recommend running ppa-purge on all PPAs before upgrading to a new Ubuntu release. You might not need them any more.

PPAs can cause various upgrade problems. I recommend using Snap packages (or Flatpaks) instead as they don't interfere with the rest of your system and can easily be removed.

Some Snaps like Firefox are especially awesome as you can easily switch between different channels if you want to try Beta or ESR. That was never supported with the normal Firefox apt package.

---

### Post by wildmanne39 on 2022-04-20
I did a fresh install of Jammy:
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy

```
I was just trying to install updates for Jammy when I received that error, I did not install any ppa's for some reason it was there when I installed Jammy, I have not installed ppa's in a few years.

I will remove them and see if the updates work as they should afterwards.

Thank you

---

### Post by #&amp;thj^% on 2022-04-20
> **jbicha said:**
> 
Some Snaps like Firefox are especially awesome as you can easily switch between different channels if you want to try Beta or ESR. That was never supported with the normal Firefox apt package.

your a snappy salesman. ;) (pun intended)

---

### Post by jbicha on 2022-04-21
> **wildmanne39 said:**
> I did a fresh install of Jammy:


By default, if you install to the same partition where you previously installed Ubuntu, the installer doesn't format the partition and still keeps whatever was in `/etc/` before. Maybe that's what happened here?

---

