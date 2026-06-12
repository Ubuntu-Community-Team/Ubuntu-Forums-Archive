---
title: "Thunderbird Not Playing Nice with Mail Server"
date: 2018-02-22
forum: Server Platforms
---

### Post by rduhb on 2018-02-22
Mail server setup complete.  Postfix and Dovecot configured and running.  I can telnet to port 110, 465, 587, 143, 993, 995.
But for some reason the authentication fails when setting up an account in Thunderbird.  It connects to the server but it says the password is incorrect.  Outlook doesn't work either.  I have been troubleshooting for a few days and I can't figure this out.  Has anyone had a similar problem and how did you solve it?

---

### Post by #&amp;thj^% on 2018-02-22
I know this sounds very silly, But it has happened to me.
1.Check that Cap Locks is set right.
2.Check the settings in the Email's or Gmail's web page to see that the settings there are correct and allow you login with the same password.
3.There are times when Gmail (If using Gmail) flags a new login as suspicious and requires confirmation from a device already logged in.
4.Again this pertains to Gmail, Make you can use what they call less secure applications to receive and send mail.
Forgot to mention: If you run a personal firewall make sure Thunderbird isn't blocked.

---

### Post by rduhb on 2018-02-22
> **1fallen said:**
> I know this sounds very silly, But it has happened to me.
1.Check that Cap Locks is set right.
2.Check the settings in the Email's or Gmail's web page to see that the settings there are correct and allow you login with the same password.
3.There are times when Gmail (If using Gmail) flags a new login as suspicious and requires confirmation from a device already logged in.
4.Again this pertains to Gmail, Make you can use what they call less secure applications to receive and send mail.
Forgot to mention: If you run a personal firewall make sure Thunderbird isn't blocked.


Thanks for the feedback.  At this point, nothing is out of bounds. :)
I created a couple of test users on the server and I can send/receive email from the command line.  However, creating accounts in Thunderbird for those same users is not working.  I'm new at this, but my understanding is that I can create accounts in Thunderbird or Outlook for users on my server.  It's got to be something simple I'm overlooking or not understanding.

---

### Post by #&amp;thj^% on 2018-02-22
> **rduhb said:**
> Thanks for the feedback.  At this point, nothing is out of bounds. :)
I created a couple of test users on the server and I can send/receive email from the command line.  However, creating accounts in Thunderbird for those same users is not working.  I'm new at this, but my understanding is that I can create accounts in Thunderbird or Outlook for users on my server.  It's got to be something simple I'm overlooking or not understanding.
Linux and Easy are like Vinegar and Oil. :D
Well it Sounds like possibly your postfix is not properly setup. Here is a [TUTORIAL]("https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04") on how to do it.

Also once you have postfix properly setup you will need to install and **IMAP/POP3 email server**, I also recommend Dovecot. Here is a [full tutorial]("https://www.digitalocean.com/community/tutorials/how-to-configure-a-mail-server-using-postfix-dovecot-mysql-and-spamassassin") on how to configure a mail server using postfix, and dovecot.
One last Question, Are you using Gmail here?

---

### Post by rduhb on 2018-02-22
> **1fallen said:**
> Linux and Easy are like Vinegar and Oil. :D
Well it Sounds like possibly your postfix is not properly setup. Here is a [TUTORIAL]("https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04") on how to do it.

Also once you have postfix properly setup you will need to install and **IMAP/POP3 email server**, I also recommend Dovecot. Here is a [full tutorial]("https://www.digitalocean.com/community/tutorials/how-to-configure-a-mail-server-using-postfix-dovecot-mysql-and-spamassassin") on how to configure a mail server using postfix, and dovecot.
One last Question, Are you using Gmail here?


Thanks again for your help.  I'll review the link and check Postfix again, (and again...and again)  LOL.  
And no, I'm not using Gmail.

---

