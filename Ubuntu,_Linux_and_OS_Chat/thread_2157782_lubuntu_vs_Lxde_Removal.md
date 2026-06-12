---
title: "lubuntu vs Lxde Removal"
date: 2013-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by GrimJa on 2013-06-26
After an adventurous, frustrating, but educational Ubuntu minimal install. I have managed to surrect an operational Gui-desktop. :popcorn:

The successful method involved me selecting 2 package bundles upon installation :- 

By memory: "lubuntu-desktop" and "LXDE".
I now have the option (at gui login) to initiate either of these 2 'desktops'.

I understand the differences between the 2, however I selected BOTH of them as a safety-attempt (after my many previous failures).

I would now like to remove the "lubuntu-desktop" package and all it may have required additionally (dependencies). I DO NOT however, wish to remove the "lxde" package, as logging into it feels lighter and snappier than  "lubuntu" does.

How do I accomplish this, you gurus! - help. 
Not in the mood to break anything.

(Side note - if you're curious as to why I need to - the short answer is HDD space - I am limited to 4.5GBs for this installation).
I acknowledge that some of the packages are inter-dependent, but would like to delete those I can).

Hopefully, I can wean my family unto linux.

---

### Post by ajgreeny on 2013-06-26
I am not sure this is going to be possible in any simple manner because, of course, Lubuntu uses the LXDE desktop.  Therefore if you remove all the dependencies of lubuntu-desktop it would also take with it most, if not all of LXDE.

One way to try to figure out all of this would be to try to get a list of all dependencies of both packages and then compare both lists (with the diff command if you want to try that) and then remove the parts of Lubuntu that you don't want or need.

However, that may not be as simple as just removing the lubuntu-desktop using the info at [http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu) or one of the other "**pure *ubuntu**" links that you will see in the **playing around** section of that linked page (scroll down and look in left hand pane).  Having done that simply re-install the lxde metapackage to make sure anything you have removed is added back again.

Not something I've ever done or needed to do, but worth a try, I think.

---

### Post by momist on 2013-06-26
If you have anywhere to put it (DVDs?), take an image with Clonezilla before you make any changes, then you are insured against breaking anything.

---

### Post by snowpine on 2013-06-26
Fantastic suggestion from  ajgreeny, to follow the psychocat "pure" tutorials. Highly recommended! :)

---

### Post by mips on 2013-06-27
If it was me I would just uninstall lubuntu desktop and whater it decides to drag with it. If it removes lxde then fine you can simply reinstall lxde as it's already in your package cache and it will be quick.

---

### Post by ajgreeny on 2013-06-27
> **mips said:**
> If it was me I would just uninstall lubuntu desktop and whater it decides to drag with it. If it removes lxde then fine you can simply reinstall lxde as it's already in your package cache and it will be quick.

That is what the link I gave actually does; removing the lubuntu-desktop package will not help as it is just a metapackage and will not remove all its dependencies.

---

### Post by GrimJa on 2013-06-28
Thank you kindly all gentlefolk for your responses ):P

> **ajgreeny said:**
> 
One way to try to figure out all of this would be get a list of all dependencies....and then remove the parts of Lubuntu that you don't want or need.

However, that may not be as simple as ...[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu) or one of the other "**pure *ubuntu**" links that you will see in the **playing around** section 
AJ thanks for all your thoughts. I will read the article an incorporate it into the solution I am keen to attempting.

> **momist said:**
> If you have anywhere to put it (DVDs?), take an image with Clonezilla before you make any changes, then you are insured against breaking anything.
I shall do exactly that, good idea.

[SUB][/SUB]> **mips said:**
> If it was me I would just uninstall lubuntu desktop and whater it decides to drag with it. If it removes lxde then fine you can simply reinstall lxde as it's already in your package cache and it will be quick.

AJ, Mips, This is more or less what Ive decided to do, in fact, I hope to remove lubuntu/LXDE completely, then reinstall lxde (and hope I don´t have any of those ANNOYING X11/Sorg issues, (argh!)

Ill tell of my successes/roadblocks here.
Thanks again team.

*edit* - doubtful Ill have space for the clonezilla image!

Ok, an update:
dropping those commands into a terminal gives me:

E: Unable to locate package audacious-plugins-data
E: Unable to locate package libbs2b0
E: Unable to locate package libept1.4.12
E: Couldn't find any package by regex 'libept1.4.12'
E: Unable to locate package libfm-gtk-bin
E: Unable to locate package libfm-gtk3
E: Unable to locate package libfm3
E: Unable to locate package libgmlib0
E: Unable to locate package libgmtk0
E: Unable to locate package libgmtk0-data
E: Unable to locate package libpwquality1
E: Unable to locate package libvpx1
E: Unable to locate package lubuntu-artwork-12-10
E: Unable to locate package lubuntu-lxpanel-icons
E: Unable to locate package lubuntu-software-center
E: Unable to locate package lxsession-data
___

Ive confirmed it ISNT the case, that these files are in use (and hence not removable).
How can I command apt-get to complete the process regardless of these files not being found. (I ask, for the education, as I realize I could just manually remove them from psycocat´s line of commands)

---

### Post by GrimJa on 2013-06-28
Manually took out offending entries, removed lubuntu-desktop, then installed only lxde. Cleared up nearly a Gig (700MB).
Totally worth it.

Short version of story: Success!

Thanks much guys. God bless.

---

