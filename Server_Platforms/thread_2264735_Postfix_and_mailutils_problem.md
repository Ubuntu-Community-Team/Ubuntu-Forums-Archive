---
title: "Postfix and mailutils problem"
date: 2015-02-09
forum: Server Platforms
---

### Post by niccolo.ferrari on 2015-02-09
I set up postfix (I can receive and send mail, they are stored in  /root/Maildir/ for root user), but now when I try to read mail he say  that there are no mail for root (ith mail command). I tried to read  /var/mail/root and it was empty, why?

---

### Post by TheFu on 2015-02-09
If there isn't any mail, there isn't any mail to be read. Is this a trick question?

Most of the time, email in the "inbox" is left under /var/spool/mail/ somewhere. Only when a client mailreader grabs the email and moves it under ~/maildir/ <-- whatever that is - does mail get moved. Different mail readers will move the email to different places.

BTW, it would be smart to forward all root email using the /etc/aliases file to a normal user account. A few other accounts like postmaster should also be forwarded.  Don't forget to run newaliases after modifying that file.

---

### Post by niccolo.ferrari on 2015-02-10
No the problem is another: I set up a Maildir and $MAIL was configured to point at a mailbox and not a Maildir. I solved this setting MAIL=$HOME/Maildir

---

