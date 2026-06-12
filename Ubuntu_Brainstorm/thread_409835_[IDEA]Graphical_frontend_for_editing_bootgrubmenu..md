---
title: "[IDEA]Graphical frontend for editing /boot/grub/menu.lst"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-15
**Summary:**
A menu entry by which users can change the default boot option on a dual-boot, change the timeout for the Grub selection, remove or add the *splash* option from the kernel, and specify a Grub splash image to use.

**Rationale:**
Right now, the most likely successful migrations to Ubuntu happen for *nix experts and total novices who have someone install Ubuntu for them, but the most likely people to *try* Ubuntu are Windows power users--those who like a lot of configuration options but who are also used to using the GUI for tweaking options and not manually editing a text configuration file.

The most popular requests for editing the /boot/grub/menu.lst file involve changing the default boot option (to Windows instead of Ubuntu) and changing the timeout before a boot option is selected. The other less popular ones would be just bonus features, I guess.

**Scope and Use Cases:**
Indira has just installed a dual-boot of Ubuntu and Windows. She loves Ubuntu, but she shares the computer with the rest of the family, who primarily use Windows. She wants to change the default boot option from Ubuntu to Windows. She has no problems pressing the Up arrow a few times to change the boot selection, but she knows her other family members would just be confused by the Grub menu.

She looks for a configuration option in the menus but can't find anything. Finally, she ends up signing up for the Ubuntu Forums and getting some confusing (to her) directions about editing some text file. Eventually, she gets it sorted but wonders why changing a default boot option from Ubuntu to Windows isn't more straightforward.

**Implementation Plan:**
It would just be another menu item: 
System > Administration > Boot Menu Editor
KMenu > System > Boot Menu Editor

**Blueprint**
[https://blueprints.launchpad.net/ubuntu/+spec/graphical-grub-config](https://blueprints.launchpad.net/ubuntu/+spec/graphical-grub-config)

---

### Post by viciouslime on 2007-04-15
This really is a must! Lots of people are scared away from ubuntu when it "takes over windows" and the only way to get windows to load by default involves using the command line (<gasp>)

---

### Post by klytu on 2007-04-15
This is a great idea! A suggestion: consider including an option that could edit the names of the Grub menu entries as well. I had some thoughts about other options for you to consider adding, but they seemed ***way***  beyond what your target users would think about and are probably outside the scope of your plan (stuff like adding default kernal options, for example ...).

---

### Post by =0verlord= on 2007-04-15
I like this: grub has always been a pain to learn how to configure manually for me and this particular tweak would make a great start.  Thinking about it for a second, this might make a better option for the installer than in the menus.  If a lot of people are changing grub after everything is set up (which I know happens, but isn't in this use case), then ignore me and go ahead, but I would get more use out of it during the install than after (and for this use case, more likely for Indira to even notice).

Klytu, do share your other ideas since aysiu is at least marginally interested in general grub configuring.  I thing your first one for the entry renaming is a good one. :)

---

### Post by bernied on 2007-04-15
I also support this. Another good idea Aysiu.

The following is mere speculation...

I don't think it would be too much of a stretch to enable selection of an alternate location (alternate to /boot/grub/menu.lst, which would be the default) for the menu.lst file. This would make it much easier to fix a menu.lst from the Ubuntu live-cd, for example.

I guess that adding that function would turn it into a text editor run as root, which is what it was always going to be, right? I suppose you could have an option that searches for menu.lst files on multiple partitions, but then we're getting complicated (it would have to list partitions, detect filesystems, mount partitions, find file, edit file - or does the live cd automatically mount partitions already?).

---

### Post by =0verlord= on 2007-04-15
> **bernied said:**
> I also support this. Another good idea Aysiu.

The following is mere speculation...

I don't think it would be too much of a stretch to enable selection of an alternate location (alternate to /boot/grub/menu.lst, which would be the default) for the menu.lst file. This would make it much easier to fix a menu.lst from the Ubuntu live-cd, for example.

I guess that adding that function would turn it into a text editor run as root, which is what it was always going to be, right? I suppose you could have an option that searches for menu.lst files on multiple partitions, but then we're getting complicated (it would have to list partitions, detect filesystems, mount partitions, find file, edit file - or does the live cd automatically mount partitions already?).


If grub has an option to pull menu.lst, I don't see why not - otherwise I don't see it being that useful, unless you really can't access /boot from the livecd like you suggest (I wasn't aware of it).
A gksudo /boot/grub/menu.lst doesn't really address the original use case, which is someone who may not feel comfortable decoding the conf file.  While a decent temporary solution, a "real" configuration gui is my favorite long term solution.

---

### Post by Toby2 on 2007-04-15
I too support this idea, although I remember that back when I installed Breezy, there was a tool in the Administration menu that did exactly this. Am I just imagining, or was it taken out in Dapper? If so, why?

---

### Post by iGama on 2007-04-15
I also think this is a great ideia.

One of the problems I see in new users, is that they wish to edit Grub, but don't understand it or are afraid of doing something wrong.

