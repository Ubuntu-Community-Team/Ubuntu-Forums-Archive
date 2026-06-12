---
title: "Tricky FTP config"
date: 2011-02-08
forum: Server Platforms
---

### Post by ofrxnz on 2011-02-08
So, I am looking to implement an FTP server with Isolated Client accounts/directories where a client can only access what’s in their directory.  I also need to provide my internal user’s (content managers) the ability to upload, delete, etc from all of the Client accounts.  

The simple part is creating the secure client accounts.  It’s a matter of changing DIR_MODE in adduser.conf to 700 or 770, creating a user, having the FTP server chroot them to their home directory, revoke/restrict shell/ssh access and maybe even slap on some ACL to prevent botched permissions.

The hard part is figuring out how to give my power users the ability to access all of their folders without thrashing security.  

My first thought was to put all of the “client user-groups” in a parent group and having my internal users inherit group permissions…..but you can’t have groups inside of groups.

My second thought was to put all of the client users in the same group and prey that the FTP chroot is enough to keep them from poking around but then I have the problem of how do my internal users access other user directories if they are chrooted.  Do I create a second server without chroot….do I create some weird nested homedir structure…..

I honestly have no idea how to satisfy both requirements (secure client accounts and privileged user accounts).  

I need my privileged users to authenticate against Active Directory via Likewise open, LDAP, etc and I don’t care how the clients authenticate.  Though, I would prefer to have both file and FTP-server level protection just to make sure no one can see the other client’s data.

Does anyone have any suggestions of experience in this field?  I am open to any solution.

Thanks,

Adam
Ubuntu 10.04 LTS 64-bit server

---

### Post by atworkwithjf on 2011-02-16
Have you considered using sftp?  That's gss enabled and would allow users to use their AD creds if the machine is joined to AD.

---

