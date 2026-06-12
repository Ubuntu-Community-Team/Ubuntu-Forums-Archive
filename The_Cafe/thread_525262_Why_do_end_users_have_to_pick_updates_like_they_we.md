---
title: "Why do end users have to pick updates like they were picking fruit at the market?"
date: 2007-08-14
forum: The Cafe
---

### Post by cutare on 2007-08-14
This morning, my mom calls me to say, "why can't I upgrade the kernel in my Ubuntu box? The terminal says Could not get lock /var/lib/dpkg blah blah blah blah".

See, my mom is a pretty industrious woman. Now, in her fifties, she likes to do home repairs and to keep her software updated. She gets her daily fix from Ubuntu's Synaptic.

When she told me about the error message, some thoughts crossed my mind:

    * When pulling the regular updates from Ubuntu (it's like crack for my mom), why does she have to know that there's a new kernel available? Her hardware works fine as it is.
    * Going further, why does she have to know that meaningless jargon like "binutils", "glibc", "tar" have new versions?
    * Why doesn't the command-line update tool detect that Synaptic is running, and that's the reason why it can't access the database? Yes, my mom had Synaptic running as well; it's her normal way to get updates. I have no idea of where in these forums my mom picked up the command line she was using (why should she even have to go to the command line at all!? Did Synaptic bring up a terminal and make her do something else? I don't know.)

But the core question is, why do end users have to pick system updates like they were picking fruit at the market?

My mom doesn't care that there's a new kernel available. It is meaningless to her. But, dutiful and industrious woman that she is, she likes to keep her software up-to-date.

When my mom gets her daily fix of software updates, she wants to see things like:

    * There's a new version of OpenOffice available! (note the lack of the idiotic .org suffix) Compared to the version you have, this one fixes a crash with Word macros, and has a nicer toolbar.
    * There's a new version of the Gaim Instant Messenger! Compared to the version you have, this one supports file uploads to Yahoo Messenger accounts.

That is, no meaningless crap like "binutils-2.16.91.0.5-23.13 available", nor updates for software which she doesn't actually use, like traceroute, nor for software which she doesn't even know that she is using, like glibc.

There are two kinds of software: the one that users see and use everyday (OpenOffice, Firefox, Gaim), and the one which users don't even know it exists (kernel, glibc, tar, binutils, Xorg, metacity, gnome-panel). That is, there's user software and there's meaningless crap, also known as system software.

**System software**

Users don't care about system software. They cannot see it. They only know when their computer breaks or works better than before.

System software should be updated transparently, automatically, and without any need for user intervention. You turn on your computer. At some point, when it detects that the network is up, it automatically checks for updates to system software, and does not ask you if you want to update, because those updates have been tested to really work, and to require no interaction when updating. The updater sets up a network traffic shaper automatically so that downloading the updates won't make your net connection really slow. It downloads the updates. If the user turns off the machine in the middle, or the network goes down, or whatever, the system is smart enough to resume downloading when conditions are appropriate again. It is also smart enough to not break horribly if the power goes out in the middle of an update (transactional file system?).

Since users don't know that system software exists, and system software must be kept updated, it follows that users should not notice when system software gets updated. It should be automatic (no asking), painless (no slow network while updates are downloaded), and reliable (things should not break after the update).

(How many times have you updated a package and your running programs started crashing?)

**User software**

People do care about software which they see and use everyday. They do not care about bug fixes for features which they don't use. They care about bug fixes for things which were problems for them in the past. Users do not really like it when the user interface changes in immediately visible ways from version to version, because it confuses them. They do like it, however, when a whole user interface gets a major overhaul with improvements (better usability, etc.). But having the GUI just change without warning is a very jarring experience: what if tomorrow you stepped into your car, and all the controls and knobs and dials and shifting lever were all in slightly different places!

So, the software should at least tell users if updates to user software will change the graphical interface. Users should be able to know what fixes and improvements the software has. That's why in the example above, the software detected which versions of OpenOffice and Gaim my mom had, and then told her what fixes were in the updated software, relative to the old versions. My mom may not want to update her word processor just now if it comes with a totally different user interface — she needs to do that on a weekend, when she has plenty of free time to explore the new features, without having the pressure of having to turn out a document right now.

There's a lot of user software which people don't use every day, or which they don't use at all. My mom seldom uses gnome-calculator, if at all, and practically never uses the GIMP or GEdit. It is fine to update that software without her knowing, since she won't even remember what the software looks like from run to run, as it is used so rarely.

But for software which she does use every day, like Gaim and Skype and Firefox, she wants to be notified when there would be noticeable changes — those that would cause her to change the way she works.

Sorry for the long rant, but this is how I feel about Ubuntu right now. I just had to say it.

---

### Post by argie on 2007-08-14
If you want to hold a piece of software to one version, 'Pin it' or 'Lock version' in Synaptic.

I don't understand. You would prefer that the Update Manager does not show kernels in the list of updates? You would prefer that it updates on its own? (You have no idea how bad this is, I had an antivirus software that would update on its own back in Windows. Oh lord, it was so painful. Did exactly what you said, detect an internet connection it would update if the signatures were out-of-date. God, it was awful!)

How the hell is the computer supposed to know what features you use, dude?

I do agree on one count though. Very often the Changelog for the packages have nothing in them. So the Changelog tab is empty. That sucks. Does this happen to anyone else or is it just me?

And doesn't the Update Manager says, 'you cannot run this program while another package manager is running' or something? The Updates Available icon grays out too. Perhaps there's a bug where this isn't happening?

---

### Post by az on 2007-08-14
> **cutare said:**
> 
    * When pulling the regular updates from Ubuntu (it's like crack for my mom), why does she have to know that there's a new kernel available? Her hardware works fine as it is.

A vulnerability doesn't mean that your computer is broken, just that there is a potential danger there.  It still needs to be fixed.

> **cutare said:**
> 

    * Going further, why does she have to know that meaningless jargon like "binutils", "glibc", "tar" have new versions?
    * Why doesn't the command-line update tool detect that Synaptic is running, and that's the reason why it can't access the database?

It does know that another package manager is running and that's why it refused to install anything!  That doesn't mean that you can't use the tools for browsing packages and looking at the changelogs.

You don't have to look at the individual packages.  Just install the updates when you get them.  There is no reason to not install updates.

> **cutare said:**
> 
But the core question is, why do end users have to pick system updates like they were picking fruit at the market?


Of course they don't.  You imply that your mom does this like it was crack and that makes it sound like you don't think it should be done.  Or at least that it is not important.  Keeping your system up-to-date is very important.  There is no reason to not install all updates.

---

### Post by cb951303 on 2007-08-14
you dont have to choose the updates just because you can :) just select all and click update :lolflag: For other non-industrious users like myself it's a good thing to have the option to choose which packages to update.

---

### Post by aysiu on 2007-08-14
I agree with some of what you said. If Synaptic is open, the Update Manager should say > In order to install updates, Update Manager will have to close Synaptic Package Manager. Would you like to do that now? 
**Close Synaptic and Install Updates** / **Keep Synaptic Open and Update Later** I also agree that most users don't really care about cryptic system file jargon.

I don't really care for the names of the programs being updated, but that's why I just click **Install Updates**. I don't bother reading about lib... whatever. I just click it, watch the updates install, and know my computer is up-to-date... probably what your mother does too.

---

### Post by Luinar on 2007-08-14
Whilst I would agree that for the most part I don't really care what it is exactly is being updated, as long as the updates are being installed, I do still like to have the option to know *exactly * which files are being updated, in case I ever run into a situation where I might want/need to know. One of the biggest appeals of Linux to me is that it tells me exactly what is going on. Similarly the idea of automatically installing updates isn't too appealing to myself; even if the automated system was proven to work flawlessly, I still like being in control enough that I have to give the go ahead for anything to happen. Personally I feel that automating these things would be "dumbing down" Ubuntu too much, but then that's just personal opinion. I do, however, agree that it would be nice if there were better change logs and explanations of what exactly an update is going to do.

---

### Post by popch on 2007-08-14
> **aysiu said:**
> I agree with some of what you said. If Synaptic is open, the Update Manager should say  I also agree that most users don't really care about cryptic system file jargon.

I don't really care for the names of the programs being updated, but that's why I just click **Install Updates**. I don't bother reading about lib... whatever. I just click it, watch the updates install, and know my computer is up-to-date... probably what your mother does too.

I think that's sound doctrine. 

Being a bit curious about what's going on in my computer, I do glance at the list of components about to be updated. It allows me to make an intelligent guess about what components are likely to get broken (or - in some cases - get fixed). Besides, I do have to know when the kernel is being replaced because I then have to recompile some VMWare stuff.

---

### Post by CarpKing on 2007-08-15
> **cutare said:**
> * There's a new version of OpenOffice available! (note the lack of the idiotic .org suffix) 

That would violate someone's trademark.  

[http://www.openoffice.org/FAQs/faq-other.html#4](http://www.openoffice.org/FAQs/faq-other.html#4)

---

### Post by Tomosaur on 2007-08-15
Generally speaking, if your mother doesn't understand what many of the updated software are - then she should just download and install the updates. It is incredibly rare that there is any reason to 'not' update software, unless you know that the update is going to fundamentally change something and you don't want it to happen (which is why you have the option of locking versions - but I'd like to see this feature put into the actual update manager too).

---

### Post by salsafyren on 2007-08-15
I completely agree with the poster.

There is some Gnome work on package managers and update programs:

[http://hughsient.livejournal.com/32723.html](http://hughsient.livejournal.com/32723.html)

The good thing about this is you can queue updates and installs in the background, so you'll never have to see that stupid "Could not get lock bla bla" again.

The package management in Ubuntu is good, but it needs some refiinement.

---

### Post by M$LOL on 2007-08-15
> **cutare said:**
> 
There are two kinds of software: the one that users see and use everyday (OpenOffice, Firefox, Gaim), and the one which users don't even know it exists (kernel, glibc, tar, binutils, Xorg, metacity, gnome-panel). That is, there's user software and there's meaningless crap, also known as system software.

Users don't care about system software. They cannot see it. They only know when their computer breaks or works better than before.

That's where you're wrong. Some of us do care about it, we like to know what's going on. Many people dislike transparency, which is often a big reason they moved from Windows.
> **cutare said:**
> 
Since users don't know that system software exists, and system software must be kept updated, it follows that users should not notice when system software gets updated.

Again, some people like to know exactly what is being updated. It can also help fix crashes, if Xorg suddenly doesn't work, and you know you just updated it to the latest version, you have somewhere to start troubleshooting. On the other hand, if it's updating automatically, you don't know when it last updated or to what version.


I agree with you that there should be better information available about the updates, such as "Adds a new toolbar", but I imagine that that sort of information is hard to get, as the developers would probably give more technical information. It would be a nice thing to have though.

---

### Post by awakatanka on 2007-08-15
For company's it isn't good at all to have automatic updates without interactionl, also for those company's it is important to know what there is to be updated. They have to test in save environments before they install it live on the rest of the company's computers. So there need to be a option for both sort of users else ubuntu isn't good for company's.

---

### Post by salsafyren on 2007-08-15
apt seriously needs rollback capability.

I think it would be easier to do the installs ala GoboLinux and just move a link.

If something does not work, move all moved links back.

There is a another distro out than (other than GoboLinux) that can do this.

Regarding transparency: Yes, Ubuntu still needs to tell the user which kernel version you are using because things break.
The quality needs more focus until you get an unbreakable machine.

---

### Post by ssam on 2007-08-15
if you just use the update manager then you should never get problems with dpkg lock files.

you can enable automatic updates in
System -> Administration -> Software sources.

update will never bring new features, unless you upgrade the whole distro (eg edgy -> feisty). for stable release updates you will only get security fixes, and serious bug fixes.

---

### Post by Old Pink on 2007-08-15
[B]System > Administration > Software Sources

[/B]"Updates" Tab

Check "Install security updates without confirmation" and "Check for updates daily" 

Now, you won't see security fixes which don't interest the end user, but your system will remain stable. You'll also be able to use update manager to click "Details" and get a list of what exactly has changed. Using synaptic for updates isn't necessary.

---

### Post by 3rdalbum on 2007-08-15
If you implement this involuntary upgrade system, will you pay the excess usage fees for my internet connection?

I pick and choose because if a package is big and I don't use it (or it fixes a security vulnerability that doesn't affect me), I don't want it contributing to my download quota. And with new kernels, I'm much happier using the one that shipped with the distribution - it'll have better testing put behind it.

---

### Post by FuturePilot on 2007-08-15
I like to know what is being updated. And then find out if there happens to be any breakage with the update. It's usually very very rare though.

---

### Post by tecknogyk on 2007-12-19
It should be an option in the updater.  Users should be given the option to automate system updates and there should also be an option specific to key components such as the kernel that gives the user the option to be notified before going through with the update.  I, for one, get tired of the constant barrage of updates and would welcome the option to automate some of it at a time of my choosing.  However, I would not like the kernel or other key system components automatically updating without my knowledge.  It doesn't need to be an "either/or" situation.  We can have both and make everyone happy.

---

### Post by PrimoTurbo on 2007-12-19
In general I think Linux is targeted more towards a user who knows their system, so specific version information might be useful for some. For most I agree it's pointless to know that some odd libx has a little update from 0.23.54.23 to 0.23.68.21 with no info on the changes.

Anyone else notice that the kernel updates mess up the /boot/grub/menu.lst ? It always edits my custom menu.lst removes Windows from the options (I have it setup as the first option), I have to go back to a backup file every time and re-edit the file. _**This is stupid**_.

Automatic kernel or system updates are dangerous, especially if there is no notification. You cannot test for all systems, you need to know what changes and how. I think there should be less updates and they should be ranked from urgent to less necessary. For example it will notify about minor system updates once a month on a weekend or something.

Also system and program updates should be separated and there should be different notifications for each, like using colors or something.

---

### Post by aysiu on 2007-12-19
> **PrimoTurbo said:**
> 
Anyone else notice that the kernel updates mess up the /boot/grub/menu.lst ? It always edits my custom menu.lst removes Windows from the options (I have it setup as the first option), I have to go back to a backup file every time and re-edit the file. _**This is stupid**_. Make sure the Windows entry is below or above the "automagic" part of the /boot/grub/menu.lst file.

---

### Post by macogw on 2007-12-19
> **aysiu said:**
> Make sure the Windows entry is below or above the "automagic" part of the /boot/grub/menu.lst file.

And then if you want it to be the first thing that boots, change the "default" line (line 17) to whatever number (counting down the screen through your ubuntu kernels) Windows is.  And put true on the "update default entry" line so that when you get an update, it automatically changes the number in the default line to whatever Windows is now.

---

