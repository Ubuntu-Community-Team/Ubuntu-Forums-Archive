---
title: "Ubuntu Apache Question"
date: 2009-10-08
forum: Server Platforms
---

### Post by julikaburger on 2009-10-08
Hi,

I am using a apache server under ubuntu in a vmware enviroment.
My chef created here some perl scripts with DBI and TKK usage.
If I change the perl scripts and template html files with eclipse nothing changes on this pages.
I checked the apache2 document root directory and everythings seems to be right but my changes 
are not shown in the web browser.
Of course I have restarted the apache2 server (/etc/init.d/apache2 restart).
I also stopped the apache2 server with /etc/init.d/apache2 stop but still the same web page are shown.
Of course I click on the reload button in mozilla firefox.
Now I have also renamed the start perl script file but still this start html page is shown in my browser.
I also restarted the ubuntu but nothing change. 
Can anyone help my, what could be the problem on this system?

Thanks for any help
best regards,

Julika Burger

---

### Post by t3r0 on 2009-10-08
> **julikaburger said:**
> 
I also stopped the apache2 server with /etc/init.d/apache2 stop but still the same web page are shown.

Are you on the right server? :D

If you stop apache you should see only a error when trying to load the webpage. 


- Tero

---

