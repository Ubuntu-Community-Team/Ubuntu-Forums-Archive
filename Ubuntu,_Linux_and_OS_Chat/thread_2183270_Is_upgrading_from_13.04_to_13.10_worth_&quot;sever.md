---
title: "Is upgrading from 13.04 to 13.10 worth &quot;several hours&quot; install??"
date: 2013-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by ripx2 on 2013-10-24
Got the option, then picked it...but them it said it would be an hour to download all the things that will change and that the upgrade installation could take up to several hours...is it worth it? Im really worried about my virtualbox as Ive read it breaks with every upgrade and ive got both a registed win 7 and office that i use regularly.

thoughts???

---

### Post by TheFu on 2013-10-24
Well, you don't really have any choice.
Support for 13.04 ends in January and running a non-supported/non-patched OS really isn't an option.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) for reference.

There is a very good reason to run LTS releases.

---

### Post by buzzingrobot on 2013-10-24
What kind of net link do you have?  Upgrading over dialup would, I'd imagine, take a very long time.  Over a broadband link, not very long. (I can download the entire install image in 4-5 minutes, depending on the mirror used.  I've found that downloads from Ubuntu links rotate through a succession of mirrors, so if I stop a slow download and start another one, I often see a large speed boost.  There is also a function in the software and updates tool to select the fastest available mirror.)

If bandwidth is the issue, and you do want to move to 13.10, then perhaps just finding time to download the 13.10 ISO and doing a clean install might be best.  That way, if there are problems, you have the install DVD/USB and can start over.  If a live upgrade goes bad, you're stuck with no install DVD/USB and the prospect of more long hours of another live upgrade attempt.

Is 13.10 worth upgrading *right now*?  Frankly, if you don't have problems that you know 13.10 fixes.,probably not.  It's a modest incremental improvement, plus some new stufff going on with scopes and lenses (which you may or may not want, in any case.) 

(BTW, upgrading via slow low-bandwidth connections is an issue for all Linux distributions.  They are all built around an assumption that users have fast broadband connections.)

---

### Post by craig10x on 2013-10-24
If you only run one ubuntu, then download the iso...see if it offers you the option to upgrade on the installer...if it does, use that...it will only take about 20-25 minutes that way...

For me the upgrades from the installer have worked pretty darn well...and it installs everything directly from the iso instead of having to go to the internet...
You can read about my experience here:
[http://ubuntuforums.org/showthread.php?t=2181643](http://ubuntuforums.org/showthread.php?t=2181643)

---

### Post by ikt on 2013-10-24
> **ripx2 said:**
> Got the option, then picked it...but them it said it would be an hour to download all the things that will change and that the upgrade installation could take up to several hours...is it worth it? Im really worried about my virtualbox as Ive read it breaks with every upgrade and ive got both a registed win 7 and office that i use regularly.

thoughts???

What are you doing on your ubuntu virtualbox?

As others have suggested if you don't need to update all the time go with 12.04 LTS, but if you're running on 12.10-13.10, upgrading is something you're going to need to do.

---

### Post by help_me2 on 2013-10-25
That's why I do fresh install every time. I use a flash drive and it only takes 7 minutes. I keep the same home folder, which makes things nice and easy. And then I spend another 15min or so tweaking and reinstalling apps. Easy peasy.

---

### Post by craig10x on 2013-10-26
Fresh installs don't take long....but it's more a matter of how many programs and data you have...if you have a lot of stuff, and you have a good upgrade, it can save a lot of extra work...
but if you don't have much, then a fresh install would be the way to go...

---

### Post by john_ferrier on 2013-10-26
I suggest you just hold for one or two months. Ubuntu 13.10 is buggy, if you have a look at the bug reports on Launchpad, I am sure your'll be frightened. For Ubuntu, the .10 versions were actually beta versions of .04 versions, and Canonical's current foucus on their phones and tablet makes it even worse. Unity is only developped and supported by Canonical, things are just getting worse and worse like rolling a snow ball!

---

### Post by rrnbtter on 2013-10-26
Greetings,
Regarding VirtualBox, I just installed the VirtualBox included in the Trusty development version Software Center and it opened my Windows 7 VM just perfect. I have been using the same Windows 7 VDI file since Natty or before. I keep a backup without all of the software installed just in case I have a problem. In the couple of years since I created it I haven't needed to use it.  VirtualBox may get broken for a short period but that has nothing to do with the VDI file that is the virtual HD. Usually you can just regress a version and be back in business. I have a 700meg scaled version of Windows 7 that I use so my VDI file is only 10 Gig software and all. I keep all of my downloads and installers on my Trusty /Home so as not to take up space in the VM. FYI

---

### Post by eyTkT7Y on 2013-10-26
> **ripx2 said:**
> Got the option, then picked it...but them it said it would be an hour to download all the things that will change and that the upgrade installation could take up to several hours...is it worth it? Im really worried about my virtualbox as Ive read it breaks with every upgrade and ive got both a registed win 7 and office that i use regularly.

I just installed 13.10 this morning. VirtualBox 4.3 is working fine. The VirtualBox saucy repository isn't ready yet, so I just used the raring one. Worked like a peach!

---

### Post by eyTkT7Y on 2013-10-26
> **john_ferrier said:**
> I suggest you just hold for one or two months. Ubuntu 13.10 is buggy, if you have a look at the bug reports on Launchpad, I am sure your'll be frightened. For Ubuntu, the .10 versions were actually beta versions of .04 versions, and Canonical's current foucus on their phones and tablet makes it even worse. Unity is only developped and supported by Canonical, things are just getting worse and worse like rolling a snow ball!

Ouch. That doesn't sound good. My new install of 13.10 is working very well. But it's still early. :)

