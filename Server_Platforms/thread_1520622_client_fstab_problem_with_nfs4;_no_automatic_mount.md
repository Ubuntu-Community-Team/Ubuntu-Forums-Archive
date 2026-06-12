---
title: "client fstab problem with nfs4; no automatic mount at boot"
date: 2010-06-29
forum: Server Platforms
---

### Post by jwferk on 2010-06-29
I'd like to have my client desktop automatically boot up the connection to my server.  Both machines are running the latest versions of Ubuntu (desktop or server).  NFS4 works fine from the terminal with the commands shown below.  The desktop mounts the appropriate hardisks on the server. However, I can't get the desktop to mount the server at boot.

The server is always running.  The firewalls are set with appropriate permissions for crosstalk between the machines.

The terminal output to manually mount the server looks like this:

ferk@reuben:~$ sudo -i
[sudo] password for ferk: 
root@reuben:~# mount 192.168.1.2:/home/ferk /ServerHome
root@reuben:~# mount 192.168.1.2:/media/LinuxBackup /LinuxBack
root@reuben:~# mount 192.168.1.2:/media/WindowsBack /WindowsBack

The desktop /etc/fstab file is here:

192.168.1.2:/home/ferk		/ServerHome	nfs4	_netdev,auto	0	0
192.168.1.2:/media/LinuxBackup	/LinuxBack	nfs4	_netdev,auto	0	0
192.168.1.2:/media/WindowsBaxk	/WindowsBack	nfs4	_netdev,auto	0	0

What am I missing?

Thanks.

---

