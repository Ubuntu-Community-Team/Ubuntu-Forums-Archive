---
title: "WebDav, SMB Folder Permissions"
date: 2012-09-20
forum: Server Platforms
---

### Post by hyunkseo on 2012-09-20
Hey guys,

So I've setup an SMB + Webdav fileshare on a small box.

So I'm having some problems...
Before I go into any specifics:
SMB File share works fine.
Meaning I can read/write via SMB Locally, and from WebDav in Internet.
The SMB login is 'user1'. Let's say it's also in a group called 'group1'

On WebDav however, when I log in and create a folder called 'whatever'
'whatever' is assigned to www-data:www-data (user:group).
I assigned 'user1' to www-data on top of 'group1' and I added www-data user to 'group1' group...
However, whenever Webdav creates a folder it's locked to www-data and I can't access it LOCALLY under 'user1' (although if I connect through SMB from a different computer and login as 'user1') I can edit the files and what not...

I have no idea if this makes sense to you guys..
but put it simply, I am asking:

IS there a way to assign WebDav in Apache2 to a different user + group than www-data?
OR 
I believe tehre are other ways to solve this problem which is having umask to 0002 / 002. (I don't know how to do that, and I tried to put 'umask 002' in different apache conf files but didn't work)

I am on Ubuntu 10.10.
Apache2 version is 2.2.20

---

### Post by redmk2 on 2012-09-21
> **hyunkseo said:**
> Hey guys,

So I've setup an SMB + Webdav fileshare on a small box.

So I'm having some problems...
Before I go into any specifics:
SMB File share works fine.
Meaning I can read/write via SMB Locally, and from WebDav in Internet.
The SMB login is 'user1'. Let's say it's also in a group called 'group1'

On WebDav however, when I log in and create a folder called 'whatever'
'whatever' is assigned to www-data:www-data (user:group).
I assigned 'user1' to www-data on top of 'group1' and I added www-data user to 'group1' group...
However, whenever Webdav creates a folder it's locked to www-data and I can't access it LOCALLY under 'user1' (although if I connect through SMB from a different computer and login as 'user1') I can edit the files and what not...

I have no idea if this makes sense to you guys..
but put it simply, I am asking:

IS there a way to assign WebDav in Apache2 to a different user + group than www-data?
OR 
I believe tehre are other ways to solve this problem which is having umask to 0002 / 002. (I don't know how to do that, and I tried to put 'umask 002' in different apache conf files but didn't work)

I am on Ubuntu 10.10.
Apache2 version is 2.2.20

This might help -- [[COLOR="Blue"]_http://hexeract.wordpress.com/2011/02/25/configure-a-webdav-enabled-webserver-for-multiple-user-folders-and-one-shared-folder/_[/COLOR]]("http://hexeract.wordpress.com/2011/02/25/configure-a-webdav-enabled-webserver-for-multiple-user-folders-and-one-shared-folder/")

---

