---
title: "Postfix help..."
date: 2008-08-18
forum: Server Platforms
---

### Post by hockey97 on 2008-08-18
OK so I recently installed postfix and it works, but I notice when I send an e-mail to like g-mail I notice that it shows the address that it was sent by www-data , I want it to be like admin@mydomain

how can I do this??

I also would like to use mysql to add new users ect.

I want to know how I can create users and addresses like [email]user@mydomain.com[/email] ect or [email]user@mail.mydomain.com[/email] ect.

how can I do this and is there a good website that would provide a tutorial.

---

### Post by MJN on 2008-08-19
> **hockey97 said:**
> OK so I recently installed postfix and it works, but I notice when I send an e-mail to like g-mail I notice that it shows the address that it was sent by www-data , I want it to be like admin@mydomain
 
how can I do this??The From: address is the responsibility of the sending client. As you've mentioned www-data I'm guessing this is most likely a PHP script so modify it to include a From: address.
 
> I also would like to use mysql to add new users ect.Someone else will have to help with this one as I don't use MySQL (for Postfix).
 
Mathew

---

### Post by hockey97 on 2008-08-19
yes I did used the from: thing.

this test I was saying was an auto e-mailer from the registeration which I put from:admin@mydomain.com ect and I still see on the otherside see it being from www-data 

I remeber seeing www-data to be the user permission from php apache bind9 ect. 

Now about the postfix using mysql the reason is that I plan to use php script well will add code to the registeration to create a new e-mail account/address for that new person.

I would also like to make a webmail interface with php to my website so my clients can see their e-mail online.

I currently did test the user already in postfix to send mail I was able to with gmail but with AOL, or Hotmail,or yahoo I get rejected and they send me a error link to a html page saying what the error is. I get that I am blacklisted which I did do a blacklist check with googling tools online to do a check which shows I am clean.

I notice that with these e-mail services I notice they look at the reverse record which is my ISP, plus my ISP dosen't allow servers so once I am finished making the website ect I plan to switch to an ISP that is offering 50 bucks for unlimited dedicated dsl. They told me that for me it would be a T1 same price. 

So thanks for the help so far.

---

### Post by MJN on 2008-08-19
Okay... deep breath as we have even more issues now!

> **hockey97 said:**
> yes I did used the from: thing.Post the relevant code snippet as it's obviously not working. Whatever your client (PHP mailer) says is the From: line is what Postfix will send it out as (unless you've explicitly told it to rewrite but you'd know if you had).

> Now about the postfix using mysql the reason is that I plan to use php script well will add code to the registeration to create a new e-mail account/address for that new person.Sorry, yes, I didn't mean to make it sound like MySQL was a bad idea just that I don't use it hence cannot help.

> I would also like to make a webmail interface with php to my website so my clients can see their e-mail online.To code such a beast would be quite an undertaking. Have you considered one of the existing PHP-based solutions such as Squirrelmail etc? If you're after a particular look you'd be better off putting your effort into skinning what's already there.

> I currently did test the user already in postfix to send mail I was able to with gmail but with AOL, or Hotmail,or yahoo I get rejected and they send me a error link to a html page saying what the error is. I get that I am blacklisted which I did do a blacklist check with googling tools online to do a check which shows I am clean.Without seeing the error it sounds like you'll have to relay outgoing mail via your ISP's mail server (using the **relayhost = [name of ISP's server]**)

> I notice that with these e-mail services I notice they look at the reverse record which is my ISPSome do, some consult RBLs which list known dynamic IP ranges and/or ranges declared as not being authorised to send mail.

Mathew

---

### Post by hockey97 on 2009-08-04
Anyone else can help me config postfix with mysql? 

I did install the addon plugin to postfix to talk with mysql.

I just need to understand what postfix needs from mysql. 

Like can I name the data tables anything? or does postfix have some default names that it will scan mysql and find those names and use those tables?

I have a working postfix server. I can send e-mail outside to any ISP aol,yahoo,gmail...etc. 

I just can't recieve e-mail from the outside to my account on my postfix server.

I want to use mysql So I can use php to create new e-mail accounts and also to provide a e-mail interface with the users mailbox. 

For right now I just need to know how to use mysql with postfix and config it properly to send mail to the outside world and get mail from the outside world. 

I have setup the mx records. I do plan to use php to create a web interface with the users mailbox. 

I did looked at many online tutorials and how to's but it's very confusing.

They never talk about the mysql data tables on what those tables needs to posses. I mean I understood you need to install that postfix-mysql plugin.
Then they tell you to make tables in mysql. like an aliase table yet they don't talk about what that table needs to have. They then go right ahead to setting up authentication. 

What I need to know is what are the functions of each mappings. aliase users and other stuff. 

I plan to provide e-mail for 2 domain names. I already setup the mx records.

I just need to get mysql and postfix setup to talk to each other and have postfix to use mysql database for the information of users and virtual domain names and user mail boxes location.

---

### Post by cdunbar on 2009-08-04
Hello,

The Postfix community is very active and has a great mailing list for asking questions and getting help. Here is a link to their main mailing list page:

[http://www.postfix.org/lists.html](http://www.postfix.org/lists.html)

Regards,
Chris

---

