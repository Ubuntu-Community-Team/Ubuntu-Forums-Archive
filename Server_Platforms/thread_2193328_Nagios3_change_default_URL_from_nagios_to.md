---
title: "Nagios3: change default URL from /nagios to / ?"
date: 2013-12-12
forum: Server Platforms
---

### Post by michael_teter on 2013-12-12
Hello all.

I would like to change my ubuntu-packaged Nagios3 URL from [http://myhost/nagios3](http://myhost/nagios3) to [http://myhost](http://myhost) (on 12.04 LTS)

I've searched the web and followed a few different sets of instructions on how to do this, but I haven't achieved success.

Can anyone advise?

Thanks in advance.

---

### Post by newbie-user on 2013-12-12
Assuming you're using Apache, you can simply edit your default site in /etc/apache2/sites-available:

change
```
...
DocumentRoot /var/www
...
<Directory /var/www>

```
to
```
...
DocumentRoot /path/to/nagios
...
<Directory /path/to/nagios>

```
and then reload Apache.

---

### Post by nerdtron on 2013-12-12
Or if you are not hosting any other website on your server, assuming nagios is stored in /var/www/nagios, move all its contents to /var/www/. But I still suggest the above recommendation.

---

### Post by CharlesA on 2013-12-12
You can try messing with the alias but it might cause problems because of the way the cgi-scripts are called.

I just had the Nagios machine I set up at work direct the root to /nagios by adding:

```
RedirectMatch ^/$ /nagios
```

to the default site for Apache. I do have other virtualhosts set up on the server, but as it is an internal setup, that is a quick and dirty way to get it to redirect you automatically.

---

### Post by michael_teter on 2013-12-13
Thanks for the suggestions.

However, due to other circumstances, this effort is being put on hold.  Sorry to waste anyone's time!

---

