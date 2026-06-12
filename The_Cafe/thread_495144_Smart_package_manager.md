---
title: "Smart package manager"
date: 2007-07-07
forum: The Cafe
---

### Post by forrestcupp on 2007-07-07
If the Smart package manager is as great as they say it is, why doesn't Ubuntu use it by default?  And is its dependency management compatible with apt?

---

### Post by Vajra Vrtti on 2007-07-07
Because it is still in beta testing?

---

### Post by ButteBlues on 2007-07-07
Because Debian's repositories are huge and its packaging process is proven?

---

### Post by Vajra Vrtti on 2007-07-07
From the **Smart** FAQ:
> **How stable is Smart?**
It does work pretty good, and has been used either in testing and production environments on many Mandriva, Debian, Fedora Core and Slackware systems. Even though it should mostly work just fine, some features have been more tested than others, and it is possible that important bugs still remain in the code.

---

### Post by 23meg on 2007-07-07
[QUOTE=forrestcupp]If the Smart package manager is as great as they say it is[/QUOTE]

Who are "they"? 

[QUOTE=forrestcupp]why doesn't Ubuntu use it by default?[/QUOTE]

The plan was to integrate Smart into Edgy, but as far as I know, it still messed up in some not-too-uncommon use cases. The main developer is employed by Canonical, and efforts from many leading Ubuntu contributors has gone into Smart; it's quite likely that we'll see it in future releases, but as usual, it's hard to tell which.

---

### Post by forrestcupp on 2007-07-07
> **ButteBlues said:**
> Because Debian's repositories are huge and its packaging process is proven?

From what I can see, smart uses Debian repositories or whatever repos you tell it to.  It's not a packaging system, but rather a package manager.

> **23meg said:**
> 
The plan was to integrate Smart into Edgy, but as far as I know, it still messed up in some not-too-uncommon use cases. The main developer is employed by Canonical, and efforts from many leading Ubuntu contributors has gone into Smart; it's quite likely that we'll see it in future releases, but as usual, it's hard to tell which.
So it isn't dead and we still may see it coming.

Would you say it's dangerous to use now?  And is its dependency management compatible with apt's?

---

### Post by SunnyRabbiera on 2007-07-07
> **forrestcupp said:**
> From what I can see, smart uses Debian repositories or whatever repos you tell it to.  It's not a packaging system, but rather a package manager.

yup, it works fairly well here on PClinuxos but yeh synaptic is better in my opinion.
Smart seems lighter though, but overall I dont think at this stage it is a good replacement

---

### Post by init1 on 2007-07-08
> **forrestcupp said:**
> If the Smart package manager is as great as they say it is, why doesn't Ubuntu use it by default?  And is its dependency management compatible with apt?
I think Synaptic is fine. No reason to replace it.

---

### Post by Polygon on 2007-07-08
"if it aint broke, dont fix it..."

---

### Post by Andrewie on 2007-07-08
> **Polygon said:**
> "if it aint broke, dont fix it..."

just like we didn't have a need for personal computers.

---

### Post by Atomic Dog on 2007-07-08
> **Polygon said:**
> "if it aint broke, dont fix it..."

Yes.  I believe in this philosophy...to a point.  Obviously right now there is little reason to bail on Synaptic.

---

