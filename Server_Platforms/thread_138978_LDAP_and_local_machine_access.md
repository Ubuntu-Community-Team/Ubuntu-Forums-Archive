---
title: "LDAP and local machine access"
date: 2006-03-02
forum: Server Platforms
---

### Post by BiggerBadderBen on 2006-03-02
I've set up a small smbldap network using Debian Sarge as the LDAP/Samba PDC.  I have a couple of desktop machines running Ubuntu and have them NFS mount the /home directories from the server to have common login (I played with autofs-ldap but gave up after a few hours of pain).  My problem is that the Ubuntu clients can't access local hardware like CD-ROM or USB thumb drives (syslog shows permission was denied) when logged in as an LDAP user.  Local users have no such problems.  I should mention that otherwise the users have full access (can sudo etc.)  Does anyone have suggestions on how PAM should be configured so automount will work?  Or maybe it's not PAM-related?  My /etc/pam.d/common-* files all are configured as:

sufficient    pam_ldap.so
required     pam_unix.so   <options>

thanks!

---

### Post by gpredrag on 2006-03-04
You may want to check this link.
[http://www.debian-administration.org/articles/308]("http://www.debian-administration.org/articles/308")
Basicaly Debian and Ubuntu controll acces to physical devices trough membership of local groups (audio,video, plugdev, cdrom...).
This link shows solution that basically dynamically grants memebership in those groups to anyone that logs on with gdm  using pam_group. Most of the time that is desirable.
I also saw solution where those groups (audio,video...) were created in LDAP with same gid, but I don't like that.
Really cool solution would be if there would be possible to have group nesting. For instance LDAP group "Desktop" that would dinamically translate to memebership of those local groups.

---

### Post by flip on 2006-04-08
[QUOTE=BiggerBadderBen]I should mention that otherwise the users have full access (can sudo etc.)  Does anyone have suggestions on how PAM should be configured so automount will work?[/QUOTE]

I'm in a similar situation, but haven't managed to get sudo working for my ldap users. I've got the users in the right group but sudo keeps telling me that they're not in sudoers. Did you have to do something specific or did I miss something. I'll be taking on the nfs mount issue soon so hopefully I have more to contribute next time :-)

Any help would be great.

---

