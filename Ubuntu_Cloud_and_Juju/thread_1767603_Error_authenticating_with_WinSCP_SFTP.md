---
title: "Error authenticating with WinSCP SFTP"
date: 2011-05-25
forum: Ubuntu Cloud and Juju
---

### Post by kevinsteger on 2011-05-25
My instance is ami-1aad5273

I'm trying to connect to the machine via WinSCP using root, something I have successfully done with a few other AMI's.

```
The error I get is: Received Too Large (1349281121 B) SFTP packet.  Max supported packet size is 1024000 B.  The error is typically caused by message printed from startup script (like .profile).  The message may start with ""Plea"".
```In a thread on AWS someone suggested that the /etc/motd was the problem.  I deleted it.  I'm not sure if that worked because when I use Putty I still get the message.

Can anybody give me tips on how to disable whatever login messages are automatically being generated so I can use WinSCP?

Thanks!

---

### Post by kim0 on 2011-05-26
I bet that message you're getting is "Please login as the Ubuntu user" :) you should sftp as the ubuntu user, not as root. Try that and let me know

---

### Post by kevinsteger on 2011-05-26
Kim0 that's not the problem I don't think.  On other boxes I am able to do this with my WinSCP configuration login of "root".  How is that possible?  I'm thinking someone set a password for root on those other machines or changed some other authentication setting to allow this?

---

### Post by kevinsteger on 2011-05-26
SOLVED

WinSCP does allow you to become root while still logging in with the 'ubuntu' user for cloud AMI's.

On the configuration of the SFTP tab you need to explicitly define the SFTP server as:

```
sudo su -c /usr/lib/openssh/sftp-server
```

Be advised you will be able to do root level stuff with files and folders to be sure to be careful.

---

