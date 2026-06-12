---
title: "How to manage packaged web applications?"
date: 2010-04-27
forum: Server Platforms
---

### Post by Jive Turkey on 2010-04-27
The ubuntu repositories have a number of packaged versions of popular web applications, ie drupa, wordpress, and so on.  When they are installed by this method (usually using appache to seve them up) it isn't really obvious to me how to make apache load/unload the app since it doesn't use the sites-available/sites-enabled configuration.

In my case I'm fighting with rtgui, installed from the repos, which I have gotten to work nicely with SSL and htdigest authentication, but I can't get apache to stop serving the site when I don't want it up.  I'm experimenting with other stuff that uses ssl and I don't want any conflicts.

Please don't suggest "sudo a2dissite blah" as I have already stated the packaged web apps don't conform to that setup, they are set up in some other mysterious way.

Please share any insight on this, please!?

---

### Post by Jive Turkey on 2010-04-27
I figured it out, the installer or something puts a symlink in /etc/apache2/conf.d/<relative link to apache.conf> 

I was able to delete the link and copy the apache.conf to sites-available and now I can manage it using the a2ensite/a2dissite commands, yay!

now, what was I doing in the first place that I needed that handled for?....

---

### Post by Ilalmi on 2010-04-27
Hi,

```
dpkg -L package
``` shows all files that have been installed by your package. This way you should be able to find out how the package interacts with your apache configuration.

Hope that gets you any further.

---

### Post by Jive Turkey on 2010-04-28
That's a great tip thanks!

---

