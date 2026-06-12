---
title: "Distribution addresses in Postfix"
date: 2011-08-29
forum: Server Platforms
---

### Post by lazloman on 2011-08-29
I want to create a distribution address that will send mail to internal and external addresses. Something like this:
[email]group@local.com[/email] -> [email]me@local.com[/email] [email]me@external.com[/email]

Ive gone through the docs and found one working solution, but sub optimal. I can create a local account for "group", and then use it's .forward to send mail, but it seems a bit silly that I need to create an otherwise useless account to do this.

/etc/alias - This only allows for local address, so I can't send to external.com (or can I?)

/etc/postfix/virtual - Can't seem to get this to send to an external address. I configured it this way:
/etc/postfix/virtual
    [email]group@local.com[/email] [email]me@local,me@external.com[/email]

sudo postmap /etc/postfix/virtual
sudo service postfix stop/start

When sending email, I get an undeliverable message back and I find this in the logs:
"User unknown in virtual alias table"

Please help

---

### Post by SeijiSensei on 2011-08-30
Edit /etc/aliases (as root with sudo) and add this entry:

```
group:     me, me@example.com
```

Then run "sudo newaliases" to update the database.  Now mail to "group" will be delivered to both your local and remote mailboxes.  The only catch is if your ISP blocks outbound SMTP over port 25.  If so, you won't be able to send to external addresses.

---

### Post by lazloman on 2011-08-31
Thanks for the reply, but the mail to the external address gets bounced by Postfix with message "User unknown in virtual alias table". Mail to the local address is delivered.

---

### Post by lazloman on 2011-08-31
I think I've finally figured it out. I had to place both my local and external addresses into the /etc/postfix/virtual file, run postmap against it and reload postfix. The /etc/aliases file is for local delivery only.

---

