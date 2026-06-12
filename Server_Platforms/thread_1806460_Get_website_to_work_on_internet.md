---
title: "Get website to work on internet"
date: 2011-07-17
forum: Server Platforms
---

### Post by ScottG89 on 2011-07-17
I finally got my apache web server up and running and tested it using local host. I was wondering how I can create a domain name now and get this accessible on the internet. Thank you

---

### Post by Dangertux on 2011-07-17
You would have to go through a domain registrar. Usually it's between 5 and 10 US dollars per year for a domain. Sometimes less if you want something like a .info

You also need to consider if you have a dynamic IP how are you going to keep your domain dns records up to date. Most registrars do not support this functionality natively. 

Services like no-ip or dyndns offer subdomains or domains that will keep up with your changing ip. I believe the yourname.com style no-ip accounts are about a little bit more pricey. 

You can probably get a static ip from your ISP (depending on ISP sometimes free) and bypass the dns headache. 

Also consider security before going public Apache and Ubuntu are reasonably secure out of box but depending on your configuration and what type of web site you're wanting to run that could change drastically. 

Hope this helps.

---

### Post by ScottG89 on 2011-07-18
Ok, thank you very much.

I know I can change my ip from dynamic to static in /etc/network/interfaces, but since I am on a router, that means that I can just make sure that my internal ip is always something like 192.168.1.8, would I need a static external ip?

I understand the concern with security, my site isn't going to have much info being passed through it, but once I learn how to get this up and running, I will definitely look at some security tips.

---

### Post by zero2xiii on 2011-07-18
ScottG89,

I'm running serveral FTP public servers. I might be able to assist you in some detail:

1. For a free domain, register at [http://www.dyndns.com/](http://www.dyndns.com/). This will give you a domain name MY_DOMAIN_NAME.dyndns.org (org might be .com or other...)

2. Download the dynamic client thingy (what ever the correct naming is) ddclient via synaptic or apt-get: "sudo apt-get install ddclient".

3. Setup ddclient through the on screen prompts.

4. Now comes the tricky part. Getting your router to forward all inbound connections to the router on a specific port, to a specific internal IP:Port combination (NAT port forwarding).

For details on how to set this up, visit [http://portforward.com/](http://portforward.com/)


Once all of the above is done correctly, you should be able to visit your website from ANOTHER connection, OVER the internet. Please note it is NOT possible to visit localy hosted sites just by entering the URL in your browser, its a port clash (cant make and receive a connection from a single origin or something in those lines.)

Hope this helps a bit:popcorn:

Edit:
What exactly are you doing:

1. The domain registration, is just to have a static name you can point a browser to eg, instead of typing  74.125.71.103 for google, you type [www.google.com](www.google.com).

2. The ddclient sends your new INTERNET (external IP as you reffered to it) to the domain host (dyndns in this case) so that it can point all requests to MY_DOMAIN_NAME.dyndns.org to your correct internet IP each time your IP changes. This step will fall away if you were to use a STATIC internet IP... 

3. This is pretty self explanatory

4. What this NAT port forwarding does is sending all requests to your internet IP (which is your router looking from the internet) to the computer on the LAN of the router, basicly creating a doorway from the internet to your PC doing the hosting (this is really explain basicly, don't flame me for using INCORRECT terms or defitions plzzzzz???). If you skip this, and I visit eg xxxx.dyndns.org:80 I will be prompted for a username/password, which, if i guessed correctly, will lead me to your router's webconfig. The NAT forwarding sends my request to xxxx.dyndns.org:80 (which is currently your router) to xxxx.dyndns.org:80/xxx.xxx.xxx.xxx:80 (which is the PC BEHIND the router, please note this is technicaly INCORRECT, its just to explain what happens, again).. 

SO there you have it, now you know what you are doing, and why :)

---

### Post by ScottG89 on 2011-07-18
Ok, that was an awesome guide. I can't actually say that it works yet because I messed one thing up and need help fixing it. I installed the ddclient and it auto ran in terminal, I was going through the prompts but I forgot to activate my hosts. So when ddclient went to pull up a list of my hosts, it said there were none and exited. How can I pull the prompts back up? I tried uninstalling then reinstalling but they won't come up.

Also, this guide told me how to get a free mydomainname.dyndnswhatever.com or I assume I would be able to register a domain for $15/year with dyndns and then I could just have a mydomainname.com. I was wondering, does every website on the internet have to pay for domain registration through dyndns or another similar company or is there a way that they do it all on their own for free.

Thank you for all of the information

---

### Post by zero2xiii on 2011-07-18
>  I installed the ddclient and it auto ran in terminal, I was going through the prompts but I forgot to activate my hosts.

Haha look here: /etc/ddclient.conf but that means manual edit, also try "man ddclient" to see some more manual options you can set. 

I found this guide [http://linhost.info/2008/12/ddclient-set-up-for-ubuntu/](http://linhost.info/2008/12/ddclient-set-up-for-ubuntu/)  which says:

```
dpkg-reconfigure ddclient
```

should allow you to reconfigure the deamon. I sugest reading through the guide though, it goes through some of the more indepth options, if you so happen to need to use some of them.


As far as your DNS query goes. Yip, ALL sites need to be registered at some form of a DNS server. There are a few out there. I haven't come accross one that allows a full "www.mydomainname.com" without some form of payment (I have seen a few that require you add >10 advertisements on your site and you get bandwidth per click). But in any logical reasoning, some for of payment is neccesary, sorry.. haha.. 

If you do find one that is free full domain name hosting. Please share it.

Well, glad I helped a bit, any more questions, just shout :D

---

### Post by ScottG89 on 2011-07-18
Ok, thank you very much for the information. I got everything to work now

---

### Post by zero2xiii on 2011-07-19
Hay awsum!

Haha please remember to mark the thread as solved :biggrin:

---

