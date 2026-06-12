---
title: "How come our SSHD v4.6 doesn't support ChrootDirectory?"
date: 2008-03-11
forum: Server Platforms
---

### Post by Meson on 2008-03-11
According to the latest sshd_config man page, OpenSSH v4.7 includes a ChrootDirectory option.  I can't really tell with which version this became active, but is there a particular reason why it's not included with Ubuntu?

This would be a great benefit.  For me it would mean I don't need vsftpd at all.

---

### Post by faulkes on 2008-03-11
> **Meson said:**
> According to the latest sshd_config man page, OpenSSH v4.7 includes a ChrootDirectory option.  I can't really tell with which version this became active, but is there a particular reason why it's not included with Ubuntu?

This would be a great benefit.  For me it would mean I don't need vsftpd at all.

There is currently an outstanding LP bug on this issue at

[https://bugs.launchpad.net/bugs/24777](https://bugs.launchpad.net/bugs/24777)

The chroot feature will not likely be backported until after Hardy is completed.

Faulkes

---

### Post by netlogic on 2008-03-11
Yea, I know. However, FTPs has some purpose too. Sometimes, you don't want users to interact with the system. You just want them to transfer files. The best option I found so far is create multiple accounts for each users' functions. I usually change the permission in the /usr/bin and add users interactive functions on that. Certain ftp users,  I don't want them to use sftp. Last thing you want is users to compile apps by copy paste codes with vi and run apps that aren't allowed. However, on the production servers, you should never install the compiler. You should always compile in the test machine and make the debs from it. Sometimes, FTP can be useful. On the webservers for developers, it isn't necessary to run FTPs. It is better to go ssh only. Of course, you can also chroot their ssh account and only allowed to run some bin files by copying to their /home/$user folder on a seperate machine with NFS to other machine. Having options are good. :)

---

