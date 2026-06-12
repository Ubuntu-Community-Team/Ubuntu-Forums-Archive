---
title: "Updates Fail"
date: 2013-12-31
forum: Server Platforms
---

### Post by grier-devon on 2013-12-31
Hello Everyone,
So in the future I want to set up a Ubuntu server for the house and figured I would create an virutal Ubuntu server for learning purposes. I installed Ubuntu Server 12.04.3 in Virtualbox and when I do 
```
sudo apt-get update
```
and I get all             "W: Failed to Fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)
                               W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)
                               W: Failed to Fetch [http://us.archieve.archieve.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archieve.archieve.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)
                               W: Failed to Fetch [http://security.ubuntu.com/ubuntu/dists/precise-sercurity/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-sercurity/Release.gpg)
                               W: Some index files failed to download. They have been ignored, or old ones used instead."
So I know it is something I did not set up correctly, I am just needing some direction on what I failed to set up on a fresh Ubuntu Server install, thanks for any help.

---

### Post by mikewhatever on 2013-12-31
It's networkworking. If there aren't any settings in /etc/network/interfaces, search for a server guide.
For example: [https://help.ubuntu.com/10.04/serverguide/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/network-configuration.html).

---

### Post by grier-devon on 2013-12-31
Well I have downloaded the Ubuntu Server 12.04 manual and all I am seeing is how to add the universe and multiverse repositories, I am new to working with the server side of the house. Shouldn't the Ubuntu Server have a base set of repositories in which it pulls updates for bug fixes and security updates? I am looking at my sources.list and this is what it shows me...

---

### Post by volkswagner on 2013-12-31
As Mikewhatever stated, it is a networking issue.  The problem is not related to your apt sources.list.

This could be a VirtualBox issue depending how you setup networking for the VM.

From Ubuntu post the following commands:

```
cat /etc/network/interfaces
```
```
ifconfig
```
```
ping google.com
```

Try to ping your gateway: ie if your router is 192.168.1.1

```
ping 192.168.1.1
```

---

### Post by grier-devon on 2013-12-31
When I try to ping google it just keeps trying to connect.

---

### Post by volkswagner on 2014-01-01
I see your ip address is 10.0.2.15.

What is the ip address of your router?

Can you ping your router from ubuntu?  Can you ping 10.0.2.15 from the host machine?

How did you setup networking in VirtualBox?

What is your host Operating System?  It may be a firewall issue on the host.  You may try
disabling firewall on host to see if Ubuntu VM can get a gateway.

---

### Post by JnPson on 2014-01-01
It might be that you have to change your network settings for your virtual machine. If you are using VirtualBox you change this in```
Settings | Network | Attached to: 
```
Change it from NAT to Bridged Adaper and your virtual machine should be able to update.

---

### Post by grier-devon on 2014-01-01
Okay so I pinged my router IP address and it did the same thing when I pinged google. I also checked the Attach in the network setting and changed it from NAT to Bridge Adapter, I even reset the VM and still fails but this time gives "Err" to connect at first. I am running this VM on the Ubuntu desktop and don't believe I configured the firewall. I don't know if this matters but I can load a linux distro example being link Fedora in a VM and have internet connection with no problems. Also when I try to ping 10.0.2.15 and it says 
"PING 10.0.2.15 (10.0.2.15) 56(84) bytes of data."
with a non stop blinking courser.
When I try to ping from my Ubuntu computer I get the same results when pinging my router.

---

