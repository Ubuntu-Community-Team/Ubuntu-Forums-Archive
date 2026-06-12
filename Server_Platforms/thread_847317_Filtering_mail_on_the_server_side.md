---
title: "Filtering mail on the server side"
date: 2008-07-02
forum: Server Platforms
---

### Post by defaulk on 2008-07-02
Hey,
I operate my own home server and have several computers.  I'd like to check mail from them all so IMAP seemed the obvious choice.  Now I've been using postfix + courier IMAP on the server for a little over a year.

It works ok except I have to set up a bunch of filters every time I set up a new computer or set up a new mail client.  It seems much more sensible to have these filters applied on the server.  Any suggestions on a good way of doing that?  Should I be using procmail?  Should I abandon IMAP for something better?

If procmail, how do I set that up initially?  Any howto's I can be pointed to that will show me how to set that up with postfix?

Thanks

---

### Post by HalPomeranz on 2008-07-02
Yes, you should use procmail for this.  You can configure it to run out of a .forward file in your home directory, so you don't have to deke around with your MTA configuration (and besides, it will keep working even if you decide to switch MTAs).  Activate procmail simply by creating a ~/.forward file that looks like this:

```

"|/usr/bin/procmail -f-"

```

Before you do that, however, you will need to set up your filtering recipes in ~/.procmailrc.  There's lots of How-Tos available-- I just Google-d for "procmail how-to" and got tons of useful hits.

---

