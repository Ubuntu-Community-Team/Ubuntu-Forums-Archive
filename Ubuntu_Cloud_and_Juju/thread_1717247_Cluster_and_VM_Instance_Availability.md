---
title: "Cluster and VM Instance Availability"
date: 2011-03-29
forum: Ubuntu Cloud and Juju
---

### Post by JasonN on 2011-03-29
Hello everyone and thank you for allowing me/us to participate in your forum! 

We've been taking a crack at UEC for the past three months or so and we have successfully been able to create two functional cloud environments (with many thanks due to you all and your informative forum posts).  One had a rather simple topology using two machines (CLC+Walrus+CC+SC and NC), while the other was more complex with one machine running CLC + Walrus, four running SCs+CCs, and 8 nodes.  For the networking, we've relied principally on a Managed-noVLAN setup and it seemed to have satisfied most of our requirements.  Our last deployment has been running without issue for a couple of weeks now.

Lately, however, we ran into a slight issue when it came to deciphering all the potential pitfalls our last deployment.  Is it true to believe that, in the any setup of UEC, if a cluster controller happens to go down, it will bring down all the VM instances running on the nodes associated with that cluster?  I hope this isn't the case as we plan to and would greatly appreciate any feedback/commentary on our conjecture.

Thank you all in advance for your help! We hope to provide our insights on UEC to the community soon.

Cheers,
Jason (and others)

---

### Post by kim0 on 2011-03-31
Hi there,
Great work you're doing there! Unfortunately and afaik HA is not UEC's best point of strength, if a CLC fails, I would think VMs would continue to run, but probably wouldn't be accessible since their public addresses were on the CLC machine (thus they should be running but perhaps inaccessible) .. Note that this is my impression of what would happen (not really tested)

That said, should you want to cluster you CLC for better HA, check out this post
[http://www.roaksoax.com/2010/10/high-availability-uec-clc-howto](http://www.roaksoax.com/2010/10/high-availability-uec-clc-howto)
If that doesn't cut it for you, you might want to check out a different cloud stack (openstack) that is being shipped as a tech-preview with Natty (11.04) .. AFAIK, openstack could be made to operate without a SPOF. Although it can be a bit challenging still, since it's a quickly moving target without much documentation

---

### Post by JasonN on 2011-03-31
Hello Kim0,

Thank you for prompt your reply! I'll make sure to check out the RoakSoax's weblog.  

On a related note, would you happen to know if there's any interest in this type of feature from other members?  I'm curious to hear what type of contingency plan administrators would have in the case of a cluster failure. (It's really a question of when).   I mean, wouldn't they find it neat to have some built in cluster hot-swap feature that would prevent any instances from being lost when a cluster poops?  

Thanks again for your response!

Cheers,
Jason

---

### Post by kim0 on 2011-04-02
Hey, yes I have heard that feature request before. I'd just like to differentiate between two things:
1- HA on CLC level
2- HA on NC level

Commenting on number2 .. I would say most cloud operating environments, don't really do NC "clustering". The reason being, virtual servers are considered disposable, important user-data is stored on separate "volumes" .. If a virtual server is killed, or if a NC fails killing all virtual servers on it .. no problem .. you just spin up new virtual servers that mount the user-data volumes and continue

Regarding HA on CLC level, with the networking setup chosen in UEC, I do believe a CLC failing would result in all virtual servers behind it not being reachable! That might be resolved if you chose to configure networking in a different mode, such that virtual servers would have the real IPs directly on them .. that is not the recommended/tested/verified configuration of UEC however! If your plan is a "fully redundant no SPOF" cloud, that is not easy to get running, even if you try other technologies like openstack .. not saying it's impossible, but I'd say it needs some tweaking and a lot of testing

---

### Post by kim0 on 2011-04-02
And hey, if you're planning on running this in a production env. with very strict uptime requirements, you might want to talk to Canonical professional support .. Try [http://www.canonical.com/enterprise-services](http://www.canonical.com/enterprise-services)

---

### Post by JasonN on 2011-04-04
Thank you Kim0 for the informative answer! 

Though, did you mean to say CC instead of CLC? 

In any case, I will probably have to revisit our implementation plans a bit further. At the moment, we're attempting to solely use the private IPs to govern VM instances connectivity. We're not entirely sure where this will lead us, but we're hoping the experiment will at least teach us a thing a two.

Thanks again for the response.  I will try my best to be more helpful to other's in the forum as well.

Cheers,
Jason

---

### Post by kim0 on 2011-04-06
Thanks! More help answering questions is definitely most appreciated. You get the benefit of becoming the local expert too :)

---

