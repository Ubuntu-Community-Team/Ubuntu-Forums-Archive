---
title: "Problem with email"
date: 2013-01-10
forum: Server Platforms
---

### Post by imchivaa on 2013-01-10
Hi Ubuntu Forum,

I have a problem with my setup. I am using ubuntu server 12.10 with webmin installed. I run a phpbb forum version 3.0.11. My problem is with emails. When a user signup, i have set the setting to send an activation email to the person's email id but somehow it doesn't send out the email. I don't know how to setup the email server to send email out. Any solutions? :(

---

### Post by SeijiSensei on 2013-01-11
You need to be running a "mail transfer agent" like Postfix or sendmail on the server.  Try just using "[FONT="Courier New"]sudo apt-get install postfix[/FONT]" and see if it solves your problem.  For more details, read [https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html).

---

