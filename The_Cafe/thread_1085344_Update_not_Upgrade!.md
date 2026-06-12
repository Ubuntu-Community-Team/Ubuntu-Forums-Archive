---
title: "Update not Upgrade!"
date: 2009-03-02
forum: The Cafe
---

### Post by Dekkon on 2009-03-02
Seriously, why do we have a release every six months if all we are implementing is new themes, software, and possible to changes to the backend software, all of which can be implemented through updates!

If there is new stable software out, shouldn't that software be in the repos? Waiting six months for new features, is ridiculous, and having to update to a new version of that STABLE software manually is inconvenient. 

Am I the only one who thinks this?

---

### Post by kevin11951 on 2009-03-02
> **Dekkon said:**
> Seriously, why do we have a release every six months if all we are implementing is new themes, software, and possible to changes to the backend software, all of which can be implemented through updates!

If there is new stable software out, shouldn't that software be in the repos? Waiting six months for new features, is ridiculous, and having to update to a new version of that STABLE software manually is inconvenient. 

Am I the only one who thinks this?

I think you are defining a "rolling release", look at arch linux.

---

### Post by Dekkon on 2009-03-02
> **kevin11951 said:**
> I think you are defining a "rolling release", look at arch linux.

I thought they were called "Bleeding Edge" distributions but I have heard that term before. 

I was just wondering, if there is a new version of say, Evolution, has reached the stable status, no bugs, no crashes, but you have to wait six months for the next release of Ubuntu, when it could just be pushed through updates.

---

### Post by OutOfReach on 2009-03-03
> **Dekkon said:**
> Seriously, why do we have a release every six months if all we are implementing is new themes, software, and possible to changes to the backend software, all of which can be implemented through updates!

If there is new stable software out, shouldn't that software be in the repos? Waiting six months for new features, is ridiculous, and having to update to a new version of that STABLE software manually is inconvenient. 

Am I the only one who thinks this?

Yeah if you like this kind of idea, rolling release distros are right for you. There's not only Arch Linux that's rolling release there are other distros too that are not as 'bleeding edge' (or at least I would think) out there.

---

### Post by swoll1980 on 2009-03-03
When you upgrade online your basically updating. The new release is more of a recent image than anything else, so people don't have to download a crap ton of updates.

---

### Post by lykwydchykyn on 2009-03-03
There's a logistical problem here you have to look at.  In a Linux distro, you're putting together pieces of software from various sources that have little or nothing to do with each other.  So part of developing a distro is taking these things and tweaking them so that they all work together and aren't causing problems with one another.

On top of that, they have interdependencies with various libraries, standards, languages, etc all of which are evolving constantly.  

So let's say you are the package maintainer for package fiddlefaddle.  Fiddlefaddle is a graphical front-end for various CLI commands written in C that uses GTK and libspackle.  You will need to compile Fiddlefaddle against whatever version of GTK and libspackle that will be on the target system, and you need to make sure it knows what versions of the CLI commands are available (if they are available) in case there are syntax changes in them.  

Now, suppose for licesing issues one of the CLI commands needs to be pulled and replaced with another.  And suppose a new version of libspackle comes out and the maintainer of that package updates it.  Suddenly Fiddlefaddle is broken.

This is why distros like Ubuntu do releases:  they spend a few months agreeing what is to be put in the system, then "freeze" the package selection, and spend a few months working out the bugs and failed interdependecies of the packages.

Rolling release distros have ways of handling these issues, I guess; I won't pretend to know how they do it.  But that's the rationale behind the six-month release schedule.

---

### Post by kevin11951 on 2009-03-03
> **lykwydchykyn said:**
> But that's the rationale behind the six-month release schedule.

Here is another rationale:  The warm feeling of a fresh install with new features just waiting to be used!  :)

---

### Post by mips on 2009-03-03
> **Dekkon said:**
> I thought they were called "Bleeding Edge" distributions but I have heard that term before. 

I was just wondering, if there is a new version of say, Evolution, has reached the stable status, no bugs, no crashes, but you have to wait six months for the next release of Ubuntu, when it could just be pushed through updates.

Rolling release != bleeding edge

Arch for example has repositories Unstable->Testing->Stable so you can use any of those as you please.

