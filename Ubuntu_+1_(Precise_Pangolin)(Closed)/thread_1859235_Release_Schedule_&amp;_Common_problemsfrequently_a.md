---
title: "Release Schedule &amp; Common problems/frequently asked questions about testing"
date: 2011-10-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cariboo on 2011-10-13
[**[COLOR="SeaGreen"]RELEASE SCHEDULE[/COLOR]**]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule")

**Common Problems / Frequently Asked Questions About Testing**

Here are answers to some commonly asked questions and solutions to common problems when testing pre-release Ubuntu versions. It will be updated during the testing period as necessary, so you may want to check back. Feel free to post suggestions for things that you think should be included (I won't promise to include them all, since making the document unnecessarily long typically discourages people from reading). 

**How can I upgrade to Precise?**

There's basically no point in upgrading to Precise at this point. It exists as a release in the archive, but isn't open for development, the Debian auto-sync hasn't started, and you can't really do anything useful. Unless you're a toolchain hacker or have special interest in a particular Debian sync issue, it's going to stay this way until after UDS.

That said, if you just want to feel like an early adopter, you can upgrade by replacing all instances of "oneiric" in your /etc/apt/sources.list with "precise", and issuing

```

sudo apt-get update && sudo apt-get dist-upgrade

```

Other methods such as using Update Manager will not be working until around Alpha 1. Be advised that "apt-get dist-upgrade"ing isn't a supported upgrade method for regular upgrades; it's only used in the early stages of a development cycle since it's the only way to upgrade during those periods.

**I already have a testing installation. Do I have to reinstall the latest alpha/beta when it comes out?**

If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the alpha / beta / RC, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix.

The milestone releases (alphas and betas) are slightly stabilized snapshots of the package archive at pre-decided dates, so they reflect the latest state of Precise on those dates. If you're up to date, you already have the latest packages. If you have to reinstall, and have an old disc image, you may want to use zsync to avoid having to download the whole image.

**If I install the alpha/beta now, do I need to reinstall the final version when it's released? **

You don't have to (Update Manager will let you upgrade to the final version), but you may want to, if one or more of the below apply:
[LIST]
[*]You have tweaked your testing installation to a point where you're not aware of its exact components and configuration 

[*]You have replaced essential components of your installation with versions from external repositories/PPAs

[*]You have used package installation scripts or similar tools which are not trusted by the Ubuntu development community

[*]You have applied hacks/workarounds for testing purposes for good reason (prompted during structured testing, bug triage etc.), which may cause problems during daily usage of a stable installation

[*]You're affected by potential corner cases that may require a reinstall to fix (which will be documented in the release notes)
[/LIST]
**Update Manager offers a "Partial Upgrade". What should I do?**

[Read this]("http://ubuntuforums.org/showthread.php?t=1859240").

**When/at what time will the alpha/beta be released?**

Take a look at the release schedule There's no specific time of the day for releases; just wait for the official release announcement, which will be mirrored immediately in the forum with a sticky thread as well.

**I'm trying to report a bug, but I don't know which package it belongs to. What should I do?**

Take a look at the Bugs/FindRightPackage page on the wiki, and try invoking Apport's symptom-based reporting mode by issuing

```

ubuntu-bug

```

with no arguments. If those don't help, feel free to start a thread, or join the #ubuntu-bugs channel on the Freenode IRC network to ask for assistance.

**My testing installation is badly broken. Is there a way to roll back to the stable release, or a relatively stable point in the development branch?**

No. You'll have to fix your installation or do a fresh install.

**I haven't been getting updates for a while. Is it that there's nothing new in P, or is there a problem with the servers?**

The archive mirror you're using is probably lagging behind. You can see the status of the mirrors at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors). Also note that there will be relatively few updates during the freeze periods leading to alpha, beta and RC releases.

**I downloaded the daily CD image, but it's oversized and I can't burn it on a CD.**

The daily images get built automatically, and due to the rapid and asynchronous nature of uploads to the development branch, no effort can be made to make them fit on a CD on a daily basis; such an effort is only made for the milestones. Note that you can still use oversized CD images for testing in a virtual machine.

**Is testing Precise in a virtual machine useful?**

For testing kernels, X, and anything that interacts directly or at a low level with hardware, it's hard to produce useful bug reports. If filing bug reports from virtual machine installs, don't forget that they will be reports about Ubuntu failing to work on that particular virtual machine, and don't forget to indicate that you're testing on a virtual machine in your bug report. While virtual machines are a valid use case, bugs from real hardware are much more useful. If, however, you're only looking to test high-level functionality such as userspace applications, user interfaces, documentation, translations and so on, virtual machines are mostly fine.

---

### Post by vagrale13 on 2011-10-14
The name where must be change the names in *sources.list* is **oneiric** not **oneric**! :popcorn:
This we can do easiest with command
```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
```

---

### Post by cariboo on 2011-10-14
> **vagrale13 said:**
> The name where must be change the names in *sources.list* is **oneiric** not **oneric**! :popcorn:
This we can do easiest with command
```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
```

Thanks, I corrected the error.

---

### Post by raja.genupula on 2011-11-22
What is this ?  Buddy this kind of post you should not place here .

---

### Post by raja.genupula on 2011-11-22
> **cariboo907 said:**
> Thanks, I corrected the error.

@cariboo907

Thanks for the post .It will be helpful to new persons who are stepping to testing  development releases .

---

### Post by Elfy on 2011-11-22
> **raja.genupula said:**
> What is this ?  Buddy this kind of post you should not place here .

spam - report it :)

