---
title: "egroupware"
date: 2007-04-06
forum: Server Platforms
---

### Post by wallcrawler78 on 2007-04-06
I used the repos to install egroupware.  But it installed it in /usr/share/egroupware instead of in /var/www.  how do i launch the setup and configuraiton program.  I can only see my test page that loads in apache.  Since the files are not in the www directory i can not navigate to any of the .php files from a webbrowser.

I tired using symbolic links, but that doest want to take  it ends up saying something about not found... arghhh... help!

Thanks!
Danny

---

### Post by elst on 2007-04-07
Take a look in /etc/apache2/sites-available/. If there isn't anything there for egroupware, then add a virtual host config, and use /usr/sbin/a2ensite to enable it. IIRC, Ubuntu enables virtual hosts for Apache by default, and it's better to work with that rather than alter the default Web site.

---

### Post by jaheds on 2007-04-07
Before you move things aroung, try going to [http://localhost/egroupware](http://localhost/egroupware)

Of course, replace "localhost" with your machine's IP address if you're not browsing on the same machine as your apache web-server.

Are you using Apache2?  If so, apt packages put their configurations in /etc/apache2/conf.d/

Good luck

---

