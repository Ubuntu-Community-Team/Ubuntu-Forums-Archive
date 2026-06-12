---
title: "cannot get apache to host websites"
date: 2011-06-03
forum: Server Platforms
---

### Post by covenist5 on 2011-06-03
I've built an Apache web server using Ubuntu 10.04.2 Lucid Server.  I've installed http, ssl, php, tls, python, ruby, and all kinds of other modules per [http://howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2](http://howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2) ... I am trying to get a website online, but I'm missing some key piece of the puzzle.  I can't seem to even get the default web page to actually show up for testing except on the server itself .  I know next to nothing about DNS and suspect that to be the problem, but no one can seem to give me any info that is relevant.  any info would be greatly appreciated.

---

### Post by Lars Noodén on 2011-06-03
If it's visible from the machine itself it should be visible to others on the same LAN.  How is that machine and your LAN connected to the Internet?

---

### Post by terazen on 2011-06-03
Try going to [http://x.x.x.x](http://x.x.x.x) from somewhere outside of the server where x.x.x.x is your server's ip address.  Also, check /var/log/apache2/access.log and /var/log/apache2/error.log to see attempted connections.

---

### Post by wojox on 2011-06-03
Have you configured port forwarding on your router?

---

### Post by Scunizi on 2011-06-03
Port forwarding in your router for outside access is crucial.  However, a lot of ISP's block the standard port 80 used by Apache.  You might need to change it to 8080 or just add 8080 as an option to the .conf.  Accessing from outside your lan after changing the listening port and setting up port forwarding on the router you'll need to use the OUTSIDE IP address... not the internal LAN IP address.  You can find that by going to "whatismyip.com" or similar.  If you've changed the listening port to 8080 then you use http://<IP Address:8080>

To access on the lan you'll have to use the ip address of the machine running Apache.  That is unless you go mucking about in the hosts.conf file or equivalent in windows.  

Another thing to check is the ownership of the web page files.. 
cd /var/www <enter>  -  this gets you into the directory where the html files are typically living.

ls -la to get a list of the files and their ownership within that directory.. if they are not root:www-data then you'll need to change it 

chown -R root:www-data /var/www/

---

### Post by covenist5 on 2011-06-03
It isn't visible on my lan because the rest of my systems are set up as a personal workgroup setup. One system runs SAMBA sharing all my data/media to my other systems in a workgroup.  I've given the web server a domain name, differing from the others.  (Maybe I should walk before I run, but I was never good at that).  However I have not looked at my router's settings yet.  I'll check into that and get back.

---

### Post by CharlesA on 2011-06-03
what workgroup or domain your web server is in shouldn't matter if you are connecting via IP address.

---

### Post by covenist5 on 2011-06-09
OK. The default page is visible all across my LAN.  I've enabled port forwarding on both my modem and router respective of the addresses they are forwarding to.  How do I now access them via the internet (by typing the domain name I've assigned to the server itself?)

I'm not entirely sure where to make the port changes throughout apache in case my ISP is blocking port 80

---

### Post by Scunizi on 2011-06-09
You can add port 8080 to apache and leave 80 there as well so it will listen on both ports.  In the router forward only 8080 to the machine hosting apache.. 

To get access from outside your LAN sign up for a free account at Dydns.com and you'll get a free domain name.. something like <your_choice>.<your choice domain>.<some extension com, org, info etc>

Your router should have a section in the setup to add your dydns.com account info.  What that does is it lets dydns know what your real WAN IP address is.  

If you want to use the domain name you've given your site already, you really can't outside your lan unless you are paying for (ISP dependant), commercial internet access or a static WAN IP address.. consumer level access typically doesn't let you buy a static IP.

---

### Post by covenist5 on 2011-06-10
Well at this point, I'm fairly certain it's my isp blocking incoming traffic.  with a free dyndns registration, port 8080 forwarded on both my modem and router, dyndns service enabled on my router, and my ports.conf file containing the line "Listen 8080" when I type the web url in a web browser, it dead-ends at the config page for my modem.  So it looks like I cannot do this for free with the service I have.  My ISP is the Clear home package (ethernet hookup of course, not the cheesy USB deal)  I think my next step would be to contact them and verify this to be the case.  If I'm wrong, again, any input will be appreciated, but I suspect I need a more robust ISP.

---

### Post by Lars Noodén on 2011-06-10
You can use [Canyouseeme](http://www.canyouseeme.org/) to check the availability of specific ports as seen from the outside.

---

### Post by Scunizi on 2011-06-10
It could be that port 8080 is being used by your modem for web control.. change apache to 8082 and see what happens.. you'll also have to change the reference at dyndns.com.  As I remember with mine I also setup a "web hop" address with dyndns.com to point to a different port number.  when you list the web hop address it should be http://<something>.<something>.com:8082 to direct it to the right port.

---

### Post by Scunizi on 2011-06-10
Sorry for double posting.. but I just thought of something.. you've got a modem (cable or dsl?) going to a router.  Does the modem provide a DHCP address to the router? and does the router provide DHCP to the LAN? Can you set a static address for the router itself and let it handle dhcp to the lan?  If so then port forwarding on the modem will be to the static IP of the router... then the router's port forwarding should be set to the appropriate machine on the LAN.. 

I hope that's clear enough to understand.. it almost sounds like the modem IS also a router.. so at this point the path to the PC is a little convoluted.

Another question.. can you get to your web page from inside your LAN using port 8080?

---

### Post by covenist5 on 2011-06-10
Yup, the option is available for ddns on the modem page, but the option checkbox to accept incoming connections is greyed out, along with the (unalterable) port setting that lists 8080 also having been greyed out, however since the options are actually there, It must be a feature that requires more $$

---

### Post by covenist5 on 2011-06-10
no, the modem is not a router, having only 1 ethernet port, but the option to select between a static IP vs. dhcp is also greyed out.  I think it must be a service I need to subscribe to or something.  all the options are there, I just can't change the settings to make them functional.

---

### Post by Scunizi on 2011-06-10
So it sounds like the modem just passes everything except what's blocked on the ISP's end (ie.. port 80).  Changing the apache port to 8082 and the port forwarding in the router should help get you there.  I wouldn't use the port forwarding in the modem at all since it's not a router.  Most likely not needed there anyway.

---

### Post by covenist5 on 2011-06-10
Oh, just to clarify,

Modem -- DHCP to the ISP; static IP, "allow incoming connection", port (8080) all greyed out
                port forwarding enabled to router's static ip address on modem at port 8080.
                
Router -- Static address to the modem, "allow incoming connection" enabled, port 8080 forwarded to Servers static ip on router, listening on ports 80 and 8080.

It's not a mobile modem (usb) but is on mobile service.  Clear's home service (3Mb/s down, 1.5Mb/s up) but again, I think they want money to activate these features since it could be used for hosting, and therefore making money.  I think they just want "their cut".  I will post after I talk to them to confirm.

ooh, just tested with canuseeme.org, 8080 not being blocked. disabling modem's port forewarding, and trying again

---

### Post by covenist5 on 2011-06-10
Do'oh!

They're blocking all ports except 8080 which seems to be in use strictly to access the modems web page.  I think I found my problem...

I do appreciate all the help though,  Now I know what I have to do.  Get better service.  and at least I'll have the necessary info to make it work at that point.  Thank you all for all your help

---

### Post by Scunizi on 2011-06-10
Not a problem .. Can you mark this thread "Solved" ?? the info here might be useful to others.

---

### Post by covenist5 on 2011-06-10
Aaaaaahhhhhh HAAAAAAA!!!!!!

    the configuration is now miffed, but I was able to connect (not properly) to my server from a library!  Port forwarding had to be enabled on the modem and router, but the thing that I was missing (i think) was port forwarding of port 53(DNS).  Just forwarding a port on the modem opened said port.  I forwarded port 53 to ports 53-8082 across my lan, then from my lan to my servers ip address, and (since the domain name changed, and I hadn't yet changed it on the server) instead of taking me to a "server not found" page, It took me to a "index1.html page not found on this server page/Apache/2.2.14 (Ubuntu) Server at server.xxx Port 80" page

Now going to tighten up all the open ports till I get it more streamlined, But I do believe my server to at least now be reachable!!!!!
WOOOOO HOOOOOOO!!!!

Now I think I can mark it as solved.

---

