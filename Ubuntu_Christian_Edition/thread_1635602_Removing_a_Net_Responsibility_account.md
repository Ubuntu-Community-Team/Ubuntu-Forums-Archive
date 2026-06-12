---
title: "Removing a Net Responsibility account"
date: 2010-12-02
forum: Ubuntu Christian Edition
---

### Post by Cityscape on 2010-12-02
Hi. We were configuring Net Responsibility today and put in a wrong username/password.

So when we put in our correct username/password we got this error:
> 
/usr/local/bin/net-responsibility-config-cli:114:in `initialize': ERROR (RuntimeError)
Another account have already been set up on your computer. Please delete that account before you use this one.
	from /usr/local/bin/net-responsibility-config-cli:132:in `new'
	from /usr/local/bin/net-responsibility-config-cli:132

How can we remove this account that has been set up so we can setup the proper account?

---

### Post by Consecrated on 2011-03-12
Bump!!! Same issue. And when I try to generate a report with whatever account was previously set up on this computer, it says:

Downloading the configurationfile...
/usr/share/net-responsibility/lib/server_connection.rb:38:in `get_config':  (RuntimeError)
ERROR
Couldn't find no user with your username -  - on the server. Please visit [www.netresponsibility.com](www.netresponsibility.com) to register.

---

