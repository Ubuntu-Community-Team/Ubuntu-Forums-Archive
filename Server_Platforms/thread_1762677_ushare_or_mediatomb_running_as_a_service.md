---
title: "ushare or mediatomb running as a service?"
date: 2011-05-19
forum: Server Platforms
---

### Post by w1n78 on 2011-05-19
all the tutorials i found for ushare and mediatomb shows it installed on desktop and not server. it also requires an account to be logged in. once logged it, you have to run a command to start it up. some questions...

1) is there a way to run either one w/o having to log into an account? so if say i restarted the server, it'll run the programs w/o me having to log in.

2) i would like to specify a directory to share music and movies. is one better than the other? clients that i plan to use are songbird, itunes (maybe), and vlc - maybe xbox 360 and ps3. other client suggestions?

3) other dlna server suggestions? this will be running on ubuntu 10 or 11 desktop or server. but the main thing i'm looking for is what i mentioned in #1.

thanks

---

### Post by arrrghhh on 2011-05-19
Mediatomb can easily be run as a service, in fact if you install it from the repo's, it should already include an init.d script...

Also, I prefer ps3mediaserver - I do have a PS3, not sure how well it works with other devices, but compared to mediatomb and ushare, ps3mediaserver works SO much better (again, for my PS3...)  It should work just fine for other devices, it is a standards-compliant DLNA streaming service.

---

### Post by w1n78 on 2011-05-19
i installed PMS but i'm getting an error 

Media renderer was not recognized. HTTP User agent: Mozilla/5.0 (X11; Linux x86_64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1

i'm googling it now and trying to figure it out. so far no luck but looks good. i'll continue to try mediatomb if this doesn't work out. thanks

> **arrrghhh said:**
> Mediatomb can easily be run as a service, in fact if you install it from the repo's, it should already include an init.d script...

Also, I prefer ps3mediaserver - I do have a PS3, not sure how well it works with other devices, but compared to mediatomb and ushare, ps3mediaserver works SO much better (again, for my PS3...)  It should work just fine for other devices, it is a standards-compliant DLNA streaming service.

---

### Post by arrrghhh on 2011-05-19
> **w1n78 said:**
> i installed PMS but i'm getting an error 

Media renderer was not recognized. HTTP User agent: Mozilla/5.0 (X11; Linux x86_64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1

i'm googling it now and trying to figure it out. so far no luck but looks good. i'll continue to try mediatomb if this doesn't work out. thanks

See [this thread](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589&sid=b62c3f172e6266dba9aa553da49a0423) on PS3MediaServer.  Makes the initial setup/install a breeze...

---

