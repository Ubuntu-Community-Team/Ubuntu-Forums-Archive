---
title: "Fetchmail Multiple Emails + Round Cube"
date: 2007-11-02
forum: Server Platforms
---

### Post by passbe on 2007-11-02
After searching google / these fourms all day, i have still got no further in my desired setup.

Fetchmail getting 4 pop3 account emails and dumping them into an IMAP server, in which my roundcube installation can interact with. 

im currently battling with fetchmail to try and connect to gmail to grab the emails.

my fetchmailrc is as follows:

```

set no bouncemail
set postermaster <username>

poll pop.gmail.com with proto POP3 port 110 timeout 120 user 'passbe@gmail.com' there with password 'a secret' is passbe here keep

```

i know there is something simple i am missing. any help would be greatly appreciated.

passbe

---

### Post by JasonRivers on 2007-11-02
I might be wrong on this, but:

I'm pretty sure Gmail doesn't accept requests on port 110, and I think it uses SSL to communicate on port 995, this COULD be your issue, I don't know if gmail has an open port that does not use SSL, but if you can setup Fetchmail to accept Gmails certificate then this would be the route I would choose.

Jason.

---

### Post by passbe on 2007-11-02
ok brilliant that was a silly mistake. ive configured fetchmail for one of the other accounts through port 110 and its working. 

how do i setup an imap server to put that email into. I'm assuming procmail or another MTA MDA ?

---

### Post by JasonRivers on 2007-11-02
I use Postfix for SMTP and Dovecot for IMAP/POP3

setting it up is fairly straightforward, have a look at Webmin for configuration if you have no Gui: [www.webmin.com](www.webmin.com) and also Usermin will configure Fetchmail for each user account too, as I pick up mail from 4 different places at the office, I use Fetchmail to pick up from those 4, and place into my POP3 / IMAP box, then I pickup through Dovecot so my workstation only picks up from one place. not sure I'll be of much more help than that, as it was quite some time ago, but this helped with setting things up:[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

and then my old friend Google for Dovecot setup.

/J

---

### Post by passbe on 2007-11-03
that helped a lot thank you. I believe i now have fetchmail and dovecot working properly and roundcube looking at dovecot. How do i set fetchmail to deliver the emails to the Maildir that dovecot uses ?

---

