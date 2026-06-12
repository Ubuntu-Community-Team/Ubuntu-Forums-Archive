---
title: "Postfix - Says &quot;no mail&quot; problem"
date: 2010-12-06
forum: Server Platforms
---

### Post by alienprdkt on 2010-12-06
ok I have installed and configured postfix to setup a mail directory to $HOME/Maildir

when I check ls Maildir/new there is mail there but when I run the command it outputs "No Mail"?

Anyone know how to fix this?

Thanks in advance,
Joe

---

### Post by alienprdkt on 2010-12-06
bump some has to know how to fix this..

---

### Post by alienprdkt on 2010-12-07
> **alienprdkt said:**
> bump some has to know how to fix this..

Would it help to know that I followed this:

[https://help.ubuntu.com/community/Postfix ]("https://help.ubuntu.com/community/Postfix")

Where it states:
Now is a good time to decide which mailbox format you want to use. By default Postifx will use mbox for the mailbox format. Rather than editing the configuration file directly, you can use the postconf command to configure all postfix parameters. The configuration parameters will be stored in /etc/postfix/main.cf file. Later if you wish to re-configure a particular parameter, you can either run the command or change it manually in the file.

To configure the mailbox format for Maildir:

sudo postconf -e 'home_mailbox = Maildir/'

I have mail there but running the command mail, outputs no mail

HOw do I go about fixing this?

---

### Post by SeijiSensei on 2010-12-07
Install dovecot.  It provides POP3 and IMAP services.

---

### Post by alienprdkt on 2010-12-07
> **SeijiSensei said:**
> Install dovecot.  It provides POP3 and IMAP services.

thanks but still wont fix my problem.

---

### Post by alienprdkt on 2010-12-10
ok so i need an imap to recieve, postfix only sends?

is this correct?

I remember setting at work so i sent it to my gmail. hmmm I guess with an imap i could send email from google to mysite.dyndns.org site? would this be correct?

---

### Post by SeijiSensei on 2010-12-11
Postfix is a "mail transfer agent."  It takes messages and delivers them to either a local account or a remote server.  How you access the account is handled by other software, usually an IMAP/POP server.  That's why I suggested installing dovecot, which plays this role.  You can then use standard clients like Thunderbird, Evolution, or Outlook to access your inbox and manage your folders.

---

### Post by alienprdkt on 2010-12-13
Thanks I guess I will try setting that up this week.

---

