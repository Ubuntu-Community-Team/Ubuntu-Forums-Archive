---
title: "How to run a Centos LXC guest in graphical mode?"
date: 2011-01-03
forum: Virtualisation
---

### Post by Nighthog on 2011-01-03
Hi folks.  On a 10.04.1 host I have created Centos LXC guests from the OpenVZ template centos-5-x86.tar.gz and have them running; I can SSH into them via Putty and I've also got them talking to the outside world over a bridged network.  So far so good for server-type apps.

What I want to do though is run graphical apps such as Eclipse on one of the guests - I'm at a loss to know how to do this.  I'm sure more knowledgeable people must have done this - 

Can anybody help me out here, please?

---

### Post by bodhi.zazen on 2011-01-03
You can use ssh -X to forward X applications.

You can use VNC for a desktop.

You can use Xephyr 

[http://ubuntuforums.org/showthread.php?p=3816948#post3816948](http://ubuntuforums.org/showthread.php?p=3816948#post3816948)

You can use web biased applications such as webmin to manage servers.

There are reports of assigning a VT to the guest, I have not tried that, not sure how well it works, if at all, you could ask on the LXC mailing list.

With all that in mind, if you want to run graphical applications I would try an alternate option (VBox or KVM).

---

### Post by Nighthog on 2011-01-04
Thanks, Bodhi.

I was coming to the conclusion that I should use a different virtualization method for a graphical UI but I'd prefer not to use VMWare.  You suggest KVM or VirtualBox - is there a preference between these for running a Centos guest?  They're both new to me.  If anyone has hints & tips for running Centos under either of these I'd be glad to hear!

Thanks -
Cliff

---

### Post by bodhi.zazen on 2011-01-04
> **Nighthog said:**
> Thanks, Bodhi.

I was coming to the conclusion that I should use a different virtualization method for a graphical UI but I'd prefer not to use VMWare.  You suggest KVM or VirtualBox - is there a preference between these for running a Centos guest?  They're both new to me.  If anyone has hints & tips for running Centos under either of these I'd be glad to hear!

Thanks -
Cliff

If you want better graphical integration (mouse and copy-paste form host to guest) use VirtualBox.

Personally I use KVM.

---

