---
title: "mailx and postfix packages fail at sending email"
date: 2009-07-21
forum: Server Platforms
---

### Post by Jago6060 on 2009-07-21
I'm trying to send an email via command line and have had no luck.  I have mailx and postfix installed and upgraded.  My command is as follows...

```
mail [*email prefix*]@gmail.com 
```Which prompts for a subject...

```
Subject: test
.
EOT
```

And I never receive the email...Any thoughts?  I really need to get this working.

---

### Post by grantemsley on 2009-07-21
Jago, why would you start a new thread for this?

There are tons of reasons why it might not work...you'll have to tell us a bit more about how it is setup, and how your network is configured.

---

### Post by Jago6060 on 2009-07-21
--I apologize for the slack in description.  I'm very tired so descriptiveness is not my forte this morning.  I started the new thread because I tend to get better results by asking users with experience than trying to decode the variables scattered in a HowTo.  Unless someone has a descriptive HowTo they could direct me towards.

--I'm running Ubuntu Server 9.04, mailx and postfix packages.  I'm running on a private network with outside access.  Static IP.  I think that's everything pertinent to this problem...

---

### Post by Jago6060 on 2009-07-21
SOLVED: I don't know what the issue was, but I just re-ran the setup for postfix and now everything is working...I think I may need the day off...

---

