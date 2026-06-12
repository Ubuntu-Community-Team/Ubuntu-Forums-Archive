---
title: "Ubuntu Server 14.04 No Networking After Update"
date: 2015-07-07
forum: Server Platforms
---

### Post by corporationsruleyo on 2015-07-07
Hey Ubuntu Community!

I seem to be having a network issue after a security and/or kernel update on my Ubuntu 14.04 server.
I'm not exactly sure what has happened here and from what I can see I haven't changed any network or interface settings.
I did attempt to switch interface settings from dhcp to static to fix the problem but that didn't work unfortunately.
I have my Ubuntu 14.04 server setup dhcp, and I have my router set to assign the server's mac address a local ip of 192.168.0.7 as an example.
I cannot ping the server locally on my workstation within the network. I cannot ping from the server to my workstation locally and I know it has a local ip of 192.168.0.101 as an example. I can't ping out to google.com either.
I'm seeing Apache complain on start up about not finding the fully qualified domain name and something about setting the ServerName to avoid the warning.
Were any of the default configs overwritter with a recent update?

Are there any tools to help me debunk the problem? Ive tried ifconfig and the settings are all correct as I can see, but still wont connect me to the network... Very frustrating!

Any help is greatly appreciated! I will edit my post or reply with my interface settings in a minute!

---

### Post by corporationsruleyo on 2015-07-07
Okay, plugged the server into a different port on the router and it works now... Oddly enough I used that port for the PS3 and it worked just fine streaming across the network... Why is Ubuntu being picky here? Or is it a limitation of my network card?

---

