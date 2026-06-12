---
title: "Ubuntu One on web doesn't display all my files"
date: 2010-02-12
forum: Ubuntu One (CLOSED)
---

### Post by wjwh on 2010-02-12
In the My Files folder in Ubuntu One, I have a sub-folder which contains over 400 small files.  I can see all these in Ubuntu One on my computer (using Nautilus).  However, when I try to view them on the Web, the display there will only show me one page of these files (about 40-50).  Consequently, I cannot find out whether the others in the cloud have synchronised.  Certainly, they are _not_ synchronising with my other computers.  Is there a way that I can get Ubuntu One to let me see all my files in the cloud (apart from setting them up in a multitude of different folders, each holding about 40 files)?

---

### Post by joshuahoover on 2010-02-12
> **wjwh said:**
> In the My Files folder in Ubuntu One, I have a sub-folder which contains over 400 small files.  I can see all these in Ubuntu One on my computer (using Nautilus).  However, when I try to view them on the Web, the display there will only show me one page of these files (about 40-50).  Consequently, I cannot find out whether the others in the cloud have synchronised.  Certainly, they are _not_ synchronising with my other computers.  Is there a way that I can get Ubuntu One to let me see all my files in the cloud (apart from setting them up in a multitude of different folders, each holding about 40 files)?

It's possible that the files are still trying to transfer to the server. You can check this in a terminal session, running the following command:

u1sdtool --current-transfers

If that command reports no files are transferring, then we could use some debug logs to see what is going on. You can do this by:


[LIST=1]
[*]Quit Ubuntu One
[*]Open (or create if it doesn't exist):  ~/.config/ubuntuone/syncdaemon.conf 
[*]Add the following 2 lines to this file and save: 
[main] 
 log_level = DEBUG 
 
[*]Restart the  Ubuntu One client 
[*]If it's not syncing, then please add a file to your ~/Ubuntu One/ folder to get it to sync
[*]Wait until Ubuntu One says it's done syncing files
[*]Right-click on Ubuntu One and select "Report a Problem" to file a bug report 
[*]Attach  ~/.cache/ubuntuone/log/syncdaemon.log to the bug report
[/LIST]
Thank you,

Joshua

---

### Post by wjwh on 2010-02-15
[QUOTE=joshuahoover;8815366]It's possible that the files are still trying to transfer to the server. You can check this in a terminal session, running the following command:
u1sdtool --current-transfers

I would have thought that 13 days would have been long enough for files to transfer!  That is how long these files have been in the Ubuntu One folder on my main computer.

Also, the command u1sdtool --current-transfers indicates that nothing is transferring.  However, some files have now synchronised with my other computers - but I can still only see about 40-50 of them in Ubuntu One on the web.  I can find no way to go to another page or to scroll further down the list of over 400.

---

### Post by rtg on 2010-02-16
Hello,

In order to make sure that there are files that are not synchronized, could you please run the script from [LP:488232]("https://launchpad.net/bugs/488232"). It will show what files are not yet synchronized.

---

### Post by wjwh on 2010-02-23
> **rtg said:**
> Hello,

In order to make sure that there are files that are not synchronized, could you please run the script from [LP:488232]("https://launchpad.net/bugs/488232"). It will show what files are not yet synchronized.

As I said in my previous post, some files certainly _have_ synchronised with my other computers now, so I am reasonabley satisfied that synchronisation is occurring.  However, I can still only see around 40 of these files in Ubuntu One on the web.  It seems to be showing only one page - with no facility to move to a new page or to scroll further down the list of around 400 files which I know are in that folder.  Some of the files that have synchronised with my other computers are among the ones that I cannot view on the web, so I know that they must be there - somewhere.  Is there no way to view all these files?

---

### Post by DedMoroz on 2010-02-26
Ive noticed something like this (files not appearing on the UbuntuOne website) when Im using Google Chrome browser. I can see them fine though in Firefox.

---

### Post by wjwh on 2010-02-28
> **DedMoroz said:**
> Ive noticed something like this (files not appearing on the UbuntuOne website) when Im using Google Chrome browser. I can see them fine though in Firefox.

Unfortunately, I am using Firefox and I still cannot see my files!  I haven't been using Chrome.

---

### Post by joshuahoover on 2010-03-01
> **wjwh said:**
> As I said in my previous post, some files certainly _have_ synchronised with my other computers now, so I am reasonabley satisfied that synchronisation is occurring.  However, I can still only see around 40 of these files in Ubuntu One on the web.  It seems to be showing only one page - with no facility to move to a new page or to scroll further down the list of around 400 files which I know are in that folder.  Some of the files that have synchronised with my other computers are among the ones that I cannot view on the web, so I know that they must be there - somewhere.  Is there no way to view all these files?

The reason Roman (rtgz) wants you to run his script is so we can see whether ALL your files have been synchronized with the server or not. There are two likely issues here: 1) Not all your files have synchronized to the server properly or 2) The web UI is preventing you from seeing more than 40 files when it should be showing 400. I have a folder with over 100 files in it and am able to see all of them in the web UI. This is using Firefox 3.5.8 on Karmic.

Thank you,

Joshua

---

