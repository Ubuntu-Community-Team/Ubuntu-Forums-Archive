---
title: "POP to IMAP"
date: 2007-05-16
forum: Server Platforms
---

### Post by jelledc on 2007-05-16
In my father's company we recently installed a new server, running the feisty server edition.
Now we'd like to use IMAP to check our email as we mail a lot and we want a safer and better way to manage our email then pop3.
The problem is that our existing email-addresses are hosted by our isp, and support only pop3.
Is there a way we could set up our server to fetch the mail from the pop-server, and "re-host" it through IMAP?

or are there any other solutions for this? We want to keep using the same addresses as before.

---

### Post by Frosty Cold Drink on 2007-05-16
Yes! Fetchmail!

[http://fetchmail.berlios.de/fetchmail-man.html](http://fetchmail.berlios.de/fetchmail-man.html)

Set up your IMAP server, and have fetchmail download the POP3 emai and forward it to the local mail server.

You can actualy run fetchmail as a daemon too, si it will just run in the background and do its thing without you having to call it from cron.

---

