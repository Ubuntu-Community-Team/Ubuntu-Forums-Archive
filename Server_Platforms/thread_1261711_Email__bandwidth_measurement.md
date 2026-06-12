---
title: "Email  bandwidth measurement"
date: 2009-09-09
forum: Server Platforms
---

### Post by HammerHed on 2009-09-09
I am looking for a way to monitor email bandwidth usage on my webserver, I host about 100 websites and get the total bandwidth but this is derived from the /var/log/httpd/access_log.

I am wanting to determine how much bandwidth is used by each virtual host including email.

Is this possible?

I have installed Cacti and this gives me total bandwidth at eth0 or lo but I cannot differentiate what is email or web.

Please help, I have Googled extensively on this and can find no answers.

---

### Post by zipperback on 2009-09-09
There are numerous ways to monitor your network bandwidth.
Have you taken a look into something like MRTG by any chance?

[http://freshmeat.net/projects/mrtg/](http://freshmeat.net/projects/mrtg/)


Depending on what kind of mail server you are running there are different configurations available for mrtg as well.

[http://lmgtfy.com/?q=mrtg+%2B+mail+server](http://lmgtfy.com/?q=mrtg+%2B+mail+server)

Hopefully this will help you.

- zipperback
:popcorn:

---

### Post by zipperback on 2009-09-09
For your individual virtual hosting domains you can setup apache log files for each of the domains and then just process those on a per domain level basis to determine the statistics for each domain.

Check this link.
[http://lmgtfy.com/?q=apache+log+files+on+a+per+virtual+domain+basis](http://lmgtfy.com/?q=apache+log+files+on+a+per+virtual+domain+basis)

- zipperback
:popcorn:

---

### Post by HammerHed on 2009-09-09
Thanks guys for you feedback, I will investigate these options.

---

