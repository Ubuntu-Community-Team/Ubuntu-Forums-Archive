---
title: "Problem Sending Mail with Squirrel Mail"
date: 2008-10-15
forum: Server Platforms
---

### Post by Black Mage on 2008-10-15
I have a postfix mail server set up and I am using SquirrelMail to send emails. The problem is when I send emails, the recipient recieves the return address which includes the name of the server it is on. For example, instead of the return address being [email]john@yahoo.com[/email], it will be [email]john@mymailserver.yahoo.com[/email].

Does anyone have any ideas how to fix this?

Thanks

---

### Post by MJN on 2008-10-15
The choice of sender name (and address) is the job of the client hence you should configure it in Squirrelmail (Options > Personal Information).

In your case it sounds like this isn't set and hence Postfix is adding a suffix itself because it cannot function without them. The default is to use $myorigin which itself defaults to $myhostname.

Mathew

---

