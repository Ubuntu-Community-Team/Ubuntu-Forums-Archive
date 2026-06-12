---
title: "vsftpd - require client certificate?"
date: 2007-04-26
forum: Server Platforms
---

### Post by SoundOfPoetTree on 2007-04-26
Hello. My main question is simply (or not so simply): Is there a way to, in vsftpd, require that clients provide the server with a certificate using SSL (openssl)? I have scoured the internet(s) for hours and days on end to no avail. I already have the server's certificate set up, and a secure SSL connection is established when a user connects. The thing is, I need to require client certificates for one main reason:

Basically, I currently run an FTP server on my Windows box that uses GlobalSCAPE's Secure FTP Server. I require clients also provide certificates (in addition to their username/password) as a further security measure to prevent users from giving their login information to friends. Essentially, due to the sensitive data on the server, requiring client certificates allows me to explicitly accept the user's connection and thus preventing them from allowing their buddies to connect to my server.

I want to migrate all my server's functions over to Linux (I'm running Ubuntu Feisty currently) but am having issues with this security measure.

I would be more than open to any other alternatives that provide the same security measures I've discussed; however, I can not restrict connections based on IP addresses, as 99% of my users do not have static IPs, thus making that solution a pain in the butt.

Please... if you know *anything* that might help get me on the right track, tell me.

P.S.: I feel I owe something back to the Ubuntu community, as I have had many problems solved by this unequivocally helpful community. That said, I have been working on a very detailed guide to create such a secure-vsftpd server... I guarantee there are others out there that have run into the same frustrations of hopping from site to site to site while piecing together parts of various guides that don't end up working anyway.

---

### Post by elnormeo on 2008-07-08
Hey guys,
I'm new to this fabulous community forum.
I'm stuck with the same question too. I'd like the users have an certificate to get access to vsftpd. I search for days and days to find out anything. But i'm stuck. My configuration over ssl is working fine and the ftp clients are aber to use account and password to login. But i want to force them to use a certifiacte to login to my vsftpd.
**Question: Therefore i seach and found nothing: Is vsftps capable of having the certificate login technique anyway????**
If its not, it might be the fastest and most secure ftp, but without the ability to use certs, its useless for me. (unfortunately!!)
So, please any hint would be appreciated very much!!
Thanks anyway,
El normeo

---

