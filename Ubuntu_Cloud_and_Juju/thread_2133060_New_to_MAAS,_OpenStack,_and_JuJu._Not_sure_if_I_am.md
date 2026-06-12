---
title: "New to MAAS, OpenStack, and JuJu. Not sure if I am doing the right setup."
date: 2013-04-06
forum: Ubuntu Cloud and Juju
---

### Post by drifter666 on 2013-04-06
Hi Everyone,
I've been tasked by my employer to setup Drupal server with as much redundancy as possible. The old Drupal server got corrupted and a hard drive failed. I rebuilt a new ubuntu server and got everything back up. But now they are uber paranoid so they want to mitigate as much fault as possible. I know cloud won't stop corruption but we have backups in place. This is all about fault tolerance and scalability. Plus if I can get other uses of these brand new servers by using cloud, all the better. These servers are pretty overpowered to just be running Drupal alone.

So my linux server choice has always been Ubuntu, so I start googling how to cluster ubuntu server. A lot of things I've read was pointing to use MAAS, JuJu, and OpenStack. I think my wires are being crossed here or being short circuited. 

So my simple question is, as I continue to setup MAAS, JuJu, and OpenStack will things become more clearer on what I'm doing to setup the webserver like I would normally do on a single Ubuntu install?

Right now my head is exploding with sooo much new information. Currently, I got my 12.10 server setup with MAAS configured with 2 nodes in the ready state. Am I right in saying that the MAAS configuration is done? Where do I go from here? The good thing is I have time to play. I know this is going to be key to get used to what JuJu and OpenStack do. Should I use JuJu to be installing OpenStack? Is OpenStack going to be controlling the 2 nodes in the ready state? 

Sorry for the newbie questions but if someone can just say, "Keep going with the configuration. It'll all make sense once you install OpenStack through JuJu." or correct me to point me in the right direction.

Thanks.

---

### Post by castrojo on 2013-04-09
You might be overkilling it with OpenStack if you only need 2 nodes, but generally speaking you're heading in the right direction. 

What OpenStack will allow you to do is have a generic cloud that you can deploy other services on top of, so if you plan on adding more services in addition to drupal then that'll be the way to go. There's a drupal and mysql charm, though the drupal charm doesn't look production-ready to me (I'll ping someone to check it out). The mysql charm is awesome though, and it should enable you to set up a resilient db deployment. 

The hardest thing you'll have to figure out when moving to a cloud deployment is how to think about services instead of machines and webservers. So instead of manually setting up drupal and mysql you'll just tell juju to deploy those two things and connect them together, and it'll do the heavy lifting.

EDIT: It only seems hard because you're setting up a private cloud at a small scale; so all the hard work is frontloaded, but once you're up and running when you want to expand you can just add nodes very easily.

---

