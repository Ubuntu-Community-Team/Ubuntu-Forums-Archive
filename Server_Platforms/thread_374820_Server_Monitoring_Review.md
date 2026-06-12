---
title: "Server Monitoring Review"
date: 2007-03-03
forum: Server Platforms
---

### Post by SuperMike on 2007-03-03
Here's my review of some server monitoring products if you're planning on considering a monitoring tool for watching your Ubuntu servers.

**BMC Patrol**
This is non-free. The older version was an agent design and froze up a lot. It's in perpetual beta and I found myself constantly updating the agents, ripping my hair out. The newer design is agent-less, but it looks like they went back to the blackboard on it is not mature compared to other products. It's also expensive and non-intuitive. The install is a nightmare. Don't use this product. It can drive a man to drink.

**Hyperic**
This is free and open source, but you'll probably want to purchase it and get the support. This is a sensational product except for two huge problems. One, it requires a hefty JRE and footprint for the server agents. The developers in your company may not like the fact that you may have to maintain more than one JRE on a server just so that Java works for one app and doesn't interfere with another app. Two, it is not an agent-less design and is therefore very time-consuming and problematic. The guys who make Hyperic should just go back to the blackboard with this thing as a prototype, and rewrite it in something like JSP or SSJS (since they have an investment in Java), or perhaps Python or PHP, and then switch it so that it uses an agent-less design.

**Nagios**
Great product, snap to install, but it's immature. You'll want something more. I believe Nagios has an agent-less design. Still, it's cheap to purchase and easy to maintain. It's also open source and free if you want to go that route too.

**Zenoss**
Sensational product if you can ever get the dang thing installed. It has a steeeeeeep installation process that's problematic, even when following their instructions. You'll keep scratching your head why?? If they could ever fix that, the product will sweep the planet and take the marketshare, easily. Also, this product comes in a free open source version and the same version + tech support in a pay version.

