---
title: "HELP server crash, UBUNTU, LDAP &amp; SAMBA"
date: 2013-07-17
forum: Server Platforms
---

### Post by sampsoncp on 2013-07-17
About 3 months ago I took a job at a company which has a SuSE 9.2 file server running ldap and samba to authenticate XP users and share files with windows machines. I have been endeavoring to figure out the set up for a while with limited success (because of limited time).   Well the worst thing possible happened over the weekend .  THE SERVER CRASHED.  The User files are on a RAID 5 array which is degraded but useable and I have backups using rsync (preserving the ACLS {-aAx}).  I have a backup of the LDAP structure.  On a totally different machine, I'm in the process setting up a 12.04 server.  I set up ldap to match the samba structure that I needed based on the backup ldap “database” and re-populated the ldap database with the backup.  I have a minimalistic samba share for the root directory (/var/raid/samba shared as samba) .  Everything is mounted in the exact same place as the old machine and has the exact same folder structure.  SO I go to mount the file system on my Win7 machine and it allows me to mount but has an “Access is Denied” error.   This seems like a permissions problem but the permissions are the same as before (as far as I can tell) so I'm kind of lost on this (and I'm not a Linux GURU).  Come to think of it  getfacl on the old machine told me the group names that had access to the folders.  That doesn't happen now.  What have I missed that is the connector?  Also which might (or might not) be related is that the old machine allowed login  authentication through ldap and I'm now working to get that back to working.  Any pointers to good instructions would be most appreciated.  If I'm in the wrong forum please let me know.  Thanks for your help in advance.  Charlie

---

### Post by Vegan on 2013-07-17
you are using the wrong distribution, so ask on the SuSE forum

there are manuals for SAMBA, and the other major applications, so use Google and spend some quality time with a cup of coffee

---

### Post by sampsoncp on 2013-07-17
I solved my problem.  What none of the setup help I found on the web seem to think about is that the folder and all those below have to have a 755 permission on the server.  Guess I should have known that but it wasn't something that was thrown in my face until I used the smbclient on my machine to get a "NT_STATUS_BAD_NETWORK_NAME" error and search for it.

---

### Post by sampsoncp on 2013-07-17
I apologize about not being specific.  I am setting up an UBUNTU 12.04 LTS server with LDAP and SAMBA to replace the SuSE 9.2 server.  

OK SO I didn't solve all my problem.

I got my basic share directories (samba and public) to be visible but I can't get to anything below them.  Also I remembered that I set the shares to be  publicly readable.  Can this be a problem with importing the ldap.

This is the config for the shares.

[public]
comment = public directory
path = /var/raid/samba/public
read only = no
public = yes
writable = yes
create mask = 0765
directory mask = 0755

What other config files /command outputs / etc can I supply that will help with this?  

Thanks

Charlie

---

### Post by sampsoncp on 2013-07-17
> **Vegan said:**
> you are using the wrong distribution, so ask on the SuSE forum

there are manuals for SAMBA, and the other major applications, so use Google and spend some quality time with a cup of coffee

Wow guess the 4 days I've been searching GOOGLE and getting things set up mean nothing.  If I'm going to get this type of response from these forums I will just not post.  I hope you don't have a problem with something that you aren't familiar with and get the same response from another forum.

---

### Post by Toz on 2013-07-17
@sampsoncp, please understand that the members of these forums come from all over the world, and that you need to be patient when posting for assistance. In fact, it was only 30 minutes ago that you identified the server as an ubuntu server (prior to that, one would have naturally assumed that you were using opensuse).

I'm not sure if you were able to locate any ubuntu wiki documentation while googling, but these may be helpful:
- [Samba]("https://help.ubuntu.com/community/Samba")
- [Samba and LDAP]("https://help.ubuntu.com/lts/serverguide/samba-ldap.html") 
- [OpenLDAP Server]("https://help.ubuntu.com/community/OpenLDAPServer")

Also, please be considerate and don't bump your thread for at least 24 hours.
Thank you.

---

### Post by SeijiSensei on 2013-07-18
Directories below /var/raid/samba/public also need 755 permissions.  The files within all those directories need to have the read bit set for everyone (644).

Here's a test. Log in to Ubuntu as a user who should have read privileges via Samba.  Can you list all the files and directories you want to share?  Or do you get permission denied errors?

---

