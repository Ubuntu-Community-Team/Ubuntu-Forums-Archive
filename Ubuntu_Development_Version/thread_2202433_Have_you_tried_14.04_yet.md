---
title: "Have you tried 14.04 yet?"
date: 2014-01-29
forum: Ubuntu Development Version
---

### Post by cptrohn on 2014-01-29
I Just wondering if anyone had given it a go?  I did last week and 1 thing that impressed me was that my Display Link usb adapter worked right out of the box, but the system was running VERY slowly with it.  That gives me alot of hope :)   I should have tried it without the adapter connected to see if that was what was causing the slowness though.  But it is still beta though, but I was pleased to see it "just work" nonetheless.

---

### Post by QIII on 2014-01-29
Hello!

Moved to Ubuntu +1.

The Ubuntu +1 subforum is dedicated to the current dev release, which is Trusty right now.  Yes, a lot of us have tried it.  If you want to discuss it in detail, this would be the place.

---

### Post by cchat on 2014-01-29
I have 13.10 now which I only recently installed.  What improvements are there in the new 14.04 that would make it worth upgrading, other than the long support period of a major release?

---

### Post by zika on 2014-01-29
> **cchat said:**
> I have 13.10 now which I only recently installed.  What improvements are there in the new 14.04 that would make it worth upgrading, other than the long support period of a major release?To get decisive answer to this question of Yours You will have to wait 3 months from now to see 14.04. Now, it is just part on drawing board and part on test-bench... ;) Testing-bench is what this forum is part of...

---

### Post by grahammechanical on 2014-01-29
@cptrohn

> [COLOR=#000000]the system was running VERY slowly with it. [/COLOR]

Check to see what video driver you are using. From 13.10 Ubuntu uses as a fall-back video mode llvmpipe which attempts to give 3D effects on video adapters that do not have 3D acceleration. If llvmpipe is running on a video adapter that is capable of 3D acceleration then it does seem to run slowly from what we would normally expect. If we run Recovery Mode>Resume, then we get llvmpipe. Your system may have dropped into llvmpipe. That is what I am thinking.

@cchat

I think the days of noticeable differences from one release to another are over. Ubuntu 13.10 has Unity 7. Ubuntu 14.04 will have Unity 7 which in turn is not so very different from Unity  8 which will be in 14.10 or 15.04 at the latests. There are improvements on the way but I do not think that they will be of the sort that will be instantly noticeable.

The really interesting period will be between the release of 14.04 and the release of 15.04. That is when the convergence strategy will be complete (hopefully). Then we may see the Ubuntu phone/tablet utilities appearing on the Ubuntu desktop alongside or instead of the present utilities. We should also be able to install apps from the Ubuntu app store. The Dash will effectively replace the Software Centre as the means of downloading and installing applications. There is a useful looking music app that could replace Rhythmbox as the default music player. And we already have a Ubuntu Web Browser installed.  

Regards

---

### Post by Cavsfan on 2014-01-29
> **cptrohn said:**
> I Just wondering if anyone had given it a go?  I did last week and 1 thing that impressed me was that my Display Link usb adapter worked right out of the box, but the system was running VERY slowly with it.  That gives me alot of hope :)   I should have tried it without the adapter connected to see if that was what was causing the slowness though.  But it is still beta though, but I was pleased to see it "just work" nonetheless.

IMO it runs very well for the most part. Although like others have said you do not want 14.04 to be the only thing you have until it's in final release in April. If you have a spare partition you could load it up and see.
Ever since I believe it was Precise 12.04, prior to installation, I have to disconnect/turn off my Fantom USB drive. If I don't it tries to read/install there not sure and it hangs for a long time. Since subsequent releases did the same thing I just unmount it and turn it off before I install. That provides much better results. Before it would try to install grub on sdb (USB drive) instead of sda which caused problems.

---

### Post by vicshrike on 2014-01-30
...and looking good at the moment...well worth a try :)