This tool would be welcome.

---

### Post by GoHabsGo on 2007-04-15
I greatly support this !!! Crucial feature and nice idea !!

---

### Post by Toby2 on 2007-04-15
Like I thought, this tool was definitely in Breezy, as can be seen in this screenshot (bottom left "Boot Manager Settings"):
[http://madpenguin.org/images/reviews/ubuntu510/tools.jpg](http://madpenguin.org/images/reviews/ubuntu510/tools.jpg)

I wonder why they took it out? Hopefully it'll just be a matter of adding a menu entry in; the application is already done.

---

### Post by duff on 2007-04-15
I started a project for this about 2 years ago called "grime" ([http://grime.sourceforge.net/](http://grime.sourceforge.net/)).  I've lost interest in it, but it anyone feels like taking it over and allowing for menu entry editing, let me know.

---

### Post by Ric95 on 2007-04-15
I agree this would be good. Also a way to set a splashscreen on the boot screen. 
But please try to add it to an existing app, like the login window manager, to avoid M$ style addative programing. ;)

---

### Post by migla on 2007-04-15
> **duff said:**
> I started a project for this about 2 years ago called "grime" ([http://grime.sourceforge.net/)](http://grime.sourceforge.net/)).  I've lost interest in it, but it anyone feels like taking it over and allowing for menu entry editing, let me know.

The closing parenthesis has stuck to your url, braking it.

---

### Post by opticyclic on 2007-04-15
There is also the GrubEd script
[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

---

### Post by =0verlord= on 2007-04-15
> **opticyclic said:**
> There is also the GrubEd script
[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

Thanks for that link, seems like the exact app we've been talking about.  And it looks like it's getting at least some attention for moving into the dist, so...woot?  I'm happy.

---

### Post by loserboy on 2007-04-22
I've been using GrubEd since it first came out, it rocks and i've never had a problem with it even once.

---

### Post by adelgado on 2007-04-22
What about SUM, the StartUp Manager?

[http://www.linux.com/article.pl?sid=07/04/10/1830249](http://www.linux.com/article.pl?sid=07/04/10/1830249)

[IMG]http://web.telia.com/~u88005282/sum/images/sum1.png[/IMG]
[IMG]http://web.telia.com/~u88005282/sum/images/sum2.png[/IMG]
[IMG]http://web.telia.com/~u88005282/sum/images/sum3.png[/IMG]
[IMG]http://web.telia.com/~u88005282/sum/images/sum4.png[/IMG]

---

### Post by nokrev on 2007-04-22
I really like this idea, and it doesn't seem hard to implement at all. It'd definitely help beginners. I also like the idea of integrating it into the installer, but I think the configuration there should be limited to setting the timeout and default choice.

---

### Post by Sand Lee on 2007-04-28
I really think this should be an option. It would save my parents from the scare they recieve whenever I forget to edit menu.lst on a fresh install and it loads into ubuntu.

---

### Post by marianoi on 2007-04-28
+1

---

### Post by drf_av on 2007-04-28
I've posted this thread another 2 times so...
+1 +1 +1

---

### Post by Jimmy_r on 2007-04-28
> **klytu said:**
> A suggestion: consider including an option that could edit the names of the Grub menu entries as well.

The problem with that is the update-grub command.
update-grub is issued to rewrite the grub menu.lst for example on system upgrades.
It will remove any custom boot entries(including titles) with some exceptions.

That is probably the reason grubconf was retired.

It is also the reason SUM does not support editing of individual boot entries.

---

### Post by u.b.u.n.t.u on 2007-04-29
+1 for GUI

---

### Post by Rinzwind on 2007-04-29
I think this should be expanded and not limited to grub

We should have 1 place where we have tabs that include ways to change:
1, grub
2. splash screen
3. login
4. desktop splash screen
5. background for different workspaces

with external linkage to gnome-art and/or themes in repository packages if possible.

That way someone could make a COMPLETE theme where anything graphical can be changed into the same style.

---

### Post by Cheizzz on 2007-04-29
This is an excellent idea, aysiu. This has been bugging me for a long time, as i had no easy way to remove obsolete kernels from the boot up list. this seems to be fixed in 7.04 (they are automagically removed) but a GUI based, easy to use application could greatly enhance the experience of editing the GRUB menu. 
+1 from me.

---

### Post by Pisi-Deff on 2007-05-01
I totally love this idea :D
+1

---

### Post by Bou on 2007-05-01
> **adelgado said:**
> What about SUM, the StartUp Manager?

[http://www.linux.com/article.pl?sid=07/04/10/1830249](http://www.linux.com/article.pl?sid=07/04/10/1830249)

[IMG]http://web.telia.com/~u88005282/sum/images/sum1.png[/IMG]
[IMG]http://web.telia.com/~u88005282/sum/images/sum2.png[/IMG]
[IMG]http://web.telia.com/~u88005282/sum/images/sum3.png[/IMG]
[IMG]http://web.telia.com/~u88005282/sum/images/sum4.png[/IMG]

This has to be in the repos NOW.

---

