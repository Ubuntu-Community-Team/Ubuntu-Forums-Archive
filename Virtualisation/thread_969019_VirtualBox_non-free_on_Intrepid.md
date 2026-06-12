---
title: "VirtualBox non-free on Intrepid?"
date: 2008-11-03
forum: Virtualisation
---

### Post by speedsix on 2008-11-03
While the repos isn't listed on the official site, the repos is there. The problem is, when I add it to Synaptic, refresh, nothing shows except the regular OSE from the Ubuntu repos?

Any ideas why?


Thanks

---

### Post by FrostyFlames on 2008-11-03
You can download the .deb file from the official site and it should install just fine.

---

### Post by tuxxy on 2008-11-03
You should download the virtualbox-2.0 PUEL licensed version, this is available from the virtualbox website aswell, the repos only contains the open source OSE version i think but you could check search for virtualbox-2.0

---

### Post by grim4593 on 2008-11-03
The non-free repos are on this page:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I just used the Hardy repos they have listed.

---

### Post by HotShotDJ on 2008-11-03
Do NOT use the Hardy repository in Intrepid.  It is not necessary. Use the proper repository:```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

```Don't forget to import the PGP Public key from [HERE]("http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc").

Now, to answer the OP's actual question (which had nothing to do with using the hardy repositories):

I've noticed that packages from third-party repositories (like virtualbox.org) do NOT show up when you use quick search in Synaptic.  Use the Search button -- it will then show up for you.  Just make sure that you refresh the repositories after making changes by using the "Reload" button in Synaptic.

---

### Post by speedsix on 2008-11-03
I've installed the deb directly from the site now (it's not listed but just changed hardy for intrepid in the url)

Interesting point about the quick search, I'll have to test that theory out.

---

### Post by And6ate9 on 2008-11-03
What's the PGP key used for? Apt secure?

oh never mind I see it now

---

### Post by grim4593 on 2008-11-03
> **HotShotDJ said:**
> Do NOT use the Hardy repository in Intrepid.  It is not necessary. Use the proper repository:```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

```

Well, I said to use the hardy repo since Intrepid is not listed as an option on the download page I [linked]("http://www.virtualbox.org/wiki/Linux_Downloads"). Yes, if you browse to [http://download.virtualbox.org/virtualbox/debian/dists/](http://download.virtualbox.org/virtualbox/debian/dists/) it lists Intrepid as an option, but how do you know it is ready? I am assuming there is a reason its not listed on the official page yet. I mean, Intrepid JUST came out.

---

### Post by HotShotDJ on 2008-11-03
> **grim4593 said:**
>  but how do you know it is ready? I am assuming there is a reason its not listed on the official page yet. I mean, Intrepid JUST came out.All I can tell you is that it is installed and working perfectly on my system (Vista Home Premium as guest on Intrepid). Why not on the official page?  Perhaps the web master just hasn't gotten around to it.  Who knows.  But since changing the version name (hardy to intrepid) is a pretty standard procedure, I think it is safe to use the repository.  If it weren't ready, the repository wouldn't be there at all.  Just my humble opinion -- Works for me, YMMV -- all the standard disclaimers. :)

---

### Post by reader4 on 2008-11-11
It's true about the third-party repos... use the full search for these.  Also, they will not always show on the "upgradeable" etc. lists.

---

