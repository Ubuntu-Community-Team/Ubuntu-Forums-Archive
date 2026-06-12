---
title: "Tripwire &amp; Email"
date: 2015-06-12
forum: Security
---

### Post by patrikmellq on 2015-06-12
Hello i try to make my configuration to get Tripwire to send email.

I have change and edit the /etc/tripwire/twpol.txt     file with my email "MyEmail@gmail.com"
I have wrote a comma sign after the **severity=** line and putting     **emailto=** on the next line and that works fine - no errors when updating changes.

```

(   
rulename = "Networking Programs",   
severity = $(SIG_HI),   
emailto = MyEmail@gmail.com

```

I am using SMTP and it is working fine with Logwatch on my computer - i get email each day via SMTP and Logwatch.
This is how my original twcfg.txt file look like:

[IMG]http://i61.tinypic.com/xssqf.png[/IMG]

And this is how it looks like when i add SMTPHOST and SMTPORT

[IMG]http://i59.tinypic.com/343n9rm.png[/IMG]

But then i get the following error message when i try to send test mail.

```

patrik@patrik:~$ /usr/sbin/tripwire --test --email MyEmail@gmail.com
Sending a test message to: MyEmail@gmail.com
### Error: The SMTP server returned an error.
### Error Number:530 5.7.0 Must issue a STARTTLS command first.
### j6sm957858laj.13 - gsmtp
### Exiting...
Email test failed.
patrik@patrik:~$ 

```

Cheers

---

### Post by patrikmellq on 2015-06-13
I look up the Error Number:530 but i am not sure what this means!
My SMTP is set up with email and password to get direct access to my gmail account.
And Logwatch sends daily emails to my gmail account and its working great.

[h=3]530 SMTP authentication is required.[/h] You have enabled SMTP authentication for the IP range that the user  is connecting from, but the user has not configured his client to use  SMTP authentication. 
There's two ways to solve this problem. 
Either  configure your email client to use SMTP authentication. 
This setting is  normally found in the account settings in your email client. 
Or, disable  SMTP authentication for the IP range. 

The first solution is recommended  since it reduces the risk that anyone will send spam through your  server.

 By default, hMailServer does not require SMTP authentication for  connections coming from localhost / 127.0.0.1. 
For connections coming  from other hosts, SMTP authentication is required for deliveries to  external recipients. 

By default, hMailServer never requires SMTP  authentication for deliveries to local accounts, since that would  prevent other e-mail servers to deliver email to your installation. 
For  information on how to enable SMTP authentication, check the [HOWTO]("https://www.hmailserver.com/documentation/v5.5/?page=howto_enable_smtp_authentication_in_client").


 If you are using a Cisco router, you may need to disable SMTP Fixup  protocol. 
If this is enabled, the router will sometimes intercept SMTP  traffic and replace data in it before it reaches hMailServer which will  cause problems.

---

### Post by patrikmellq on 2015-06-13
I check the Error Number:530 5.7.0 Must issue a STARTTLS command first.
I check SSMTP ans the settings are correct.
```

# Use SSL/TLS before starting negotiation
UseTLS=Yes
UseSTARTTLS=Yes

```

---

