---
title: "Correct way to add more users for sftp?"
date: 2009-02-22
forum: Security
---

### Post by pcit on 2009-02-22
Hi everyone,

I am trying to find the right way to create user accounts for sftp for them to upload files to the server. Also, these files will sit in /var/www/{some folder} for people to download (anonymously).

I have the following questions:
1.) What kind of user account should I create for them?
     i.e. regular linux account with bash shell, or...?

2.) What is the correct directory/file permission for this folder?
     I tried to setup the folder with permission 664, but I was not able to cd to that directory nor read/write/create any file in that directory. I thought permission 664 was "readable and writable" for the user and users who were in the assigned group. When I used the Cyberduck (sftp client for mac), I was not even able to login to the folder...

---

### Post by cdenley on 2009-02-23
664 = owner: rw, group: rw, other: r
775 = owner:rwx, group:rwx, other: rx

For a directory:
r = can list contents
w = can add/remove contents
**x = can access directory**

For a file:
r = can read
w = can modify
x = can execute

For a unix user to be able to browse and add files to a directory, they need full access to that directory (rwx). When you get into more complicated setups like this, you might need ACL's.
[https://help.ubuntu.com/community/HelpOnAccessControlLists](https://help.ubuntu.com/community/HelpOnAccessControlLists)

When giving users any access, it is always best to give them as little access as possible. I would suggest using a restricted shell like scponly.

---

