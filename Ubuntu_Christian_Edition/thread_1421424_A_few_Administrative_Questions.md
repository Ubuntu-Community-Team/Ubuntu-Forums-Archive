---
title: "A few Administrative Questions"
date: 2010-03-04
forum: Ubuntu Christian Edition
---

### Post by nefarmboy on 2010-03-04
Ok. I'm sold on Ubuntu CE.  
Now, how does one keep someone from accessing the DG/Proxy controls so they can't disable/circumvent it?  

Can the application be password protected? 

Use a different username/non-admin password at logon? 

Do I need to remove previously loaded firewall applications prior to converting to UCE? 

Are the blacklists updated automatically?  Can a script still be written/found to make it automatic? 

How do you whitelist a site? For instance, my wife tried to get to her Facebook account and our current windows app wouldn't let her.  It wouldn't let me get to biggovernment.com either.

Are the updates to UCE automatic like other distros of Ubuntu?

Is it easy enough to get up, running, and be administrated by a caveman?

Sorry for some pretty lame questions, but the help would be greatly appreciated.

---

### Post by stlsaint on 2010-03-04
UCE is still ubuntu based but with added applications. You can still control and run it as if you are running a regular install of ubuntu. As for DG i think if you just open the DG control interface than you will see all options in that window. With the firewall question i would suggest maybe tweaking dg to block the sites while your firewall just hanldes direct ip attempts.

---

### Post by david_kt on 2010-03-04
> **nefarmboy said:**
> Ok. I'm sold on Ubuntu CE.  
Now, how does one keep someone from accessing the DG/Proxy controls so they can't disable/circumvent it?  

Can the application be password protected? 

Use a different username/non-admin password at logon? 

Do I need to remove previously loaded firewall applications prior to converting to UCE? 

Are the blacklists updated automatically?  Can a script still be written/found to make it automatic? 

How do you whitelist a site? For instance, my wife tried to get to her Facebook account and our current windows app wouldn't let her.  It wouldn't let me get to biggovernment.com either.

Are the updates to UCE automatic like other distros of Ubuntu?

Is it easy enough to get up, running, and be administrated by a caveman?

Sorry for some pretty lame questions, but the help would be greatly appreciated.

1. Yes, you should create new user without administrative right. User without administartive right will not able to modify dansguardian. Remember to lock firefox proxy as well when enabling dansguardian
2. Previous firewall should be removed as it would interfere with ubuntu ce firewall, which come with dansguardian gui.
3. Blacklist is not updated automatically. Anyhow, dansguardian is "true content filtering" means even new website could be block due to its content, not the web address.
4. For white list and other setting, launch dansguardian-gui, it is specially made for ubuntu ce for easy administration of dansguardian. Even new user to linux would find it easy to administer dansguardian using dansguardian gui, I hope.
5. Ubuntu CE is similar to any other ubuntu, there are automatic updates

DK

---

### Post by nefarmboy on 2010-03-05
Thanks All.  I'll get started on it as soon as I get time.

---

