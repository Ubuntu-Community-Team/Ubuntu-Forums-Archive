---
title: "Company Linux Requirements"
date: 2019-10-17
forum: Ubuntu, Linux and OS Chat
---

### Post by daniel-patrick on 2019-10-17
1. Apart from saving money on licenses, how feasible is it for companies to use Ubuntu Linux?

2. Are most companies shifting to Linux nowadays?

3. What's the best Linux server distro to use for a company with approx. 150 users? The clients have Linux Ubuntu version 18.14 installed on them where other machines using MacBook Pro. 
Since this is something new for me, is there someone where I can do some reading about this?

---

### Post by slickymaster on 2019-10-17
Not a support request.

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by SeijiSensei on 2019-10-17
The answer to your question depends entirely on your company's work flow. If people rely on MS Office products, then moving to Linux will be difficult. Other issues concern things like authentication. Is your company running Active Directory?

Most companies are not, as far as I know shifting to Linux. If anything, they're shifting to cloud-based services.

Any distribution can handle hundreds of clients if the hardware is robust enough.

---

### Post by TheFu on 2019-10-17
> **daniel-patrick said:**
> 1. Apart from saving money on licenses, how feasible is it for companies to use Ubuntu Linux?

2. Are most companies shifting to Linux nowadays?

3. What's the best Linux server distro to use for a company with approx. 150 users? The clients have Linux Ubuntu version 18.14 installed on them where other machines using MacBook Pro. 
Since this is something new for me, is there someone where I can do some reading about this?

1:
It depends.
It depends on the sorts of programs that each group of desktop users actually use.
It depends on how the company works with external clients/organizations.
It depends on how much upper management is pushing to kick MSFT out.

2: 
Every company where I've worked since 1993 has had *some number* of Linux doing production workloads.  They also used Windows and UNIX.  Since around 2004, lighter UNIX workloads have been shifting to Linux. That has been extremely common.  A few 100% MSFT companies have migrated some of their formerly Windows-Servers to Linux servers.  Linux doesn't have licenses (usually). Linux doesn't require payment of CALs.  Linux systems are much more stable, if run by knowledgeable admins.  1 Admin can manage thousands of Linux systems around the world. Being physically near the computer isn't necessary and hasn't been since before Linux existed.

3:
There is no "best Linux server distro".  It depends on what the needs are.  For servers, almost all the well-know distros are mostly the same for how things are configured, just minor differences. Different distros have different goals that different businesses would rate differently.  It depends is the only answer from the provided data.

I don't know what 18.14 is. For Unix systems, details matter and prevent confusion.
I haven't any clue about OSX, beyond being too frustrated dealing with it for 2-3 weeks that I wanted to throw the machine against a wall.

Years ago, I wrote a long post here about what a business should do to plan their migration to Linux.  I'll try to find it, but it was a long time ago. It was lots of lists, lots of accounting, lots of farming out determining Linux alternatives to each impacted team, getting buy-in by each group AND ownership for the success.
And it includes having a few Windows Servers (used to be called Terminal Servers) where hold-outs could remote desktop from Linux into Windows to run the last Windows-only software.

I've been asked by my boss to migrate 22K laptops to Linux from Windows. These laptops has very specialized hardware diagnostics software loaded that didn't have Linux alternatives and would cost tens of millions dollars and a few years to get the software created for Linux.  Took me about 30 minutes to make a SWAG estimate of the costs and time required to accomplish the transition.  Not all businesses can switch within the allowed budget and realizing that quickly is important.

I've also worked at places where we ran 100% Linux software for all but 2 things.  Quickbooks and In-Design.  Everything else was F/LOSS.  We supported standard protocols on all our servers and let the desktops make the connections using whatever client OS they liked. Company policy was that no business data was to be retained on any clients.

While you are doing a migration, be certain to setup data backup and data retention policies.  Nobody will be happy about this extra work, so having the CxO guys standing together saying it was needed for the company's long-term viability will be very important.  We lost 2 senior sales guys over a switch at one place. They had addons for MS-Outlook and didn't like the change from MS-Exchange to Zimbra.  If we were changing, in their minds only Salesforce would be worth it.  We were deploying a F/LOSS solution, which they saw as detrimental to their skillset.  There are some dynamics like that which aren't technical, but play a role.

---

### Post by SeijiSensei on 2019-10-17
I recall a woman at one client's workplace who told their IT guy she could no longer do her work. Turns out an icon had been moved from one location on the screen to another. Yes, the issues involved as really as silly and petty as this.

---

### Post by Tadaen_Sylvermane on 2019-10-17
I know nothing about existing businesses. I know that if I was to start an IT of some sort business I would do my best to use Linux all the way around. At the bare minimum all backend and server infrastructure would be Linux. If desktops require Windows only software though, not much choice.

