---
title: "What is the use for a private cloud?"
date: 2012-01-19
forum: Server Platforms
---

### Post by Darthcolo on 2012-01-19
**Hello all!**
I am about to install Ubuntu Server and perform some tests on it. I want to try the "private cloud" feature... but I still don't see a worthy use for a small-medium company. :confused:

My plan is to implement Ubuntu on a company in some future...

Anyone can explain to me how a company may use the private cloud?

**Thanks!**

---

### Post by rwslippey on 2012-01-19
I'll second that... love to hear some good uses for small businesses


right now running up a local dev server and samba system for file storage... whats the benefit of the cloud?


:popcorn:

---

### Post by Habitual on 2012-01-19
in 2 words.

Aggregate.
Resources.

---

### Post by Lars Noodén on 2012-01-19
I'm curious about it too.  I've looked at the official web page for "cloud" services ([http://www.ubuntu.com/cloud](http://www.ubuntu.com/cloud)) and can't find anything beyond marketing speak.  It'd be nice to get some concrete examples of what it does and maybe also how it does what it does.

---

### Post by Darthcolo on 2012-01-19
> **Habitual said:**
> in 2 words.

Aggregate.
Resources.

Could you use more than 2 words please?

Resources of what kind and for what end? Space for backup? Server services like FTP, mail server, and so on?

I would love to hear that you can run Micro$oft Word (or Libre Office) directly from the cloud...

---

### Post by Darthcolo on 2012-01-19
> **Lars Noodén said:**
> I'm curious about it too.  I've looked at the official web page for "cloud" services ([http://www.ubuntu.com/cloud](http://www.ubuntu.com/cloud)) and can't find anything beyond marketing speak.  It'd be nice to get some concrete examples of what it does and maybe also how it does what it does.

I second that!

---

### Post by nsnidanko on 2012-01-19
Hi All,

If you are interested in private clouds highly advise you to check out OpenStack project.
Private clouds offer scalability, availability and overall better usage of your available physical hardware resources. Also the main goal clouds try to achieve is resources on demand.

To briefly explain the use of private cloud I am going to start with examples. 

For example you are a software developing company. Your current infrastructure has production, development servers etc sitting on the standalone box or being a guest machines on the hypervisor. Lets say your production server hit its max capacity and you need to deploy another one instantly. With private's cloud images you can do it in the matter of minutes, only limited by resources of your cloud.

Lets say developers test application; process takes 4hrs with 4 CPU and 8GB of RAM. After testing these resources stay idle, thus costing your company money. If you have another set of developers that test another part of your application (lets say performance of the back end database) and they require 2hrs of runtime with 2CPU and 16GB of RAM. Therefore these developers only load their images during the testing, thus using the same resources. 

Private clouds become more cost effective the more different "tiers" of users you have, the more overall pool of resources.

Regards,
Naz

---

### Post by Lars Noodén on 2012-01-19
@nsnidanko  thanks.

Could you elaborate a little, it would be nice to have details.  Do you mean in the example above that it is a compile farm?  Or is it merely an expandable pool of hosts for a VM guest?

---

### Post by Habitual on 2012-01-19
> **Darthcolo said:**
> Could you use more than 2 words please?

Sure.
[https://en.wikipedia.org/wiki/Cloud_computing](https://en.wikipedia.org/wiki/Cloud_computing)

I don't use Ubuntu personally so I have no idea what their "private cloud" is, or should be.

I do use AWS and AppLogic for cloud computing resources.
[http://doc.3tera.com/AppLogic2/AppLogic.html](http://doc.3tera.com/AppLogic2/AppLogic.html)

For example: On AppLogic, should one of my servers needs 256G more RAM, it is merely an edit away on the AppLogic canvas and a reboot away.

Scalable Resources.

---

### Post by Darthcolo on 2012-01-19
So, basically, you are providing resources (CPU, RAM, disk?) to the employees. That is similar to a Cluster to my understanding.

But if the employees wants to use some specific application (like a management suite like SAP, virtualized on the cloud), they can do it?

---

### Post by nsnidanko on 2012-01-19
> **Lars Noodén said:**
> @nsnidanko  thanks.

Could you elaborate a little, it would be nice to have details.  Do you mean in the example above that it is a compile farm?  Or is it merely an expandable pool of hosts for a VM guest?

Well not exactly; I am going to use Openstack as example since it will be a defacto for open source cloud. 

You have the following resources:
- networking
- storage
- processing power (CPU + RAM)
- images

Networking is a pool of available VLANs, IP addresses, could be ether public, private or both depending on your cloud set up

Storage is a permanent store that can be attached as a disk to your instance (instance = Virtual Machine).
Processing power - as it says it is the amount of CPU and RAM available for you

Images - are pre-build virtual machines templates in that can be span into the instance

So to summarize it is a pool of resources, which offers fault tolerance and are accessible on demand. Unfortunately, I am not familiar with compile farm term, but acording to a quick wikipedia search, cloud can run any platform. You can have System32 and *nix systems sharing the same cloud.

---

### Post by nsnidanko on 2012-01-19
> **Darthcolo said:**
> So, basically, you are providing resources (CPU, RAM, disk?) to the employees. That is similar to a Cluster to my understanding.

But if the employees wants to use some specific application (like a management suite like SAP, virtualized on the cloud), they can do it?

Cluster is designed for load balancing and fault tolerance. It does not provide resources on demand unlike a cloud.

Yes, you can have a self provisioning portal with prebuild image of CentOS that has this SAP application installed. Data for this SAP application could be stored on permanent storage (refer to my post above). Let say employee finds that he needs this application today for 30 minutes and maybe in a 2 mnth again. You will not waste resorces having it running on at all times, right? Neither you will waste your own time preparing his SAP every time he needs to use it. With cloud you can give him ability to power it anytime he wants it with any reasonable amount of resources he requires.

---

### Post by Darthcolo on 2012-01-19
> **nsnidanko said:**
> Cluster is designed for load balancing and fault tolerance. It does not provide resources on demand unlike a cloud.

Yes, you can have a self provisioning portal with prebuild image of CentOS that has this SAP application installed. Data for this SAP application could be stored on permanent storage (refer to my post above). Let say employee finds that he needs this application today for 30 minutes and maybe in a 2 mnth again. You will not waste resorces having it running on at all times, right? Neither you will waste your own time preparing his SAP every time he needs to use it. With cloud you can give him ability to power it anytime he wants it with any reasonable amount of resources he requires.

Thank you for you explanation.

Now I have another consern: how can I, as a user, access to an application on my private cloud?

As I see it:

/// APP ON CLOUD ///---> what goes here? ---> My desktop PC

Should I have to access via VNC to the instance in the cloud running the application?

---

### Post by nsnidanko on 2012-01-19
> **Darthcolo said:**
> Thank you for you explanation.

Now I have another consern: how can I, as a user, access to an application on my private cloud?

As I see it:

/// APP ON CLOUD ///---> what goes here? ---> My desktop PC

Should I have to access via VNC to the instance in the cloud running the application?

As as user, you will create running instance with specs you need using self-provisioning portal (or automatic scripts, etc). When you are referring to "APP ON Cloud" I assume you saying that Aplication consists of several components (i.e Active Directory server for authentication, Apache server for webgui and application server itself). You would deploy 3 instances. For accessing server you will use SSH or whatever method your cloud platform supports. For example, OpenStack automatically injects SSH keys (you create your own private ssh keys) into the any instance you spark so you can administer them.

Therefore,
//APP on the cloud // ->>automatic injection of SSH keys upon instance creation ---> SSH client on your local pc

If your instances have the VNC installed you can probably access it that way. I dont have experience deploying cloud instance with VNC. Also if that instance has application installed, you most likely can set application client to use it.

If you would like to "experience" cloud you can try AWS. Amazon offers free Micro instance for a year with limited bandwidth.

[http://aws.amazon.com/free/](http://aws.amazon.com/free/)

Please note this a public cloud. Public cloud is shared by everyone, whenever private is dedicated to your own organization and in most cases you own infrastructure.

---

### Post by TheFu on 2012-01-28
There are too many reasons to list them all.  If you understand virtualization and already KNOW it is critical to getting the most utilization out of your infrastucture, then having the added flexibility that a "private cloud" brings is a HUGE win for many companies.  It is especially useful for growing companies.

With a properly designed cloud, you can improve availability, increase redundancy and prevent single points of failure with much fewer resources than otherwise possible.

If you work with a technical architect, she/he can explain more.

As an example, a client company had 22 servers a few yrs ago. Each ran 1 main software application - email, document management, remote access, telephony, CRM, file server, print server ... etc.  You get the idea.  Because they had so many servers, they needed a huge UPS too. That meant they needed huge coolers for their "data center" - really just a resource room in their building.  We came in and helped them consolidate where it made sense. First we deployed a SAN - storage network. Next we purchased 3 newer servers which were 3x more powerful, much more power efficient and provided warranty protection - their old servers were all out of warranty.  We setup virtual machines for each of the old physical servers.  Many were barely used, so putting 10 VMs onto a single physical server was pretty easy. How much does it take to have a print queue server for 100 desktops? Not much.

With the VMs all running off the SAN, migrating the VMs between any of the newer servers was pretty easy. Live migration.  When their IT guy wants to try a new product out, he can easily spin up an new server OS instance and try it, then when he's done, wipe it OR freeze it to a USB HDD or tape for later consideration.  

For a small shop that isn't web base for customers, virtualization can handle most of these things - the "private cloud" aspect isn't very important.  However, for a web-centric small business, private clouds can be extended into public clouds when necessary.  Imagine your business usually needs 20 server, except during Christmas. During that period, you need 60 server to handle the additional shoppers. With an elastic cloud, for those 3 months around Xmas, your company can leverage someone else's servers without the capital outlay of buying the infrastructure, managing all those licenses, backing up additional servers, etc.

Clustering can be done with virtual servers and that's a good move provided the clustered VMs do not run on the same physical hardware.

A small company would never deploy SAP. That would be a huge waste.

Virtualization, cloud computing, high availability, disaster recovery and clustering are all slightly different things. They can work together effectively, when deployed with the correct reasons and expectations.  Usually the added complexity and cost of clustering isn't worth it for most applications. Often there are better ways to accomplish those requirements for less money.

---

### Post by shumifan50 on 2012-01-28
I have an instinctive resistance to 'CLOUDS' and 'SANS'.

When you have SLA with your users, then it is highly undesirable that the traffic of one user can adversely affect your agreement with another user, which is what happens when they share hardware; disk space or CPU or network. It also means that a single point of failure can take out several services.

The whole concept of hardware consolidation is a matter of [COLOR="Red"]projected[/COLOR] money saving without due consideration of users and the adverse effect a bad experience can have on the long term business of a company. Much worse is the fact that these projected savings are hardly ever achieved in properly run environments because you now need a new bunch of experts that can configure/maintain the SANS and CLOUDS - and they are normally much more expensive and fewer than 'normal' operations staff.

After consolidation no manager will admit to it not having made 'huge' savings, as it will badly reflect on him/her, so we never hear about this. Then you also have to go through he cost of the consolidation process and how long it will take with the real savings to recover the cost of the consolidation - not mentioned too often in today's short term management philosophy: by the time they discover the disaster I will be long gone, but I will have a nice addition to my CV. 

And when it gets to public clouds: Why would anybody want to allow another company to have total control over their systems? And rely on network connections that they share with many other users: again what about SLAs, but I guess few of these are getting signed these days. In public CLOUDS other companies can adversely affect your services - GREAT!

This will no doubt make accountants very happy, but what about clients!

---

### Post by Lars Noodén on 2012-01-29
> **TheFu said:**
> ...
As an example, a client company had 22 servers a few yrs ago. Each ran 1 main software application - email, document management, remote access, telephony, CRM, file server, print server ... etc.  You get the idea...  


It used to be that one Linux/Unix machine could run many different services.  What went wrong there at the client that they ended up with so many servers?

---

### Post by shumifan50 on 2012-01-29
> Imagine your business usually needs 20 server, except during Christmas. During that period, you need 60 server to handle the additional shoppers. With an elastic cloud, for those 3 ...

Now this 'elastic cloud' - where does it get 3 times capacity over christmas? And where does it dump the capacity ater christmas? The provider still has to have the hardware to provide 3x the capacity at christmas and therefore, before christmas and after christmas, and somebody still has to pay for the 'idle' hardware and if it is a public cloud, also pay the profits on the idle hardware for the rest of the year. Or the provider could just sell you 60 instances on the same hardware with reduced performance.

The christmas example is very good, as at the same time ALL RETAILERS have this increased requirement, so where does this huge increase in capacity materialise from? And who pays for it when?

Or you can follow sound statistical principles and never load your servers more than 65%, to allow recovery after flooding etc, without harming processing times too much. Lower this utilisation figure slightly, say to 45% and you would most likely cope with your christmas load.


And then the little matter of data security: Google Sony and most of the big players have had breaches of their systems, exposing thousands of user accounts. The bigger the player the more desirable it is to hack; so when many businesses consolidate with one provider, it appears much higher in the tree of likely attacks. And we know from past experience that we cannot trust big institutions to keep our data secure, it will just be a matter of time to when the breach happens.

---

### Post by TheFu on 2012-02-01
> **shumifan50 said:**
> Now this 'elastic cloud' - where does it get 3 times capacity over christmas? And where does it dump the capacity ater christmas? The 


You pay an external provider to run front-ends to handle the added browsers.  Your back-end is still hosted internally and you redirect buyers to your internal systems.  In that way you don't give up any security just for browsers, but add the capacity until a purchase comes in.

> **shumifan50 said:**
> 
provider still has to have the hardware to provide 3x the capacity at christmas and therefore, before christmas and after christmas, and somebody still has to pay for the 'idle' hardware and if it is a public cloud, also pay the profits on the idle hardware for the rest of the year. Or the provider could just sell you 60 instances on the same hardware with reduced performance.


How the external "cloud provider" deals with excess hardware is not my issue.

> **shumifan50 said:**
> 
The christmas example is very good, as at the same time ALL RETAILERS have this increased requirement, so where does this huge increase in capacity materialise from? And who pays for it when?  

The cloud service providers plan for this. In August, they swap out older servers for newer ones. They beef up their networking and internet connections to be prepared for the fall/winter rush.  They provide SLAs with their contracts to the companies who demand it, for increased costs.  This is common and still many times less expensive to the company expanding their front-ends.

> **shumifan50 said:**
> 
Or you can follow sound statistical principles and never load your servers more than 65%, to allow recovery after flooding etc, without harming processing times too much. Lower this utilisation figure slightly, say to 45% and you would most likely cope with your christmas load. 

Facts and data are critical to making good decisions.  FUD doesn't help anyone.  If you aren't already monitoring your servers and don't have a plan to easily expand as needed, you are failing.  By running an internal cloud that uses the same control APIs as the public services, you are allowing your company to expand quickly. Buying 40 more servers for a 3 month need is hard to sell. It won't happen and your business will lose customers.  Why do you think Amazon created an internal cloud?

There may be other services instead of cloud servers that could alleviate growth problems or network spikes like content networks distribution.

> **shumifan50 said:**
> 
And then the little matter of data security: Google Sony and most of the big players have had breaches of their systems, exposing thousands of user accounts. The bigger the player the more desirable it is to hack; so when many businesses consolidate with one provider, it appears much higher in the tree of likely attacks. And we know from past experience that we cannot trust big institutions to keep our data secure, it will just be a matter of time to when the breach happens.

Data security is never a little problem. I want the most critical data running inside networks and on disks that I control.  I want redundant network connections from at least 2 different, unrelated, providers.  

I've worked inside many companies as a consultant, including SONY-JP, telecoms, and highly secure government networks with air gaps and others with one-way traffic.  Deploying to the public cloud like many companies do it is a terrible idea, IMHO.  That doesn't mean you can't lease servers for a known period in a provider's datacenter and expand selected parts of your private cloud to those servers for a new months.   Leasing servers for a few months is much less costly than buying them.

Would I ask to be on shared computer or storage hardware? No, but for information that will be 100% public anyway, I'm confident that a system design could be made to address almost every concern.

Perhaps we are saying the same things?  The topic of this thread was private clouds, right?

---

### Post by shumifan50 on 2012-02-01
> How the external "cloud provider" deals with excess hardware is not my issue.

It has everything to do with you:
1. If the provider does provide the right level of hardware, then you WILL pay for it by raised prices in high demand periods to recoup the low demand losses. Somewhere virtual has to map onto real and the costs most be born. The provider is running a business hence has to make a profit, so cannot carry the losses during the rest of the year.
2.The alternative is that the provider hardware is overloaded and you will suffer the consequences. Remember that any company looks at its own bottom line not that of its customers.

Internal clouds suffer the same problems; Even NAS causes bottlenecks that can take lots of time and expertise to find and fix - in the meanwhile the users suffer; but the accountants are still happy. They only realise the problem when the revenue drops, by which time the consultant or manager is long gone, bonuses and all. I say this from bitter experience; Unfortunately I cannot name the company as I will be in court post haste. We have suffered mass storage 'rationalisation', server consolidation and outsourcing and are now beginning to lose our clients as when they come up for renewal they go to the competition instead.

> Why do you think Amazon created an internal cloud?
Because of the hard sell of the cloud concept and the lure of cost savings to accountants running the company. Again it is a good example of cost cutting: Amazon used to deliver next day almost without fail; now it has to be special delivery for the same service(and paid extra for). I am not saying the internal cloud caused the delay in delivery - it shows the mentality: the customer definitely came second to cost cutting.

> an internal cloud that uses the same control APIs as the public services,
One of the first compromises in IT has been standardisation of software - this turned out to be the hackers dream resulting on a whole new industry of anti-virus companies. The best security is obscurity, as then it is not worth the while of a hacker to hack your site. I run a private website that uses a webserver written from the ground up by me. It has no anti-virus software. has been attacked numerous times (I log unrecognised traffic) and has never been broken into. I also have a hand crafted filter to stop script injections. 

> The topic of this thread was private clouds, right?
Most of what applies externally, apply internally as well, especially as related to performance.

---

