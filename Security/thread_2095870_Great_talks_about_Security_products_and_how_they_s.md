---
title: "Great talks about Security products and how they suck"
date: 2012-12-18
forum: Security
---

### Post by samiux on 2012-12-18
Hi all,

The following talks are presented by Joe McCray. He will show you how to bypassing the very expensive (sometimes) security products which claimed themselves can protect your network/system from being attack.

He also urge all the bosses to put more budget on security guys and security training but not just purchase a (or some) security product(s) only.

[Here we are.](http://samiux.blogspot.com/2012/12/great-talks-about-security-products-and.html)

Samiux

---

### Post by Hungry Man on 2012-12-18
The vast majority of deployed security products have barely changed (in concept, not technology) since the 80's. Some of them have gotten worse as the demand for security has been increasing drastically with security programs unable to meet that demand.

Most high end network devices aimed at security still rely on signature detection of traffic. I believe the people behind Pwn2Own fund it because during the event they can monitor traffic to improve their own system, which they sell for quite a lot of money.

But companies still get hacked. Users still get hacked. Everyone's getting hacked.

So it's clearly a failing of the industry.

The focus on "You spent all that money and you still got owned?" is nice. Companies are willing to spend thousands on the latest firewall with NIDS/NIPS while they're deploying Sophos (crap)and XP, and they're unwilling to spend the money doing proper auditing and then actually responding the right way to those audits.

Penetration testers spend a lot of time writing very long and comprehensive documents for companies but I think quite a lot of the time management won't give it more than a glance.

He's a very good speaker. Thanks for the videos,

---

### Post by haqking on 2012-12-18
In my experience (which is long and getting old now ;-) companies conduct Penetration tests, Security Audits, use a given product etc based on compliance, and they will do generally the minimum required to meet that and that mimimum will be based on budget.

When that device/process integrated and implemented to meet with the compliance for the sake of the overall operation and continuity of the business "fails" it is easy to find IT at fault because no one else understands the technology involved anyways, infact IT rarely does either.  The vast majority of companies do not place security as a necessity, the budget comes way before that, security is an afterthought to please people specifically auditors and compliance.

Hell most pen-tests are not given free reign anyways, it is a very controlled test/hack/audit whatever you want to call it, you are very limited and legally bound to only do what has been heavily discussed prior to the "hack/test" so as not to disrupt the business, it rarely reflects a real malicious attack where there are no legal boundaries,, times constraints or attack restrictions.

Security products suck because people are stupid not the product itself, this idea we need a product is the most flawed one, the product is part of a process not a one stop band aid that wont fix a problem. It is people who suck not the products.

Peace

---

### Post by Grenage on 2012-12-18
Yup, it's a shame you can't just buy some magical product and it will protect your system.  The best firewalls and OS security in the world is rendered useless through poor management and understanding.

As most of us know, it's frightening how easy it is to compromise your average business network - truly frightening.

---

### Post by Hungry Man on 2012-12-18
>  companies conduct Penetration tests, Security Audits, use a given product etc based on compliance
This is exactly it.

> 
Security products suck because people are stupid not the product itself, this idea we need a prodcut is the most flawed one, the product is part of a process not a one stop band aid that wont fix a problem. It is people who suck not the products.
I disagree here though. It's both. Products suck and they're deployed terribly.

---

### Post by CharlesA on 2012-12-18
I can only speak from my (limited) experience, but at least at the company I am working for now - no one checks the firewall logs. They *might* check the VPN logs, but only if someone reports a problem and I am pretty sure they aren't running any form of IDS.

I really doubt they have ever had a pen test done to see where their weaknesses lie.

What good is a firewall if you don't monitor it?

---

### Post by Soul-Sing on 2012-12-18
I don't know the facts exactly, but when reading about cracked/hacked systems its all about forgotten-to-update software talk, and the use of intrinsic poor software as Java. Or its the one employee story, who has lost his/her root access usb stick, who no encryption.(Of course)
Security and big organizations with lots of people, is the weak part in the chain story. Mostly a 'lazy' employee, indeed the human factor.

---

### Post by Ms. Daisy on 2012-12-18
> **haqking said:**
> Security products suck because people are stupid not the product itself, this idea we need a product is the most flawed one, the product is part of a process not a one stop band aid that wont fix a problem. It is people who suck not the products.

PeaceSorry Hungry Man, I have to agree with haqking on this. There is a mentality among the non-technical crowd that you can toss products at a problem and walk away. Anyone that has actually used the tools knows it takes knowledge and thought to implement a tool properly. Some of the tools out there do suck but it takes knowledge to test and choose the right one, all coming down to people.

---

### Post by CharlesA on 2012-12-18
> **Ms. Daisy said:**
> Sorry Hungry Man, I have to agree with haqking on this. There is a mentality among the non-technical crowd that you can toss products at a problem and walk away. Anyone that has actually used the tools knows it takes knowledge and thought to implement a tool properly. Some of the tools out there do suck but it takes knowledge to test and choose the right one, all coming down to people.

Indeed. The sad thing is there is sometimes the same mentality among the IT guys too. :|

A tool only works if you know how to use it.

---

### Post by haqking on 2012-12-18
> **CharlesA said:**
> Indeed. The sad thing is there is sometimes the same mentality among the IT guys too. :|

A tool only works if you know how to use it.

A great sculptor can create a masterpiece with a spoon and a lump of granite, give a non-sculptor or a poor one  every tool under the sun and an unlimited amount of clay they will only end up with sore fingers, even if they took a class ;-)

And there are server rooms everywhere with lumps of clay on the floor....LOL

---

### Post by CharlesA on 2012-12-18
> **haqking said:**
> A great sculptor can create a masterpiece with a spoon and a lump of granite, give a non-sculptor or a poor one  every tool under the sun and an unlimited amount of clay they will only end up with sore fingers, even if they took a class ;-)

And there are server rooms everywhere with lumps of clay on the floor....LOL

So bloody true! :lolflag:

---

### Post by chadk5utc on 2012-12-18
Agreed this is sad but true

---

### Post by samiux on 2012-12-18
In my own opinion, why security products are suck is that the developers of the security products are not fully understand the commands/strings that attackers used.  They just copied some of the commands/strings as the pattern of the signatures for their security products.  

If the attackers changed something on the commands/strings (but it still works as the theory is the same), the such security products cannot detect the attack.

Most likely, those security products are signature based and the developers cannot include all the variants of the pattern.  Or, they do not know that there are some variants on the pattern.  :(

Meanwhile, the users of the security products do not fully understand how the products work.  They do not know how to configure it or they do not have a proper training on them.

Therefore, developers of the security products, security products and users are suck.

Samiux

---

