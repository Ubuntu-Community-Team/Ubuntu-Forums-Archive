---
title: "Help Configuring ProFTPd Multiple Users"
date: 2010-09-27
forum: Server Platforms
---

### Post by creamers on 2010-09-27
10.04 Lucid
64 Bit Server Edition With Ubuntu-Desktop

Hi I am have been having massive trouble with proftpd and multiple users since the day I started using it. My problem is I have 3 directorys that need to be accessed.

/Html/www
/Storage
~

I have 2 user accounts to.

User1
User2

All of them need to be able to access there Home Directory and 1,2 need access to /Storage to and User1 needs access to everything including /Html/www

Problem is I can access all the directory's if you Use a separate accounts for each directory. But I would like to be able to let each account access multiple roots without the need for multiple accounts like how real web servers are ran.

My second even bigger problem is if User1 makes a file/folder only User1 can overwrite or upload to that space. User2 can not it can only read it if that.

I have tried using gproftpd admin and fake roots etc. I have tried serveral other ftp software solutions.

What do I need to do to let User1 and User2 do whatever in there directorys and not worry about permissisons.

~Wesley K

---

