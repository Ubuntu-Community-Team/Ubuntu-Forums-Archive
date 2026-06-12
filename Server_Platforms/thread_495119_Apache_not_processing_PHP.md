---
title: "Apache not processing PHP"
date: 2007-07-07
forum: Server Platforms
---

### Post by afbase on 2007-07-07
I just followed [The Perfect Setup - Ubuntu 6.10 Server (Edgy Eft) ]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4") on howtoforge.com

I also installed ISPConfig

Everything went without a hitch, with the exception that now apache2 doesn't process PHP!  

this is what is loaded in my "/etc/apache2/mods-enabled" folder
> cgi.load  include.load  php5.conf  php5.load  rewrite.load  ssl.conf  ssl.load  suexec.load  userdir.conf  userdir.load

So the modules are loaded to process php, but it still doesn't work.   Does anyone know how to get apache to process php again?

---

