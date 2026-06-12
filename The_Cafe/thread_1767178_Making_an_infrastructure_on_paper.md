---
title: "Making an infrastructure on paper"
date: 2011-05-25
forum: The Cafe
---

### Post by tapi0n on 2011-05-25
So, for a school assignement I got to make some sort of business IT-infrastructure suggestion. Bassicly the assignement sketches a current situation in a company, naming it's wishes and requirements.

For example 3 different wireless networks in the company building (all with different priveleges etc). 

For most of the aspects (like servers, cabling, switches) needed I am already getting some good ideas as to what I'm gonna go for. 

However for some things (like firewall, mail server, ...) I'm still not sure. More specifically I'm not sure which way to go (prebuilt, open source,  ...).

So my question to this loving community is the following. 

When chosing your hardware and server setup. Which way do you go? What aspects are more important to you (security, price, possible external support, extra services) and why?

Also. I'm not very into firewalls, does anyone know a good place to check up on heavy-duty firewalls or something like that?

Cheers,

---

### Post by Old_Grey_Wolf on 2011-05-25
> **tapi0n said:**
> When chosing your hardware and server setup. Which way do you go? What aspects are more important to you (security, price, possible external support, extra services) and why?

I work for a large corporation. We use both open source and proprietary software. For both hardware and software we do a trade study. The trade study analyses the products against a ranking system. When we begin the trade study, we give; meeting the functionality, security, price, external support, and certifications/training requirements a weight factor. We also define the functionality, security, support, and training/certification requirements. We then assess each product against the requirements and apply the weight factor. The weight factors vary; for example, if the infrastructure service connects to the Internet then security will have a higher weight factor, or if the infrastructure service is similar to what we already have then certifications/training any have a lower weight factor. 

The equation may look something like this> 50% X functionality requirement net + 30% X security requirements met + 2% X price + 7% X support requirements met + 11% X certifications/training requirements met

What I am trying to explain is that there is not a single set of criteria that applies to all product selections.

For a small company, price may have a higher weight factor. For a small company, the trade study will be less formal; however, someone goes through the same basic though process.

---

### Post by Bandit on 2011-05-26
Sounds like my Systems Analyst course I just took in college. 
But before I can suggest solutions I may need more information form you.


> So, for a school assignement I got to make some sort of business IT-infrastructure suggestion. Bassicly the assignement sketches a current situation in a company, naming it's wishes and requirements.

- Whats the budget looking like..


> For example 3 different wireless networks in the company building (all with different priveleges etc). 

- This is not all that much of a biggy, but your gonna need at least 3 wireless routers per floor, if not 2 of each to keep your signal up. This will depend on what the building is constructed of and the size.


> For most of the aspects (like servers, cabling, switches) needed I am already getting some good ideas as to what I'm gonna go for. 

- First you need to check out local fire codes in your area, there are some restrictions in city area on the type of cabling you can have for horizontal cabling. 


> When chosing your hardware and server setup. Which way do you go? What aspects are more important to you (security, price, possible external support, extra services) and why?

- I would go with a small rack server cluster or large multi CPU system running your flavor of Linux and Virtual Machine. Then I would nest each server system in Vbox letting you do load balancing and get the most of your hardware. You can very easily have Linux in a VM hosting Appache, then another running your SQL server, another running MS Exchange server for email. Each would be sand-boxed and independent from each other.


> Also. I'm not very into firewalls, does anyone know a good place to check up on heavy-duty firewalls or something like that?

- Most likely you will want to go with a solid hardware firewall right off your closet wiring then followed by your main router that will also serve as a lower level firewall offering increased security.

---

### Post by koenn on 2011-05-26
> **tapi0n said:**
> 
For most of the aspects (like servers, cabling, switches) needed I am already getting some good ideas as to what I'm gonna go for. 

However for some things (like firewall, mail server, ...) I'm still not sure. More specifically I'm not sure which way to go (prebuilt, open source,  ...).


you're going about it the wrong way.
You need to look at the business requirements first (supplemented with common best practises in IT) and work back from there towards a design, and then look at the sort of hardware, external support, SLA's with external companies, ...  you're going to need to implement that design.  

