---
title: "HELP: vsFTPd not automatically giving CHMOD 755 to new FTP'ed files?"
date: 2008-04-15
forum: Server Platforms
---

### Post by doctorfilter on 2008-04-15
Hey folks,

I'm having a little trouble with my new Ubuntu Server 7.10 installation.

I have set up  vsFTPd and have my **/home/<user>** symbolically linked with my** /var/www**... no problem.

BUT! Every time I log in with Smart FTP, and FTP some new files... I have to **sudo chmod -R 755 <myfile>**.

Is there a way of automatically chmoding 755 to everything that's uploaded using vsFTPd or Ubuntu itself?

I have searched countless forums searching for the answer to this over the last 3 days and feel it's time to shout.. HEEELLLPPPP!!

:)

Just wanted to add... setting up Ubuntu Server on an old PC under the stairs is one of the most useful things I've done in ages. I'm a contract web-designer who's just getting into using Ubuntu seriously and having set up SVN... I can backup my contract work from anywhere in the world by right clicking my mouse and choosing "Commit". If there's any developers or other digital artists reading this who havn't set up an Ubuntu Server with SVN yet... you're wasting precious time!
**Long live the Linux!**

---

### Post by AlphaWu on 2008-04-16
check your vsftpd.conf and add the line:
local_umask=022

---

### Post by doctorfilter on 2008-04-16
Ok will do. Any explanation of what this actually does before I screw up my computer? :-P

---

### Post by netlogic on 2008-04-16
it is setting the umask to 022.
UMASK: user file creation mode mask
it sets the permission on the newly created files, which is exactly what you asked for.

note: 
local_umask=022 is for your local account

for anonymous 
anon_umask=022
anon_other_write_enable=YES

========
easy way to understand is just minus what you want.

777-755=022

---

### Post by doctorfilter on 2008-04-17
Uncommenting **local_unmask=022** did not work. :(

You say in your NOTE: this is for the local user. So if I log in from another IP addres otehr than my server... does this count as a local user?

---

### Post by doctorfilter on 2008-04-17
ISSUE RESOLVED:

local_umask=022 worked fine after-all.

I did some rather extensive testing with the mask values and realised that SmartFTP or perhaps Linux was saving the old CHMOD values for deleted files.

I was uploading index.html over and over, thinking that on a new upload... it would re-write with the new umask. Not so. I had to change the file name to index2.html before the new settings were being applied.

I am assuming it is probbaly SmartFTP which is being so "clever" by remembering CHMOD values?

Anyway, if anyone else has been having the same problems, I hope this has helped you too.

Thanks for the info AlphaWu, much appreciated. :)

---

