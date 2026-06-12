---
title: "exim4 disclaimer"
date: 2009-10-21
forum: Server Platforms
---

### Post by daniele75 on 2009-10-21
Hello.
We have a linux box with ubuntu and exim4 4.63.
I'm trying to insert automatic disclaimer to all outgoing mails.
But after many trying, it seems it doesn't work.
I've tried to send plain text from mail client and from telnet
connections, and also in html format, but disclaimer doesn't appear into
mail.

Configuration is:

transport_filter = "/usr/bin/altermime --multipart-insert
--disclaimer=/etc/exim4/disclaimer
--disclaimer-html=/etc/exim4/html/firma --input=-"

If i try to use the command with a file, for example with a plain text
file "test.txt"

/usr/bin/altermime --multipart-insert --disclaimer=/etc/exim4/disclaimer
--disclaimer-html=/etc/exim4/html/firma --input=./test.txt

it works, and after execute the command, test.txt contains the disclaimer.

But it doesn't work if I send an email.

From /var/log/exim4/mainlog I can see that transport used is one that
I've configured with transport_filter.

Where I'm wrong?

Thanks
Daniele

---

