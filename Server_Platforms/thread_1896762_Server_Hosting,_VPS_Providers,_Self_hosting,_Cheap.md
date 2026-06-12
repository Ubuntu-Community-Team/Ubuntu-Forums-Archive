---
title: "Server Hosting, VPS Providers, Self hosting, Cheap providers, etc?"
date: 2011-12-17
forum: Server Platforms
---

### Post by gkffjcs on 2011-12-17
I don't quite know which forum this is most appropriate to post on, feel free to move it.
I am currently developing an e commerce website as an addendum to a successful ebay store. I am using django, and python for this project. I am at the point of figuring out whom/where this site will be hosted. The challenge for me is that I currently don't know what kind of traffic load to expect, which makes it more difficult to determine the cost of bandwidth provided by various services.  

I would like to have root access, and be able to use ubuntu server, since I know it, however, I am also open to a managed solution. 

Currently I see three options and I would like to hear from people with experience doing this sort of thing which option is best, were there any nasty gotchas etc.  Unexpected very high bills or other "that seemed like a good deal, buts"...

Option 1: Get a basic hosting provider which supports django. Downsides, not root access, possible lack in flexibility if for example load increases. 

Option 2: Hire a dedicated server with root access in one of the many data centers. That provide that service.

Option 3: Hire a VPS or use a cloud service like amazon ec2. This is what I'm most confused about since they all do their pricing by the hour/bytes of bandwidth used. Which is not useful information for me.

Option 4: Upgrade my ISP contract to a business class connection and host the site on my own metal.

I ask this question, mostly because after hours of reading pricing charts from Amazon, RackSpace, Comcast, and several other providers of various services I am now less knowledgeable than I was when I started. For example Aamazon's pricing chart with things like 0.0X dollars per megabyte upload is pretty useless to me, if I don't have an estimate of how much data I will be uploading per month. Also the little fractions of cents look cheap but could add up really fast if I'm not careful! 

Thanks for any input, it is appreciated!

---

### Post by Dry Lips on 2011-12-18
Is cost an issue? The very best, but probably also the most expensive solution would probably be to rent a dedicated server. You would have access to support if something goes wrong, and bandwidth wouldn't be an issue. But then again, you might find out that a dedicated server is a complete overkill, so the question is then what kind of business you're running, and how much money you can afford to spend on hosting.

Since it's going to be an e commerce site, self hosting would probably not be a good idea. Data centres have redundancy in their network, in their power networks, etc. If you're running e commerce, downtime is obviously something you can't afford, so play safe. 

But then again, it really depends on what you're doing. If this is your family business where you're selling you're wife's homemade organic shampoo, then you probably will be alright no matter what solution you choose.

Good luck! :D

---

### Post by azmyth on 2011-12-18
You could start out with shared hosting and go with a host that has a path to VPS and dedicated and you can move as your site grows. If you think your site will make enough money from day 1 to cover dedicated then I'd just start with that since it has the most control.

---

### Post by Habitual on 2011-12-18
[Eric Hammond's site]("http://alestic.com/") is a Gold Mine of Information about AWS. I found [this...]("http://alestic.com/2011/11/ec2-schedule-instance")
I have been managing some half-a-dozen servers up in Amazon's Cloud for the last year. 
_You only pay for what you actually use_ as far as resources.

You could sign-up and make an Instance from any number of Eric Hammond's  pre-built Ubuntu-flavored AMIs, or make your own from an existing AMI  (Amazon Machine Image). AS LONG AS IT'S NOT RUNNING, you incur NO  charges.

This makes it easy on the financial level (Cost) , but hard on a technical level (ie, DNS Records...)
A balance must be possible with such information such at the Excellent Advice Dry Lips gave.

[Amazon Web Services AWS Cloud Pricing Summary]("http://www.webhostingcloud.co.uk/2009/06/amazon-web-services-aws-costs-summary.html")

I hope this helps.
Subscribed with interest...

---

### Post by SeijiSensei on 2011-12-19
I'm a fan of [Linode]("http://www.linode.com/").  You can get a basic server for $20/month with your choice of distros, Ubuntu included.  They have very flexible pricing and no long-term commitments.  You also get a static IP with configurable reverse DNS, a huge pipe to the Internet, giant honking generators to keep you online, and, for a few dollars more, automated snapshot backups.  You can access the machine via SSH or, in a pinch, use Linode's shell access tools.  

Oh, and they have an excellent and knowledgeable support staff.

I'm in the process of dumping my business-class ISP connection because hosting on Linode is much cheaper.

---

