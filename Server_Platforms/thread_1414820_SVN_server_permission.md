---
title: "SVN server permission"
date: 2010-02-24
forum: Server Platforms
---

### Post by any.linux12 on 2010-02-24
Hi all!

In my company we have a svn that we use every day. We have now over 100 project under svn's revision but today I have a different situation.

Normally when I open a project I have a group for that specif project, like, projectXX1 is the project name and also the group for that project and then I just add users to the group. They can all read and write the problem is that now I want to give write permission to only 4 users and read to all 7 users in the project.

How can I set write permissions to some users and read to all?

Thank you!

---

### Post by kiranmurari on 2010-02-24
Hi,

You can use svnserve (a small dedicated SVN server), which has per user ACL; for setting the read/write permissions, authentication and authorization. [http://svnbook.red-bean.com/en/1.2/svn.serverconfig.svnserve.html](http://svnbook.red-bean.com/en/1.2/svn.serverconfig.svnserve.html)
[URL="http://svnbook.red-bean.com/en/1.2/svn.serverconfig.svnserve.html"]
[/URL]In addition, you can use apache to access the subversion over the network. There are modules available that enable repository access with user authentication and authorization. Using the authz_svn module for apache you can easily setup per-directory access control. Please see: [http://svnbook.red-bean.com/en/1.1/ch06s04.html#svn-ch-6-sect-4.4.2](http://svnbook.red-bean.com/en/1.1/ch06s04.html#svn-ch-6-sect-4.4.2).
   
Hope this helps.

---

### Post by any.linux12 on 2010-02-24
thank you...I will try that

---

