---
title: "How to use a Godaddy domain name in Ubuntu 8.04 LTS Server Edition?"
date: 2008-09-22
forum: Server Platforms
---

### Post by lopes_andre on 2008-09-22
Hi,

I have one domain registred in Godaddy.com

I want o use that domain name in my Ubuntu 8.04 LTS Server Edition installation to setup onde website and e-mail server.

There is some documentation or tutorials on how to set-up one domain in Ubuntu 8.054 Server Edition?


Best Regards, André.

---

### Post by jonabyte on 2008-09-22
There are a lot of docs to help you out.

You may want to search the forums here, then google your questions and lastly if those dont help, try one of the manuals available at amazon.

Your question is a little broad, you may want to specify what you want to do first (i.e. have you installed Ubuntu yet? Apache web server?, etc)

---

### Post by lopes_andre on 2008-09-22
Hi,

Yes I have some specific questions.

I have set up one nameserver in Godaddy. But I have only one static IP, so I have only NS1.

Now I have configured my NS1 as (NS1.mydomain.com) and have associated this NS1.mydomain.com with my static IP. I can't configurate NS2 because I don't have any addicional IP.

Now this is done, what is the next step to have the domain name that I buy on Godaddy pointing to my machine?

Best Regards,
Andre.

---

### Post by mbeach on 2008-09-22
I doubt you need to be setting up a nameserver.  Use Godaddy's.  

You want to be setting up an A record to point to your ip address.

[http://help.godaddy.com/article/678](http://help.godaddy.com/article/678)

from there you'll need to port forward your port 80 to your server.  Ensure your server has a static ip on your internal network.

After than, setup Apache (sudo apt-get install apache2) and see what happens.

As for a mail server - I can't help - given up on those - switched to using google hosted services for that functionality.

---

### Post by lopes_andre on 2008-09-22
Thanks for yor reply mbeach.

Yes I can forward the domain to the IP, but I need to use POP3 and IMAP. I think I realy need to do something with nameservers

It is easy to do this, or it is better to forgot it?

Best Regards,
Andre.

---

### Post by lazyart on 2008-09-22
You'll need to specify an MX record, which points to where mail traffic should flow... this goes into your DNS record.

---

### Post by lopes_andre on 2008-09-22
Thanks for your rely lazyart.

One more question. How I update the MX records? 

Where I have:

Goes to: smtp.secureserver.net

I should change to 234.234.3.45 (my IP)?

Sorry for my lameness.


Best Regards,
Andre.

---

### Post by lazyart on 2008-09-22
yup.  Just make sure you designate that as an MX record, and not just an A record.

---

### Post by mbeach on 2008-09-22
godaddy's help on the topic:
[http://help.godaddy.com/topic/332/article/347](http://help.godaddy.com/topic/332/article/347)

I only recommend not managing a mail service because I have many staff who are already familiar with the gmail interface, so it makes sense for me to use google's services.  Plus that eliminates my need to manage the service, backup, etc...  
[http://www.google.com/apps/intl/en/business/editions.html](http://www.google.com/apps/intl/en/business/editions.html)
and google's help if you sign up with them (standard edition is free - check the specs if it is enough for your needs)
[http://www.google.com/support/a/bin/answer.py?answer=33353](http://www.google.com/support/a/bin/answer.py?answer=33353)

---

