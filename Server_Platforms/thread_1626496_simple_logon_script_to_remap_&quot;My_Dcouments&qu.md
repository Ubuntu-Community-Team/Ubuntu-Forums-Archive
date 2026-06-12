---
title: "simple logon script to remap &quot;My Dcouments&quot;"
date: 2010-11-20
forum: Server Platforms
---

### Post by BarryDocks on 2010-11-20
I have a samba PDC set up, roaming profiles are not needed as the user accounts are on a per-machine basis (ie the machine on reception logs on as the "user" reception for all the operators, no personal data is stored but I would like to redirect the local My Documents folder of the XP clients to the user /home folder on the samba server.  

I thought about making the user /home share browsable and having a simple logon script to redirect the My Documents folder to it.  

Any suggestions would be very useful, thanks.

---

### Post by dtfinch on 2010-11-20
You can also use variable substitutions (like path=/home/%u or path=%H) in smb.conf to make the share's path always point to the home folder of the user logging into it.
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#id2532525](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#id2532525)

---

### Post by BarryDocks on 2010-11-24
> **dtfinch said:**
> You can also use variable substitutions (like path=/home/%u or path=%H) in smb.conf to make the share's path always point to the home folder of the user logging into it.
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#id2532525](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#id2532525)
Thanks for the reply.  I think this will just enable roaming profile that I am trying to avoid.  If the [homes] share is set to browsable then the user can have access to their home folder through network places in XP.  I just want a simple script to redirect My Documents to the home folder on the path //server/username

---

