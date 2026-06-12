---
title: "Is there an Ubuntu CE metapackage?"
date: 2007-07-06
forum: Ubuntu Christian Edition
---

### Post by KIAaze on 2007-07-06
Hi,

I was wondering if there is an Ubuntu CE metapackage as there is one for ubuntustudio for example.
I would like to try it out without having to reinstall Ubuntu.

---

### Post by avik on 2007-07-06
Apparently, there are two things you can do, according to [this page]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html"):

You should be able to download the main ISO and use it as a LiveCD to try it out.  Or, you can use the conversion script on that page.

There might be other options that other members might be able to point to you towards.

---

### Post by mysticrider92 on 2007-07-07
As avik said you can use the convert_me script to try it out. The changes are reversable if you don't like it. A meta-package has been suggested a few times, but the changes are a bit to complicated for that to work.

---

### Post by KIAaze on 2007-07-07
Thanks, I had a quick look at the script, but I don't see any way to reverse the changes.
Is there no script for reversing them yet?

I'm already using Gutsy, so I don't want to mess things up to much.
From what I've seen everything gets backed up into UbuntuCE_Backups and then the packages are installed.

However, there are certain things that don't seem to be backed up like here:

```
function remove_files()
{
	rm -f "/usr/lib/firefox/firefox.cfg"
	rm -f "/etc/firefox/pref/firefox.js"
	rm -f "/usr/share/pixmaps/firefox.png"
	rm -f "/etc/firefox/profile/bookmarks.html"
}

```

I think I'll just wait for now. But I know some friends that might be interested in the script. :)

And why does the script remove bug-buddy?!

---

### Post by mhancoc7 on 2007-07-07
> **KIAaze said:**
> Thanks, I had a quick look at the script, but I don't see any way to reverse the changes.
Is there no script for reversing them yet?

I'm already using Gutsy, so I don't want to mess things up to much.
From what I've seen everything gets backed up into UbuntuCE_Backups and then the packages are installed.

However, there are certain things that don't seem to be backed up like here:

```
function remove_files()
{
    rm -f "/usr/lib/firefox/firefox.cfg"
    rm -f "/etc/firefox/pref/firefox.js"
    rm -f "/usr/share/pixmaps/firefox.png"
    rm -f "/etc/firefox/profile/bookmarks.html"
}

```I think I'll just wait for now. But I know some friends that might be interested in the script. :)

And why does the script remove bug-buddy?!

There isn't a script to reverse the changes. Most things are backed up for the users convenience. However, some items that relate to the web filtering configuration are not backed up. i do not want to make it too easy to undo those changes.

Also, the script is not designed for Gutsy.

Thanks for your interest, Jereme

---

### Post by KIAaze on 2007-07-08
Well, I tried the script out anyway, and of course my PC overheated and crashed during the process (temp went above 73 C => immediate shutdown).

Now i am greeted with 2 eroor messages and no taskbars/menubars... :/

The error messages:

> The application "gnome-panel" attempted to change an aspect of your configuration that your system administrator or OS vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.

> The application "evolution-alarm-notify" attempted to change an aspect of your configuration that your system administrator or OS vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.


And then a lot of details starting with "no database available to save your configuration: ..."
i have to copy things by hand right now since I don't have internet and I don't want to copy all of it right now.

While I can understand that you don't want to make it to easy to undo the changes, an undo script might have come in handy here.
I already started making a little undo script, but it will probably be faster if I can locate the exact cause and fix it.
I already tried to remove all ~/.gconf*, but it didn't work.

---

### Post by mhancoc7 on 2007-07-08
> **KIAaze said:**
> Well, I tried the script out anyway, and of course my PC overheated and crashed during the process (temp went above 73 C => immediate shutdown).

Now i am greeted with 2 eroor messages and no taskbars/menubars... :/

The error messages:






And then a lot of details starting with "no database available to save your configuration: ..."
i have to copy things by hand right now since I don't have internet and I don't want to copy all of it right now.

While I can understand that you don't want to make it to easy to undo the changes, an undo script might have come in handy here.
I already started making a little undo script, but it will probably be faster if I can locate the exact cause and fix it.
I already tried to remove all ~/.gconf*, but it didn't work.

Sorry for your trouble, but like I said before the script id not designed for Gutsy. :)

Jereme

---

### Post by KIAaze on 2007-07-09
Well, after using Debian yesterday evening and booting into Ubuntu this morning, it suddenly worked. I don't know why, but now it's usable again.
You did a lot of customization for the menu bar and Firefox. :)

I couldn't access the Dansguardian configuration GUI however. I'll have to run the script again as soon as I can to make sure that it finishes successfully, but I don't have an internet connection at home right now.

---

