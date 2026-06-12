---
title: "Ubuntu to AD (Single Sign On)"
date: 2006-09-29
forum: Server Platforms
---

### Post by camshere on 2006-09-29
Hi,

I'm looking to get my Ubuntu boxes to a point where single sign-on is possible from my windows boxes and all user authentication takes place via a combination of ldap and kerberos. I would like to do this without using Samba's winbind. 

At the moment I have my ubuntu boxes authenticating to a 2003 AD box using ldap simple bind for user attributes and the 2003 KDC for password authentication. So I can log onto the unbuntu box using my AD credentials and can perform a kinit on my user to retrieve a TGT from the KDC but I'm having some issues getting the rest of the shooting match together. 

I'm looking firstly, to have the pam.d setup configured so that su and ssh etc automatically retrieve TGTs from the KDC when logging in or switching users (needs to be done manually with kinit at the moment)

Then I need to configure SASL/GSSAPI and the ssh client/server to allow authentication via the kerberos credentials - I've installed the ssh_krb5 package and enable the kerberos options, and i'm using the vintella patched version of putty from my windows box - but it still complains about issues with the service_principal in kerberos. I'm assuming this is because Vintella putty leverages GSSAPI to pass credentials, and i haven't figure out how to configure it yet. 

Can anyone give me a run down on these issues? I've read plenty on the net and some are semi-complete but usually don't deal with single sign-on, either that or they just suggest windbind. I'd like to get it running and create some documentation as i think easy ubuntu config for AD integration could be a real selling point.

Cheers 

Cam Marshall
Perth WA

---

### Post by camshere on 2006-10-01
50 + views and no info on this. Surely someone has looked at this sort of thing before? I'm still not having much luck...

---

### Post by munwin on 2006-10-03
This might help.

[http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba+active]("http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba+active")

---

### Post by merkur2k on 2006-10-03
why not winbind? from what I can tell, it was made specifically to do this exact thing.

---

### Post by camshere on 2006-10-05
Mainly because i have MS SFU installed on my AD domain so i don't need the UID mapping abilities of Winbind and its just another thing to be hassled with - it also still doesn't address my issues with single sign on. Winbind allows authenticaion and interacts with kerberos, but simply installing winbind wont fix all my probelms.

Really if you have MS SFU and AD you shouldn't need winbind as far as i know.

---

