---
title: "SSH Help"
date: 2010-09-09
forum: Server Platforms
---

### Post by darms21 on 2010-09-09
I am trying to set up SSH from a windows machine to a linux box on my home server. Can any1 provide me with a thorough instruction set to perform this? I have found tons of article online but they all tell slightly different stories and I am looking for the full story including what I need to do my windows machine/linux box/belkin router. Thanks so much again to all for the time. It is very much appreciated.

---

### Post by Hobgoblin on 2010-09-09
Instructions for setting up the ssh server are [in the server guide](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html).

You'll need an ssh client on the Windows PC (Google "putty").

What else you need to do will depend on if the PC is in the same network as the server or you want to access it from the internet.

If you are both on the same network then just put the server IP address into putty and click open, then enter your user and password when prompted.

If you need to access it from outside then you will need to set up port forwarding on your router. This will depend on your router make and model. [this site should help](http://portforward.com/).  If it is to be accessed from the internet then make sure you (and all users on the system) have a strong password.

---

### Post by CharlesA on 2010-09-09
I prefer using keys instead of passwords if I have SSH exposed to the internet, since they aren't exactly able to be brute-forced.

As long as you have a strong (non-dictionary) password you should be ok.

In order to access the machine remotely, you'd have to configure port forwarding. Check out the site [here]("http://portforward.com/") for more info.

---

### Post by aeiah on 2010-09-10
one thing no one has mentioned is that you of course need to have the ssh service installed and running on your linux box ;)

if we are talking about accessing this over the internet, then you should probably change the default port too, but you can cross that bridge after getting it working.

install with:
```

sudo apt-get update
sudo apt-get install openssh-server

```

start the ssh service with:
```

sudo service ssh start
```

for setting up an sshkey, you basically want your windows public key to be placed on your ubuntu box. putty will be able to generate a key for you i would think. it'll generate a key pair, one private, one public.. move the public one onto your ubuntu system.

- move it into ~/.ssh/
then issue the commands:
```

cd ~/.ssh/
cat windows.pub >> authorized_keys

```

where 'windows.pub' is the name of your windows public keyfile.

you'll now be able to log in from this windows box to your ubuntu box without providing a password. this is convenient on local networks, and offers more security over the internet once you turn off password authentication in your ssh server config (so only computers with your windows private key can access the ubuntu server over ssh).

---

### Post by darms21 on 2010-09-10
I tried entering my routers IP address in PuTTy but I keep recieving the error "Connection Timed Out." Any ideas?

---

### Post by aeiah on 2010-09-10
well its probably a port forwarding issue. port 22 (if using the default for ssh) needs to be forwarded on the router to your ubuntu server.

i assume you're going over the internet, yes? and that by 'routers ip' you mean the external IP address that the world sees? (just find it with whatsmyip.org)

if you're on a local network you want to be going directly to your ubuntu machine's IP number.

---

### Post by darms21 on 2010-09-10
My setup is: a windows laptop and a linux server on the same network behind 1 router.

---

### Post by aeiah on 2010-09-10
in which case, you dont (and indeed, shouldnt) open up port 22 on the router. inside your network, you should have access to this anyway. opening and forwarding port 22 onto your ubuntu machine is only necessary if you want to access it from over the internet, and carries the extra weight of security issues associated with having something available on the net.

to find out the IP address of your ubuntu server either look on your router's control panel, or on the ubuntu command line, issue:
```

ifconfig

```

this should provide you with your IP address. it'll probably be something like 192.168.0.2

if you've got the ssh-server service running on the ubuntu box you should be able to log in on the windows box without needing to touch the router

---

### Post by CharlesA on 2010-09-10
Can you ping the ubuntu box from the laptop?

---

