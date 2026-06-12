---
title: "Web server not showing up anymore"
date: 2010-07-29
forum: Server Platforms
---

### Post by darkapec on 2010-07-29
SOO... Here is the story...
I installed an ubuntu LAMP server on a soon to be computer that would be used to host my website. I did not have a computer case yet so there it sat on some cardboard. I setup everything (server wise). I got webmin, apache2, shorewall and mysql installed. I then port forwarded the needed ports on my router and everything worked great. I was able to access the computer from its local ip address 192.168.1.125 (I received the "It Works!!" message from apache) and from my ip address assigned by my ISP (charter). I then tested webmin, ftp etc all was working just as it should. I started moving my website over to it and that also worked just fine. I then let it set (shutoff and unplugged) for about 2 weeks. Than the case arrived so I moved it into its new low profile server chassis *sexy*... On first boot ubuntu told me there was some disk error and to manually run fdisk. I realized the cmos battery had died. I booted to the bios reset everything up (the time was set to year 2002 so ubuntu was throwing a fit). Now everything boots again as it should, according to ubuntu. However my router assigned it a new local ip, so all the port forwarding stuff had to be changed... not a big deal. I changed it and still I am unable to access the server via webmin, ip, isp ip, or sftp. Any ideas? apache2, webmin, shorewall etc are all up and running according to ubuntu. But even apache2 does not give me the it works or the website when i type the local ip address in. Is there some kind of internal ip address in apache2 that is auto assigned during installation and now i need to change it because the router changed the ip? that is the only thing I can think of. 
Thanks for any help
Jake

---

### Post by arrrghhh on 2010-07-29
If you're setting up a dedicated server, my #1 rule is static IP.

Start with that.  Reboot the server, let us know what happens.  This way, your server will ALWAYS have the same IP address on your LAN.  If the WAN IP is subject to change, you can use a service like DynDNS to solve that problem.

---

### Post by flatline on 2010-07-29
First of all, what kind of error does it give when you try to navigate your browser to your server's IP?  A 404, 403?

Also, can you do some snooping around?  Paste the output of the following commands:

```
$ ifconfig
```
```
tail /var/log/apache2/error.log
```

Maybe take a look at /etc/apache2/ports.conf, /etc/apache2/sites-enabled/000-default, see if there's anything weird in there that doesn't match up.

---

### Post by darkapec on 2010-07-29
After typing my rant I went "hey, I should setup a static ip" I setup the static... still was not working. It was at that time I noticed the network light on the network adapter was not on. I went to my router (been doing a lot of cleaning lately, just bought a new house) and notice the cable got unplugged, plugged it in, router picked it up and now everything works... and I couldn't feel stupider lol. Its funny how we sometimes look over the most obvious things. Thank you for your response and everything is working again :D

---

### Post by darkapec on 2010-07-29
> **flatline said:**
> First of all, what kind of error does it give when you try to navigate your browser to your server's IP?  A 404, 403?

Also, can you do some snooping around?  Paste the output of the following commands:

```
$ ifconfig
``````
tail /var/log/apache2/error.log
```Maybe take a look at /etc/apache2/ports.conf, /etc/apache2/sites-enabled/000-default, see if there's anything weird in there that doesn't match up.

Yah that is what I had been doing for the last couple hours. I am not to familiar with the ifconfig command in ubuntu, so I was not to sure what exactly was suppose to pop up but I found it weird that the gateway etc did not show up (probably because the cable was unplugged). apache2 looked good and so did shorewall. That is when I decided to post the issue here... next time I will remember to see if its plugged in next time. 

This whole situation reminds me of those tech support people that you hear about that ask idiotic questions like "is it turned on? is it plugged in?"

---

### Post by flatline on 2010-07-29
> **darkapec said:**
> This whole situation reminds me of those tech support people that you hear about that ask idiotic questions like "is it turned on? is it plugged in?"

Now you know that there is a reason they ask that.

;)

---

### Post by arrrghhh on 2010-07-29
LOL happens to the best of us sometimes.

---

