---
title: "webalizer"
date: 2005-08-17
forum: Server Platforms
---

### Post by SychoSly on 2005-08-17
Can someone please help me setup webalizer so that I can monitor my visitors. I tried setting up awstats but I was getting some problems with that.

I downloaded the binary from the website, and untarred it. I put it in my /var/www/webalizer/ directory.

I copied the webalizer program to /usr/bin and /usr/local/bin

Then everytime I execute it I get the following error:

webalizer: error while loading shared libraries: libpng.so.2: cannot open shared                                                               object file: No such file or directory

I search the apt-cache and didnt find anything that matches libpng.so.2 I did find somethign like libpng12-0 and libpng10-0 I installed those and i still get teh same error.

Any one know what to do. I need somethign to see my logs. Or if anyone knows an easier log file viewer then please tell me.

Thanks.

---

### Post by invalid on 2005-08-17
The easiest way to go about this, would be to install the version (of awstats or webalizer) from your apt sources (using synaptic or apt-get). While you are at this, also grab webmin and the module that goes with it.

From here, it will install itself properly, and you can configure the setting inside webmin.

Cheers,
Cb

---

### Post by SychoSly on 2005-08-17
Is webmin a gui interface? I only have the "server" install of ubuntu, I am doing everything the hardway.

---

### Post by SychoSly on 2005-08-17
I installed webalizer through apt-get and it works. I just had to change the path to the directory where the logs are located.

Now it asks me for the path to the log file. Which one should I link to it:

access.log  - or -  access.log.1  - or -  access.log.2.gz

---

### Post by invalid on 2005-08-17
I personally don't use it, but I think it is wanting the log that is rotated. Check them to see which that is (or check apache documentation).

webmin is a web interface by the way, with access by [https://localhost:10000](https://localhost:10000)

Cheers,
Cb

---

### Post by SychoSly on 2005-08-17
[QUOTE=invalid]I personally don't use it, but I think it is wanting the log that is rotated. Check them to see which that is (or check apache documentation).

webmin is a web interface by the way, with access by [https://localhost:10000](https://localhost:10000)

Cheers,
Cb[/QUOTE]


I would have to access webmin from the actual computer, right? My web server is another physical computer.

Everytime I try to access:  [https://my-domain:10000/](https://my-domain:10000/) I keep gettnig " You are not authorized to view this page....."

---

### Post by invalid on 2005-08-17
You can edit webmin configuration to respond to a list of given IPs (by defauly it is only localhost).

I know this can be done from within webmin.. I am not positive if it is possible to set a configuration file from a terminal, but I would be suprised if it were not possible. I personally have never tried it though.

Cheers,
Cb

---

### Post by mioip on 2005-08-18
[QUOTE=invalid]You can edit webmin configuration to respond to a list of given IPs (by defauly it is only localhost).

I know this can be done from within webmin.. I am not positive if it is possible to set a configuration file from a terminal, but I would be suprised if it were not possible. I personally have never tried it though.

Cheers,
Cb[/QUOTE]
 Honestly, I just copped out and it came with the XAMPP project. [www.apache-friends.org](www.apache-friends.org)
But I'm already too late to chip that in.

---

### Post by Ab3 on 2005-09-01
i setup webalizer from apt-get remotely and it is running without problems. I dont think webmin installation is required, as webalizer will display apache stats as html at [www.xyz.com/webalizer](www.xyz.com/webalizer). One thing though, if you are running apache 2, then change the /etc/webalizer.conf file, to reflect the apache2 logs (default is apache). 
Also, trying to set up a cron job so that webalizer updates itself every night. lets see what happens.

---

### Post by Mujaheiden on 2005-12-10
I think webalizer installs itself standard into cron.daily.

---

### Post by gruepig on 2005-12-10
[QUOTE=Ab3]I dont think webmin installation is required[/QUOTE]

Correct.  Webmin is a web-based interface for all kinds of system administration tasks.  You don't have to use it for webalizer or for anything else.  Just edit the config files (in this case webalizer.conf) directly.

---

