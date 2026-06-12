---
title: "postfix setup"
date: 2010-12-15
forum: Security
---

### Post by fairbro on 2010-12-15
I am a Ruby on Rails developer and have setup a linode vbs server with Ubuntu to host my apps.

I have also used the following article to setup an email server with Postfix.

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04)

I would much rather just host email with Gmail and not have to worry about my own mail server but clients want to be able to send email from their domain name and through their local mail app without paying for the business version of Google apps.

My question to you is, how secure is my setup and how much maintenance does it require?

I am more of a programmer than a Linux guru. Am I nuts or is it a relatively manageable setup? 

I don't want to really worry about mail, I would rather just focus on developing apps.

Sorry if this question is not really Ubuntu related.

Cheers

---

### Post by HermanAB on 2010-12-16
Howdy,

Installing and configuring Postfix is a royal pain in the derrier.

If you want a system that just works, go to [http://citadel.org](http://citadel.org) and run their Easy Install script.  It takes about 20 minutes and the result is an easy to use full featured mail system that can do anything you want.

However, if you only want to forward mail to Google, or your ISP mail server, consider installing nullmailer.  Google for it.

---

### Post by fairbro on 2010-12-16
Thanks for the info Herman.

I have actually got it all working nicely with virtual domains etc but was wondering if it would be a pain to maintain or if it opens up my server to massive security risks?

I hate having to deal with whinging customers because their email isn't working (especially if its my fault!).

Cheers

---

### Post by HermanAB on 2010-12-17
Well, that is why I use Citadel.  The magic of Citadel is really the Easy Install script and Webcit, the web front-end.  It is very easy to set up and configure and then it Just Works (TM).

Postfix, as you know, is very hard to configure, easy to mess up and it is hard to be certain that it is done right.  It is just a Permanent PITA (TM).

---

