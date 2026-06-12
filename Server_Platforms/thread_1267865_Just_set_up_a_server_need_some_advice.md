---
title: "Just set up a server need some advice"
date: 2009-09-16
forum: Server Platforms
---

### Post by RFXCasey on 2009-09-16
I just set up an Ubuntu server and installed gnome and webmin. Can someone give me some advice on what I need to do to set up a firewall that will potential work with webmin. I also need to know, if I install vsftp will there be any controlling it through webmin? Back to the firewall thing, can I set up uncomplicated firewall or something similar and what if I want to implement something like dansguardian how would I go about doing so.

---

### Post by R.Bucky on 2009-09-16
Sorry to see that you installed a GUI on your server. It just became far less secure of a server and overall environment. Depending on your version, UFW should be installed by default. Enable it with ```
sudo ufw enable
```
Open up port 80 and your server should be live from the server's point of view pending your router/hardware firewall config. Check to see if Webmin has a vsftp module. Look on the left-hand frame of Webmin for "Unused Modules" and see if it is listed.

---

### Post by RFXCasey on 2009-09-16
> **R.Bucky said:**
> Sorry to see that you installed a GUI on your server. It just became far less secure of a server and overall environment. Depending on your version, UFW should be installed by default. Enable it with ```
sudo ufw enable
```
Open up port 80 and your server should be live from the server's point of view pending your router/hardware firewall config. Check to see if Webmin has a vsftp module. Look on the left-hand frame of Webmin for "Unused Modules" and see if it is listed.

Well, I wasn't going to install a GUI sometimes it seems like finding the command line way of doing things on the internet is harder then finding the GUI way. I also seemed like a lot less of a hassle to use webmin which I am assuming you can't do in CLI. I am all for CLI only but time is valuable these days, convenience and ease of use are worth their weight in gold. If you have a better suggestion let me know.

---

### Post by R.Bucky on 2009-09-17
I certainly agree that CLI is a different way of doing things coming from a GUI only world. But, once you start out with CLI it really is more efficent. I have a headless server (no monitor) which also has Webmin that I use for backups and quick reference (accepting lashings for this install...). You can access webmin on port 10000 from any computer on your network as it operates its own server. 

Do you have UFW enabled yet? 

Suggestions: If you have an extra box, install the Serve edition and force yourself to use CLI. Keep a notebook for all of those helpful Terminal commands so that you can remember them for a later time. Even though you have a GUI, still try and use Terminal for your commands. It might smooth the transition until you are ready. 
 
Good luck! 

~Mark

---

### Post by RFXCasey on 2009-09-17
Well one of the first things I did was print out a list of the bash commands and keep them at my desk at all times. That has helped quite a bit. I have a notepad but I need a new one as the one I have is a mess. Is there anyway to purge the gnome-desktop and all related apps from my server without causing havoc? I didn't really want a GUI in the first place it's just that I was reading a tutorial on installing webmin and they threw in the GUI install without mentioning weather it was options or not. I kinda got sucked into that one as it was really early in the mourning and I was kinda punchy at the time. I had just run out of coffee too.

---

### Post by openfly on 2009-09-18
It's no webmin, but fwbuilder has a great interface for defining iptables.

---