---

### Post by Amorget on 2014-01-30
Installed on my brand new laptop.  Optimus compatibility is greatly improved.  Haven't seen many differences between 13.04 (what I was running on my old laptop) and 14.04.

---

### Post by cptrohn on 2014-01-30
> **grahammechanical said:**
> @cptrohn



Check to see what video driver you are using. From 13.10 Ubuntu uses as a fall-back video mode llvmpipe which attempts to give 3D effects on video adapters that do not have 3D acceleration. If llvmpipe is running on a video adapter that is capable of 3D acceleration then it does seem to run slowly from what we would normally expect. If we run Recovery Mode>Resume, then we get llvmpipe. Your system may have dropped into llvmpipe. That is what I am thinking.

@cchat

I think the days of noticeable differences from one release to another are over. Ubuntu 13.10 has Unity 7. Ubuntu 14.04 will have Unity 7 which in turn is not so very different from Unity  8 which will be in 14.10 or 15.04 at the latests. There are improvements on the way but I do not think that they will be of the sort that will be instantly noticeable.

The really interesting period will be between the release of 14.04 and the release of 15.04. That is when the convergence strategy will be complete (hopefully). Then we may see the Ubuntu phone/tablet utilities appearing on the Ubuntu desktop alongside or instead of the present utilities. We should also be able to install apps from the Ubuntu app store. The Dash will effectively replace the Software Centre as the means of downloading and installing applications. There is a useful looking music app that could replace Rhythmbox as the default music player. And we already have a Ubuntu Web Browser installed.  

Regards

Thanks for the reply, thats very interesting, hmm any ideas on how to disable the llvmpipe?

---

### Post by buzzingrobot on 2014-01-31
I've been checking it out, off and on, using a machine I use for such things.

It seems in pretty good shape and ought to be a very nice, if non-startling, release.  

Still, it's early yet. Stuff happens, so I would not, at the moment, use Trusty as my only system.  For example, I did an install of yesterday's (30 Jan) daily.  Some of the icons in System Settings would not respond to clicks.  System Settings would not close.  Clicking on the close icon just prompted the launch of another version.

Since Settings is being migrated away from the Gnome settings tool it has been based on, behavior like that isn't surprising.  But, if those kind of bumps annoy you, then you probably are not a candidate for running a release still in development.

---

### Post by Amorget on 2014-01-31
> **buzzingrobot said:**
> I've been checking it out, off and on, using a machine I use for such things.

It seems in pretty good shape and ought to be a very nice, if non-startling, release.  

Still, it's early yet. Stuff happens, so I would not, at the moment, use Trusty as my only system.  For example, I did an install of yesterday's (30 Jan) daily.  Some of the icons in System Settings would not respond to clicks.  System Settings would not close.  Clicking on the close icon just prompted the launch of another version.

Since Settings is being migrated away from the Gnome settings tool it has been based on, behavior like that isn't surprising.  But, if those kind of bumps annoy you, then you probably are not a candidate for running a release still in development.

Same issue happened to me.... it was fixed last night, btw.

---

### Post by buzzingrobot on 2014-01-31
> **Amorget said:**
> Same issue happened to me.... it was fixed last night, btw.

Thanks.  Off to update...

---

### Post by sports fan Matt on 2014-01-31
I plan to upgrade because I have another partition running Elementary OS.

---

### Post by nomenkultur on 2014-01-31
I've been using it since buntu SMP Sun Dec 8 23:39:27 UTC, nothing but good things to say about it.

 It has been, so far, the most enjoyable experience I've had with any distro. 

 Stable, snappy and functional... the unity aesthetics are still broken but this is by far the best version of ubuntu canonical has ever released.

 People need to jump into it since the future is murky and with canonical refusing to adopt the technologies that will usher a new age for linux (wayland, systemd, btrfs) this will probably be all we have left.

---

