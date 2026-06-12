---
title: "Outlook Shared Calendar - How to Avoid  Exchange?"
date: 2008-03-24
forum: Server Platforms
---

### Post by ryth on 2008-03-24
Sort of a newb question here but I thought I'd throw it out there anyway.

I just started as admin for a small charity that has unfortunately taken the microsoft desktop plunge before my tenure.

We have ~20 seats, and the president wants to use Outlook and have access to the shared calendar. 

Since we are a charitable organization with limited funds I'd love to avoid M$ Server/Exchange on the back-end, even if I have to deal with Outlook user-side.  

What are my options?  I noticed there is a paid plugin for **[Citadel]("http://citadel.org")**, are there any other suggestions?

---

### Post by gfowler on 2008-03-24
> **ryth said:**
> Sort of a newb question here but I thought I'd throw it out there anyway.

I just started as admin for a small charity that has unfortunately taken the microsoft desktop plunge before my tenure.

We have ~20 seats, and the president wants to use Outlook and have access to the shared calendar. 

Since we are a charitable organization with limited funds I'd love to avoid M$ Server/Exchange on the back-end, even if I have to deal with Outlook user-side.  

What are my options?  I noticed there is a paid plugin for **[Citadel]("http://citadel.org")**, are there any other suggestions?

Scalix has a free Outlook plugin for their Exchange replacement software.  I've had it running with 5 users.  It was a bit slow on access, they have a cache option for each user but it will/did hose the alarm for appointments. 

Jerry

---

### Post by artcancro on 2008-04-25
> **gfowler said:**
> Scalix has a free Outlook plugin for their Exchange replacement software.  I've had it running with 5 users.  It was a bit slow on access, they have a cache option for each user but it will/did hose the alarm for appointments.

Scalix plugin may be free, but that doesn't save money if you have to pay for Scalix (which you do, if you want the full feature set).

Citadel does not play silly games with server licensing, everything is one hundred percent GPL.  Since its Outlook connector is built and sold by a third party, it requires a paid license (they do offer a free trial).  At the very least, this will allow you to only shell out the $$$ for those users who insist on continuing to use Outlook.

New version of Citadel came out this week, by the way.  Check it out.

---

