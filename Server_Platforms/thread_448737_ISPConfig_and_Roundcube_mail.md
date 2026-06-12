---
title: "ISPConfig and Roundcube mail"
date: 2007-05-19
forum: Server Platforms
---

### Post by blmartin777 on 2007-05-19
I followed a nice how to on howtoforge to set up a server. I installed ISPConfig and Roundcube mail. I set up a website which is working fine. I then created a database in ISPConfig and created a email user for the website. If I go to the Roundcube mail login and type in the username and password it just sits there saying its loading and eventually the webscreen just goes blank and thats it. If I type in the wrong username and password it tells me login fails. I am not sure what is wrong or what I did wrong.

Any ideas?

---

### Post by mbradlcu on 2007-05-22
just to make sure I'm not totally of base,, roundcube is connecting to your mail server,, postfix? and if so, I would tail -f /var/log/mail.log and syslog and try and connect. sorry this isn't a giant help but maybe a start

---

### Post by nexxus07 on 2008-05-23
It helped me for sure. I had a similar problem and the logfile showed me that the Maildir for that particular user was not existant.

In ISPConfig this can be activated under Management - Server SEttings- email- Maildir (checkbox)
I read somewhere else that it will be created automatically once the first e-mail has been received (did not test ist though)

Thanx

---