---

### Post by raja.genupula on 2011-11-23
Yeah ! I am also finding them but i cant delete . I dont have authority to delete them . :D:D:D

Thanks for deleting that .

---

### Post by Elfy on 2011-11-23
We know who can = just use the report button and then someone will see it and deal with it.

---

### Post by raja.genupula on 2011-11-23
Yeah sure man . 
Have a great day a head .

---

### Post by Irihapeti on 2011-11-23
Are there any guidelines about what you should have installed in your testing installation so as to give useful feedback?

Should it be kept as close as possible to an out-of-the-box standard install? Or is it OK to remove and add packages to suit oneself?

What about a custom install with Openbox or other WM, for instance? Would that still be useful?

---

### Post by cariboo on 2011-11-23
As long as you are using Precise as a base, almost anything goes, you'll find people here that do a minimal install and only add what they want, as well as many using gnome shell. We do need more testers for some of the other variants, especially Xubuntu and Kubuntu. There is a fairly active group testing Lubuntu too.

---

### Post by jerrylamos on 2011-11-24
> **cariboo907 said:**
> As long as you are using Precise as a base, almost anything goes, you'll find people here that do a minimal install and only add what they want, as well as many using gnome shell. We do need more testers for some of the other variants, especially Xubuntu and Kubuntu. There is a fairly active group testing Lubuntu too.

I've got newish to old pc's and multiple partitions so I can test whatever ubuntu throws over the wall on the faster ones, but I do prefer Unity-2D's sharp images to Unity-3D fuzzy images and foggy windows, and prefer Lubuntu on 5  to 10 year old notebooks.  

Even on an older notebook with a 20 GB hard drive I've got 3 Ubuntu installs.  For recovery always a stable example Lucid Lynx (Fast!  Easy!) plus daily updates on a couple Precise Pangolin variants. 

Ubuntu development "unstable" install & grub are usually ripe areas for bugs (including partition slaughter) so I'll try installs on my usb hard drive come Alpha 1 time.

As Ubuntu becomes gains more weight (my view obese sluggish eye candy) and exceeds CD size I'm getting into minimal install plus what this ordinary user does with internet, office write, network file sharing, etc.

Best part is the forums...

Jerry

---

### Post by PaulW2U on 2011-11-24
> **cariboo907 said:**
> We do need more testers for some of the other variants, especially Xubuntu and Kubuntu.

Indeed, I've felt quite lonely in here at times. I've even had to re-install Ubuntu to follow what you're all talking about. :D

But seriously, anyone testing Kubuntu should report bugs to the [KDE Bug Tracking System](http://bugs.kde.org/) as well as Launchpad as KDE specific problems may also be seen by users of other distributions. I've seen some KDE bugs that haven't been reported in Launchpad at all but the fixes have eventually filtered through to Kubuntu.

Xubuntu testers could also report to [Xfce's Bugzilla](https://bugzilla.xfce.org/).

---

### Post by ventrical on 2011-11-25
> **cariboo907 said:**
> As long as you are using Precise as a base, almost anything goes, you'll find people here that do a minimal install and only add what they want, as well as many using gnome shell. We do need more testers for some of the other variants, especially Xubuntu and Kubuntu. There is a fairly active group testing Lubuntu too.


  I successfully upgraded Edubuntu 11.04 (natty) to 11.10 (Oneiric) , installed 3.2 kernel and works great.

  I don't hear much about it .. but it is like  one of the hidden treasures or well kept secrets of Canonical :)

---

### Post by ventrical on 2011-11-25
***ALL YOU BETA TESTERS :)**

If you are a modder or have some hardware experience then  remember to install some extra fans about your processor and video adapters cards.  I fried a Dell Dimension tower lastnight . My own fault, I had the cart before the horse .. thought I could push that little Celeron to the limit without a fan-change.

Just be ready!

:)

---

