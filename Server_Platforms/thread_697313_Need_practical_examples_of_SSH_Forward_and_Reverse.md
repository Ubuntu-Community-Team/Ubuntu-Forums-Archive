---
title: "Need practical examples of SSH Forward and Reverse Tunneling"
date: 2008-02-15
forum: Server Platforms
---

### Post by kevdog on 2008-02-15
Whats the difference between ssh reverse and forward port tunneling?  Can someone give me some concrete examples?  I understand the idea of tunneling ports -- I am just confused about forward vs reverse.  I usually use the forward mechanism. When would I need to reverse the tunnel.

---

### Post by croto on 2008-02-15
Check out this thread. It may answer your question.

[http://ubuntuforums.org/showthread.php?t=694439](http://ubuntuforums.org/showthread.php?t=694439)

---

### Post by kevdog on 2008-02-15
Thanks for the reverse tunneling link.  What is a good explanation however of a forwarded vs reversed tunnel?

---

### Post by faulkes on 2008-02-15
> **kevdog said:**
> Thanks for the reverse tunneling link.  What is a good explanation however of a forwarded vs reversed tunnel?

Lets change up the terminology a bit to better match.

ssh supports two modes of port forwarding, a local port forward and a remote port forward.

1. Local Port Forwarding
- A local port forward means that port XYZ is forwarded from the local machine to port WQY on the remote machine.  

An example might be forwarding port 6000 (X windows) on the local machine to port 6000 (X windows) on the remote machine.  
This would in effect make it appears as if the user was local to the remote machine.

2. Remote Port Forwarding
- A remote port forward means that port ABC is forwarded from the remote machine to port DEF of the local machine.  
This works in as expected, the opposite way of a local port forward.  

An example might be forwarding port 5060 (sip) on the remote machine to port 5060 (sip) on the local machine.  
External users connecting to port 5060 on the remote machine would in actuallity be connecting to port 5060 of 
the local machine.

In both cases, ssh port forwarding will bind to the loopback address unless an ip address is bound.

Each of the above is explained with greater detail in the ssh manpage (-L and -R options).

Faulkes

---