### Post by forrestcupp on 2007-07-08
Well, there are a couple of reasons to bail on Synaptic (and Smart isn't the answer to either).

1. It's based on GTK2, and I use KDE - I know I can use GTK apps, but a good native version would be nice, and Adept isn't a good solution.

2. It uses apt-get instead of aptitude.  With apt-get, Synaptic, and Adept, I can install kde-amusements which is a metapackage for all of the KDE games, educational software, and toys.  Then when I uninstall kde-amusements it only uninstalls the metapackage, but not any of the apps that it actually installed earlier.  With aptitude, it uninstalls everything.

Smart package manager is GTK, but it seamed like it would take care of my #2 problem.  Why isn't there a good GUI based on aptitude?  I know about the command line GUI, but that's a pain to use.

---

### Post by bread eyes on 2007-07-08
> **Vajra Vrtti said:**
> Because it is still in beta testing?

pretty much

---

### Post by ice60 on 2007-07-08
i've used smart for about a year, not on ubuntu though. i seems ok to me, i don't like using the CLI version though and mainly use the GUI

i took a picture

---

### Post by qazwsx on 2007-07-08
> **forrestcupp said:**
> Well, there are a couple of reasons to bail on Synaptic (and Smart isn't the answer to either).

1. It's based on GTK2, and I use KDE - I know I can use GTK apps, but a good native version would be nice, and Adept isn't a good solution.


Kpackage(apt-get install kpackage) ( apt frontend etc ) is actually quite good and has some nice features like some kind of rpm support. Not as good as synpatic  but pretty nice tough.

---

### Post by linux_learner on 2008-04-09
Perhaps reading the book I am working on will help with understanding a few things. I also welcome feedback and questions. The link for the book via html is [here]("http://thecompletecomputerresource.com/main/en/node/26") or if you want to download the book, which is a work in progress, you can find that here [http://downloads.thecompletecomputerresource.com/smart/smartbook.odm](http://downloads.thecompletecomputerresource.com/smart/smartbook.odm)

I did the original documentation over 2 years ago. Now I am trying to improve it.

The QT feature of smart hasn't been done yet, simply because we prefer to improve other features. I personally am working on a revised gui. But that is also in gtk. I do plan, once finished with the gtk revision, to do the qt interface.

---

### Post by hyper_ch on 2008-04-09
> **forrestcupp said:**
> Well, there are a couple of reasons to bail on Synaptic (and Smart isn't the answer to either).

Just you CLI all the way ;)

---

### Post by bone2006 on 2008-04-17
I tried smart package manager on both ubuntu 7.10 and opensuse 10.3 and smart package manager is great on opensuse, but horribly slow on ubuntu.

Just do sudo apt-get install smartpm

make sure you update smart package manager
sudo smart update

then check out the time and compare it to apt-get

$time sudo apt-cache search vlc

then compare it to 

$time sudo smart search vlc

I tried this on 3 boxes, two had flavors of ubuntu and the other one was opensuse 10.3

opensuse -> much faster for smart package manager
ubuntu -> apt-get much faster

I did a lot of testing of not just searching, but actually installing software.  On an ubuntu server system smart package manager was beyond slow.............

So I'm sticking with apt-get/synaptic on ubuntu

---

### Post by ingeon on 2008-12-05
Also using Opensuse1x.x with smart and loving it. One thing though is with smart one can do a complete installation, install extras using smart and since i am a newbie use "smart config --set remove-packages=false" it keeps copies of the rpms so i can do offline installation and pass them to friends and not waste bandwidth everytime i format (bandwidth is a huge issue some places and the time it takes)

Now i thought of using smart on ubuntu for the same reason, but it`s not that easy.
Can i use apt or any other native ubuntu installer to keep copies of offline files to use the same way?
And how?

Any recommendations would be appreciated,

Ref: [http://forums.opensuse.org/archives/sf-archives/archives-software/342000-offline-restricted-format-rpms.html](http://forums.opensuse.org/archives/sf-archives/archives-software/342000-offline-restricted-format-rpms.html)

---

### Post by hyper_ch on 2008-12-05
all downloaded packages are being stored in /var/cache/apt/[archives]

Not sure about the final folder but you'll see it when you go look for it.

---

### Post by Slug71 on 2009-01-10
> **init1 said:**
> I think Synaptic is fine. No reason to replace it.

Correct me if i'm wrong but as i understand, Smart package manager is a backend and therefore replaces APT and NOT Synaptic.

Canonical has been funding Smart since 2005 and has one or more of its developers working on it along with devs. from Mandriva, Fedora and OpenSuse.

C/P from Smart's Website:

> The Smart Package Manager project has the ambitious objective of creating smart and portable algorithms for solving adequately the problem of managing software upgrades and installation. [SIZE="5"]This tool works in all major distributions and will bring notable advantages over native tools currently in use (APT, APT-RPM, YUM, URPMI, etc).[/SIZE]

Notice that this project is not a magical bridge between every distribution in the planet. Instead, this is software offering better package management for these distributions when working with their native packages. Using multiple packaging systems at the same time (like rpm and dpkg) is possible but would require packages from those systems to follow the same packaging guidelines. As this is not the case at the moment, mixing package systems is not recommended.

---

### Post by Slug71 on 2009-01-10
> **init1 said:**
> I think Synaptic is fine. No reason to replace it.

Synaptic will anyhow at least in part be replaced by Packagekit.

Smart Package Manager is already in the repos(smartpm) and so is Packagekit along with the Packagekit backend for Smart.

---

### Post by Slug71 on 2009-01-10
Link to Smart's Website(scroll down to credits to see the parties involved):

[http://labix.org/smart](http://labix.org/smart)


Link to a poll in the Ubuntu Idea Pool:
[http://ubuntuforums.org/showthread.php?t=1036322](http://ubuntuforums.org/showthread.php?t=1036322)


Link to Brainstorm:
[[IMG]http://brainstorm.ubuntu.com/idea/17172/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/17172/)

---

### Post by ingeon on 2009-05-12
> **hyper_ch said:**
> all downloaded packages are being stored in /var/cache/apt/[archives]

Not sure about the final folder but you'll see it when you go look for it.

great, thanks.

I have been using APT and Smartpm and noticed packages in smart that does not appear in APT/Synaptic packet manager.
An example would be Nvidia drivers (did apt-get update and nvidia on 177.xx, did smart channel update and nvidia
on 180.xx. The one right after the other).

I just changed Software Sources to my local country locale after fresh installation,
not sure how to add more channels without typing myself blue every time i want something extra.
Any advice... (both smart and apt).
Lets say i want to add stuff from  [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) which is closest.
I feel a little lost between [archive&indices&pool&project&ubuntu]

I also tried adding a channel in smart but don`t know where to go.
I need some help here please or a point in the right direction.

---

