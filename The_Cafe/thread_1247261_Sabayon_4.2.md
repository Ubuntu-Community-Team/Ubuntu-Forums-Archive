---
title: "Sabayon 4.2"
date: 2009-08-22
forum: The Cafe
---

### Post by Shibblet on 2009-08-22
I tried my "Linux" hand at Sabayon this last week.  And I have to say that I am quite impressed, especially with the simplicity of the Sulphur package loader.

I'm still a Ubuntu lover though, NBR has a permanent home on my MSI-Wind, and the full version on my laptop.

It's not as simple as Add/Remove you get with Ubuntu, but I can understand it, and it works none-the-less.

In a word, Sabayon is, Performance.  Edit the make.conf file and xorg.conf file, and off you go.

Where I start to falter is compiling.  I don't understand why every time I go to compile something, I get errors.

---

### Post by koleoptero on 2009-08-22
Sabayon looks very interesting. I will give it a try sometime in the near future.

---

### Post by stwschool on 2009-08-22
Sabayon is basically Gentoo made pretty. As for the errors, often it's due to something you depend upon not being there. Care to share those errors so I might be able to hint at what's missing?

---

### Post by Shibblet on 2009-08-24
I got it figured out.  I needed to download "Jam" in order to compile HandBrake.

But I am finding that eBuilds are significantly better for compilations.

---

### Post by HappyFeet on 2009-08-25
> **Shibblet said:**
> I tried my "Linux" hand at Sabayon this last week.  And I have to say that I am quite impressed, especially with the simplicity of the Sulphur package loader.

For me, the sabayon experiment lasted about 40 minutes. I then took mental stock in the fact that I use and enjoy Debian based distros. They just work. It's so much easier to apt-get than anything else. Anyway........

I'm not dissing Gentoo based distros, if you are into that sort of thing, go for it.

---

### Post by Shibblet on 2009-08-25
> **HappyFeet said:**
> For me, the sabayon experiment lasted about 40 minutes. I then took mental stock in the fact that I use and enjoy Debian based distros. They just work. It's so much easier to apt-get than anything else. Anyway........

I'm not dissing Gentoo based distros, if you are into that sort of thing, go for it.

I am beginning to see what you are talking about.  apt-get is REALLY easy to use.

Where I am falling short right now is figuring out how to get Sabayon to install .DEB packages, which I understad is possible.

---

### Post by RATM_Owns on 2009-08-25
Releases?
I use rolling-release distros only. :P

I'll get my own Gentoo and make it pretty. I don't get non-rolling-release distros.

EDIT: Distros can install deb packages, but it's not worth the time and you're better off installing it through the distro's repositories. There is nothing that just installs debs on non-Debian based distros, you convert it yourself into it's own package format (deb is just a gzip'd tarball).

---

### Post by JohnAStebbins on 2009-08-26
Shibblet, if you had to install jam to build handbrake, then you are using a very old version of handbrake (9 months or more).  I suggest you try checking out current svn code or getting the latest snapshot build.

Instructions for building current svn:
[http://trac.handbrake.fr/wiki/CompileGuide#lingui](http://trac.handbrake.fr/wiki/CompileGuide#lingui)

Snapshot link:
[http://handbrake.fr/?article=snapshot](http://handbrake.fr/?article=snapshot)

---

### Post by BrokenKingpin on 2009-08-26
I tried Sabayon a while back and found it far too buggy, but it did have potential. I also found that it just had way to much **** installed by default. I plan on trying the latest release sometime soon though.

---

### Post by HappyFeet on 2009-08-26
> **BrokenKingpin said:**
> I tried Sabayon a while back and found it far too buggy, but it did have potential. I also found that it just had way to much **** installed by default. I plan on trying the latest release sometime soon though.
I agree with sabayon having too much installed by default. I also found the package management lacking and buggy. But, it is after all, based on gentoo. ;)

[IMG]http://www.nyblom.org/pub/gentoo.png[/IMG]

---

### Post by Shibblet on 2009-08-26
HA!  I love the picture.  I am getting less and less enthused with Sabayon.

The package management works fine, but that's binaries only.  And I can't get Handbrake installed.  This time I went for an ebuild, and just can't get the damn thing running.

.DEB packages might not be machine specific, but they flippin' work.  So, Looks like I am going to have a happy reunion with Ubuntu again.

---

### Post by bodhi.zazen on 2009-08-26
Sayabon is nice as is, a live DVD that includes the kitchen sink.

The biggest problems I have with it are :

1. It is not fully compatible with Gentoo. If you like what you see, just install Gentoo.

2. The only way to update, the last time I looked, is to download another DVD and re-install. Terrible waste of bandwidth.

3. Did I mention the bloat factor ?

---

### Post by HappyFeet on 2009-08-26
> **bodhi.zazen said:**
> Sayabon is nice as is, a live DVD that includes the kitchen sink.


I agree. It is actually one of my favorite live discs. I'll break it out once in a while when I want to show someone some real nice eye candy. But I could not use it on a day to day basis.

I'm in too deep with debian to use anything than else. But I do admit that Mandriva comes close. Fedora 11 was good to me also.

---

### Post by Shibblet on 2009-09-02
I really like Sabayon, but I just get to the point where I don't feel like I am using it for it's capabilities.

I really like using Handbrake, and I spent about two weeks trying to get it to run in Sabayon, to no avail.

I like the simplicity of .DEB's, for anything that's not in the general repository.

Sabayon is very command line driven.  And not knowing a lot about Linux or the command line, I feel uncomfortable trying to "emerge" ebuilds.

So it's back to Ubuntu, and pleasant happiness for me.  Anxiously awaiting 9.10 Karmic.

---

