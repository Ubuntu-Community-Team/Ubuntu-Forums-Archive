---
title: "Collaborative Email management"
date: 2009-12-28
forum: Server Platforms
---

### Post by pibipibi on 2009-12-28
Hi,
I'm looking for a solution to manage the e-mail of a voluntary association with ubuntu.
We just have one mail box where we receive the requests of the people who contact us. We would like to realize a web service where a superuser could read all the emails and sort them to the volunteers (while they are working on their computers) without using other email boxes. 
The volunteers then should be able to send the answers through the same box. 
Obviously we would like to have periodical backups and search possibilities. 
I hope that you can help me, thank you in advance.
Best Regards

---

### Post by Lars Noodén on 2009-12-29
The technologically simplest method would be to use a mailing list as the recipient.  But what you save in set up you will lose every week through extra effort.  Getting your volunteers to return address and reply-to address must be set to that of the mailing list for that to begin to work.  [mailman](http://packages.ubuntu.com/karmic/mailman) would be the first mailing list package to consider. 

However, it might be *very* well worth your time to set up a proper ticketing system.  That will help archive the conversation with the customers and help bring up the whole history.  OTRS, RT and IRM are three to look at:

[http://otrs.org/](http://otrs.org/)
[http://bestpractical.com/rt/](http://bestpractical.com/rt/)
[http://sourceforge.net/projects/irm/](http://sourceforge.net/projects/irm/)

These will allow web management of the tasks, but also allow the customers to send e-mail questions or receive e-mail answers.  

If you are dealing with software, then Bugzilla is one to consider also.  

They are all flexible.  For example, I've set up RT twice at different sites to be used as a library reference service.  It might be wise to try one to get the feel of it along with some volunteers.  Then figure out a workflow and then re-install everything.

---

### Post by ElaineZhang on 2012-05-03
A free help desk software we used, which has the features in Back-end, front-end and email synchronization and Ticket assignment logic Customer self-service system: Have the helpdesk system which is to be the last insurance to help your customers to combat the problems. However, no one wants to wait for your reply if there is any chance to get the answer. So at higher priority, the customers should search their answers from the knowledgebase and articles you have prepared already. This must be designed intelligently and functionally.
More info you can check: [http://www.phphelpdesk.org/](http://www.phphelpdesk.org/) .

---

