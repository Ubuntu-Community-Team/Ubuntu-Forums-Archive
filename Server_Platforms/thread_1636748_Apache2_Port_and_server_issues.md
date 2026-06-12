---
title: "Apache2 Port and server issues"
date: 2010-12-03
forum: Server Platforms
---

### Post by yettiman2208 on 2010-12-03
So I have installed Apache and have everything running and presenting webfiles from within the local network.

I know that my provider blocks port 80. So I have a dyndns account which has two addresses. the first is server.dyndns-web.com (not actual). This url webhops to the url server.dyndns.org:8888 (this is in order to get around the isp blocking 80)

I then tried to set up port triggering on my linksys (cisco) e1000 router so that ports of 8888 will trigger to port 80. This is something I am not sure how to do correctly, but I think I did. I also have both 80 and 8888 forwarded to the internal IP of the server ****.130.

When I attempt to access the server.dyndns-web.com from outside my network I get a website that says 404 apache cannot find website or something. And indicates the domain server.dyndns.org:8888.

I have the apache listening on both 8888 and 80 at this point just in case.

So my understanding is that the website server.dyndns-web.com is directing correctly and rerouting to the .org:8888 which is then connecting to the server and apache. The problem appears to be that apache is not serving the website from the /var/www/ directory. Is this correct?

I have sufficiently run myself in circles now and am not sure exactly what is going on.

Any help would be much appreciated.

-a large yetti

---

### Post by arrrghhh on 2010-12-03
Alright, let's start small.

Can you hit the 'main' website ( server.dyndns.org:8888 ) and get your site?

Make sure you do this from outside your LAN, it probably will not work on your LAN.

---

### Post by yettiman2208 on 2010-12-03
Thanks for the response!

No. When I put in that address I get the 
"
Not Found

The requested URL / was not found on this server.
Apache/2.2.16 (Ubuntu) Server at rprk.dyndns.org Port 8888"

So its reaching the server I believe.

I also get the same response with server.dyndns-web.com

---

### Post by arrrghhh on 2010-12-03
Hrm.  Ok, perhaps even smaller.  Does the site work on your LAN?

---

### Post by yettiman2208 on 2010-12-04
Ok, so this is sort of odd.

It does work on the lan. server.dyndns-web.com points to the generic index.html that apache starts with (it works!) but outside of the lan it does not.

However, I installed mediawiki a litle while ago, and I just tried right now to access server.dyndns-web.com/mediawiki from OUTSIDE of the network and it works........

so now I am really confused. Is the index.html file just not setup correctly?

because server.dyndns-web.com/index.html does NOT work outside the lan. Only inside.

hmmmm

---

### Post by CharlesA on 2010-12-04
Are you using the default apache config, or using virtualhosts or some such thing?

---

### Post by yettiman2208 on 2010-12-04
I didn't think I had set up anything out of the ordinary, 
But when I checked the Webmin interface, it lists a "Default Server" as well as a "Virtual Server"

I am not sure if this is what you were asking. I am totally new to apache

-a large yetti

---

### Post by yettiman2208 on 2010-12-04
THANK YOU!

You all pointed me in the right direction!

When I went into the Webmin I noticed that there was an additional "virtual Server" which listed the various /var/ directories. I then noticed that this virtual server was listening on port 80. I changed this to listen on any port. and now everything works just wonderfully.

I do get this when restarting, but I am just going to ignore it atm cause everthing else works.

"* Restarting web server apache2
[Sat Dec 04 10:36:10 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Sat Dec 04 10:36:11 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
   ...done.
"

server.dyndns-web.com gives me the index.html file. and also, the */testphp.php i made works. and the same */mediawiki works as well.

I very much appreciate all the help!

sincerely, 

-a large yetti

---

### Post by CharlesA on 2010-12-04
Awesome.

Don't forget to mark the thread as solved from thread tools. :)

---

