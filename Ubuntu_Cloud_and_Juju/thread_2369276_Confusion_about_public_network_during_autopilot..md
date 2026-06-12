---
title: "Confusion about public network during autopilot."
date: 2017-08-21
forum: Ubuntu Cloud and Juju
---

### Post by michaelvdb2 on 2017-08-21
Hi All,

i've set up the juju/autopilot to have maas network = 10.60.1.x
tenant interface network =192.168.50.x
Both networks have a gateway that can reach internet.

Autopilot can see 3 nodes ready for deployment but for some reason says it has no public network.
All these 3 nodes have two network interfaces. One on the MAAS network. An another network.


Can someone explain clearly how do I setup the nodes to have public network.
I can't find any clear document to explain what this is. If you could point one out to me, I'll be grateful.

Thanks in advance.

Regards,

Michael

---

### Post by michaelvdb2 on 2017-08-21
Nevermind, finally figured it out.
The public interface, for some reason cannot be on the same maas interface. Don't understand why but seems to be allowing me to install the nodes.

---

### Post by tschuh on 2017-09-06
I have a similar problem but each subnet has its own physical interface.  I come from a VMWare/NSX world so my instinct is to put every interface on every host.  That appears to be completely wrong in the MAAS/Landscape philosophy.  I need to provide as much resiliency as practical so I'd think at least two hosts in the cluster with legs into the public network and all of them on the private network.  Landscape seems to disagree and the logs and forum posts I've seen so far aren't providing any useful information.  If someone can point me to clear and current documentation for best practice, particularly on Blade-based systems, I'd be very happy to RTFM.

---

### Post by michaelvdb2 on 2017-09-06
The problem with the landscape, it requires that you define IP ranges for each of your network interfaces.

Now the quirky problem is this
a) The maas network and its associated IP range can never be the public internet range.
b) So at least another IP range must be the internet range.
c) Even if you get pass this, the maas install, the individual machines will somehow route back some weird place for DNS on the maas network and it might fail to install because it cannot download stuff from the internet. That was another royal pain to resolve. Never understood how to properly deploy this landscape properly.
Eventually I gave up.

With that it then recognizes that there are two networks to work with.
Atleast I got that far. Never had enough ram on my esxi server to get it to install the 3 nodes for tests.

However, I was eventually given One development server with 128G of ram and fast drives.
Eventually, I went with Packstack-openstack. Then install juju on a vm node and bootstrap into the packstack-openstack.
Which requires you to setup simplestream partially on the ubuntu image with juju and partially on the openstack system (man it was not so simple :) pun intended)
That was royal pain to do. Now, finally its up and I can do "juju deploy mysql" and it spins up a mysql ubuntu image so it works. Juju gui works. 

Now I am learning juju charms to create my own production images.

---

### Post by cmccane on 2017-09-15
Is there another forum where people are discussing Ubuntu Openstack installation? The newest post I see here is a week old. 

Thanks,
Charles

---

