---
title: "Ubuntu One is ridiculously slow"
date: 2012-04-29
forum: Ubuntu One (CLOSED)
---

### Post by calavier62 on 2012-04-29
Hey all,

I've been using Ubuntu One since it came about (about two years ago, if I'm not mistaken), and I've never had an issue with it.

For about a year, I was using Fedora as the OS on my laptop, but after I bought a new laptop, and Fedora didn't work right (even after days of tinkering with it), I switched back to Ubuntu.

One of the first things I did, of course, was install Ubuntu One (by the way, why doesn't it come preinstalled anymore?), and I've been trying to download the files that I put on my account. Except, that's basically impossible to do.

The problem is quite simple, and that is I can only get download speeds of anywhere from 2 **bytes** per second to 11 **kilobits** per second. And I know that my internet and LAN connection is set up properly. I can access the web interface fine, however. And downloading files goes through without a hitch.

My internet connection is non-throttled, 18 mb/s average download, 1mb/s upload. And I just downloaded some programs at an average speed of 575 kb/s (according to apt-get). 

I've been using Linux for about 8 years, and my knowledge of networking is nothing small, so all I'm wondering is: what in the hell is up with this? I'm in college, and I don't want to pay for more storage on my dropbox, box.net, or skydrive accounts (all mostly full), and it doesn't appear that I'd be able to do **anything** with my ubuntu one account.

All help is greatly appreciated. Thanks in advance!
-Camden

---

### Post by lazor on 2012-04-29
I have the same problem. Just bought some music through the Ubuntu One music store and now I am waiting for it to finish downloading... at what must be around >2kByte/s.

Oh, and I just looked with

```
~> u1sdtool --current-transfers
```

and the one track that was already at 2MBytes (!!!) after an hour or so just got reset to 0 again.

---

### Post by Rifester on 2012-04-29
You are not the only one.   I purchased a 20 gig upgrade hoping to back up my 16 gig of pictures/videos....  I am not sure this will ever happen.   I am greatly disappointed.  I suppose it is time that I gave Canonical some cash, but I would prefer to have a paid for a service that works.

---

### Post by talexbikes on 2012-04-29
I've been seeing the same issue since Friday, very frustrating when I want to take my work home and it won't sync...

I think the issue is because of the 12.04 release all the canonical servers are being hammered. Not an excuse (who wants their files unavailable for 2 weekends every year), but we can hope it will be resolved soon.

---

### Post by JB1234 on 2012-04-30
> **lazor said:**
> I have the same problem. Just bought some music through the Ubuntu One music store and now I am waiting for it to finish downloading... at what must be around >2kByte/s.

Oh, and I just looked with

```
~> u1sdtool --current-transfers
```

and the one track that was already at 2MBytes (!!!) after an hour or so just got reset to 0 again.

Same issue here, I didn't know about that tool so thanks for mentioning it :)

Just been watching the file progress and it seems *very* small files get downloaded fine but larger files just keep restarting (though the smaller ones aren't exactly downloading that reliably either).

---

### Post by lazor on 2012-04-30
On AskUbuntu there is an answer giving a reason and a time estimate as well as a link to launchpad:
[http://askubuntu.com/questions/128019/ubuntu-one-slow-download-sync-speed/128158#128158](http://askubuntu.com/questions/128019/ubuntu-one-slow-download-sync-speed/128158#128158)

---

### Post by kingofpain on 2012-04-30
I see some of you used Ubuntu One for a long time so I have a question: did it EVER worked?
I know a few months ago I tried it, waited a few hours to sync some files and gave up.
This weekend I tried it again, and for syncing apx. 140MB I've waited about two days (~20h uptime).
Don't know what to say but... Dropbox syncs in minutes.:confused:

---

### Post by lazor on 2012-05-01
> **kingofpain said:**
> I see some of you used Ubuntu One for a long time so I have a question: did it EVER worked?
I know a few months ago I tried it, waited a few hours to sync some files and gave up.
This weekend I tried it again, and for syncing apx. 140MB I've waited about two days (~20h uptime).
Don't know what to say but... Dropbox syncs in minutes.:confused:

I used it to buy music for three times now. Two of which I had to wait for a few days for my music to arrive. It worked fine once though! Still, I am optimistic, I'll just try again in a few months and who knows, maybe they fixed it by then.

---

### Post by ubiquitin.jf on 2012-05-01
> **kingofpain said:**
> I see some of you used Ubuntu One for a long time so I have a question: did it EVER worked?
I know a few months ago I tried it, waited a few hours to sync some files and gave up.
This weekend I tried it again, and for syncing apx. 140MB I've waited about two days (~20h uptime).
Don't know what to say but... Dropbox syncs in minutes.:confused:

It works wonderfully usually. I don't know if that's because I live ~20 miles from where the servers supposedly are, though. They clearly weren't prepared for how popular 12.04 was going to be!

---

### Post by JB1234 on 2012-05-02
I'm pretty sure this issue is resolved now, it is for everyone I know who was affected anyway. Mine actually synced faster than ever yesterday, I'm so impressed I'm considering adding some paid storage!

---

### Post by David Crockett on 2012-05-02
I have found that every once in a while it is rather slow.    It is still amost impossible.   (I have only had problems since Monday)   I put some microscope picutre files to sync two days ago and they still have not gotten up there.

Where are the servers anyway?  Just curious.    

Cheers,
D

---

### Post by BackwardsDown on 2012-05-02
> **David Crockett said:**
> 
Where are the servers anyway?  Just curious.    


Some ubuntuone servers are in the UK, altough I do not know if all of them are.

The data itself is stored on the servers of Amazon S3. They are spread all over the world.

---

### Post by Rifester on 2012-05-03
Just to give an update and credit where it is due...   I have uploaded 17 Gig of pictures and and video (I started the upload last Saturday).   The upload speed doubled in the last two days and finished last night.   My other two computers have been set up and have been set to sync and worked flawlessly.    This will really save me some time with back ups and I am happy to finally pay something for Ubuntu.   I highly suggest downloading the app- indicator mentioned in the the sticky.   The Ubuntu One interface is nice but the fact that it offers no progress while uploading or syncing is a drawback.

---

### Post by David Crockett on 2012-05-09
I too have just purchased 20 gig on Ubuntu one.   It has been working very well of late and it has been very useful for backing up my photomicrographs and distributing them to other work stations and a home computer.    

Happy computing.
David

---

### Post by Starwolf on 2012-05-18
Well basically I have the same problems - I started using Ubuntu One when 12.04 came out, but it is still a slow and unusable as ever :(

What' worse, while it is syncing, it gobbling up all bandwidth, it is virtually impossible to browse the web.

Dropbox works fine though.

---

