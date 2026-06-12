---
title: "ubuntu server eucalyptus virtualbox issue"
date: 2010-03-11
forum: Server Platforms
---

### Post by misterjinx on 2010-03-11
Hey all,

I'm trying to build my own private cloud and for that i chose ubuntu server (which comes directly with eucalyptus). For that, I installed first the cluster on my laptop machine. everything was fine. After that i had to install again on another computer, for the node. At this stage i chose to install it on a virtual box on my host pc, which is a windows platform. The installation was successful after the 2nd shot. 

Now I came to the point where I have some problems. I have to register the nodes, but there's a problem when I run the following command on my cluster:

```
sudo euca_conf --no-rsync --discover-nodes
```I get the following error:
```
Failed to resolve service 'Eucalyptus cluster controller' of type '_eucalyptus._tcp' in domain 'local': Timeout reached 
```followed by some other lines.

I don't know why I'm getting this error. Can anyone of you help me with this problem ? I really have to build this environment :(

Thank you.

p.s. i don't know if it's related with the fact that it's installed on virtualbox, but i had to do it like these because i don't have another machines to test on.

---

### Post by madmaxo on 2010-03-26
Virtualbox doesn't allow incoming connections to a guest by default I think. it's a bit fiddly setting this up but you'd have to look into bridging vbox's network adapter with your physical network adapter, or editing your vbox machine config file to allow access to certain ports.

---

### Post by guessswh0 on 2010-03-26
Also, how is your VM connecting to the network?  Via NAT or a bridged connection?

Use bridged

---

