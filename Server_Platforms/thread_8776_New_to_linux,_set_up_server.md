---
title: "New to linux, set up server"
date: 2004-12-20
forum: Server Platforms
---

### Post by crunkmonkey on 2004-12-20
Hi, I'm new to linux.  My main purpose is to use an old computer as a file and web server.  I have installed Apache 2 but I seem to be stuck from there and the HOWTOs are too advanced so I'm asking for help on these issues:

1) How can I connect to my computer/server through ftp?
2) Where do I put my html files for web viewing?
3) I'm connected through DSL+Router.  This changes everytime I connect so what is the address of my webpage (when I finally figure out where to put it)?  If I use the currect IP, it tries to connect to the router.  I can change the router settings but this is not what I want to do.  

I know these are kinda basic but this is the level that I'm at and the documentation is way over my head.  :confused:

Thanks!

---

### Post by dare2dreamer on 2004-12-21
> 1) How can I connect to my computer/server through ftp?

You'll need to install an ftp server (ftpd?) via synaptic.

> 2) Where do I put my html files for web viewing?

Ubuntu does not install a web server (or any servers for that matter) by default, but fortunately apache (and many, many others) is in the repository. Again, synaptic is your friend. :-)

> 3) I'm connected through DSL+Router. This changes everytime I connect so what is the address of my webpage (when I finally figure out where to put it)? If I use the currect IP, it tries to connect to the router. I can change the router settings but this is not what I want to do.

There is a package in the repository called ipcheck, which with a bit of scripting will allow your machine to update a dyndns.org dynamic dns entry on a regular basis (hint: read up on cron for the automation part). I use this solution on a regular basis, and it allows me to connect to my home machines with no issues. Apt-get ipcheck (or google a bit) and read the man pages for ideas on how to set it up.

Once you do that, you can forward appropriate ports from your router over to your server. This is usually referred to as virtual server or port redirection in most router's web-based configuration.

I use Ubuntu on my desktop, but frankly I've noticed its desktop-centric nature leaves it better suited to that task alone. For servers that behave more or less the same way, I recommend installing a minimal installation of debian and working from there. The two together, in my opinion, are a wonderful combination.

Good luck!

---

### Post by fishd on 2004-12-21
I've recently done this and it's not an easy thing to explain in a short time.

If you're just looking to quickly get a webserver up and running on a stand-alone machine perhaps [www.e-smith.org](www.e-smith.org) or [www.clarkconnect.org](www.clarkconnect.org) would be an easier road.

If you're looking to move your desktop to linux and also have it serve webpages and remote file access (as I have done) then read on a little.

I've installed the following services:

DDClient - Updates a DYNDNS.ORG DNS entry with your new IP address so whenever your IP changes a DNS entry of yourclient.dyndns.org is updated.

SSHD - Provides remote login capability AND secure remote file transfer (think FTP with encrypted logon).

Apache2 - Serves HTML pages, also using mod_music-thingy-something-or-other can provide a dynamic web page to stream your MP3's/OGG/etc across your LAN.

Step one is to configure your router. If it has a firewall - TURN IT ON! Next check for a section called "port forwarding". You need to forward ports 22 and 80 to the internal ip address of your router. If it's only you using the box try using something other than port 80 for WWW traffic, it reduces the number of attacks from script-kiddies.* If you want to do that you'd forward something like port 5555 to port 80 on your servers internal IP address and to access the page you'd type *[HTTP://yourclient.dyndns.org:5555](HTTP://yourclient.dyndns.org:5555)* in your browser. Pick your own random port number though.

Step two is to configure the various services. 

The readme file included with DDClient is quite good and should have you up and running quickly. You'll need to visit [www.dyndns.org](www.dyndns.org) and create an account (it's free for the type of account you'll want).

