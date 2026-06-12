---
title: "Update for TOR, FF, Pale Moon BitCoin ect"
date: 2016-12-30
forum: Security
---

### Post by poisonfor3 on 2016-12-30
I use the TOR program its self to check for updates and with FireFox I have a profile manager that lets me use different releases of FF for all kinds of reasons like one just for social networking, one for  downloading, one for testing Addons etc. and they are all different releases. The PaleMoon (oops I said blue moon in title)  browser I am just testing. I have the most up to date LTS Ubuntu Release with Mate. When I run the software updater I get the "failed to download repository" message:

[ATTACH=CONFIG]272912[/ATTACH]

 I would not worry about it (May be do to the LTS) except it is asking for everything that should be my most secure things to be updated and I know the TOR is up to date, I used the program its self to update it. When I do the get update command I get this;

```
root@big-bot:/home/miss# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bitcoin-qt chromium-codecs-ffmpeg-extra firefox gir1.2-unity-5.0
  libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9
  palemoon tor-browser unattended-upgrades
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 156 MB of archives.
After this operation, 5,823 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```

My question is this. Why or what it is trying to do my TOR, FF, bitcoin and stuff? Is this a legit update or some kind of evil thing that got into my computer (Like the the BORG from Star Trek they are real nasty!)? AND if this IS A LEGIT update what is it going to do with my all the different types of firefoxes I have? Is it back end stuff only?

I am not new to computers but a newbie to Linux. Thanks for any info you can provide on this.

-Annie

---

### Post by llamabr on 2016-12-30
Hi. If you're new to ubuntu or linux, there's also a new user forum, which is better populated:
[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)
How did you install these programs you're worried about? If from the repositories, then doing an apt-get upgrade is just upgrading them to the most recent release. You can read the release information about the new versions, and do lots of other cool stuff, with apt and dpkg:
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

The answer is, no, it's doubtful that the borg have taken control of your system. You should definitely do updates frequently, particularly for sensitive programs, because they contain security and feature updates by the package managers.

---

### Post by poisonfor3 on 2017-01-01
I am not new to computers. I know some people just post here first without doing any research but I myself will do hours and hours of research before I ask the on the forums. Sadly most people misunderstand my question because of that.
 
I do thank you for taking the time to respond but it does not answer my question. As you can see above I did the get app update just I do not see what it is doing. By that, my TOR and my other programs say they are up to date but if so why is the get app trying to update them? If you where a black hat evil-doer would not being able to compromise TOR be on the top of your list of to-dos? How do I know the repositories that my computer is going to is the real ones and if so how do I know the repositories themselves have not been computerized? With Windows I could at least find out what the updates where tying to fix. Is this not open source? There should be a way to find out what is trying to update and why I need it and if in fact it is safe. 

I have found that if I post questions like this in the newbie section they just move it over here.

---

### Post by vasa1 on 2017-01-01
> **poisonfor3 said:**
> ...
```
root@big-bot:/home/miss# sudo apt-get upgrade
...
```

... what is it going to do with my all the different types of firefoxes I have? 

...
Why are you using sudo and root? Why not just use sudo as a normal user?

Could you post the output of```
apt-cache policy firefox
``` to give us an idea of what you mean by "all the different types of firefoxes I have"?

---

### Post by poisonfor3 on 2017-01-01
Mmmm that's interesting. Seems like it is updating things that I am not using. 

About running as root I have no good reason. It just opens up that terminal when I click the icon I made.

Lets put firefox and PaleMoon aside right now because I am using a non-stock Profile Manager* for them where I can choose the release as well as the Profile. Palemoon is totally not with the game.**

But the TOR browser is 100% stock. When I click on the check for updates from within Tor-browser it says it is up to date. When I click the about I have "6.0.8 (based on Mozilla Firefox 45.6.0)". Yet I get 

> 
root@big-bot:/home/miss# apt-cache policy tor-browser
tor-browser:
  Installed: 6.0.5-1~webupd8~0
  Candidate: 6.0.6-1~webupd8~0
  Version table:
     6.0.6-1~webupd8~0 500
        500 [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) xenial/main amd64 Packages
 *** 6.0.5-1~webupd8~0 100
        100 /var/lib/dpkg/status

If I understand this it is telling me I have 6.0.5 and it wants to update me to 6.0.6 but I have 6.0.8 up and running what gives?







*[https://ftp.mozilla.org/pub/utilities/profilemanager/1.0/](https://ftp.mozilla.org/pub/utilities/profilemanager/1.0/)

** Pale Moon 
I did the upgrade it said I needed for palemoon as a test and now it says this:

> 
root@big-bot:/home/miss# apt-cache policy palemoon
palemoon:
  Installed: 27.0.3~repack-2
  Candidate: 27.0.3~repack-2
  Version table:
 *** 27.0.3~repack-2 500
        500 [http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04)  Packages
        100 /var/lib/dpkg/status

but when I launch palemoon and click that about it tells me I am running Version: 26.2.2 (x64)

---

