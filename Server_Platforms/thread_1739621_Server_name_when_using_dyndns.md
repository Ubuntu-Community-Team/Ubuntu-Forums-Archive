---
title: "Server name when using dyndns"
date: 2011-04-26
forum: Server Platforms
---

### Post by knottulf on 2011-04-26
How should I set up my webserver when using dyndns?

My server lives behind a private router, and I opened a nonstandard port for it (xxx.dyndns.org:6789)

I need to be able to access the webserver  both from behind the router, and from outside. But espescially wordpress needs to have a defined specific site-url for each site, which I can not get working both inside and outside the router. Inside I now just just the local ip-number, which works ok. To access the server from outside, I have to redefine the site-url to "xxx.dyndns.org:6789", but then it is not accessible from behind the router.

Joomla does not have this problem, but anyway, my configuration obviously is not correct.

Any advice, anyone?

Knottulf

---

### Post by Charlietje on 2011-04-26
the best thing to do in my opinion.

Set up your webserver to work on port 80.
On the local side of your router, you will be able to connect to the webpage

On your router, enable portforwarding from port 6789 to port 80.
So from external side, the url is xxx.dyndns.org:6789 but will be translated on internal side as xxx.dyndns.org

---

### Post by Vegan on 2011-04-26
unless your isp blocks port 80, do not worry about it

you can always use a welcome page if needed

with a log in for access and a cookie to check for authentication

---

### Post by elico on 2011-04-26
there is a way to not use specific site name on wordpress but i wouldnt recommend it.
if you cant use port 80 cause of an ISP limits or router Limits you can use port 8080 or 8111 or any other above 1024.
and change it also on your local webserver.

what router do you have?
i can might help you settings ip up.

---

