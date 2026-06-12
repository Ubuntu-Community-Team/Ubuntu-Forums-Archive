---
title: "Do people see a market for makeing an Ubuntu Workgroup Server"
date: 2008-05-13
forum: The Cafe
---

### Post by tymiles on 2008-05-13
I know, I know every so often bring up this issue. Not that I can program or develop so I can't really help do this but it drives me nuts that no version of Linux (Other then Xandros Server) has tried to go for the workgroup server/desktop market. 

Yes, this is Microsoft's domain. They prob have 90 percent of this market on a bad day. I guess cause I wear glasses I don't see why a Linux company has not tried to get into this market themselves. 

What I mean by Workgroup market is MS's bread and butter. Windows XP for the client, Windows 2003 / 2008 server for file sharing, print sharing, AD for identity management, Exchange for email. With Windows its easy as pie to set up a Windows 2003 server with DHCP, DNS and AD then add a bunch of Windows XP machines and have them auth and connect to the Windows server and then share files to the XP machines and also hang a few printers off the server. My 15 year old brother was able to do this in about 20 minutes (Not including the time to install and patch Windows) 

Xandros has done a pretty good job at this but 1. They charge too much for a first time (Well now on version 2) server product from an almost unknown company and 2. The desktop product is too clunky. Xandros should lower the price of the server product to slightly over the price of the desktop. And they should make their management and auth tools that are in Xandros pro desktop available for most versions of Linux. 3. They have extra third party pricing for Email, BRU backup server, Helix Streaming Media Server etc. They should limit those prices like MS does in their small business product. 

But enough about them, the main reason for this is I don't see why a company like Ubuntu has not gone down this road. I would not even be mad if they came out with a framework that went on top of Ubuntu server (like Xandros bridgeworks) that they would charge for. If in the end I could quickly and reliably do what I can do on Windows. Or better yet what I can do on Mac OS X server I would pay for it so it would get better. 

So why do I mention Mac server? Because Apple uses all the software that is available to Ubuntu: Open Ldap, Cups, Samba, Apache etc to make a pretty good workgroup server product. If it was not Mac only and ran on any server, I would choose it over Windows server anyday. I don't know why Apple doesn't make Mac server platform independent. This is the gap that Ubuntu could fit right into. 

