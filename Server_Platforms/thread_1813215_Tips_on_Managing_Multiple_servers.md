---
title: "Tips on Managing Multiple servers"
date: 2011-07-27
forum: Server Platforms
---

### Post by harveyd on 2011-07-27
Hi All,

I manage about 15-20 ubuntu servers that are all remote in a data center. 

I use a Mac as my client and I am after some tips and tricks for managing multiple servers. Simple things like keeping .bachrc, .vimrc, .screenrc in sync. Making sure certain tools are installed etc.

I would like to be able to login to a server and have the set up as similar as possible.

Any tips or tricks would be gratefully received.

Regards

Harv

---

### Post by karlson on 2011-07-27
> **harveyd said:**
> Hi All,

I manage about 15-20 ubuntu servers that are all remote in a data center. 

I use a Mac as my client and I am after some tips and tricks for managing multiple servers. Simple things like keeping .bachrc, .vimrc, .screenrc in sync. Making sure certain tools are installed etc.

I would like to be able to login to a server and have the set up as similar as possible.

Any tips or tricks would be gratefully received.

Regards

Harv

Try automounting home directories via NFS.  You will also need to set up LDAP to be able to have the logins the same across the board.

Otherwise you will need to have the home directories published from the machine it was updated on.

---

