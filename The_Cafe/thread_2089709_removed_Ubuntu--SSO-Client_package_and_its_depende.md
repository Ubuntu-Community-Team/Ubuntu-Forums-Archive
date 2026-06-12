---
title: "removed Ubuntu--SSO-Client package and its dependencies today (solved my problem :)"
date: 2012-11-30
forum: The Cafe
---

### Post by LABcqX on 2012-11-30
Not only did removing the ```
python-ubuntu-sso-client
``` package and all its dependencies fix the problem I was having of having keyring windows constantly popup for no reason whenever I use ubuntu, but it also gave my computer a noticeable speed-boost. the system is a little less sluggish overall now. I think this is mostly do to less RAM being needed without the SSO working in the background.

I was hesitant about removing the SSO-client and avoided doing it for a while because it necessitated removing the ```
ubuntu-desktop
``` package. But I've gotten pretty sick of the SSO packages so I finally went ahead with it.

Removing the dependencies also meant removing the ```
software-center
``` package. but a friend showed me this other package called ```
synaptic
``` And it is much preferable so I just use that instead of the software-center. Synaptic is better actually. It is kinda disappointing that the ubuntu chooses the software-center over Synaptic. I think it much better to make the software-center to be just for browsing for new software, kind like a shopping site. But to accomplish the package management, users will do it better to use the Synaptic.

I'm brand new to the ubuntu and still learning how it works. I can be much happier without the SSO packages. I'm glad these packages are allowed to be removed. I guess I won't be able to upgrade without the ubuntu-desktop package so I guess I just backup and then do a CD new install if I need to update the ubuntu version.

I don't use any of the SSO services. Truthfully, I strongly dislike the idea of apps themselves being able to sign into the ubuntu services (or even asking/prompting to sign them into a service). I want me (myself) to manually sign-in if and when I decide sign-in is needed. Apps shouldn't prompt for this. The keyring shouldn't prompt for this. It is bad design in my estimation.

Anyone else in my position that isn't using SSO may want to do the same.

---