### Post by castrojo on 2013-04-09
Also feel free to fill out the Juju survey to tell me what sucked about the set up: [http://www.surveymonkey.com/s/ubuntu-juju](http://www.surveymonkey.com/s/ubuntu-juju)

---

### Post by TheFu on 2013-09-11
If you only have 2 physical servers, OpenStack is overkill and much more complexity that needed.  For anything under 50 physical servers, I would stay with a KVM + libvirt + virt-manager setup. The openstack effort just doesn't pay off for less ... unless you WANT TO LEARN the technology (add to your resume). 

Redundancy can be added in many different ways - expensive server hardware, cheap, but redundant hardware with logical redundancy, DNS redirectors, reverse proxies that load balance, plus near-real-time DB replication. Cheap SAN for storage.

I would use some tool like Ansible, Rexify, Puppet, Chef ... to manage more than a few nodes, however.

Having great backup processes is something you've already covered, so the next step in my mind is to use RAID1 or RAID10 disks and a reverse proxy for load balancing.  If a front-end server needs to be updated, it can be pulled from service.  If not iSCSI, check out AoE ... if your budget doesn't support the larger storage vendor solutions.

I should also say that I'm a drive-by commenter in this sub-forum. I know little about juju, but I hear war stories from my business partners about OpenStack deployments at client locations.  They've been working a 1000+ physical node deployment for over a year - design, prototype, deploy, policies, network architecture, CMDB, redundancy, etc.  

Anyway, I thought I'd provide a different perspective.  I run the internal systems for our consulting company and we use KVM+libvirt+virt-manager. It is too easy this way.

Hopefully, by displaying my ignorance, someone will provide counter arguments that lead you to the best possible solution.

---

### Post by Joseph_Motacek on 2014-01-21
> **TheFu said:**
> For anything under 50 physical servers, I would stay with a KVM + libvirt + virt-manager setup. 

When I started looking into this I started thinking the same thing for small private deployments.  OpenStack plus MAAS seemed like a bit much when MAAS alone can use Juju charms.  I'm curious though (as a newbie to this) how one would setup the deployment you mention "KVM + libvirt + virt-manager".  

Better yet what would be the best way to start given the deployment mentioned by the OP.  He has two servers but lets say he wants to start with MAAS to maintain the ability to be scalable.  Would you want to install Ubuntu Server on the hardware then KVM + libvert + virt-manager then use virtual machines created in that server to create your MAAS master and subsequent nodes?  Would this kind of virtualization be recommended?  It's just difficult to understand the best course of action when you want to start small but leave your self room to grow.

---

### Post by TheFu on 2014-01-21
virt-manager is only needed on the/any remote, management desktops, not any of the KVM hosts.  For a small infra setup, KVM+libvirt+virt-manager is easy.  [http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization](http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization) There must be 2,000 different ways to accomplish this. 

It is impossible to achieve the "best course" of action since the future is unknowable. I just try to do the best I can, with the information, time and resources available.  When I was younger, I thought 95% of the folks who came before me were idiots. Clearly, they made terrible choices and I was having to live with those. As I gained more experience, I learned they were all pretty smart and working within the available options.

* nobody has all the knowledge or skill they need the first time through any solution
* tools and features change over time, sometimes drastically.
* requirements are never static. Marketing is great at leaving out HUGE things.

I'd also point out that I've never used juju anything.  Ansible meets my current needs for automation, takes about 15 minutes to get going and doesn't care if I'm on Ubuntu, Debian, CentOS, Fedora, RHEL, Zoran, whatever ... or not. I prefer to understand as much as possible about things running on my systems.  Anything that looks like "magic" concerns me.  Network-manager drives me crazy!  Settings determined by others scare me, especially for internet-facing services.  After all, I don't deploy with the default sshd_config, so how could I expect any other config to be close to my needs?

For my needs, juju is just too new for consideration.  I've seen enterprises completely stagnant after deploying complex "management tools" because the admins lost track of what the real goal was and their scripting skills withered. The guy that setup everything tends to leave and nobody else will touch it to avoid causing an outage. That's fine for 6 months, then being out of patches becomes a HUGE issue.  

I'm confident that Ansible will scale to 500+ nodes, 10,000 nodes in the future, but is simple enough understand in 15 minutes and run just 1 node.  Talk to people using tools like puppet, they've become experts at puppet and solving issues with that tool. There will always be customers looking for puppet skills, since it was the favored tool for a few years. OpenStack recommended it ... I know a 2,000 physical server deployment where they are still fighting with puppet 18 months later.  The tool has become almost worse than the problems is was supposed to help them to avoid.

It is doubtful that my current company will need more than 100 nodes, ever. After 20 or so, we expand with front-end servers into "somebody elses' computers" (i.e. cloud).  I'm a major share holder and never intend to work anywhere else in the world, so my needs probably do not align with many readers here.

Sorry, don't have any more time today to show the depth of my ignorance. ;)

---

### Post by Miguel_Morales on 2014-07-05
Actually, very wise answer. I like the way you think about this and with your feet on the ground decide not to follow the new 'Justin Bieber' just because everybody is. Don't get me wrong, I think Openstack and Juju are quite awesome, but if you don't need it, you don't need it. If your solution is to scale, your pocket will, your team will and then it all will become easier.

---

### Post by coffeecat on 2014-07-05
Thread closed to avoid further necromancy. The OP has not been back since the day they posted.

---

