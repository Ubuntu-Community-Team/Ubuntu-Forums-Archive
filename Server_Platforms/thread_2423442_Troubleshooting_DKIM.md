---
title: "Troubleshooting DKIM"
date: 2019-07-23
forum: Server Platforms
---

### Post by Robert_Boutin on 2019-07-23
This is driving me absolutely nuts, hopefully somebody has a good suggestion for me (besides a valium)...

Ubuntu Server 18.04 LTS is email server w/ispconfig 3.1.14.  I have 4 email domains set up in ispconfig and enabled DKIM for each.  

When I test all four using [EMAIL="ping@tools.mxtoolbox.com"]ping@tools.mxtoolbox.com[/EMAIL], for three of the domains I get:

DMARC Compliant = yes
SPF Alignment = yes
SPF Authenticated = yes
DKIM Alignment = yes
DKIM Authenticated = no

For the 4th domain, I get DKIM Authenticated = yes.

I've spent hours trying to identify what I did differently for the 4th, both in ipconfig as well as in my dns records but no matter what I do, I can't get any of the other three to show DKIM Authenticated = yes.

What I haven't been able to find is what does "DKIM Authenticated" mean EXACTLY.  Mxtoolbox isn't showing me what's mismatched, missing, whatever, to try to figure where to look next.  Searching "DKIM Authenticated" online brings up a very broad list of results that hasn't been able to help me.  Does anyone have a thought about how to tackle this?  Thanks

***EDIT  I do see a difference in the headers.  In the one where DKIM passed authentication, DKIM-Signature shows c=relaxed/simple.  In the email headers that failed authentication, c=relaxed/relaxed.  I don't know why they would be different...

---

### Post by bistromasa on 2019-07-23
i will follow this topic

---