**SiteScope**
This is another non-free one, although you can download a ten day eval. It costs about $45 per thing to monitor on a server in 2007 (current bulk pricing). SiteScope can do a whole lot, has a super-easy installation process, but it's interface is sometimes slow and non-intuitive. When you want to do several things at once for large quantities of servers, it's not intuitive in the interface how to speed this up until you learn copy, paste, and global replace, using a Content tab that you might otherwise ignore if you weren't poking around. Oh, and another thing -- to monitor both Windows and Linux, you have to install on Windows, but to install Linux only, you can install on Linux. Doesn't make much sense, but it has to do with the poor netbios APIs on Linux. (And that's Microsoft's fault, not Linux's.)

**HP OpenView**
Actually I hear this is going to be phased out. It's a rumor. HP purchased Mercury and SiteScope is going to be the new OpenView. I don't know how that's all going to work out, or if that's true. But it was enough to spook me out and to not try it.

**Summary**
One bad thing to note about HP (regarding SiteScope or OpenView) is its god-awful tech support. HP's tech support makes Dell's support look good.

On the agent-less design, most of these products go through either SSH and gather stats, or they can also go through Remote Registry Service, SNMP, and Windows Performance Metrics.

All and all, SiteScope in my opinion was the winner for now, although perhaps a future version of Zenoss might win in the long run.

What I did notice, however, was that we're not talking rocket science here. If you're a decent web developer with some experience in socket programming, you could build your own product and mint your own money. You can also look at the source for Nagios to see how it does what it does. All you have to do is get a pencil out, install Zenoss, Nagios, and SiteScope, configure each for a real world environment, and write down what frustrated you about it. Then, develop a product that doesn't have any of this frustration and doesn't add any more.

---

### Post by szocske on 2007-03-13
Hi!

I'm just getting familiar with Hyperic, but already feel I must advocate it :-)

It is of robust design based on a database backend, JBoss for logic, TomCat for GUI.
To get monitoring only, you can use it without installing agents on monitored hosts just fine: it can collect SNMP data just like the simpler systems in your review can.

The agent however enables loads of more sophisticated things, for example advanced data acquisition for common server software (RDBMs, web- and application servers, virtual machines, etc) out of the box, control actions for supported services, and an easy to extend API.

Bottom line: (bottom two lines, really)
Want monitoring only? Use the monitoring-only apps.
Want monitoring and management? Go for Hyperic!

---

### Post by SuperMike on 2007-03-14
I think it's the "robust design" of the Hyperic agents that frightened the developers. It's the same reason they don't like to put XWindows on a server. First, the agents require a JRE, and that has heavy resource requirements for something so simple. Second, the JRE could potentially cause conflict with an existing JRE used for services on a server for an application object farm or web farm. You may have to maintain separate JRE versions between the agent and the apps running on a server. Third, there's not much more the agents can offer that you can't glean from SNMP + SSH. Since SSH and SNMP is usually already enabled on a production server (a usual preference), why open another port and add another agent?

This is why Zenoss and SiteScope stand out among the rest. My chips are behind Zenoss, but if a company refuses to go open source for such a solution, they can use SiteScope fairly effectively.

---

### Post by dannyboy79 on 2007-03-14
not sure what is meant by monitoring but I would say that tripwire is an awesome intrusion detection program! there's even a non-free version for large corporation with tons of servers. we use it at my company and we have 22000 staff worldwide, and that stat is from 2000.

---

### Post by bitfoo on 2007-03-27
> Nagios
Great product, snap to install, but it's immature. You'll want something more. I believe Nagios has an agent-less design. Still, it's cheap to purchase and easy to maintain. It's also open source and free if you want to go that route too.

Uhh...did you even use Nagios?  Nagios has been around ***forever*** (it's the successor of NetSaint), so it is hardly immature.  It also includes agent support via NRPE or NCSA, so you can monitor tons of things via those, as well as SNMP.  Also, it's not cheap.  

It's freaking **free**.  As in beer and speech. :|

Hyperic does look good, but the professional version is very expensive, something like $750 per socket, and they count two cores as one socket, so a quad core box needs two licenses.  Yeah, it gets real pricey.  But the free version is pretty damn good.

I haven't tried Zenoss yet but I'm going to tomorrow.

Also don't forget your other options like BigBrother, hobbit, zabbix, munin, and OpenNMS.  But I'll leave those as an exercise for the OP. ;)

---

### Post by davidc502 on 2008-01-01
I've been with HP for 3 years now, and I want to agree with Mike; hp's support sucks something awful!

Yes, SiteScope will replace HP Internet Services, but not Node Manager or Operations. The real "change" is OpenView will be called HP Software. WoW :sarcasm

One note: HP is aware of its support, and is working to remedy the problem by downsizing the 800 applications it currently supports. Time will tell if they are able to be more customer focused.

Like I said earlier I've been with HP and currently work on Node Manager, Operations, Internet Service, Performance Manager (no expert there), and now SiteScope, and they all have problems! lol In the past I've created incidents and all they want to do is shoot emails back and fourth suggesting trouble-shooting. They never want to bring in a engineer to log in a fix these problems. Over time I've learned to stay away from their support, and try to script work arounds if I can.

The company I work for is in too deep to change software, and even if we went with one of the smaller software companies it would probably be bought out by HP thus thrusting us back under their umbrella. 

I'll do with what I've got.

---

### Post by darrinjacks on 2008-01-06
One tool I have started working with is pt360 from PacketTrap Networks. The software has a super simple network monitoring dashboard with device specific gadgets like CPU, Memory, Availability, etc. The gadgets change colors when warning and critical thresholds are reached for clear device performance issues. A cool feature is that gadgets drag and drop to create different views, similar to iGoogle. A key feature that PacketTrap developed was to integrated ~12 diagnostic tools ping, snmp, trace router, DNS, etc. that can be run within the software. Many products say that, but my experience is that means I need to integrate others. No time to always do that or unlimited budget to pay for it.

I am familiar with most of the packages listed here, but I find that most of them are complicated and take days/weeks to customize. Most of them are overkill in features too. My network and devices are getting more and more complex daily, and I am looking for tools that simplify my life. Worth a look, and its free.

_[COLOR="Blue"][http://www.packettrap.com/download/index.html]("http://www.packettrap.com/download/index.html")[/COLOR]_

---

