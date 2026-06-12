---
title: "How to setup Hylafax with PAM authentication for Domain / LDAP users?"
date: 2017-11-22
forum: Server Platforms
---

### Post by ZippyDan on 2017-11-22
**[S]Former post title: Issue with Hylaxfax login on Ubuntu with LDAP users[/S]**

Not really sure if this is an Ubuntu, Hylafax, or YajHFC problem, but since I'm not sure I'm posting here:

Hylafax version : 6.0.6-5
Ubuntu version : 14.04.01 LTS
YajHFC version : 0.6.1

Ignore all below this line and read my first reply:

[HR][/HR]

[s]Everything has been working well for years with this install.

My Ubuntu server is setup as part of my Windows domain, and I know that it is working well because from the server terminal I can su domain.user and it will ask for my domain.user password, and it won't let me switch users unless I input the correct password.

On the Ubuntu server I have done sudo faxadduser domain.user and this works fine (this is the Hylafax command to add an Ubuntu user as an accepted user of the Hylafax server).

For years I have had each of my users setup in YajHFC to authenticate with the Ubuntu Hylafax server using their domain username and password and it works fine.

For example, domain.user1, domain.user2, and domain.user3 have all been faxadduser'd to the Hylafax server.  I can login to the server using YajHFC as all three users, but if I try to login as domain.user4 then my authentication is rejected, because I didn't use the faxadduser command for that user.

What I have recently discovered is that, even though the username part of the authentication is working fine from YajHFC, the password is completely irrelevant.  I can't login to Hylafax if the user hasn't been faxadduser'd, but I can put any password for domain.user1 and YajHFC will authenticate successfully with the Hylafax server.

Any ideas why this might be?[/s]

---

### Post by ZippyDan on 2017-11-22
So it seems my problem is rather "simple" - even though my server is connected to the domain, and even though Hylafax is using domain users, Hylafax is not setup to use PAM authentication.  The *faxadduser* step is not actually adding the domain user to Hylafax, but simply creating an entry for *domain.user* in the Hylafax config files.  Since I didn't define a password (-p) with the *faxadduser* command, then it accepts any password (null password).

So the question now becomes:

[SIZE=5]**How to setup Hylafax with PAM authentication for domain users?**[/SIZE]

---

### Post by wildmanne39 on 2017-11-22
*Thread moved to **Server Platforms for a more appropriate fit**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

