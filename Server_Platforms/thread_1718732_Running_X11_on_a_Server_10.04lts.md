---
title: "Running X11 on a Server 10.04lts"
date: 2011-03-31
forum: Server Platforms
---

### Post by keiffee30 on 2011-03-31
Dear all i would like to know if this is poss. I have set up a Web Server (LAMP) for training websites and for small charity's to host there websites. 

Now i would like to run firefox to i can run something like Ebox/Webmin. now i don't really like to install a full desktop i would only like to install X11 and then run firefox when needed. I have looked at the documentation and i would like to know the commands needed. Im also using a Nvidia card just to make life harder lol.

**sudo apt-get install libvdpau1 nvidia-185-libvdpau**

This would be to install the driver for the video card. i think

**sudo apt-get install xserver-xorg xserver-xorg-core**

This is to install a "Bare Bones" xserver i take it ?? i hope this dosen't start up "x" if the server reboots / starts up. 

**sudo apt-get install firefox**

As it said on the tin installed firefox. so far so good i think? can anyone see anything i have missed so far. I am also thinking of installing** Ebox/Webmin**. After reading how to install **Ebox** the web address to enter to access this is 

**[http://webserver-ip-address/](http://webserver-ip-address/)**

If i go to this address i would hope to see the default website and not the Ebox page. i know with Webmin you have to put in a port number i.e. 

**[http://ip-address:10000](http://ip-address:10000) **

but for Ebox there is no port. could someone please tell me that if i go ahead and install/set this up i will not "muck" the webserver up???

---

