---
title: "Setting up a secure FTP (with proftp)"
date: 2010-05-10
forum: Server Platforms
---

### Post by FizzBuntu on 2010-05-10
Hi
I'm trying to setup a secure FTP on a Ubuntu server. Here's what I want to do:
- Each user must have its own login
- The content and access rights of the ftp directory may be different according to user and/or group
- Some directories are common to all users, some are specific to one or more users or to a group
- Connection and transfer must be secure (ssh, ssl ?)
- No anonymous or unsecured connections

I've read a bunch of "tutorials" and "how-to" but it only gave parts and bits o the answer.
Obviously there's several way to do that:
- FTPs or SFTP ?
- Virtual server or not ?
- User Authentication method...

and so on

Any help would be appreciated.

---

### Post by Tlingit on 2010-05-10
I Just wanted to add that i have been exhausting research for the past couple hours on. All i need now is a little human help with some questions and a couple more answers.

---

### Post by Iowan on 2010-05-10
I'm not sure which "tutorials" and "how-to's" you've seen - is [this]("http://ubuntuforums.org/showthread.php?t=79588") one of them?

---

### Post by FizzBuntu on 2010-05-11
Yes, I've read this one but it doesn't talk about virtual server and the directory access rights works so that users who don't have access to directories can see the directory (I don't want that).

So it's only parts of the answer.
(I may add that I wasn't able to make it work properly so far wuth this configuration)

---

