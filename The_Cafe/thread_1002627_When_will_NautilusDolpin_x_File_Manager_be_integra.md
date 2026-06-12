---
title: "When will Nautilus/Dolpin/ x File Manager be integrated with PolicyKit?"
date: 2008-12-05
forum: The Cafe
---

### Post by JerecDrak2 on 2008-12-05
I was just reading about PackageKit integration and it suddenly occurred to me that PolicyKit isn't really fully implemented across the system yet, if it was there would be no use for sudo/gksudo. I'm just wondering if there are plans to integrate it into file managers so we don't have to run them as root when we want to play with some system files? For totally inexperienced users I think the complete integration of PolicyKit is necessary so that they can get on with what they're trying to do and not be lumped with an "insufficient privileges" message and then stumped as to how to proceed.

---

### Post by decoherence on 2009-06-29
Hi. I'm just gonna bump this. Anyone know how this is going?

---

### Post by juancarlospaco on 2009-06-29
What do you want?, you are full privilege at your $HOME only, 
and thats very nice :)

---

### Post by 23meg on 2009-06-29
[http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/](http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/)

---

### Post by Skripka on 2009-06-29
> **JerecDrak2 said:**
>  For totally inexperienced users I think the complete integration of PolicyKit is necessary so that they can get on with what they're trying to do and not be lumped with an "insufficient privileges" message and then stumped as to how to proceed.

This strikes me as an astronomically bad idea...not to mention the fact that the number of reasons for a user to be messing in the system folder with a file manager are few and far between.

---

### Post by zekopeko on 2009-06-29
> **Skripka said:**
> This strikes me as an astronomically bad idea...not to mention the fact that the number of reasons for a user to be messing in the system folder with a file manager are few and far between.

far more danger if you run something with gksudo/sudo.
mac os x has something similar and is very nice to have for those occasions when you do want to mess with the system folders.

---

### Post by Skripka on 2009-06-29
> **zekopeko said:**
> far more danger if you run something with gksudo/sudo.
mac os x has something similar and is very nice to have for those occasions when you do want to mess with the system folders.

Meh.  The second you have to type sudo for a command-flags should be going off in the users' mind regarding what it is they are doing and why.  As I said-the number of reasons to be messing with a file manager in the root folder are very few....Just about ***_EVERY_*** tutorial or instruction for editing something in the system folders uses the terminal and NOT a file manager anyway.

I suppose everyone has heard the classic about the lady that calls the IT helpdesk saying that her computer no longer works?  When asked-she said that she was looking in her file manager and found a folder full of files that seemes completely disorganized-so she went and neatened them up...which later turns out to be the system folder.

---

### Post by decoherence on 2009-06-30
> **Skripka said:**
> Meh.  The second you have to type sudo for a command-flags should be going off in the users' mind regarding what it is they are doing and why.

Absolutely! And the same should be true for any authentication dialog. In fact, with an authentication dialog, we can do an even better job than sudo does (and OS X) by putting a warning in the authentication dialog so that people are always reminded when they are stepping out of the limited user role.

This would be a big improvement over sudo, which only gives you a warning the first time you use it. Also, I've seen people get in to the habit of running sudo unnecessarily, 'just in case.' And then there's the ever contentious "free ticket" it gives you for however long afterwards. Proper integration of PolicyKit would make that unnecessary.

> As I said-the number of reasons to be messing with a file manager in the root folder are very few....Just about ***_EVERY_*** tutorial or instruction for editing something in the system folders uses the terminal and NOT a file manager anyway.

So you acknowledge that there are valid reasons to be messing about outside your home folder? ;)

Say, for example, your friend just set up a web server. Is it going to be easier for them to move their html from their home to /var/www through the command line with sudo mv or with drag and drop and an authentication dialog? For you or I the answer might be the command line, but try explaining that to your friend.

Oh, and I think those tutorials that say "copy and paste this in to the command line" are a TERRIBLE idea. At best they are a band-aid until we have a system that is consistent enough that it can be explained at a more conceptual level. PolicyKit integration is a big chunk of that.

> I suppose everyone has heard the classic about the lady that calls the IT helpdesk saying that her computer no longer works?  When asked-she said that she was looking in her file manager and found a folder full of files that seemes completely disorganized-so she went and neatened them up...which later turns out to be the system folder.

The alternative -- having new users playing with sudo on the command line -- is no better. I would argue that it's worse. After all, it's difficult to accidentally rm -rf something from the GUI.

I think the question here is "should we be able to do our standard administrative tasks completely through the gui?" As in, rather than opening a terminal and typing vi /etc/fstab, we browse to /etc/fstab, open it in gedit and authenticate when we have to save.

