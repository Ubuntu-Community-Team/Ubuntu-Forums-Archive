---
title: "efficient way to administer or manage an aws autoscaling instance"
date: 2013-04-25
forum: Server Platforms
---

### Post by kolokoy on 2013-04-25
I need some advice on how do you efficiently administer an auto scaled instance with the following scenario: (our environment is running with autoscaling, Elastic Load Balancing and cloudwatch) 

(a.) patching the latest version of the OS for patch cycles or security reasons?
(b.) making a configuration change (like a change of the httpd.conf) and apply it to all instances in the auto-scaling group? with less downtime
(c.) how do you deploy the latest codes of my apps to the server with less disruption in production?
(d.) how do you use puppet or chef to automate your admin task? 

I heard about user-data, metadata and cloud-init. But I'm not sure how does it works.

I would really appreciate if you have anything to share on how you automate your administration task with aws. 

Thanks.

---

### Post by kolokoy on 2013-04-29
any advice?

---

### Post by howefield on 2013-04-29
You might get a better response in here, thread moved to the "*Server Platforms*" forum.

---