The problem with what you are proposing is that newer packages like Evolution might also have newer dependancies so you will have to update these as well. But these dependancies might be common to other apps as well so might cause conflicts .Before you know it you essentially have a rolling release system.

---

### Post by Dragonbite on 2009-03-03
What about, updates available in the repos for LTS versions?  Even if they aren't the latest and greatest, if they are being updated to stable versions every so often while the non-LTS versions are running more "up-to-date" (but not quite bleeding edge) versions then you have a choice. 

For companies and individuals that don't want to update every six months but prefer getting stable updates they can count on then go for LTS.

For more up-to-date systems which also act as a sort-of testbed for the LTS (not to the same degree as Fedora is for Red Hat, but somewhat that concept) then update with the 6 month releases.

*Bleeding Edge means it has the latest version of applications available. Unfortunately bleeding edge doesn't give much room to ensure stability so your mileage may vary (ymmv).  For example I find Fedora more up-to-date with things but until recently their stability was not expected to be too high.*

---

### Post by snowpine on 2009-03-03
A lot of misconceptions in this thread! Ubuntu is not a "rolling release" distribution. Each 6-month release is a "frozen" collection of many parts that are selected and tested to work together. You can upgrade your 8.04 Hardy Heron install until the cows come home, but you will never see OpenOffice 3 (for example) in its repositories. 

A good solution for many users is the "backports" repository. Add it to your sources list, and you will receive newer versions of certain applications once they are tested. It is a good compromise for those who want something newer than the regular Ubuntu repositories provide, but are not willing to switch to a rolling release distro.

---

### Post by Dragonbite on 2009-03-03
> **snowpine said:**
> A lot of misconceptions in this thread! Ubuntu is not a "rolling release" distribution. Each 6-month release is a "frozen" collection of many parts that are selected and tested to work together. You can upgrade your 8.04 Hardy Heron install until the cows come home, but you will never see OpenOffice 3 (for example) in its repositories. 

A good solution for many users is the "backports" repository. Add it to your sources list, and you will receive newer versions of certain applications once they are tested. It is a good compromise for those who want something newer than the regular Ubuntu repositories provide, but are not willing to switch to a rolling release distro.

So, using your example, Hardy will not see OpenOffice 3 even in the backports repository?

---

### Post by snowpine on 2009-03-03
> **Dragonbite said:**
> So, using your example, Hardy will not see OpenOffice 3 even in the backports repository?

You misunderstand; that is exactly the reason why backports exist. (Although I do not specifically know if Canonical plans to ever release OO3 into hardy-backports.)

---

### Post by mips on 2009-03-03
> **Dragonbite said:**
> What about, updates available in the repos for LTS versions?  Even if they aren't the latest and greatest, if they are being updated to stable versions every so often while the non-LTS versions are running more "up-to-date" (but not quite bleeding edge) versions then you have a choice. 

For companies and individuals that don't want to update every six months but prefer getting stable updates they can count on then go for LTS.


So now you want to double the work. Now they have to provide packages for two seprate distro's, I don't see this as feasible.

---

### Post by Dekkon on 2009-03-03
Now I am sure by now you can have more then one version of a library installed? 

Couldn't the Package Manager "Manage" all the library versions and which programs require that version. Say, new version of Evolution is out, but requires new version of libmail installed, but application Thunderbird uses the current version of libmail, so the package manager see's this and installs the new version of the library along side the old version. If no applications use the old version of the library, then update it.

Maybe, there are pluses to DLL Hell on Windows, atleast you get new software when it comes out. Waiting six months is ridiculous.

---

### Post by Vince4Amy on 2009-03-03
Try Fedora or a Rolling release such as Arch, these will be a better option for  you.

---

### Post by Dragonbite on 2009-03-03
> **mips said:**
> So now you want to double the work. Now they have to provide packages for two seprate distro's, I don't see this as feasible.

Enterprises will not want to have to upgrade every 6 months to get a key application like OpenOffice.org upgraded.  While they CAN get OpenOffice.org upgraded manually it then adds a level of possible conflicts with updates that come afterwards and borking the system.

I'm not sure how many enterprises who sign up for the LTS will be willing to loose the longer support for having to re-do all of the desktops every 6 months AND running into the possible conflicts of hardware once supported not being supported anymore without the added overhead of hunting down drivers and making custom configurations.

