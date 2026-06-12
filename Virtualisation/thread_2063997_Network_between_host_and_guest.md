---
title: "Network between host and guest?"
date: 2012-09-28
forum: Virtualisation
---

### Post by Rytron on 2012-09-28
Hi.

Is there a straight forward way to ping a guest VirtualBox machine from my main host OS?

For example. I setup a manual IP address on my host and guest OS's. What network adapters could be used?

I'd also like to try something like this: [Send messages between 2 Ubuntu PCs (Net Send Style)]("http://askubuntu.com/questions/31582/send-messages-between-2-ubuntu-pcs-net-send-style")

Thank you.

---

### Post by idlemind324 on 2012-10-02
By default the VM should be configured with NAT. You will either need to do some port forwarding to make what you want to do possible.

Otherwise possibly the easiest method would be to switch your VM to bridged mode and select the appropriate local adapter on the host to bridge to. This will make the VM appear to connected directly to the same network as the bridged adapter. It would get it's own IP from DHCP or you could assign it one. You would then be able to access your VM from the host or any machine on the network by the IP it was assigned (either by you or DHCP).

You would then be able to try that askubuntu post.

Have fun!

---

### Post by Rytron on 2012-10-03
> **idlemind324 said:**
> By default the VM should be configured with NAT. You will either need to do some port forwarding to make what you want to do possible.

Otherwise possibly the easiest method would be to switch your VM to bridged mode and select the appropriate local adapter on the host to bridge to. This will make the VM appear to connected directly to the same network as the bridged adapter. It would get it's own IP from DHCP or you could assign it one. You would then be able to access your VM from the host or any machine on the network by the IP it was assigned (either by you or DHCP).

You would then be able to try that askubuntu post.

Have fun!

Works fine. I had to be online for it to work. The wireless router was the middle man.

---

### Post by markbl on 2012-10-03
A better way is just to change the host network adapter to "host only", or create a second one of this type if you still want external access from the host. Then the host and guest will be on their own private network. Nothing to do with your home lan.

---

### Post by Rytron on 2012-10-04
> **markbl said:**
> A better way is just to change the host network adapter to "host only", or create a second one of this type if you still want external access from the host. Then the host and guest will be on their own private network. Nothing to do with your home lan.

Thanks for the tip. :)

---

