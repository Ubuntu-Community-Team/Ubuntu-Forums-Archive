---
title: "Different Updates on Multiple Computers"
date: 2020-07-02
forum: The Cafe
---

### Post by sdsurfer on 2020-07-02
I can speculate the answer and have my theories, but perhaps there is a more definitive answer. Priority: -2.

I work with an MSI I built, two System 76 Gazelles and a Dell Precision tower, all four have 18.04 on them. I have automatic updates enabled on all. Of the group the MSI is getting a bit old.

The automatic updates occur very inconsistently. I get them most on the MSI, which "kind of" makes sense, but the two Gazelles and Tower are fairly new. Sometimes it seems like the update prompts are almost daily, then it will go a week or two before another. 

What seems odd is I would expect the update deployment to be approximately around the same times for all, and the same packages, but they are not. For example one may get an update that includes python updates, the next day another machine gets a different set that includes mysql server updates, then the third gets docker updates . . . .they are always different, on different days, and different packages. All four machines run the same **approximate** software, they do not have specified purpose.

I get that update distribution may come at different times, but can anyone shed any light on the disparity of package distribution?

---

### Post by grahammechanical on 2020-07-02
Ubuntu 18.04 is a stable release and so there is a special procedure for updating stable releases. The purpose is to reduce the risk of an upgrade to a package causing instability in the release. Read about it and note section 5 - phasing.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

> Once an package is released to -updates, the update is then phased so  that the update is gradually made available to expanding subsets of  Ubuntu users. This process allows us to automatically monitor for  regressions and halt the update process if any are found.

> The Phased-Update-Percentage is initially set to 10%,  then a job is run (every 6 hours) that checks for regressions and if  none are found the phased update percentage will be incremented by 10%.  So an update will become fully phased after 54 hours or about 2 days. In  the event that a regression is detected the Phased-Update-Precentage  will be set to 0% thereby causing supported package managers  (update-manager) not to install the update. 



Regards

---

### Post by sdsurfer on 2020-07-06
Thank you, that is "kind of" what I presumed about the timing, but what about the disparity of packages? For example, when a specific update would roll out for Windows, you could always watch for it by KB number. With Ubuntu it seems like the packages are always different.

I get that, for example, if one machine has GnuCash (which is the case) only that machine will get GnuCash updates when they roll out. All of the machines have the same Apache 2 and PHP distros, but often they receive different packages, or one machine will never get the package update. It's not that important, but strikes me as odd.

---

### Post by oldfred on 2020-07-06
Do you have the same version of 18.04?
The 18.04 & 18.04.1 use the original kernel and later versions also update kernels.
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Are you using same download server/mirror?
They do not all get updates at same time.
[https://launchpad.net/ubuntu/+archivemirro](https://launchpad.net/ubuntu/+archivemirro)

Do you have any ppas as they override standard updates.
ls -l /etc/apt/sources.list.d/

Or list everything:
Check sources & ppas
find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

---

### Post by sdsurfer on 2020-07-07
Thank you, they are all at 18.04.4 (I think, the older one is off at the moment.) Yesterday that one got two updates, both requiring restart, which is mildly annoying. 

Not sure how to answer the second question, I am referring to the desktop "Software Updates Available" that appears. In Software & Updates, it is configured for "Important Security Updates" and "Recommended Updates." From time to time I run apt update, but only when I'm installing something new. Below is the list on the latest Gazelle. You can see I have a few app-specific sources (GIMP, Slack, Keepass, Docker) not many.

```

/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-bionic.list

     1    deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic main
     2    # deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic main

/etc/apt/sources.list.d/system76-dev-ubuntu-stable-bionic.list

     1    deb http://ppa.launchpad.net/system76-dev/stable/ubuntu bionic main
     2    # deb-src http://ppa.launchpad.net/system76-dev/stable/ubuntu bionic main

/etc/apt/sources.list.d/slack.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb https://packagecloud.io/slacktechnologies/slack/debian/ jessie main

/etc/apt/sources.list.d/jtaylor-ubuntu-keepass-bionic.list

     1    deb http://ppa.launchpad.net/jtaylor/keepass/ubuntu bionic main
     2    # deb-src http://ppa.launchpad.net/jtaylor/keepass/ubuntu bionic main

/etc/apt/sources.list.d/lyzardking-ubuntu-ubuntu-make-bionic.list

     1    deb http://ppa.launchpad.net/lyzardking/ubuntu-make/ubuntu bionic main
     2    # deb-src http://ppa.launchpad.net/lyzardking/ubuntu-make/ubuntu bionic main

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted
     2    deb http://archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse
     3    deb http://security.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse
     4    deb http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse
     5    
     6    deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
     7    # deb-src [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable


```

---

### Post by oldfred on 2020-07-07
I always change to local or faster local mirror.

The ppa's will not just be the application, but all the dependencies for that application. Which in some cases are not much and others can be a lot.

I am not using mirror shown.
I typically click on the check for fastest mirror, but that is based on ping not the download speed shown in link posted above.

---

### Post by sdsurfer on 2020-07-09
Yeah, I just left it at defaults. Never had an issue with speed or update failures, it's just the frequency that has me puzzled.

---

