---
title: "CVS-like (virtual) filesystem"
date: 2004-12-21
forum: The Cafe
---

### Post by ubuntu_demon on 2004-12-21
I think Ubuntu needs a CVS-like (virtual) filesystem in the future.

You could use it for example only for /home and non-binary files in /.  With a bit of thinking it wouldn't cost dramatically much space.

from  [http://www.osnews.com/story.php?news_id=9192&page=2](http://www.osnews.com/story.php?news_id=9192&page=2) :
> 
Versions

I have also been considering keeping versions of each object when that object is modified. So instead of actually changing that object, it clones it and then modifies the clone. That way if you have made a mistake and need to go back, or if you want to see what changes have been made you can view the differences. I.E. you have built-in CVS.

To go along with this there should be some mechanisms for cleaning up old objects that are no longer required. For instance if you have been modifying some source code and you had version 7 that worked and then you made several changes in versions 8, 9, 10, 11, and 12. And 9, 10 and 11 had bugs that you don't want to keep. When you are finished you should be able to remove those unneeded versions.

Disk space is extremely cheap now. I just checked and you can buy a 200 Gigabyte hard drive for just over $100. And Sony's Blu-ray discs will be able to hold 23 Gigabytes of data per layer. Given that kind of storage space I think saving multiple copies of your work just makes sense. 


maybe this is interesting :
VCFS: Virtual CVS Filesystem
[http://vcfs.sourceforge.net/](http://vcfs.sourceforge.net/)

Or maybe it could work with diff. 

Any ideas / links / opinions ?

---

### Post by shimon on 2004-12-21
or maybe not
there are ALWAY backup files saved of all files when you save them they are hidden chose to show hidden files and you will see it

---

### Post by wulf on 2004-12-21
In [another thread](http://ubuntuforums.org/showthread.php?t=7943&highlight=cvs), Chuck Vose wrote:
> Many serious admins use some version of CVS or RCS to track the
changes they make to the system; you would probably be happier if you
did too
He hasn't come back with an answer to my 'how' question yet - if nothing shows up around here, I might do some digging around to find out more about CVS sometime in the next couple of weeks.

Wulf

---

### Post by ubuntu_demon on 2004-12-21
[QUOTE=shimon]or maybe not
there are ALWAY backup files saved of all files when you save them they are hidden chose to show hidden files and you will see it[/QUOTE]
 Sure some applications use (temporary) backup files. But it's nice to have it outside of the applications. Because now it is up to them how they do it. Besides CVS is more than just temporary backups.

One CVS-like way for all files you work on is much better.

---

### Post by shimon on 2004-12-21
well it accully a ext3 feature that other filing system happened to copy there is a way for an app to disable it and many do...

---

### Post by ubuntu_demon on 2004-12-21
[QUOTE=shimon]well it accully a ext3 feature that other filing system happened to copy there is a way for an app to disable it and many do...[/QUOTE]
 I don't understand what you're saying here. I'm not talking about ext3 features. I'm talking about creating a virtual filesystem on top of the filesystem you're using to add CVS-like support.

---

### Post by Lovechild on 2004-12-21
I've been thinking of a system like this but with some metastorage facilities as well, possibly couppled in a database to handle easy searching and solve a few problems, like the stuff the GNOME team has talked about for a while about default places to store stuff and i18n.

---

### Post by ubuntu_demon on 2004-12-21
[QUOTE=Lovechild]I've been thinking of a system like this but with some metastorage facilities as well, possibly couppled in a database to handle easy searching and solve a few problems, like the stuff the GNOME team has talked about for a while about default places to store stuff and i18n.[/QUOTE]
 there's some talk about a winFS-like filesystem here :

Longhorn-like features that Ubuntu needs
[http://www.ubuntuforums.org/showthread.php?t=7567](http://www.ubuntuforums.org/showthread.php?t=7567)

But I think adding a virtual filesystem as a layer upon the filesystem is quicker to implement to test the idea out.

A new filesystem based upon relational databases and CVS. That would rock.

---

### Post by EdCrypt on 2004-12-21
That would be a nice hack with the gnomeVFS libs.

---

### Post by ubuntu_demon on 2004-12-21
A nice article about future file systems. But they don't talk about CVS-like abilities. 

File Systems and Databases
[http://www.osnews.com/story.php?news_id=9228](http://www.osnews.com/story.php?news_id=9228)

---

