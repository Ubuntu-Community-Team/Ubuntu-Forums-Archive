---
title: "FTP-users and FTP question"
date: 2009-02-07
forum: Server Platforms
---

### Post by torque154 on 2009-02-07
I just installed ubuntu server 8.04 x86 and I can't seem to figure out how to add users to allow them to access FTP. 

I see no group in the /etc/group file and I don't see any settings in the /etc/vsftpd.conf


also is there a way to have everybody's dump file (XP users via IE) to be in /home/ftp if so, then how would you do that?

thanks.

---

### Post by Poleh on 2009-02-07
try this link, it's a pretty comprehensive how-to for vsftpd

[http://ubuntuforums.org/showthread.php?t=518293&highlight=disable+ssh+login](http://ubuntuforums.org/showthread.php?t=518293&highlight=disable+ssh+login)

What do you mean "dump file" ?

---

### Post by torque154 on 2009-02-08
> **Poleh said:**
> try this link, it's a pretty comprehensive how-to for vsftpd

[http://ubuntuforums.org/showthread.php?t=518293&highlight=disable+ssh+login](http://ubuntuforums.org/showthread.php?t=518293&highlight=disable+ssh+login)

What do you mean "dump file" ?

that guide was a lot better than the ones I found and understand how it works a little better on linux.  let me restate my problem.  ok, I turned off anonimous users off and turned local users on.  the account you make from the start allows me to access the FTP. when I create a new user, I set him as a member of admin and he is still not able to log in via FTP.  I tried a few other groups but can't find one that works. I still get the same error message 530. 

what I mean by a dump file is a community place where people can dump files in one place.  I want that to be the default location.  would I set there homedir to like /home/ftp or what?

---

