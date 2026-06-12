---
title: "Unifying domain name with Linux Mail Clusters"
date: 2009-10-21
forum: Server Platforms
---

### Post by rahmath on 2009-10-21
We have around 11 site offices + 1 head office, in which few  are located in same country and others are located in different countries. Currently for each site we have seperate domain names like;
main/head office --> headoffice.com  
site1 --> site1.com
site2 --> site2.com
..
..
site11 --> site11.com

For each offices the internal/external domain name are same as i mentioned above. For each offices they have seperate mail server with their domain names. So when a user transfer from head office to site7, then his id will change from [email]user1@headoffice.com[/email] to [email]user1@site7.com[/email] 

Now our management decided to unify this domain names in to ONLY one which is really new. That is going to be ouroffice.com. I thought about different ways to achieve this and finally end up on a concept like the following;

Set the ouroffice.com domain name in our head office and set the MX records of ouroffice.com to point to the public IP of our head office so that all the mails to ouroffice.com (which means even to all 11 sites bcoz now we will not have any other domain names) will come to our head office mail server (which we are thinking of a Linux Mail Cluster - Postfix - which should act as a front end to the MS exchange currently running in the head office) and then based on specific rule (i dont know whether this will be possible with Postfix, that is one of my doubt) this Postfix server should route the mails accordingly (for all 11 sites as well as to head office). In all the sites, their mail server should accept this mails which is been routed by the Main mail server in Head office and delivered to each users... 


site10 and site11 are having Linux(Postfix Mailservers) all other sites including HO is having MS Exchange 2007/2003. 
HQ is having around 250 mail users, 5 sites is having around 250 users, 4 sites around 150 users and for the last two sites around 75 which totals to 2250 mail users...

Can anybody assist me with a hint to start working out for this project...

We would like to use Linux Mail Cluster @ our Head office to handle this task... but still more ideas are required to frame a plan...

Goals to achieve:
1. Single domain name for all the mail id's in our office (11 sites + HO users)
2. When a user from HQ is transferred to any site, his mail should be delivered to his site office with minimal administrative over head
3. Many of our users travels from HQ to sites for few days frequently... so they need to access their mails (where ever it is) without any problem
4. We need to use Linux Mail Cluster in head office as a front end to exchange as well as to handle this particular case
5. All the work should be done with minimal downtime/risk/cost


Any help is really appreciated...

---

### Post by Lars Noodén on 2009-10-21
You might look into Kolab or Citadel for the head office.  Save some work that way.

---

