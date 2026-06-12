---
title: "audacity with OSS"
date: 2008-12-08
forum: Ubuntu Studio
---

### Post by akwatve on 2008-12-08
Hi,

I am trying to use audacity with OSS4. But I get following error :

> audacity: src/hostapi/alsa/pa_linux_alsa.c:764: BuildDeviceList: Assertion `snd_config' failed.
Aborted

I believe the variable snd_config will be set only if I have ALSA but I don't use it.
I am not sure how to get around this. Why is audacity blindly assuming that I have alsa ?

Thanks,

---

### Post by Stochastic on 2008-12-08
What version of Audacity are you trying to run?  What oss configuration have you done in audacity so far - or does audacity even open fully?  At what point do you get this error?

---

### Post by akwatve on 2008-12-08
Audacity never really starts. If i start it from command line it first asks the following :

> 
Audacity was not able to lock the temporary files directory.
This folder may be in use by another copy of Audacity.
Running two copies of Audacity simultaneously may cause
data loss or cause your system to crash.

Do you still want to start Audacity?

when i click yes it gives the other error i mentioned in my previous post and dies.
if i click no it silently exits.


i have not done any special configuration in OSS for audacity. Audacity version is 1.3.5-2

thanks,

---

### Post by Stochastic on 2008-12-08
Could you post the output of ```
apt-cache policy libasound2
```

My first guess is that the Ubuntu package is built with ALSA enabled as default (the package does depend on libasound2) and that if you want OSS to be used as default, you should compile Audacity from source.

---

### Post by akwatve on 2008-12-09
Here it is :

$ apt-cache policy libasound2
libasound2:
  Installed: 1.0.15-3ubuntu4
  Candidate: 1.0.15-3ubuntu4
  Version table:
 *** 1.0.15-3ubuntu4 0
        500 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) hardy/main Packages
        100 /var/lib/dpkg/status

---

### Post by akwatve on 2009-01-14
In Hardy, I was able to run windows version of audacity using wine successfully. Although this is weird but it works. 

After recent upgrade to Intrepid, things look OK. I will post here if I see similar problem again in Intrepid.

---

