---
title: "Question on LDAP config / behavior"
date: 2008-09-25
forum: Server Platforms
---

### Post by rkleemann on 2008-09-25
Hi,

I've installed LDAP server in Ubuntu Server 8.0.4.

I have it setup and working, I can authenticate ssh, imap, etc using ldap.

I installed phpLDAPadmin in order to manage the LDAP contents.

I have a couple of questions:

1. After configuring the pam stuff, whenever I'm required to enter password for sudo, it asks me twice. Almost as if it goes through pam_unix and pam_ldap libraries, even though my user only exists in the unix system, not ldap. Why is this happening (entering password twice)?

2. I know I can manage the LDAP data via phpldapadmin, but obviously that's only for my use as the sysadmin. How can users actually change their own data, like for example changing passwords? What applications can plug-in and actually perform those kinds of changes? Is there a web console for changing user data?

Thanks
Ricardo

---

### Post by gpredrag on 2008-09-25
1. That should not be the case IF you have configured pam correctly. Post your /etc/pam.d/common-* and /etc/pamd.d/sudo
2. If you have linux users and have configured libldap-pam and common-password correctly, regular password change would change ldap password. If you have samba/ldap users try configuring smbldap-tools and smb.conf, and regular windows password change would change ldap password. If none of the above apply..., i.e. for instance those are users of some application, there is no straigt forward solution. For example squirrelmail has plugin for something like that, may not be the case for some other application.

---

### Post by rkleemann on 2008-09-25
> **gpredrag said:**
> 1. That should not be the case IF you have configured pam correctly. Post your /etc/pam.d/common-* and /etc/pamd.d/sudo
2. If you have linux users and have configured libldap-pam and common-password correctly, regular password change would change ldap password. If you have samba/ldap users try configuring smbldap-tools and smb.conf, and regular windows password change would change ldap password. If none of the above apply..., i.e. for instance those are users of some application, there is no straigt forward solution. For example squirrelmail has plugin for something like that, may not be the case for some other application.

Thanks.

I think I figured it out, I had 2 lines in common-auth, one required and one requisite... I commented out the requisite and now I no longer get the "double authentication"

---

