---
title: "Failed to connect to EC2 desktop cloud instance of ubuntu-natty-daily-i386-desktop"
date: 2011-04-27
forum: Ubuntu Cloud and Juju
---

### Post by phaan on 2011-04-27
Hi,

I started a instance of ubuntu-natty-daily-i386-desktop (ami-97a89fe3) on EC2.

I can SSH to the instance using PuTTY.

I ran 
>> sudo adduser <some user>

If I run my NX Client, I get :

NX> 203 NXSSH running with pid: 1352
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 46.51.165.158 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

I am using the default keys on the NX client. And of course the UID-PWD from before.

Why is it not working?

Ohh. I am on Windows.

Thanks

---

### Post by bmullan on 2011-04-27
> **phaan said:**
> Hi,

I started a instance of ubuntu-natty-daily-i386-desktop (ami-97a89fe3) on EC2.

I can SSH to the instance using PuTTY.

I ran 
>> sudo adduser <some user>

If I run my NX Client, I get :

NX> 203 NXSSH running with pid: 1352
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 46.51.165.158 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

I am using the default keys on the NX client. And of course the UID-PWD from before.

Why is it not working?

Ohh. I am on Windows.

Thanks

did you allow password logins in /etc/ssh/sshd_config

you might also want to read through the NoMachine NX Server Admin guide

you might also look at [x2go]("http://wiki.x2go.org/").   I've used both and x2go has a lot of advantages.  There is also alot of development going on and now there is a python client, firefox plugin client, and windows, linux and mac native clients.

x2go is GPL for both server and client and no limitation on # of users.

There is an Ubuntu ppa soon to be available also.

I've used x2go on Natty on EC2 and it works defaulting to gnome desktop.
Sound/printing etc worked.

---

