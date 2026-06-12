---
title: "Email problems with OSSEC-HIDS"
date: 2007-06-24
forum: Server Platforms
---

### Post by gaten on 2007-06-24
I used OSSEC HIDS on my Dapper installation just fine; it would email me my alerts and everything was peachy. Upon installing HIDS onto my Feisty install however, I began having problems with email reporting.

Here is the relevant portion of my ossec.conf:
```
  <global>
    <email_notification>yes</email_notification>
    <email_to>myemail@gmail.com</email_to>
    <smtp_server>smtp.gmail.com</smtp_server>
    <email_from>ossecm@fakehost.net</email_from>
  </global>

```And here is the error from the /var/ossec/logs/ossec.log:
```
2007/06/24 13:54:52 os_sendmail(1704): Mail from not accepted by server
2007/06/24 13:54:52 ossec-maild(1223): Error Sending email to 69.147.95.94 (smtp server)

```At this point, I don't feel like setting up my own mail server, I'd just like to email the alerts to myself like I was doing. Does anyone know how to specify user/pass in OSSEC, or how to solve this issue? Any help would be appreciated.

---

### Post by euler_fan on 2007-08-13
Gmail takes mine fine . . . Have you tried a different "from" address?

It could be your first choice is getting blocked as spam.

---

### Post by gaten on 2007-08-15
>  		Gmail takes mine fine . . . Have you tried a different "from" address?

Nope, I've also tried the same address its being sent to, and 3 other valid email addresses I own. Would you mind posting the email relevant contents of your config? Thanks for the reply.

---

### Post by euler_fan on 2007-08-15
> **gaten said:**
> Nope, I've also tried the same address its being sent to, and 3 other valid email addresses I own. Would you mind posting the email relevant contents of your config? Thanks for the reply.

```
  <global>
    <email_notification>yes</email_notification>
    <email_to>myemail@gmail.com</email_to>
    <smtp_server>gmail-smtp-in.l.google.com.</smtp_server>
    <email_from>ossecm@comp-name</email_from>
  </global>


```

Hope that works for you.

---

### Post by gaten on 2007-08-15
Tried your smtp server, now I get this error. This is driving me insane.

Thanks for trying to help though. I also upgraded to OSSEC 1.3, and still no go. Something odd is going on here.

```
2007/08/15 18:02:47 os_sendmail(1707): End of DATA not accepted by server
2007/08/15 18:02:47 ossec-maild(1223): Error Sending email to 209.85.147.27 (smtp server)
```

---

### Post by euler_fan on 2007-08-15
> **gaten said:**
> Tried your smtp server, now I get this error. This is driving me insane.

Thanks for trying to help though. I also upgraded to OSSEC 1.3, and still no go. Something odd is going on here.

```
2007/08/15 18:02:47 os_sendmail(1707): End of DATA not accepted by server
2007/08/15 18:02:47 ossec-maild(1223): Error Sending email to 209.85.147.27 (smtp server)
```

I don't understand either. When I did a clean install from source on edgy it all worked out of the box. Did you do this most recent install from source?

Out of curiosity, where does OSSEC-HIDS send the alerts when email updates are turned off?

---

### Post by euler_fan on 2007-08-15
Another question: Is this happening when OSSEC starts automatically on boot or is this something that happens when you try to turn it on?

It might be time to post it to the OSSEC user's list and see what pops out of that.

---

### Post by gaten on 2007-08-15
> Did you do this most recent install from source?

Out of curiosity, where does OSSEC-HIDS send the alerts when email updates are turned off?Yes, 1.3 I installed from source (using the install.sh). And it sends all the alerts to /var/ossec/logs/, which I could write a small parser for and whatnot, but the email was working on Dapper and it was very convenient. I'm having no luck w/ Feisty or Edgy. I'm thinking maybe this is a firewall issue (I'm behind smoothwall), so I think I'll start looking through the docs to see what ports I need open. 
> 
Is this happening when OSSEC starts automatically on boot or is this something that happens when you try to turn it on?

It might be time to post it to the OSSEC user's list and see what pops out of that.This happens whenever I restart ossec via **/etc/init.d/ossec restart** (to test new settings). And periodically throughout the day as it tries to send the emails out. 

I sent mail to the user list (and promptly forgot about it): [http://www.ossec.net/ossec-list/2007-July/msg00044.html](http://www.ossec.net/ossec-list/2007-July/msg00044.html)

There doesn't seem to be a solution posted thought, the basic consensus is that I setup my own MTA and stop using google. I still don't understand why it doesn;t work (I check the email for that account every 10 mins, so authentication shouldn't be a problem).

---

### Post by euler_fan on 2007-08-15
> **gaten said:**
> Yes, 1.3 I installed from source (using the install.sh). And it sends all the alerts to /var/ossec/logs/, which I could write a small parser for and whatnot, but the email was working on Dapper and it was very convenient. I'm having no luck w/ Feisty or Edgy. I'm thinking maybe this is a firewall issue (I'm behind smoothwall), so I think I'll start looking through the docs to see what ports I need open. 


This happens whenever I restart ossec via **/etc/init.d/ossec restart** (to test new settings). And periodically throughout the day as it tries to send the emails out. 

Yeah, looks like the list is my last resort. Thanks again.

Good luck. Sorry I couldn't be more help.

---