> [COLOR=#000000]Yes, the issues involved as really as silly and petty as this.[/COLOR][COLOR=#000000]

Also called a pink slip. I would never hire or accept stupidity if I could help it. It saddens me that employers don't demand some level of critical thinking. Rather they want trainable robots who can't find their way out of a paper bag.[/COLOR]

---

### Post by daniel-patrick on 2019-10-18
We are a new company so nothing has actually been implemented yet. 


I meant Ubuntu version 18.04 and not 18.14.


I'm asking to get a better overview of what I'm about to expect.


What certifications would you recommend? 
I thought of starting with the LPIC-1, LPIC-2 and LPIC-3.

Any other certifications you'd recommend?

---

### Post by mastablasta on 2019-10-18
> **TheFu said:**
> 1:
It depends.
It depends on the sorts of programs that each group of desktop users actually use.
It depends on how the company works with external clients/organizations.
It depends on how much upper management is pushing to kick MSFT out.



and also depends on the commission that the management is getting for pushing MS products.

---

### Post by TheFu on 2019-10-18
> **mastablasta said:**
> and also depends on the commission that the management is getting for pushing MS products.

I have never seen this. Management is looking for the best deal and sometimes using F/LOSS to get a huge price drop when they don't ever actually intend to move away from MSFT is a strategy deployed.

Care to provide a source that any management of any company buying for in-house use is given a commission from MSFT?

---

### Post by sdsurfer on 2019-10-18
> **daniel-patrick said:**
> 
We are a new company so nothing has actually been implemented yet. 
.....
I'm asking to get a better overview of what I'm about to expect.


For this you would have to follow the business plan from end to end, and decide what OS and software you're going to work with globally based on the requirements and resources.

What that means is it depends on what you need to do via software and who you plan to hire to do the actual work and the cost of those hires. Let's take an example.

You're a company that has a plan that involves a lot of video editing and deployment to succeed. Although there are some video editors in Linux, the employable resources to do that with any proficiency are fairly slim, that is, there are not a lot of true professionals in the field (this statement may be incorrect, but stay with me on the idea . . . )

This gets back to the basics of supply and demand. For those few professionals who edit video in Linux, you are going to consider higher salaries.

In Windows and Mac, developers who can work with Adobe Premiere are almost a dime a dozen. Supply and demand; you can probably hire two video developers for the cost of one if they work in Mac or Windows (Adobe simply does not support Linux.)

In this scenario, it may be more cost effective to work with multiple operating systems, and now your challenge becomes networking the different operating systems together reliably. Or form a plan to have the OS based in Linux with a standard of working with VM's to do the video work.There are tons of paths through this scenario, it depends on which will reliably bring you success in the most cost effective way.

So, the question you are really asking without further details is "how long is a ball of string?" :-D

---

### Post by TheFu on 2019-10-18
> **daniel-patrick said:**
> We are a new company so nothing has actually been implemented yet. 


I meant Ubuntu version 18.04 and not 18.14.


I'm asking to get a better overview of what I'm about to expect.


What certifications would you recommend? 
I thought of starting with the LPIC-1, LPIC-2 and LPIC-3.

Any other certifications you'd recommend?

All infrastructure can easily be Linux.  Make a list of what you consider infrastructure. start with authentication/authorization and backups.  I'd have at least 3 different subnets to start.  Think about security first and always, even before the first network is created.

I don't recommend any certifications, but the LPIC knowledge is fine.  It is too easy to become a cert-test-taker and not actually learn the skills.  We see this all the time - people with long lists of certs without any practical knowledge.  Seek out people with a Linux-first attitude, but not total zealots.  Zealots are great for F/LOSS projects, but not in a business.

Have a plan for when there isn't a Linux solution to a problem.  For example, my company never found a reasonable Linux solution for accounting and taxes. The accountant wasn't going to change and our external accountants needed specific file transfer formats.  Some fights aren't worth the effort.

---

### Post by monkeybrain20122 on 2019-10-28
Depends on your type of business. I work in AI, it is a Ubuntu shop. There is supposed to be one Windows machine somewhere but no one ever uses it.

---

### Post by Skaperen on 2019-10-28
> **daniel-patrick said:**
> We are a new company so nothing has actually been implemented yet. 
your company can avoid a lot of costs by going directly to cloud-based services for everything that does not absolutely need to be local.  then Ubuntu can serve you well as the OS for each workstation in front of each user.  one local server is then all you really need (for a secure tunnel to your cloud network, files that need to be extra fast, and maybe a few administrative things).  your "computer room" can then just be a closet with you internet access, telco access, LAN switches, phone switch, and patch panel).


> **daniel-patrick said:**
> I meant Ubuntu version 18.04 and not 18.14.
if you can hold off 3 more months, 20.04 LTS will be coming out, then.


> **daniel-patrick said:**
> I'm asking to get a better overview of what I'm about to expect.
expect the world to be shifting to cloud-based services.  by starting out there, you can avoid those costs and headaches.


> **daniel-patrick said:**
> What certifications would you recommend? 
I thought of starting with the LPIC-1, LPIC-2 and LPIC-3.

Any other certifications you'd recommend?
i can't help in this area.  i don't do certifications.  are you going to be the system administrator?  the network administrator?  CTO?

---

### Post by TheFu on 2019-10-28
> expect the world to be shifting to cloud-based services. by starting out there, you can avoid those costs and headaches.

I would respectfully disagree with this statement.  Run the numbers, annually, to see which makes more sense for your needs.  Don't forget to include the cost of outages due to cloud failures.   Initially, starting out the cloud will seem cheaper and for specific services, it most definitely is the case.  
8 hr S3 outage last week: [https://www.infosecurity-magazine.com/news/aws-customers-hit-by-eighthour-ddos/](https://www.infosecurity-magazine.com/news/aws-customers-hit-by-eighthour-ddos/)

Nobody will care about your services or security like your own employees will when their jobs depend on it. This depends on having people with appropriate skills.  "Cloudy" services don't always include appropriate security.

---

