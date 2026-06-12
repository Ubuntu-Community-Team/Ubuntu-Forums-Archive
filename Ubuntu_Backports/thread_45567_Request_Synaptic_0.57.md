---
title: "Request: Synaptic 0.57"
date: 2005-06-30
forum: Ubuntu Backports
---

### Post by XDevHald on 2005-06-30
There has been a new version of Synaptic 0.57 for the past week if not longer and would like to see this in the backports if possible? :)

Also if possible the new version of wget in which is 1.10 as well.

Cheers :)

---

### Post by Slo Mo Snail on 2005-06-30
Are there any significant changes in the new synaptic and wget versions which would justify a backport? at least both are fairly important packages...

---

### Post by XDevHald on 2005-06-30
[QUOTE=Slo Mo Snail]Are there any significant changes in the new synaptic and wget versions which would justify a backport? at least both are fairly important packages...[/QUOTE]
 The 0.57 has been updated to 0.57.1 by Michael Vogt. The new package is [http://people.ubuntu.com/~mvo/synaptic/synaptic-0.57.1pre2.tar.gz]("http://people.ubuntu.com/%7Emvo/synaptic/synaptic-0.57.1pre2.tar.gz")

Also note that even though you upgrade to the new version, it does **NOT** overwrite your previous synaptic verion, that is why I am eager to get this added for new release and see if it is worth adding the backports. So far, it's not done me any harm and runs smoothly.

Only issue is that I am having to run it through as root to make this load, any ideas on how to get this to load otherwise would be greatly appreciated!

I'm going to research this a bit more of as to why this package is more stable than the 0.57 although it was due to scrollkeeper in which was not compiling correctly with the newest version of Synaptic.

I haven't found anything based on wgets new release but I am sure that there will be in the next week or so. I'll keep this topic updated for both packages.

[http://wget.sunsite.dk/]("http://wget.sunsite.dk/")

-------------------------------------------------------------------------------------------------------------

**EDIT: **An updated screen shot link of Synaptic 0.57.1 on my desktop.

[http://img259.imageshack.us/my.php?image=synaptic7jl.png]("http://img259.imageshack.us/my.php?image=synaptic7jl.png")

-------------------------------------------------------------------------------------------------------------

**EDIT #2: **Only real changes there are in synaptic is that the main window of setting up and unpacking the packages is now no longer being displayed when showing the repos being installed. 

Also, the packages are being installed much faster than usual, so some lib updates are added as well.

## Still researching other changes.

-------------------------------------------------------------------------------------------------------------

**EDIT #3: **ChangeLog in 0.57.1

 > 2003-01-21 12:47  mvogt

    * po/: zh_CN.po, zh_HK.po, zh_TW.po: * some po updates from Anthony
    Fok 

Also new update manager notification icon and others as well.

---

### Post by XDevHald on 2005-07-01
Ok, as of right now, the above post is as stands of what is current with the wget and synaptic version.

I am still waiting for an e-mail from Michael Vogt based on actual release of what the changes were in the verion.

---

### Post by XDevHald on 2005-07-05
I have been chatting with Michael Vogt on the Synaptic updates and what news is in on it's basic updates compared to 0.56. Here is the updated news I have received from him during our chat.

 >  Here are the changes (from the NEWS file):
0.57.2:
 - if no changes are detected in the terminal window in
   rgdebinstallprogress after a certain timeout the expander
   is opened (assuming that something hangs inside)
 - updated Chinese/Traditional translation (thanks to Woodman Tuen)
 - updated Bulgarian translation (thanks to Yavor Doganov)
 - updated Catalan translation (thanks to Jordi)
0.57:
 - updated Bulgarian translation (thanks to Yavor Doganov)
 - updated Spanish translation (thanks to Jorge Bernal)
 - updated Brasilian translation (thanks to Andre Luis Lopes)
 - set title in repository window
 - various bugfixes (should build on rpm fine again)
 - dist-upgrade is default when when hiting upgrade
0.56.1:
 - minor bugfix

It's probably slightly more but that's about it. Mostly bugfixes and
i18n updates, some UI improvments.


 >  Please send me
a short notice if you plan to backport synaptic so that I can check if
it's safe or not (e.g. because some stuff is too experimental or
because it depends on new apt features).  

It is VERY important that whoever is Backport Developer and has contact to Michael Vogt that they e-mail him before doing any further updates to the backports for Synaptics Package Manager.

If no one from the Backport Staff has contact with him, please contact me so I can get a hold of him. 

**The e-mail will not be posted due to security purposes.**

---

### Post by XDevHald on 2005-07-07
The 0.57.2 is planted in Breezy in which everyone knows about, but could we get this backported to the mirrors if this is possible?

---

### Post by jdong on 2005-07-07
the changelog doesn't sound too impressive... Don't think we'll be backporting this. Keep in mind that Synaptic is an app that is tightly integrated with the update manager system, not to mention that it always executes with root privs.

Wait for Breezy.

---

### Post by XDevHald on 2005-07-07
[QUOTE=jdong]the changelog doesn't sound too impressive... Don't think we'll be backporting this. Keep in mind that Synaptic is an app that is tightly integrated with the update manager system, not to mention that it always executes with root privs.

Wait for Breezy.[/QUOTE]
 > Wait for Breezy. - Already  running it :D 

But thanks for the quick reply :)

---

