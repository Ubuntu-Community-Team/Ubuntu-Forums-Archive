---
title: "Migrate from Windows server to Red Hat or SUSE based on price"
date: 2010-12-09
forum: The Cafe
---

### Post by e24ohm on 2010-12-09
Not starting a flame war, but can someone explain the cost benefits of migrating servers over to Red Hat or SUSE?

I noticed on Red Hat it costs $349.00 and SUSE costs $349.00 for self-support for 1 year.
[https://www.redhat.com/apps/store/server/](https://www.redhat.com/apps/store/server/)
[http://www.novell.com/products/server/howtobuy.html#getpricing](http://www.novell.com/products/server/howtobuy.html#getpricing)

However, if I replace servers every five years, doesn’t the price of the software average about the same as a copy of Windows Server? 5 years * 349.00 = $1745.00 which is roughly the price of a copy of Windows Server Standard.

What are the main benefits for migrating to a SUSE or Red Hat from Windows.

Thanks.

---

### Post by viralmeme on 2010-12-09
> **e24ohm said:**
> What are the main benefits for migrating to a SUSE or Red Hat from Windows

You maintain control of your own software and don't infected by malware. And imho, Linux boxes are easier to maintain, turns out to need less staff, so your company saves on salaries.

ps: In a business environment, if it works don't fix it. The only patches would be related to security, and of course on an Internet facing system, you would have a full auditing and intrusion detection system in place.

---

### Post by simpleblue on 2010-12-09
There's always CentOS. It's a clone of Redhat, and it's free. The next version will be here in a few weeks.

---

### Post by nlsthzn on 2010-12-09
> **e24ohm said:**
> Not starting a flame war, but can someone explain the cost benefits of migrating servers over to Red Hat or SUSE?

I noticed on Red Hat it costs $349.00 and SUSE costs $349.00 for self-support for 1 year.
[https://www.redhat.com/apps/store/server/](https://www.redhat.com/apps/store/server/)
[http://www.novell.com/products/server/howtobuy.html#getpricing](http://www.novell.com/products/server/howtobuy.html#getpricing)

However, if I replace servers every five years, doesn’t the price of the software average about the same as a copy of Windows Server? 5 years * 349.00 = $1745.00 which is roughly the price of a copy of Windows Server Standard.

What are the main benefits for migrating to a SUSE or Red Hat from Windows.

Thanks.

Hi,

I am talking under correction here but do you get support from MS for 5 years with your purchase?  For SUSE and Red Hat you are getting support from them for your product...


Regards
Neil

---

### Post by HermanAB on 2010-12-09
Howdy,

The benefits are:
Stability
Security
Extremely low maintenance

Windows is extremely fragile and requires constant maintenance, while a properly configured Linux machine can run with zero maintenance for several years.  I install my servers, lock them down and then leave them alone until the hardware fails.  I do not do any updates or restarts ever.  Don't try that with Windows.

Google, Amazon, Rackspace, Akamai and others run hundreds of thousands of servers.  They would go bankrupt in no time if they had to use Windows and there would not be enough computer scientists in the world to manage all their machines if they did, since Windows requires two orders of magnitude more support personnel.

---

### Post by snowpine on 2010-12-09
Red Hat and SUSE are actually FREE (this is what allows spin-offs like CentOS or Scientific Linux to exist). What you are paying for is support. The price varies depending on the support level, ranging from self-support to 24/7 on-call support. Obviously Red Hat is only "worth it" if this support is valuable to your business needs.

---

### Post by e24ohm on 2010-12-09
> **nlsthzn said:**
> Hi,

I am talking under correction here but do you get support from MS for 5 years with your purchase?  For SUSE and Red Hat you are getting support from them for your product...


Regards
Neil

I thought the support usually comes automatically with volume licensing; however, I could be wrong. I understand if you purchase the software from a vendor like: tiger direct or other discount IT stores, then no support from microsoft is offered, since the software was not purchased via a authorized vendor.

---

### Post by e24ohm on 2010-12-09
I guess I see what you folks are getting at. I am a network Engineer, and mainly deal with Router and switchs, so server and desktop items are new to me.

Cisco does the same with their routers, switch and this IOS, and their support contracts. You can purhchase a router, switch or ASA without support; however, the end user is not entitled to updates or security packages.

Is that the same model with Red Hat and SUSE? If the clicent or company does not purhcase a support contract, security updates, and general updates are not available?

---

### Post by nlsthzn on 2010-12-09
> **e24ohm said:**
> I guess I see what you folks are getting at. I am a network Engineer, and mainly deal with Router and switchs, so server and desktop items are new to me.

Cisco does the same with their routers, switch and this IOS, and their support contracts. You can purhchase a router, switch or ASA without support; however, the end user is not entitled to updates or security packages.

Is that the same model with Red Hat and SUSE? If the clicent or company does not purhcase a support contract, security updates, and general updates are not available?

AFAIK yes, no contract no support or updates etc.

---

### Post by dtfinch on 2010-12-09
It really depends on what you're using the Windows Server for, your level of Linux experience, and whether you've already paid for Windows Server or if you're planning for a new server.

We use Linux for our file and backup servers, and for most of our web hosting, and I use it for my home desktop. But we have Windows servers for Active Directory (we have Windows desktops), Exchange, and SQL Server (for our ERP system).

---

### Post by sydbat on 2010-12-09
> **nlsthzn said:**
> AFAIK yes, no contract no support or updates etc.This is correct. However, you can use CentOS and get regular updates. It is based on RHEL.

---

### Post by snowpine on 2010-12-09
> **e24ohm said:**
> Is that the same model with Red Hat and SUSE? If the clicent or company does not purhcase a support contract, security updates, and general updates are not available?

With a few minor exceptions (artwork and "branding" that is considered trademarked product identity) the source code must be freely available to the public in order to comply with the Gnu Public License (GPL). Therefore it is theoretically possible to keep a non-registered Red Hat system up-to-date by downloading the source code for each update and compiling it yourself. 

In practice however it is easier to use a spin-off distro like CentOS because they do the hard work for you of compiling the source code into easy-to-install binaries (.rpm). CentOS therefore is very popular with companies who feel they have the resources to support it "in-house."

An analogy is that you may freely modify Ubuntu and re-release it as your own distro, however you may not call your new product "Ubuntu" or use the Ubuntu logo without permission, because product identity is trademarked by Canonical and not released under the GPL. Furthermore, Canonical would have no obligation to support users of your Ubuntu-based spin-off (not that they really have any obligation to support non-paying Ubuntu users as it is released "without warranty").

This is my understanding of how it works, but I am not a lawyer. :)

---

### Post by Spice Weasel on 2010-12-09
> **snowpine said:**
> or use the Ubuntu logo without permission, because product identity is trademarked by Canonical and not released under the GPL.

Didn't Super OS/Super Ubuntu do this?

---

### Post by koenn on 2010-12-09
> **snowpine said:**
> ... the source code must be freely available to the public in order to comply with the Gnu Public License (GPL).

close, but no.
GPL only requires that you make source code available to those people that you distribute binaries to. In RedHat's case, that would be only its paying customers. RH have no obligation to make source code available to the general public -- but at the same time they would also be unable to prevent those customers from publishing the source code.

---

### Post by snowpine on 2010-12-09
> **koenn said:**
> close, but no.
GPL only requires that you make source code available to those people that you distribute binaries to. In RedHat's case, that would be only its paying customers. RH have no obligation to make source code available to the general public -- but at the same time they would also be unable to prevent those customers from publishing the source code.

Thanks for clarifying... so if I understand correctly, Red Hat goes "above and beyond" by making the source available to anyone (even though they are not strictly obligated to do so)?

I have also heard they are generous when it comes to sharing their code "upstream" and that a lot of kernel improvements come from Red Hat developers.

---

### Post by koenn on 2010-12-09
> **snowpine said:**
> Thanks for clarifying... so if I understand correctly, Red Hat goes "above and beyond" by making the source available to anyone (even though they are not strictly obligated to do so)?

yes.
I don't know if this is an idealistic decision or a purely pragmatic one, or a mix of both.
And yes, they're still one of the major kernel contributers in Lines Of Code.

---

### Post by kaldor on 2010-12-09
> **e24ohm said:**
> Not starting a flame war, but can someone explain the cost benefits of migrating servers over to Red Hat or SUSE?

I noticed on Red Hat it costs $349.00 and SUSE costs $349.00 for self-support for 1 year.
[https://www.redhat.com/apps/store/server/](https://www.redhat.com/apps/store/server/)
[http://www.novell.com/products/server/howtobuy.html#getpricing](http://www.novell.com/products/server/howtobuy.html#getpricing)

However, if I replace servers every five years, doesn’t the price of the software average about the same as a copy of Windows Server? 5 years * 349.00 = $1745.00 which is roughly the price of a copy of Windows Server Standard.

What are the main benefits for migrating to a SUSE or Red Hat from Windows.

Thanks.

If you want to migrate to Linux and cut cost, use Ubuntu. It's free and you can get paid vendor support if needed.

RHEL and SUSE assume you need it off the bat. CentOS and openSUSE have no vendor support.

---

### Post by Dr. C on 2010-12-09
> **kaldor said:**
> If you want to migrate to Linux and cut cost, use Ubuntu. It's free and you can get paid vendor support if needed.

RHEL and SUSE assume you need it off the bat. CentOS and openSUSE have no vendor support.

One of the advantages of Ubuntu is that one can choose the level of support starting at free community based, to different levels of paid support. 

One very important cost when considering Windows Server is the cost of the client access licenses or CALs. Basically a per user or per device fee for access to the Windows Server. These can add up really fast.

---

### Post by kaldor on 2010-12-09
> **Dr. C said:**
> One of the advantages of Ubuntu is that one can choose the level of support starting at free community based, to different levels of paid support.

Exactly. Only shell out for SUSE/RHEL if you know you'll need it.

---

### Post by e24ohm on 2010-12-10
> **Dr. C said:**
> One of the advantages of Ubuntu is that one can choose the level of support starting at free community based, to different levels of paid support. 

One very important cost when considering Windows Server is the cost of the client access licenses or CALs. Basically a per user or per device fee for access to the Windows Server. These can add up really fast.

Oh snap, I did forget about this cost associated with Windows. You are right - technically a company needs a cal license for each machine connecting to the domain controller. In addition, I believe there is a cost associated with each machien connecting to Exchange, and a cal license for each Terminal service account. I did notice at my place of employment, we can only have two users connecting to a server. 

(I always get annoyed, becuase I can never connect to one of our server, which I keep my TFTP sight on for Router backups. Remote desktop always session in ues, or something along those lines - come to find out it is programmers that do not log out of Remote desktop, and only click the X to close the session, keeping the connection live using up Terminal Service/Remote desktop licese when only 2 are available.)

Thanks for reminding me of the CAl license...forgot totally about those...yes those do add up.

cheers!!!

---

