---
title: "Fundamental differences between version releases?"
date: 2007-04-17
forum: The Cafe
---

### Post by Rush_898 on 2007-04-17
I believe I understand the basic differences between distros.  The basic linux kernal is built up with modules for hardware support, packaging philosophies, update methods, default packages, and, extremely important, the community surrounding.  Plus a thousand other things.  Please correct this if I am off base.

My question to the community at large is; what are the common factors for each release?  

examples and thoughts...

Will the same .deb's work for breezy, dapper, edgy, and feisty?  How can you tell?  (I know this may be a question riddled with ignorance but...) will configure/make/make install always work for packages on all releases?  Is it better to keep a repository (say backup disk) of my apps in .tar.gz format to compile?  Does the $PATH or location of certain system files change, is this documented somewhere?  Is it mostly default packages and options like graphics toys and application updates?  How much should I have to re-learn for each release?


I am asking this for a few reasons.  

1.  I think it is good to have a general idea of whether a tutorial I may find from previous releases is going to also work for Feisty/Future Releases

2.  When I am trying to encourage someone to use Ubuntu I want to be able to accurately explain what the    difference in releases is and why waiting or not waiting is a factor worth looking at.


Thanks.

---

### Post by aysiu on 2007-04-17
In answer to your numbered concerns:

1. There's no easy way to tell. Some tutorials might work in all versions. Some might not. Some might work in all versions but be unnecessary in newer versions.

2. Newer releases usually have newer versions of the same software, different software to replace old software, more software available to easily install, more graphical configuration options, different installation tools and defaults, different or better artwork and icons... just about anything you can think of.

---

### Post by use a name on 2007-04-17
> **Rush_898 said:**
> 
Will the same .deb's work for breezy, dapper, edgy, and feisty?  How can you tell?  (I know this may be a question riddled with ignorance but...) will configure/make/make install always work for packages on all releases?  Is it better to keep a repository (say backup disk) of my apps in .tar.gz format to compile?  Does the $PATH or location of certain system files change, is this documented somewhere?  Is it mostly default packages and options like graphics toys and application updates?  How much should I have to re-learn for each release?


.deb will probably work, as dependencies will be calculated.
Configure/make/make install will not always work, as some of these are dependent on older kernels (I'm talking about drivers and the like here, not normal apps). In my experience, when something suddenly is not compatible with your kernel anymore, there is no need to build the package anymore as its functionality is included in the newer kernel (might require rebuilding the kernel though).
For normal apps, that you installed/built from an archive, you can redo that in a new install.
$PATH: dunno...
In Feisty, hardware support is greatly improved over Edgy. That's the big deal with Feisty.
Relearn: nothing.

---

### Post by aysiu on 2007-04-17
Some .deb files will work. Some won't. It depends what dependencies the .deb requires. If it requires higher versions of some libraries than what you have installed, it could be a nightmare installing the incorrect version .deb file.

---

### Post by Rush_898 on 2007-04-17
Cool stuff, thanks.  On the .deb's I have seen situations where packages from an old versions were said to work w/ a newer release.  It's good to know tho, that it could get really sticky trying to make it happen if it isn't meant to be.  I know I had a lot of inquiry in that post.  I appreciate the info.  A general understanding of this kind of stuff helps immensely.

---

### Post by use a name on 2007-04-17
> **aysiu said:**
> Some .deb files will work. Some won't. It depends what dependencies the .deb requires. If it requires higher versions of some libraries than what you have installed, it could be a nightmare installing the incorrect version .deb file.

Yes, in that case it won't work, of course. Then you'll have to wait for the higher versions to come into the reps.

Could it also be the other way around? That a ..deb is dependent on an now obsolete library? I've seen some dummy packages to assure backwards compatibility, but I do not know what the coverage of this is.

I said that you may find problems with archives that are for drivers and the like, but that's merely what I perceive. Most apps I use are mainstream and quite up-to-date and do not require odd/obsolete libraries.

---

### Post by TheMono on 2007-04-20
You do get some interesting effects when you install a deb for an older version on a newer version - for example, with the Beryl SVN repository for Edgy, some were using it on Feisty. However, Edgy uses Python 2.4 and Feisty uses Python 2.5, so there were some workarounds you had to use to make it work.

In short, Aysiu has the best answer - there is no way to tell if a deb will work without trying it. Even if you examine the package and it will work in theory, that is still no guarantee.

---

### Post by forrestcupp on 2007-04-20
Also, some deb's that were packaged generally, and not specifically for your distro, might put files in other places than the ones from our repos would.  For instance, most executable application files are placed in /usr/bin or /usr/games for games.  I installed a deb file for Ardour2 that is not made specifically for Ubuntu, and it placed the executable file in /usr/local/bin.  It still works, I just had to find it first to run it.

---

