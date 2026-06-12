---
title: "Postfix - stop all users from getting mailbox?"
date: 2011-03-13
forum: Server Platforms
---

### Post by Zeon100 on 2011-03-13
Hey guys,
I'm just getting started with postfix for the first time (using courier pop) and everything is working well. However I can't seem to figure out how to only allow some system users to have mailboxes?

For example I have a few accounts which are FTP only accounts but they still have mailboxes under postfix? Is there any way to tell postfix the accounts that I actually want mailboxes for?

Also on a side note, I notice that mail seems to be stored under the user's home directory. Is this a good idea? I'm scared they may accidentally delete them.

---

### Post by HermanAB on 2011-03-14
Well, that is how Postfix works. If you don't want to use system accounts for your mail server, then you got to use a better mail server that stores all things in a database, such as Citadel. [http://citadel.org](http://citadel.org)

---

### Post by SeijiSensei on 2011-03-14
Create aliases in /etc/aliases for the accounts you wish to disable.  Point them to /dev/null.

---

### Post by Demented ZA on 2011-03-14
> **SeijiSensei said:**
> Create aliases in /etc/aliases for the accounts you wish to disable.  Point them to /dev/null.

I could be wrong, but doesn't he have to run
```
sudo postaliases /etc/aliases
```
after modifying the /etc/aliases file for postfix to hash the file again?

---

### Post by SeijiSensei on 2011-03-14
Probably.  I wasn't intent on giving details.  Anyone administering a mail server needs to learn about how aliasing works, and it's not like it isn't amply documented how to do so.

---

### Post by lisati on 2011-03-14
Another option which comes to mind is Postfix's [check_recipient_access]("http://www.postfix.org/postconf.5.html#check_recipient_access") option. It won't actually disable the mailbox directory in the user's home folder, but it can be used to block incoming mail for a list of users.

The way I'd use it would be to create a file, in this example named **/etc/postfix/recipient_check** (it's possible to add a custom rejection message after the word "REJECT"):
```

user1@mydomain.com REJECT
user2@mydomain.com REJECT
user3@mydomain.com REJECT

```
After saving the file, I'd run:
```
sudo postmap /etc/postfix/recipient_check
```
Then I'd add to the smtpd_recipient_restrictions entry in Postfix's main.cf file:
```

check_recipient_access hash:/etc/postfix/recipient_access

```
All that would be left would be to restart/reload postfix and we're away.

---

