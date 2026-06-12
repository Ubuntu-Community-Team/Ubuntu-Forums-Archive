---
title: "Seting up mail server and MX Records"
date: 2007-06-20
forum: Server Platforms
---

### Post by TorchlightJay on 2007-06-20
Okay, I am not sure if this is the group to ask but my service provider say that can't help with specifics but anyway, let me break it down. I am with GoDaddy and want to create a mail server. For the sake of the example, my domain is example.com. and I want to create a mail domain called mail.example.com. I went to the DNS control and MX records and I am not sure what I put down. I know you can put down something to make it refer to mail.example.com as a mail server. How do I do it with osmething like GoDaddy? I am not sure how to enter MX records or CNames or if I am even doing the right thing. Also, maybe there is osmething I need to set inside of my actual server in order for it to work. I have an Ubuntu 7.04 server running postfix and dovecot right now. Thanks all.

---

### Post by matt_b on 2007-06-20
I'm not sure what the control panel is like on GoDaddy so can't give you specific instructions - but generally setting up your DNS to handle mail usually involves setting up an A record (e.g. "mail.yourdomain.com" to point to your public IP address), then setting up an MX record using the A record you just created ("mail.domain.com"). Set the MX priority value to anything you like (e.g. 10), as you'll only have the one server to handle mail. Ignore CNAMEs - they're not used for setting up mail.

You can then use the tools on [DNSreport]("http://www.dnsreport.com") to check that you've got it set up correctly (after you've given ~24 hours for the DNS change to take effect).

Once you've got mail correctly pointed at your IP address, you'll need to ensure port 25 on your firewall is forwarded/given access to your server. Then, provided you've configured postfix correctly mail should start coming into your server.

[I'm a real postfix newbie so someone else will have to advise on setup :)]

---

### Post by Mr. C. on 2007-06-20
Let's clarify a little more:

For Receiving:

[LIST=1]
[*]An MX record for your domain which specifies the mail server (eg.smtp.mydomain.com) that other mail servers will consult to forward mail to your domain.

[*]If there is no MX record, an A record will be consulted and used.  Its best to have an MX record to minimized DNS lookups.

[*]Setup required RFC email addresses (postmaster, abuse, etc.)

[*]Ensure your system is not an open relay.
[/LIST]

For Sending:
[LIST=1]
[*]A PTR record mapping your IP back to your A record.  This is becoming a requirement by many mail servers to prevent SPAM.

[*]A static IP, non-residential.  This is becoming a requirement by many mail servers to prevent SPAM.

[*]Your ISP must not block outbound port 25.

[*]You must manage your server with care, or your server will end up on one or more blacklists.
[/LIST]

Once you have these basics, run the Domain Name Tests at:

[http://www.dnsstuff.com/](http://www.dnsstuff.com/)

MrC

---

### Post by TorchlightJay on 2007-06-21
Sweet, I set it up and everything looks like it works. Thanks all. Hey by any chance, would you know of any good tutorials for setting up a web server.

I am trying to get webmail through squirrelmail and on that same token, I am setting up postfix and dovecot to get my SMTP and IMAP up I found some tutorials but they seemed vague or whatever. Oh might I also add, more than one domain is hosted off of this server. Do you know of a good tutorial? Thanks all.

---

### Post by Mr. C. on 2007-06-21
Start a new thread with the subject that reflects your new request; other's will more like help and benefit.

MrC

---

### Post by Brazen on 2007-06-21
> **TorchlightJay said:**
> Sweet, I set it up and everything looks like it works. Thanks all. Hey by any chance, would you know of any good tutorials for setting up a web server.

I am trying to get webmail through squirrelmail and on that same token, I am setting up postfix and dovecot to get my SMTP and IMAP up I found some tutorials but they seemed vague or whatever. Oh might I also add, more than one domain is hosted off of this server. Do you know of a good tutorial? Thanks all.

check out the official server documentation at help.ubuntu.com.  It has a section on setting up an email server here: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html)

---

### Post by Mr. C. on 2007-06-21
> **Brazen said:**
> check out the official server documentation at help.ubuntu.com.  It has a section on setting up an email server here: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html)

Hmmm. I think the OP was asking about DNS and the records required to operate a mail server; the provided overview describes nothing about DNS or the required records.

MrC

---

