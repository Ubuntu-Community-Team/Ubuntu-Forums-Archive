---
title: "Seeking advice for likely SlashDot effect"
date: 2011-11-16
forum: Server Platforms
---

### Post by volkswagner on 2011-11-16
Greetings,

A website of mine may likely experience a large volume of traffic for one or two days.   This will happen in a couple weeks, due to national advertising/promo.

Currently the site gets more traffic from search-bots, compared to organic requests.  It may get 200-300 requests/day.  It is hosted on a very modest VPS with 384MB RAM, along with email and a few other sites with even less traffic.  The VPS is Ubuntu 8.04... a hah, it is an Ubuntu question...LOL.  The site is simple HTML, going to Paypal as the payment gateway.

I am seeking opinions for solutions, so I can prepare.  I don't think I have enough time to learn how to set up an Amazon EC2 instance (although this seems a logical step).  

I don't even know if my VPS provider will handle the DNS requests.  So I'm thinking I'd have to move DNS along with the web server or at least set up a backup/secondary DNS???

Does anyone have suggestions for a short term move like this?  Currently I only pay $10/mo, so I don't think I would be able to afford a permanent move.  

I guess I would need to suggest what the traffic may look like for the two days.  Without a crystal ball, I'd at least like to be prepared to handle 5-10 thousand visitors in 24 hours... but who knows, it could get that in an hour!  One can only dream!

Do you think a 2gig or 4gig[ Linode ]("http://www.linode.com/")VPS would be a reasonable fit.  I also see [RackSpace Cloud server]("http://www.rackspace.com/cloud/cloud_hosting_products/servers/") seems like it could be less expensive, compared to EC2.  I just don't know what the learning curve would be to get up and running.



Thanks for taking the time.

---

### Post by ian dobson on 2011-11-17
Hi,

What can you current vps provider offer? Maybe the easiest option would be just to upgrade your current setup for 1-2 months then downgrade it again.

If the site is just static HTML then just add more memory (for cacheing, and maybe abit more cpu) If you have ssh access to the server just look at the amount of memory/cpu the site is using and then decide what to upgrade.

Regards
Ian Dobson

---

### Post by Jonathan L on 2011-11-17
Hi Volkswagner

> A website of mine may likely experience a large volume of traffic for  one or two days.   This will happen in a couple weeks, due to national  advertising/promo.

Currently the site gets more traffic from search-bots, compared to  organic requests.  It may get 200-300 requests/day.  It is hosted on a  very modest VPS with 384MB RAM, along with email and a few other sites  with even less traffic.  The VPS is Ubuntu 8.04... a hah, it is an  Ubuntu question...LOL.  The site is simple HTML, going to Paypal as the  payment gateway.

I am seeking opinions for solutions, so I can prepare.  I don't think I  have enough time to learn how to set up an Amazon EC2 instance (although  this seems a logical step).  

I don't even know if my VPS provider will handle the DNS requests.  So  I'm thinking I'd have to move DNS along with the web server or at least  set up a backup/secondary DNS???

Does anyone have suggestions for a short term move like this?  Currently  I only pay $10/mo, so I don't think I would be able to afford a  permanent move.  

I guess I would need to suggest what the traffic may look like for the  two days.  Without a crystal ball, I'd at least like to be prepared to  handle 5-10 thousand visitors in 24 hours... but who knows, it could get  that in an hour!  One can only dream!

Do you think a 2gig or 4gig[ Linode ]("http://www.linode.com/")VPS would be a reasonable fit.  I also see [RackSpace Cloud server]("http://www.rackspace.com/cloud/cloud_hosting_products/servers/")  seems like it could be less expensive, compared to EC2.  I just don't  know what the learning curve would be to get up and running.
First of all, most dreamed-for usage spikes  never materialise.  Of those that actually take place and overwhelm the  server, almost all of those are fabulous publicity for the "tragic"  website (eg [little beige dress frenzy]("http://www.mirror.co.uk/news/top-stories/2011/05/25/kate-middleton-s-reiss-dress-which-reiss-stores-you-can-still-buy-the-dress-from-115875-23156440/")).  However, if your web site is a charity or something like that, you want the money from the episode, as you won't get it later from the fame.

As you say, AWS is the perfect way to deal with this.  As I've written  elsewhere, it's a fantastic weapon in your armoury.  It takes two hours  to learn how to do it, and two more hours to get the details right for  production.  Call it one day.  The trick is not getting side tracked  with the many things you can do.  The per-hour charging means you can just switch things on and off as you need them.  And of course their networking is first-rate.  But don't expect miracles: I was affected by the fire in their European data centre, and didn't have any replication.  Everything came back, perfectly, but it took a few days.  That affected only one of their availability zones in Ireland.

