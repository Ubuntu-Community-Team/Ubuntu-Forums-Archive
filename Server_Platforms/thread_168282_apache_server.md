---
title: "apache server"
date: 2006-04-30
forum: Server Platforms
---

### Post by krcm on 2006-04-30
I have started setting up a server with apache2.
On my own linux-pc I can get acces to the files in /var/www/.
with ifconfig I have found my inet adress, that I gave to those that I want to show my files to, but they can't access, access to port 8080 is denied.
We use a router (levelone fbr-1418tx) in witch I have forwarded ports 80 and 443.

Can somebody help me fixing this problem.

I have already read a few threads on the subject here, but I can't seem to fis it myself.

Thx
An

---

### Post by jazzmuzik on 2006-04-30
You say you are forwarding ports 80 from the router, but you've set up Apache2 to utilize port 8080. Perhaps you should tell Apache to utilize port 80.

---

### Post by krcm on 2006-04-30
yes sorry, mixed up a few things.
in apache the port is set to 80.
in the router as well.
people i know with a server like that, use 8080 in their adress, so because putting 80 in the adress didn't work i also tried 8080 but no luck, obviously really, but when nothing works, I'm willing to try anything :).

---

### Post by jazzmuzik on 2006-04-30
Can you access the apache server locally either via localhost or via it's local address (e.g., 192.168.5.44)?

These tests should be verified before opening the server to the outside world.

I'm not completely sure about this because my networking skills are very limited, but could the address shown in ipconfig be different than the address outsiders would need to find your apache server? I was thinking it could be an IP address issue via the ISP, modem or router. A WAN address or something? I'm at the limits of my ability to give suggestions. I would search out a tutorial in this forum.

[http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by krcm on 2006-04-30
Yes, I can access the server via localhost and via the ip-adress of the router and the ip-adress of the pc and via an inet-adress.

outsiders can't acces using any of the ip's, we've tried them all.

I've changed settings on the router according to the manuel.

Any suggestions for a tutorial?

---

### Post by jazzmuzik on 2006-04-30
The only other thought is, are you using a firewall.

---

### Post by krcm on 2006-05-01
After I put the ip-adress for the router before the port, it seemed to work.
Haven't been able to check wether outsiders could get to my files but my son could using his laptop (win), he is also behind our router though.

Since we had to go somewhere I switched of the pc and when I rebooted later nothing was working anymore. I did a restart for apache, but that gave an error message saying 'httpd isn't running'.
There doesn't seem to be a file /etc/init-d/httpd or /etc/httpd/conf.d/php.conf.

Any idea what happened here?

An

---

### Post by Koybe on 2006-05-01
The files are /etc/init.d/apache2 and /etc/apache2/mods-available/php.conf
The path you'r giving are from fedora/RedHat. Ubuntu comes from Debian, it's a little bit different.
Anyway it's seems your apache is not running. What happend if you restart the service? What's in the logs? You need to clarify a bit to get more help ;)

---

### Post by krcm on 2006-05-03
hi,

so I seem to have been using the wrong files, :( oops, must have been something missing from apache as well though because I see there is a httpd.conf in /etc/apache2/ as well and I couldn't find any httpd file before.

been doing some reinstalling and got it working again, behind the router anyway. 
outsiders still can't reach it.

most probably because of the router , I have already forwarded port 80, but no luck.

Suggestions for what to do, are still very welcome :)


thx
An

---

### Post by Useless on 2006-05-03
This may seem a bit silly, but have you spoken with your ISP.  Perhaps it may be something on their end blocking you.  If possible i would try setting up another switch or hub connected to your router, see if that can reach the computer as well.  This way you know it isnt the router stopping your somewhere either.

---

### Post by krcm on 2006-05-03
don't really understand what i have to do with my isp :(

I did notice something else though, there is not a lot in httpd.conf, hence also the other problem i have probably (still happens after rebooting) when apache2 can't be started because httpd is not running ?!?.

This is all i can find in there:
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

thx for the replies so far
An

---

### Post by herrpoon on 2006-05-04
The main apache2 files should be in apache2.conf, in which, you'll be able to set the port for apache2 to use.

---

### Post by krcm on 2006-05-04
thx for helping, got it solved now   :D 

turned out our provider had port 80 blokked :-x , all I had to do was change this  


An

---

### Post by Useless on 2006-05-07
ahhh, what ISP do you have?  I knew someone with the same problem and it was the ISP blocking traffic, a lot of ISP's are known for blocking port 80 traffic this way people dont try setting up servers and killing too much bandwith.

---

### Post by krcm on 2006-05-08
Hi, 
I'm from Belgium and our provider is called 'telenet', but I know that there is also at least one doing so in Holland.
Grtz
An

---

