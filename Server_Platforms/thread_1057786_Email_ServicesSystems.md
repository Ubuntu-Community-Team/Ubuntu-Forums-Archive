---
title: "Email Services/Systems"
date: 2009-02-02
forum: Server Platforms
---

### Post by kchakrak on 2009-02-02
I'm trying to get an email system working (more for R&D than production use) and I would like some suggestions/opinions on what servers/services to use. I'm using 8.04LTS Server with the Gnome-Core GUI, as lightweight as possible.

So far I have looked at a postfix > dovecot > egroupware scenario but I cannot get this working correctly. I have also seen Exim, Courier and a few others dotted about but am not sure what to try next. I like Egroupware as is seems to be a sold groupware solution (and we already have a few implementations of it by the previous engineer).

Any opinions, suggestions from anyone who's had experience with email systems, especially from anyone who has spent time with Egroupware?

Much appreciated.

---

### Post by HermanAB on 2009-02-02
The easiest mail system to install is Citadel:
[http://www.citadel.org](http://www.citadel.org)

Run the Easy Install script from the download page.  It takes about 20 minutes and then everything works.

Cheers,

Herman

---

### Post by kchakrak on 2009-02-04
Thanks, I'll have a look into that. All opinions still welcome.

---

### Post by mechanic on 2009-02-04
This may help setting up such a system.
[http://home.in.tum.de/~baueran/techdoc/postfix.html](http://home.in.tum.de/~baueran/techdoc/postfix.html)
When I did a similar thing I just installed the imapd server, then fetchmail and some spam filter or other. Use any client to interrogate the IMAP files in <somewhere>/mail

mechanic

---

