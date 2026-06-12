---
title: "Cloud Providers Much More Expensive than OpenStack Clouds"
date: 2016-10-24
forum: The Cafe
---

### Post by TheFu on 2016-10-24
Cloud Providers Much More Expensive than OpenStack Clouds
[http://www.theregister.co.uk/2016/10/24/openstack_cost_of_public_cloud/](http://www.theregister.co.uk/2016/10/24/openstack_cost_of_public_cloud/)
and 
[http://siliconangle.com/blog/2014/02/04/beware-amazon-cloud-cost-can-ruin-startups/](http://siliconangle.com/blog/2014/02/04/beware-amazon-cloud-cost-can-ruin-startups/)

Thoughts?

With few VPS systems for a company, the costs really don't matter much, but as the company needs more and more, then the normal rent vs own decision matters more and more.

I have 20-30 VMs running usually on fairly cheap systems that would be paid for in VPS costs in 2-4 months.  Have 10-15 VMs per server.  i suppose if my background didn't have HW knowledge, getting that would be a cost-offset too.

What has been your experience?  Are Azure, Rackspace, EC2 cost effective for large numbers of VMs?

---

### Post by mastablasta on 2016-10-27
this says it al i thinkl:
> 
But the expenses are hidden as the costs move from IT to the business &#8211; those consuming the services rather than providing them.
Costs increase as more data is generated and is stored in vendors' clouds and also as organisations use more features beyond the basic cloud compute or storage.


we should also bare in mind that we do not know the actual prices. companies usually can negoitiate those if they are big enough to matter.

in any case it looks to me like they are still a good start but if oyu need them more and more if you grow with them then going at it alone should be cheaper. 

same with goods i guess. if you need 100 ovens or 500 or 1000 or even 10.000 it is easier & cheaper to have someone make them for you and stamp your brand on it. but if you need milions of them a year then it is probably a lot cheaper if you handle it all by yourself.

---

### Post by TheFu on 2016-11-05
I think with servers, there are multiple plateaus for what makes sense to have in and out-sourced.  For example, if you need just a few VPSs, putting those in the cloud makes sense. 
When you get passed about 5, hosting them internally makes sense until about 40-ish VPS are needed. By that point, enterprise networking and monitoring is needed and infrastructure costs balloon.  Outsourced systems, perhaps in colocated caged locations, makes sense.  
Probably around 200 physical systems, bringing those back into an enterprise data center starts to make sense again. At this point, your IT department probably isn't entirely flexible with quick server spin-ups.  Departments tend to spin up servers and forget to spin them down when hosted internally. When they are external, there is a cost, so spinning them down when not used is something the accountants/PMs watch.

I suspect if internal IT did charge-backs at the same rate as external providers, then a more realistic support system could be worked out.  Plus external providers don't enforce corporate standards for backups, network redundancy, security of the OS, applications, networking ... which are such a hassle to a business department.

External providers usually don't risk access to internal systems when breached either. That is a plus.

---

