---
title: "Web and Cloud Development Costs"
date: 2015-02-14
forum: The Cafe
---

### Post by phosphide on 2015-02-14
Hey everyone,
I am starting up a new business and looking into web services and cloud storage solutions (Amazon, Azure, etc.). I have been having some difficulty trying to calculate startup and recurring costs (primarily the recurring). Was hoping some of you Linux or web developers might have some insight into this (as well as some mistakes to avoid). I would like to do Linux based instead of MS.

I can't go into the nature of the business but it would be a web-based platform for desktop, tablet, and mobile. The best way to describe this software is that it's a utility, something a team of people would use to communicate and collaborate while also being used for analysis and media storage. There would be multiple people on the software at the same time with various user-permissions (need to tie to CRM system and other components). Storage seems fairly easy to calculate based off how much we anticipate offering, but not quite sure about the web services (number of requests, get/put requests, hours of instance usage, number of instances). How much is necessary to get started? At what point should we buy more? Should we purchase based off the number of users/teams? What else should I consider and need/don't need?

Appreciate the help.

---

### Post by SeijiSensei on 2015-02-14
I'd give some thought to renting a virtual machine from a reputable provider like [Linode](http://www.linode.com).  You could start small and build your applications on a server in the $10-20/month range.  If your business takes off, you could then migrate to their heftier options.  This method also gives you a predictable monthly cost with a means of estimating how your costs might grow over time.

---

### Post by phosphide on 2015-02-15
Thanks SeijiSensei. I like their setup and will definitely give them a look. I think they would be good for starting out, but don't know about long term though. Do you have experience using them?

---

### Post by SeijiSensei on 2015-02-15
I have three servers with them and have had at least one for three or four years now.  I think I've experienced at most three or four outages in that time due to scheduled maintenance, but they all happened over night and lasted only briefly.  I've also found their snapshot backup service invaluable as well as the ability to log into the host system and mount your VM as a filesystem.  I once accidentally deleted a key OpenSSL library from a CentOS server, and pretty much all the services came to a halt.  I was amazed to discover I could download the missing file and insert it into the mounted VM image.

Having data centers around the globe is also a big plus.  I have one server in Newark and another in Fremont, CA, so they are both geographcally and topologically separate in case of disaster.

Linode has excellent technical support as well.  They've always been prompt, helpful, and accurate when I needed assistance.

Having had physical servers in my own and clients' offices, I can only say I'm really glad not to have to worry about hardware problems ever again.

---

### Post by Sasha_Aderolop on 2015-02-16
[h=3]"Small Class" Development Companies[/h][LEFT][COLOR=#333333][FONT=Arial]These types of businesses run their operation on a very low budget and usually has only 2-3 workers including the business owners / partners in the company.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]Their proposals are usually based on estimated hours at the development rate ranging from $75 - $180 per hour.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]These types of businesses are usually not organized. They cannot take on a large development project.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]When you hire this type of company, the result of your project is based on the company owners or management's ethical standards or honesty, experience in development, design ability, usability awareness, SEO practices, development specialty and other relating factors.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]These types of development companies are a perfect fit for servicing small budget business clients, for example, a small one location - mom and pop ice cream shop.[/FONT][/COLOR][/LEFT]

---

### Post by Matthew_Harrop on 2015-02-16
> **Sasha_Aderolop said:**
> **"Small Class" Development Companies**

[LEFT][COLOR=#333333][FONT=Arial]These types of businesses run their operation on a very low budget and usually has only 2-3 workers including the business owners / partners in the company.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]Their proposals are usually based on estimated hours at the development rate ranging from $75 - $180 per hour.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]These types of businesses are usually not organized. They cannot take on a large development project.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]When you hire this type of company, the result of your project is based on the company owners or management's ethical standards or honesty, experience in development, design ability, usability awareness, SEO practices, development specialty and other relating factors.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]These types of development companies are a perfect fit for servicing small budget business clients, for example, a small one location - mom and pop ice cream shop.[/FONT][/COLOR][/LEFT]


Whats your source? Have you used them before? 
I don't mean for that to sound rude if it does, I am just curious to know how you know.

---

### Post by tgalati4 on 2015-02-17
Be mindful that the bandwidth costs will often exceed the cost of storage and CPU for cloud services.  Since your service model is multi-platform, those bandwidth costs will be difficult to estimate and how those costs grow as your service scales is also difficult to estimate.  Collaboration and CRM implies lots of people and lots of simultaneous connections, so bandwidth performance (and its associated cost) may be key to success of this service.

I would set up two identical cloud services and run them for a year and compare the bandwidth performance, the overall cost, uptime, and hotline service performance--after a year, you should have a good comparison to make a decision going forward.

Without knowing your business model, it's difficult to make a single cloud service recommendation.

---

### Post by SeijiSensei on 2015-02-18
A $10 Linode comes with 2000 GB of transfer per month, and the amount of bandwidth goes up with the size of the virtual server.  I've never even come close to hitting the bandwidth limits.  Disk storage is where the costs lie in this model.  A $10 server comes with 24 GB of storage.  I have a larger one with 74 GB that costs $30.  That's fine for many applications unless you're intending to archive video.

---

