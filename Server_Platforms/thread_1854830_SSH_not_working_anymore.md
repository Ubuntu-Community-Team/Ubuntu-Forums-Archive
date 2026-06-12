---
title: "SSH not working anymore"
date: 2011-10-05
forum: Server Platforms
---

### Post by LoicV on 2011-10-05
Hi,

Yesterday, i upgraded my server from ubuntu 9.04 to ubuntu 10.04.

Then i rebooted the server.

It seems the SSH and FTP stopped to work ; when i try to connect to the server with SSH, i got the message : 
> **Erreur "Connection refused"**


My server is hosted by OVH, so i could reboot in th "rescue mode" to access the disk : 

- i reinstalled SSH :
```
# sudo apt-get remove openssh-server
# sudo apt-get install openssh-server

```then : 
```
# ps -ef | grep ssh
sshd    3359     1  0 09:36 ?        00:00:00 /sbin/rpc.statd
root      3491     1  0 09:36 ?        00:00:00 /usr/sbin/sshd
root      3841  3491  0 09:50 ?        00:00:00 sshd: root@pts/1 
root      4280  3491  0 10:08 ?        00:00:00 sshd: root@pts/2 
root      9610  9242  0 10:57 ?        00:00:00 grep ssh

```And there is no firewall : 
```

# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

```The log files contains nothing after the upgrade.

I also did :
```

sudo apt-get update
sudo apt-get upgrade

```When i reboot the server, the problem is still here : no ssh.




Any idea how to fix it please ?

---

### Post by volkswagner on 2011-10-05
By any chance are you trying to ssh with root account?

If so you may have to enable it in less /etc/ssh/sshd_config.  As you can see mine is disabled (may be the default).


```
# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

```

Also make sure ssh is not listening on restricted networks.  The following should be commented out as below.  Verify the listening port is standard port 22 also.

```
# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2

```

Are you sure you server has internet access?

If you can run the following from server recovery mode.
```
host google.com
```

---

### Post by LoicV on 2011-10-05
I tried with a non-root account, and i reseted the SSH port to the default (22).

And i have internet access, even in recovery mode...



I really have no clue where the problem could be.

---

### Post by volkswagner on 2011-10-05
Perhaps you can see if ssh is working at all by

```
ssh user@localhost
```

From your recovery session.

This may help narrow down if it is a network issue or application issue.

---

### Post by LoicV on 2011-10-05
```
ssh user@localhost 
```Worked.


Somehow, it seems the application runs fine in recovery mode, but doesn't start when i reboot in "normal" mode, from HD.



Well, nevermind... i will reinstall everything from scratch, and restore the backups of the datas..
It will be faster and easier.


Thank you for help anyway, i appreciated !

---

