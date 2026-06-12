---
title: "email server"
date: 2010-06-02
forum: Server Platforms
---

### Post by captsisko on 2010-06-02
Hi,

I'm a bit of a newbie and I'm about to begin configuring an email server.

But , I thought I'd begin by checking if an email server already comes by default with my VPS.

Can anyone tell me what command(s) I might use to check what email server(s) may already be installed, please?

---

### Post by Bachstelze on 2010-06-02
"Email server" can mean a couple different things. What do you want to do, exactly?

---

### Post by dudumomo on 2010-06-03
I'm afraid you will need to install everything. 
Depending on your needs, there are several different possibilities.

In my case, I have used Postfix + Procmail + Spamassassin etc... with the web interface Roundcube.
(I even wrote a tutorial, just check my signature)

---

### Post by HermanAB on 2010-06-03
You can go the Lego route and install Postfix, Dovecot, Apache, Roundcube, yadda yadda...

or you can install Citadel:
[http://citadel.org](http://citadel.org)

It takes about 20 minutes to run the Citadel Easy Install script and it does everything.

---

