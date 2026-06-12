---
title: "ssh tunnel to Virtualbox windows remote desktop - through ubuntu host"
date: 2011-10-08
forum: Virtualisation
---

### Post by manco1911 on 2011-10-08
Hi guys, im trying to implement a new project which requires to have access to a remote desktop on windows. 
But the idea is to not have this windows box directly connected to the web. 
So one thought was this:

Have Ubuntu (probably 10.04, desktop?) as a host for VirtualBox. And windows installed on VB (guest). 
And the path would be, access ubuntu through SSH tunnel, and access the remote desktop service of the virtual windows. 

First of all, is this possible?
if it is, some idea where to start? Im not looking for a complete tutorial or howto, but an indication where to start searching to accomplish this.. 

Thanks in advance guys

---

### Post by Dangertux on 2011-10-09
Yes this should be very easy, in fact it's no different than setting up a regular ssh tunnel 

example 

```

ssh user@host -p 22 -D 4141

```

so host is your ubuntu box and user is the username assuming openssh server is running on port 22, and you want to open an SSH listener on port 4141 on the guest machine.

Now the only trick to this working is that the guest machine has to be on the same network or have access to the Ubuntu host, so you would have to have the guest either bridged or NAT'ed to the host.

Hope that helps.

---

### Post by HermanAB on 2011-10-09
Hmm, you need not encrypt RDP with SSH, since RDP is encrypted already. Double encryption will slow it down. Just forward port 3389 to the Windows machine.

---

