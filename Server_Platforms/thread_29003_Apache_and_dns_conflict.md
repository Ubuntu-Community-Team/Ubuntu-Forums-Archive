---
title: "Apache and dns conflict"
date: 2005-04-22
forum: Server Platforms
---

### Post by tedbeau on 2005-04-22
I an a pure linux newbie so please be kind.
Got unbuntu installed, installed Samba, and apache ver 2.0
I am hooked to a cable modem thru a netgear router.
I have windows networking installed, and able to see windows machines OK from linux box.

I got the Apache server runing OK also, (Able to see the apache test page from one of the windows machines)

I wanted to install DNS so I could host my own domain on the linux server.

I installed the DNS (Bind9) seemed to work OK, except now when I try to view the linux web page (Public_Html) over the Lan, I am presented with a logon window, asking for user name and password. I tried entering the user name and password for the linux machine but it does not accept it.

Keep in mind that I have not edited the Name.conf file, but I did edit the Apache.conf file per some reccomendations from sites I found on internet.

My thought here is if Apache was working OK, (no logon) before I installed the DNS is that what caused the problem. Why would DNS require logon?

It seems I saw something some where about password directives in Apache.conf. but can't seem to find it again. I do have a group and user line added to Apache.conf but no password command, that I can see.

My httpd.conf is all remarked out, as being left for backward compatability.

Any suggestions?

---

### Post by alastair on 2005-04-22
If you're presented with a login dialog on a web page, it's because you've got some sort of HTTP authentication set up e.g. BasicAuth. This might be set in the Apache config file for the directory/location, or in files like .htaccess in the web directory (note the ".", they're hidden, so list via "ls -a").

---

### Post by jdonnell on 2005-04-22
You don't need to setup a dns server to do what you want. Most domain name registrars let you configure the dns for the domain thru them. You can also use a free server like dyndns.org if you don't mind having a subdomain. My home server is bloc.homelinux.org which I setup thru dyndns. 

One more thing, a lot of isp's block port 80. My cable company does so I can't run a webserver on port 80 and get to it from the outside. I can run it on a different port, but then your url will look like [http://bloc.homelinux.org:8080](http://bloc.homelinux.org:8080) 

Ask away if you have any more questions

---

### Post by jdonnell on 2005-04-22
are you alastair from livejournal? If so, I'm bloc07 on lj.

---

### Post by alastair on 2005-04-22
[QUOTE=jdonnell]are you alastair from livejournal? If so, I'm bloc07 on lj.[/QUOTE]
 No, I'm not. Sorry!

---

### Post by tedbeau on 2005-04-26
[QUOTE=jdonnell]You don't need to setup a dns server to do what you want. Most domain name registrars let you configure the dns for the domain thru them. You can also use a free server like dyndns.org if you don't mind having a subdomain. My home server is bloc.homelinux.org which I setup thru dyndns. 

One more thing, a lot of isp's block port 80. My cable company does so I can't run a webserver on port 80 and get to it from the outside. I can run it on a different port, but then your url will look like [http://bloc.homelinux.org:8080](http://bloc.homelinux.org:8080) 

Ask away if you have any more questions[/QUOTE]
 I may not need a DNS host machine, but since I have a Url already registered and I am to cheap to pay for a hosting service, it seemed like a good way to go. I can host the site on my old linux machine for free. I did look at DynDNS and another simular service except that they require a small fee, and/or you must use their TLD. 
Back to the original problem, which I have not had time to look at too much more, it seems like I get to different log in boxes on my windowsME machine. One ask for a password to access the linux machine if I try to access files on the linux machine over LAN. (I suspect this is something to do with Samba, not DNS) The other ask for user name and password to access a device, which when I checked turned out to be the cd player description (device name) for my windowsME cd player. I am not sure if this caused by DNS or not. This login does disappear if I shut down the linux box. To check, is there a terminal command I can issue to shut down DNS, and Samba, and Apache, one at a time to trouble shoot? I would think that turning one at a time off, trying the login, and turning each back on until I find which one causes the login display would at least point me in the right direction.

Thanks
Ted

---

