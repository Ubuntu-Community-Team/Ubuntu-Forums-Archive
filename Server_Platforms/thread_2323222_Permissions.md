---
title: "Permissions"
date: 2016-05-03
forum: Server Platforms
---

### Post by kambiz2 on 2016-05-03
Hi,
I've read that only root or own user can use chmod. Is this true?
Is there anyway that all the users of the group could change the permisions?
I need to execute chmod from a Delphi program I'm writing, under Windows

Thanks.

---

### Post by gnusci on 2016-05-03
read this

[https://en.wikipedia.org/wiki/Chmod](https://en.wikipedia.org/wiki/Chmod)

and this

[http://www.thegeekstuff.com/2010/06/chmod-command-examples/](http://www.thegeekstuff.com/2010/06/chmod-command-examples/)

---

### Post by kambiz2 on 2016-05-04
Thanks gnusci, I've read both links. Or I miss something because of my poor english, or I don't see the way how a user of the group, not the owner neither root, to use chmod.

---

### Post by darkod on 2016-05-04
I think you are asking for too much... Security is one of the most popular parts of linux, and allowing any user member of a group to change permissions on related files would be a great security risk in my opinion...

It is quite logical only the owner user or root to be able to handle permissions. Even in windows a user of a group that has rights to use some files does not automatically have the right to change their permissions. That's why admins are for...

You can reconsider how you organize your file structure and their permissions, etc... Run scripts as root using cron, or something like that... But not trying for normal users to handle admin stuff.

For example on a samba share you can use the 'create mask' and 'directory mask' parameters so that all files created inside a share will have the same owner. Then you can try to control permissions running your script as that user.

---