The funny thing is that Xandros is coming out with their Bridgeworks product soon for most versions of Linux (It's out for Xandros, Red Hat and Oracle / CentOS Enterprise Servers)and I will be able to then take a group of Ubuntu Servers and make them into a workgroup that will work with Linux and Windows. And Xandros will make that money if it's priced right. I think Ubuntu could do better and take that market if they wanted to! 

Anyway people let me know what you think. Do you think this is a market for Linux? Is Microsoft just the king of this and everyone else should leave it alone? 

Post and let us know what you think!

For you reading:

[http://www.xandros.com/products/business/server/overview/managed_community.html](http://www.xandros.com/products/business/server/overview/managed_community.html)

[http://www.xandros.com/products/business/server/overview/xmc.html](http://www.xandros.com/products/business/server/overview/xmc.html)

---

### Post by jetsam on 2008-05-13
> Not including the time to install and patch Windows
...that would be cheating.  ;)

Plenty of people already fill this role with Ubuntu, Mandriva, Fedora, Centos, or any of a number of other distros.  There's also a few that specifically target it: [Clark Connect]("http://www.clarkconnect.com/") and another whose name escapes me now.

There was some talk a while back about an Ubuntu Home Server, but I'm not sure what happened to that.  

So, yes there's demand, and yes configuration could be easier, but I don't agree that this is a good reason to add a proprietary layer to the software stack.

---

### Post by tymiles on 2008-05-15
I am not that gung ho about a proprietary layer in the software stack, but in reality it doesn't have to be in the software stack, it would be an add on for those who want to pay for it. Since it doesn't exist at all right now on Ubuntu I don't think it would be bad. 

Or they can do what Red Hat is doing and making Red Hat Identity Server a paid and open product. So you can get it as Fedora Directory server (If you just need directory services) or with all the tools as Free ISA

Having tools for their paid customers is also not out side Canonical's business model as they have several proprietary tools, most important on Ubuntu being the landscape system management tool. 

But I used to use Clark Connect and I have used SME server etc. None of them actually do what I am trying to do which is look for a robust scalable solution. 

Lets look at SME or Clark Connect. They both offer stuff really good for a really small company. You can use them as your gateway server, web server, mail server, file server, you can auth Windows machines against them etc. But they are not scalable, meaning if you need more then one server there is no way in Clark Connect to out the box create a directory structure or to make a domain structure. Which I can do out the box with Xandros, Windows and Mac server. 

What if you want to manage your PC's and multipule servers from one interface. You can do that with Windows, Xandros and Mac.

So if I have a small company say 3 people, with Windows, Xandros and Mac I can manage my whole business and then as the business grows I don't have to come up with a whole new solution. 

With Windows I can use Windows SBS which comes with AD, Exchange etc. Then if my business grows over 50 users, then I can migrate from SBS to regular Windows 2008 server. With Xandros and Mac I just add more servers as the company grows and don't even need to migrate. 

But people, add more input! Thanks.

---

### Post by Mr A Mouse on 2008-05-15
> **tymiles said:**
> What I mean by Workgroup market is MS's bread and butter. Windows XP for the client, Windows 2003 / 2008 server for file sharing, print sharing, AD for identity management, Exchange for email. With Windows its easy as pie to set up a Windows 2003 server with DHCP, DNS and AD then add a bunch of Windows XP machines and have them auth and connect to the Windows server and then share files to the XP machines and also hang a few printers off the server. My 15 year old brother was able to do this in about 20 minutes (Not including the time to install and patch Windows) 

It can be done, and (as you note with Xandros) it has been done ... but like the others, I'm not fond of the idea of adding a proprietary software layer. More importantly, all of the functionality you speak of above is *already available* in every distro of Linux that I've worked with.

The only real problem is there is no unified GUI to control all of this functionality ... but for someone already familiar with network setup and unix administration, it's a piece of cake to set this up via the command line.

---

### Post by tymiles on 2008-05-15
> **Mr A Mouse said:**
> It can be done, and (as you note with Xandros) it has been done ... but like the others, I'm not fond of the idea of adding a proprietary software layer. More importantly, all of the functionality you speak of above is *already available* in every distro of Linux that I've worked with.

The only real problem is there is no unified GUI to control all of this functionality ... but for someone already familiar with network setup and unix administration, it's a piece of cake to set this up via the command line.

True, but most people have no clue how to use the command line. Which is why Novell now has to answer to MS and not the other way around. And why MS has 90 plus % of the office server market. 

My first cert I got was the Novell CNA and I remember when I would be working that the MS sales people used come in and sell Windows by saying it would lower costs because you would no need so many specialists on staff. As we know this tactic worked because they were right. Things like password resets, new user accounts and Exchange accounts are a snap using the AD users and computers MMC. Easy for a help desk to use. Easy for a small business to find a tech / admin to handle. 

Also like I said before for business customers what matters are the tools and how well they work. They don't care about proprietary or not. Yet at the same time Canonical could still follow the Red Hat model with Red Hat identity Server. Red Hat has a paid version and they have a free version. Fedora Directory Server / Free ISA (FDS with added features) 

In the end Canonical has to make some money. Having some paid add ons while keeping the core Ubuntu that is free now always free to me is a good trade off. Better then one day seeing Ubuntu gone or turned into a fully commercial company and everything is paid like Red Hat. (Not including Fedora)

---

### Post by Mr A Mouse on 2008-05-15
> **tymiles said:**
> True, but most people have no clue how to use the command line. Which is why Novell now has to answer to MS and not the other way around. And why MS has 90 plus % of the office server market. 

My first cert I got was the Novell CNA and I remember when I would be working that the MS sales people used come in and sell Windows by saying it would lower costs because you would no need so many specialists on staff. As we know this tactic worked because they were right. Things like password resets, new user accounts and Exchange accounts are a snap using the AD users and computers MMC. Easy for a help desk to use. Easy for a small business to find a tech / admin to handle. 

Also like I said before for business customers what matters are the tools and how well they work. They don't care about proprietary or not. Yet at the same time Canonical could still follow the Red Hat model with Red Hat identity Server. Red Hat has a paid version and they have a free version. Fedora Directory Server / Free ISA (FDS with added features) 

In the end Canonical has to make some money. Having some paid add ons while keeping the core Ubuntu that is free now always free to me is a good trade off. Better then one day seeing Ubuntu gone or turned into a fully commercial company and everything is paid like Red Hat. (Not including Fedora)

This is well thought-out on your part, and I have to admit I answered your question like a hobbyist, rather than like a business person.

Is there a market? Perhaps for a while. One possible problem that I can see is if Canonical came out with a proprietary "Command and Control" software, it would most likely swiftly be analyzed and "cloned"--if not by the community, then definitely by competing companies. Heck, I would not be terribly surprised to see Microsoft quietly reproduce such a toolset and distribute it for free (via some form of shell group, to keep their interests in the cloned toolset secret).

Is there a viable market? I fear I do not know. It's certainly an interesting project, but perhaps I'm too tech-bound to think like a manager and give a good answer.

---

### Post by tymiles on 2008-05-15
You right about the clone part. That surely could happen. :-( 

The interesting thing is that Xandros actually got their server management software into a Microsoft product. 

It's called: Xandros BridgeWays Management Packs for Microsoft System Center. 

But really, the only reason I have this sort of thought out is because I am a SMB consultant and I look for these types of solutions for my customers. In the end I almost always have to come back to using MS products and it drives me nuts! :-( 

What I would really love to see is if someone could GPL Banyan. For those who don't know Banyan was one of the first NOS's to use LDAP etc for user management.

The Vines OS was Unix system 4 and they used LDAP for everything. One of the people who started Banyan was James Allchin of MS fame. 

Banyan was the company that came in and showed MS how to do AD right. 

When Banyan went out of business they took their software with them. It would have been great to of seen that GPL'd 

[http://en.wikipedia.org/wiki/Banyan_VINES](http://en.wikipedia.org/wiki/Banyan_VINES)

---