eg. you need mail. Are you going to do spam filtering and virus protection ? Yesn How ?  => this may have impact on how your network is laid out.
the  3 wireless networks with different privileges will also impact your network layout. 
So what will the network look like ?
how you going to route between them ? routers and firewalls ? VLANs and layer 3 switches ? => depends on what sort of  separation/connectivity/management you need on traffic going from one subnet to the other => you're back to your business needs

> What aspects are more important to you (security, price, possible external support, extra services) 
That's not a technical consideration, it's a business decision, or a decision that should follow from the business needs. Do you *need* external support ?  Can you afford it ? 
Do you have uptime requirements and how are you going to fulfill them ? 
etc.

---

### Post by Old_Grey_Wolf on 2011-05-26
> **koenn said:**
> you're going about it the wrong way.
You need to look at the business requirements first (supplemented with common best practises in IT) and work back from there towards a design, and then look at the sort of hardware, external support, SLA's with external companies, ...  you're going to need to implement that design.  


Looks like you have read Information Technology Infrastructure Library (ITIL).

---

### Post by koenn on 2011-05-27
> **Old_Gray_Wolf said:**
> Looks like you have read Information Technology Infrastructure Library (ITIL).

I haven't, but I think I probably should, some day. 

In my experience, if the design of an IT environment is based more on available technology than on business needs, you'll end up with a technically beautiful, elegant, robust, performant environment nobody uses because it doesn't do what the users need. 

It would be like an architect designing a house without any consideration for the needs, preferences and expectations of the people who are going to live there.

---

### Post by wizard10000 on 2011-05-27
> **Old_Gray_Wolf said:**
> Looks like you have read Information Technology Infrastructure Library (ITIL).

Anyone who does enterprise architecture should.

koenn's right.  You do a requirements analysis first and figuring out what make and model to buy is pretty far down the list.  What you *don't* do is preselect your hardware or software.

For example - "I want to run Linux servers."

That's great - but does Linux make sense in the business case?  You don't build a business case analysis to fit a certain platform, you run Linux if it makes sense.  On the server side it generally does, on the client side it generally doesn't  ;)

Everybody does this differently but in most cases hardware and software costs are inconsequential.  The vast majority of an IT budget is support (people) costs.

I think virtualization is a great thing but I personally don't virtualize mission critical servers.  That means depending on the size of the business, the mail and database clusters are generally standalone machines while web, file and print servers are good candidates for virtualization.

---

### Post by Old_Grey_Wolf on 2011-05-27
> **koenn said:**
> I haven't, but I think I probably should, some day. 


> **wizard10000 said:**
> Anyone who does enterprise architecture should.

Defining the Business needs and including them in the requirements for the design is a fundamental premise of ITIL.

---

### Post by pookiebear on 2011-05-27
how about the end around. This is what I have thrown at businesses just like this a bunch of times and it has worked.

Firewall: Sonicwall for firewall. (just because it does what a cisco does but is easier to configure)  They also have spyware and gateway anti-virus protection built in for a yearly service.

Wireless: HP access points for the wireless 1 for every 2000sqft  of floorspace. VLAN's for the 3 networks.
your secure wireless network (non guest) will need a XAUTH server. 
(just because they do what cisco APs do but at half the price)


Servers:
Linux servers for files storage and print serving.
exchange for email just because you want to mix it up. and exchange has good webmail and outlook and smartphone sync. But you could just use hosted exchange too from microsoft (easy)
Depending on the applications your SQL server needs you can run windows or linux.
I only sell HP server hardware. The OS's can be loaded virtual or not. Just depends on the size of the office. example. Your exchange server can also be your file and print server if you have less than 50 people in the office. I won't run SQL and exchange on the same box. 

Cabling
Fiber cabling to connect the switches on each floor run to code.
Depending on the construction you will might need plenum fire rated cat5e cable to the workstations CAt6 is never used in my area but it might be required for yours.

2 network cable drops per office. unless your phones are VOIP then you will want 3 unless they are pass through.


Remote sites: 
Sonicwalls are easy to configure for VPN between each other. 


Hope this helps. I sell this setup a couple of times a month.

---

