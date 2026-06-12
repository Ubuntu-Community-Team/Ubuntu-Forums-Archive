---
title: "Moving from qpopper to dovecot for pop3"
date: 2013-06-04
forum: Server Platforms
---

### Post by JKyleOKC on 2013-06-04
Having just upgraded from 10.04 to 12.04, I find that my qpopper installation to provide pop3 access for local mail (from other units on my LAN) has been deleted, and qpopper is no longer in the repository. Thus it looks as if I'm compelled to use dovecot.

However I have no idea at all how to configure it, and the man pages only add to the confusion. All I need to do is allow a mail client at 192.169.0.52 to access messages on the local postfix server, but so far every attempt to connect is refused. Can someone provide a simple step-by-step procedure telling what needs changing? I don't use imap, and none of this traffic goes outside my LAN...

EDIT: After several hours of googling I finally got it working, by installing the dovecot-postfix package, commenting out qpopper's entry in inetd.conf, and changing my mail client's configuration to use STARTTLS authentication instead of regular handshaking. I'm not impressed with the available how-tos, though. They were esentially useless, except for the one that mentioned the dovecot-postfix package...

---

