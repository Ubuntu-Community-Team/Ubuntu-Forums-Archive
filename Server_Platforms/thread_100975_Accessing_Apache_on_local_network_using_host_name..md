---
title: "Accessing Apache on local network using host name."
date: 2005-12-08
forum: Server Platforms
---

### Post by DavidVanCan on 2005-12-08
Greetings,

I have a small home network that is connected to the internet via a router. I recently installed Ubuntu 5.10, Apache 2.054 and Webmin 1.230 on two of the computers on the network. I don't think it matters but one installation was an i386 install and the other was a powerpc install. (By the way both installs went flawlessly which was extremely gratifying for a novice such as myself).

There is one small difference between the two installations that I would like to change:

On one computer the Apache web server can be accessed by the web browser on other computers on the network by using the hostname in the URL like this; "http://hostname1/". The same with WebMin, it can be accessed like this; "https://hostname1:10000".

The other computer is different. When accessing Apache using a web browser on a networked computer I must use the IP address like this; "http://192.168.0.7/" and WebMin like this; "https://192.168.0.7:10000". However, if I access these programs with the web browser on the computer that they are installed on then I can use the host name.

I have carefully examined the System/Administration/Networking settings and any other settings I could find but I can see no difference between the two installations. How can I get the other computers on my network to access the second computer using its host name?

Thanks, David

---

### Post by cactus on 2005-12-08
1) run dns on your local network. even something like dnsmasq that just does recursive queries against your upstream dns server... then add your hostname / ip addresses to the dnsmasq conf.

or

2) on every workstation, add the ip address and hostname to the /etc/hosts file. ps. Even windows has a hosts file. in \WINDOWS\system32\drivers\etc

---

### Post by jameso on 2005-12-12
In my experience installing and running samba on the server should automatically share it's hostname with the windows pcs on the network.

This might be a good option if you were planning on having windows based file sharing anyway.

---

### Post by LordHunter317 on 2005-12-12
In Linux, tha will only work for some Windows filesharing activites.  Unlike Windows, Linux doesn't normally use NetBIOS name resolution as part of any of it's everyday activities.

---

### Post by dbee on 2005-12-12
Isn't that what resolv.conf is for ???

---

