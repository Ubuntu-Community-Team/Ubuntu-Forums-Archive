---
title: "[SOLVED] Help with Apache and Port 80 Redirect . . ."
date: 2008-11-11
forum: Server Platforms
---

### Post by madhartigan on 2008-11-11
Hi.

I'm having trouble getting remote access to the website I'm creating because my Verizon DSL blocks incoming Port 80 requests.

I've configured my freedns.afraid.org account to redirect [www.mydomain.com](www.mydomain.com) to home.mydomain.com:31976.  I've also configured my router to port-forward port 31976 to 192.168.11.2 (my ubuntu server).

My problem is that I don't know how to tell Apache to listen to port 31976 and serve the index.html page I have in my /var/www/ directory when it receives requests from [http://home.mydomain.com:31976](http://home.mydomain.com:31976).

I'm not sure that I'm providing all the necessary details but I think there's enough here to get an idea of where I'm trying to get.


TIA for any advice/help!!

---

### Post by hictio on 2008-11-11
Well, depending on how you are making the port forwarding, you don't need to change anything on the Apache config file.
You can simply make the router forward whatever comes over the internet to port 31976 to the port 80 of the IP address of the Ubuntu server box, that would be the private one, inside your LAN.

---

### Post by oneloveamaru on 2008-11-11
You can do as hictio stated, use 31976 as your public port and then 80 as the private port when forwarding. Or you can make Apache listen on port 31976. I'm not sure what version of ubuntu you are running but go into /etc/apache2 and then run a "grep -R 80 *" and it will show you any lines with port 80 in all of the files. I say do the grep because there could be a port.conf file or not if you are running ubuntu 8.1. I don't have apache set up on my box with that version but I know Debian Lenny has that file, so I would assume the new Ubuntu does as well. Anyways, change the lines it finds with port 80 to the port you want it to listen on and then restart apache. /etc/init.d/apache2 restart.

Port forwarding would probably be easier but now you have a choice.

---

### Post by hictio on 2008-11-11
On my crappy DLink 614+ router, the option is called 'Virtual Server', it is located on the 'Advanced' tab, one plus, at I think it is, is that on this DLink enabling and disabling this does not need a restart of the router, a thing I personally find a total PITA.

---

### Post by madhartigan on 2008-11-11
yeah, well I have the Buffalo WZR2-G300N and it doesn't have the option to set the lan side port of whichever IP you're forwarding to.

For example, I can set the Internet Side incoming port to 31976, but I can't tell the router to send that to 192.168.11.2:80.  It gives me a Server Address error because of the port being included.  I can send it to 192.168.11.2, but that would be defeating the whole purpose of forwarding 31976 to 80.

Also, I don't have the advanced tab or Virtual server option.

Not sure what I'm going to do.

I think I'll give the suggestion oneloveamaru provided a shot.

Either that or I may buy a new router that's compatible with dd-wrt so I can have more overall control over EVERYTHING with my router.

????? Grrrrrr.

---

### Post by oneloveamaru on 2008-11-11
That sucks. Go with what I said. Tell me exactly what version of ubuntu you are running and I'll tell you exactly what to change. Also, is this the only site you have running?

---

### Post by oneloveamaru on 2008-11-11
Err.. I'm retarded. /etc/apache2/ports.conf should exist on all versions. Too much changing between distro's for me, gets me all confused. Just throw in Listen 31976 on there, should do it for you. Just make sure in your site config in /etc/apache2/sites-enabled/ that you only have VirtualHost * and not a :80 at the end, otherwise that page will only listen on port 80.

---

### Post by madhartigan on 2008-11-11
Oops, forgot to tell you the Ubuntu version, I'm on 8.04LTS.  I decided to stick with the LTS and not upgrade.

Currently, I'm only planning on running one website.

Thank you for the help!!

---

### Post by oneloveamaru on 2008-11-11
Looks like we posted at the same time. :) Just change that ports.conf file to include the port you want Apache to listen on and you should be fine. Let me know how it works out.

---

### Post by madhartigan on 2008-11-11
At first attempt it doesn't seem to have worked.

It's really late for me right now and I need to get to bed.  I'll be back at trying this in about 22 hours.  I'll post my progres up here then.

Thank you for sticking with me through this.

I appreciate the help.

-Darryl

---

### Post by oneloveamaru on 2008-11-12
After you add Listen and the port you want, restart apache. then do a netstat -a and see if that port is listed as listening. See if you can telnet into it also, that will tell you what you got.

If that doesn't work, then in the part where you have VirtualHost *, add the :31976 at the end. THat will make that page only listen on that port. It'll be a pain accessing your page inside without adding that at the end thogh.

Let me know. I can give it a test run on a test server if you can't figure it out.

---

### Post by madhartigan on 2008-11-12
I'm up and running now.

Tried it on two local "borrowed" wireless connections just to test the accessibility and everything is just PHYNE!!


Thank you for your help!!

---

### Post by oneloveamaru on 2008-11-12
Sweet, what were the steps to get you going? I'm thinking about those Ubuntu newbies who will be look at this thread next week or next year. Make it easy as possbiel for them. :)

---

### Post by madhartigan on 2008-11-12
Exactly what you told me to do. 

[quote=oneloveamaru]Just throw in Listen 31976 on there, should do it for you. Just make sure in your site config in /etc/apache2/sites-enabled/ that you only have VirtualHost * and not a :80 at the end, otherwise that page will only listen on port 80.[/quote]

It didn't work immediately last night but, when I tried it today, everything was working.

Now I'm having another problem.  I updated the "Under Construction" page (my original index.htm that I had in /var/www/) and added some additional pages with links.  I tried the site on my computer running it locally and everything worked fine.

I copied the files over to the /var/www/ directory and overwrote the original index.htm

Now, all I get when I access my site is the content of the original index.htm not the new one.  What's weird is the fact that the original one doesn't even exist anymore.  It's deleted and GONE.  I don't know where it's getting the data to load that old page.

:confused::confused::confused:

---

### Post by oneloveamaru on 2008-11-12
Clear your browser cache, close it down, re-open it.

The only time i have ever seen a page survive that is when tomcat on the server was caching the pages. Then a simple tomcat restart fixes that, but i doubt you are running tomcat.

---

