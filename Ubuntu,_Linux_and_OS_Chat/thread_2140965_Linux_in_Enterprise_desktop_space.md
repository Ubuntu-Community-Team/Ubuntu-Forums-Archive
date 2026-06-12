---
title: "Linux in Enterprise desktop space"
date: 2013-05-01
forum: Ubuntu, Linux and OS Chat
---

### Post by sytechie on 2013-05-01
Hi,
I am (Java/JEE) techinical arichitect and developer for a major IT consultancy and Linux supporter. I try hands on different linux flavors as part of my job. I found liking for Ubuntu in desktop use.
I feel linux is lagging in enterprise level desktop use and I will give my reasons for it.
I divide emloyees (for any size of organization) in three categories:
1. Managers
2. Office assistants (e.g. clerical, travel department etc.)
3. IT Specialists (from both development and support/maintainance)

Majority of non technical users don't care about OS and struck with M$ because of availability of user friendly and stable UI tools.

Key factors in enterprise desktop are:
1. Unified communication and collaboration tools
2. Good documentation tools
3. Security and Authentication & Authorization
4. GUI tools/clients for Enterprise applications
5. Tools for IT specialists (including operations and maintenance)

Organizations prefer one tool/client for one service for reasons of cost effectiveness and logistics (for procuring, training, installing and maintaining). In other words variety is good but not suitable for category 1 and 2 (i.e. non technical staff)

