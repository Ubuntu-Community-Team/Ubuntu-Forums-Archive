---
title: "Postfix - Dovecote package auto configure?"
date: 2011-01-30
forum: Server Platforms
---

### Post by thesti on 2011-01-30
Hello,

I am trying to setup a mail server with postfix in ubuntu server 10.04. I follow the tutorial in [this]("https://help.ubuntu.com/10.04/serverguide/C/postfix.html").

I've installed postfix and dovecot and went through the configuration, then I install dovecot-postfix package. 

From what I get, dovecot-postfix package will configure postfix authentication for us. So then I expect to get the "250-AUTH LOGIN PLAIN" output when issuing the ehlo command at postfix. But I didn't see that...

Is there any step that I'm missing?

Thank you.

---

### Post by Vegan on 2011-01-30
IBM has an excellent manual for postfix

---

### Post by HermanAB on 2011-01-30
Howdy,

If you want a mail server that is trivially easy to set up and manage, install Citadel.  It takes about 20 minutes and it does everything.

---

### Post by elico on 2011-01-30
the question is: what have you done wrong? or... what is written unclearly on the tutorial?

or somethings else.

try this manual...
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

it's much more understandble then the one that you have been using
And that is because you can understand why something wont go or will go wrong.
hope it will be good for you.

---

### Post by druhboruch on 2011-01-30
You may also install mail-stack-delivery package.
It will setup and configure dovecot and postfix for you.

---

### Post by thesti on 2011-02-01
Hello,

Thanks for all of the replies. Well, after some more hours spent to configure postfix, I've managed to send an email from a local user to another. I followed the tutorial given by Elico [here.]("https://help.ubuntu.com/community/Po...asicSetupHowto")

All I do is install postfix on a new server (no postfix installation has been done before), and have a DNS which has an mx record that point to the postfix server.

I think the next think to do is to have SASL authentication, LDAP addressbook and authentication integration, and the ability to send mail to another mail server (on the Internet perhaps...), spam & antivirus filtering... Is there any other critical configuration that I miss?

But, again I'm stuck when I was trying to install courier-pop and courier-imap, when I issue the command

```

sudo apt-get install courier-pop

```

It says "couldn't find package courier-pop". Strange...

---

### Post by thesti on 2011-02-03
Ah, I finally made it. I do "apt-get update" then the courier packages could be installed. I've tried postfix installation and it could send messages even to my yahoo mail account.

Thank you for your help!

---

### Post by des2013 on 2013-02-13
> **HermanAB said:**
> Howdy,

If you want a mail server that is trivially easy to set up and manage, install Citadel.  It takes about 20 minutes and it does everything.

I respectfully disagree. Citadel, IMHO, is not a mail server. It is chat room software that happens to include aspects of a mailserver. The "Easy Install" runs easily, but does not complete the installation. Once running, you discover a weird chat room configuration layout that provides no obvious way to even create a mailbox.  It might be great as BBS or chat software, but it is not a substitute or easy path to a postfix/dovecot mailserver setup.

---

### Post by lisati on 2013-02-13
The suggestion to check out Citadel is appreciated, even though this thread wants to go back to sleep.

Old thread closed.

---

