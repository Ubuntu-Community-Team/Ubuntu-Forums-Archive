---
title: "better explanation to users needed"
date: 2016-05-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Swiftjay on 2016-05-03
I have 16.04 installed and when I turned on my laptop the past two days I got a message important security os and software updates are available.  I check my software update package and nothing shows up.  However, on a whim I went to the software centre and there was an update stating this.  

Ubuntu should be more clearer how to obtain these updates to users or at least explain go to to the software centre to update.  Just a personal opinion

---

### Post by VE6EFR on 2016-05-03
I agree. I too stumbled on this popup. I opened software updater and it said that my computer was up to date. Seems odd that now we have to check two places for updates to make sure our systems are current.

---

### Post by Bucky Ball on 2016-05-03
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not support. This is the place for opinion.

It's 16.04, been out for, what, two or three weeks? Give it time. Many of us don't go to a new LTS until a few months in (and the official upgrade is not offered until after the first point release, which will be a few months).

Teething problems are common with new releases. If you want to avoid them, wait a couple or three months after release.

---

### Post by Swiftjay on 2016-05-03
@bucky While I'd agree with a .10 release a LTS release is suppose to be solid from the start, I agree there are always teething problems but things like this should be explained.  If I'm going to have to go to my "app store" like Mac to do security updates from now on, it would be nice to get a circle highlight on my software centre to let me know updates are available.  Hopefully this gets resolved in time.

---

### Post by vasa1 on 2016-05-03
I rely on the old-fashioned *sudo apt-get update* followed by *sudo apt-get dist-upgrade*.

---

### Post by NikTh on 2016-05-03
> **vasa1 said:**
> I rely on the old-fashioned *sudo apt-get update* followed by *sudo apt-get dist-upgrade*.
Me too. Although "dist-upgrade" needs attention because it can remove software. First read, then hit Y(es) or N(o). 

However OP has right, others have right also. 
There are some bugs in 16.04 that should be corrected. Release Notes describe these bugs and everyone should read Release Notes before upgrade.
For Ubuntu Software, [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Ubuntu_Software](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Ubuntu_Software)
That's a new implementation of GNOME software inside Ubuntu. Give it time. At least until July when the first point release comes out. (16.04.1)

---

### Post by grahammechanical on 2016-05-03
Comments about LTS releases and stability are correct but we do need to take into account a couple of things. It seems that some additions to the LTS had to be made at the last minute otherwise they would not get into the LTS. At least two of these additions were unfinished products.

If the developers had waited until Gnome Software was polished & fully fitted out it would not now be in Ubuntu 16.04 LTS. Apparently there is a need for an application store that is compatible with AppStream and the Ubuntu Software Centre would have needed a complete re-write to bring that about. Bringing in Gnome Software has made 16.04 more useful. Not bringing it in due to lack of time would have saddled 16.04 with Ubuntu Software Centre for 5 years.

The second addition that I am referring to is the running of snap packaged apps in Unity 7 on 16.04. That too is a work in progress. There are next to no useful snap apps to install. So, why bring it in now? Because it is an LTS & it cannot be brought in a year later. So, the foundation is laid for the future.

Besides, 16.04 is stable. Nobody's OS is going to break because these two additions are not finished and polished. Upgrading Ubuntu Software will take place naturally and the upgrade will not break anyone's OS.

As I pointed out in some other thread, there have always been more than one location from which a user could start off the system upgrade process. They are different front ends to the Apt commands.

Regards.

---

### Post by kansasnoob on 2016-05-03
Yep, what I said [here]("http://ubuntuforums.org/showthread.php?t=2310398&page=9&p=13463032#post13463032"):

> Also software management and automated updates are a bloody mess in both Ubuntu and Ubuntu GNOME 16.04!


IMHO they should have pulled a Dapper and delayed this a couple of months, meaning we had a 6.06, why not a 16.06?

I'll grant you that people like me know how to check for and install updates, but things need to be simple enough for anyone to just install and use an OS without wondering what to do. And the lack of intuitive & user friendly updates presents a true security risk :(

---

### Post by montag dp on 2016-05-03
It always seemed to me like a fixed release cycle causes more problems than it is worth; namely, either including software that's not ready yet or excluding it when it would be ready in a short time. Both problems would be avoided by simply delaying the release. But I can see why commercial-backed distros might want to do a fixed release to ensure constant progress is being made.

---

### Post by QIII on 2016-05-03
Anybody know what happens when you delay release until everything is right?

Anyone heard of "feature creep"?

How do you all react if an anticipated event is delayed?

I release software on my clients' schedules -- as free of bugs as possible -- with the full knowledge that something will be wrong.

The other choice is missing my clients' delivery expectations.  Even worse, I might never release because it would never be right.

---

### Post by pfeiffep on 2016-05-03
Since there are many Xenial bugs reported in  Launchpad I'm planning on using apt to keep my system current at least  until 16.04.1 is released. 
Instead of manually typing the commands  required I made a small script named sapt [for sudo apt] 
1) Contents
  ```
#!/bin/bash
sudo apt update 
sudo apt upgrade
sudo apt autoremove 
```
2) after saving to your directory change permissions
```
chmod 755 sapt
```
3) test it
```
./sapt
```
  4) if it runs correctly move it ~/bin
a) if directory ~/bin doesn't exist make it
```
mkdir bin
```
b) then move it
```
mv sapt bin
```
  Next time you want to update your system open a terminal and type sapt [assuming you used the names in this example]

---

### Post by vasa1 on 2016-05-03
> **NikTh said:**
> Me too. Although "dist-upgrade" needs attention because it can remove software. First read, then hit Y(es) or N(o). 
...
Hi Nik, it's been a while!

You're right! Read, understand and then press Y/n. The same applies to autoremove. man apt in 16.04 has this:>        autoremove (apt-get(8))
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed as dependencies changed or the package(s) needing them
           were removed in the meantime.

           **You should check** that the list does not include applications you have
           grown to like even though they were once installed just as a
           dependency of another package. You can mark such a package as manually
           installed by using apt-mark(8). Packages which you have installed
           explicitly via install are also never proposed for automatic removal.
with emphasis added


> **Swiftjay said:**
> I have 16.04 installed ...
Ubuntu should be more clearer how to obtain these updates to users or at least explain go to to the software centre to update.  Just a personal opinion
You maybe aware of this but it needs mentioning anyway... There just aren't enough testers of pre-release versions.

---

### Post by kansasnoob on 2016-05-05
Ubuntu MATE still sensibly displays the availability of updates in (or next to) the window list in the panel:

[ATTACH=CONFIG]268863[/ATTACH]

I hope by 16.04.1 Ubuntu might start displaying them in the launcher again but since it was a design decision I have doubts.

---

### Post by SantaFe on 2016-05-05
> **pfeiffep said:**
> Since there are many Xenial bugs reported in  Launchpad I'm planning on using apt to keep my system current at least  until 16.04.1 is released. 
Instead of manually typing the commands  required I made a small script named sapt [for sudo apt] 


Me too, except I made a file called .bash_aliases & let bashrc do the same thing.
```

alias DUpdate='sudo apt update && sudo apt dist-upgrade'
alias Clean='sudo apt autoremove && sudo apt autoclean'

```

---

