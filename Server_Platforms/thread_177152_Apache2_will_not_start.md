---
title: "Apache2 will not start"
date: 2006-05-15
forum: Server Platforms
---

### Post by davebgimp on 2006-05-15
I have an ubuntu server and cannot start, restart or reload apache2.

All I get is this error message:

```

(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```

It seems to say something's using port 80, but doing a netstat, I can't find anything.

I'm kind of in the dark about what to do. I've attached my apache2.conf file, just in case that helps.

Any help would be greatly appreciated. I'm pretty lost with this.

---

### Post by empthollow on 2006-05-15
you could try: 

portscan your_ip_address

to find out what might be using the port, or you could change the listening port but i think that might prevent browsers from seeing the site altogether.  i've never tried changing the listening port. just an idea.

good luck

---

### Post by davebgimp on 2006-05-16
I did a port scan and 80 is shown as closed but not blocked with no program accepting connections. Any ideas?

---

### Post by empthollow on 2006-05-16
are you using a firewall? ... otherwise i found a thread on a different forum that suggests changing the port to 8080
[http://forums.devshed.com/apache-development-15/can-not-start-apache2-98-address-already-in-use-341064.html](http://forums.devshed.com/apache-development-15/can-not-start-apache2-98-address-already-in-use-341064.html)
and then restart apache.

---

### Post by cvmiller on 2006-05-16
[QUOTE=davebgimp]I have an ubuntu server and cannot start, restart or reload apache2.

It seems to say something's using port 80, but doing a netstat, I can't find anything.

I'm kind of in the dark about what to do. I've attached my apache2.conf file, just in case that helps.

Any help would be greatly appreciated. I'm pretty lost with this.[/QUOTE]

There are a couple of things you can do to see what is on port 80. If you are root on the machine, then do a 'netstat -anp' it will show you the process name. This is the easy way.

Another way is to use telnet, such as 'telnet localhost 80' and see what talks to you. This method may not be obvious what is actually running on port 80, but it will confirm that _something_ is running on port 80.

I hope this helps,

Craig...

---

### Post by davebgimp on 2006-05-16
Well, I edited my ports.conf file and changed the Listen from 80 to 8080 and that did the trick, though I never could figure out what was preventing me from using 80 normally.

---

