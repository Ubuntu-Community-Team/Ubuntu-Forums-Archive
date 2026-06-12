---
title: "ubuntu 16.04 iscsi no portals found"
date: 2017-10-19
forum: Server Platforms
---

### Post by alexbrans on 2017-10-19
Hello All,

  This one has me pulling out my hair in frustration. I am trying to mount a volume (dell equallogic san) to ubuntu using iscsi

iscsiadm -m discovery -t sendtargets -p 10.0.0.10 gives me no portals found.

Thinking it may have been an acl issue I ran

tgtadm -lld iscsi --op bind --mode target --tid 1 -I ALL

--that gives me tgtadm: failed to send request hdr to tgt daemon, Transport endpoint is not connected

iscsiadm -m node ...gives no records found

I must have missed a step but have gone over everything and it appears that it should be working.

Can anyone please help?

---

### Post by darkod on 2017-10-19
Can you telnet the target from ubuntu? Don't remember the port now but look it up. First check connectivity is working from the ubuntu to the iscsi target.

---

### Post by alexbrans on 2017-10-19
Yes I can telnet into the san from ubuntu and obviously ping is successful

---

### Post by darkod on 2017-10-19
Are you sure targets are published? Can you try if another computer on the network can see them?

Just to make sure, you are trying to telnet to port 3260 (the default iscsi port), right?

Because you seem to be using the correct iscsiadm command. It should work unless there are communication issues or problems with the targets on the host.

---

### Post by alexbrans on 2017-10-19
when I first did telnet and it connected I did not specify port 3260. Now doing that it connects and then 20 seconds later 'connection closed by foreign host'. So it appears there must be some communication issue

---

### Post by darkod on 2017-10-19
Telnet is mainly used for testing specific ports (services). If you don't specify a port it doesn't know which service on the target you want to test.

Double check the cabling and network connectivity to make sure all is good.

If you have another windows or linux computer in the LAN it is worth checking if it can connect to iscsi target to make sure it works.

---

