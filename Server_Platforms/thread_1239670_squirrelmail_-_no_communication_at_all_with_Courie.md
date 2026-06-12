---
title: "squirrelmail - no communication at all with Courier-IMAP"
date: 2009-08-13
forum: Server Platforms
---

### Post by localfiend on 2009-08-13
I've run into a problem that I can't even find mentioned on google.

I've been following the Flurdy mail server how to: [http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html)

I'm currently using:
Ubuntu 9.04, postfix, mysql, courier-imap, squirrelmail

My mail server so far is working great. I have a virtual user/domain database in mysql - postfix & courier both work.  I can connect to my server via thunderbird & outlook, send and recieve both internal and external e-mails.

I have installed squirrelmail, followed flurdy's guide and set it up to run as virtual - as well as all of the following configuration steps (server settings set for courier-imap). The squirrelmail login screen is viewable on any browser (e.g. [http://webmail.mydomain.com](http://webmail.mydomain.com)).  

However, if I try to login with a valid user and password (that works in thunderbird) I get an (Authentication Failed. Please try again) error in the browser.  Now, I don't suppose that would be bad if I were able to troubleshoot the problem, however none of my logs do a thing.  syslog, mail.info, & mysql.log don't change at all.  This has me thinking that squirrelmail isn't even trying to send/receive information with courier - which leaves me quite stuck.

Any ideas on what I should try?  I've looked at the squirrelmail website faqs, checked the howtoforge walkthroughs, but none of them mention this kind of problem.  All errors I have run across on the web so at least something in the sytem logs.

Thanks

---

