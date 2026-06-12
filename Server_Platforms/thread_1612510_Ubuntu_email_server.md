---
title: "Ubuntu email server"
date: 2010-11-03
forum: Server Platforms
---

### Post by msjones on 2010-11-03
Hi,

First post here in a long time, hope you are all still friendly :)

I have recently set up an ubuntu 10:04 based email server using postfix, clamav and squirrelmail. The setup works like a beast, much better than the old sco based system we were using.

Anyway I work for a law firm, and we have use a bespoke case management system to complete work on cases. We have started a paperless office initiative. This means we are asking more and more clients and firms to correspond via email. This is where my troubles are kicking in. The governing body of solicitors in the UK is very picky, and we have to have certain formats and information in documents when sent out to clients, this is the same for emails.

I have a script that will cat the html header information, then cat the body of the email and finally cat the footer html information. The output of which is perfect and usable to the firm.

My problem comes sending this file. The end of the script I have the following:
```
mail -s $SUBJECT $CLIENTS_EMAIL < email.$$$
```
Pretty self explanatory. But when the email is sent from the mail queue its not delivered in html format but in plain text.

Any email sent using outlook from any machine on the network can send and receive html email. How can I make this happen from the command line?

Thanks in advance for any help, apologies for the essay!

---

### Post by HermanAB on 2010-11-03
Howdy,

You got to add a MIME type header identifying the email as html format.

---

### Post by SeijiSensei on 2010-11-03
I wrote a PHP application once to send HTML email.  It requires a bit of work to get all the headers and boundaries in place.  I found the easiest solution was to construct an HTML template message in Thunderbird and mail it to myself.  I then used Thunderbird's "View > Message Source" command to open the entire message and copy the MIME structure to my application.  Then I could muck with the script to create the plain-text and HTML versions of a message and stick them between the appropriate dividers.

For details on MIME-encoded email, read [RFC2045]("http://www.faqs.org/rfcs/rfc2045.html") and [RFC2046]("http://www.faqs.org/rfcs/rfc2046.html").  

Once I got a format that worked, I just used the same dividers for every message I sent.

---

### Post by msjones on 2010-11-05
Thanks for the help, much appreciated. Working on it now, any more problems and ill be back!

---

