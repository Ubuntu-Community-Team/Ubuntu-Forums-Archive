---
title: "Setting up a nvcserver"
date: 2019-04-12
forum: Server Platforms
---

### Post by torbentf on 2019-04-12
Hi,
I have a problem setting up a nvcserver:

ssh -v -L 5901:127.0.0.1:5901 -C -N -l sammy your_server_ip

gives

torben@torben-Aspire-E5-773G:~$ ssh -v -L 5901:127.0.0.1:5901 -C -N -l torben 192.168.110.1
OpenSSH_7.6p1 Ubuntu-4ubuntu0.1, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.110.1 [192.168.110.1] port 22.
debug1: connect to address 192.168.110.1 port 22: Connection refused
ssh: connect to host 192.168.110.1 port 22: Connection refused

the relevant part of /etc/ssh/ssh_config gives:
.
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Protocol 2
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc
#
.

I have tried:

ufw allow 22
and:
torben@torben-Aspire-E5-773G:~$ sudo service ssh restart
Failed to restart ssh.service: Unit ssh.service not found

I assume that "sammy" is the user name I log on to my computer with (torben) and "your_server_ip" is my server address (192.168.110.1 - the same I use to access my router with).

The proxy is off.

I found one item on the net which prompted the two tries - to no avail.
Can anybody help?
torben

---

### Post by slickymaster on 2019-04-12
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2019-04-12
Troubleshooting ssh connections: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

Forget trying to get the tunnel to work until you have plain ssh working first.  ssh_config is a client-only file. All settings in the client-config file can be set in ~/.ssh/config on the client machine for each individual userid. The server config file is named sshd_config.

Also, trying to restart ssh on the client isn't useful.  The server is where that runs, not the client.

---

### Post by torbentf on 2019-04-13
Hi TheFu,
Thank you for the address.
It appears there are problems with "open ssh-server":

torben@torben-Aspire-E5-773G:~$ sudo apt install openssh-client openssh-server
[sudo] password for torben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version (1:7.6p1-4ubuntu0.1).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 openssh-server : Depends: openssh-client (= 1:7.6p1-4)
                  Depends: openssh-sftp-server but it is not going to be installed
E: Unable to correct problems, you have held broken packages

I can find several sshd_config - fx.:

/snap/core/6405/etc/pam.d/sshd
/snap/core/6405/etc/ssh/sshd_config
/snap/core/6405/etc/systemd/system/sshd.service
/snap/core/6405/usr/lib/snapd/sshd-host-keygen
/snap/core/6405/usr/lib/tmpfiles.d/sshd.conf

I am out of my depth!

torben

---

### Post by torbentf on 2019-04-13
Hi TheFu,
Thank you for the address.
It appears there are problems with "open ssh-server":

torben@torben-Aspire-E5-773G:~$ sudo apt install openssh-client openssh-server
[sudo] password for torben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version (1:7.6p1-4ubuntu0.1).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 openssh-server : Depends: openssh-client (= 1:7.6p1-4)
                  Depends: openssh-sftp-server but it is not going to be installed
E: Unable to correct problems, you have held broken packages

I can find several sshd_config - fx.:

/snap/core/6405/etc/pam.d/sshd
/snap/core/6405/etc/ssh/sshd_config
/snap/core/6405/etc/systemd/system/sshd.service
/snap/core/6405/usr/lib/snapd/sshd-host-keygen
/snap/core/6405/usr/lib/tmpfiles.d/sshd.conf

I am out of my depth!

torben

---

### Post by torbentf on 2019-04-13
Hi TheFu,
There are plenty of openssh-server, openssh-client and openssh-sftp-serverr files.
torben

---

### Post by TheFu on 2019-04-13
I don't know anything about snaps.  We don't use them and purge the snapd subsystem from all our computers after having almost every snap package causing problems.  Sorry.

---