1. Unified communication and collaboration tools: This is the major hindrance in acceptance of Linux in enterprise desktop space. There are good independent tools exists for email, calendar, chat, voip and (only to some extent) meeting tools but they do not work together. Linux distributions has to either develop (or promote development) of a single collaboration tool (which has all above) or umbrella tool in which all these work together. Also need to work in partnership with Communication/collaboration server providers like IBM Lotus etc. to come out with stable and well featured clients (similar to their windows clients). (My sure guess is M$ won't even talk about Linux compatible tools for Outlook etc.)
2. Good documentation tools: Libre Office / Open Office is good but needs catch-up (and quickly). I think this will happen automatically if usage increases. Also these documentation tools should support (if not already) corporate templates/logos, headers, footers etc.
(I am mentioning about printing here, although technically it is not under documentation) Linux driver base of printers, ease of installation and managing, and support for standard preferences and settings (e.g. default setting for whole organization etc.)
3. Security and Authentication & Authorization: We all know that independently security is higher and more granular in Linux systems than in M$ Windows (which is like ground floor house with open windows having no metal grills). Needs more seamless integration with LDAP & SSO. Also need to parner with makers of corporate security tools like Symantec etc.
Also for IT administrators it is easy to manage what softwares are allowed and not allowed, automatic installations, versions in Linux than in Windows.
4. GUI tools/clients for Enterprise applications: This is another major hindrance of Linux in enterprise desktop space. Strangely not many enterprise application providers has GUI clients for Linux. Surprisingly this is same for even major ERP providers like Oracle, SAP etc. Enterprise applications which has browser based clients runs properly in IE only which is baffling. Siebel recommends Solaris / Unix / Linux for servers but officially supports only IE for client. Linux distributions has to work in partnership with these major ERP/CRM providers to have/improve GUI client for Linux and support for browsers like Firefox etc. (by promoting XUL instead of ActiveX etc.)
5. Tools for IT specialists: Who needs windows unless you are VB/.Net/C# developer. As a developer try running Eclipse, Database (Oracle or Mysql) and App server (JBoss or Weblogic) on your windows machine, you can have tea/coffee break between each Alt+Tab ;-). But not all green here. Linux lacks in development tools for enterprise applications. This is the major roadblock why Linux systems haven't accepted completely even by IT specialists.

To penetrate into enterprise desktop space, Linux has to win acceptance of category 1 and 2 employees. And for that areas (1) Unified communication and collaboration tools, and (4) GUI tools/clients for Enterprise applications need priority focus and out of which achieving (1) Unified communication and collaboration tools would be major coup.

Thanks,
Muneer Ahmed Syed

---

### Post by grahammechanical on 2013-05-01
Why have you posted this here? What has this to do with the members of this forum? I notice that this is your first post here. What do you expect from us? This is simply incorrect:

> [COLOR=#000000]Majority of non technical users don't care about OS and struck with M$ because of availability of user friendly and stable UI tools.[/COLOR]

Employees use whatever computer equipment their employer decides to buy. Some employees are actually better informed about computers than their employer and their managers. Many employees are just taught enough to do their job. They never learn all the functions of the software simply because they only need to use a small set of functions in order to do their job.

If Linux is lagging in Enterprise Desktop use it is because for decades computers have been sold with a Microsoft operating system pre-installed and so businesses are experiencing Microsoft lock-in. You must also take into account that many I.T. administrators have gained certifications in the administration of Microsoft products. They cannot recommend a system they are not trained to administer for they would have to learn new things.

I notice that you do not claim to have any experience of working in an enterprise. I worked for 25 years in a high street store for a company that had more than 300 stores. I remember when our store first received PCs. The staff were many women who were employed to operate a till and fill up shelves. They had to learn to use the PC for email, stock reporting and learn to use a PDA type handheld terminal for stock control. Some of these women were middle aged with no experience of computers but they learnt enough to do their jobs.

Later we got computers so that customers could order garments that weren't available in store. These women learned to access a Unix type online database. Did they know what they were doing? Yes, to the extent that they could do their job. But not beyond that. They learned as much as they needed to.

Those employees had no say whatsoever in what software was run on those computers. This was all decided by the head office IT department. This included the decision to stick with Windows NT on the desktop long after Windows Vista had replaced XP on the desktop. So, I do not accept that claim of yours. And that causes me to doubt the validity of your other claims.

Regards.

---

### Post by pfeiffep on 2013-05-01
What is your intention by posting here? Are you seeking guidance on how to roll out a major paradigm shift? 

In a large enterprise the responsibility for production equipment doesn't reside in the hands and minds of #2 in your list. Management and informed IT departments will dictate the correct technical tools for the enterprise, if there's a major shift in end user experience training sessions will be provided in advance to total adoption.

While you do make some valid observations the overall post is somewhat misleading, and IMO inaccurate.

What is your intention by posting here? 

Are you seeking guidance on how to roll out a major paradigm shift in technology?

---

### Post by prodigy_ on 2013-05-01
> **grahammechanical said:**
> If Linux is lagging in Enterprise Desktop use it is because for decades computers have been sold with a Microsoft operating system pre-installed and so businesses are experiencing Microsoft lock-in.

While this is certainly true for home users, no serious company ever uses pre-installed operating systems. Even if we leave potential security and compatibility issues aside, it's simply impractical to install the whole set of your required software manually on every computer you buy.

Corporations use Windows because Windows itself is backed by a very large corporation which is unlikely to go out of business or otherwise disappear. On the other hand pretty much any Linux distro may cease to exist tomorrow, including RHEL because Red Hat is nowhere near as big as Apple, MS or Google.

---

### Post by TheFu on 2013-05-01
TL;DR  I did skim, however.  I think you nailed many of the issues for corporate use, but some of your views are skewed towards your experience (as they would be) and don't necessarily reflect the entire world of corporate and government uses.

I'm an enterprise architect too, but came from a different history - cross-platform C/C++ (12+ diff platforms) and technical architecture (networks, storage, complex multi-tier applications and real-time systems).  I've worked with and for companies with 3 employees up to multiple companies with 20,000 to 200,000 employees around the world.  15 different companies in my career.  I've worked for very budget friendly clients where spending US$200M happened annually for a single project and for a Buddhist Monastery where $300 was a tough budget to be approved. Both were very rewarding, just in different ways.

Where I work today, at a small consulting business, we deploy F/LOSS by default. I think only 1 server remains running MS-Windows - it is for the accountants. All the other machines use F/LOSS. That goes for the infrastructure too.  Our clients are more typical businesses. They generally run MS-Windows on the desktop and a mix of UNIX, Linux and Windows servers in the back office.  When we discuss using more F/LOSS, I see they are envious, but must be cautious with their decisions.

BTW, we use these tools:
* openldap
* postfix (email gateway)
* Zimbra (communications server; enterprise calendar)
* Alfresco (DMS)
* Redmine (project management)
* vTigrer (CRM)
* nginx
* OpenVPN
* pfSense
* FreeNX
Clearly, these tools are not everything that large enterprises need, but they are a starting point for small and mid-sized companies from which to grow.  Transition is always harder than initial deployments. As more small companies grow that have never deployed any Microsoft software, more mid and large enterprise solutions will be created.

**Eclipse is not the answer - god I hope it isn't.  Java is not the answer either.  **More Ruby on Rails and more Python-based web apps are the answer for cross-platform server solutions - both internally and externally developed.  As a Java dev, I think you've been warped in your world view.  Java has a place - on professionally managed systems, not on the desktop.  **Your point 5 says more about Java development than enterprise development. **I know many RoR devs who run everything local - Postgress, nginx, multiple application servers, and their development tools inside virtual machines on their desktop PCs with plenty of excess RAM and CPU. These are modest machines - 4G of RAM, Core i3 desktops.  The same applies to C/C++ and Python and Php and Perl developers.  If you are unhappy with Java development, perhaps it is time for a change?  BTW, I remember when some Sun engineers visited the US government lab where I worked in the mid-1990s and showed us Java. We were developing a C/C++ app for 12 different platforms at the time, so Java seemed like the greatest thing possible.  Then we tried it and saw how slow it was.  **Sun promised that as Java matured, it would become faster.  that was almost 20 yrs ago. I'm still waiting.**

Unified communications and collaboration tools? Have you looked recently?
* Zimbra
* Alfresco
* Redmine

Here's a story about a company that removed everything Microsoft:  [http://news.cnet.com/2008-1082_3-5065859.html](http://news.cnet.com/2008-1082_3-5065859.html) Interesting reading for those that care.  For companies looking to migrate away from MS-Windows, I'd like to offer my help and expertise.  PM if we can help.  There are workable solutions today for many companies, but it needs to be a transition, not a revolution, if there is any hope of acceptance and cutting the Microsoft cord.  

The smaller a company is, the more likely that switching away from Microsoft is the best choice to be made today. Sooner is better than later.  Even if Microsoft can't be removed completely, a smaller footprint CAN save tremendous amounts of money and reduce the attack vectors from outside AND inside the network.

There are some places where migrating away from Microsoft doesn't make sense. There will always be a place for MS in the enterprise where it provides value to many companies, just not to every company.

---

### Post by sytechie on 2013-05-01
> **grahammechanical said:**
> Why have you posted this here? What has this to do with the members of this forum? I notice that this is your first post here. What do you expect from us? This is simply incorrect:

I posted in this particular area as header reads Forum -> The Ubuntu Forum Community -> Ubuntu Community Discussions -> Ubuntu, Linux and OS Chat.
If this is not the correct place, let me know appropriate forum.
My idea is to start discussion on limitations and areas to improve in linux for use as enterprise desktop.

> **grahammechanical said:**
> 
If Linux is lagging in Enterprise Desktop use it is because for decades computers have been sold with a Microsoft operating system pre-installed and so businesses are experiencing Microsoft lock-in.
 
No doubt MS Windows attained maturity because of the extensive use over the long period of time and Linux is lagging. That is the whole point, to brainstorm reasons for it and ideas to improve. I am suprised how you missed it.

> **grahammechanical said:**
> 
I notice that you do not claim to have any experience of working in an enterprise. I worked for 25 years in a ...

I didn't know I have to put my CV here before expessing an opinion. If you are so curious I have started my job 13 years ago as java and sql developer and also did solution design which involves identifying and proposing required software and hardware etc., but always considered my self as learner and disucssion is also one of the ways of learning for me.

> **grahammechanical said:**
> 
Employees use whatever computer equipment their employer decides to buy.  Some employees are actually better informed about computers than their  employer and their managers. Many employees are just taught enough to do  their job. They never learn all the functions of the software simply  because they only need to use a small set of functions in order to do  their job.

.......

I remember when our store first received PCs. The staff were many women who were employed to operate a till and fill up shelves. They had to learn to use the PC for email, stock reporting and learn to use a PDA type handheld terminal for stock control. Some of these women were middle aged with no experience of computers but they learnt enough to do their jobs.

Later we got computers so that customers could order garments that weren't available in store. These women learned to access a Unix type online database. Did they know what they were doing? Yes, to the extent that they could do their job. But not beyond that. They learned as much as they needed to.

You just said same thing in lot more words, what I said "Majority of non technical users don't care about OS". They just need required tool and knowledge to the use the tool (companies provide knowledge in some from ranging from user manuals to hands-on trainings)

> **grahammechanical said:**
> 
Those employees had no say whatsoever in what software was run on those computers. This was all decided by the head office IT department. 

Yes, those are decided by Head of IT deparment based on assessment, which sometimes based on he/she or his team feels which is suitable for the users or some times include feedback they recieved during training and usage by users.

> **grahammechanical said:**
> 
. So, I do not accept that claim of yours. And that causes me to doubt the validity of your other claims.

What ever you call it claim/suggession/idea/opinion, what I have put my opinion of deciding factors in selecting a software or tool.

Thanks,
Muneer Ahmed Syed

---

### Post by sytechie on 2013-05-01
My idea of posting here, is to open up the discussion on limitations and reasons (of low usage) of linux in enterprise desktop and ideas to improve.

---

### Post by sytechie on 2013-05-01
Thanks TheFu.

Mention of Java in point no. 5, was to give example (as you pointed out because of my exposure to it). But point I wanted to stress was makers of popular ERP and CRM systems even though support deployment of production software in Linux servers, but provide development tools / IDE only for Windows desktops but not for Linux.

Thanks,
Muneer Ahmed Syed

---

### Post by TheFu on 2013-05-01
I think that Linux is every bit as mature as Windows, it is just that 3rd parties haven't had an impitus to migrate their efforts.  To that end, only a very large client with deep pockets will make that possible.  A US-Government, a GM, an AT&T are needed to lead the way.  Google is doing it, but has their feet in other platforms for obvious reasons.  1M corporate users isn't enough.  We need 100M paying, corporate users, world-wide to make it workable.  Governments like Spain and Brazil have taken a lead.  Other governments with less-popular languages will probably follow, since waiting for native language releases of their OS is a sticking point for many of their users.

Commercial software vendor lobbyist in the USA will make it next to impossible for the US government to migrate to F/LOSS. We need political changes to campaign finance for that to ever happen.

Talking about issues is fine, but with our skills, we should really be evangelist towards these larger clients spreading the good-news of Linux in the enterprise and on the desktop.  Solution deployments of Linux desktops that reduce risk, extend desktop hardware lifetimes and still allow end-users to be highly productive should be our goals.

---

### Post by pfeiffep on 2013-05-01
> **TheFu said:**
> I think that Linux is every bit as mature as Windows, it is just that 3rd parties haven't had an impitus to migrate their efforts.  To that end, only a very large client with deep pockets will make that possible.  A US-Government, a GM, an AT&T are needed to lead the way.  Google is doing it, but has their feet in other platforms for obvious reasons.  1M corporate users isn't enough.  We need 100M paying, corporate users, world-wide to make it workable.  Governments like Spain and Brazil have taken a lead.  Other governments with less-popular languages will probably follow, since waiting for native language releases of their OS is a sticking point for many of their users.

Talking about issue is fine, but with our skills, we should really be evangelist towards these larger clients spreading the good-news of Linux on in the enterprise and on the desktop.  Solution deployments of Linux desktops that reduce risk, extend desktop hardware lifetimes and still allow end-users to be highly productive should be our goals.

I believe budget is also a stumbling block. Enterprise adoption would require massive changes in how IT budgets are allocated, and it's just possible that retraining everyone, redeploying everything just might outweigh the savings of not paying $ for the OS itself.

---

### Post by prodigy_ on 2013-05-01
> **pfeiffep said:**
> I believe budget is also a stumbling block. Enterprise adoption would require massive changes in how IT budgets are allocated, and it's just possible that retraining everyone, redeploying everything just might outweigh the savings of not paying $ for the OS itself.

Not to mention finding, testing and implementing new solutions to everything. There's isn't as much cross-platform software as some people think and while Linux-based alternatives exist for many Windows apps, they're not drop-in replacements in most cases. Now let's assume you have 1k servers and 100k workplaces worldwide and you want to migrate all that. Well, say hello to a 10+ years long project where cost estimates are going to be just wild guesses until you're about halfway through.

---

### Post by TheFu on 2013-05-01
> **pfeiffep said:**
> I believe budget is also a stumbling block. Enterprise adoption would require massive changes in how IT budgets are allocated, and it's just possible that retraining everyone, redeploying everything just might outweigh the savings of not paying $ for the OS itself.

You nailed it.  That is definitely true.  I've seen this on one of my projects even when the customer begged for a Linux-based deployment.  We just didn't have the time to achieve any return on investment in a reasonable time by deploying Linux for 22K users, rewriting device drivers and getting 3rd party software "certified" for Linux.  After less than an hour of estimating costs, effort, productivity and "other factors", it was clear the payback would take over 10 yrs.  It had taken them 10 yrs to get Windows integrated into their daily workflow, so migrating to some other solution was going to take at least half that time if the budget flowed.

OTOH, migrating 90% of desktop users to Linux desktops inside an average company shouldn't be too tough if they've been using standards-based solutions and avoided proprietary installations.  That is really the hard part - choosing a standards-based solution over the "fully integrated" solution pushed by the Microsoft business machine and AVR network.  I feel for these small and mid-sized companies who have deployed 100% Microsoft solutions because they've never talked with anyone else except Microsoft-centric solution providers.

For large customers, they need to migrate slowly, avoid desktop stuff for some time. Start with file and print servers. Those work and work well.  Then slowly dismantle other infrastructure stuff that seemed great from the sale brochure, but turned out to be less-than-great after deployment.  Sharepoint and MS-Project server would be next on my list.  Then I'd replace DHCP and DNS choosing a F/LOSS alternative.

As time continues, I'd make a conscious choice for standards-based solutions, NEVER proprietary.  Ok, almost never.  We know that sometimes there is the solution that is possible vs the solution we want, right?  New contracts would require support for non-proprietary clients.  No more IE, but current generation browsers. For a large enterprise, dictating this sort of stuff happens all the time.  If the architecture team doesn't have the budget control to force this, let data security do it.  Sure, the initial contract won't support the "desired state", but as terms of that contract, include that corporate architecture and security standards will need to be solved for following releases.  Where I worked, we'd get a corporate officer to sign off on this addendum to contracts, which would force a corporate officer of the vendor to respond.  That would make this a priority at the vendor.  Clearly, some vendors don't play - I can think of 3 - Microsoft, Oracle and ... can't mention the next.  All the other vendors will - the size of the contract made certain about that.  

Being a large enterprise does mean being able to dictate to vendors. Use that power wisely.

---