Added: Comparison against Rackspace per-hour servers: they are probably good too, but I only have experience of their dedicated servers, which was mostly positive.  I note that Rackspace Cloud is purely a reaction against AWS, with slightly-cheaper pricing at the bottom end of the services.  It is more difficult to get information from Rackspace Cloud than AWS, in terms of documentation and so on.  The main thing about AWS is that it was built in order to make Amazon easier and cheaper to run, and made available to us to get the benefit of scale, and so is very mature.  In the end, however, I'm sure they are pretty similar to the end user.  I've had nothing less than first rate experience with AWS however, and continue to use it constantly.

Steps

1.  Sign up for account.  Read the details and especially the pricing of [EC2]("http://aws.amazon.com/ec2/") (the computers), [EBS]("http://aws.amazon.com/ebs/") (the disk drives).

2.   Terminology: You need to know that "machine image" means a starting  state for a computer; "instance" means an individual virtual machine,  "instance type" means how big the server is (and how much you'll be  charged); "volume" means virtual disk drive; "snapshot" is a backup of a  volume.  A "region" is a data centre, an "availability zone" is a power  supply and network within that zone.   Instances are behind a NAT firewall and are  natively numbered in 10.0.0.0/8.  They get a random public IP address,  or you can allocate yourself a static one (they call it "elastic ip").  A "security group" is a named set of firewall rules.

Don't  use "instance-store" images: these have their own (virtual) disk and it  is destroyed on termination.  Use EBS (virtual) disks, as you can  unplug them and plug them into other instances.  Completely ignore "spot  instances" and also "reserved instances" for the time being.  

3.  First your learn how to do  it on their excellent web control panel. However there's a lot there  which isn't relevant so it can be a little confusing.  When you first  get to it, it's on S3 and you need to click on the EC2 tab, and once  there check you're in the right region as the other information is  per-region.  The control panel can be a little slow (5 or 10 seconds to  refresh some things) and really doesn't work at all well if you're on a  netbook screen that's only 600 pixels high.

4. I'd suggest following the details in the [Getting Started Guide]("http://docs.amazonwebservices.com/AWSEC2/latest/GettingStartedGuide/").  But if you like to, um, go fast and take risks, just click away.[INDENT] 4.1 When you click on "Launch Instance", use "classic launch" not "quick launch".

4.2 Instance type: use t1.micro as it's very cheap!  Only use the bigger ones when you know you need them.

4.3 Machine  image (AMI). You choose it in their control panel, but in  real life you might find it easiest to look at Canonical's [list of images]("http://cloud.ubuntu.com/ami/") and  type in the number.  In the first case, use ami-ab36fbc2 (10.04,  us-east, block storage, i386) unless you're not in us-east!

4.4 Availability zone: for the time being, always choose 1.

4.5 Advanced Instance Options (Kernel ID, ramdisk etc): just ignore.

4.6 Tag Key and Value page: type something the the value for Name ("test1"), or ignore it.

4.7 Create Key Pair: create a new one   Call it perhaps "volks-aws-useast", and save it on your own computer in ~/.ssh/volks-aws-useast.pem

4.8 Security group: use the default one. This defines the  access lists at the border into EC2 network towards your new servers.   It won't have web allowed by default, you'll have to fix that later.
[/INDENT]And you're running.

```
ssh -i ~/.ssh/volks-aws-useast.pem [COLOR=Red]ubuntu[/COLOR]@1.2.3.4
```The username is ubuntu.  I always forget that!

```
sudo apt-get update
sudo apt-get install lamp-server^
```Then your homework:

1.  Make a static IP address and apply it to the running server.
2.  Stop the running server and restart it.
3.  Fix your security group to allow web access
4.  Make a new volume "webdata" and mount it on /var/www
5.  Stop server, start a new one, mount your webdata on it

It's perfectly possible to stop images and restart them with different sized instances, but it's a bit fiddly until you know what all the parts do and how they interrelate (volume -> snapshot -> ami -> instance).  The easiest way would be to put your data (and perhaps logs) on their own volume, and mount that on a new faster server, then cut over your IP address.  Remember you don't get charged for stopped servers!  (Just the disk space).  So your plan would be to a tiny instance running, and a larger server on standby (in stopped mode) while you monitor load.  If and when you start getting trouble, you stop the little instance, umount the web data, start the big instance, remount the web data, and move the static ip address; all of which will take about 1 minute.  If you can't afford the downtime, and your data is sufficiently static, copy the web data to the big instance and cut the ip address over, with no downtime at all.

DNS: I wouldn't worry about it much, but it's perfectly possible to use Amazons excellent DNS service, or of course run your own for a little while on their kit, as a secondary or two. 

Important point: you have to remember that Amazon's IP space is pretty jungly.  If you're unlucky, the random IP address you've been allocated was used by someone recently for terrible purposes, and is blacklisted all the way to Pluto.  The way to address this is keep a static IP address available and hold onto it (you have to pay a little if you're not using it) and use that for any real purpose.

