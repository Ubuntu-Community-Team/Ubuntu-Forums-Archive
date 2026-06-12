---
title: "Postfix + Zarafa on ububtu"
date: 2015-07-05
forum: Server Platforms
---

### Post by rmit2 on 2015-07-05
I am trying to setup Zarafa on Ubuntu server 12.04 I have followed this link [http://bit.ly/1C4CtEy](http://bit.ly/1C4CtEy) to configure the server
I am a fairly new user to linux. While setting up postfix i gave the hostname as the system name of the mail server. in my case its mail
then the fqdn asssume as example.co.uk

I am unable to send emails locally between the 2 users and the email finds its way to the internet to the actual domain. i am actually trying this setup on a virtual machine. If i send an email to an external domain it reaches without any issues. ( well since its a test environment, my outgoing  email is classified as  spam and i could see that it actually reaches the mail server of the intended domain)

My question is why am i unable to send email between the 2 users i have created in zarafa. 
i am actually sensing if i have set the mydestination parameter incorrectly in the main.cf
I have attached main, master and host and hostname files. Can you please point out what actually is incorrectly set.

---

### Post by volkswagner on 2015-07-05
If your users have email addresses like [email]tom@mail.example.co.uk[/email], then your main.txt is correct.

If your users have email addresses like [email]tom@example.co.uk[/email], you should remove the "mail." from that name (in myDestination).

---

### Post by rmit2 on 2015-07-08
Thank you

---

