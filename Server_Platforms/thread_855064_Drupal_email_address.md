---
title: "Drupal email address"
date: 2008-07-10
forum: Server Platforms
---

### Post by bakaeigo on 2008-07-10
How can I set the administrator email in Drupal so that it can actually send emails? I set it as my personal email, but it is unable to send messages from it. Do I also have to set up my server for email?

---

### Post by bakaeigo on 2008-07-10
Bump

---

### Post by rickyjones on 2008-07-10
> **bakaeigo said:**
> How can I set the administrator email in Drupal so that it can actually send emails? I set it as my personal email, but it is unable to send messages from it. Do I also have to set up my server for email?

Do you have a Mail Transport Agent (MTA) installed on your server? An example would be Postfix. Without it you will not be able to send email.

-Richard

---

### Post by bakaeigo on 2008-07-10
> **rickyjones said:**
> Do you have a Mail Transport Agent (MTA) installed on your server? An example would be Postfix. Without it you will not be able to send email.

-Richard

No, I do not. How do I install and configure an MTA?

---

### Post by rickyjones on 2008-07-10
> **bakaeigo said:**
> No, I do not. How do I install and configure an MTA?

The absolutely simplest way to go would be to install Postfix in my opinion. There are hundreds of guides out there for the configuration portion of it.

To install: sudo aptitude install postfix

During the install it will ask you some basic questions. I believe you should be able to use most of the defaults and you will be able to send email out (so long as your internet connection and/or ISP is OK with this).

Some links to get you started as well:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Sincerely,
Richard

---

### Post by bakaeigo on 2008-07-11
Is there some other kind of thing I could use instead? :confused: I've tried all the guides I can't seem to get any of them to work for me.

---

### Post by rickyjones on 2008-07-11
> **bakaeigo said:**
> Is there some other kind of thing I could use instead? :confused: I've tried all the guides I can't seem to get any of them to work for me.

That is the only product that I've used. How is it not working? Are you getting any error messages? How did you configure it? 

Thanks,
Richard

---

### Post by bakaeigo on 2008-07-11
When using this guide ([https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)) and telnetting to "localhost 25", it connects but does not print out the statement that it is apparently supposed to:
> 220 localhost.localdomain ESMTP Postfix (Ubuntu)
Neither does it give any of the prompts that it is supposed to, e.g when I type "ehlo localhost". And of course it does not send the message at the end.

Sorry, I'm new to this :confused:

---

### Post by bakaeigo on 2008-07-12
Nevermind -- I got sending emails to work by purging and reinstalling the required packages. But I still have one problem -- Any email that is sent is always marked as spam. How do I fix this?

---

### Post by bakaeigo on 2008-07-13
Bump :(

---

### Post by Yfrwlf on 2008-10-04
> **bakaeigo said:**
> Bump :(

Not sure if you care anymore, but I think the key is to relay your email through your ISP or some other email server which isn't blacklisted or is whitelisted.  Basically, your domain isn't trusted by most email servers so they won't want to recognize you.  Annoying, and I'm not sure how you're supposed to "get on their good side", but one workaround is to relay through your ISP which will most likely be viewed more positively.

If that doesn't solve it, I think you can set up your mail server to log into another mail server and send mail to it instead.  So basically for example, you give your server your username and password to connect to Gmail, so it'd be like you were using your server as a mail client, so the emails to your users will be being sent from your Gmail account.

Unfortunately, I hate email for reasons like these, because it has to be so complicated to do the most basic stuff like this.  You'd think that by default Drupal would at least have something that allowed the easy configuration of email.  I mean, getting users registered by being able to send them registration emails is a pretty basic need for Drupal, so it's a pity there's not a more elegant solution, and email configuration is just flat out ignored by the Drupal installation guides.

That said, I've heard that there were supposed to be some Drupal email modules to make email configuration easier, somehow, but I'm not sure what they do or if they work.

So, to sum up, you can either edit your php.ini file and tell it to somehow relay or be an email client, possibly, or if you can't do it through php, you can leave it alone because it's configured to use sendmail, and then you can configure sendmail to do it instead.  Or, you can change it to use some other mail server thingy other than sendmail I think.

I just wish there was some easy way, like a GUI or easy self-contained package or something.  Point, click, done.  Please. :P

---