---

### Post by llanitedave on 2013-10-27
> **eyTkT7Y said:**
> Ouch. That doesn't sound good. 

It doesn't sound realistic either.

> 
My new install of 13.10 is working very well. But it's still early. :)

It doesn't wear out.  If it's working now, chances are it will keep working.

---

### Post by craig10x on 2013-10-27
It doesn't wear out?  That's good to know ;) :D

---

### Post by Erik1984 on 2013-10-27
I guess it depends on your setup. With a seperate /home you could do a fresh install and still have your data in place. If you have to copy all data over and reinstall / reconfigure all kind of applications then an upgrade is probably worth the time. I did an upgrade from Kubuntu 13.04 to 13.10 and the desktop looked 99% the same after upgrading (one icon in the systray changed :P) All programs and settings were still in place. Definitely worth the time for me.

---

### Post by craig10x on 2013-10-27
@Euroman: yeah...that's why i use the upgrade (on the installer iso) way myself now...saves me like a day or two work putting all my programs back on, settings, data, etc...a real time saver...just a few minor tweaks and good to go! :D

For years i only did the clean install method...didn't mind that part...it was having to put all that stuff back on again...what a difference!
And nice part about doing it with installer...very fast (like 20 minutes or so)...gets it right from the iso (not the internet)...

---

### Post by monkeybrain20122 on 2013-10-27
> **craig10x said:**
> Fresh installs don't take long....but it's more a matter of how many programs and data you have...if you have a lot of stuff, and you have a good upgrade, it can save a lot of extra work...
but if you don't have much, then a fresh install would be the way to go...


If you have a separate /home partition you don't need to worry about data and settings. Just install into the / partition. Reinstalling all the programs would still be faster than an upgrade, but there is also a way to automate it too if that is too much trouble. [http://www.webupd8.org/2010/03/2-ways-of-reinstalling-all-of-your.html](http://www.webupd8.org/2010/03/2-ways-of-reinstalling-all-of-your.html) (the first method)

I always do clean install.

---

### Post by craig10x on 2013-10-27
Looked at link...that is very interesting....but this iso installer upgrade sure looks and feels like a fresh install...i saw it cleaning out a lot excess toward the end and then it put back the programs and data at the very end...while i don't think i'd want to chance things with the software updater upgrade method, i feel very confident using the iso installer method without any reservation...

---

### Post by ssam on 2013-10-28
If you install ubuntu to an existing partition it will preserve the home directory (as long as you don't tell it to format that partition)
.[http://okolovich.info/how-to-reinstall-ubuntu-over-existing-installation-while-preserving-home/](http://okolovich.info/how-to-reinstall-ubuntu-over-existing-installation-while-preserving-home/)

(of course you should always have a backup before doing an install)

---

### Post by monkeybrain20122 on 2013-10-28
> **eyTkT7Y said:**
> I just installed 13.10 this morning. VirtualBox 4.3 is working fine. The VirtualBox saucy repository isn't ready yet, so I just used the raring one. Worked like a peach!

Or just install the .deb from Oracle. I cloned the VM and restored it to the new system in no time.

---

### Post by monkeybrain20122 on 2013-10-28
> **john_ferrier said:**
> I suggest you just hold for one or two months. Ubuntu 13.10 is buggy, if you have a look at the bug reports on Launchpad, I am sure your'll be frightened. For Ubuntu, the .10 versions were actually beta versions of .04 versions, and Canonical's current foucus on their phones and tablet makes it even worse. Unity is only developped and supported by Canonical, things are just getting worse and worse like rolling a snow ball!

I will hold for another month. I haven't switched to 13.10 yet as 13.04 is very good. I am testing 13.10 on an external drive, so far everything seems to be working (may need a few tweaks such as Compiz edge flip and installing google earth) except that the ppas are not set up yet. There may be some hidden bugs or new version of xyz may not work, this is how I find out (on an external hd) before changing my 'real' working system. I expect to switch over maybe late Nov.

---

### Post by King Dude on 2013-10-28
For myself, yes it is. I mean, I have a life outside of my computer. All I do is start the upgrade and go off to do something else for a few hours.

Besides, "several hours" is only the longest scenario it could possibly take. Chances are it'll take maybe an hour or so, maybe less, maybe more. It'll probably only take several hours if you're running an 800Mhz single core processor and have a slow internet speed.

---

### Post by moshefeit on 2013-10-31
It took me for about 20 minutes long to upgrade to Saucy from terminal.

---

