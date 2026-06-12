---
title: "Two network cards --- possible use?"
date: 2011-02-17
forum: Server Platforms
---

### Post by garfonzo on 2011-02-17
Hey Folks:

I just received a new server with two network cards on the motherboard. Now, I know that in certain scenarios, the two ports are used as a one-in and one-out situation so all network traffic is routed through the server. 

However, for me, this server is the *only* computer on the network. As such, is there benefit or scenario in which I could utilize both ports? 

The server is simply a remote file backup server, a web server, and a MySQL server. 

Thanks!

---

### Post by kevinthecomputerguy on 2011-02-17
I can think of hundreds, but you ruled out most by saying what they are for.
 
For your setup, you could make a service only listen on one nic, like samba or ssh. That way the public wan facing NIC would appear to not have anything but port 80 open, but then nic #2 can have admin services bound to it, without a known hostname or address.
 
A great use for this if your not going to turn this box into a router, is to bind samba or webmin to the second nic, so you can have the awesome-ness, bind it to that second interface, and not worry about locking it down, as it only listens on probably what is a lan facing nic.
 
The other great use is to set it up as a router. Then you can move your wireless router to a better room, and use it as an access point instead of a router.

---

### Post by garfonzo on 2011-02-17
> **kevinthecomputerguy said:**
> I can think of hundreds, but you ruled out most by saying what they are for.
 
For your setup, you could make a service only listen on one nic, like samba or ssh. That way the public wan facing NIC would appear to not have anything but port 80 open, but then nic #2 can have admin services bound to it, without a known hostname or address.
 
A great use for this if your not going to turn this box into a router, is to bind samba or webmin to the second nic, so you can have the awesome-ness, bind it to that second interface, and not worry about locking it down, as it only listens on probably what is a lan facing nic.
 
The other great use is to set it up as a router. Then you can move your wireless router to a better room, and use it as an access point instead of a router.

Thanks for the response. I was actually thinking of something like this. Perhaps have one nic *only* for port 80 for hosting the website, then the other nic *only* for SSH. 

The thing is, this is the only computer on the LAN, there are no other computers connected to the router so the question is, what does this accomplish? Since there are no other comps on the LAN, doesn't that mean that one nic for WWW and one nic for SSH is useless since *both* nics are looking at the internet?

---

