---
title: "vsftpd  issue - connection refused"
date: 2012-02-09
forum: Server Platforms
---

### Post by Jstall on 2012-02-09
Hello all,

I am running a virtual Ubuntu server on my machine. Yesterday I set up a vsftp server that allowed logins with system user credentials. It was working fine but today when I tried to connect I am getting a connection refused error. 

Even if I try:
```

ftp localhost

```

I get a connection refused message.

Here are some of the lines in my vsftpd.conf file:
```

local_enable=YES
chroot_local_user=YES
userlist_file=/etc/vsftpd.userlist
userlist_enable=YES
userlist_deny=NO 

```

In my /etc/vsfpd.userlist file I have one line:
```

ftptest

```

this is the name of the user I created to test out the ftp functionality.

I have made sure the service is running by using :
```

service vsftpd start

```
I get the message "start/running, process 6402" , which suggests to me the service is starting properly. Again this was working yesterday, I touched no config files or anything of that nature since then. Could anyone suggest a reason why this is not working? Any advice is very much appreciated. Thanks!

---

