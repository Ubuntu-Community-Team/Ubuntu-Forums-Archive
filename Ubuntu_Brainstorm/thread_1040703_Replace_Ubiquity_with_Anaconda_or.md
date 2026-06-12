---
title: "Replace Ubiquity with Anaconda or ?"
date: 2009-01-15
forum: Ubuntu Brainstorm
---

### Post by Slug71 on 2009-01-15
Ubiquity seems to have had its fare share of troubles and i think maybe its time to move on and replace it with Anaconda?
Anaconda also allows the user to select the drive boot order.

If you select 'Other', state you preference.

Launchpad wishlist entry since Brainstorm decided to mark this as 'Not an Idea'.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/317725](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/317725)

---

### Post by smartboyathome on 2009-01-16
I like Ubiquity. It is simpler, and thus there is less that can go wrong (and, consequently, simpler for the user). In fact, I have had nothing go wrong with Ubiquity itself, it is usually based on drivers or programs with bugs (mostly drivers) if Ubuntu's livecd crashes.

---

### Post by oomingmak on 2009-01-16
Yes, yes, and thrice yes.

[http://ubuntuforums.org/showthread.php?p=6562272&#post6562272](http://ubuntuforums.org/showthread.php?p=6562272&#post6562272)

---

### Post by smartboyathome on 2009-01-16
> **oomingmak said:**
> Yes, yes, and thrice yes.

[http://ubuntuforums.org/showthread.php?p=6562272&#post6562272](http://ubuntuforums.org/showthread.php?p=6562272&#post6562272)

How many users would actually use that? To me, it can be left out because Ubuntu tries to cater to the newbies coming to Linux, not to power users.

---

### Post by cardinals_fan on 2009-01-16
> **smartboyathome said:**
> How many users would actually use that? To me, it can be left out because Ubuntu tries to cater to the newbies coming to Linux, not to power users.
Sorry, but I have to agree with oomingmak on this one.  That would be very useful.

With that said, it might be better to try and add something like that to Ubiquity.  Moving to a new installer is a pretty big change.

---

### Post by Slug71 on 2009-01-16
> **cardinals_fan said:**
> Sorry, but I have to agree with oomingmak on this one.  That would be very useful.

With that said, it might be better to try and add something like that to Ubiquity.  Moving to a new installer is a pretty big change.

If i remember correctly Anaconda also gives you the option to install it as an office desktop or for media etc. and installs appropriate apps. during installation and i think a lot of people might find that usefull too.
Less clutter and stuff you may not use/need which currently gets installed by default and iv'e seen people ask for a feature like that numerous times here before.

---

### Post by smartboyathome on 2009-01-17
> **Slug71 said:**
> If i remember correctly Anaconda also gives you the option to install it as an office desktop or for media etc. and installs appropriate apps. during installation and i think a lot of people might find that usefull too.
Less clutter and stuff you may not use/need which currently gets installed by default and iv'e seen people ask for a feature like that numerous times here before.

Now that IS impossible for Ubiquity as it operates now. It just copies the image from the disk and installs it to the hard drive. Ubiquity would have to be completely reworked to do this.

---

### Post by Slug71 on 2009-01-17
> **smartboyathome said:**
> Now that IS impossible for Ubiquity as it operates now. It just copies the image from the disk and installs it to the hard drive. Ubiquity would have to be completely reworked to do this.

Yeh but you make a good point about Ubiquity's ease of use. What would be very cool is if Ubuntu adopted Anaconda and then worked with RH/Fedora to kinda simplify it for the average/newb by having an 'Advanced' button somewhere in the installer which if you click on it opens up a menu where you can set the drive boot order and change default keyboard shortcuts etc.
Like being able to turn on Ctrl-Alt-Backspace which is going to be disabled by default in Jaunty now.

This way you keep certain things away from people that are new and keep the basic function of the installer simple but have the option there for a more advanced menu for users that know what they are doing.

---

### Post by smartboyathome on 2009-01-17
> **Slug71 said:**
> Yeh but you make a good point about Ubiquity's ease of use. What would be very cool is if Ubuntu adopted Anaconda and then worked with RH/Fedora to kinda simplify it for the average/newb by having an 'Advanced' button somewhere in the installer which if you click on it opens up a menu where you can set the drive boot order and change default keyboard shortcuts etc.
Like being able to turn on Ctrl-Alt-Backspace which is going to be disabled by default in Jaunty now.

This way you keep certain things away from people that are new and keep the basic function of the installer simple but have the option there for a more advanced menu for users that know what they are doing.

The problem is, adding an "advanced" button and tools makes the code more complex and likely to break. I think the Ubiquity team is trying to follow KISS as close as possible in both the installer's GUI and in its code.

---

### Post by Slug71 on 2009-01-17
> **smartboyathome said:**
> The problem is, adding an "advanced" button and tools makes the code more complex and likely to break. I think the Ubiquity team is trying to follow KISS as close as possible in both the installer's GUI and in its code.

I'm  not very clued up on the technical side of these things but would it not be a lot easier with Distros being involved thus having double the amount of people working on it and testing it?

---

### Post by oomingmak on 2009-01-17
> **smartboyathome said:**
> How many users would actually use that? To me, it can be left out because Ubuntu tries to cater to the newbies coming to Linux, not to power users.
That is completely bogus reasoning. 

If Ubuntu were exclusively designed on that premise, then the CLI would have long since been removed, as would things like alternative disk formats (XFS, JFS, Resiser etc.),  functions like Chroot, control over system services, multiple X sessions etc. -  none of which are things a beginner will concern themselves with. 

Clearly Ubuntu is not *just *catering for newbies.

There is a difference between *requiring *a beginner to undertake a task that is deemed to be for 'advanced' users, versus simply having the option made available somewhere for those that require it. And the notion that good usability somehow only needs to be provided for beginners, is both specious and erroneous. Good usability should be available to *all *levels of user. Just because someone may be a little more advanced in their requirements, it does not mean that they deserve to have a horrible user experience or that they should have to put up with inadequate features that break their system.

Wanting your system to be able to boot up after installation is hardly what I would call a "power user" feature. It's pretty essential. How else are you going to use it if it can't boot? 

Likewise, it's not a power user feature to want to be sure that your existing data won't be destroyed by an overwrite. So, deciding where the install should go (and therefore, by definition, what existing data should be left alone) is also not an power user task. Newbies will be just as angry and upset if they lose their data as more experienced users would be. The existence of Wubi is a testament to this (and proves just how badly existing install routines have been designed).

The only reason that installing to another disk is deemed an "advanced" task is that so little effort has been put into making it even vaguely understandable that only power users can make sense of it. It's not because deciding where to put your new install is an advanced requirement. Plenty of people do not want to risk losing precious existing data by having an unknown OS messing with partition tables, resizing and altering disk formats etc. and would rather just install to a separate device that they know is empty.

I speak from first hand experience. Read my own **newbie** comments from back in 2006. 

 [[COLOR=DarkOrange]**http://ubuntuforums.org/showthread.php?p=1937710#post1937710**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=1937710#post1937710")

I got so badly burned by the experience that it is still fresh in my mind nearly 3 years later. Look through the rest of that thread and you'll see that I am not the only one who suffered like that. Is this really the kind of first experience people should be having with Ubuntu?

[COLOR=black]Ubiq[/COLOR]uity allowing the OS to be installed to a particular drive, but then not providing the necessary options to make that installation bootable, is sheer idiocy. The feature is not a luxury, it's the difference between the install working or not.

Not so long ago (in the days of Edgy Eft) [COLOR=black]Ubiq[/COLOR]uity wouldn't even let you specify which disk Grub should be installed to. That feature was later added because people got sick and tired of their MBR being overwritten on disks that Ubuntu had no business touching at all. But that's only part of the task. If you put Grub on disk 2 because you want to ***boot ***from disk 2, then why on earth does [COLOR=black]Ubiq[/COLOR]uity apply boot partition settings that apply to the *current *disk 1 boot order when they will be invalid (and therefore break) as soon as disk 2 is booted?

Anaconda recognised this issue years ago, and has provided the necessary options to deal with it. The interface was simple enough even for a total newbie like me to use.

[[COLOR=DarkOrange]**http://ubuntuforums.org/showthread.php?p=2558032#post2558032**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2558032#post2558032")

The option said "Change Drive order" and you simply used up / down buttons to move the drive you were going to boot from to the top of the list. The result was a correct partition assignment and a fully working booting system after installation.

Expecting people to figure out how to find and edit menu.lst in order to alter a setting that Ubuntu should have never messed up in the first place, is not my idea of a good installer tool.




> **smartboyathome said:**
> The problem is, adding an "advanced" button 

There already is an advanced option, how else do you think you get to the custom partitioner in the first place? Beginners will not see this as they tend to be encouraged to use the automatic partitioner. Also, the button already exists to specify grub install location, so the disk order feature could (and should) be added there. No new "advanced" buttons are required.

> **smartboyathome said:**
> and tools makes the code more complex and likely to break.

But yet [COLOR=black]Ubiq[/COLOR]uity can add fancy zooming maps of the world with illuminating cities that respond to mouseover, plus ridiculous, brightly coloured rounded disk partition maps, (both of which contributed nothing constructive to the install experience and added unnecessary code). Yet a simple fix to get Ubuntu actually booting (i.e. just defaulting to HD 0,0 value) is somehow going to cause breakage? If that really is the case then it's all the more reason to use Anaconda. The code is already working and has been tested for years and years.

---

### Post by cjwatson on 2009-01-24
This isn't going to happen, sorry. I've replied to your [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/317725") with further details.

oomingmak is right that the drive ordering issue is a problem, but has some serious misunderstandings in several respects.

Firstly, oomingmak assumes that Anaconda is somehow something you can drop into an arbitrary distribution and just work. It isn't. Installers are typically very tightly associated with particular distributions; Anaconda is very much designed around the Red Hat view of the world and has links to Red Hat's configuration tools. Porting it to Debian-based systems is insanely painful. (Porting Ubiquity to non-Debian-based systems would be similarly painful; and in both cases this is an artifact of their integration with the operating system they're installing, which is a feature in other respects.) I have been working on installer code for a very substantial part of the last five years; believe me when I say that merely switching installers would not be an automatic improvement, and in fact would be overwhelmingly likely to lead to a significant number of regressions that would get us lynched, and for good reason.

Secondly, oomingmak assumes that these problems are all bugs in the installer rather than elsewhere in the operating system. The GRUB disk order issue is not solely an installer flaw, although it's true that the installer has done some incorrect things. Fundamentally, it is because there is no reliable way to figure out from Linux what the BIOS boot order is, even *currently* let alone at some future boot. As Linux has evolved, disk ordering has stopped being something you can rely upon from boot to boot, which is why we put effort into using UUIDs for filesystem location (Anaconda made the elementary mistake of automatically assigning filesystem labels instead, which results in clashes when you install multiple vaguely-similar operating systems on the same disk; in fact, I challenged some Anaconda maintainers about this in person once and they admitted it had been an error). The last critical piece here is getting GRUB to do all of its filesystem location by means of stable interfaces such as UUIDs, and we've been working on this in recent releases; see, for example, [bug 244141]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/244141"), although we still need to get GRUB to locate its stage 1.5 by similar means.

While I certainly believe that Anaconda's approach worked for oomingmak, it's a stopgap at best. What if you decide to change your system around so that it chain-loads the boot loader on the second hard disk from one on the first (not an uncommon setup)? If you're relying on device numbering in menu.lst, you're screwed - and moreover you're probably screwed in a really confusing way after you spent some time setting your system up. What if you run grub-install later on, but because traditional device names aren't stable on Linux these days you find that menu.lst no longer corresponds to the current layout and now your system no longer boots? These are real problems that you can't paper over for good with an option in the installer. We really want to fix this stably, and that means having GRUB locate the root filesystem in a reliable way that doesn't depend on that increasingly fragile relationship between BIOS disk enumeration and Linux device names.

Thirdly, oomingmak commits the rather infuriating though perhaps understandable fallacies of believing that effort spent on one aspect of a piece of software crowds out development on other aspects, and that everyone must have exactly the same priorities. We implemented the silly zoomy timezone map thing before Ubuntu 6.06 was released, and certainly well before the problems with drive ordering were recognised; aside from some relatively minor changes to it since then, it's had no effect on availability of developer effort for reliability. As for "ridiculous" partition maps, they were widely requested to alleviate confusion at the automatic partitioning stage (which was itself a deeper reliability problem), and have largely been well-received.

Fourthly, no, simply defaulting to hd0 isn't good enough; that's what we used to do and lots of people complained that it overwrote their MBRs (even though the installer goes to significant effort to offer chain-booting of other systems; I rather suspect that the Windows booting problem that oomingmak ran into is now fixed). Furthermore, what if you're installing from a USB stick? In that case, hd0 during installation and hd0 after reboot will be different, and if you take Anaconda's approach and ask for menu.lst based on the desired drive ordering after reboot then you'll find that grub-install ends up writing the GRUB MBR to the USB stick (current hd0) rather than whatever's going to be hd0 after reboot.

Fifthly, people who let grub install to the default location don't run into this problem.

oomingmak's whole approach of taking a single cluster of bugs - admittedly bad bugs if you happen to run into them, and ones that I do take seriously, but not ones that the vast majority of users I've spoken to have run into - ignoring the fact that we've been working on improving them, and then shouting about how the installer is a joke and we all suck is grossly offensive. I'm sorry that you had problems. If you file civilised bug reports, I will be more than happy to try to help you. However, simply slinging insults is not going to get you anywhere, either in Ubuntu or in any polite society.

---

### Post by Slug71 on 2009-01-25
Thanks for the reply Colin. Wasnt aware that it would actually take so much to get it ported to Ubuntu/Debian and with the possibilty of having no real benefits.
Nice to have you guys come here and put us in our place every now and then.
:)


P.S.-If you check post #161 you will see what is meant by drive boot order.
[http://ubuntuforums.org/showthread.php?t=994973&page=17](http://ubuntuforums.org/showthread.php?t=994973&page=17)

---

### Post by Slug71 on 2009-01-25
Could the mods please lock this thread?
I think Colin has explained this well enough and see no need to have this thread continue.

---

### Post by oomingmak on 2009-01-26
> **cjwatson said:**
> shouting about how the installer is a joke and **we all suck** is grossly offensive.
I never said that you all suck.

Kindly don't make up quotes and then attribute them to me.

---

