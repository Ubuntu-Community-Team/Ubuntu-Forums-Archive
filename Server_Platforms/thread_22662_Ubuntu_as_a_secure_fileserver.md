---
title: "Ubuntu as a secure fileserver"
date: 2005-03-28
forum: Server Platforms
---

### Post by angrylittleman on 2005-03-28
Hello - 
Here is my situation:  I am going to be away from my normal location (my home) this summer, collaborating on a project with some friends.  I would like to have a secure fileserver where we can backup and trade info on.  I understand that SSH is the best way to do this, and an even better approach is to use a chroot-jail for users.  I am pretty new to the server side of stuff, I have a headless box with an ssh server (warty) on it now that I use for moving files around my LAN, however, I am afraid to open it up to the net.  Here are some questions that I can't find an answer to:

1.  What is the best FS type?  Ext2/3?  Reiser?  I am concerned not so much with performance as with recoverability.

2.  Is Ubuntu best suited for this with the lack of root?  Or is debian better?  I am very concerned with people helping themselves to my files (confidential files for clients)

3.  SSH seems to be the way to go with Gftp for linux and some other clients for windows users.  Am I correct to assume that SSH is the safest?

4.  Is it possible to leave this box exposed while still safely running samba so that I can improve my LAN connectivity and get rid of the associated overhead with SSH (to make moving large files faster)  

5.  Will this ([http://www.fuschlberger.net/programs/ssh-scp-chroot-jail/](http://www.fuschlberger.net/programs/ssh-scp-chroot-jail/)) work for Ubuntu to provide me with chroot-jails?  

6.  Should I use portforwarding on my router (WRT54G) or use the DMZ to place this box on the net?  I use the WRT54G as my hardware firewall with all of my other computers running software firewalls

I am sorry for the length of this post, I have never had formal LAN training and I don't want to expose confidential information on the internet.  I would like to be able to have all of the transactions on the internet side be encrypted with all of the LAN side run under samba.  Thanks for your time in advance.

ALM

---

### Post by alastair on 2005-03-29
1. Filesystem - for recovering from errors, choose a journalling FS. Ext3 is fine (and default).
2. I see no reason why Ubuntu would not be ok for this.
3. SSH is fine. You might also want to consider sftp (ssh ftp), vsftp or something like OpenVPN (SSL based).
4. Samba over OpenVPN might be OK. Make an informed decision ([www.openvpn.net](www.openvpn.net))
5. No idea (I didn't look). Vsftp does chroot jail as well.
6. Portforwarding should be fine - secure the forwarded to machine. And don't be hung up about h/w vs s/w firewalling (the WRT is essentially s/w as well - s/w firewalls are fine)

---

### Post by garyng on 2005-03-29
apache2 + SSL + WebDAV + UserDir 

It is simple, flexible and secure(all modern OS has WebDav support, needed only for uploading). The only thing against it is performance.

---

### Post by yanik on 2005-03-30
ssh is secure as long as you use it along with the public/private keys.  If not it's as secure as telnet.

---

### Post by angrylittleman on 2005-03-31
Does anyone know what bit encyrption RSA for SSH uses?  Is it 128 bit?   Or do I need to do some more research to figure out what I am talking about?  thanks so much for everyones help.

alm

---

### Post by alastair on 2005-03-31
[QUOTE=yanik]ssh is secure as long as you use it along with the public/private keys.  If not it's as secure as telnet.[/QUOTE]

Untrue.

SSH is much more secure than telnet, even when not using key based auth methods e.g. host or password based. Passwords are never sent cleartext.

See : [http://www.openbsd.org/cgi-bin/man.cgi?query=ssh](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh)

---

### Post by nocturn on 2005-04-05
As an additional precaution, you could encrypt your files with GnuPG (OpenPGP) before tranfering them from your remote location, that way they will be useless to anyone who breaks in (although they can still destroy them).

---

