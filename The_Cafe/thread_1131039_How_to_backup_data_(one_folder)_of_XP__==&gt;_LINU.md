---
title: "How to backup data (one folder) of XP  ==&gt; LINUX machine, periodically?"
date: 2009-04-20
forum: The Cafe
---

### Post by frenchn00b on 2009-04-20
Hello,

How to backup data (one folder) of XP  ==> LINUX machine, periodically?

c:\foldertobackup (25GB) source  =====>   LINUX   (delete the changes here) mirror

if I delete in c:\foldertobackup it should also delete into hte linux folder.

Any ideas how to make it ? 
whatever idea accepted that is fast and easy

---

### Post by rotwang888 on 2009-04-20
Try rsync or grsync (rsync with a gui).

---

### Post by frenchn00b on 2009-04-20
> **rotwang888 said:**
> Try rsync or grsync (rsync with a gui).

it is for windows? 
because windows has not single shares,
it can access the samba of linux

---

### Post by logos34 on 2009-04-20
maybe use automatic incremental backup in rsync or sbackup

---

### Post by frenchn00b on 2009-04-20
> **logos34 said:**
> maybe use automatic incremental backup in rsync or sbackup

and it is included already in microsoft XP?

---

### Post by logos34 on 2009-04-20
no, you'd need to use rsync/grsync or sbackup from the linux side.

You want a windows app? (if so you'd need to install fs-driver so xp can access the ext3 linux partition).

---

### Post by frenchn00b on 2009-04-20
> **logos34 said:**
> no, you'd need to use rsync/grsync or sbackup from the linux side.

You want a windows app? (if so you'd need to install fs-driver so xp can access the ext3 linux partition).

but I can access linux, it is the /home/user thourght the samba, like a normal share
it is my O:\mydata into linux

---

### Post by kevdog on 2009-04-20
Unison has a windows gui client (although its primitive).  It also needs to run on the server.  It uses rsync which seems to be the most established replication/mirroring solution.  I wrote a tutorial on how to compile unison from svn or cvs -- its in the tutorials and tips section.  The windows gui build is available from the website.

[http://alan.petitepomme.net/unison/index.html](http://alan.petitepomme.net/unison/index.html)

---

### Post by mips on 2009-04-20
> **frenchn00b said:**
> it is for windows? 
because windows has not single shares,


> **frenchn00b said:**
> and it is included already in microsoft XP?

[http://www.gaztronics.net/rsync.php](http://www.gaztronics.net/rsync.php)
[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)
[http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html](http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html)
[http://www.brentnorris.net/rsyncntdoc.html](http://www.brentnorris.net/rsyncntdoc.html)
[http://www.rsync.net/resources/howto/windows_rsync.html](http://www.rsync.net/resources/howto/windows_rsync.html)

---

### Post by fjf on 2009-04-20
In linux, grsync.
In windows, icemirror.

---

### Post by frenchn00b on 2009-04-20
> **kevdog said:**
> Unison has a windows gui client (although its primitive).  It also needs to run on the server.  It uses rsync which seems to be the most established replication/mirroring solution.  I wrote a tutorial on how to compile unison from svn or cvs -- its in the tutorials and tips section.  The windows gui build is available from the website.

[http://alan.petitepomme.net/unison/index.html](http://alan.petitepomme.net/unison/index.html)

I dont know but it is not working :( 

[http://yellowprotoss.ye.funpic.org/website/errors/Clipboard02-error-union.jpg](http://yellowprotoss.ye.funpic.org/website/errors/Clipboard02-error-union.jpg)

---

### Post by frenchn00b on 2009-04-20
> **fjf said:**
> In linux, grsync.
In windows, icemirror.

icemirror hasnt to delete the files on the SAMBA LINUX box :( 
[http://www.softpedia.com/screenshots/ICE-Mirror_1.png](http://www.softpedia.com/screenshots/ICE-Mirror_1.png)

---

### Post by MaxIBoy on 2009-04-20
> **frenchn00b said:**
> it is for windows? 
because windows has not single shares,
it can access the samba of linuxYou can use Cygwin to duplicate the UNIX API on Windows.

---

### Post by frenchn00b on 2009-05-22
> **frenchn00b said:**
> icemirror hasnt to delete the files on the SAMBA LINUX box :( 
[http://www.softpedia.com/screenshots/ICE-Mirror_1.png](http://www.softpedia.com/screenshots/ICE-Mirror_1.png)

Hi, 
So it is working ice mirror, I did some further testing.
I will adopt it for a while and let you know about it, further progresses.

the procedure is as follows:
[http://img40.imageshack.us/my.php?image=icemirrorprocedure.jpg](http://img40.imageshack.us/my.php?image=icemirrorprocedure.jpg)

the problem is that icemirror does not save the configuratino in ini file :(

[B][I]solved in alternative solution :( 

anyfuther ideas, are welcome[/I][/B]

---

### Post by LookTJ on 2009-05-22
Download and install SyncToy, it's pretty straightforward to use

ALSO: [http://www.mydigitallife.info/2008/01/01/schedule-synctoy-to-run-and-automatically-and-repetitively/](http://www.mydigitallife.info/2008/01/01/schedule-synctoy-to-run-and-automatically-and-repetitively/)

---

### Post by frenchn00b on 2009-05-22
> **Taylor said:**
> Download and install SyncToy, it's pretty straightforward to use

ALSO: [http://www.mydigitallife.info/2008/01/01/schedule-synctoy-to-run-and-automatically-and-repetitively/](http://www.mydigitallife.info/2008/01/01/schedule-synctoy-to-run-and-automatically-and-repetitively/)

it needs the framework microsoft, and wine does not like it :( :(
but not that bad,

Does it do the echo sync via SSH to our linux servers?

---

### Post by frenchn00b on 2009-05-22
> **Taylor said:**
> Download and install SyncToy, it's pretty straightforward to use

ALSO: [http://www.mydigitallife.info/2008/01/01/schedule-synctoy-to-run-and-automatically-and-repetitively/](http://www.mydigitallife.info/2008/01/01/schedule-synctoy-to-run-and-automatically-and-repetitively/)


Program not good :( 
[http://img200.imageshack.us/my.php?image=configsynctoyms.jpg](http://img200.imageshack.us/my.php?image=configsynctoyms.jpg)

==> 
d:\tosave
d:\backup
 
if you delete files, into the d:\backup, after teh sync echo, a new echo sync, will not re-place them into the d:\backup 

damn, i dont know what they think MS programers
:( 

[http://img200.imageshack.us/my.php?image=configsynctoyms.jpg](http://img200.imageshack.us/my.php?image=configsynctoyms.jpg)

---

### Post by frenchn00b on 2009-05-22
synctoy does NOT delete in bakcup the hidden files

and creates jkdflsjkslfdjkflsdjjfskldjklafd.1.exe  like that, when the program is LOST :( 
damn :(

---

### Post by frenchn00b on 2009-05-25
-- removed

---

### Post by dragos240 on 2009-05-25
why not just create a script that automatically mounts your xp partition, and then copies the folder. It would do it on bootup.

---

### Post by frenchn00b on 2009-05-25
> **dragos240 said:**
> why not just create a script that automatically mounts your xp partition, and then copies the folder. It would do it on bootup.

"MASTER XP  ===> LINUX BOX, with delete"

but actually it should rename and delete, changes, on hte linux box. A brutal CP would take too much time :(

---