### Post by cbowman57 on 2011-11-25
I've been running Precise I built from a mini.iso so I could have a Gnome-only installation.

Observation: Installed with an alternate daily so I could do some simple Raid striping & was pleasantly surprised to see that it installed Unity2 & 3D, as well as Gnome shell & fallback.

Question: Is that the plan for 12.04 LTS, both Unity & Gnome on the desktop iso?

---

### Post by kevpan815 on 2012-01-15
Sorry Cariboo907, but I need 2 stick with Ubuntu Alpha 1, because I use a rather strange Internet Connection Setup where I share my Apple IPhone 4 WIFI Personal Hotspot with Ubuntu Alpha 1. That said, I also own an older Dell Dimension 8400 (same computer as the other guy), however, so far I have been unable 2 get most of these newer Ubuntu Builds 2 run on it. Alpha 1 runs just fine on my other 2 Dell's however.

---

### Post by Sylslay on 2012-02-25
I mean that after updates we has whole bunch off 

1) Old kernels that are still on HDD.
2) Synatpic has loads of files kept in cache. (about 1GB for forthnight)

PS> I was use for this purpose "Ubuntu Tweak",

but if I delete  "old an config files" then more like very clean OS will brakdown :-) :-) :-(,

What is the best way to keep clean  Ubuntu from old updates???

THX for script: jerrylamos

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by cariboo on 2012-02-25
> **Sylslay said:**
> I mean that after updates we has whole bunch off 

1) Old kernels that are still on HDD.
2) Synatpic has loads of files kept in cache. (about 1GB for forthnight)

PS> I was use for this purpose "Ubuntu Tweak",

