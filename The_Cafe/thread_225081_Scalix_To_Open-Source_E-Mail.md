---
title: "Scalix To Open-Source E-Mail"
date: 2006-07-29
forum: The Cafe
---

### Post by RAV TUX on 2006-07-29
[http://www.informationweek.com/industries/showArticle.jhtml?articleID=191203861](http://www.informationweek.com/industries/showArticle.jhtml?articleID=191203861)

> **     Scalix To Open-Source E-Mail    **


 [IMG]http://cdn.cmpnet.com/infoweek/spacer.gif[/IMG]
                   ** The next Community Edition Open Source will consist of the mail server, a Web services API platform, an installer, an administration console, Scalix Web Access Mobile, and new search and indexing services, the company said. **

                  
        [IMG]http://cdn.cmpnet.com/infoweek/spacer.gif[/IMG]
                                                                         By                                                                                                                        [EMAIL="bdarrow@cmp.com"]_Barbara                                                                                  Darrow_[/EMAIL]                                                                                                                               
                                                                                                                                                                                                                                      [                 CRN                 ]("http://www.crn.com/;jsessionid=OFZCMVIYPMSF2QSNDLPSKHSCJUNN2JVN")                                                               
        [IMG]http://cdn.cmpnet.com/infoweek/spacer.gif[/IMG]
                Jul 26, 2006 06:35 AM
                                    
  Scalix will offer up a good chunk of its next e-mail release to the open source world, the company said Wednesday. 
  Components of [ Scalix Community Edition]("http://www.scalix.com/products/communityedition.html") will be available under a license modeled on the Mozilla Public License (MPL). That will enable the legal use of third-party code not licensed under the MPL to coexist with commercial code. A commercial license will also be available for the Scalix enterprise product. 
The next Community Edition Open Source will comprise the mail server, a Web Services API platform, installer, administration console, Scalix Web Access Mobile and new search and indexing services, the company said in a statement. 
 The entire stack will be based on a new release of Scalix to be announced at LinuxWorld in August. The various open source components will roll out through next year. The company's existing Community Edition is free but is not available under open source licensing. It has been positioned as an adjunct to the paid Enterprise Edition but for users who do not need that version's collaborative features. 
In a related announcement, Scalix said it had inked a new licensing pact with Hewlett-Packard that will enable it to open source the portions of the Scalix line that are based on HP's OpenMail. 
  Scalix and other smaller Linux mail vendors like [ Open-Xchange]("http://www.crn.com/showArticle.jhtml;jsessionid=GKYWQ3UJD4VLGQSNDLPSKHSCJUNN2JVN?articleID=180200732") and [Zimbra]("http://www.crn.com/showArticle.jhtml;jsessionid=QNQ0QDJSZMHYEQSNDLPSKH0CJUNN2JVN?articleID=184405228")  are fighting the open-source e-mail battle.  
 Meanwhile, IBM's Lotus, a perennial market leader, said it will offer [ a full Linux version of the Notes client]("http://www.crn.com/showArticle.jhtml;jsessionid=QNQ0QDJSZMHYEQSNDLPSKH0CJUNN2JVN?articleID=190301221") this summer.  
 IBM says that move should make Domino/Notes the only top-tier mail system available for Linux. IBM and Microsoft vie for top spots in e-mail market share but Microsoft Exchange Server is obviously a Windows-only product. 
 In other open-source news, [ObjectWeb]("http://www.crn.com/showArticle.jhtml;jsessionid=QNQ0QDJSZMHYEQSNDLPSKH0CJUNN2JVN?articleID=173400488") and eXo Platform SARL announced the availability of what they call the first open-source content management and repository that will let users create and manage documents from a single access-point Web portal. 
 ObjectWeb is a an open-source consortium; eXo is a privately-held company backing its open-source content management platform.


---

### Post by etank on 2006-09-13
I found this link to help get Scalix installed on an Ubuntu machine. [http://www.scalix.com/wiki/index.php?title=Makefile_for_Ubuntu_Breezy%2C_Hoary_and_Dapper](http://www.scalix.com/wiki/index.php?title=Makefile_for_Ubuntu_Breezy%2C_Hoary_and_Dapper) I am trying it out where I work because we do not have the money to upgrade our current system and it is badly out of date.

---

### Post by Mayk on 2006-10-24
Hi,

how is your progress on getting it on ubuntu ? I have installed the version 10 with success on ubuntu server 6.06. Version 11 preview installed kinda ok with some bumps, but beta1 was kinda a horror story , but it worked, till i rebooted the system.

So i'm wondering how your progress is in this field.

Please let me know

kind regards,

Mayk

---

### Post by rverrips on 2007-02-14
Scalix is an awesome Mail and Groupware server solution.  The "community edition" allowed of 25 premium users and unlimted mail users.  Mail protocols supported are POP3 and IMAP, but with the 25 premium users you can use a MAPI and plugin for either Evolution or Microsoft Outlook ... The premium users get "Microsoft Exchange"-like functionality in terms of sharing calendars, contacts, etc. and the licensing costs are fairly competitive if you need more than 25 users.

The bummer though it's an absolute nightmare to get it running on Ubuntu - I succeeded with Scalix 11 and Ubuntu 6.06 Edgy (and some "forward-ports" to Feisty) and got all the core services working (POP3/IMAP/LDAP/MAPI) 

[http://www.scalix.com/forums/viewtopic.php?t=5354&highlight=](http://www.scalix.com/forums/viewtopic.php?t=5354&highlight=)

However hit a brick wall trying to get the webclient to work, which is also needed to ease the administration of user, etc (although command line tools exist and worked ok) so at present still run it on a CentOS box instead, but hope to migrate that one back to Ubuntu once Scalix get's better 'deb support.

[http://www.scalix.com/forums/viewtopic.php?t=5758&highlight=](http://www.scalix.com/forums/viewtopic.php?t=5758&highlight=)

---

