---
title: "Covering my tracks"
date: 2008-10-07
forum: Security
---

### Post by dgg9879 on 2008-10-07
What is the best way to eliminate evidence of what sites I've visited, incriminating data on hard drive etc on ubuntu ie something like evidence eliminator for windows.

I read that no software, even evidence eliminator, can completely wipe all evidence. Is that true?

---

### Post by stinger30au on 2008-10-07
dban will do the trick

[http://www.dban.org/](http://www.dban.org/)

---

### Post by ajgreeny on 2008-10-07
However, I don't think you can use dban on an existing, installed OS and keep the OS on the disk.  It is good for completely wiping a disk (takes for ever on a large disk) but certainly does the job.  The only thing I can think of which might work for you is shred```
shred -uv path/to/folder file.name
```Have a look at ```
man shred
``` for more info.

---

### Post by hyper_ch on 2008-10-09
install a fully encrypted system.

---

### Post by geester on 2008-10-09
If you Google "File destoyer", this does it, well it did it for me when I sold my old computer, I destroyed all my online banking detaisl with it and they couldn't be restored.

---

### Post by hyper_ch on 2008-10-09
and how does it handle the journaling?

---

### Post by jerome1232 on 2008-10-09
> **hyper_ch said:**
> install a fully encrypted system.
edit: reworded my post a bit

+1, 

You don't want to know how much browser cache I've recovered from a formated Hard Drive before.

If you don't want to go full disk encryption (the best solution) then empty your cache and use a program like shred to randomise the free space on your drive, I doubt that would account for the journal as Hyper pointed out but then again I don't know how to take advantage of information stored there either.

---

### Post by cariboo on 2008-10-09
I have a brother-in-law that works for the Provincial Government. He told me they take a sledge hammer to the hard drives of outdated computers then send them off to the recyclers.

Jim

---

### Post by lisati on 2008-10-09
Firefox has its Tools->clear private data option, but I take it that the OP wants something more.

---

### Post by HermanAB on 2008-10-09
It depends on your threat level.  If you are only interested in protecting yourself against your little kid sister, then the Firefox privacy settings or 'shred' will work.  However, in this case, a better quality password and a separate user account for your little kid sister is still better.

There are tools like 'sleuthkit' with the 'forensic browser' that can reveal much of what has been deleted by common delete and overwrite utilities such as 'shred'.

If you are worried about a more knowledgeable snoop, then you should encrypt your hard disk.

Cheers,

Herman

---

### Post by Old_Grey_Wolf on 2008-10-09
> **HermanAB said:**
> There are tools like 'sleuthkit' with the 'forensic browser' that can reveal much of what has been deleted by common delete and overwrite utilities such as 'shred'.

Hmmm. I have never been able to recover data using sleuthkit/autopsy after the shred command was used properly.

---

### Post by HermanAB on 2008-10-10
The results of shred depends on the file system used.  If you are using a journaling FS and nowadays it is pretty much the default, then shred may not delete things effectively.

The best way to delete a disk is to use an encrypted disk and forget the key.

---

### Post by randy78 on 2008-10-11
There is a script inside the Secure-Delete package that will allow you to run a secure wipe of user defined directories.

This is the closest thing I've seen to having something like CCleaner in Gnome, as KDE has a privacy menu.

You can apt-get install secure-delete or you can download the source package [http://freeworld.thc.org/releases.php?s=4&o=1]("http://freeworld.thc.org/releases.php?s=4&o=1") and modify "the_cleaner.sh" script to fit your needs (BE CAREFUL!)
Don't let the name fool you, THC (The Hacker's Choice) is a reputable group of guys and they release top quality software.
Most of their stuff is already included in the Ubuntu repositories.

After you get Secure-Delete installed, its command is srm -v -r (for directories) then the file, like this "srm -vr /home/kooky/PDF/yourfile.pdf" Be sure to look at the manual (In a terminal, run "man srm" without the quotes)

Note that this program is extremely powerful and does not require super-user privileges, so BE CAREFUL!

Don't forget to clear the flash-cookies from the /home/.macromedia directory, the .thumbnails directory and the recent documents (menu, places, recent documents, clear) and also run "history -c" in the terminal, to clear previous terminal commands.

Clear Private Data in Firefox (Ctrl+Shift+Delete) and be sure to check every box (unless you have Firefox store passwords for you)

Afterwards, it's just a matter of wiping the unused space on your hard drive.

Good luck!
:guitar:

---

### Post by djhedges on 2008-10-12
Browse from a LiveCD inside vmware.  Then all your history is stored on ram.

---

### Post by bcom on 2008-10-15
Here is a link to the Adobe Flash Player Settings Manager that I found on Slashdot: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html)

Go to the tab for Web Privacy Settings to delete cookies.

The settings manager is a GUI that lets you delete the Flash-Cookies as well as make other changes to the security settings.

---

### Post by Nesaskewatch on 2009-11-14
> **bcom said:**
> Here is a link to the Adobe Flash Player Settings Manager that I found on Slashdot: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html)

Go to the tab for Web Privacy Settings to delete cookies.

The settings manager is a GUI that lets you delete the Flash-Cookies as well as make other changes to the security settings.

Buddy!  I had no idea sites were accessing my camera/mic!  They won't anymore.  Thanks for that link!!!

May all who sail in you be blessed.  Here endeth the lesson.

---

### Post by rookcifer on 2009-11-15
A few ways:

1) Use whole disk encryption and don't allow anyone physical access to the machine while it is on.

2) Use a liveCD for browsing.

3) Use Firefox's private browsing mode (Tools --> Start Private Browsing).

4) Manually deny write access to the cache folders that Firefox writes to.

5) Use shred to delete the files in the browsing cache and then use smfill to securely delete all free space on the partition.

Obviously, the easiest way is simply to use #3.

---

### Post by tubbygweilo on 2009-11-15
> **bcom said:**
> Here is a link to the Adobe Flash Player Settings Manager that I found on Slashdot: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html)

Go to the tab for Web Privacy Settings to delete cookies.

The settings manager is a GUI that lets you delete the Flash-Cookies as well as make other changes to the security settings.

Nesaskewatch,
You may also wish to look at the Mozilla Firefox extention [BetterPrivacy]("https://addons.mozilla.org/en-US/firefox/addon/6623") in addition to the Adobe offerings.
> Better Privacy serves to protect against not deletable longterm cookies, a new generation of 'Super-Cookie', which silently conquered the internet. This new cookie generation offers unlimited user tracking to industry and market research. Concerning privacy Flash- and DOM Storage objects are most critical.
This addon was made to make users aware of those hidden, never expiring objects and to offer an easy way to get rid of them - since browsers are unable to do that for you

---

### Post by RH9R on 2010-04-12
current version of firefox for hardy is 3.0.19 Perhaps the more recent releases have a later version. 
What version of BP do folks use for the 3.0.19?

---

### Post by Soul-Sing on 2010-04-12
> **HermanAB said:**
> The results of shred depends on the file system used.  If you are using a journaling FS and nowadays it is pretty much the default, then shred may not delete things effectively.

The best way to delete a disk is to use an encrypted disk and forget the key.

Indeed, that imo,the best way, the safest way, other than "hammering" and shredding it physically.( Even then companies as Norman can recover sever damaged hard disks, even from the bottom of the sea.)
:KS

---

### Post by rookcifer on 2010-04-12
> **leoquant said:**
> Indeed, that imo,the best way, the safest way, other than "hammering" and shredding it physically.( Even then companies as Norman can recover sever damaged hard disks, even from the bottom of the sea.)
:KS

Journaling filesystems have no effect on the efficacy of tools like shred, when these tools are used to erase the *whole disk.*  The journaling FS issue only comes into play when trying to overwrite a single file in place.  But even that isn't an issue when the FS is mounted data=ordered, which is the default in Ubuntu and most Linux distros.  Therefore, the whole issue is moot and nothing to worry about.

---

### Post by f1r3flie on 2010-04-13
If you also need to conceal your Internet activity from prying eyes using TOR and torbutton will be helpful. It is a service that sends your Internet communications through a string of random routers to get to you, thereby making it untraceable to you (although there is a small chance someone could read the data). It slows down your Internet a bit, but it can be turned on and off so you can disable it when watching YouTube etc.

---

### Post by Jive Turkey on 2010-04-14
If you live in the United States you also need to destroy your ISP's datacenters as they are required to keep records of that stuff for a period of time under the patriot act.  Only law enforcement is supposed to have access to it, but who really knows.  Also the sites you visit could have logs, and there might be other ways.  The sledge hammer method mentioned above should work pretty well for your HDD.

I urge you to look at whatever it is you are hoping to hide and ask yourself if that activity was in anyone's best interest.

---

