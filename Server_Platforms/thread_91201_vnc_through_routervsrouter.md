---
title: "*vnc through routervsrouter?*"
date: 2005-11-16
forum: Server Platforms
---

### Post by kruz on 2005-11-16
hello, i have a pc that i can connect to that doesnt have restrictions
ie a server lol
but the pc i want to connect to (my home pc)
is behind my neighbors firewall
built in on his dlink router

question is
is there a way to use liek reverse netcat  to use vnc??
any possible methods to do so?
any ideas would help me figure this out
thanx!

---

### Post by grendelkhan on 2005-11-17
Have him open up port 5901 and forward it to the pc running vnc.

---

### Post by nagilum on 2005-11-17
If your neighbour doesn't want to open a port you can use ssh's port-forwarding feature. Look for the -L and -R switches in the manpage.

---

### Post by kruz on 2005-11-17
thanx nag that helps

and yes i dont have port forwarding from him
he doesnt know im using it


thank you ill try this and get back
also heard u can acheive this via netcat

using listenin on ur server with open ports
then blah ill look around with ssh and see here though

btw after i get ssh setup can i run vnc through that tunnel?

---

### Post by nagilum on 2005-11-18
Netcat wasn't designed for this kind of work, it just creates TCP connections, either as client or server. But even if you find a way to do this, netcat has no encryption and authentication mechanisms. SSH really is the better way IMHO.

[QUOTE=kruz]btw after i get ssh setup can i run vnc through that tunnel?[/QUOTE]
Sure, I do this myself a lot. Once you have the SSH tunnel open you can run anything through it you want.

---

### Post by kruz on 2005-11-19
then how do i ssh behind a router??
check this

i can ssh to my windows 2k3 server thats on dmz host so all ports are forwarded
then i got a firewall which forwards whatever port i want to the host

i log into this computer, from a computer behind a router
that wont forward any ports, since its not mine

how do i go open connecting the win2k3 server, and from there, can i connect back to here???my ubuntu machine??

any ideas?

because i wana use remote desktop to connect to my win2k3 from out of town ect. then to my ubuntu machine 
ideas?

---

### Post by nagilum on 2005-11-20
Since your neighbour's firewall doesn't allow any incoming connections the only solution is to ssh from the inside (i.e. your home machine) to the win2k3 server. When you connect to your windows machine in the DMZ you could create 2 ssh tunnels, one for VNC and another one for SSH itself to be able to login on your machine at home.

For example connect from home to the windows PC with this:
```

$ ssh -R 10022:hostname:22 -R 5901:localhost:5901 hostname

```
where 'hostname' is the hostname of the windows machine. It will open 2 ports on it, 10022 and 5901 (last one only on localhost, so it's closed to the public and no one can use it without logging in first). When you ssh to your windows machine using port 10022 you will automatically be forwarded to your home PC and actually connect to that one.
To VNC to your home machine from a third computer you have to ssh to your windows machine first, i.e. 'ssh -L 5901:localhost:5901 hostname' where hostname is again your windows machine's one. Then you can tell VNC to connect to localhost on that 3rd computer.

Hope this all was more or less clearly described... ;)

---

