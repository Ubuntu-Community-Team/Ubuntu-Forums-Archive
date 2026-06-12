---
title: "Remote root access denied (SSH and Rlogin)"
date: 2008-05-03
forum: Server Platforms
---

### Post by f3ua on 2008-05-03
Hi everybody,

I need a little support on my new Ubuntu server. Due to compatibility reasons with some scripts running on other servers, I've enabled the root user and installed some services to get access from other machines like ssh and rlogin.

The problem is that, for both services, I can't get access with root user. If I try with a normal user all works well.

Why? Any ideas?

PS. for SSH I also checked the parameter "AllowRoot" and it's yes.

---

### Post by windependence on 2008-05-04
> **f3ua said:**
> Hi everybody,

I need a little support on my new Ubuntu server. Due to compatibility reasons with some scripts running on other servers, I've enabled the root user and installed some services to get access from other machines like ssh and rlogin.

The problem is that, for both services, I can't get access with root user. If I try with a normal user all works well.

Why? Any ideas?

PS. for SSH I also checked the parameter "AllowRoot" and it's yes.

This is a GOOD thing. Can you su - once you log in as a regular user? You really don't want people to be able to log in as root anyway.

-Tim

---

### Post by f3ua on 2008-05-04
Yes, I can logon as normal user and than do a su -. But I absolutly need to get root access directly.

Any other solution?

Thanks in advance.

---

### Post by Oldsoldier2003 on 2008-05-04
> **f3ua said:**
> Yes, I can logon as normal user and than do a su -. But I absolutly need to get root access directly.

Any other solution?

Thanks in advance.

check roots shell in /etc/passwd it's probably set to /bin/false

---

### Post by wormser on 2008-05-05
You should check the sshd_config file.  There is an option to turn root login on.

```
sudo nano /etc/ssh/sshd_config
```

Change PermitRootLogin to yes.

---

### Post by windependence on 2008-05-05
> **f3ua said:**
> Yes, I can logon as normal user and than do a su -. But I absolutly need to get root access directly.

Any other solution?

Thanks in advance.

Tell me why you absolutely need it that way. There may be a more secure way to do it. What are you doing with the box that needs this access?

-Tim

---

### Post by f3ua on 2008-05-05
> **Oldsoldier2003 said:**
> check roots shell in /etc/passwd it's probably set to /bin/false

This is the first line of /etc/passwd

```
root:x:0:0:root:/root:/bin/bash
```

Is this line ok? should I change something?

---

### Post by geertn on 2008-05-05
Should be fine. Might be obvious, but did you change the root password? (sudo bash; passwd)

If it still doesn't work, check the output of /var/log/auth.log

---

### Post by f3ua on 2008-05-06
No way...

This is when I try to login trough ssh:

```
login as: root
root@10.101.30.150's password:
Access denied
root@10.101.30.150's password:

```

BUT, if I do...

```
login as: rferrar1
rferrar1@10.101.30.150's password:
rferrar1@kue04hpnew:~$ su
Password:
root@kue04hpnew:/home/rferrar1#

```

So the password for root user has been enabled. Now I checked the auth.log:

```
May  6 08:58:41 kue04hpnew login[3742]: ROOT LOGIN  on `tty1'
May  6 09:04:19 kue04hpnew su[3793]: + pts/0 rferrar1:root
May  6 09:04:19 kue04hpnew su[3793]: (pam_unix) session opened for user root by (uid=1000)

```

And this is the sshd_config
```

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

```


I can't see the forbidden authorization for direct root access.
Any other ideas?

---

