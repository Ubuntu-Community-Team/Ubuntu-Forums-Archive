---
title: "Creating a server for my website"
date: 2007-04-05
forum: Server Platforms
---

### Post by neverett on 2007-04-05
I have installed XAMPP on my laptop, and it works perfectly.  I can host my own website and point my domain to it.  I'm just wondering if I can create an email server so i can create as many email addresses as I want (i.e. - user@domain.com).  I'm not too sure how to go about this, and was wondering if anyone could lend some advice.  Thanks in advance for everything! -- NE

---

### Post by Brazen on 2007-04-05
Look into Postfix.  There is some good, easy documentation on it here: [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html)

---

### Post by Brazen on 2007-04-17
For webmail, any easy tack-on to Postfix would be squirrelmail.

If you want a more full-featured "groupware" solution, than you should checkout eGroupware.  eGroupware has webmail in addition to calendars, task list, contacts, and a ton of other features.  However, with great power comes great configuration.  eGroupware will be considerably harder to get set up.

---

