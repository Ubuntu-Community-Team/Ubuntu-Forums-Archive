---
title: "Samba shares and Active Directory"
date: 2008-08-21
forum: Server Platforms
---

### Post by iupetre on 2008-08-21
At my company, all our user authenticate to Active Directory database (Windows 2003).
I'm interested in rebuilding some old servers with Ubuntu running some Samba shares; however, I'm not sure which is the best way to have our users authenticated to the proper shares.
I don't want them to be prompted for credentials, if they have already logged into the domain from their workstations.

I know I will need Samba and Winbind, but I'm not sure how to set them up.  
The best I can do is 
sudo apt-get install samba
sudo apt-get install winbind
I have credentials that can poll and add a computer to Active Directory, and I know what servers are running LDAP.  I just need to know where to put that information.

Then, can I add an Active Directory Group read/write permissions to certain Samba shares.

---

