---
title: "virtual box and ip address"
date: 2010-06-11
forum: Virtualisation
---

### Post by mosaic2s on 2010-06-11
can one define the IP address for the guest OS?
will this give more power to the VM like printing thru network? or will it make the VM vulnerable to virus attacks?

---

### Post by TheFu on 2010-06-11
The host can only provide a MAC address. The client OS, just like a physical installation, is required to set the DHCP or static IP accordingly.  You'll also want to set bridged networking, not NAT in the vbox settings for the VM.

---

### Post by mosaic2s on 2012-05-30
yes. have used it with bridged networking but then it is susceptible to virus attacks.

thanks.

---

### Post by overdrank on 2012-05-30
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

