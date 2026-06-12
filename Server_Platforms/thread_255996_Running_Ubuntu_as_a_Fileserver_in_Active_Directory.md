---
title: "Running Ubuntu as a Fileserver in Active Directory"
date: 2006-09-12
forum: Server Platforms
---

### Post by OneSeventeen on 2006-09-12
I know this is possible, as there are many tutorials on using Samba 3 to connect to Active Directory 2003, but I was wondering from a Server Admin's perspective how difficult this is to manage.

Meaning, how do I actually set up share folders?  Is there a GUI I can use?

I hate to say it, but I've grown fond of how easy it is to set up network shares in Windows while handling permissions against Active Directory Users and Groups, but I don't like spending $1200 on an Operating System that I don't trust as much as I do Ubuntu.

Any guides on not only setting up the system, but also administering it as well?

---

### Post by fnjordy on 2006-09-13
Have a look at the SWAT web interface for Samba, not very pretty but its functional.

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html)

---

### Post by OneSeventeen on 2006-09-19
thanks, that document doesn't really help me see how to manage user permissions, or even if SWAT manages user permissions (just that it creates the default config file, which I would assume manages permissions, but you never know.)

Either way, I went to the home of that document and found it very helpful.  I don't know why I haven't read it before!  I'm definitely excited to try to set up an Ubuntu Fileserver on our network, since linux is so much easier to manage files on that windows (IMO, since I can have more control over the system.)

---

