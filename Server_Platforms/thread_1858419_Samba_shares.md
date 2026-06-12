---
title: "Samba shares"
date: 2011-10-12
forum: Server Platforms
---

### Post by albertramsbottom on 2011-10-12
Hi

I have Ubuntu server 10.4 LTS and have successfully installed and configured Samba

This currently connects to my home directory on Ubuntu by using [homes] in the config file

What I really need is to be able to share a directory in the root called newweb

Is this possible?

Many thanks for any help

---

### Post by DavidBeijer on 2011-10-12
That is most definately possible! 


If you look for instance [here]("http://www.ghacks.net/2009/09/04/set-up-your-new-ubuntu-server-as-a-samba-server/"), there is a howto of modified shares. Don't forget to add a user and to restart samba after having changed the config file!

---

