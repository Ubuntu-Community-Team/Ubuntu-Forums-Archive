---
title: "upstart: best practice questions"
date: 2010-05-11
forum: Server Platforms
---

### Post by HeinMueck on 2010-05-11
Hi all,

moving towards lucid and having upgraded my test system, I cant stop thinking the best practice using upstart and sysvinit together smoothly.

For instance, what is the best way to disable an upstart script? Edit it? Move it? Is there a nice way, leave it untuched but mark it disabled?

More complex:

I have some vm's running, the /etc/init.d/vmware loading the modules and setting up network interfaces. The main interface is natted. Samba only binds to that NAT interface, only accessible from inside the guest systems. 

Now samba has gone towards upstart and its up and running before the vm nat interfaces are available. Each time I realise the shares are missing I restart samba and its fine. 

I recon I could set an emit into the vmware initscript and handle this event in the samba upstart. But I dont like this idea, as it means that a future admin could decide to reconfigure the server, move the vm's somewhere else, using samba in a different way and wonder why samba wont start - just because my custom event will never get fired. And of course you cannot handle this kind of config from packages very well. I try to use custom deb's to configure my servers wherever I can. 

So I guess there is a better way, but for now I could not find it.Maybe a very late prerequisites-up event emitted by a late sysv init script could be a general solution - but I would need to customise the package maintainers upstart scripts - urgh! :)

Has anyone found a nice solution for this?

Cheers,
Hein

---

