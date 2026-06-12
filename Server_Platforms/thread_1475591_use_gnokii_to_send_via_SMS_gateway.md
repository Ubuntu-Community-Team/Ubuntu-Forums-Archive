---
title: "use gnokii to send via SMS gateway"
date: 2010-05-07
forum: Server Platforms
---

### Post by Tutigan on 2010-05-07
Hiya guys,

I am using nagios at work (on a virtual machine running ubuntu 10.04), to monitor a dozen windows servers, several links (to external branches) and all the switches on the network. It runs nicely... Except for one small problem.
We have decided that we need notification if something goes done, from nagios, sent to our mobile phones. I have googled the hell out if this, trying to find help... We have our own SMS server on the network, which we want to use -we can NOT use a modem hanging off the nagios server!
From what I have found, it is possible to use gnokii to send SMS through a SMS server, but so far, I have been unable to find out how to configure it to do so... Does anyone know about configuring gnokii to do this? Or another program that will do this for me?
Any help would be greatly appreciated.

---

### Post by robvas on 2010-05-07
Can you just email to an sms gateway?

---

### Post by Tutigan on 2010-05-13
Unfortunately the SMS gateway that we have is a custom-built gateway program on one of the windows servers...
I've been talking to the developer that made it, and he's going to look into parsing the messages from nagios into the windows messaging queue... If you know of a way to do that... :P
Thanks for the suggestion though!

---

