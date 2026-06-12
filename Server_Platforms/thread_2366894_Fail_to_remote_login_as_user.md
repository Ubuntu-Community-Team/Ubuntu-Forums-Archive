---
title: "Fail to remote login as user"
date: 2017-07-23
forum: Server Platforms
---

### Post by satimis on 2017-07-23
Hi all,

Ubuntu 16.04 server on VM of VirtualBox

There is some strange happened here.  This is the 5th Ubuntu 16.04 server installed within 2 days.

Installation went through without problem including update and upgrade.

ssh also installed
$ apt-cache policy ssh```

sh:
Installed: 1:7.2p2-4ubuntu2.2
Candidate: 1:7.2p2-4ubuntu2.2
....

```

But I can't remote login the server as user

$ ssh user@ip_address```

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:HjMkOuERIUkwdnqIg0/NU7Jk5M6pwRDEs+LZYAAzpb8.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/user/.ssh/known_hosts:5
  remove with:
  ssh-keygen -f "/home/user/.ssh/known_hosts" -R ip_address
ECDSA host key for ip_address has changed and you have requested strict checking.
Host key verification failed.

```

I can't find the directory .ssh

# ls -al /home/user
.ssh is not there

I have performed;
```

sudo apt-get install --reinstall ssh

```

also
```

sudo apt-get purge package
sudo apt-get install package

```

all without result.  /home/user/.ssh is not there.

remote ping ip_address works without problem

Please help.

Regard
satimis

---

### Post by darkod on 2017-07-23
As the message says, just remove the entry in known_hosts with this command:
```
ssh-keygen -R ip_address
```

Then try again.

You can see that message after you have reinstalled the server you are tryig to access, or after reinstalling openssh-server.

---

### Post by satimis on 2017-07-23
> **darkod said:**
> As the message says, just remove the entry in known_hosts with this command:
```
ssh-keygen -R ip_address
```

Then try again.
Hi,

Performed following steps

&#10219; ssh-keygen -R ip_address```

# Host ip_address found: line 5
/home/user/.ssh/known_hosts updated.
Original contents retained as /home/user/.ssh/known_hosts.old

```

&#10219; ssh user@ip_address```

The authenticity of host 'ip_address (ip_address)' can't be established.
ECDSA key fingerprint is SHA256:HjMkOuERIUkwdnqIg0/NU7Jk5M6pwRDEs+LZYAAzpb8.
Are you sure you want to continue connecting (yes/no)? yes

Warning: Permanently added 'ip_address' (ECDSA) to the list of known hosts.
user@ip_address's password: 
Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-62-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

7 packages can be updated.
7 updates are security updates.

Last login: Sun Jul 23 23:03:56 2017

```

Your advice works for me.  Thanks

> 
You can see that message after you have reinstalled the server you are tryig to access, or after reinstalling openssh-server.
No I haven't reinstalled this server.  I saw that warning on first remote login as user.

I thought it was the problem of ssh therefore I reinstall openssh-server 

I installed 5 Ubuntu 16.04 servers on 5 VMs, all fresh installation on ISO.  The steps of installation were the same but with different result.  I can't under stand.  All are for testing Docker.

Later I'll clone a new server on this server for testing Docker rather than making fresh installation each time.

Edit
===
On the server
$ ls -al /home/user/
.ssh is NOT there.  Why?

Regards
satimis

---

### Post by darkod on 2017-07-23
The .ssh folder does not exist by default. It is created only when it is needed. So, that is normal.

---

### Post by satimis on 2017-07-23
> **darkod said:**
> The .ssh folder does not exist by default. It is created only when it is needed. So, that is normal.
Noted and thanks

satimis

---

### Post by TheFu on 2017-07-25
Please mark all solved threads as **solved** to help the community.  This helps people looking for answers and prevents people who want to help from bothering, if it is SOLVED already.

---