[COLOR=Red][B]Very important point: remember to check and terminate any instances you don't want!

[/B][/COLOR] 
Costs: the little servers are only a few $0.02/hour, the bigger ones are $0.085 (1.7 Gbyte RAM) or $0.34 (7.5 Gbyte) or $0.50 or more; disk space is $0.10/Gbyte/month, traffic out costs $0.12/Gbyte.  In your case you might use $0.34 * 2 days * 24 hours = $16.32 for CPU, 10 Gbyte * 1 mo = $1.00, traffic negligible.  The real point is that you can scale up quickly and cheaply, and then scale back down, and that's where you save the money.


Any use?

All best

Jonathan.

---

### Post by Habitual on 2011-11-17
Jonathan:

Mad Props for the excellent howto.

JJ

---

### Post by volkswagner on 2011-11-17
Jonathan,

Thank you kindly for such a comprehensive response.

You are my hero.

If I ever were looking for a reason to jump into AWS, you have narrowed the gap for the great unknown. 

After reading Jonathan's post a few more times to digest the new vocabulary, I feel this is something I can accomplish, while keeping all my hair.

This is all still way above my pay scale, but I'm ready to jump in.  I'll post back here once I hit the wall.

Many thanks to all who have replied.

---

### Post by Jonathan L on 2011-11-18
Hi

> This is all still way above my pay scaleIt's the only way to act if you want your pay scale to catch up!

Thanks Volkswagner and Habitual for kind* words, glad it's helpful.

Jonathan.

* I confess I [checked]("http://www.urbandictionary.com/define.php?term=mad+props") that I understood them first!

---

### Post by volkswagner on 2011-11-19
I have an update.

I have to admit, I can see how using AWS could become a little addictive.  I currently have setup a t1.micro and m1.small server.  I'm not sure the 1.7Gig RAM on the m1.small makes me feel secure.  I think I'll also setup an m1.large, 64bit instance with 7.5gig RAM!

This stuff is way to cool.


I think it will be all fun and games until I get the invoice... LOL


I may have lucked out, it appears the static ip offered to me is not on any major blacklists!

Thanks again to all. 

I'll give an update in a few weeks, to inform if the flood ever materializes.

---

### Post by Habitual on 2011-11-19
> **volkswagner said:**
> ...This stuff is way to cool.

I think it will be all fun and games until I get the invoice... LOL...

I believe the general rule-of-thumb for AWS is you only pay for what asset(s) you actually *use*. But I could be wrong (see signature) since I don't pay the bill each month (but if it's High, I do hear about it).

Subscribed with interest...

---

### Post by Jonathan L on 2011-11-22
Hi Volkswagner

> I think it will be all fun and games until I get the invoice

You can look at the bill for the partial current billing period and see what you're spending as you go.  Control panel, top right by your username, "account activity" > "current statement".

Sounds like you're enjoying your new machine room.

Kind regards,
Jonathan.

---

### Post by volkswagner on 2011-12-14
> **Jonathan L said:**
> ...

First of all, most dreamed-for usage spikes  never materialise.  Of those that actually take place and overwhelm the  server, almost all of those are fabulous publicity for the "tragic"  website (eg [little beige dress frenzy]("http://www.mirror.co.uk/news/top-stories/2011/05/25/kate-middleton-s-reiss-dress-which-reiss-stores-you-can-still-buy-the-dress-from-115875-23156440/")).  However, if your web site is a charity or something like that, you want the money from the episode, as you won't get it later from the fame.



Well I did want to update y'all.

Unfortunately the flood did not fully materialize.  I was fully prepared thanks to the help from kind folks here.

I am very happy with the services available through AWS. 

I can't complain about what the free press did offer, and I feel more knowledgable and ready for what ever the net may throw my way!

Thanks again.

---

### Post by Dry Lips on 2011-12-15
For those of you in a similar situation to the OP who don't want to sign 
up with amazon, [https://www.cloudflare.com](https://www.cloudflare.com) might be an alternative.

---