That brings up one of the positive aspects of Windows that Linux has not overcome yet: people are still using Windows XP in spite of having Vista, and soon-coming Windows 7, and are still able to run up-to-date applications like Office 2007, SQL Server Management Studio 2008 and Visual Studio 2008. I know because that's what I have on my system right now.  

If I need to upgrade to 8.10 then that eliminates any benefit of the LTS except for servers.

Then again, this could all be my misunderstanding of LTS. > [With three years of support and maintenance on the desktop, 8.04 LTS is a great choice for large-scale deployment. ]("http://www.ubuntu.com/news/ubuntu-8.04-lts-desktop")Does this mean they just do security updates and code-cleanup?

---

### Post by mips on 2009-03-03
> **Dekkon said:**
> 
Maybe, there are pluses to DLL Hell on Windows, atleast you get new software when it comes out. Waiting six months is ridiculous.

You don't have to wait, you have choices. You have the choice to use a rolling release distro or a distro with a six month release cycle. No one is forcing you to use Ubuntu. Alternatively there is windows for you and you can choose from WinXP, WinVista & and soon Win7.

---

### Post by Dekkon on 2009-03-03
> **mips said:**
> You don't have to wait, you have choices. You have the choice to use a rolling release distro or a distro with a six month release cycle. No one is forcing you to use Ubuntu. Alternatively there is windows for you and you can choose from WinXP, WinVista & and soon Win7.

Mhm, I completely understand my choices, which is why Fedora is my main distribution. :P

---

### Post by mips on 2009-03-03
> **Dekkon said:**
> Mhm, I completely understand my choices, which is why Fedora is my main distribution. :P

Good for you. Have never tried Fedore though, been stuck on Arch for more than a year now without hopping.

---

### Post by Dragonbite on 2009-03-03
> **Dekkon said:**
> Mhm, I completely understand my choices, which is why Fedora is my main distribution. :P

Yeah, I just installed OpenOffice.org 3.0 a couple nights ago on Fedora. I just wouldn't use Fedora or Arch or any of the 1,000+ non-enterprise-orientated distributions in an Enterprise scenario (well, maybe Fedora but with CentOS on the servers).

---

### Post by BGFG on 2009-03-03
Ok, Slowly now...think about it.
ubuntu is aimed not only at experienced linux users but also at persons altogether new to Linux. It's meant to be friendly and easy. 'Linux for human Beings'

For mid-level to advanced users a rolling release may be the perfect setup, I myself have been diong some heavy research into it lately, but for new inexperienced users a rolling release is simply NOT the way to go.

As any honest Arch or Gentoo user will attest to, rare though it may be, some updates can break a system. When this happens any 'rolling' user worth their salt will simply fix it, but what do you say to the greenhorn ? What exactly do you say when a rolling update breaks networking or the X sever ? again I emphasize, RARE but POSSIBLE.

The Ubuntu model follows sensibility. Release a new, tested by experienced professionals and a technically powerful community, system every six months. make it stable and friendly for the new guy.

'Linux for a Human being' 

how do people not get this ?

---

### Post by mips on 2009-03-03
> **bgfg said:**
> when this happens any 'rolling' user worth their salt will simply fix it, but what do you say to the greenhorn ? What exactly do you say when a rolling update breaks networking or the x sever ?


rtfm???

---

### Post by lykwydchykyn on 2009-03-03
Where I work we have not yet rolled out MS Office 2007; we're still using Office 2003, and some are still using Office XP.  How is having a six-month-old version of OpenOffice a problem by comparison?

I would think that if any reasonably sized "enterprise" needs a backport of OOo3 or any other key application, they can backport it to whatever platform they need by themselves.

For average users, OpenOffice.org releases statically-compiled versions you can install without updating the rest of your OS.

Issues like this are where you get into the meat of what makes a distro different from another; by all means try a rolling release distro and see how it suits you.  There are no perfect scenarios, just things that work better for some people and some situations.

---

### Post by BGFG on 2009-03-03
> **mips said:**
> rtfm???

That almost never works mips :) Besides we're talking about green beans here....

---

### Post by mamamia88 on 2009-03-03
isn't releasing something when it's ready rather forcing it out on a deadline whether done or not?

---

