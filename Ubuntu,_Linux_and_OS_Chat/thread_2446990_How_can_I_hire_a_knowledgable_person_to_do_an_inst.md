---
title: "How can I hire a knowledgable person to do an install?"
date: 2020-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by pengyou2 on 2020-07-10
I am changing webhost providers and I need to hire someone post haste to install Ubuntu on my new hosting company (if it is not on there already) and a mail server (likely Horde, but doing some evaluation now).  I will ultimately be installing WordPress on it, a wiki, Canvas learning management system, a photo album and a few others.  Is the a site where I can post an ad and likely get responses from qualified people?

---

### Post by wildmanne39 on 2020-07-10
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

No, this site is for free end user support for individuals, you can contact Canonical at:

[https://ubuntu.com/support/contact-us](https://ubuntu.com/support/contact-us)

We can help with recommendations.

Thanks

---

### Post by TheFu on 2020-07-10
Sologig or Fiverr or Freelancer but you are on your own for deciding whether anyone is qualified.
Perhaps you really mean a VPS install?  
i definitely wouldn't do an install as you seem to want for security and future maintenance reasons.  Getting all those things working on a single OS won't be easy and the first upgrade will probably break some dependencies.  if possible, go with a separate container for each to segment those dependencies. Doing it upfront should make ongoing maintenance 100x easier.

Plus there's a bunch of stuff needed not in the list. Stuff for security, alarming, monitoring, and versioned backups.

I&#8217;m not qualified since i use different systems for each of those things than the list for a number of reasons - some good and some bad. ;)  We all get where we are travelling different paths.

Good luck.

---

### Post by pengyou2 on 2020-07-10
Thank you!  That is helpful information.

---

### Post by TheFu on 2020-07-10
i forgot to mention to be certain to get weekly patching in the proposals and patching as-needed for all WP-related aspects.

Securing WP is an ongoing battle as soon as we use any addons.  i specifically avoid php webapps like WP because i don't have the needed expertise to maintain them or secure them.   Right now over 2 Million WP sites are hacked and being used for illegal uses.  Those combined with email servers just make spamming so much easier to go with the phishing that webapps often allow.

A friend maintains a corporate WP site with about 10 addons and he sometimes has to patch multiple times a week.

Because of the security and network architecture, i only patch weekly the last 12 yrs with just 3 times where some mitigation was needed mid-week for high-risk systems.

Setting up these systems isn't a 1-time thing unless you don't mind the systems being taken over by bad people for their illegal uses -  spam, phishing, C&C servers for other systems doing bad things.

---

### Post by pengyou2 on 2020-07-10
Is there a thread that will list all of the things that need to be done - once the OS is installed?  or tell me which terms I should use to search on?

---

### Post by pengyou2 on 2020-07-10
> **TheFu said:**
> i forgot to mention to be certain to get weekly patching in the proposals and patching as-needed for all WP-related aspects.

Securing WP is an ongoing battle as soon as we use any addons.  i specifically avoid php webapps like WP because i don't have the needed expertise to maintain them or secure them.   Right now over 2 Million WP sites are hacked and being used for illegal uses.  Those combined with email servers just make spamming so much easier to go with the phishing that webapps often allow.

A friend maintains a corporate WP site with about 10 addons and he sometimes has to patch multiple times a week.

Because of the security and network architecture, i only patch weekly the last 12 yrs with just 3 times where some mitigation was needed mid-week for high-risk systems.

Setting up these systems isn't a 1-time thing unless you don't mind the systems being taken over by bad people for their illegal uses -  spam, phishing, C&C servers for other systems doing bad things.
Thank you!  PHP is pretty pervasive in the scripts that I want.  This is going to be a bigger job than I thought!  Though in searching this question, I have found some really simple threads that show me how to set up the apps that I need on my hosted space.  It seems that the knowledge I will have to gain is how to manage it to keep it safe!

---

### Post by mastablasta on 2020-07-11
on a good host you will have option to install applications by clicking their icons in dashboard. then all you need to configure it. good host will also do backups and security (along with security warnings, server load balancing etc.). i use Hostko and so far they proved themselves (i had a breach in wordpress and they detected it, secured the server immediatelly and provided backups so i could restore it). since then, i also use additional security solutions in wordpress and also create my own automatic backups (just in case).

---

### Post by TheFu on 2020-07-11
> **pengyou2 said:**
> Is there a thread that will list all of the things that need to be done - once the OS is installed?  or tell me which terms I should use to search on?

Not that I know.  Just my guess is that to accomplish what you seek in a custom, secured, way is about 3 years of full-time Linux administration + webapp deployment knowledge in the specific stuff you care about.  No, there isn't a list. It comes from experience and making mistakes.

---

### Post by zebra2 on 2020-07-11
If it were myself I would go to 123ehost.com, submit a support ticket with your intentions and needs listed and see what they have.  I have been using them since the mid ninety's and they have extensive support. Much more than I ever needed. Price point is unbeatable. They also sell hosting through resellers so a person could be using their services and not even know it.

---

### Post by pengyou2 on 2020-07-12
Thank you for all of your suggestions and advice.  I have used Bluehost for hosting for a number of years and was really spoiled.They take care of the "background stuff" for me and offer a lot of 1 click installs for everything else.  In the past, my apps were mostly for people living in the US, so that was no problem.  I live in China and teach, so want to start using webtools to help my students in China. My BH apps are almost useless from within China, so I have turned to Aliyun as a provider.  Their servers are inside China, so thinking that speed is not going to be a problem.    I will keep doing my homework!  It seems that if I continue to pursue this option, I will have to spend at least 2 or 3 hours every week just doing maintenance alone.  That is OK with me, if I can find a roadmap to help me see what needs to be done.

---

### Post by mastablasta on 2020-07-12
find a host with same services as Bluehost. i am sure they have it in China as well.

---

