---
title: "Help Control My E-MAIL Server!"
date: 2010-01-29
forum: Server Platforms
---

### Post by idlemind324 on 2010-01-29
Hello,

I manage several different MTA's and I'm looking for help in finding a solution to help me control them better. I want to be able to implement some limitations to users of my SMTP services. I would like to only accept requests for mail relay based on 2 parameters: message size, and number of recipients. Most MTA's make this possible but they I haven't found a way to have a message filtered both ways. For example I want setup rules like the following (incoming and outgoing):


[LIST]
[*]Allow mail with 10 or less recipients to have no limit on message size.
[*]Decline all mail with 10 or more recipients that have message size over 10MB.
[*]Decline all mail with 500 or more recipients (traditional rule)
[/LIST]

What this allows:

[LIST]
[*]A message between 0 and 10 people without any restrictions on size
[*]A message between 0 and 500 people under 10 MB in message size
[/LIST]

I'm open to suggestions of different SMTP servers to use as a relay along with any other solutions the bright minds here on Ubuntu forums have to offer.

For Clarity My MTA's Are:

[LIST]
[*]Exchange (I wouldn't mind finding a Linux based MTA to place as a relay in front of this server)
[*]Postfix
[*]MailFoundry
[/LIST]
Thank you,

---

