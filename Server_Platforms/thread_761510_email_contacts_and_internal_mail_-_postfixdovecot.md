---
title: "email contacts and internal mail - postfix/dovecot"
date: 2008-04-21
forum: Server Platforms
---

### Post by beaker15 on 2008-04-21
[FONT="Lucida Sans Unicode"]Hi

I'm setting up a mail server (called SERVER1) on Feisty using Postfix and Dovecot, which send and receive mail fine. On my clients I'm using Thunderbird. Basically, I want to be able to send an internal email from thunderbird just using the username of the person its going to. I can do this using webmin if i go to the postfix server mailboxes and send a message. From thunderbird it works if i type 'user@SERVER1' but it'd be better if i could just type 'user'.
Also eventually I want to have a contacts list of internal users for the network users to choose from when sending to them. How can i do this?  Is it done with postfix or dovecot? or even sugarcrm, which i also use  [/FONT]

thanks

---

### Post by beaker15 on 2008-04-23
should i be looking in postfix or dovecot to fix this?

---

### Post by beaker15 on 2008-04-25
ok i fixed this, it was my mistake. I had made a couple of changes to the postfix config (myhostname & mydestination), which i'd forgotten to amend in thunderbirds settings.

As for contacts,i decided to make an address book in thunderbird, export it as a CSV file to the server, then Import it to the other machines from there. 

ta

---

