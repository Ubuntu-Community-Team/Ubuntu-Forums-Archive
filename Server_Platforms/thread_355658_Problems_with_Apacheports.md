---
title: "Problems with Apache/ports"
date: 2007-02-07
forum: Server Platforms
---

### Post by txmxmatt on 2007-02-07
OK, I lied. This is a two parter. First off, I have Apache2 installed, and did alot of googling for configuration and the likes. When I tried to start it up, I get the error
> (98 )Permission denied: make_sock: could not bind to address [::]:80
(98 )Permission denied: make sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
I found several answers to these problems, but none of them make sense.
Supposedly something is listening on port 80, but lsof -i:80 returns a bunch of apache2's even though apache isn't even started:confused:
If it's unable to open logs, that means you're not running the command as root. But I am:confused:
So any help on this front would be very welcome.

*sigh* Now part 2.
I changed the port number to 88 in the config file, and it worked. But when I tried to view a php file, it printed out the code...but I know php is installed because the phpinfo() works when I view it locally.

---

### Post by chalex on 2007-02-07
For the first part, what makes you think it's not started?  It's running, right?

/etc/init.d/apache2 {start|stop|status} or something like that should be the way to control it.

---

### Post by conjur3r on 2007-02-08
1. Try stopping apache and starting it.  After stopping, check if apache is really stopped by doing a ps...

2. You need to install php5.  After installation, restart apache for changes to take effect.

---

