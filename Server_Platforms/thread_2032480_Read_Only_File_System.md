---
title: "Read Only File System"
date: 2012-07-24
forum: Server Platforms
---

### Post by xpresservers on 2012-07-24
Hello Fellows,

One of my client is running Ubuntu 12 server edition on Windows Azure. I configured it with LAMP, VSFTP, Webmin and on client's request I setup NewRelic php extension too. This is second time whole server's file system change to read only. The only solution worked for me is rebooting the server. After reboot this problem resolve automatically but appear again after few days. The server is running under Hyper-V virtualization from Microsoft Windows Azure.

```

login as: (username)
(username)@(IP)'s password:
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-virtual x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Jul 22 15:42:40 UTC 2012

  System load:  0.01              Processes:           94
  Usage of /:   6.5% of 29.96GB   Users logged in:     0
  Memory usage: 22%               IP address for eth0: 10.119.36.136
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Get cloud support with Ubuntu Advantage Cloud Guest
  http://www.ubuntu.com/business/services/cloud

(user)@(host):~$ sudo su
[sudo] password for (user):
sudo: unable to open /var/lib/sudo/(user)/0: Read-only file system
root@(host):/home/(user)#

```

And when I tried to connect using ftp I got following error

```

Status:	Connecting to xxx.xxx.xxx.xxx:21...
Status:	Connection established, waiting for welcome message...
Response:	500 OOPS: failed to open xferlog log file:/var/log/vsftpd.log
Error:	Critical error
Error:	Could not connect to server

```

Help me to resolve this issue.

---

### Post by SeijiSensei on 2012-07-24
[http://ubuntuforums.org/showpost.php?p=11825327&postcount=6](http://ubuntuforums.org/showpost.php?p=11825327&postcount=6)

---

### Post by rubylaser on 2012-07-25
I have had this read only behavior happen in our organization on with Ubuntu virtualized in Hyper-V.  I don't see it with any other hypervisor, and it seems to happen with only one of our 6 virtualized Linux boxes on this same Hyper-V host.  Updating this host almost always leads to this behavior.  I worked on it for a few months, and finally, migrated this web host back onto Proxmox where it's been running great for months.

---

