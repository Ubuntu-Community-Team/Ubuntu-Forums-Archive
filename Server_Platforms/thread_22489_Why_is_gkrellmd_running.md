---
title: "Why is gkrellmd running?"
date: 2005-03-28
forum: Server Platforms
---

### Post by TheOtherShoe on 2005-03-28
A little while ago I installed gkrellm in Hoary to look at my network transfer rates. I didn't mess with the configuration at all and I haven't used it since. Just today though I was looking at some discussions on Ubuntu security, so I ran nmap on my machine, the external interface as well as the loopback, and found to my surprise gkrellmd running and listening on an open port:

19150/tcp open  gkrellmd

I checked my /etc/rc* listings and found that gkrellmd is listed in every runlevel. The /etc/init.d/gkrellmd script was installed by, unsurprisingly, the gkrellmd package; but I don't know where the rc* listings came from.

So my question is, might it be a security risk to set up a new network service without notifying the user? And how did those rc* entries get there anyway?

---

### Post by alastair on 2005-03-28
It looks like it's part of the install ....

When packages are installed, it is always worth looking at the install/config output - you can see what happens and what services might be stopped/started. You would have seen this.

In "synaptic", there is a "terminal" you can look at to see this.

To remove a service :

/etc/init.d/<service> stop
update-rc.d -f <service> remove

But ... watch out for them being turned ON again if they are updated/upgraded.

---

### Post by localzuk on 2005-03-28
Gkrellm allows a user to monitor a remote system as well as a local system. So in order for the remote system monitoring to work, it has to have an open port.

If you don't want remote monitoring ability, then you should be able to remove the rc.d services.

---