It's just as easy to mess up an OS X system this way but you don't hear about it. The thing is, nobody would edit their /etc/fstab -- in vi OR gedit (or textedit.app) -- unless they had a reason to.

---

### Post by decoherence on 2009-06-30
> **23meg said:**
> [http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/](http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/)

Hehe that's the blog post that originally turned me on to this :lolflag: Thanks anyway :) maybe I should get in touch with alex?

I found the GNOME bug...

[http://bugzilla.gnome.org/show_bug.cgi?id=490200](http://bugzilla.gnome.org/show_bug.cgi?id=490200)

not much new information there, though.

---

### Post by geoken on 2009-06-30
I like this idea. I find the terminal inefficient for browsing directories and transferring files in most situations and especially in situations where I'm not completely sure which exact file 'm looking for.

sudo nautilus has always been my preferred method for browsing protected config files I needed to edit.

---

### Post by NTolerance on 2009-08-14
> **decoherence said:**
> Absolutely! And the same should be true for any authentication dialog. In fact, with an authentication dialog, we can do an even better job than sudo does (and OS X) by putting a warning in the authentication dialog so that people are always reminded when they are stepping out of the limited user role.

This would be a big improvement over sudo, which only gives you a warning the first time you use it. Also, I've seen people get in to the habit of running sudo unnecessarily, 'just in case.' And then there's the ever contentious "free ticket" it gives you for however long afterwards. Proper integration of PolicyKit would make that unnecessary.



So you acknowledge that there are valid reasons to be messing about outside your home folder? ;)

Say, for example, your friend just set up a web server. Is it going to be easier for them to move their html from their home to /var/www through the command line with sudo mv or with drag and drop and an authentication dialog? For you or I the answer might be the command line, but try explaining that to your friend.

Oh, and I think those tutorials that say "copy and paste this in to the command line" are a TERRIBLE idea. At best they are a band-aid until we have a system that is consistent enough that it can be explained at a more conceptual level. PolicyKit integration is a big chunk of that.



The alternative -- having new users playing with sudo on the command line -- is no better. I would argue that it's worse. After all, it's difficult to accidentally rm -rf something from the GUI.

I think the question here is "should we be able to do our standard administrative tasks completely through the gui?" As in, rather than opening a terminal and typing vi /etc/fstab, we browse to /etc/fstab, open it in gedit and authenticate when we have to save.

It's just as easy to mess up an OS X system this way but you don't hear about it. The thing is, nobody would edit their /etc/fstab -- in vi OR gedit (or textedit.app) -- unless they had a reason to.

I'd like to add another point about the limitations of the command line with regards to file management.  The standard cp and mv tools fail to provide any information on status or speed of file transfers.  This is problematic during transfer of large files/folders (/var/lib/mythtv comes to mind).  

It's a shame that there seems to be little movement on Nautilus/Policykit integration.  I hope that Policykit dialogs can become standard across the OS.  

As you mentioned, Mac OS X has provisions for this, but Vista does as well.  The competition has got Ubuntu beat on this, unfortunately.

---

### Post by cariboo on 2009-08-14
> I'd like to add another point about the limitations of the command line with regards to file management. The standard cp and mv tools fail to provide any information on status or speed of file transfers. This is problematic during transfer of large files/folders (/var/lib/mythtv comes to mind).

Use mc in a terminal, it will provide the info you are looking for, another plus is that you can do much more with it. Mc is in the repositories.

---

### Post by NTolerance on 2009-08-14
> **cariboo907 said:**
> Use mc in a terminal, it will provide the info you are looking for, another plus is that you can do much more with it. Mc is in the repositories.

Thanks for the info.  I know there's quite a few more feature-filled command line file management programs.  Of course something like rsync could be used when copying large files to provide status/speed info, but it's just overkill IMHO.  

It's standard and straightforward to know and understand the mv/cp/nautilus behaviors as similar things are already present in other operating systems.  Having to learn a new and more complex program just to get status/speed info is a bit much I think.

---

### Post by Mornedhel on 2009-08-14
Side note : progress bars are not implemented in cp and mv, and probably won't be for quite some time. The reason is that both utilities are already horribly bloated, and the way they're coded now, adding progress bar support would probably create a few additional bugs. For a while, it was possible to get a Gentoo patch for progress bars in coreutils and compile them for source, but not anymore (the patch is for older versions and has been dropped from Gentoo).

---

### Post by Starlight on 2009-08-14
> **Skripka said:**
> This strikes me as an astronomically bad idea...not to mention the fact that the number of reasons for a user to be messing in the system folder with a file manager are few and far between.

Copying a theme to /usr/share/themes :P

---

### Post by Mornedhel on 2009-08-14
> **Starlight said:**
> Copying a theme to /usr/share/themes :P

