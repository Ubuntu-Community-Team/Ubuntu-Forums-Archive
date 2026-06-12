---
title: "read access control of libapache2-svn"
date: 2012-10-28
forum: Server Platforms
---

### Post by sjerry4u on 2012-10-28
hi,
I have successfully installed libapache2-svn with help of [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion) and its working,

I also have created password passwd users,
It asks password when i try to commit but it doesnt ask password when I checkout...
so basically anyone can checkout and download code from my website which i don't want..

Kindly suggest me the configuration to restrict the reading/checkout of the repo..

my current config:

>  <Location /svn>
     DAV svn
     SVNParentPath /home/svn
     SVNListParentPath On
     AuthType Basic
     AuthName "Subversion Repository"
     AuthUserFile /etc/subversion/passwd
     <LimitExcept GET PROPFIND OPTIONS REPORT>
        Require valid-user
     </LimitExcept>
  </Location>

thank you...

---

