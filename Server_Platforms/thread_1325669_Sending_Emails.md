---
title: "Sending Emails"
date: 2009-11-13
forum: Server Platforms
---

### Post by velkymx on 2009-11-13
I am currently setting up my own web server to host a few of my personal domains. They are not large traffic sites but I still need to have all of the features my current paid service has.

So far I've got PHP/MySQL/Subversion all working great. Only piece of the puzzle missing is the email. I'd like to have my web sites send emails when users sign up or with alerts.

I've kind of got postfix working, but it is only sending as root@localhost and while that works for me internally it really doesn't work for clients who receive the emails. So I adjusted the hosts to make it [email]root@mydomain.com[/email] but only for the one domain and only for root.

So my question is how do I add a user file to my postfix and how do I add multiple domains?

---

### Post by JonRohan on 2009-11-14
Have a read through this: [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

---

### Post by velkymx on 2009-11-18
Thanks for the link to the tutorial. Didn't really help as I don't want to setup mailboxes - I just want to be able to send emails from my web site...

Things like:

Thanks for signing up

You've got a reply to your forum post

stuff like that.

Anyone??!?

---

### Post by wyldfury on 2009-11-19
A straight "Internet host" installation of Postfix should do what you want. Ubuntu normally asks which type of installation you'd like and asks for the domain etc I think.

Setting the headers and envelope sender is done from PHP.

---

### Post by Bachstelze on 2009-11-19
> **wyldfury said:**
> 
Setting the headers and envelope sender is done from PHP.

This. An example script would look like:

[php]<?php

$to = "recipient@domain.tld";
$subject = "Test.";
$message = "This is a test message.";
$headers = "From: Mr. Sender <sender@otherdomain.tld>";

mail($to, $subject, $message, $headers); [/php]

---

