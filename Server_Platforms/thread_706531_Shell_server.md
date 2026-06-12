---
title: "Shell server"
date: 2008-02-24
forum: Server Platforms
---

### Post by evilfootware on 2008-02-24
Hi folks,

I am not sure if this is the right to ask, I do apologise if not.  My friend has asked me to help him setup a shell server, where users have SSH access to the server so they can run their eggdrop/bnc’s and connect to a irc server.

We plan to user ubunto’s server edition as I use ubuntu on my laptop, so I know a little about it. We plan to have a couple of user account packages which the basic one gives the following:- 50mb HDD space, 2 BG processes, SSH access, compiler access, crontab access, bitchx access, vhosts and custom vhost/dedicated IP,  and screen access.
I have a couple of questions, which I hope someone would be kind enough to help me with. 

1). How can we limit the number of BG processes a user has access to?
2). Add a custom vhost/dedicated IP to a users account?
3). Is there a web based utility to make the administration easy?
4). To make the box as secure as possible.

Thankyou in advance.

EFW

---

### Post by k_grdn on 2008-02-24
Hi,

1) PAM /etc/security/limits.conf
2) Use apache2 named virtual hosting (one ip multiple sites)
3) Being an admin takes practice the shell is your friend!
4) [http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/) ( a good start)

Regards,

k_grdn

---

