---
title: "Easy Server Q: how to get program loading at startup"
date: 2009-05-06
forum: Server Platforms
---

### Post by kristiaan_d on 2009-05-06
Hi Guys,
i have had a quick search on here can cannot seem to find a definitive way to-do this.

I am running a 9.04 server box as a load balancer. my problem is the program i am using does not load up when you reboot the box. 

I know the old saying about never needing to reboot a Linux box, but i would like peace of mind in case someone in our IT dept takes it upon themselves to restart the box for what ever reason.

i have heard mention that i need to add it to a file called init.d but cannot seem to find this file.

Also the program needs to be run as root to gain access to particular folders and files, so it would be appreciated if any examples of how to-do this would cover running the app as root.

thanks
Kris

apologies if this is in the wrong section.

---

### Post by ikonia on 2009-05-06
Ubuntu uses "upstart" as an init daemon.

The init daemon is what starts things at boot time using "run level"

 ( basic overview is here [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/) )

One method of a simple startup script is to use the rc.local script

this is a file which is executed last on boot up, so the last tasks it does. Startup options can be put in here.

Or you can create your own init script

this is documented here (remember local is just an example script)

[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

---

### Post by kristiaan_d on 2009-05-08
Thanks for the reply regarding this, i took a look at rc.local but i have no clue on scripting in Linux so i figured this might not be the easiest option.


in regards to upstart again this seems overly complicated considering all i want to-do is get Linux to run the following command when the box starts up.

```
sudo xrctl start
```

is there no simple Linux equivalent of the old windows autoexec.bat file??

---

### Post by albinootje on 2009-05-08
> **kristiaan_d said:**
> i took a look at rc.local but i have no clue on scripting in Linux so i figured this might not be the easiest option.

What makes you think that scripting knowledge is required ?
> 
all i want to-do is get Linux to run the following command when the box starts up.
```
sudo xrctl start
```


You can simply put that line in /etc/rc.local *before* the last line (Read the comment inside /etc/rc.local). 
And "sudo" is not needed in that line because /etc/rc.local is executed as "root".
Make sure you add the full path of the application you want to start just to be sure.

---

### Post by kristiaan_d on 2009-05-08
> **albinootje said:**
> What makes you think that scripting knowledge is required ?

If you change to /etc/init.d/ and then sudo nano rc.local the file is full to the brim of what i can only assume is linux script, this is why i thought i would need to have an idea of scripting. from what i read about the location of rc.local and what you mention below it appears i had the wrong file.

> **albinootje said:**
> 
You can simply put that line in /etc/rc.local *before* the last line (Read the comment inside /etc/rc.local). 
And "sudo" is not needed in that line because /etc/rc.local is executed as "root".
Make sure you add the full path of the application you want to start just to be sure.

Thanks for this, exactly what i wanted, will give it ago now, hopefully this will be the end of my troubles :)

thanks
kris

---

### Post by albinootje on 2009-05-08
> **kristiaan_d said:**
> If you change to /etc/init.d/ and then sudo nano rc.local the file is full to the brim of what i can only assume is linux script
I see, you're right about that, /etc/init.d/ is full of bash scripts.
Luckily you can use /etc/rc.local for simple things.

---

