---
title: "sharing samba users"
date: 2021-01-13
forum: Server Platforms
---

### Post by espressobeanmachine on 2021-01-13
How can I assign multiple users to a samba share? So let's say i have a share /var/www/stuff that I need to have ownership to www-data user but also to allow certain samba users to have write access as well. So let's say I have samba users, Bill, Ben, Jill, Lily, to /var/www/stuff I need to have www-data to have ownership of it but also to have Bill and Jill to be able to access it as well. Can this be done? If so, how?

---

### Post by SeijiSensei on 2021-01-13
[https://www.oreilly.com/openbook/samba/book/ch06_01.html](https://www.oreilly.com/openbook/samba/book/ch06_01.html)

One trick I've used in the past is to run Samba with the "force user" and "force group" options. This tells Samba to use a specific user or group for all file transactions at the operating system level regardless of the identities of the logged-in users. I used this for a company which wanted to limit its accounting system to a specific group of users. In this case we didn't care which user wrote a specific file to the system (the software handled that) and wanted to insure all of them could access every file.

---

### Post by rsteinmetz70112 on 2021-01-13
Create a group, make sure all users are in it then make sure you force group permissions.
There are probably a bunch of ways to accomplish this depending on your needs.

---

### Post by LHammonds on 2021-01-13
I would utilize groups.  Users can be in multiple groups.  You can have "grp_users" assigned to the share for full read/write capability which allows all users to connect to the share and then limit permissions at the file/folder level.  Here is a very simplified overview.

Example of Group (users):
```
grp_users (jon, joe, mary, jane)
grp_providers (jon, joe, jane)
grp_accounting (mary)
grp_nurse (joe, jane)
grp_doc (jon)
```

Folder structure (owner of folder):
```
share (grp_users)
 |--> providers (grp_providers)
 |--> accouting (grp_accounting)
 |--> users (grp_users)
     |--> jon (jon)
     |--> joe (joe)
     |--> mary (mary)
     |--> jane (jane)
```

---

