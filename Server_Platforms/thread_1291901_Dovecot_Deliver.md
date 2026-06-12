---
title: "Dovecot Deliver"
date: 2009-10-15
forum: Server Platforms
---

### Post by Musicalgibbon on 2009-10-15
Hi all,

I've got an email server running Dovecot, Squirrelmail, Postfix, Getmail.

I'm having trouble with Dovecot's deliver function not being allowed access to 
*var/run/dovecot/auth-master*, or indeed such a folder existing at all. 

I've set up Getmail to pass mails to Deliver, which it seems to be doing fine, but (if I am to understand correctly) Deliver is having trouble looking up the virtual user database (which it is supposed to do through *var/run/dovecot/auth-master*).

The folder currently doesn't exist.
If I create one it says that it's permission is denied.
If I chown the permissions to allow it access is says connection refused
I'm not sure how I am supposed to allow deliver access, or indeed what is supposed to be in there.

I really am at a loss, so close to having a functioning mail server. Any help would be *really* appreciated.

---

### Post by yknivag on 2009-10-15
How have you configured dovecot to determine the users?

I did this (though I was using fetchmail-dovecot-squirrelmail and postfix).  Dovecot has several options as to how it is to determine who it can deliver to, it has a built in system, or it can assume that users with an account on the machine are valid (and also use their password) or it can use a database (mysql etc).  I chose to use the "pam" auth which relies on each mail user having a system account and dovecot simply worked no further config.

I'm guessing that you've chosen to use a different authentication route in order for it to be looking there.

---

