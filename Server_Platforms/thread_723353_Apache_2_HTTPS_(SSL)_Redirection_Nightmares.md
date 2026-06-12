---
title: "Apache 2 HTTPS (SSL) Redirection Nightmares"
date: 2008-03-13
forum: Server Platforms
---

### Post by GenuineXP on 2008-03-13
Ugh! Is it just me, or is Apache a never ending maze of configuration files? I've been trying all day to redirect requests for my SVN repositories to HTTPS with no success at all.

Now I have a very strange problem. An earlier attempt seems to have marred my entire Apache installation as requests for the document root are redirected to some bizarre address.

I'm not using DNS, so I access the server by IP. When I attempt to visit [http://192.168.1.9](http://192.168.1.9), I get redirected to [https://%25%7bhttp_host%7d/svn](https://%25%7bhttp_host%7d/svn) ! Brilliant!

I've searched all the files under /etc/apache2/ for the strings "svn", "redirect", and "https" using find -exec to no avail. I can't find the source of this bizarre redirection. Visiting http**s**://192.168.1.9 (note the 's') works just fine and I get the usual access denied page I expect. How can I find the source of this broken redirection?

Also, does anyone have any idea how to perform this redirection, keeping in mind that my server has no domain name or name of any kind (especially since winbind won't work between my Ubuntu machines; no host names either!). Most guides I've seen so far don't tell you into which configuration file to dump the code, so I end up moving it from one place to the next without any results.

Any help would be **greatly** appreciated; this problem is frustrating me to no end.

btw, I know about XAMPP, but I'm exposing this server to the Internet which the XAMPP team says is unsafe with their bundle. Also, I'd like to learn how to set these things up... even if it *is* killing me! :-P

Thanks!

---

### Post by GenuineXP on 2008-03-13
Hm, it seems restarting the browser at the client fixed the strange issue with the bizarre redirection! Maybe it had something to do with accepting the certificate temporarily...

Strange enough! :-)

Anyway, I'm still in need of help forwarding requests from HTTP to HTTPS. Specifically, I want this to happen whenever [http://.../svn](http://.../svn) is accessed. Is there a simple way to do this? The simplest solutions I've seen so far force HTTPS for **all** pages on the server, which is not what I want (none of them worked either, btw).

Thanks again.

---

### Post by benne on 2008-03-13
Redirecting is fairly easy with apache. Just put the line below in your configureation for the default vhost (the 000-default thing)

Redirect / [https://adress/svn](https://adress/svn)

Or if you would like to forward [http://address-or-ip/secure](http://address-or-ip/secure) -> [https://address/secure](https://address/secure)

Redirect /secure [https://address/secure](https://address/secure)

You get the idea..

---

### Post by GenuineXP on 2008-03-13
Wow! That was very simple and it works pretty well. Thanks a lot!

I tried something very similar earlier, but it involved some regular expressions that I didn't really understand. It generated the strange results seen in my first post and did so from just about any location. This works as I intended, and anything under [http://.../svn](http://.../svn) is redirected to HTTPS. :-)

Is there a variable or placeholder I can use for the server's IP address? Right now I hard coded it in as 192.168.1.9, but this may change.

Thanks again!

---

### Post by benne on 2008-03-16
Sorry for the delay. But you can change apache's setting ServerName to either the hostname or the ip. Im not sure what you are trying to accomplish but tingering with it might help you.

Apache is really easy to configure when you understand how it works. I bought 3 O'Rialy (hwoiever its spelled) book on apache a while back and it helped me a lot. Now i work as a sysadmin, linux specialist and i manage a lot of apache servers.

---

