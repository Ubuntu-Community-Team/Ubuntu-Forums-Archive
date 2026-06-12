---
title: "ssh: remote logins fail until the first local login"
date: 2009-07-28
forum: Security
---

### Post by maitrebart on 2009-07-28
A friend of mine has a particular problem: any attempt to remote login using ssh will fail until he first logs in locally on his server. Then all ssh remote login work.

Anyone ever experienced this before?

---

### Post by The Cog on 2009-07-28
I think that gnome-network-manager doesn't set up the network until a user is logged in. It would be interesting to know if the server even responds to pings until a user has logged in locally - if not then I would definitely suspect that the networking hasn't been configured.

If it is a wired interface, you should be able to configure /etc/network/interfaces by hand so that it gets configured upon boot. Otherwise try replacing gnome-network-manager with wicd, which I know actively configures networking even when no-one is logged in yet.

If the server does respond to pings before local login then my theory is completely wrong and you will have to look for other reasons for your problem.

---

### Post by bodhi.zazen on 2009-07-29
My guess is that you are using an encrypted /home directory. When you are not logged in locally , $HOME is encrypted, and thus ~/.ssh/authorized_keys is not available.

When you log in locally, $HOME is un-encrypted and thus ~/.ssh/authorized_keys and thus you can log in.

If this is the case, simply edit /etc/ssh/sshd_config and set the authorized_keys to an alternate location, such as /etc/ssh/authorized_keys

Move (copy) the contents of ~/.ssh/authorized_keys to /etc/ssh/authorized_keys and re-start the ssh server.

---

### Post by maitrebart on 2009-07-29
Thank you very much guys.

The Cog: My friend's Ubuntu computer responds to http requests so it's not a network interface issue.

Bodhi: I'll communicate that to my friend.

---

### Post by swinnea on 2009-08-05
I was seeing similar effects on a system.  sshd only responded when there was a console login.  Print sharing also stopped working.  I also could not ping the box.

I'm using 9.04.  In the network manager I tried selecting the All Users checkbox.   That ended up keeping the network up at startup and after logging out. :)

---

### Post by maitrebart on 2009-08-05
I'm starting to think it could be a problem of iptable rules.
They might have a default setup at boot that fails ssh connections. Then once a console is started or the first user is logged in, some rules are changed and then sshd starts responding.

In a next test, I'll try comparing iptable rules before and after.

---

### Post by Rob_H on 2009-08-05
An easy way to verify that **sshd** is listening without logging into the box would be to run **nmap** on another computer and probe the port.

---

### Post by Tha-Fox on 2009-08-19
I have a similar problem here. My laptop has wireless network connection and I'm using the default network-manager in gnome. I'll try to switch that to wicd to see if it helps. Any other suggestions?

---

### Post by bodhi.zazen on 2009-08-19
I did run across this problem recently (well not exactly).

The issue may be with network manager.

Open network manager (RIght click on the network manager icon - > select "Edit Connections ..." )

Select your interface (eth0 , wlan0, etc). hit the "Edit" button.

In the next box make sure both "connect automatically" and "Avaliable to all users" are selected (there is a check in the check boxes).

The other option is to disable network manager and configure your network manually. If you need help with this let us know (it is easier with a wired connection, but can be done with wireless).

---

### Post by michelstpierre on 2009-11-20
Thank you maitrebart for starting this thread.  The problem I had was because my home folder is encrypted (as pointed out by bodhi.zazen).  I moved the keys to another folder (not encrypted) and everything works fine now; I can ssh without ever having to login locally. 
Thank you all!

---

