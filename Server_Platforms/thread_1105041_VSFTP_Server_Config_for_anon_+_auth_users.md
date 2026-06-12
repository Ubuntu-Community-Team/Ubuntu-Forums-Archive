---
title: "VSFTP Server Config for anon + auth users"
date: 2009-03-24
forum: Server Platforms
---

### Post by (aptainMorgain on 2009-03-24
UBUNTU 8.10

Hey guy's and gal's.

I've got the VSFTP server running. I can log in using the system users. I can log in using anonymous account.

I can't log in using authenticated user and upload a file to the root directory of the anonymous account.

I would like to do that...

Any sugestions?

-----------------------------------------------------------------
Currently:
anonymous can connect
root dir: /home/ftp/

Set home directory for auth user to same in "Users & Groups" GUI.
-----------------------------------------------------------------

P.S. - I'm very tired - hence the short short descriptions.

---

### Post by Bachstelze on 2009-03-24
You must give the auth user permission to write to /home/ftp. If it is only one user, you can just give it ownership home /home/ftp:

```
sudo chown -R user /home/ftp
```

if it's several users, you must create a new group, add all those users to it, and then give group-ownership of /home/ftp to that group and make it group-writable:

```
sudo chown -R :group /home/ftp
sudo chmod -R 775 /home/ftp
```

---