SSHD has a default config which works, I've yet to read into the config in any depth but it'll allow you to use the excellent Putty for Windows to remote login to your server, you can also use psftp from the same site for FTP with SSH login (plain FTP sends usernames and passwords in plain text and can be sniffed over the net, SSH (and therefore PSFTP) encrypts login information before sending!).

For Apache configuration you need to do some reading... no, scratch that... a LOT of reading. The Apache website is a good place to start. BE AWARE that Ubuntu uses a slightly different method to configure Apache, instead of one large unweildy .conf file it uses a number of smaller more focused configuration files either in conf.d or sites-enabled. Configuration of Apache modules is done in mods-available with symbolic links to mods-enabled.

Well, those are the basic steps, although I'm afraid it'll take a lot of reading. 

* I said "reduces" and "script-kiddies" - it won't stop the attacks all together and it won't protect against an intelligent hacker but there you go.

---

### Post by dare2dreamer on 2004-12-21
A little note about ddclient vs. ipcheck:

Back when I set up my dyndns.org account, I set up ddclient at their suggestion. I found that it ran constantly as a daemon, eating a pile of memory and spinning the wee little hard disks on my debian server to the point where I actually got concerned about wearing them out.

ddclient does nothing more than ipcheck, but imho ipcheck does it with far less overhead.

Just my experience, your mileage may of course vary.

---

### Post by fishd on 2004-12-22
Cool, I'll check it out ! Thanks for the suggestion.

---

### Post by az on 2004-12-22
I must dissagree with ddclient eating up cpu.  I had no such experience, it ran like a charm.

If, however you are running behind a store-bought router (as opposed to a linux box acting as a router) you may need to use the router's buit-in dyndns client if it has one.  If it does not, you may still be able to access the ip-address functions to find out what you ip address is.  Check to see what dyndns client you can use for this, since they do not all support this.

If you cannot know your wan ip address, your dyndns client will not work...

---

### Post by cpinto on 2004-12-22
My two cents:
instead of using a prebuilt client that is a daemon, put together a small bash script that gets the router's external IP and sends the update to DynDNS. Clients won't do you any good if they'll look for an external IP on one of the ethernet cards in your computer. Some of those clients also use some sort of callback method on a remote site to get your IP address, which I really don't like and can't trust.

So the solution that best suites my case is the bash script. You can look at this script [http://yimports.com/downloads/ipupdate](http://yimports.com/downloads/ipupdate) to get a feel for it. 

All the magic is done in the crontab.

In my case, I'm looking to improve it to reset the xDSL modem whenever it can't get an external IP address.

---

### Post by fishd on 2004-12-22
I know ddclient actually parses the html page on the router to get the routers external IP address. This means adding your routers username and password into your ddclient.conf but you can restrict the file so only root can read it... I assume that means the ddclient deamon is running as root which could be bad... but hey ho.

As for routers inbuilt dyndns clients, I know my pals netgear box works ok but my linksys craps out after a day or so and I need to warm-reset the router to get updating working again... I think I read that at one point dyndns.org had barred updates from Linksys MAC addresses because a newly released router was sending updates every two or three seconds!!!

---

### Post by McDano on 2005-01-19
[QUOTE=cpinto]
So the solution that best suites my case is the bash script. You can look at this script [http://yimports.com/downloads/ipupdate](http://yimports.com/downloads/ipupdate) to get a feel for it. 
[/QUOTE]

Hm, link seems to be dead. Could you put it back on? Tried ddclient but I had some strange errors which I didnt understand (not too strange since i'm a a bit of a noob ;)) and I think i'm read to try something new

Cheers :)

---

### Post by az on 2005-01-19
"Tried ddclient but I had some strange errors which I didnt understand"

Please post them (the errors)  perhaps someoen here will understand them.  Errors can be a very good trail to follow since they tend to lead straight to the answer.

---

### Post by McDano on 2005-01-20
Thanks for the offer, what I did is manually download and configure it the first time

did an apt-get install ddclient now and it works like a charm, I think I made some mistakes in that config file

---

