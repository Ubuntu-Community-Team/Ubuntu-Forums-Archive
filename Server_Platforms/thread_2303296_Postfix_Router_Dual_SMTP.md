---
title: "Postfix Router Dual SMTP"
date: 2015-11-17
forum: Server Platforms
---

### Post by Alex_Reid on 2015-11-17
I am migrating from GroupWise to Google Apps and before I completely change to Google I'd like to use both servers.

This is what I am thinking:


[LIST=1]
[*]Both GroupWise and Google Apps have users inserted with same email addresses
[*]Change MX to point to Postfix server so that all mail goes here
[*]Mail is then sent to both SMTP servers so that both have a duplicate of the email
[*]When I am ready to completely move to Google Apps, point MX to Google and I won't need GroupWise or Postfix
[/LIST]

I could also forward the message to the temporary google address with the same username as long as the original email still went to GroupWise. 

I haven't been able to find any good resources on accomplishing this with two SMTP servers and I am not exactly sure what to call it so I can search for it.

Any help or direction will be much appreciated. 

Thank you!

---

### Post by smtp on 2015-11-19
What do you mean by "I'd like to use both servers."?

---

