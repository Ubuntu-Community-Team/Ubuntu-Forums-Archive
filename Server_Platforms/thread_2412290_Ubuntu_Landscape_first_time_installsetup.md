---
title: "Ubuntu Landscape first time install/setup"
date: 2019-02-10
forum: Server Platforms
---

### Post by techwhizard on 2019-02-10
Hello all,

I am from my personal experience, predominantly a Windows admin and I have started looking into Ubuntu for a particular project at work we are looking at doing with Azure IoT Edge and on premise Ubuntu server. I now have couple of Ubuntu VM joined to our Windows domain and IoT edge with no issues there and working beautifully hosted on ESXi already. Now I am looking at setting up a Ubuntu Landscape server and following Ubuntu's quickstart documentation when I try and proccess the [FONT=monospace, monospace][COLOR=#111111]sudo add-apt-repository ppa:landscape/19.01  command in terminak I receive,[/COLOR][/FONT]  ERROR: '~landscape' user or team does not exist.

The Ubuntu server version is 18.04.01 LTS. The VM's are behind a proxy which i have allowed access through for and apt-get update or apt-get upgrade connects to the internet ok and pulls through latest bits fine with no issues. I also submitted via terminal both for https & replacing with https command below.  I added the proxy in the /etc/apt.conf file as well for http, https & ftp. I cannot seem to figure out why I keep getting the above ERROR. I have tried to run all of the above commands directly via the root login as well without any luck. Hopefully someone can help me here point to something very obvious I have missed.

Thanks

[COLOR=#FF6301][FONT=&quot]export http_proxy="http://username:password@your proxy":"port"


[/FONT][/COLOR]

---

