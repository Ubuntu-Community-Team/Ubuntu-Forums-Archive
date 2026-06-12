---
title: "HEUR:Trojan.Script.Generic."
date: 2015-03-27
forum: Security
---

### Post by Caril Chasens on 2015-03-27
Is HEUR:Trojan.Script.Generic a potential threat to a computer running ubuntu 12.04? We need to do business with an outfit that may be infected... Kaspersky stopped my partner's windows computer flat.

---

### Post by slickymaster on 2015-03-27
*Moved to the ***Security*** sub-forum*

---

### Post by Habitual on 2015-03-27
If you intend to do business with them, isn't it in your best interest to bring it to *their* attention?

---

### Post by bashiergui on 2015-03-27
> **Caril Chasens said:**
> Is HEUR:Trojan.Script.Generic a potential threat to a computer running ubuntu 12.04? We need to do business with an outfit that may be infected... Kaspersky stopped my partner's windows computer flat.You're focused on only part of the threat. Would it infect your ubuntu machine-  probably not but will the attackers pivot into your environment from the business partner? It's a possibility.

Also assume any business you do with a company infected with malware will also be shared with the malware owners. 

Are you OK with those risks? If not ask the other company to clean up their system.

---

### Post by Caril Chasens on 2015-03-27
I have brought it to their damned attention.  The business in question is Xplornet, which provides our satellite internet service. Up here in the bush, in the canadian north, we don't have much choice of servers, and internet access is important to us because we have no phone. Xplornet is purporting to offer a free equipment upgrade and higher speed to us, their rural customers across the north, I think as part of a deal with the Canadian government. We we would at least like to check out and read the fine print of their offer, but my partner's Kaspersky stopped him cold, with a message that the offer link was infested with HEUR:Trojan.Script.Generic. Maybe they have cleaned up... they have, so far, been unclear. 
Thus, my question... is it safe to follow the link with an Ubuntu system.

---

### Post by Geoffrey_Arndt on 2015-03-27
It seems you could do a live chat with a rep and even have the offer e-faxed or emailed as an attachment to you versus a link (or even, have a look at their web "site map" to find another avenue to your data).    

Re clicking on the link - - use a "Live Linux CD" such as Porteus [http://www.porteus.org/](http://www.porteus.org/) or Xubuntu (but don't enable persistence).   The trojan seems to be written to modify the windows registry,  . . but, I would not try to access the link from a production system of any type - - thus the Live CD becomes very handy.

Bottom line, I have to believe the technical dept at Xplornet should be able to best answer your questions if you're persistent and professional . . . unless they're not interested in new business.

---

### Post by bashiergui on 2015-03-28
> We would at least like to check out and read the fine print of their offer, but my partner's Kaspersky stopped him cold, with a message that the offer link was infested with HEUR:Trojan.Script.Generic. Maybe they have cleaned up... they have, so far, been unclear.This bit makes it sound like you're clicking on a link in an unsolicited email. Is that the case?

---

### Post by Caril Chasens on 2015-03-28
bashiergui - my first thought was phishing fraud. We contacted them via their online support. They say the site is theirs and d'oh what malware, we don't see any malware...

Geoffrey_Arndt - The live linux cd sounds like a good idea, if we succeed in downloading such a thing, given the terrible speed we usually get, way less than the 1m/sec up-to speed we pay for.  We will continue to try to deal with them persistantly and professionally. At least, I would do a thorough back-up before going into the site with the password they gave us, and hope that since we are already customers being billed, we might not have to enter financial info.

---

### Post by bashiergui on 2015-03-29
Your partner is a customer of Kapersky which means he can submit the link for analysis to Kapersky. It could be a false positive. From what I see in searching, the category Trojan.script.generic is...well, generic or a catch-all for uncategorized stuff. That makes me suspicious that it's a false positive. But Kapersky should be able to tell you specifically what the exploit is and whether it would work on Ubuntu.

Submit the link to virustotal.com. That will scan the link with 50+ AV scanners. If Kapersky is the only one marking it as malicious then that increases the liklihood it's a false positive. If several AV engines say it's malicious then it probably is.

---

