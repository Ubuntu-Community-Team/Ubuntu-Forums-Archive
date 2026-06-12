---
title: "Ubuntu VPN + SSH"
date: 2013-02-25
forum: Server Platforms
---

### Post by cotoman on 2013-02-25
so i have a server that has ubuntu 12.04. an it has public IP on it. and i access it from that IP so i cannot risk any IP change or anything that may interrupt the interface. i need to make SSH from server to my local computer. a VPN is not that easy to do on a local computer and if i set up a VPN on the server i risk that when i connect the interface will take the default gateway of the VPN so it won't have a connection. anyway any ideas on doing this it would be appreciated. here is a summary:
Machine A: public IP, not reachable but from ssh and VNC.
Machine B: local network, fully accessible 
Machine A must connect to Machine B using SSH somehow.
Machine A cannot risk any network interruption.

---

### Post by codemaniac on 2013-02-25
Not a Programming topic, moved to "Server Platforms".

Best of luck.

---

### Post by greenpeace on 2013-02-25
Hi!

Might be a silly question, but if you already have access over SSH, why do you need the VPN?

Configure your SSH server properly [1], particularly preventing root login, and tie it all down to keys, and it will make for a perfectly secure connection.

Perhaps you could explain in a little more detail why you need the VPN, and what you're trying to achieve?

Cheers!
Gp 

[1] [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by cotoman on 2013-02-25
well. the idea is that i HAVE to access using SSL but how can i do it while not on the same network and Machine B is not on global IP

---

### Post by greenpeace on 2013-02-25
Apologies, I had misunderstood :)

Are you able to run a SSH command from the remote box?  You could use that to set up a reverse SSH tunnel from machine A to machine B:

The command that needs to be run on machine B is then:

```
ssh -R <remote port>:localhost:<local port> <machine A's address>
```

The <remote port> should be any high number report (19999 for example).

Then, on machine A you can run the following to connect to machine B:

ssh localhost -p <remote port>

Hope that helps, check the article here for more information:
[http://www.howtoforge.com/reverse-ssh-tunneling](http://www.howtoforge.com/reverse-ssh-tunneling)

Cheers,
Gp

---

### Post by darkod on 2013-02-25
> **cotoman said:**
> well. the idea is that i HAVE to access using SSL but how can i do it while not on the same network and Machine B is not on global IP

I didn't understand this. Are you worried you will not be able to access a public IP from a machine with private IP?

Your private network usually has a public gateway as internet route access. This gateway will establish the connection to your server public IP.

Have you tried accessing the server with SSH and it doesn't work? Or you haven't even tried accessing it?

---

### Post by dwhitney67 on 2013-02-25
> **cotoman said:**
> so i have a server that has ubuntu 12.04. an it has public IP on it. and i access it from that IP so i cannot risk any IP change or anything that may interrupt the interface. i need to make SSH from server to my local computer. a VPN is not that easy to do on a local computer and if i set up a VPN on the server i risk that when i connect the interface will take the default gateway of the VPN so it won't have a connection. anyway any ideas on doing this it would be appreciated. here is a summary:
Machine A: public IP, not reachable but from ssh and VNC.
Machine B: local network, fully accessible 
Machine A must connect to Machine B using SSH somehow.
Machine A cannot risk any network interruption.

I do this all the time; I connect to my home server, using SSH, from a remote location (e.g. my office), and from there, connect to another system (at home), again using SSH.

I don't quite understand the issue you are having.

If you are unable to SSH to your Machine B, then perhaps you may want to investigate whether it is indeed running an SSH server daemon.

---

### Post by cotoman on 2013-02-26
> **darkod said:**
> I didn't understand this. Are you worried you will not be able to access a public IP from a machine with private IP?

Your private network usually has a public gateway as internet route access. This gateway will establish the connection to your server public IP.

Have you tried accessing the server with SSH and it doesn't work? Or you haven't even tried accessing it?

the problem is the way around, i want to access my private IP from the public. it is a matter of license, i cannot risk a license on the server if it won't work. i want to try the licensed software issues on my computer since it has the license. if it works i buy it for my server.

---

### Post by cotoman on 2013-02-26
> **dwhitney67 said:**
> I do this all the time; I connect to my home server, using SSH, from a remote location (e.g. my office), and from there, connect to another system (at home), again using SSH.

I don't quite understand the issue you are having.

If you are unable to SSH to your Machine B, then perhaps you may want to investigate whether it is indeed running an SSH server daemon.

the problem is, in my country, one public IP is for like 100 people. how can i set a SSH server on my private home, if i cannot access it from outside the network.

i was thinking of teamviewer on both PCs and make a VPN connection from it, less headache i think. this way i can definitely make SSH.

---

### Post by darkod on 2013-02-26
> **cotoman said:**
> the problem is, in my country, one public IP is for like 100 people. how can i set a SSH server on my private home, if i cannot access it from outside the network.

i was thinking of teamviewer on both PCs and make a VPN connection from it, less headache i think. this way i can definitely make SSH.

Are you sure so many users share the same public IP? For that, you would have to have the same common public router for all users.

In that case, Teamviewer to connect directly to your workstation (or server) sounds like the best solution.

---

### Post by dwhitney67 on 2013-02-26
> **cotoman said:**
> the problem is, in my country, one public IP is for like 100 people. how can i set a SSH server on my private home, if i cannot access it from outside the network.

i was thinking of teamviewer on both PCs and make a VPN connection from it, less headache i think. this way i can definitely make SSH.

In my country, internet subscribers are assigned a unique IP address (some permanent, others temporary) when they connect to the internet.

At home, I am connected to the internet 24 hours a day, via my cable modem, however that does not guarantee that I will remain with the same IP address all the time.  To work around this potential problem, I rely on the use of a Dynamic DNS client (ddclient), and an account at DynDNS, for my primary server.

My cable modem (which also serves as a router), not my server, is assigned the unique IP.  I have the router forward packets arriving on port 22 (SSH) to my server, which I have assigned a fixed-IP address (e.g. 192.168.1.xxx).

If you do not have a fixed IP address assigned to your home/business, then perhaps you should consult with your internet provider in acquiring one.

---

### Post by aerokid240 on 2013-03-06
Look into hamachi. Perhaps it might help you achieve what you want.

---

