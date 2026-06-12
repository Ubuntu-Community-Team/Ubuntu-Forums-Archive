---
title: "Fresh install vs Upgrade"
date: 2010-04-15
forum: The Cafe
---

### Post by TheNerdAL on 2010-04-15
Which is better and why?

---

### Post by sn0m on 2010-04-15
Well I have upgraded in the past, but sth wasn't right, so ended up doing a fresh install.
My great concern is that I have a home directory which is encrypted and I'm not sure if that will cause problems with a fresh install.

---

### Post by TheNerdAL on 2010-04-15
> **sn0m said:**
> Well I have upgraded in the past, but sth wasn't right, so ended up doing a fresh install.
My great concern is that I have a home directory which is encrypted and I'm not sure if that will cause problems with a fresh install.
 
Yeah, I heard it's better and has less bugs but I don't want to reinstall my programs.

---

### Post by madjr on 2010-04-15
> **TheNerdAL said:**
> Yeah, I heard it's better and has less bugs but I don't want to reinstall my programs.

backup

download live-cd

check ubuntu in virginal state (fresh live session)

go wow

prepare to deflower

upgrade from cd

check everything woiks

iF not you still got live-cd handy

when done spread joy to friends and strangers

---

### Post by TheNerdAL on 2010-04-15
> **madjr said:**
>  
...check ubuntu in virginal state... 

 
How do I do that? Is that the option where it checks for errors?

---

### Post by descendent87 on 2010-04-15
I tend to do a fresh install when it's first released and then as soon as testing for next version begins I upgrade to that all the way until it's released then start with a fresh install again to clear up any mess/config files etc

---

### Post by FuturePilot on 2010-04-15
I've always upgraded and I've never had an issue caused by the upgrade itself. I've upgraded multiple computers multiple times all without problems.

---

### Post by cariboo on 2010-04-15
Upgrading vs Clean Install all depends on your experience level, the first thing to do before putting the Live CD in the drive, or running:

```
upgrade-manager -d
```

is to read the release notes, to see if you have any of the bugs will affect you. Then do a backup of all your important files.

Upgrading has become a lot easier since karmic, as the applet disables all your ppa's before doing anything, then runs a thorough check of what you have installed.

The one thing to keep in mind that an upgrade can take a lot more time than a fresh install. The last upgrade took me about 2.5 hours. as opposed to about 1/2 an hour to do a clean install.

---

### Post by FuturePilot on 2010-04-15
> **cariboo907 said:**
> 

Upgrading has become a lot easier since karmic, as the applet disables all your ppa's before doing anything, then runs a thorough check of what you have installed.
AFAIK it has always done that.

> as opposed to about 1/2 an hour to do a clean install.

But then how much time does it take to restore backups (if any) and reinstall all your programs?

---

### Post by Sonsum on 2010-04-15
A fresh install lets you get some of the neater features, like 9.04's ext4 support and the newer version of GRUB currently.

I upgraded my 9.10 to 10.04 Beta and broke my system (it was my fault). I did a fresh install and man does it boot fast.

I recommend that if you don't have anything to lose, do a fresh install.

---

### Post by FuturePilot on 2010-04-15
> **Sonsum said:**
> A fresh install lets you get some of the neater features, like 9.04's ext4 support and the newer version of GRUB currently.


You can still get all those things with an upgrade. Ext3 can be converted to Ext4 and Grub can also be upgraded.

---

### Post by Sonsum on 2010-04-15
> **FuturePilot said:**
> You can still get all those things with an upgrade. Ext3 can be converted to Ext4 and Grub can also be upgraded.

It can be, but ext4 would only be applied to new system files, and not the pre-existing ones.

---

### Post by FuturePilot on 2010-04-15
> **Sonsum said:**
> It can be, but ext4 would only be applied to new system files, and not the pre-existing ones.

You mean extents. Everything would still be Ext4.

---

### Post by Sonsum on 2010-04-15
> **FuturePilot said:**
> You mean extents. Everything would still be Ext4.

Oh, okay. I guess I was mislead then, I remember being told that if you REALLY wanted the ext4 speed boost, then you'd need a fresh install.

---

### Post by Lightstar on 2010-04-15
> **Sonsum said:**
> Oh, okay. I guess I was mislead then, I remember being told that if you REALLY wanted the ext4 speed boost, then you'd need a fresh install.

Yeah old files will stay in ext3 until they are changed.
Can be changed by an update, rewrite, overwrite, etc.  Then when the file is 'saved' it would be saved in ext4

---

### Post by Otis Spunkmiyer on 2010-04-15
Update is always the safest way to go.  Period !
Why you ask.
Because your PC is already stable to begin with.  All you are really doing is enhancing the packages you already have.

And in case something did go wrong you can simply fall back/roll back to what you had.  People are under the impression that some how 'a virgin' environment makes for a smooth transaction.  Not necessarily, and falls to the minus side of  50 percent.  The only time it is above that is at the factory be loaded.

---

### Post by cariboo on 2010-04-15
There is no way to roll back to a previous version after an upgrade, the only thing you can do is use a previous kernel, which in the case of Lucid may lead to problems.

---

### Post by madjr on 2010-04-15
> **Otis Spunkmiyer said:**
> Update is always the safest way to go.  Period !
Why you ask.
Because your PC is already stable to begin with.  All you are really doing is enhancing the packages you already have.

And in case something did go wrong you can simply fall back/roll back to what you had.  People are under the impression that some how 'a virgin' environment makes for a smooth transaction.  Not necessarily, and falls to the minus side of  50 percent.  The only time it is above that is at the factory be loaded.

you speaking about mac OS w/ time machine or an rollback ready distro like **fedora 13** or NixOS

> found in Fedora 13 is the ability to use the roll-back feature of the **Btrfs file system**: "Btrfs lets you take lightweight snapshots of the file system which can be mounted or booted into selectively. This means that you can easily take a snapshot of the partition and in case something bad happens, just boot into the older snapshot."

[http://linuxers.org/article/some-cool-features-fedora-13-goddard](http://linuxers.org/article/some-cool-features-fedora-13-goddard)


ubuntu with rollback would be best distro

---

### Post by Otis Spunkmiyer on 2010-04-15
Really,,,care for a quick example ?
I'm running Ubuntu NBR, went into Synaptic the other night and loaded up Lucid.  That 'overlay' lasted all of about 15 minutes. (still to many bugs)  Went back into Synaptic's and Wa-LA, I'm a very happy camper again.
Less stress for me and the machine.
That is quite possibly the single over riding feature of Linux vs. Windows.  [U]Synaptic...

*the ironic thing is MS holds the patent on Sudo*
[/U]

---

### Post by madjr on 2010-04-16
> **Otis Spunkmiyer said:**
> Really,,,care for a quick example ?
I'm running Ubuntu NBR, went into Synaptic the other night and loaded up Lucid.  That 'overlay' lasted all of about 15 minutes. (still to many bugs)  Went back into Synaptic's and Wa-LA, I'm a very happy camper again.
Less stress for me and the machine.
That is quite possibly the single over riding feature of Linux vs. Windows.  [U]Synaptic...

*the ironic thing is MS holds the patent on Sudo*
[/U]

you speaking about synaptic, virtualbox or some other progi?

how can you just "Wa-LA" things back?

maybe you can post a pic on how you do it

---

