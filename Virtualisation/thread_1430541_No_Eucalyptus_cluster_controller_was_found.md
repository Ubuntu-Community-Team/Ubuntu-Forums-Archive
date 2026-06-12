---
title: "No Eucalyptus cluster controller was found"
date: 2010-03-15
forum: Virtualisation
---

### Post by uwannawhat on 2010-03-15
I have gone through the process;
Install Ubuntu Enterprise Cloud
on the cluster controller and now installing on the node machine.

I'm following the instructions from this site:

[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

During the installation on the node machine, this message is displayed,

"No Eucalyptus cluster controller was found on your network,..."

The network environment here is a 10-space with many subnets.
There are two subnets for my building, one is dhcp controlled and the other is not.
These two subnets begin with 10.8.x.x.

What could be the problem and what should I try?

Thanks.

---

### Post by clotterm on 2010-03-17
Well, it really depends on your network configuration. The NC and at least one nic need to be set up in the same subnet. It would be easier if you'd post your ifconfig both of your NC and your CC and describe your network infrastructure a little more in detail.

---

### Post by yogesh.girikumar on 2010-05-06
Hi,

On the cluster controller, can you check if the services eucalyptus-cc-publication and eucalyptus-cc-publication-ip are started and running. They broadcast/ announce their presence over the network.

[HTML]$ sudo status eucalyptus-cc-publication
$ sudo status eucalyptus-cc-publication-ip[/HTML]


Let me know what happens..

---

### Post by sunder.srv on 2010-05-12
Hi all, Even we are getting the same problem. We tested the command "sudo status eucalyptus-cc-publication" , eucalyptus-cc-publication is running, but eucalyptus-cc-publication-ip is reported as an unknown job.

---

### Post by yogesh.girikumar on 2010-05-12
Hi,

eucalyptus-cc-publication-ip need not necessarily run always. What matters is eucalyptus-cc-publication. It broadcasts it's existence.

Your problem could happen if the node did not get registered on the CC. So do the following in the terminal on the CC and see if the nodes get registered.
```

$ sudo euca_conf --discover-nodes
$ sudo euca-describe-availability-zones verbose

```

Please make sure all the networking configurations are set up right. Here's a link to a simple Eucalyptus Guide. You might also find it useful.

[http://cssoss.wordpress.com](http://cssoss.wordpress.com)

Let me know what happens.

---

### Post by sunder.srv on 2010-05-14
Hi, 
        ya we did wat u said. But we are getting zeros in the free/max field in response to "euca-desacribe-availability-zones verbose". 
  
       Also we tried to register the nodes again. But nothing new turned up :(

       Please help us.

---

### Post by mjo_se on 2010-05-15
Hi. I think I had the same problem.

This is what I did to solve the problem:
- de-register the node
- de-register the cluster from command line (web GUI re-registration gave same problem)
- restart the cluster controller and the cloud
- register cluster again
- discover node and add it

See [http://open.eucalyptus.com/forum/node-controller-not-registering](http://open.eucalyptus.com/forum/node-controller-not-registering) for full details.

I hope this helps

---

### Post by sunder.srv on 2010-05-19
Hi mjo_se,
             Its working:) Thanks a lot.:)

---

