---
title: "Dovecot"
date: 2007-11-05
forum: Server Platforms
---

### Post by mode87 on 2007-11-05
hi i installed dovecot on my computer and i am able to login with telnet however when i do the stat command it shows that i have no emails. i put an mbox file in /var/mail/<user> and i am pretty sure that my config file points to that location but still no go. what could be the problem?

---

### Post by HermanAB on 2007-11-05
Errrm... I used Dovecot some time ago but doesn't have anything runing at present so I cannot check for you.  However, I believe that Dovecot uses maildir format only.  I don't think that it can do mbox.

---

### Post by mode87 on 2007-11-05
it can, it says so in the documentation. however when i set it up like the documentation says i still get the same problem.

---

### Post by HermanAB on 2007-11-05
Well, maildir worked for me...

You can easily convert mailboxes to maildirs with formail, which is in the fetchmail package.

---

### Post by MJN on 2007-11-05
Is there mail in the mbox?

Is there a reason you want to use mbox as opposed to maildir? I'd go with the latter unless you have specific reasons not to.

If there is mail in the mbox, but Dovecot is not seeing it, post your config and we can take a look (just post the section's you've changed if you'd prefer as the default Dovecot config is pretty lengthy).

Mathew

---

### Post by mode87 on 2007-11-05
mail_location: mbox:~/mail:INBOX=/var/mail/%u

now that should work, but it does not. what i am trying to do is pull mail from hotmail to a file on my computer then host it on a pop3 server so that the gmail fetcher can pick it up. but after some research i am finding that the gmail fetcher does not play nice with dovecot so are there any alternatives?

---

### Post by MJN on 2007-11-05
Is there any mail though in the mbox? If there isn't Dovecot isn't going to see it.

The Fetchmail package HermanAB mentioned may be an alternative solution to explore, but then I can't see how something like this can't be compatibile with Dovecot - why does it utilise Dovecot at all as opposed to writing directly to the mailbox?

Mathew

---

### Post by mode87 on 2007-11-05
yes the mbox has mail in it, i am reading off it with thunderbird. and the way the gmail fetcher works is through pop3, since hotmail does not have a free pop3 server i am trying to use an alternative method.

---

### Post by mode87 on 2007-11-05
i was jut looking at fetchmail but i do not think that would work because it forwards the mail and i think that would loose the timestamps on the mail as well as the sender.

---

### Post by MJN on 2007-11-06
How is Thunderbird accessing the mail? Or is it just accessing the local mbox directly (i.e. via the file system as opposed to a POP/IMAP server)?
 
I don't have personal experience of Fetchmail but I was always under the impression it could download mail from multiple remote mailboxes and drop them in to local mailboxes (as opposed to forwarding them per se). I don't know what this assumption was based on so it could be very wrong.
 
Mathew

---

