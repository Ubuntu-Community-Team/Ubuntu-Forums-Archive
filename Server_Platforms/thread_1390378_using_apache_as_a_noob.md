---
title: "using apache as a noob"
date: 2010-01-25
forum: Server Platforms
---

### Post by karimruan on 2010-01-25
I want to set up apache to work with the software found at [http://downloads.webhelpdesk.com/](http://downloads.webhelpdesk.com/) I called tech support their but they don't really help much. Anyway, I already have cherokee which they say is unsupported. They do however support apache. So, I would like to completely uninstall cherokee (unless someone knows how to get it working) and set up apache to allow my customers to connect to my local machine, and view the web help desk page. I know nothing about this whole scene, but was able to get as far as installing and setting up mySQL for web help desk.

Any help is appreciated.I already tried [sudo apt-get remove cherokee] and installed apache2 using apt-get but I still get the cherokee page when viewing local host in firefox. 

Also, I get the following message when installing apache2:

invoke-rc.d: initscript apache2, action "start" failed.

I tried posting this in general support but can't find it anywhere, so I figured I would repost it here. Please, feel free to move if incorrectly posted.


KarimRuan

---

### Post by volkswagner on 2010-01-26
To completely remove cherokee try:

```
sudo apt-get remove --purge cherokee
```

---

### Post by badSheep8 on 2010-01-26
I suppose that if the other server was still running, you wouldn't be able to start Apache if they both run on the default port 80. So unless you completely remove cherokee, you should change the port number in the config file /etc/apache2/apache2.conf .

Once successfully installed and you have problems, you can can check out the error log when you have problems which if I remember well, resides in /var/log/apache/error.log .

---

