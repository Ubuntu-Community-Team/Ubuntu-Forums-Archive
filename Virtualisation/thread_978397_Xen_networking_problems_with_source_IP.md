---
title: "Xen networking problems with source IP"
date: 2008-11-11
forum: Virtualisation
---

### Post by maresa on 2008-11-11
Hello,

I got Ubuntu 8.04 64-bit running. I got Dom0 running fine and I got about 5 DomUs running. Everything is working fine, I can boot fine, networking runs smoothly (incoming and outgoing traffic works fine) and it's pretty stable too, I think.

I only have 1 problem with it: I lost source IP address of anyone connecting to my DomU.

Here's what I got:
- Linux mail.microshell.com 2.6.24-19-xen #1 SMP Wed Aug 20 21:08:51 UTC 2008 x86_64 GNU/Linux
- A network card connected to network on Dom0 at eth0 with live IP 1.1.1.1
- A Dummy0 virtual NIC for running local IP 10.1.1.1

Now my problem is, say on DomU, I assigned live IP address 1.1.1.2 then I tried to SSH from my home at IP address 2.2.2.2, when I connect, on DomU it shows that there's SSH connection from Dom0 IP address (1.1.1.1).

The same thing for my DomU that serves HTTP. All the log files shows connection from my Dom0 IP (1.1.1.1). Worse is my Postfix mail. I've set 1.1.1.1/24 as within network and since SMTP connection to any DomU is seen as originated from Dom0 IP address (1.1.1.1), it basically renders my Postfix to be open relay. (before you jump on me about it ... I've set Postfix to not be set as open relay, however since any connection is seen as Dom0 IP address, it appears to Postfix that it originated from trusted local network. My workaround is to not set any trusted networks.

So going back to my original problem ... Can anyone help me configuring things out so that DomU will see the original IP address instead of Dom0 IP address?

If you're wondering why I have Dummy0, it is for my DomU database server. I don't want to give it a public IP. So each DomU (other than database server) will have 2 virtual network card: 1 that has live IP and another one that has local IP 10.1.1.1/24.

Hopefully someone can answer me. I've tried searching Google, etc but I just could not find any answers ...

Thanks,
MSN

---

