---
title: "Tripwire emails"
date: 2010-11-29
forum: Security
---

### Post by Axolotl9250 on 2010-11-29
Hi All, I'm trying to get Tripwire set up so as it sends me reports every day via email, I've been doing this with the following command:

sudo tripwire --check | mail ben -s "Tripwire Check" EMAIL ADDRESS HERE

but I don't get anything in my Inbox, I've tried several times, has anyone else gotten tripwire to do this? If so, how?

Thanks,
Ben.

---

### Post by cariboo on 2010-11-29
Do you have an email server setup? If so which one?

---

### Post by Axolotl9250 on 2010-11-30
My emails all powered by windows live mail, as that's the account I was given when I came to university. So I think I have pop3 for sending and smtp for receiving, if that's what you mean.

---

### Post by brian_p on 2010-11-30
> **Axolotl9250 said:**
> My emails all powered by windows live mail, as that's the account I was given when I came to university. So I think I have pop3 for sending and smtp for receiving, if that's what you mean.

No, he means do you have an smtp server installed on your machine. exim4 and postfix are popular ones.

Check:

```
sudo apt-get exim4 -s

sudo apt-get postfix -s

```

(A small correction: pop3 is for collecting mail. smtp is for receiving and sending mail).

---

### Post by Axolotl9250 on 2010-11-30
I see, no I don't think I have either of those, but I'm installing postfix now. I'm afraid I'm not very up and knowledgeable with mail setups and such, other than webmail. I did once have Mutt with getmail, procmail, and sendmail, on Arch, but I blindly followed a HOWTO and I don't recall explicitly installing a mail server, unless one of the above mentioned was it, or it came as a dependency with something.

---

### Post by OpSecShellshock on 2010-11-30
Don't forget to re-do your tripwire baseline after installing the mail server.

---

