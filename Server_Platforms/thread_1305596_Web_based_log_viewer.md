---
title: "Web based log viewer?"
date: 2009-10-30
forum: Server Platforms
---

### Post by SirGe on 2009-10-30
I am looking for a simple web-based log viewer, something with equivalent functionality of gnome log viewer applet. 

Primary purpose is to be able to insert links with pointers to 'interesting' log locations into emails from monitoring tools.

This was asked before in [[COLOR="Magenta"]we based log viewer[/COLOR]]("http://ubuntuforums.org/showthread.php?t=512919&highlight=log+viewer+web") (sic), but never got an answer and got archived.

---

### Post by Lars Noodén on 2009-10-30
Cacti would be my first thought:
[http://www.cacti.net/what_is_cacti.php](http://www.cacti.net/what_is_cacti.php)

---

### Post by samosamo on 2009-10-31
syslog-ng, with the php-syslog-ng front end.  Cacti has a plugin to integrate this front end as well.

---

### Post by SirGe on 2009-10-31
Thanks for the suggestions. Cacti sounds wonderful and syslog-ng seems like the right way to go for any serious logging.

In my case, though, the need is too casual to make a significant investment into re-organizing logging or setting up a cacti infrastructure. Just need to get some _existing_ text bits out through Apache to a browser...

In detail, the original request was to e-mail any exceptions from a Tomcat server to a support list. As there were several other monitoring needs at the same time, I went top-heavy (in my opinion) and installed/configured Nagios. The log_check plugin in Nagios is old and weak and the contrib/log_check2.pl is not working well (crashes with embedded perl) and is not providing enough info about the exception.

I think what is needed is a new plugin and a (wider-purpose) log viewer. The log viewer should have the capability of being handed a 'bookmark' to display. The plugin, of course, should be able to generate the bookmark as an option. That way a notification can contain both a short summary and a link to the actual place in the relevant log. 

Time to hit the code :)

---

### Post by PixelDJ on 2009-11-01
I don't know if this is the best solution for you or not with the e-mail situation, but I use Webmin for looking at my logs when I don't want to go digging through my log files via SSH. It runs on port 10000 usually and you can do many web based administrative tasks. Maybe it will help you for something.

[http://www.webmin.com/](http://www.webmin.com/)

Sorry if it's not what you're looking for, or if you already use it but I find it useful. ;)

---

### Post by mbaas on 2009-11-01
You could also see if [Ossec]("http://www.ossec.net/") + Ossec WUI would do. You could probably disable everything but the logcheck daemon.

---

### Post by rgerhards on 2009-11-02
I suggest you also have a look at [http://www.phplogcon.org](http://www.phplogcon.org) - it can directly work with text files. While it is developed as a syslog viewer, this capability provides flexibility to work decently OK with other files as well.

There is a demo available at [http://demo.phplogcon.org](http://demo.phplogcon.org)

---