but if I delete  "old an config files" then more like very clean OS will brakdown :-) :-) :-(,

What is the best way to keep clean  Ubuntu from old updates???

All debian based distributions archive downloaded packages, to clean them out, open a terminal and type the following command:

```
sudo apt-get clean
```

to remove dependencies no longer needed use this command:

```
sudo apt-get autoremove
```

Synaptic should list old kernels as obsolete, it's OK to remove them using synaptic, I'd suggest you keep one old kernel, just in case there is a problem with the newest one.

---

### Post by jerrylamos on 2012-02-26
After an update, I run an exec:

gedit clean

#! /bin/bash
echo "apt-get clean, autoclean, autoremove"
df
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
df
exit 0

Shows size before & after.

It does not remove the last linux image, so when I'm booted on a new image after an update I do:

to find out what image(s) could be left over:
ls /boot

To see what image is in use:
cat /proc/version

To clear out previous image if this one's working:
sudo apt-get remove linux-image-3.2.0-16-generic

Could be ...generic-pae

In spite of all that, used bytes can increase so an occasional install cleans things up,  Beta's coming.

Enjoy.

Jerry

---

### Post by NHclimber on 2012-02-26
With the Precise Beta 1 test cycle started, maybe the OP would be kind enough to edit the "**How can I upgrade to Precise?**" section to link to here: [http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade](http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade).

---

### Post by Sylslay on 2012-03-02
Someone post an improve ./clean script 
POST all version of "brainstorming"

We start at
Home folder 
cd ~
gedit clean


> #! /bin/bash
echo "apt-get clean, autoclean, autoremove"
df
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
df
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
exit 0

then run it form home folder
sudo ./clean

THX to all

Is anyone know how to change this line for keeping 2 kernels in OS, I mean newest and one before in case system will break down on latest kernel???

dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge

I am looking for more safety clean, one kernel in system is not enoguh, just in case some thing go wrong with wi-fi, sound or graphic driver.

---

### Post by cariboo on 2012-03-02
@Sylslay, you forgot to make the command executable:

```
chmod +x clean
```

---

### Post by mikodo on 2012-03-12
> **PaulW2U said:**
> But seriously, anyone testing Kubuntu should report bugs to the [KDE Bug Tracking System]("http://bugs.kde.org/")  as well as Launchpad as KDE specific problems may also be seen by users  of other distributions. I've seen some KDE bugs that haven't been  reported in Launchpad at all but the fixes have eventually filtered  through to Kubuntu.

Xubuntu testers could also report to [Xfce's Bugzilla]("https://bugzilla.xfce.org/").


I thought this shouldn't be necessary, as this is the function of the [Bug Squad.]("https://wiki.ubuntu.com/BugSquad")

A bug-triaging schemata from the [Bug Squad's KnowledgeBase]("https://wiki.ubuntu.com/Bugs/HowToTriage/Charts"), showing bug reports, triaged and being sent upstream.

Are not bugs specific, to upstreams like KDE and Xfce, forwarded to them? Wouldn't reporting to both, cause redundancy?

I'll be happy to start with both, if it is best practice.

Thanks.

---

### Post by mikodo on 2012-03-19
> **mikodo said:**
> I thought this shouldn't be necessary, as this is the function of the [Bug Squad.]("https://wiki.ubuntu.com/BugSquad")

A bug-triaging schemata from the [Bug Squad's KnowledgeBase]("https://wiki.ubuntu.com/Bugs/HowToTriage/Charts"), showing bug reports, triaged and being sent upstream.

Are not bugs specific, to upstreams like KDE and Xfce, forwarded to them? Wouldn't reporting to both, cause redundancy?

I'll be happy to start with both, if it is best practice.

Thanks.Why oh why, would a question like this, quoting an earlier post in the thread, not be answered in a FAQ thread?

---

### Post by effenberg0x0 on 2012-03-19
> **mikodo said:**
> Why oh why, would a question like this, quoting an earlier post in the thread, not be answered in a FAQ thread?

Although most people won't read anything, this sub-forum could probably use a single and very well designed and comprehensive omnibus FAQ sticky thread. But there's a limited number of regulars (less than 60 according to what I have been researching) and, within this group, not enough people willing to contribute creating content. Also, many of them are already involved with other testing-related activities and drown deep into QA short-term needs

We can easily get away with the fact that almost all questions here are not related to Development Releases and, therefore, already covered in Ubuntu Wiki documentation and threads at "General Help". But, in parallel, we have an ongoing effort to build such FAQ at the [U+1 Team Tester Wiki]("https://wiki.ubuntu.com/U+1/tester-wiki") (currently being developed single-handedly and heroically by [Ventrical]("http://ubuntuforums.org/member.php?u=1140838")).

Regards,
Effenberg

---

### Post by mikodo on 2012-03-19
> **effenberg0x0 said:**
> Although most people won't read anything, this sub-forum could probably use a single and very well designed and comprehensive omnibus FAQ sticky thread. But there's a limited number of regulars (less than 60 according to what I have been researching) and, within this group, not enough people willing to contribute creating content. Also, many of them are already involved with other testing-related activities and drown deep into QA short-term needs

We can easily get away with the fact that almost all questions here are not related to Development Releases and, therefore, already covered in Ubuntu Wiki documentation and threads at "General Help". But, in parallel, we have an ongoing effort to build such FAQ at the [U+1 Team Tester Wiki]("https://wiki.ubuntu.com/U+1/tester-wiki") (currently being developed single-handedly and heroically by [Ventrical]("http://ubuntuforums.org/member.php?u=1140838")).

Regards,
Effenberg

Thank you, for taking the time and giving the effort to respond. I agree with you, Testing and Reporting Bugs, is not something that comes intuitively, but through learning, and attempting to follow written advice. Exactly, where I am at!

Mike

---

### Post by cariboo on 2012-03-19
I have to admit, I missed your question, about upstream bugs. Launchpad has improved quite a bit over the last year or so, but there are still some warts here and there. That being said, at times there still is a need for a member to post the bug to the upstream, but those times are getting fewer and fewer.

You will usually be informed by one of the bug triagers when it is a good idea to send the bug upstream. Just as a point of interest, the very first bug I sent upstream, took almost 3 years to get solved.

---

### Post by mikodo on 2012-03-20
> **cariboo907 said:**
> I have to admit, I missed your question, about upstream bugs. Launchpad has improved quite a bit over the last year or so, but there are still some warts here and there. That being said, at times there still is a need for a member to post the bug to the upstream, but those times are getting fewer and fewer.

You will usually be informed by one of the bug triagers when it is a good idea to send the bug upstream. Just as a point of interest, the very first bug I sent upstream, took almost 3 years to get solved.
Thank you, for your response and advice.

When I am up to speed, in writing good bug reports, I'll wait upon any triagers, to give any direction to, before filing any bug reports, upstream.

---

### Post by jokop on 2012-03-29
I am an old newbie
Ive upgraded my 11.10 to 12.04  and doing partial upgrade everytime im asked about it (I know now I shouldnt do that generally)
now my ubuntu 12.04 version is a bit corrupted after a partial upgrade to 3.2.0.20 my 12.04 now have  no launch bar at the left and no reaction  to  alt-tab keys (should show the current applications list) and some more drawbacks
so I now ive restarted the computer in 12.04 ubuntu in 3.2.0.18 generic pae  and it works ok except that launch bar is not vanishing and constantly shown
i can live with that
but how should i upgrade to the stable 12.04 ubuntu release that should come out in end of april?
shoul i upgrade  from my 12.04 version?
should i first  fix the packages or somthing before upgrading?

---

### Post by cariboo on 2012-03-29
I had the same problem, yesterday's update of Unity solved my problems.

---

