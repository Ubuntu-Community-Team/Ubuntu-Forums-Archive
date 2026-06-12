---
title: "Multiple connections to SMB server"
date: 2010-05-25
forum: Server Platforms
---

### Post by smc18 on 2010-05-25
I'm curious how I can use a Windows client with two separate accounts to connect, at the same time, to a SMB server hosting two shares.  (Provided permissions and accounts are all in order) 

Scenario:

User1 is always logged onto a Windows client mapped to a Public share on a Linux SMB server.

I need a way to keep User1 connected to the Public share and then when needed, allow User1 to provide User2's credentials to connect to a Restricted share.

The only way I've been able to do this is to disconnect from the Public Share then reconnect to the Restricted share using User2's credentials.  (This is the issue because I need to keep User1 connected to the Public share).

Is this a limitation of SMB? Or am I missing a configuration?  Please point me in the right direction :) :)

---

### Post by capscrew on 2010-05-25
> **smc18 said:**
> I'm curious how I can use a Windows client with two separate accounts to connect, at the same time, to a SMB server hosting two shares.  (Provided permissions and accounts are all in order) 

Scenario:

User1 is always logged onto a Windows client mapped to a Public share on a Linux SMB server.

I need a way to keep User1 connected to the Public share and then when needed, allow User1 to provide User2's credentials to connect to a Restricted share.

The only way I've been able to do this is to disconnect from the Public Share then reconnect to the Restricted share using User2's credentials.  (This is the issue because I need to keep User1 connected to the Public share).

If you have the restricted share configured to use "valid user" then it should always ask for a password when that share is accessed.  See [**_here _**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")for configuration of the smb.conf file.

---

### Post by smc18 on 2010-05-25
When I try to login with User2 to the Restricted share (while logged in as User1 and connected as User1 to the Public share) I get the error:

"Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed.  Disconnect all previous connections to the server or shared resource and try again..."

---

### Post by smc18 on 2010-05-25
And my smb.conf section for the Restriced share includes:

> valid users = @restricted

and User2 is in the restricted group.

Permissions are set right; I'm just wondering if there is a workaround to have two users on the same machine connected to two different shares on a single server.

---

### Post by capscrew on 2010-05-26
> **smc18 said:**
> And my smb.conf section for the Restriced share includes:



and User2 is in the restricted group.

Permissions are set right; I'm just wondering if there is a workaround to have two users on the same machine connected to two different shares on a single server.

You can be two (2) users at the same time.

---

### Post by clrg on 2010-05-26
Yes, Samba allows that, but not Windows. As far as I know, logging in as two different users on a domain is not possible, maybe this restriction also applies to CIFS.

Souns like a client problem to me.

---

