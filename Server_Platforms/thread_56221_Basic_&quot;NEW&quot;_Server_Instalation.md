---
title: "Basic &quot;NEW&quot; Server Instalation"
date: 2005-08-11
forum: Server Platforms
---

### Post by Rodrigo on 2005-08-11
Hi to all, I was just wandering: 
What do you, as a server admin, install or uninstall to setup a webserver (or any other) before you feel comfortable with it?

The basics I do are (for a web server):
Server Expert installation (with ubuntu of course)
(add the proper reppos)
remove some stuff (sound, floppy utils)
add new kernel (acordin to the processor)
install apache2, php4, mysql4.1
install a php accelerator -> [http://www.php-accelerator.co.uk/download.php](http://www.php-accelerator.co.uk/download.php)
change the /home path to /var/www (for all users but root)
setup some basic cron scripts (auto update, auto save repos and .deb packs, rotate logs, etc...)
setup a firewall
make my ssh account
and bless it with holy water hehe.

what are your "basics"?

---

### Post by bjweeks on 2005-08-12
That is like what I do but you have some cool ideas in there. You learn something new ever day. :)

---

### Post by LordHunter317 on 2005-08-12
[QUOTE=Rodrigo]change the /home path to /var/www (for all users but root)[/quote]Wait, why?  If I undestand what you're saying, this is a really bad idea.


> setup some basic cron scripts (auto update, auto save repos and .deb packs, rotate logs, etc...)You'll have to be more detailed, but some of this stuff sounds like it shouldn't be automated, or is already done for you. 

> setup a firewallIf all it's running is Apache, this is likely unnecessary.

---

