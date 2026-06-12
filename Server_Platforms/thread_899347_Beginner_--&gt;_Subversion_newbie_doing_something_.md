---
title: "Beginner --&gt; Subversion newbie doing something wrong"
date: 2008-08-24
forum: Server Platforms
---

### Post by supergrover1981 on 2008-08-24
Hi Gang,

I'm just trying to come to grips with Subversion 1.4.6 on Hardy. Everything seems to work fine, except "commit" doesn't seem to have any effect. Below are details of the process I'm using. Any help appreciated.


#1.) cd /home/supergrover
#2.) sudo svnadmin create svn
#3.) sudo svn mkdir file:///home/supergrover/svn/subtest
#4.) cd /home/supergrover/subtest (this directory has a single index.php file, with nothing but "echo 'Pre changes'" inside)
#5.) sudo svn import file:///home/supergrover/svn/subtest
#6.) sudo svn checkout file:///home/supergrover/svn
#7.) (I make changes to /home/supergrover/subtest/svn/subtest/index.php)
#8.) svn commit

I get a 'log' screen, enter log details, then return to the original file at /home/supergrover/subtest/index.php - unfortunately, the changes haven't been made.

Any suggestions deeply appreciated.

 - SuperGrover

---

### Post by lpanebr on 2008-09-17
HEllo,

I guess you just need to add a sudo there just like you did on the other lines:

[INDENT]sudo commit[/INDENT]

[]s

---

