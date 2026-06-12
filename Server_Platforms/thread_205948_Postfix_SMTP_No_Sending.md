---
title: "Postfix SMTP No Sending"
date: 2006-06-29
forum: Server Platforms
---

### Post by benjaminjo on 2006-06-29
Hi there - I've setup a Postfix server with Courier IMAP/POP and SASL/TLS. The machine has a direct connection to the internet (ADSL). For some reason I can't send mail through postfix and my sending options  in evolution are set to SMTP server- here's some of my main.cf file.

 > 
myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $myhostname
mydestination = myserver.co.za, localhost, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.0.99/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/

Any tips or help or advice would just be sooooooo great - I'm just about tearing out my hair ;)
my username for a local account is *sales* and password also *sales* - dunno if that helps ....... oh yeah - evolution gives me this error : "Error while performing operation. Welcome response error: Operation now in progress."


Thanks
Jo

---

