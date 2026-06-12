---
title: "Spammers using my server HELP!"
date: 2011-06-23
forum: Security
---

### Post by seemeinhi on 2011-06-23
Hi, spammers have been using my server for 3 days to send 1,000's of junk mail, (endless list?). Yesterday I shut down postfix, but they keep going to the queue, 1,500 in 2 hrs., which makes me think that they ARE ON MY server. I can install and make everything work... But have no clue where/how to start looking for aholes like this. I have had this server for over 6 yrs and never had a problem... Customers (2) are not happy with 15000 failure notices. Before I had it set so that "only" true users could use smtp. Now there are all kind of different names in front of the domain name. any help would be appreciated.

---

### Post by falko on 2011-06-24
First, you should check if your server is an open relay: [http://www.spamhelp.org/shopenrelay/](http://www.spamhelp.org/shopenrelay/)

If it is, you should set up SMTP-AUTH as soon as possible. If it is not, you should check if spammers abuse one of your web applications, e.g. through a vulnerable contact form, to send spam.

Also, you should check if your server is already blacklisted: [http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx)

---

### Post by SeijiSensei on 2011-06-25
The first thing I would do is limit the acceptable To addresses to only those you support and to block all other destinations.  I use sendmail, so I know how to do this there, but I'm pretty sure postfix offers an equivalent option.  It sounds as though there are not any controls over what From and To addresses are legitimate.

---

