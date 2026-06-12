---
title: "Problems with Postfix and Outlook"
date: 2009-03-10
forum: Server Platforms
---

### Post by markdt on 2009-03-10
I've configured Postfix and Dovecot on my Ubuntu 8.1 box. Things seem to be mostly working. When I attempt to setup an account in Outlook on my windows desktop to send/receive mail via this box, I run into a strange problem.

Outlook can login to the POP server just fine, and it can contact the SMTP server, but it fails to send the test message saying:
&#8220;Send test e-mail message: The specified server was found, but there was not response from the server. Please verify that the port and SSL information is correct&#8230;..&#8221;

The really strange thing is that I can open a telnet session on the same Windows box and connect to the SMTP server at port 25 and manually create and send a mail and everything seems to work fine--both to internal and external domains.

I'm using the private IP address of the Ubuntu box in the Outlook setup just to avoid any naming issues and the mail log clearly shows that Outlook is connecting with the SMTP server, but it fails to send the mail. Outlook says there was "no response".

I think that Postfix is at least basically setup correctly because I can manually send mail using telnet.

Also, I tried the same Outlook setup on another machine on the same network with the same results.

I'm stumped... I'd be happy to send main.cf or any other configuration files, but I am really stumped as to where to look for this problem.

Thanks!!
Mark

P.S.: One more interesting detail: I just tried installing Thunderbird and it WORKS! (Yes, I know, I should probably switch to Thunderbird, but I can't force the other people on my network to change--I need to get Outlook working).

---

### Post by HermanAB on 2009-03-10
"Please verify that the port and SSL"

It sounds like you enabled SSL on Outlook, but not on Postfix.

Anyhoo, once you are tired of playing with postfix and want a system that works, install Citadel.  It only takes about 20 minutes using the Easy Install script:
[http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)
:)

Cheers,

Herman

---

### Post by markdt on 2009-03-10
Thanks, but no, I've checked that. I do not have the "This server requires an encrypted connection" box un-checked in Outlook. I believe that Outlook is attempting to connect on port 25 with an un-encrypted connection.

Mark

---

