---
title: "vsftpd virtual users"
date: 2006-10-11
forum: Server Platforms
---

### Post by devnulljp on 2006-10-11
Looking for some help setting up virtual users on vsftpd
I ran through the basic setup in /usr/share/doc/vsftpd/EXAMPLE/VIRTUAL_USERS but it routed all virtual users to the same directory

I need multiple virtual users with different home directories and different permissions

user1 -> /home/ftp-docs/user1
user2 -> /home/ftp-docs/user2 mount-bind to /home/ftp-docs/user1/user2
user3 -> /home/ftp-docs/user3

user1 has access to everything user2 does but not the other way around
user3 is isolated

When I set up virtual users, they were all dumped into the same directory
I'd like to not have to have real unix accounts for these users for security reasons
Any ideas?

---

### Post by nix4me on 2006-10-11
I never had success getting vsftpd to work with virtual users.  I do have proftpd working very nicely with mysql virtual users.


nix4me

---

### Post by Gabriele Persia on 2007-12-12
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

Regards,
Gabriele

---

