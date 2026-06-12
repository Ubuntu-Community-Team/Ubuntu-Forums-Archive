---
title: "One machine not connecting to SSH w/ Putty - Ubuntu Server 14.04.1"
date: 2015-01-31
forum: Server Platforms
---

### Post by tlarson91119 on 2015-01-31
Hi!
This is my first post on the forums. I've just created a new account. Just recently got into networking and learned how to install Ubuntu Server on a simple machine to use as a learning tool. I've managed to set up SSH Server on the machine and I am able to connect to it from all my machines in the local network, but I noticed something weird

I've got 1 desktop running Lubuntu and three Windows clients. When I try to connect with Putty on one of my Windows clients (by entering the **server's local IP**), I get the following error:
**PuTTy Fatal Error: Server unexpectedly closed network connection.**

I can only connect to it, from this machine, if I enter my public IP instead of the local ip of the server, which really confuses me because I can enter the local IP on all of the other machines.
The only thing that I think might be related to it, is denyhosts. I tried to configure denyhosts for some added security. Denyhosts didn't work out to well for me, so I removed it and installed fail2ban. I had my friend, who works with servers and stuff, help me setup and configure fail2ban and that seems to be working good.


To be honest, I don't really know if it matters that I enter the public IP to login opposed to the local IP, but I'm just curious as to why all of my other machines let me enter the local IP without problems, but I have to enter the public IP in order to connect to it.

If anyone has any ideas to share with me, that would be great. It's probably something simple, but I haven't any idea. Thank you!

*I hope I posted this thread in the right location. I saw Server Platforms and thought that might be it, hopefully it is.*

---

### Post by nerdtron on 2015-01-31
Are all the PCs, linux and windows on the same LAN and the same address block?
Can each windows pc ping the servers local IP?

---

### Post by volkswagner on 2015-01-31
Can you ping the server's ip address from the client?

As mentioned, are all machines on same LAN/Subnet.

It could be a simple as your client is mistakenly connected to your neighbors unsecured wireless network, or
your own guest network on different subnet.

---

### Post by TheFu on 2015-01-31
Agree with the other 2 posters questions.
Might be good to check the firewall settings on the linux machine.  **sudo iptables -L**.
And it couldn't hurt to check the outbound firewall settings on the Windows machines too.

---

### Post by tlarson91119 on 2015-02-03
I believe they are all on the same "address block". I'm assuming you mean a sub-network? I'm still getting used to all this terminology. I can also ping the server from my Windows client. I tried checking iptables and couldn't find anything that I thought might be related to the issue.
I'm sorry for late reply. I just remembered that I posted this thread. But yeah. All my machines are on the same sub-net and they can all ping each other (including the desktop that doesn't want to connect by entering the local IP address).

I did some more work on the ssh server. I managed to setup an authorization key login, which is working very nice and I saved a preset so I don't have to enter all the parameters constantly. I saved the preset with the public IP, which is doing great.

Here is what I got from the iptables output:
###############################################
root@server-name:/# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-ip-blocklist  tcp  --  anywhere             anywhere
fail2ban-repeatoffender  tcp  --  anywhere             anywhere
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports 222

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-ip-blocklist (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

Chain fail2ban-repeatoffender (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
###############################################

Again sorry for the late reply. :)

---

### Post by volkswagner on 2015-02-03
Have you verified the client ip hasn't been jailed/banned by fail2ban?

I'm no fail2ban expert but you should be able to check the status of each jail to see if an ip's have been banned.

Get a full list of commands
```
fail2ban-client
```
Find the name of all your jails
```
fail2ban-client status
```
find the status of a specific jail
```
fail2ban-client status name-of-jail
```
unban an ip from a specific jail
```
fail2ban-client name-of-jail addignoreip 192.168.7.172
```

```

```

---

