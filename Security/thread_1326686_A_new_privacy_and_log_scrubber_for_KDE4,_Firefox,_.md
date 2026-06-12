---
title: "A new privacy and log scrubber for KDE4, Firefox, &amp; Flash"
date: 2009-11-14
forum: Security
---

### Post by IgnorantGuru on 2009-11-14
A new script for cleaning KDE4 log files and more...

First I found out recently about Flash 'cookies'.  I'm a fairly security conscious if not paranoid person so I was surprised to be surprised.  They are nasty little critters that are used like cookies for tracking, and are often used by websites to recreate cookies you've deleted!  And they are ignored by Firefox's cleaning options.  Look around with a text editor in ~/.adobe/Flash_Player and ~/.macromedia/Flash_Player - unless you know about them and have disabled them, you've got 'em.  Plus, the tool Adobe offers to disable and manage them is highly questionable, requiring you to visit a webpage to change files and software stored locally.  Ummm...
About Flash cookies:
[http://www.imasuper.com/66/technology/flash-cookies-the-silent-privacy-killer/](http://www.imasuper.com/66/technology/flash-cookies-the-silent-privacy-killer/)

Like I always do with each new version of Ubuntu, I've been writing an updated script to cleanup logs files and all the insane recent activity tracking that KDE4 is so determined to do for us.  (Why it needs a record of every file one has accessed, copied, moved, or deleted for months makes one wonder.)  Just look in ~/.kde/share/config/kdeglobals and ~/.kde/share/config/plasma-desktop-appletsrc

In the course of writing that, I discovered that when you delete your browsing history and form data in Firefox, it doesn't actually REMOVE this data from it's SQL files.  It's all still there, as any text editor will show you.  This kind of "oops, I forgot" is pretty ridiculous for what they claim is a security-conscious browser.  Personally, I think this falls under the heading of a deliberate oops.  Ubuntu and its commonly used software seems to be following the Windows trend of randomly spraying user data all over the system.

I'm sharing the script I wrote for KDE4/karmic to clean up this and more.  This is a work in progress, and suggestions are welcome, but it does a decent amount, while also being careful.  It also has an experimental option to disable the evil Akonadi, Soprano, and Nepomuk servers in karmic, which eat up memory and CPU indexing files, which the Ubuntu devs think everyone wants running on their system slowing it down.

Please read the instructions carefully, and if you like details, open up the script and read it - it's well-commented.  Feel free to use it as-is or borrow pieces.

"USE AT YOUR OWN RISK – By design, kscrubber is a fairly heavy-handed script that removes and modifies a large number of files belonging to the system, KDE, and users. While every attempt is made to avoid breaking software or causing system instability, these outcomes are not impossible. If any instability is encountered, a reboot will generally correct it, as many of the files that kscrubber removes are temporary files which will be automatically recreated by the system or software. Nevertheless, it is recommended that you have a recent backup of your /home folder and your system before using kscrubber. See [Wikibook: How To Backup Operating Systems]("http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems") for help."

If it makes you feel better, I've been writing these cleanup scripts for years, including KDE3 and for SUSE as well.  Even my worst goofs only resulted in a few desktop problems which were cured by a reboot.  I've never had to reinstall my system or lost any data.  Nothing is impossible but this is pretty well tested and it treads carefully.

Please let me know if you do have any problems, and also if you have suggestions on how it can be improved I'd like to hear them.  Also, I don't know where Nepomuk and Soprano save their data - either I can't find it or I had them disabled from the start.  So if you can tell me what files to clobber that would be helpful.

kscrubber details and download...
[http://igurublog.wordpress.com/downloads/script-kscrubber/](http://igurublog.wordpress.com/downloads/script-kscrubber/)

---

### Post by FuturePilot on 2009-11-14
The Firefox sqlite issue is being worked on [https://bugs.launchpad.net/ubuntu/+source/sqlite3/+bug/457791]("https://bugs.launchpad.net/ubuntu/+source/sqlite3/+bug/457791")

---

### Post by IgnorantGuru on 2009-11-14
Thanks for the link - good to know this is being addressed.  I hope they release an update for karmic, not just a PPA.

---

### Post by rookcifer on 2009-11-15
This is what firefox's private browsing mode is for.

As for flash cookies, all you have to do is deny write access to the flash cookie folder (though some flash websites wont work if you do this).

---

### Post by IgnorantGuru on 2009-11-15
> **rookcifer said:**
> This is what firefox's private browsing mode is for.

That may avoid the database problem for new data, but it won't delete data already in the database - there is no way in the current Firefox to do so.  Also,  sometimes it's nice to have a history and form completion, etc., and then be able to delete it when you're done.  Due to the bug in Ubuntu's build of Firefox that deletion is not done properly.

> As for flash cookies, all you have to do is deny write access to the flash cookie folder (though some flash websites wont work if you do this).

I had problems with Flash player running or npviewer.bin crashing when I tried that - perhaps it depends on the version and the websites.  Another option is to use Adobe's website to disable the LSOs.  It's important to remember that it's not just Flash content websites that will use these.  Many website have hidden flash modules whose sole purpose is to use these cookies for tracking and recreating conventional cookies that have been deleted.

This command deletes the Flash cookies one time only (best to close browsers first), but Flash will create more.

```
rm -r ~/.adobe/Flash_Player/* && rm -r ~/.macromedia/Flash_Player/*
```

Another option is to replace the ~/.adobe and ~/.macromedia folders with links to folders in /dev/shm (which is the default ramdrive).  You need to recreate the folders in /dev/shm each time KDE or Gnome starts, perhaps using a script in Autostart.  That way Flash can use the cookies and websites work, but the data is not written to disk, only memory, and is not persistent between boots.

For example, if you close Firefox, then save the script below to "~/.kde/Autostart/moveflash"

```
#!/bin/bash

# Move flash player cookies to ramdrive

rm -r ~/.macromedia/Flash_Player
rm -r ~/.adobe/Flash_Player
mkdir -p /dev/shm/flashcookies/.macromedia/Flash_Player
mkdir -p /dev/shm/flashcookies/.adobe/Flash_Player
ln -s /dev/shm/flashcookies/.macromedia/Flash_Player ~/.macromedia/Flash_Player
ln -s /dev/shm/flashcookies/.adobe/Flash_Player ~/.adobe/Flash_Player
#

```

Then make it excutable and run it with:

```
chmod +x ~/.kde/Autostart/moveflash && ~/.kde/Autostart/moveflash
```

The change will be made, and those folders in /dev/shm will be automatically recreated when you reboot.

---

