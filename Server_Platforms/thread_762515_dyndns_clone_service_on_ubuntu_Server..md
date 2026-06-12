---
title: "dyndns clone service on ubuntu Server."
date: 2008-04-22
forum: Server Platforms
---

### Post by masterqmax on 2008-04-22
Hi guys

My first post so please don't kill me if this has been discussed before, I did search the forums but could not quite find what I was looking for.

I want to host a dynamic dns service like the free service hosted by dyndns.com It would service only a few users I want to provide it free as a value add, the reason for me trying to do this is there has been various requests for this from allot of my clients, who want to have static hostnames from dynamic ip's provided by their isp's on their dsl service. But do to some restrictions with their accounts they can only access local sites. So they are unable to resolve dyndns.com, to do updates using ddclient and the like. 

I have read a great post on the forums about setting up dns using bind and some reference to dynamic dns but every thing I read there has some explicit reference to dhcp as well, I cant provide them with IP's via dhcp because they are on dsl from different providers... My idea was to provide them with a client (ddlcient or custom) so they will be able to update their ip;s.

Can anyone point me in the right direction, a tutorial some advice or simply tell me if it is possible or not? 

Thank you in advance!

---

### Post by ikonia on 2008-04-22
you don't need dhcp, bind (for example) can accept dynamic dns updates, so all you need to do is setup bind (or an other dns service) as a dynamic dns zone for your clients, then get your clients to update your dns servers when their ip's change.

On a side note, I really don't see this as a good idea to be offering this service, the headache of it may prove troublesome, and if you are unable to get clients to use the bind updater successfully (eg: windows clients) you'll have to start writing and maintaining a front end to your clients zone files, then start dealing with security etc etc.

---

### Post by masterqmax on 2008-04-22
> **ikonia said:**
> you don't need dhcp, bind (for example) can accept dynamic dns updates, so all you need to do is setup bind (or an other dns service) as a dynamic dns zone for your clients, then get your clients to update your dns servers when their ip's change.

On a side note, I really don't see this as a good idea to be offering this service, the headache of it may prove troublesome, and if you are unable to get clients to use the bind updater successfully (eg: windows clients) you'll have to start writing and maintaining a front end to your clients zone files, then start dealing with security etc etc.

Hi, Thanks for the reply, I read some nice tutorials, and think I get it now!

This helped 
[http://idefix.net/~koos/dyndnshowto/dyndnshowto.html](http://idefix.net/~koos/dyndnshowto/dyndnshowto.html) 

This one was very good too:
[http://forums.knownhost.com/showthread.php?p=6281](http://forums.knownhost.com/showthread.php?p=6281)

So I will be looking into it, I hear you on the front end, but at this stage everybody is running ubuntu7.10 so they will have access to nsupdate. but this is more of an experiment to see if I can get it up and running! 

Will post on my progress.

---

### Post by masterqmax on 2008-04-22
My next task would be to find out what type of hardware I will need, I have a 2ghz machine at moment, in terms of processing I think it would be just fine, but memory is the problem, at this stage it only has 64Mb of memory? 

Would this be sufficient, I will also be hosting a few medium-ish traffic sites(2 at the moment may increase to 4) on it and running LAMP setup with 6.06 LTS. If I have about 20 clients updating dns, would 64mb ram be sufficient?

---

