---
title: "Question about Samba(is this a bug?)"
date: 2008-04-29
forum: Server Platforms
---

### Post by _sAm_ on 2008-04-29
I have a «home server» witch use Samba to share some folders. Under Ubuntu 7.10 I had 
*security = user*
 and the users needed to log in with username and password to gain access. When security sat to user it didn't matter what settings I gave for the different shares. Meaning; if I had:
[I]available = yes 
browsable = yes 
public = yes 
writable = no[/I]
the user still had to enter username and password. 

I have now upgraded to Ubuntu 8.04(fresh install), and have still *security = user * under Global settings in /etc/samba/smb.conf
Even though, I can open the shares on a Windows pc without entering username or password. I have not changed anything from security. 


Is this a bug or have they changed how Samba works. 

Thanks for any answers(and sorry for my English).

---

### Post by phos4us on 2008-04-29
Have the windows clients been changed in anyway?

As far as I know, if the username and password used to log into windows matches those on the Samba Server, windows should automatically log the user in. If this fails the user is prompted to log in.

Not sure if that will help in anyway.

Regards
Andy

---

### Post by Brazen on 2008-04-29
Yeah, if the user name and passwords are the same on the Samba server and the Windows clients, then it should NOT ask for a password.  If it did under 7.10, I would say that was a bug in 7.10.

---

### Post by _sAm_ on 2008-04-29
Have done no changes on the clients at all(3 Vista pc). The username/password are also not the same on the server and the Windows (vista) pces. 

Locking at the *default* samba configuration file in Ubuntu 7.10(samba 3.0.26a) and the one in Ubuntu 8.04(Samba 3.0.28a), some differences I can see are this(under Authentication):

   unix password sync = yes
In samba 3.0.26a it was:
;unix password sync = no 

pam password change = yes
In  samba 3.0.26a it was:
pam password change = no

And this is new:
# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

---

### Post by Brazen on 2008-04-29
> **_sAm_ said:**
> 

And this is new:
# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

hmmm, that map to guest looks suspicious.  Even if you don't have that in your current config on the new server, it could be a new default.  You may need to look for an option to disable guest connections.

You can read about all the configuration options with "man smb.conf"

---

### Post by Brazen on 2008-04-29
Try adding "guest ok = no" to your smb.conf.  It can go in a share definition or it should be able to go under global to apply to all shares (unless a share overrides it).

---

### Post by _sAm_ on 2008-05-07
I did try guest ok = no under Global, but can still open the share without password/username.

---

