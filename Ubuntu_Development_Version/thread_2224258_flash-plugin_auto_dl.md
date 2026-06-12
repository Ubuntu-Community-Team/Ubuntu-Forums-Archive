---
title: "flash-plugin auto dl?"
date: 2014-05-15
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-05-15
flashplugin auto installed (or updated) today with updates.

Don't recall seeing this.

```

flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.359.orig.tar.gz

```

---

### Post by fjgaude on 2014-05-15
I can't say if I've seen it before 14.04 but 14.10 both have the same thing going on. Has to do with upgrading Chrome Stable? Nothing that's an issue AFAIK.

---

### Post by ventrical on 2014-05-15
> **fjgaude said:**
> I can't say if I've seen it before 14.04 but 14.10 both have the same thing going on. Has to do with upgrading Chrome Stable? Nothing that's an issue AFAIK.

Youtube is still working fine but I can't get my CBSNews videos.

---

### Post by Cavsfan on 2014-05-15
I believe this has been happening since 14.04 like          fjgaude mentioned. I always use CLI so I see every update *usually*.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy flashplugin-installer
flashplugin-installer:
  Installed: 11.2.202.359ubuntu1
  Candidate: 11.2.202.359ubuntu1
  Version table:
 *** 11.2.202.359ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/multiverse amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Cavsfan on 2014-05-15
YouTube works fine but I could not get CBS news videos to come up no matter what I do.
NBC, ABC news videos no problemo. Must be something with the CBS news site.

---

### Post by Cavsfan on 2014-05-15
As a matter of fact I have not found a video I couldn't watch except CBS News. Couldn't even get the site up let alone any videos. :p

---

### Post by cariboo on 2014-05-15
There is something definitely wrong with the CBS News site, as I can't get it to fully load, and it took a very long time to connect to the site.

---

### Post by ventrical on 2014-05-15
++1,1!

Thats a first! Iv'e been using cbsnews for years with never a glitch. Wonder if it is a bigger security problem across the board. (not talking about ubuntuforums).

all I get is spin..

---

### Post by ventrical on 2014-05-15
Sorry to be off topic but it says that the website is reachable but that it is 'probably just down for you'!

Wha!?

 I'm going to try a stable install.



[URL="http://www.isitdownrightnow.com/cbsnews.com.html"]http://www.isitdownrightnow.com/cbsnews.com.html


[/URL]

---

### Post by ventrical on 2014-05-15
Stable install will not work  cbsnews either. Looks like a major hack job.

---

### Post by ventrical on 2014-05-15
@cavsfan

Are you in Canada?

---

### Post by ventrical on 2014-05-15
xcuse me .. Could somebody from the UK or US check to see if cbsnews.com  is up.

Thanks.

---

### Post by howefield on 2014-05-15
From the UK, same result as cariboo907.

---

### Post by ventrical on 2014-05-15
+1 .. thanks.

---

### Post by EnglishElectricAndy on 2014-05-15
UK here, and my 'Down for everyone or just me' tester reports that cbsnews.com is up, it's just me.

And I'm not even a bleeding edge type, just an interested amateur spectator.

---

### Post by ventrical on 2014-05-15
Thanks electric andy.

 Looks like a bigger problem with server.

---

### Post by ventrical on 2014-05-15
Flash works fine on other sites.

Marking this thread as solved.

---

### Post by sammiev on 2014-05-15
I'm from Canada but use a US vpn and I have no problem with cbsnews.com and flash.

---

### Post by cariboo on 2014-05-16
The site is back up for me, and videos work without any problems.

---

### Post by ventrical on 2014-05-16
Thanks you guys.

---

### Post by Cavsfan on 2014-05-16
Yeah me too. The site is back up. I'm from the US and it was definitely down yesterday. 
I just tried cbssports and then cbsnews and both are good.

---

### Post by jerrylamos on 2014-05-17
CBS News video running O.K. here.  Note, this is Utopic updated every day.  I'm using Google Chrome browser with whatever Google Chrome uses for flash.

I do think Google Chrome video's definitely go slower and jerky with more tabs open.  Likely some problem with multi-tasking.

"Fastest" video I have here is debian wheezy live with wattOS which comes with Firefox flash installed.  The .iso is smaller than Ubuntu about a CD in size, 32 bit fitting on a CD while 64 bit is perhaps a bit over so I'm using USB, with a variety of desktops I'm using LXDE version like Lubuntu.  I do have utopic Lubuntu live but haven't done a comparison yet, and of course Ubuntu doesn't come with flash installed, it is available from synaptic.

---

