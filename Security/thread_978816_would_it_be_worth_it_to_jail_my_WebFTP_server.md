---
title: "would it be worth it to jail my Web/FTP server"
date: 2008-11-11
forum: Security
---

### Post by randomstuff on 2008-11-11
I have recently aquired/rented a dedicated server from a hosting company and I am now wondering whether it would be worth it to jail the different services.

The primary purpose of the server is to host my personal (public) homepage as well as provide me with means to access private/personal data from basically anywhere without having to take my computer/harddrives with me (Examples are source code (subversion server), photos, and other documents.). The server will also be used to host e.g. sites for family members and give them some FTP space.

Now I am wondering, do you think I can gain much security by jailing my servers? The web/ftp servers would likely be placed in the same jail for convenience. But if that jail is compromised, all private data is compromised as well, unless I create two different jails and make a strict seperation between private and public data. Is there an easier alternative, or is it maybe just not worth it?

What would you do, considering that I am relatively paranoid about my private data?

Perhaps the best choice is not to put it there in the first place, but I am looking for a bit of convenience here. Also, the server will function as backup of my personal data.

How much of a hazzle is it to route http/ftp/email requests to different jails?

I do not expect a perfect solution, but I wish to hear your opinions on this. Thank you for your time.

---

### Post by HermanAB on 2008-11-11
IMHO jailing increases maintenance costs by a huge margin and doesn't improve security at all, so it is quite useless.

---

### Post by randomstuff on 2008-11-11
after thinking about this a lot, I have come to the same conclusion. I don't want to bother with creating jails.

---

