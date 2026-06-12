---
title: "Ubuntu for Business need a CRM (Customer Resource Manager) and other stuff?"
date: 2024-06-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Omnios on 2024-06-15
Greetings I just started a work from home job which requires me to manage a lot of contact information mainly for leads. I currently have LibreOffice for Excel files but am looking into getting a CRM (Customer Resource Manager) to manage my contact with companies. Currently looking at the following programs on Sourceforge 
 Dolibarr ERP - CRM 
Vtiger CRM 
Group Office groupware and CRM 
Krayin CRM 

 Any information on which ones work well would be appreciated.

---

### Post by Omnios on 2024-06-16
Found a very basic CRM at Google Sheets and Customer Relationship Management Google sheets template by: Copper. Still looking for something to have customer information in and allow for notes about leads.

---

### Post by krishnan t s on 2024-06-24
I don't know if its what you're looking for, but give ERPNext([https://erpnext.com/](https://erpnext.com/)) a try.
Unfortunately its a pain to set up on a local server but it could be worth it.

---

### Post by oldfred on 2024-06-24
While not for Customer data, data is data.
You can probably modify fields to be what you want.

Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[https://gitlab.com/GCstar/GCstar](https://gitlab.com/GCstar/GCstar)

Or if familiar with databases any database will work.
I use sqlite, python and a bit of sql for my data that is too large for spreadsheet.
Then totally customizable.

---

### Post by 0f4d0335 on 2024-06-27
Some security recommendations that are related to Ubuntu.

Using a server hosted in the Internet risk domain requires you to do extensive setup and maintenance. Therefore, if you want a server others can work in, you should use a SaaS product unless you're prepared to protect your server in the Internet. Reasons why you shouldn't manage your own server:

[LIST]
[*]Specific compliance and laws require PII (customer data) should be protected from tampering and remote attacks. 
[*]Significant fines may be the consequence of mishandling PII. 
[*]Ubuntu alone is not secure. It must be hardened using the CIS, PCI DSS, and GDPR frameworks. [https://ubuntu.com/security/cis](https://ubuntu.com/security/cis) 
[*]Ubuntu Pro should help you achieve the third point easier than using Debian or Ubuntu default. 
[/LIST]

Therefore I recommend using a SaaS you trust. You should conduct a review with the CISA star catalog. [https://cloudsecurityalliance.org/star/registry](https://cloudsecurityalliance.org/star/registry)

Good luck!

---

### Post by rg4w on 2024-06-28
Have you looked at SuiteCRM?
[https://suitecrm.com/](https://suitecrm.com/)

---

### Post by him610 on 2024-07-01
Hello,
You may want to check out vTiger CRM: [https://www.tecmint.com/install-vtiger-crm-on-ubuntu/]("https://www.tecmint.com/install-vtiger-crm-on-ubuntu/")

Good luck.

---

### Post by TheFu on 2024-07-01
I ran vTiger for a few small companies.  The power was in hooking up the CRM servers to their email server so that data from campaigns and "touches" could be captured.  That was the goal.  The marketing people never figured out how to use CRM and ended up using our email/communications server with tagging to setup virtual folders for all potential clients that got beyond the first contact.

I helped them setup firefox and thunderbird addons, but there was a Zimbra addon for the webmail users. We used Zimbra as our email/communications server.  I still do for my company and I'm fully addicted to Zimbra capabilities - especially server-side filters and filing using both keywords and tags.  It is great to add a tag to messages, then be able to create a virtual folder with all messages that have that tag.  And those virtual folders can support delegation across an entire team.  Fantastic tool (Zimbra).  I haven't moved to a newer release in a few years, which I definitely need to do.

2 of those small businesses never expanded beyond their current consulting clients, so the CRM really didn't help get any new contracts/customers. I suppose it was because nobody knew how to take full advantage.  We actually had more problems getting company leadership to use mediawiki to share status and plans.  We also had a DMS - Document Management System - and only a few people trusted it to maintain versions of documents automatically. The marketing and project manager teams insisted on adding dates to new filenames for their versioning.   All the different saved versions were available with just a right-click.

Human factors matter more than anything else with software.  Try as we might to show people a better way to work, sometimes it is impossible to get them to change to be more efficient.  Rather than become frustrated over all the integrated infrastructure I'd setup that they didn't use, I just let the systems die and nobody complained.  The DMS became a simple storage server. Zimbra became the tool everyone used. vTiger died. WikiMedia died.  Redmine did work as our PM tool, but the project managers only used it for the minimal stuff. They kept using their spreadsheets for issue tracking and MS-Project for Gant Charts/dependency tracking.

There are some personal relationship systems these days.  Most seem to be cloud hosted, but a few can be run on local servers and are 100% F/LOSS.  I looked at self-hosting "Monica" a few years ago. [https://medium.com/scheduled/top-10-personal-crm-apps-for-2024-a-comprehensive-guide-92082711e4e6](https://medium.com/scheduled/top-10-personal-crm-apps-for-2024-a-comprehensive-guide-92082711e4e6) and decided that I could keep notes in my Zimbra LDAP addressbook just as easy while having lots of search capabilities and calendar reminders that would integrate with my phone using DAVx5 [https://www.davx5.com/](https://www.davx5.com/).  My phone syncs the addressbook and calendar with Zimbra daily.

---

