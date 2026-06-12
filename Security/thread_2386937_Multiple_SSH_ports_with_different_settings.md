---
title: "Multiple SSH ports with different settings?"
date: 2018-03-12
forum: Security
---

### Post by ejj28 on 2018-03-12
Hi there,
Is there a way to have SSH listen on multiple ports, each with separate security settings?
I would like to have one port open to the internet with key authentication and one for my local network with password authentication.
Is there any way to do this? Thanks!

---

### Post by slickymaster on 2018-03-12
Thread moved to **Security** for a better fit

---

### Post by QIII on 2018-03-12
Hello!

Having never tried to do something this way, I can't say that the SSH configuration files are flexible enough for something like this.  I use keys even on my home network to avoid getting in to bad habits.  Maybe someone will have done something like this before.  What might be helpful is if you would explain what your goal with this is and why.

Cheers!

---

### Post by ejj28 on 2018-03-12
I run a (very) small server out of my home and I use SSH to connect to it using a password on my local network. However, I want to be able to access my server from anywhere using SSH, with higher security, while still being able to easily connect while at home. Basically just have simple SSH on my home network and very high security SSH opened to the internet. I could just use keys everywhere and have one port, but I want my outward facing SSH to be on a non-standard port and my internal to be standard.

---

### Post by steeldriver on 2018-03-12
Unless the box is connected directly to the internet, then you can control the outward facing port on the WAN side via your router's port forwarding tables

Nevertheless I *think *you should be able to do what you asked using the sshd_config Match directive e.g.

```

PasswordAuthentication no
.
.
.
Match LocalPort xx
PasswordAuthentication yes

```

You would need to set an appropriate ListenAddress / port for the two cases

Alternatively you could match on the Address (i.e. match originating addresses from your LAN)

I've never tried it though ...

---

### Post by ejj28 on 2018-03-12
Ok, I'll give that a try, thanks!

---

### Post by TheFu on 2018-03-12
You can setup different settings based on the subnet.  But using ssh-keys is both more secure AND more convenient.  I'm always surprised when folks don't just use keys all-the-time. Passwords are such a hassle.

For example, if you want to allow passwords, but only from the internal LAN, then put these settings at the end of the sshd_config file:

```
# Change to no to disable tunneled clear text passwords
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24
      PasswordAuthentication yes
```

I use a few different LAN networks. This does work, BTW.  But really if fail2ban is working correctly, most of this isn't necessary.  If fail2ban is broken (which seems to happen a few times recently), then having more secure settings is an added safety net.  There are lots of articles about securing ssh.

---

