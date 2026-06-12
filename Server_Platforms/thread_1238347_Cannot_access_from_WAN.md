---
title: "Cannot access from WAN"
date: 2009-08-12
forum: Server Platforms
---

### Post by phillw on 2009-08-12
[RESOLVED]

Hi, I have set up apache - it appears correctly, as i can access the server via the LAN with its IP address okay.

I have used Firestarter to allow port 80, 443 and 10000 traffic thru' (10000 is for Webadmin)

The router has been told to allow web-server and HTTPS through.

I'm running 9.04, all builds are on auto-update.

the IP address is 192.168.1.69, again I can ping it from the LAN, but not from WAN :-\

My IP address *may be* 81.132.19.250  though - that one is the one gmail shows me as using - that one I can ping, but not connect to.

I'm betting I've missed something glaringly obvious...

Any ideas ?

Thanks,

Phill.

---

### Post by jfmanamtr on 2009-08-12
I am not sure that it isn't working. When I go to your IP address (81.132.19.250) in a web browser I get a screen telling me that I am in var WWW!. So I am guessing your web server is ported to the outside world correctly.

On the note about pinging your server's IP (192.168.1.69), that IP can't be pinged from the outside world. It is a routable internal IP for your router. As far as the internet is concerned, that address doesn't exist. Any time you want to ping your web server, you will need to ping your external address 81.132.19.250.

~John

---

### Post by phillw on 2009-08-12
thanks .. at least I know that bit is working !!!

Now to work out why i cannot access via https - but that's a job for tomorrow !!!

Regards,

Phill.

---

