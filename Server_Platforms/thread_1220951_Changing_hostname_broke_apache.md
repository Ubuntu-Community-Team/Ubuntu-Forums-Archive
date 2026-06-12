---
title: "Changing hostname broke apache"
date: 2009-07-23
forum: Server Platforms
---

### Post by nimbostratus on 2009-07-23
Hi

I tried changing the hostname on my machine by changing /etc/hostname and restarting. Apache stopped working so I changed the hostname back and restarted again. Apache still doesn't work.

My hostname file is now:

```
aaron-desktop
```

My hosts file contains:

```
127.0.0.1       aaron-desktop   localhost.localdomain   localhost
127.0.1.1       aaron-desktop
```

And the relevant part of my apache conf contains (it's a development machine I only want to access locally):

```
Order deny,allow
Deny from all
Allow from localhost
```

Accessing that directory from my machine gives a HTTP 403 Forbidden error.

The weird thing is that if I change 'localhost' to 'aaron-desktop' in the apache conf, everything works fine.

I guess that means apache isn't connecting the IP of the request (127.0.0.1 - I've checked that) to the name 'localhost'.

Can anyone tell me why not?

Thanks
Aaron

---

### Post by wojox on 2009-07-23
Change hosts file to:

127.0.0.1	localhost
127.0.1.1	aaron-desktop

---

### Post by nimbostratus on 2009-07-23
Great, thanks.

I tried a few other combinations too - it seems anything with localhost first on the line works.

I went back to changing the hostname as I wanted to originally - after restarting, the hosts file was broken again. Fixed it no problem, but it seems weird that the automatic updating of hosts breaks it. Maybe a bug?

---

