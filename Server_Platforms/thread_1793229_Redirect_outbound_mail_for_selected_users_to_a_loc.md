---
title: "Redirect outbound mail for selected users to a local account."
date: 2011-06-29
forum: Server Platforms
---

### Post by john_spiral on 2011-06-29
Hi,

I've setup an Ubuntu mail server using Postfix/Dovecot from the below excellent guide:

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

It's all working well.

I've spent a fair amount of time looking into way I can 're-route' _outbound_ email for selected users to a mangers internal inbox, for review purposes, in a sales environment.

The Dovecot/Sieve plugin looks like it might work, but are there any other solutions?

Looks like Postfix alone might be up to the task but most threads advise against this route as the script becomes unwieldy to maintain.

Enough of my waffling.

Your input will be greatly appreciated. Is Dovecot the beast I'm after?

Thanks

John

---

### Post by SeijiSensei on 2011-06-29
> **john_spiral said:**
> Is Dovecot the beast I'm after?

No, it's an IMAP/POP server so it only handles messages after they've been sent.  If this were an option, I'd use a simple [procmail]("http://www.procmail.org/") recipe based on the From: header.

Your problem is a very difficult one, I think.  I've spent a few minutes mulling over possible solutions, and any I can think of require some custom programming.  What you'd need to implement is called a "store-and-forward" method where all outgoing messages are put in a queue, then a program extracts the messages from the queue, and decides where they should be delivered based on the From: address.  This is akin to how [MailScanner]("http://www.mailscanner.info/") does scanning for spam and viruses.  All messages are placed in a custom queue, /var/spool/mqueue.in, then a Perl script grabs each message from that queue, scans it, and takes appropriate actions.  Ones that pass the scanner are sent along to their final destinations using another instance of the SMTP server.

If you asked me how to handle this problem as a consultant, I'd suggest using a custom internal web application.  Salespersons would fill out an HTML form which, when submitted, would notify the manager that a pending message needs review.  The manager could then use the application to bring up the message, review it, and either click one button to send it to its intended recipient, or click another button that would send it back to the sales person with comments attached.  One nice thing about this approach is that you'd be archiving each of these messages in a database.

---

### Post by john_spiral on 2011-07-01
thanks for your input **SeijiSensei**

After a couple of weeks of Googling for a postfix solution I decided to look at Exim:

[http://forums.cpanel.net/f5/outgoing-mails-copy-39909.html](http://forums.cpanel.net/f5/outgoing-mails-copy-39909.html)

Looks like the below edit of /etc/antivirus.exim might do the trick, will report back with my success:

[FONT="Courier New"]if first_delivery
and ("$h_from:" contains "@domain.com")
and not ("$h_X-Spam-Checker-Version:" begins "SpamAssassin")
then
unseen deliver "monitor@domain.com"
endif[/FONT]

---

### Post by john_spiral on 2011-07-11
I've figured out another easier solution:

Set-up a new headless mail server called _**salesmail**_ ,using postfix, with your current mail server as your 'relayhost' in the /etc/postfix/main.cf file. 

Keep the mynetworks parameter the same.

Make the changes detailed in the below guide "Redirecting outgoing mail with Postfix":

[COLOR="Blue"][http://johnleach.co.uk/words/797/redirecting-outgoing-mail-with-postfix](http://johnleach.co.uk/words/797/redirecting-outgoing-mail-with-postfix)[/COLOR]

All you now need do is configure the mail clients with the new smtp server _**salesmail**_.

The above set-up isn't perfect as both outbound external and outbound internal mail will how route via the email address specified in the below line:

/etc/postfix/recipient_canonical_map:

/./	[email]devteam@example.com[/email]

I guess it might just be a case of changing the above regexp to filter out internal mail?

---

### Post by john_spiral on 2011-07-13
Hi,

I've now got outbound internal mail routing correctly via a redirect based on the "To" header, please refer to:

[http://rackerhacker.com/2007/07/01/redirect-e-mails-in-postfix-based-on-subject-line/](http://rackerhacker.com/2007/07/01/redirect-e-mails-in-postfix-based-on-subject-line/)

Summary:

The below config is implemented on the **_salesmail_** server.

Enable header checks in /etc/postfix/main.cf:

header_checks = regexp:/etc/postfix/header_checks

Make sure the above line is placed before (see my previous post on this thread):

recipient_canonical_classes = envelope_recipient
recipient_canonical_maps = regexp:/etc/postfix/recipient_canonical_map 

Then, create /etc/postfix/header_checks and add the following:

/^To: *.john*.smith@domain*/   REDIRECT [email]john.smith@domain.com[/email]
/^To: *.susan*.smith@domain*/   REDIRECT [email]susan.smith@domain.com[/email]

Note the '***.**' (regexp) in the above file.

---------------------------------------

I know the system I've implemented isn't elegant but it seems to work. If you've got an easier solution please contribute.

---

