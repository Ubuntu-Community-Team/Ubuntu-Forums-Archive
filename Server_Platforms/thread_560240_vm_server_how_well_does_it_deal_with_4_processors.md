---
title: "vm server how well does it deal with 4 processors"
date: 2007-09-26
forum: Server Platforms
---

### Post by twistedtwig on 2007-09-26
Hi all,

I have a compaq proliant server which has 4 550mhz processors with 500MB cache on each with 1.5GB of ram.  I was wondering how vm server deals with multiple processors.  None of them are that powerful on their own but together they are not bad.  

What I was thinking of having, if it will deal with it well.  

The base OS with VM server on would be ubuntu.

I would like to have a couple of VM servers running on it, one ubuntu server and one windows 2003 server.

do you think it would deal with all of this? or just maybe the 2003 server and the "base" OS does all the ubuntu stuff.

The reason for this is a few fold.

1) having them on VM should be very helpful for future movement and backing up.

2) the base OS is the firewall and the VM server and the just dishes out the other jobs to the vm servers.

Does this sound doable and or sensible?

thanks

---

### Post by veloce on 2007-09-26
Some notes:

ubuntu as base operating system is a good idea.  It's smp is hugely better than windoze.

We have a similar setup at work on a twin dual core machine.  ubuntu os acting as server to local network.  Second windows server running as a vm used for a different subnet. 

I also run a couple of other vms as workstations and these do not seem to impair performance. 

All the vms are set up as single processor machines and ubuntu's smp manages the processing.  This seems to work better than having vms as dual processor.

Good luck.

---

### Post by twistedtwig on 2007-09-27
I tried using a VM server about a year ago. although I didn't know much about it then.  I tried to install window 2003 on it and it ran like a DOG!  It only seemed to give it one of the processors 550MHZ and was just tooo painful.

I don't know if I did it wrong, choose the wrong version of VM server or something but it really didn't work.

I guess what I am getting at is, should I use VM server that has SMP or not worry? 

My other issue is because its an old compaq the highest rez is 800 x 600.  I have a comp that is running 2003 atm and could take the card out of there and see if it works.

Can I ask does your "base" Ubuntu OS do the DHCP and DNS?  I was thinking the base would only do the firewall and port forwarding and hold the VM's.  The VM ubuntu would do all the DHCP.

But how would I set up  the network then?  Could I setup vm server to use the same subnet my local uses but only in a range of say 192.100.5.1 - 192.100.5.20?  Then the DHCP could use 21 onwards?  Would they all be able to talk to each other?

I don't have another machine to be able to test this all on which is a real shame.  I do want to upgrade my server but funds wont allow this for a fair while yet.

Thank you for any and all advice

---

