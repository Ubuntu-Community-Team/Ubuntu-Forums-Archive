---
title: "Authenticate samba share against LDAP (eDirectory)"
date: 2010-05-05
forum: Server Platforms
---

### Post by markjohnson on 2010-05-05
Hi guys,
I've got an Ubuntu 9.10 server on our network.
I need to set up a Samba share on the Ubuntu server which only some users have access to, so they can access it from Windows boxes. The Windows boxes currently authenticate using Novell eDirectory authentication.

I've succeeded in setting up the share, and allowing guest access to read/write to the share. However, this means that currently anyone who knows the address of the share can access it.

What I need to know is how to get Samba to authenticate from the eDirectory server, and restrict access to one group of users in the tree. Do I need to set up LDAP authentication on the server as a whole, or just on Samba itself? How do I implement it?

---

