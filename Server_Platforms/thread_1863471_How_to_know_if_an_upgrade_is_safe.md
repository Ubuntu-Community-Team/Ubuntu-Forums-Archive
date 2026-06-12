---
title: "How to know if an upgrade is safe?"
date: 2011-10-17
forum: Server Platforms
---

### Post by Jarozas on 2011-10-17
Hello,
 
my recent server upgrade to 11.10 was a nightmare.
 
Suddenly postfix stop to send messages and only with the great job of Otlayi, my server returns to work just few minutes ago (you can see the related thread).
 
My question is:
 
There is a way to know when a upgrade is safe for our production servers?
Theres a way to try the upgrade and revert changes in case of problems?
 
 
Thanks for your attention.

---

### Post by HermanAB on 2011-10-18
Howdy,

Do what everyone else in your position does: Make a virtual machine copy of your production server and test on that.  

Don't apply updates to a production machine without testing them first and don't apply changes when accounting is processing the payroll...

---

### Post by Jarozas on 2011-10-18
Thanks Herman,

Now I'm looking for the way to make this virtual machine copy of a running server.

---

### Post by 2F4U on 2011-10-18
I don't want to sound offensive, but why are you running 11.10 on a server? My server runs 10.04 LTS and I don't worry too much about upgrades. I would never recommend anything else than a LTS release for a server.

---

### Post by Jarozas on 2011-10-18
Hi 2F4U,
 
You don't offend.
 
I run upgrades and last releases thinking this is better for security, surely I'm wrong.
 
Don't know much about LTS concept. But I think someday you should do an upgrade too, and then the original question may arrise again, will be safe that upgrade?

---

### Post by bab1 on 2011-10-19
> **Jarozas said:**
> Hi 2F4U,
 
You don't offend.
 
I run upgrades and last releases thinking this is better for security, surely I'm wrong.
 
Don't know much about LTS concept. But I think someday you should do an upgrade too, and then the original question may arrise again, will be safe that upgrade?

Upgrading for security is a myth.  Not going to happen.  Rolling releases allow new software to be added. 

LTS is Long Term Support.  Ubuntu OS that are LTS (i.e. 80.4, 10.04 and upcoming 12.04) have the following: Desktop -- 3 yrs of updates.  The Server has 5 years of updates.

When updating you should read the [**_[COLOR="Blue"]release notes[/COLOR]_**]("https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes"). If you really insight as to what is happening with Ubuntu read the last 5 or 6 release notes (0.04 through 11.04).  You will see what the developers had in mind.  interesting reading.  You can find all the currently supported release listed at the bottom of [**[COLOR="Blue"]this page[/COLOR].**]("https://wiki.ubuntu.com/")

---

