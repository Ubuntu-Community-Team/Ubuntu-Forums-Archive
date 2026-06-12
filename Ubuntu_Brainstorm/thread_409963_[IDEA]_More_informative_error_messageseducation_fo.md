---
title: "[IDEA]: More informative error messages/education for build-essential and ndiswrapper"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-15
**Summary:**
If something like *build-essential* is missing, don't just say *bash make command not found*--tell people they can install *build-essential* off the CD and how to do it.

**Rationale:**
Well, I don't agree with the developers' choice to not include *build-essential* and *ndiswrapper* by default in the installation, and I'm glad they included both on the CDs to install later, but most new users have no idea those packages are available on the CD. So they try to download the packages on a Windows computer and transfer them over. Only later, through a forum thread, do they realize the packages were on their CDs the whole time!

**Scope and Use Cases:**
Affects users who need *build-essential* and/or *ndiswrapper* in order to get an internet connection working.

**Implementation Plan:**
If the wireless card is an unsupported one, there should be some kind of notification that *ndiswrapper* may be needed and then a one-click way to get it installed straight off the CD.

If someone is trying to compile something from source, she should get some kind of message that *build-essential* is required and that the metapackage can be installed off the CD. And since it is supposed a "security risk" to have *build-essential* installed by default (that was the major rationale for not installing it by default), how about a warning indicating that installing it is a security risk and a brief explanation as to what the risk is?

**Blueprint**:
[https://blueprints.launchpad.net/ubuntu/+spec/build-essential-error-message](https://blueprints.launchpad.net/ubuntu/+spec/build-essential-error-message)

---

### Post by =0verlord= on 2007-04-15
Well, unless you put a special case into bash/[your favorite shell], your first request just isn't going to happen.  I agree with you on thinking build-essential should be in the default install, especially since it's already on the CD.

As far as ndiswrapper is concerned, I'd have to take a look at feisty and see how far it got with automating wifi card detection/installation/configuration.  If it still needs work, I'm completely in agreement with you - those cards have caused me more pain then I'd like to admit. :mad:

---

### Post by .t. on 2007-04-15
aysiu, you say "If someone is trying to compile something from source, she should get some kind of message that build-essential is required and that the metapackage can be installed off the CD". Which CD? What kind of message? On feisty, if a user tries to run an application that is not currently installed, then they receive a notice explaining which package to install. As I have build-essential installed and a compile happening at the moment, I could not remove the package to see whether this feature works, say, for GCC. It should at least explain to install the "gcc" package; and maybe a slight alteration to pull build-essential is in order.

As an example: ```
toby@leopard:~/src$ sl
The program 'sl' is currently not installed.  You can install it by typing:
sudo apt-get install sl
Make sure you have the 'universe' component enabled
bash: sl: command not found
```

---

### Post by =0verlord= on 2007-04-15
Are you suggesting bash be linked into apt so every unknown command gets a lookup?  Otherwise I don't see how it could determine between gcc and foobar.

---

### Post by .t. on 2007-04-15
That is how it currently works, yes.

---

### Post by =0verlord= on 2007-04-15
Interesting, it seems I am learning a *ton* about Ubuntu this morning.  So if you try to run gcc it tells you to install build-essential, not gcc?  That's impressive. *golf clap*

---

### Post by .t. on 2007-04-15
No; that's the issue: build-essential isn't required to run GCC. Only the package "gcc" is. I guess there could be some kind of info given, but atm it only (as far as I recall) advises you install "gcc".

---

### Post by =0verlord= on 2007-04-15
Okay so that's a bad example, sorry - I forgot that gcc has it's own package.  My question was more "what if a user tries to run an executable that's not the name of the package it's contained in?"

---

