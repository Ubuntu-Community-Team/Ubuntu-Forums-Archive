---
title: "Ubuntu AD auth - changing password at logon"
date: 2010-11-17
forum: Server Platforms
---

### Post by shikomizue on 2010-11-17
Hi everyone,

I have succesfully set up authentication manually in Ubuntu so users can log on with Windows Active Directory accounts and have their network drives mapped automatically using pam_mount.

I have one more issue that I need some help with.

Please note due to the setup I can't make any changes to the Windows 2k3 server.

If a user wants their password reset I can change it to a generic password. When they next log on to a Windows computer with the generic password it will automatically ask them to change it to something else.

Is there anyway to get this to work with Ubuntu 10.10? At the moment when logging onto Ubuntu with an account that is in this state the message Please change your password appears, it then proceds to log on without prompting to change the password and natually it won't map the drives etc.

Can anyone point me in the right direction as to what I should be looking at?

---

### Post by shikomizue on 2010-11-22
Bump anyone have any ideas on this?

---

### Post by scorp123 on 2010-11-23
Likewise Open. It's in the repos.

Guide here:
[http://www.likewise.com/products/likewise_open/](http://www.likewise.com/products/likewise_open/)

---

