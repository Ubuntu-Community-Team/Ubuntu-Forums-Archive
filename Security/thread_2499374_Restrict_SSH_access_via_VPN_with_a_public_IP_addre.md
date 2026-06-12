---
title: "Restrict SSH access via VPN with a public IP address."
date: 2024-07-24
forum: Security
---

### Post by impending9530 on 2024-07-24
Hello, I am new to this forum. ):P
 
I have a question for you guys. How, can I secure the SSH servers so that the access is through the VPN that I have with a public address.
 
The query is because I want to run VPS in my country that do not have a firewall system like DigitalOcean, Hetzner, AWS or Linode has.
 
Rest assured, I say right away that I have SSH access via a key. But I would prefer to limit SSH access to VPN only. For several weeks in a test environment, I tested various solutions given on the Internet on various sites, which does not work at all, for example: through “Match Users” or “ListenAddress”. 
 
In these above ways, I specified the public IP address of the server where the VPN is running. After restarting the service, it spit out an error and I applied various possible solutions given by users and failed.

---

### Post by The Cog on 2024-07-24
Hi and welcome to the forum.

I do this. I installed wireguard on my PC and my VPS, and run a wireguard VPN between the two. Then I can ssh the VPS through the wireguard tunnel. Actually, the VPS is configured with two peers - my laptop and my desktop. You can then configure sshd_config with AllowUsers yourname@your_wireguard_address so it only allows you from your tunnel's address. 

Make sure you can ssh to it using the vpn before you restrict logins or you will lock yourself out. You could actually open one ssh connection, then using that connection, make the config change and restart sshd (this doesn't break your existing ssh connection) and try making a new connection from another terminal to make sure you can still connect. Revert the config if you can't make a new connection so you're note locked out.

---

### Post by currentshaft on 2024-07-24
> **impending9530 said:**
> Hello, I am new to this forum. ):P
 
I have a question for you guys. How, can I secure the SSH servers so that the access is through the VPN that I have with a public address.

Install the VPN server, install SSH, configure SSH to listen on the VPN interface address.

> **impending9530 said:**
> 
The query is because I want to run VPS in my country that do not have a firewall system like DigitalOcean, Hetzner, AWS or Linode has.

Not an issue if you use public-key authentication and run on a non-standard port; a firewall is not really even required then.

> **impending9530 said:**
> 
Rest assured, I say right away that I have SSH access via a key. But I would prefer to limit SSH access to VPN only. For several weeks in a test environment, I tested various solutions given on the Internet on various sites, which does not work at all, for example: through “Match Users” or “ListenAddress”. 
 
In these above ways, I specified the public IP address of the server where the VPN is running. After restarting the service, it spit out an error and I applied various possible solutions given by users and failed.

You need to share the error and your sshd configuration here for us to be able to help.

---

