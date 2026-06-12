---
title: "How to set up web-facing ssh server securely?"
date: 2010-10-18
forum: Security
---

### Post by chevelleman71 on 2010-10-18
**Here's what I have:**

I have a small network at my office (3 workstations, 1 ubuntu desktop that I'm using as a file server). I'm using a WRT54G2 router for networking and internet connectivity. 


**Here's what I'm trying to accomplish:**

I want to be able to access my little file server from home, across town. I think ssh might be the best way to go now. 


**What I don't know:**

How do I set up the ssh server on my machine/network without compromising my network security and the security of my server?

Do I just set up port/ip forwarding on my router, install openssh, and that's it?

Help!
Thanks

Luke

---

### Post by kelt65 on 2010-10-18
> **chevelleman71 said:**
> **Here's what I have:**

I have a small network at my office (3 workstations, 1 ubuntu desktop that I'm using as a file server). I'm using a WRT54G2 router for networking and internet connectivity. 


**Here's what I'm trying to accomplish:**

I want to be able to access my little file server from home, across town. I think ssh might be the best way to go now. 


**What I don't know:**

How do I set up the ssh server on my machine/network without compromising my network security and the security of my server?

Do I just set up port/ip forwarding on my router, install openssh, and that's it?

Help!
Thanks

Luke

More or less, that's all you have to do. However, it would be wise to set

PermitRootLogin no # from "yes" in /etc/ssh/sshd_config

And also restrict the networks that can connect in /etc/hosts.allow

---

### Post by chevelleman71 on 2010-10-18
> **kelt65 said:**
> More or less, that's all you have to do. However, it would be wise to set

PermitRootLogin no # from "yes" in /etc/ssh/sshd_config

Ok, sounds great!

> **kelt65 said:**
> And also restrict the networks that can connect in /etc/hosts.allow

So... I would set up dyn-dns with my home dynamic ip then use that as the only allowed traffic source? 

Also, would I want to set up some other kind of firewall(s) like an IP table to help keep things safe?


Thanks.

I know these are noob questions, but I learn alot from the answers here.

Luke

---

### Post by cariboo on 2010-10-18
If your office is behind a router, and you only have port 22 forwarded, you don't need another firewall. The only other thing you may want to look at is [Denyhosts]("http://denyhosts.sourceforge.net/"), it's in the repositories.

---

### Post by oregonbob on 2010-10-18
1) Simply install openssh on your ubuntu machine. Assign a static (fixed) IP address to your ubuntu.

2) Go into router admin, setup IP forwarding of port 22 to be directed to the IP address of your ubuntu machine. Even better you can assign a custom port such as any port over 1024 to be redirected to port 22 on your ubuntu. On my Linksys WRT54G port forwarding is under "Gaming and Applications"

3) Use good passwords. As stated above it is a good idea to use hosts.allow and hosts.deny to restrict who can access your machine. If you leave it open the kiddies will try to break in 24/7/365

4) If you want excellent GUI desktop access, try installing NXServer. You can download it from nomachine.com . Easy to install & config. It is the best remote access on the market and 2 user version is free.

Oops, I assume your office has a static external IP address. If it is dynamic, see if ISP will make it static or you can setup with a dynamic DNS service. Static is the way to go.

---

### Post by FuturePilot on 2010-10-18
> **oregonbob said:**
> 
3) Use good passwords.

Keys > passwords

My two pieces of advice:

1. Disable password auth completely and only use keys.
2. Use denyhosts or fail2ban.

---

### Post by CharlesA on 2010-10-19
> **FuturePilot said:**
> Keys > passwords

My two pieces of advice:

1. Disable password auth completely and only use keys.
2. Use denyhosts or fail2ban.

Big +1 to that.

Personally, I just use key auth only and use iptables to ban ipaddresses that try to connect repeatedly within a specific time.

---

### Post by Grenage on 2010-10-19
I use a good password for my home machine - I can't be bothered with the hassle of a key.  For work machines, I would definitely use a key.

---

### Post by CharlesA on 2010-10-19
> **Grenage said:**
> I use a good password for my home machine - I can't be bothered with the hassle of a key.  For work machines, I would definitely use a key.

As long as it's a non dictionary password with some special characters thrown in, it should be fine.

---

### Post by HermanAB on 2010-10-19
Howdy,

My tuppence worth:
I disable root login, set the server to use a non standard port for SSH and use very long semi-pronounceable passwords as well as keys.

So I don't disable password login, but I always use strong passwords.  The SSH keys are used for automatic tasks like rsync backup scripts.

---

### Post by chevelleman71 on 2010-10-21
Thanks for the answers. I really appreciate everyone's input. I'm going to set this all up this weekend - I'll let you know how it goes!

Luke

---

### Post by chevelleman71 on 2011-01-08
I wanted to follow up on this, finally. I followed the suggestions of some of the previous posters, and installed open ssh. I configured it, along with Denyhosts. I set it up to run on a custom port, and made sure that port was opened in my firewall/router. It worked like a charm. 

Thanks for all the input everyone gave.

For anyone else considering doing this, it's pretty easy.

Luke

---

### Post by ptn107 on 2011-01-09
You can also add *AllowUsers* to your /etc/ssh/sshd_config file as such:

```
AllowUsers username
```

Replace *username* with a space separated list of users or maybe just your own username.  Anyone not listed cannot log in, period.

---

