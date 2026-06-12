---
title: "Whole disk encryption and SSH"
date: 2013-01-30
forum: Security
---

### Post by mcreef on 2013-01-30
I am having trouble setting up an SSH connection with a new (12.04) server build through putty, and I am wondering if I am just banging my head against a brick wall here.

As the title suggests, I have implemented whole disk encryption during install, so everything is encrypted with the exception of /boot.

My troubles are with getting keyed SSH to connect, though password connection works just fine. I have been working under the assumption that this should work, as (as I understand it) once the system is booted and the passphrase entered with WDE, the whole system operates unencrypted, where as with /home encryption you need to make special accommodations as the /home partition is encrypted right up until you log in (and therefore the key as well).

I realize that I will not be able to reboot through SSH, and this is fine for my application, I just want to be able to SSH into my machine while it is already up and running for other administrative tasks. I would like to be able to do this through the most secure means that are reasonably available to me, hence my desire to use keys, but I am having real difficulty working it out. I want to make sure I am not just chasing my own tail here before I rip out any more of my own hair trying to get it to connect.

I have seen some tutorials for dropbear in my searches, but if I can accomplish what I am looking to do without going down that road I would like to do that. Please let me know if I am way off track here.

---

### Post by chadk5utc on 2013-01-30
Heres is a good tutorial for key based ssh setup [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) its the best way to go for security. Also note that any command you can use on the machine sitting in front of it can be used remotely unless restricted by user permissions. This is how most will monitor and administer their machines/servers

---

### Post by mcreef on 2013-01-30
I appreciate the help. However, I have been through that tutorial, and several others, without any luck in making this work.

I am able to log in using a password, it is only the key method that fails.

All I get is "Server refused our key". Searches for that term have brought me no solutions that work for me. Though I do get some references to encrypted home directories which is what got me wondering if my WDE is the issue, though if I am understanding how that work correctly I don't think it should...

sudo /usr/sbin/sshd -d gives me

```
debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Bind to port 22 on 0.0.0.0 failed: Address already in use.
debug1: Bind to port 22 on ::.
Bind to port 22 on :: failed: Address already in use.
Cannot bind any address.

```

sudo netstat -lnp --inet gives me...

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1724/smbd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3893/sshd
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1724/smbd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1136/dhclient3
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1392/dhclient3
udp        0      0 10.1.10.255:137         0.0.0.0:*                           1734/nmbd
udp        0      0 10.1.10.196:137         0.0.0.0:*                           1734/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1734/nmbd
udp        0      0 10.1.10.255:138         0.0.0.0:*                           1734/nmbd
udp        0      0 10.1.10.196:138         0.0.0.0:*                           1734/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1734/nmbd
```

---

### Post by Lars Noodén on 2013-01-30
If you're able to log in with a password, then the problem is not likely with sshd.  (Also, you need to kill the existing sshd before running it with -d)  Have you checked that the key is complete on the remote host, safely in ~/.ssh/authorized_keys and complete, unbroken on a single line?

What is the output from 'ssh -v' when trying to connect using the key?

---

### Post by mcreef on 2013-01-30
I am pretty certain I have the key saved correctly, all one line.

cat /var/log/auth.log gives me...

```
Jan 30 10:05:29 severname sudo: username : TTY=tty1 ; PWD=/home/username ; USER=root ; COMMAND=/sbin/start ssh
Jan 30 10:05:29 severname sudo: pam_unix(sudo:session): session opened for user root by username(uid=1000)
Jan 30 10:05:29 severname sudo: pam_unix(sudo:session): session closed for user root
Jan 30 10:05:29 severname sshd[5601]: Set /proc/self/oom_score_adj from 0 to -1000
Jan 30 10:05:29 severname sshd[5601]: Server listening on 0.0.0.0 port 22.
Jan 30 10:05:52 severname sshd[5602]: Set /proc/self/oom_score_adj to 0
Jan 30 10:05:52 severname sshd[5602]: Connection from 10.1.10.148 port 49418
Jan 30 10:05:53 severname sshd[5602]: Failed publickey for username from 10.1.10.148 port 49418 ssh2
Jan 30 10:06:00 severname sshd[5602]: Accepted password for username from 10.1.10.148 port 49418 ssh2
Jan 30 10:06:00 severname sshd[5602]: pam_unix(sshd:session): session opened for user username by (uid=0)
Jan 30 10:06:00 severname sshd[5602]: User child is on pid 5618
```

---

### Post by mcreef on 2013-01-30
I appreciate all the help. It appears as if I had made some sort of error with my passkeys. After regenerating my keys for the tenth time or so and re-copying and saving them again, it works. Clearly the error was in there somewhere though they looked exactly as they should, as that is all I did to fix it.

A copy and paste is just about the most simple thing I have done in this whole build, but somehow I managed to muck that up anyway.

Thanks again.

---