Not a good reason. You want to install a theme and don't have administrative rights, you install your theme into ~/.themes. Same for fonts.

---

### Post by Xbehave on 2009-08-14
great take a simple system (that new users should understand), users vs root and make it much more complicated (on a code and concept level) and this is somehow better?

security is about simplicity,
*the less code used to decide if i can modify a file the better
*the simpler the system is to understand the better

If your not running natilus as root, you shouldn't be allowed to modify any file not owned by you.
If you are running natilus as root, you should know what your doing **and** there should be no limits on your powers to mess things up

---

### Post by NTolerance on 2009-08-14
> **Mornedhel said:**
> Not a good reason. You want to install a theme and don't have administrative rights, you install your theme into ~/.themes. Same for fonts.

Sure, but now when you run Synaptic or another root GUI app your eyes bleed when you see the default GTK theme.

---

### Post by NTolerance on 2009-08-14
> **Xbehave said:**
> great take a simple system (that new users should understand), users vs root and make it much more complicated (on a code and concept level) and this is somehow better?

security is about simplicity,
*the less code used to decide if i can modify a file the better
*the simpler the system is to understand the better

If your not running natilus as root, you shouldn't be allowed to modify any file not owned by you.
If you are running natilus as root, you should know what your doing **and** there should be no limits on your powers to mess things up

For "new users" there's nothing simple about system file management requiring the command line, either to start nautilus as root or even worse, use sudo cp/mv/rm etc...

---

### Post by SunnyRabbiera on 2009-08-14
> **NTolerance said:**
> 
It's a shame that there seems to be little movement on Nautilus/Policykit integration.  I hope that Policykit dialogs can become standard across the OS.  

As you mentioned, Mac OS X has provisions for this, but Vista does as well.  The competition has got Ubuntu beat on this, unfortunately.

No they have not, just because they both have GUI's doesnt make them better.
Plus Ubuntu has no control over what gnome does, in linux the DE is separate from the OS.

---

### Post by NTolerance on 2009-08-14
> **SunnyRabbiera said:**
> 
Plus Ubuntu has no control over what gnome does, in linux the DE is separate from the OS.

Ubuntu has contributed to the upstream GNOME project with items such as jockey, gnome-app-install, etc...

---

### Post by Xbehave on 2009-08-14
> **NTolerance said:**
> For "new users" there's nothing simple about system file management requiring the command line, either to start nautilus as root or even worse, use sudo cp/mv/rm etc...
start natilus as root is complicated? (it seams to me any "clever way" of doing this will just get in the way of people who really need to use natilus as root and will not benefit users who don't understand root/non-root)

> Sure, but now when you run Synaptic or another root GUI app your eyes bleed when you see the default GTK theme. And that is a bad thing? root apps should run with a different theme anyway. Besides just installing it to /usr/share/themes will not change what theme root apps use (a deliberate design choice in kdesu/gtksu)

---

### Post by Starlight on 2009-08-14
> **Xbehave said:**
> And that is a bad thing? root apps should run with a different theme anyway. Besides just installing it to /usr/share/themes will not change what theme root apps use (a deliberate design choice in kdesu/gtksu)

This is strange, but I've noticed that if I move a theme I'm using to /usr/share/themes, then root apps use it too. But you're right that root apps should look different. It would be nice if root apps by default used the same theme as normal apps, but with special root colors :)

---

### Post by Xbehave on 2009-08-14
> **Starlight said:**
> This is strange, but I've noticed that if I move a theme I'm using to /usr/share/themes, then root apps use it too. But you're right that root apps should look different. It would be nice if root apps by default used the same theme as normal apps, but with special root colors :)
Interesting i don't install custom themes but i do use kde and so its probably a bug somewhere causing my root apps to look different.

---

### Post by pelle.k on 2009-08-14
> When will Nautilus/Dolpin/ x File Manager be integrated with PolicyKit?
This topic has been up for discussion before, and nautilus isn't the only app that should have better integration with policykit (for example prompt for access if you move files to a unprevilegied location), but also gedit, so that you don't have the password prompt when opening a text file in say /etc, but when you actually want to save it.
So, the password prompt should come when you actually want to save the document, and not when you open it (if you have read privilegies, that is).
Such fine grained authentication is preferred, since you dont want to grant the *whole* application "root" access, but only the "save part", for example. This is possible with policykit, and say gedit, but when will we have it?

> And that is a bad thing? root apps should run with a different theme anyway. Besides just installing it to /usr/share/themes will not change what theme root apps use (a deliberate design choice in kdesu/gtksu)
It's a "good thing". But that doesn't mean the "root" theme has to be the super ugly gtk default. It could be a modified human gtk, or metacity could be modified to be red'ish (and include some warning in the titlebar).

---

