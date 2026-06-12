---
title: "Synchronize users and passwords"
date: 2011-06-18
forum: Server Platforms
---

### Post by vikfreeze on 2011-06-18
Greetings,

i'm not sure if i'm posting this in the right place, so feel free to move it if not.

I have a Xen Server pool with multiple Ubuntu 10.04 Server gusts running on it.

On one guest i have an NX server where the clients login, NX uses the ssh authentication layer so the native users of the unix system are used. This guest also runs a Samba server witch has its own users database here is where my first issue pops up (#1) described below.

The other guest are worker nodes that run Matlab, Mathematica, etc...
The users use these nodes via X forwarding, from the NX desktop they run ssh -X [node ip] matlab for example.
For this to work the node must have the calling user and password in its system (for simplicity i want to have the same users and password on all guests) so the nodes must mirror the NX guests users.
Now this can be implemented as mentioned above(i've tried it and it works just fine), however im foreseeing a big problem if a user wishes to change his password,(#1) namely is a user uses passwd to change his unix password the NX login will reflect this but the Samba database won't, now if he uses smbpasswd to change the Samba password it can be rigged so the unix password is changed as well, but this still leaves all the worker nodes with the old password.

Can anyone give me some advice on how to make the user and password of the NX guest global. (i don't necessarily want a unique login, its fine if the user has to retype the password when connecting to a worker node as long as its always the same one)
Basically all i want is that if a use changes his unix password on the NX guest, Samba and all the worker nodes should reflect this change.

I have looked at Kerberos but unfortunately all i have is a private sub-network, a set of word wide IPs but **_no_** DNS.:(

Id appreciate any advice on how to manage these services with just the users database of the NX guest so i don't have to keep all of them manually synchronized.

Thanks for reading
Victor

---

