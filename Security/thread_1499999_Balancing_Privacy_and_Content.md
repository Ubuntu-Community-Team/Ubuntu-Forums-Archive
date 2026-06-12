---
title: "Balancing Privacy and Content"
date: 2010-06-02
forum: Security
---

### Post by markbahnman on 2010-06-02
Tried asking people's thoughts in the cafe but got no response so I'll try here.
 
Basically I've been working on a website and with all the recent issues with privacy and accounts with big companies (Google, Facebook, etc) I've been trying to figure out a solution that balances user privacy while maintaining quality user content. On the one end of the spectrum, I see that near complete anonimity isn't exactly the healthiest of states (i.e. *chan) but I see the need to combat things like spam and abuse while trying to encourage quality user content (comments, videos, etc). 
 
My question is, what do people think is a good system to balance the need to allow users to control their information and encourage quality content? Examples of attempts at this I think are Gawker's auditioned commenter system, Open IDs or creating your own account system with bare bones personal information requirements.

---

### Post by noway2 on 2010-06-02
I have been working on a e-commerce site for about a year now and have recently gotten to the point where I need to think about these kinds of concerns.  One way to turn the question on end is to ask: as a system administrator what obligations do I have to my clients?

I would say that many are not going to want to provide information that is personally identifiable unless there is a valid, justifiable need to.  For example, in an e-commerce application you need a name and billing / shipping address.

If you do obtain any such information you have an obligation to keep it safe.  Is it stored electronically?  Can a cracker get at it and make use of it for nefarious purposes?  Consider storing data only in encrypted format (PGP can work here).  Do you support cookies on your site and if so, for what purpose?  Some people won't accept scripting on sites, so you may need to account for this too.  What about email?  Will you solicit to your clients and will they consider it spam?

Speaking of scripting you should be concerned about data received from a user and be sure to sanitize it properly.   On the flip side, you need to be sure any output you present has been properly sanitized too.  You have a responsibility to prevent cross site scripting and SQL injection.  Along the lines of SQL, if you use a database back end there are a lot of things to consider security wise.  

Also consider the administrator interface to your site.  If you use common programs such as phpmyadmin these can be the target of crackers, so be sure to protect them properly.

I am sure there are lots of things I am missing, but these things come to mind right now.

---

### Post by sidzen on 2010-06-04
Give people an interface, like Bastille ([https://help.ubuntu.com/community/BastilleLinux](https://help.ubuntu.com/community/BastilleLinux)) where *they* make the choices with regard to degree of privacy?

---

