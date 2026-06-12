---
title: "What's to stop some nasty person sticking rm in a script and deleting important files"
date: 2011-09-18
forum: Security
---

### Post by xahdoom on 2011-09-18
First of all - apologies if this turns out to be a stupid question; I understand that I may be missing something obvious, but I'll ask anyway.

What's to stop someone from hiding an rm command in a bash script - a bash script that advertises itself as being for something useful - and deleting the contents of your home folder?

I know that things like system files are more protected, and the sudo rm command is obligatory, but lets say you download a script (or series of scripts, or an entire program...) that serves a purpose such as installing a driver, program, etc - but some nasty fellow has hidden within it a rm -r ~/ call?

Aside from the answer of not trusting anything you download and meticulously checking all scripts - some of which may be rather obfuscated - what steps could be taken to prevent this?

---

### Post by Porcini M. on 2011-09-18
> **xahdoom said:**
> 
Aside from the answer of not trusting anything you download and meticulously checking all scripts - some of which may be rather obfuscated - what steps could be taken to prevent this?

That's the only answer. Often, you download things to install. Installation requires root access, so you are pretty much handing over the keys to the installation script, which is written by someone other than you.

---

### Post by OpSecShellshock on 2011-09-18
Well you've already pretty much answered it yourself, to be honest. The only way to know is to read it before you run it. If it's obfuscated, ask yourself if it's really necessary. If it's some kind of third-party proprietary thing from a vendor, make sure you're only using the one that came directly from the vendor, or, if you're willing to get fancy/tedious, run it in virtual or on a non-production system first and see what it does.

The only thing that can stop someone from putting that kind of command in a script is for the person who writes the script to decide not to put it in (which is what usually happens, so that's good news).

---

### Post by The Cog on 2011-09-18
Agreed. Every time you download and run software you are taking a risk. 

Stuff posted in these forums would get removed very quickly if it was malicious, but that might only be after people complain, but you might be one of the early users who gets hurt. I guess the same is true for any source, with varying amounts of care from the distributors.

---

### Post by haqking on 2011-09-18
+1 to all the above.

The weakest link in the security of any system is the user, not a product or system.

Only download from trusted sources, if you dont know whether to trust them or if they are trusted then DONT until you can find out if you can.

Linux assumes you know exactly what you are doing, and though sudo exists to help protect and authenticate, if you provide the credentials for sudo then you are doing just that....authenticating and authorising the code whatever that maybe to run.

peace

---

### Post by _d_ on 2011-09-18
> **The Cog said:**
> Every time you download and run software you are taking a risk.

Statement right here applies to any and all OS.

The best defense against such threats is knowledge.

---

### Post by HermanAB on 2011-09-19
Yup, that is one of the reasons why I don't do 'auto update' on my systems.  Once the system is installed and working, I leave it alone and just use it normally.  Instead of updates, I do a fresh install once a year or two.

The risk of an update clobbering something is greater than the benefit of an obscure bug fix that doesn't affect my system anyway.

---

### Post by tgm4883 on 2011-09-19
> **HermanAB said:**
> Yup, that is one of the reasons why I don't do 'auto update' on my systems.  Once the system is installed and working, I leave it alone and just use it normally.  Instead of updates, I do a fresh install once a year or two.

The risk of an update clobbering something is greater than the benefit of an obscure bug fix that doesn't affect my system anyway.

Err, if apt-get is offering you a security update, then it obviously affects your system. Otherwise you wouldn't be getting the update notification. Apt-get doesn't offer updates for things you don't have installed.

---

### Post by HermanAB on 2011-09-20
There are lots of things installed on a desktop machine that I am not using.  There are also lots of bugs that have very little effect on anything.  Therefore, once I installed a machine and is happy with how it performs, I turn the update system off and leave it alone for a year or two or even three.

Servers even more so.  Once I have a server installed and locked down. I leave it alone for the next 5 years or so when I replace the whole thing, or until some piece of hardware fails.  A bug has to be extremely serious (e.g. SSL), before I'll do an update to a server.

You just have to browse these forums a little to see that most problems are due to finger trouble!

---

### Post by Soul-Sing on 2011-09-20
> There are also lots of bugs that have very little effect on anything

How do you decide this a priori? How do you decide which bugfix is relevant?

> A bug has to be extremely serious (e.g. SSL), before I'll do an update to a server.

Again how do you know which is an extremely serious, and relevant one?
(Do you read/study the security related updates?)
Only an expert +++ can imo, so not something to give as an advice for beginners.

---

### Post by tgm4883 on 2011-09-20
> **HermanAB said:**
> There are lots of things installed on a desktop machine that I am not using.  There are also lots of bugs that have very little effect on anything.  Therefore, once I installed a machine and is happy with how it performs, I turn the update system off and leave it alone for a year or two or even three.

Servers even more so.  Once I have a server installed and locked down. I leave it alone for the next 5 years or so when I replace the whole thing, or until some piece of hardware fails.  A bug has to be extremely serious (e.g. SSL), before I'll do an update to a server.

You just have to browse these forums a little to see that most problems are due to finger trouble!

Serious bugs? Looking at [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/) shows that there are a few serious patches. It's your system though.

---

### Post by bodhi.zazen on 2011-09-20
> **leoquant said:**
> How do you decide this a priori? How do you decide which bugfix is relevant?



Again how do you know which is an extremely serious, and relevant one?
(Do you read/study the security related updates?)
Only an expert +++ can imo, so not something to give as an advice for beginners.

I assume he is applying the "If it is not broken, don't fix it" strategy and applying security only updates.

IMO the above advice is very reasonable to give to beginners, many new users run apt-get update multiple times a day.

As I gain more experience, unless an update is marked as security related, I perform non-security updates much less often and only after reviewing the packages to be updated, Certainly new users do not know how to do this, but we, more experienced users should explain it to them.

---

