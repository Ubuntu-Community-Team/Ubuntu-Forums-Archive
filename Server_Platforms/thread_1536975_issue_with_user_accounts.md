---
title: "issue with user accounts"
date: 2010-07-22
forum: Server Platforms
---

### Post by associates on 2010-07-22
Hi,

I was wondering if I could get some help with user account type. I have accidentally changed the user account type from custom to administrator. Now I am no longer able to add new user accounts. The user account I am using to add new users is the account I created when installing the Ubuntu Server 10.04. I suspect I have stuffed up my root account. 

I wonder if there are any way of changing the account type back to custom as it was before.

Any help would be greatly appreciated.

Thank you in advance

---

### Post by ruffEdgz on 2010-07-23
I don't understand what the problem is but here is some words of advise:

- If you need some admin rights at times, make sure you setup sudo for yourself ([https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers))
- Never place yourself in the group 'root'
- Try to understand the files /etc/passwd, /etc/group and /etc/sudoers to figure out any user related problems
  -- GROUPS [http://manpages.ubuntu.com/manpages/lucid/man5/group.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/group.5.html)
  -- PASSWD [http://manpages.ubuntu.com/manpages/lucid/man5/passwd.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/passwd.5.html)
  -- SUDOERS [http://manpages.ubuntu.com/manpages/lucid/man5/sudoers.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/sudoers.5.html)

If you can give us a better understanding of what commands you ran to get away from this 'custom' to 'admin' type, that would be very helpful.

Thanks!

---

