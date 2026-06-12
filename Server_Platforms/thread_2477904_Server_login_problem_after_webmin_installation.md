---
title: "Server login problem after webmin installation"
date: 2022-08-10
forum: Server Platforms
---

### Post by albevala on 2022-08-10
Hi everyone, I have an Ubuntu 20.04 (virtual desktop) server on Aruba Cloud. I have installed everything needed for Laravel with [this guide]("https://www.cloud.it/tutorial/come-installare-laravel-con-lamp-e-composer-su-ubuntu-20-04.aspx?fbclid=IwAR3iTp7OTiWRsOcAoYC_N0Nv5lJax98fuxW25tBMRVboZhc6gZE2IeyoTpI"). So far everything ok. I then installed Webmin with [this guide]("https://www.guidetti-informatica.net/2021/01/come-installare-webmin-su-ubuntu-20-04/"). After finishing this installation I have agreed that I can no longer access either via ssh (port 22) or via virtual desktop. Could you tell me what the problem might have been. Thank you.

---

### Post by LHammonds on 2022-08-11
I have never used webmin but I seriously doubt setting up a web site would block your ssh (22) port.  Are you sure it was opened on the firewall before starting the webmin install?

But regardless, you need to allow port 22 in your firewall so your PC can access it remotely.

If you can get console access, make sure the sshd service is running and enable port 22 on the firewall so your PC can access it remotely.

LHammonds

---

### Post by albevala on 2022-08-11
Ok, thanks for the reply. It could be a firewall configuration problem.

---

### Post by LHammonds on 2022-08-12
If you just installed Ubuntu and did not enable the firewall, it might be possible you enabled the firewall by issuing a firewall rule to allow webmin to work.

If using UFW, you can see what rules are active using this command:
```
sudo ufw status
```

You can see if SSH service is running with this command:
```
systemctl status sshd
```

To see what ports a particular service is listening on, you can run a command similar to this (there are many ways to check for active ports)
```
lsof -i -P -n | grep ssh
```
I'm not at a terminal window to verify the above command for ssh but you would change what grep looks for to reduce the list....or look at everything without grep:
```
lsof -i -P -n
```

LHammonds

---

### Post by TheFu on 2022-08-12
For any public facing server, best to put ssh onto a non-standard port and never allow passwords to be used for authentication.
All this does is to massively reduce failed ssh attempts and keep your logs cleaner, but if going from 50K attempts/day to 20 happens, that leaves much more time to concentrate on what's important.

I tried to use webmin in the 1990s. Got hacked and the entire system, all data, was taken and trashed.  At the time, I was quite the noob. If you use webmin, please, please, please, only allow localhost connections, never allow connections from the LAN or WAN or internet.  ssh tunnels make this easy, but not if ssh isn't working. ;(
The same applies to all remote admin web tools like myphpadmin or Cockpit or phpmyadmin or the LDAP admin tool everyone uses.  Localhost connections only for all of those - even if your workstation is on the same LAN with those servers (like happens in many home labs).

Troubleshooting ssh connections: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

