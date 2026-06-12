---
title: "Small Groupware Server with Contacts, Notes and (subscribed) Dates+Tasks in Calendar?"
date: 2015-01-26
forum: Server Platforms
---

### Post by stefan_03 on 2015-01-26
Hey folks,

I am thinking about renting a small Ubuntu server for managing my data. I would like to set up a small groupware where I can synchronize my mails and additionally my contacts, notes / memos and dates. The major problem is the issue with managing the dates. I want to subscribe external calendars (e.g. university, Google calendar, etc) into my groupware's calendar, so that I do not have to add multiple calendars to Evolution. Another issue: I want to save my tasks, and if there is a due date for the task, I want it to see in my calendar too - it would be great if they will be marked as a "due date" instead of a general date.

I tried Citadel. At first I was shocked by the ugly web interface, but as I need a Mail client (Evolution or Thunderbird) I don't really care. What I like about Citadel is that I can manage tasks, dates and notes but I can neither show tasks' due dates in my main calendar, nor add external calendars.

I also tried Kolab, which is way too much for this small projects (3 people, max. 5!). Server has 1GB memory and small web applications on Apache are running, so it's not really usable. 

Any ideas about slim groupware software for Ubuntu server which cover the usual functions and solve my specific calendar problem?


Thanks!

---

### Post by TheFu on 2015-01-27
We all want what you want. Sadly, I've never found a lite version that does this.
Have you considered the Seafile or owncloud options? I've never run either, just use a VPN with them over the internet. 
Don't trust just SSL certs and HTTPS.

Also, if you have broadband at home, you don't need to rent a VPS either.

We use Zimbra for this stuff - it isn't lite and won't load in under 1.5G of RAM.

---

### Post by stefan_03 on 2015-01-28
Hello, thanks for your reply. Glad to know that I am not the only one with needs like these.

I would rent a VPS because I have no static IP and I don't want to maintain the server's hardware.

Tell me more about Zimbra. I know that there is no lite version. But there is an open source version of Zimbra. I could arrange another gig of memory, but can I do everything I wanted? See the due dates of tasks in my calendar, as well as external subscribed CalDAVs? And does it work with Thunderbird or Evolution clients? One advantage of Zimbra is the web interface. It's kind of pretty and seems usable.

Thanks!

---

### Post by TheFu on 2015-01-28
I don't know of any calendar that shows task due dates. If you want that, create a calendar entry instead/also.
Yes to everything else.

I've been running Zimbra since 2008-ish. Can't think of any time that hardware failed in that time. I run it inside a virtual machine and have moved/upgraded Zimbra a few times to another release and a different VM host. By far, the zimbra upgrades have been harder than moving to a new VM host (which is trivial).

I avoid webmail and only use the zimbra web interface to manage contacts and server-side email processing.  However, I prefer zimbra's interface over gmail.

The only negatives I have for Zimbra are:
* VMware owns it - I dislike that company very much based on prior experience.
* Installer is really picky about stupid things. /etc/hosts should have no more than 2 lines. Installer gets confused otherwise.
* Zimbra packages up about 10-20 F/LOSS tools, exact versions, and adds a bloated Java webapp on the back. All the pieces are tied closely, so running out-of-date versions seems mandatory. 
* really, really need to have a front-end MTA server which remains completely patched to protect Zimbra from bad people. Also need a reverse web-proxy to block DoS through forced password reset techniques. But this isn't just zimbra - and communications server needs that protection.

You don't need a static IP. Dynamic DNS works.  And the MTA front-end can be a 384MB box with 4G of RAM, so a relatively tiny VPS is needed.  I currently have multiple static IPs, but that will be changing in the next month or so. I plan to get a tiny VPS for the MTA front-end and retain Zimbra here, behind a dynamic IP.

---

