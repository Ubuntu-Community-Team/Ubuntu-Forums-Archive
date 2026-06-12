---
title: "When I use SFTP anything I do besides downloading tells me access is denied."
date: 2008-08-17
forum: Server Platforms
---

### Post by Macmee on 2008-08-17
I'm still fairly new at Linux, so please keep this in mind :).

I am running Ubuntu 8.04 server, and used the command
> sudo apt-get install openssh-server
to install the SSH server. I can connect with Putty, that works fine. But when I try to use SFTP, anything I do besides download, (rename, move, delete, CHMOD) gives me this error:
> Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 9

Thanks for any help!

---

### Post by Macmee on 2008-08-18
anyone!?

---

### Post by hrod beraht on 2008-08-18
So are you doing everything through a PuTTY command-line, as opposed to something like WinSCP?

If so, then are you simply logging in like:
```
ssh macmee@server
```
And then getting an error with a command like:
```
mv somefile somewhere
```

My first thought would be are you moving/deleting files outside of your home folder on the server? If so, are you using sudo? Because within your home folder is the only place you have full permissions.

Bob

---

