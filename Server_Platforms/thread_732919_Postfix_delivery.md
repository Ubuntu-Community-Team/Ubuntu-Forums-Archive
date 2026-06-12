---
title: "Postfix delivery"
date: 2008-03-23
forum: Server Platforms
---

### Post by chrisdeeley on 2008-03-23
I currently have postfix setup to deliver mail for users which are stored in an LDAP directory.

Is it possible to setup postfix to deliver messages to users from an LDAP database, but block messages sent to local users such as root etc.

---

### Post by Mr. C. on 2008-03-25
You can block deliver to local users, but perhaps it may not be the best idea.

What are you trying to accomplish?

Show your postconf -n output for additional questions.

---

### Post by chrisdeeley on 2008-03-26
How can this be done and why do you say it may not be a good idea? 

I am setting up a mail server for the company I work for. 

As yet, postfix is not installed so I cannot provide postconf output. I just know from past experience that by default, mail is delivered when addressed to root and other local users.

There isn't any real reason for wanting to do this, I just want to stop messages being delivered to users like root@mycompany and postfix@mycompany. Basically the users which are created by default when applications are installed.

Thank you for your help.

---

### Post by HermanAB on 2008-03-26
It is not a good idea to block the delivery since their may be important debug/problem information in those reports.  You should rather truncate the mailboxes monthly using 'logrotate'.

---

### Post by Mr. C. on 2008-03-26
> **chrisdeeley said:**
> 
There isn't any real reason for wanting to do this, I just want to stop messages being delivered to users like root@mycompany and postfix@mycompany. Basically the users which are created by default when applications are installed.

Setup your mail server correctly first; when you get to the step where you need to block certain addresses, post again with that question.  There are plenty of easy ways to do this.  Blocking such mail will be the least of the problems you'll face.

---

