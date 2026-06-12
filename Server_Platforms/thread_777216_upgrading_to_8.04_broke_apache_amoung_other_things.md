---
title: "upgrading to 8.04 broke apache amoung other things"
date: 2008-05-01
forum: Server Platforms
---

### Post by jpastore on 2008-05-01
I am having a bit of a problem with the upgrade to 8.04

I've been able to resolve a number of problems like complaints regarding the permissions to: 

.dmrc not being set correctly

sudoers file not owned by the root group 
    [requires rebooting into linux single and chown the file]

apache not allowing me to access projects I'm developing out of my sandbox 
(13)Permission denied: /home/jpastore/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
chmod 775 on /home/jpastore fixed this. found this forum post that lead to the conclusion: [http://gallery.menalto.com/node/68197]("http://gallery.menalto.com/node/68197")


Now if only my wifi would work.

---

### Post by ghostknife on 2008-05-03
What exactly is your question here?

---

