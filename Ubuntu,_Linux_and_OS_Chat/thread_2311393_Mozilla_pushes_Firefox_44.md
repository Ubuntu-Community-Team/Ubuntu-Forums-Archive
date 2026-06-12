---
title: "Mozilla pushes Firefox 44"
date: 2016-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2016-01-26
Just wanted to get a cheap pun in re. the push notifications feature in Fx 44:
[http://venturebeat.com/2016/01/26/firefox-44-arrives-with-push-notifications-that-sites-can-send-even-after-users-close-the-page/](http://venturebeat.com/2016/01/26/firefox-44-arrives-with-push-notifications-that-sites-can-send-even-after-users-close-the-page/)
and
[https://blog.mozilla.org/blog/2016/01/25/firefox-can-now-get-push-notifications-from-your-favorite-sites/](https://blog.mozilla.org/blog/2016/01/25/firefox-can-now-get-push-notifications-from-your-favorite-sites/)

And how to turn them off: [http://www.trishtech.com/2016/01/how-to-disable-web-push-notifications-in-firefox/](http://www.trishtech.com/2016/01/how-to-disable-web-push-notifications-in-firefox/)

---

### Post by mikodo on 2016-01-27
Vasa1.

Thank you!

---

### Post by yoshii on 2016-01-27
Such an annoying desing flaw, oops, "feature"(?!).  
Thanks for the link to how to permanently disable it.  
I have an addon that disables it but it's nice to know how to do it manually.

---

### Post by mikodo on 2016-01-29
So, I really don't understand push notifications. I seem to not use any. In FF v43 and continuing in v44 now,** dom.push.enabled ****= false **remains default. It says from [here]("http://venturebeat.com/2016/01/26/firefox-44-arrives-with-push-notifications-that-sites-can-send-even-after-users-close-the-page/"), "*Firefox only connects to the Push Service if you have an active Web Push  subscription. This could be to a website, or to a browser feature like  Firefox Hello or Firefox Sync*". So, not knowing about "push notifications", I checked my FF Sync, to see if it is updated. It was today while I am now on v44. I guess _not_ having dom.push.enabled doesn't effect the syncing. 

This post, is just in case anyone else was wondering about FF Sync without having the push enabled. That is my experience with it.

Well, ~ 8hrs later. I restarted Firefox, and all my addons were disabled. Firefox was displaying "a program or something wants to install basically all my addons. I didn't let it, closed firefox, then checked if dom.push.enabled = true by default and it _was_. I set it again to false myself this time as user set. I reinstalled my addons and unfortunately I hadn't checked what was up with FF Sync before changing back the push enabled to false. I checked after setting push enabled to false and Sync showed that it had just Synced. So maybe it had effected Sync but I don't know for sure.  :(

---

### Post by vasa1 on 2016-01-30
> **mikodo said:**
> So, I really don't understand push notifications. I seem to not use any. ...
> As part of Mozilla’s mission to promote openness, innovation and opportunity on the Web we not only make our own products, like Firefox, but work on technologies that will benefit the entire Web ecosystem. We do this because we want the Web to reach its full potential and grow with interoperable and consistent experiences for both users and developers. This includes experimenting with Service Workers and other technologies that enable a new design pattern known as **Progressive** Web Apps -a key next step in the Web Apps story.
[Source]("https://blog.mozilla.org/futurereleases/2015/11/17/extending-the-webs-capabilities-in-firefox-and-beyond/")
;)

---

### Post by mikodo on 2016-01-30
> **vasa1 said:**
> [Source]("https://blog.mozilla.org/futurereleases/2015/11/17/extending-the-webs-capabilities-in-firefox-and-beyond/")
;)

Vasa1. I was typing when you made your post. You may not have seen my addition to that post of mine you linked.

---

### Post by vasa1 on 2016-01-30
> **mikodo said:**
> Vasa1. I was typing when you made your post. You may not have seen my addition to that post of mine you linked.
I never ever synced Firefox. By not syncing I have a clear separation of stuff. Of course, I back up all my profiles. I guess it is possible to sync *and* to keep things separate but that would take some patience and experimentation.

(Google I sync, because I don't use it that much except for storage)

---

### Post by mikodo on 2016-01-30
> **vasa1 said:**
> I never ever synced Firefox. By not syncing I have a clear separation of stuff. Of course, I back up all my profiles. I guess it is possible to sync *and* to keep things separate but that would take some patience and experimentation.
Well, of course! I never thought of that, and here I was thinking I was keeping things separate with different FF profiles for different tasks.

I'll stop syncing now. I have my FF profiles backed up too, I just thought Sync was a nice feature, for new installs. Duh!

Thank you.

---

