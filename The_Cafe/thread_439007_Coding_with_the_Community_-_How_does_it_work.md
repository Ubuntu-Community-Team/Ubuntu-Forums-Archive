---
title: "Coding with the Community - How does it work?"
date: 2007-05-10
forum: The Cafe
---

### Post by BarfBag on 2007-05-10
Just trying to figure out how things work around here.

Let's say there's an annoying bug in Ubuntu that everybody wants fixed.  What if everybody wrote a patch correcting the bug and submitted it at the same time?  That would mean the efforts of most of the people who put aside time to write the code would be wasted.  How does this work?  What measures are in place to prevent this?

Let's get a little more complicated.  Suppose I wanted to do a major coding change in the Ubuntu desktop.  If I submitted the code, would it be put in the official code; or would I be pointed upstream to the Gnome project?

Here's an almost unrelated question.  I hate how some of the packages are behind in the repos (particularily Wesnoth and Gaim/Pidgin).  If I compile them and make .debs, could I submit them to the repos to have them updated?

---

### Post by maniacmusician on 2007-05-10
> **BarfBag said:**
> Just trying to figure out how things work around here.

Let's say there's an annoying bug in Ubuntu that everybody wants fixed.  What if everybody wrote a patch correcting the bug and submitted it at the same time?  That would mean the efforts of most of the people who put aside time to write the code would be wasted.  How does this work?  What measures are in place to prevent this?
If it's such a huge bug that everyone wants it fixed, it's likely that the developers will take care of it themselves. If various people submit a patch, I'd assume the one that gets accepted is the one with the cleanest code or the one that works the best.
> **BarfBag said:**
> Let's get a little more complicated.  Suppose I wanted to do a major coding change in the Ubuntu desktop.  If I submitted the code, would it be put in the official code; or would I be pointed upstream to the Gnome project?
That's a bit dreamy. Large organizations generally won't accept major code changes from just any john doe out there. Open source gives you the freedom to modify the code, but it doesn't ensure that the people who developed the code will merge it back into their application. But yes, if the major changes you propose have to do mainly with the Gnome environment, they will of course ask you to work with upstream on that project. 

To be honest, you should only consider major contributions of code if you're on the dev team. The community effort is usually focused around things like patches and bugfixes, or developing new applications to add to Ubuntu. Upstart and the restricted drivers manager are good examples of these.
> **BarfBag said:**
> Here's an almost unrelated question.  I hate how some of the packages are behind in the repos (particularily Wesnoth and Gaim/Pidgin).  If I compile them and make .debs, could I submit them to the repos to have them updated?

No. You can submit the source code for those things and submit them to the MOTU for them to package. Wouldn't get your hopes up though, as they're quite busy. There's a saying about this; If you want to get a package into Ubuntu, the fastest way is to become a MOTU and do it yourself :). 

Ubuntu generally does not update its repos in between releases. At each release, the MOTU import a large number of packages from the Debian repos, which are usually pretty up to date. But if you want to try out a package in between releases, the best way to really do that is to get the package from a third party source like getdeb.com or to compile it yourself.

---

### Post by rai4shu2 on 2007-05-10
You can just fork the project and create your own web site, etc. Or you can just read this: [https://wiki.ubuntu.com/UbuntuDevelopers](https://wiki.ubuntu.com/UbuntuDevelopers)

---

### Post by Tomosaur on 2007-05-10
Ahh, a common misconception:

Although open-source software can be modified by everyone - the patch has to be resubmitted back to the main developers if it is to be included in the main tree. The developers will check through the patches, and commit the best of the best. Occasionally they may compile a patch using features from more than one. If your patch doesn't get included into the main trunk, then it's just tough luck really. Only the best gets in.

On Ubuntu - the developers use [http://www.launchpad.net](http://www.launchpad.net). There you can submit bugs / patches / anything to do with the development of Ubuntu.

There is actually a bit of controversy with Ubuntu using launchpad - many of the fixes and such don't go into the main trunk of a project (say, Gnome), they only get applied to Ubuntu. In essence, some people view launchpad as 'forking' projects. I'm sure this isn't the intention, it's just that there have been a few oversights etc. The 'right thing to do' is to submit your patches to the main project upstream, but many of the packages for Ubuntu are customised and thus some patches are only relevant to whatever version Ubuntu uses.

The reasons some packages are old versions are many, here's just a few:

1) The sheer size of the Ubuntu repositories means that keeping absolutely everything up to date is virtually impossible.
2) By 'freezing' on a particular version - it ensures that the possibility of conflicts is limited. The modular nature of Linux means that updating some packages to the latest version may cause problems with other packages. Granted, care is taken to prevent this within most projects - but by freezing at particular versions of the software, the risk is even more limited.
3) Many of the packages are customised for Ubuntu to ensure compatibility and integration with the Ubuntu environment. The developers can't possibly keep up with the rate of change in many projects, so it's easier to stay a few versions back than it is to immediately put the updated software into the repos.
4) Updates are not always perfect. If everything in the Ubuntu repos was bleeding edge, then the risk of serious bugs and other problems, is greatly increased. By being relaxed about updating, the devs can make sure that when they DO update, most of the bugs in the software have been ironed out, thus saving themselves a lot of work.

---

