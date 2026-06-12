---
title: "Cannot edit file - permisions?"
date: 2009-10-26
forum: Server Platforms
---

### Post by niall.davis@hotmail.co.uk on 2009-10-26
Hi,
 
I have just installed my first linux server as a mail server - UBUNTU 9 Server.
 
The base installation seemd fine and then, using the admin guide "mail filtering section", I configured the mail filtering (CLAMAV and Spamassassin). Whilst the packages where installed OK - the configuration seems to have stopped with an error.
 
The admin guide instructs me to edit a file so that the state is enabled. The actual excerpt from the guide is as follows:

[INDENT]
[LEFT]*5.2.2. Spamassassin*

*Spamassassin automatically detects optional components and will use them if they are present. This means that there is no need to configure pyzor and razor.*
*Edit /etc/default/spamassassin to activate the Spamassassin daemon. Change ENABLED=0 to: ENABLED=1*[/LEFT]
[/INDENT]So I entered:
 
**edit /etc/default/spamassassin**
 
The response is:
 
**Warning: unknown mime-type for "/etc/default/spamassassin" -- using aplication/octet-stream" Error: no write permission for file "/etc/default/spamassassin"**
 
I wondered if I needed to elevate to root so I tried:
 
**sudo edit /etc/default/spamassassin**
 
And the response was:
 
**[sudo] password for support:**
**Warning: unknown mime-type for "/etc/default/spamassassin" -- using "application/octet-stream" Error: no "edit" mailcap rules found for type "application/octet-stream"**
 
As a complete Linux novice I would very much appreciate some help on this.
 
Many thanks in advance.
 
Niall.

---

### Post by ToddAP79 on 2009-10-26
try this command
sudo chmod -R 777 [B]/etc/default/spamassassin

is should change the permissions on the file.

not sure if this will cause any problems in the future.
[/B]

---

### Post by niall.davis@hotmail.co.uk on 2009-10-26
> **ToddAP79 said:**
> try this command
sudo chmod -R 777 [B]/etc/default/spamassassin

is should change the permissions on the file.

not sure if this will cause any problems in the future.
[/B]
Hi, thanks for the quick reply.
 
I have just tried and same issue persists:
 
[EMAIL="support@SVCNET-TEST1~$"]**support@SVCNET-TEST1~$**[/EMAIL][B] sudo chmod -R 777 /etc/default/spamassassin
[sudo] password for support:
[/B][EMAIL="support@SVCNET-TEST1:~$"]**support@SVCNET-TEST1:~$**[/EMAIL][B] edit /etc/default/spamassassin
Warning: unknown mime-type for "/etc/default/spamassassin" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
[/B][EMAIL="support@SVCNET-TEST1:~$"]**support@SVCNET-TEST1:~$**[/EMAIL][B] sudo edit /etc/default/spamassassin
Warning: unknown mime-type for "/etc/default/spamassassin" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
[/B]
Any ideas?
 
Thanks again,
 
Niall.

---

### Post by diesch on 2009-10-26
> **niall.davis@hotmail.co.uk said:**
> [B]
edit /etc/default/spamassassin[/B]

The response is:
 
**Warning: unknown mime-type for "/etc/default/spamassassin" -- using aplication/octet-stream" Error: no write permission for file "/etc/default/spamassassin"**
 
I wondered if I needed to elevate to root so I tried:
 
Yes, you do.
> **niall.davis@hotmail.co.uk said:**
> 
And the response was:
 
**[sudo] password for support:**
**Warning: unknown mime-type for "/etc/default/spamassassin" -- using "application/octet-stream" Error: no "edit" mailcap rules found for type "application/octet-stream"**


*edit* isn't a text editor but a program that uses the mailcap database to find a program suitable to edit a given file. Usually that doesn't work well for config files, so you better use a real text editor like nano:

```
sudo nano /etc/default/spamassassin
```

---

### Post by diesch on 2009-10-26
> **ToddAP79 said:**
> try this command
sudo chmod -R 777 [B]/etc/default/spamassassin

is should change the permissions on the file.

not sure if this will cause any problems in the future.
[/B]

**DON'T DO THIS!!!! **

Restricted permissions are there for a reason. Changing them without exactly knowing what you do can cause severe problems and may create security holes.

---

### Post by ToddAP79 on 2009-10-26
> **diesch said:**
> **DON'T DO THIS!!!! **

Restricted permissions are there for a reason. Changing them without exactly knowing what you do can cause severe problems and may create security holes.

sorry, didn't know, still really new to this.

---

### Post by niall.davis@hotmail.co.uk on 2009-10-26
> **diesch said:**
> Yes, you do.


*edit* isn't a text editor but a program that uses the mailcap database to find a program suitable to edit a given file. Usually that doesn't work well for config files, so you better use a real text editor like nano:

```
sudo nano /etc/default/spamassassin
```
That works - great!
 
Thanks very much to all!!
 
Niall.

---

### Post by HariharanS on 2012-08-07
Thanks a lot for the "nano". It helped. :)

---

### Post by Habitual on 2012-08-07
> **ToddAP79 said:**
> ...sudo chmod -R 777 [B]/etc/default/spamassassin
[/B]

Changing permissions to force it to work does NOT fixing anything. 
And for the Love of Pete, make a note, Todd, to cp first with ```
sudo cp /etc/default/spamassassin /etc/default/spamassassin.org
```, **then** you can screw up (and fix) your own mistakes after that. :)

"Experience is what you got by not having it when you need it".

I hope this doesn't come off as Flame-ish, but I merely seek to correct bad form.

Peace!

---

### Post by sffvba[e0rt on 2012-08-08
[IMG]http://i299.photobucket.com/albums/mm313/Zenzirouj/ThreadNecro.gif[/IMG]


404

---

