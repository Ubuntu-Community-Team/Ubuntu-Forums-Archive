---
title: "Ubuntu server ping hostname"
date: 2011-06-15
forum: Server Platforms
---

### Post by rothux.j on 2011-06-15
**UNSOLVED - APPEARS TO BE ROUTER'S FAULT, NOT SERVER. PLEASE FEEL FREE TO CLOSE THREAD**

Good evening,

I'm having a problem with pinging my server by hostname.
I have a router, and Ubuntu Server connected. Also connected to the router are my "clients". These clients don't need to be a part of the domain or anything, and they receive their network address and internet connection from the router.

I set up server, and my client was able to ping the IP and the hostname perfectly fine, with no configuration on the client side - no editing the hosts or anything.

However, I wrote a script while I was tired and ran it as root, erasing a lot of stuff. Unbootable.
I reinstalled the server exactly the same as before, but this time used a different IP (192.168.1.66 instead of ...65). The ubuntu server can ping the mac (rothmac.home) whilst the mac can't ping the server (rothux.local). Both can ping each other's IPs.

The idea of this system is to allow multiple clients (a lot) to join - not just the mac. But I need to have this set up properly before I introduce the other clients. Without another machine to test on, is this likely to be the mac "remembering" the previous rothux.local server? Or possibly the router's fault? Obviously, I have powercycled the router, rebooted the server and the mac, after multiple server configurations...

The only way I managed to get the mac to ping the hostname was by editing its hosts file, but this shouldn't be necessary (proven with my previous setup - the DNS is provided by the router, along with DHCP) and is also impractical when I won't have access to all the client machines.

Sorry for the long-winded post. Thanks for any pointers. I'm assuming it is the mac's fault to be honest.

---

### Post by CharlesA on 2011-06-15
What ip is the hostname resolving to when you try to ping it from the mac?

---

### Post by rothux.j on 2011-06-15
With the hosts file changed on the mac, it resolves correctly to 192.168.1.66
Meanwhile, when I take rothux.local out of the hosts file, it waits for a short period before:
**ping: cannot resolve rothux.local: Unknown host**

Something odd I have noticed; if I ping rothux.local and get the unknown host, there is a pause before it returns the error. Meanwhile, if I ping something like, rothux.home however, there is zero pause.

I've tried to flush the dns on the mac, taken it away from the router, removed its connection settings and then put back in and even set a second dns server as the ubuntu server's IP (which I don't want to do) and that didn't work either.

Confusing.

Could the ubuntu server possibly not be pushing its information up to the DNS on the router? Obviously in set-up it used DHCP, so maybe it might not be updating?

---

### Post by CharlesA on 2011-06-15
It definitely sounds like DNS isn't being updated correctly.

---

### Post by rothux.j on 2011-06-15
Any idea if there is a way of forcing my server to send its details to the DNS?

---

### Post by CharlesA on 2011-06-15
Check what ip the router thinks the server has and go from there.

---

### Post by rothux.j on 2011-06-16
The router appears to have the correct name (rothux.local) on the correct ip (...66).
To that end, I really am assuming that it is a mac problem... I'm going to borrow someone's computer and try it out. Will update for working/not.

---

### Post by CharlesA on 2011-06-16
It's probably because the mac is using .home and the server is uing .local.

---

### Post by rothux.j on 2011-06-17
Nah, that doesn't affect it: like I said, using exactly the same hostnames, it worked.

I loaded a windows client up and attempted, and it failed with the same message.

I think that I am going to cut my losses on this one, and rename the server to roth.local instead - hopefully this will work.

I'm considering this as unfixable, and guessing on the router.

**UNSOLVED - APPEARS TO BE ROUTER'S FAULT, NOT SERVER**

---

### Post by CharlesA on 2011-06-17
What sort of router is it?

---

### Post by rothux.j on 2011-06-17
A cheap one from BT... I'm going to replace it with a cisco, because they work. Thanks for trying CharlesA

---

### Post by CharlesA on 2011-06-17
Before you replace it entirely, try to reset it to system defaults and see if it works.

---

### Post by rothux.j on 2011-06-18
Well, I changed the hostname of my box to rothnet.local and gave it a different IP. Hey presto, it works.
Now that it works, I'm reluctant to go back to a state of unworking haha.
Cheers for the help.

---

### Post by CharlesA on 2011-06-18
Hahaha. Glad you got it working.

So strange.

---

