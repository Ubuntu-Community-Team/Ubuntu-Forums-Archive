---
title: "Latest Chromium update from UNOFFICIAL PPA requesting weird permissions"
date: 2013-01-30
forum: Security
---

### Post by Stonecold1995 on 2013-01-30
The official Chromium PPA is no longer maintained, so Alex somethingorother made an unofficial PPA that he keeps updated, and that's the PPA I'm using.  However, for a while, he no longer updated his PPA, but just recently the first update in a while came out (Chromium 26.0.1386.0).  I installed it, but it's requesting weird AppArmor permissions.

These are the lines I had to add to my AppArmor profile to allow Chromium to start (without this it exits with a segmentation fault):
```
  /usr/bin/lsb_release ixr,
  /etc/lsb-release r,
  /etc/python3.2/sitecustomize.py r,
  /etc/debian_version r,
  **/usr/bin/apt-cache ixr,**
  **/etc/apt/apt.conf.d/* r,**
  /sys/devices/pci0000:00/0000:00:1f.2/ata5/host4/target4:0:0/4:0:0:0/block/sdb/sdb1/size r,
  **/etc/apt/sources.list r,**
  /var/cache/apt/pkgcache.bin r,
  **/usr/bin/dpkg ixr,**
  **/etc/apt/sources.list.d/* r,**
  /etc/dpkg/dpkg.cfg r,
  /var/lib/dpkg/arch r,
  /var/cache/apt/srcpkgcache.bin r,
  /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_main_binary-amd64_Packages r,
  /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_restricted_binary-amd64_Packages r,
```The lines that concern me the most are in bold.  Now why would a Chromium PPA which has been dormant for a little while, suddenly start requesting access to a bunch of package installation-related files, when it never needed to before?  What's especially concerning is that it requires execution access to dpkg, and read access to *every* PPA list file in /etc/apt/sources.list.d/.

Could the unofficial PPA be compromised?  Am I safe allowing it to access these things?

---

### Post by Hungry Man on 2013-01-31
Did you download a file with Chromium and attempt to run it from the browser? Probably a .Deb or something.

Otherwise, no idea. That's why I don't use unofficial repos.

---

### Post by Stonecold1995 on 2013-01-31
> **Hungry Man said:**
> Did you download a file with Chromium and attempt to run it from the browser? Probably a .Deb or something.
No, this was with trying to start Chromium up at all.  After the update, with AppArmor still active, trying to run Chromium would cause an immediate segmentation fault.

> **Hungry Man said:**
> Otherwise, no idea. That's why I don't use unofficial repos.
The official PPA for Chromium is no longer updated and very out of date, the unofficial one is the only one that actually works.

---

### Post by Hungry Man on 2013-01-31
Yeah, that's why you should use Chrome. It's maintained by a reputable source.

---

### Post by Stonecold1995 on 2013-01-31
Another reason I fear the PPA is compromised: I cannot access settings.  On chrome://settings, I can go to Extensions and History, but if I go to Settings the page stays blank.

**EDIT:** That seems to be a bug, I can view settings by typing something into the Search Settings field, then deleting it.
[http://www.pictureshack.us/images/10946_settings01.gif](http://www.pictureshack.us/images/10946_settings01.gif)

Is there any way I can get into contact with the PPA maintainer?

> **Hungry Man said:**
> Yeah, that's why you should use Chrome. It's maintained by a reputable source.
I don't trust Chrome because of it's tracking features and partial closed-sourceness.

---

### Post by craig10x on 2013-01-31
Chrome is way better then Chromium...you get newer editions, gets updated faster, puts an updater in your software sources that send new versions down through your software updater...

It also has it's own flash plug in and a pdf reader so you can read pdfs right in your browser without downloading them (though you can do that too if you wish by right clicking and saving)...

Just a whole slew of plus features...I wouldn't be concerned about tracking...not that big a deal...

---

### Post by Stonecold1995 on 2013-01-31
> **craig10x said:**
> Chrome is way better then Chromium...you get newer editions, gets updated faster, puts an updater in your software sources that send new versions down through your software updater...

Actually Chromium updates faster and has the newest features out first (eventually Google puts features in Chrome, but only after they've been through Chromium), the only problem is with the repo not being maintained correctly.

> **craig10x said:**
> It also has it's own flash plug in and a pdf reader so you can read pdfs right in your browser without downloading them (though you can do that too if you wish by right clicking and saving)...
I put PDF and Flash plugins on Chromium, so that all works as well.

> **craig10x said:**
> Just a whole slew of plus features...I wouldn't be concerned about tracking...not that big a deal...
It's not just the tracking.  Chrome has a nasty EULA, whereas Chromium doesn't (I tend not to trust monopolies' versions as much as I do community maintained versions).

---

### Post by craig10x on 2013-01-31
ever do a search on yahoo or google, etc...they track you too!
so unless you have never done a search ever...odds are you are being tracked...all that is used for is to target the ads to be appropriate for things you often search for...no evil intentions...

hey..i like microsoft fonts and when i download ubuntu restricted extras i have to agree to the ms license, otherwise they don't get installed...also not a big deal...but whatever "floats your boat" as the old saying goes... :P

---

### Post by Stonecold1995 on 2013-01-31
> **craig10x said:**
> ever do a search on yahoo or google, etc...they track you too!
so unless you have never done a search ever...odds are you are being tracked...all that is used for is to target the ads to be appropriate for things you often search for...no evil intentions...

I don't use Google or Yahoo, I use Startpage for that very reason, as well as a VPN and the DNT+ extension to block tracking cookies, as well as having all third party cookies disabled by default.  I just don't like using a browser that sends everything typed in the Omnibox to Google, along with an ID that identifies you.  Plus I don't think they are doing it for "evil" purposes, but it opens up the huge potential for abuse by governments, corporations, etc.

---

### Post by bodhi.zazen on 2013-01-31
> **Stonecold1995 said:**
> I don't use Google or Yahoo, I use Startpage for that very reason, as well as a VPN and the DNT+ extension to block tracking cookies, as well as having all third party cookies disabled by default.  I just don't like using a browser that sends everything typed in the Omnibox to Google, along with an ID that identifies you.  Plus I don't think they are doing it for "evil" purposes, but it opens up the huge potential for abuse by governments, corporations, etc.

You do understand that by doing all that you stand out like a sore thumb. It makes you easier to track, lol

[https://panopticlick.eff.org/](https://panopticlick.eff.org/)

[https://panopticlick.eff.org/browser-uniqueness.pdf](https://panopticlick.eff.org/browser-uniqueness.pdf)

---

### Post by Stonecold1995 on 2013-01-31
> **bodhi.zazen said:**
> You do understand that by doing all that you stand out like a sore thumb. It makes you easier to track, lol
Having a large amount of "unique" browser information is a LOT better than having my IP address out and tracking cookies allowed, because my IP identifies me perfectly and across sites, whereas browser "signatures" only identifies me across sites, and without perfect accuracy.

I really don't understand how you'd think it would be better to just try and "blend in" with the crowd than to take steps to protect privacy.  Security through obscurity never works well.

---

### Post by bodhi.zazen on 2013-01-31
> **Stonecold1995 said:**
> Having a large amount of "unique" browser information is a LOT better than having my IP address out and tracking cookies allowed, because my IP identifies me perfectly and across sites, whereas browser "signatures" only identifies me across sites, and without perfect accuracy.

I really don't understand how you'd think it would be better to just try and "blend in" with the crowd than to take steps to protect privacy.  Security through obscurity never works well.

That is exactly my point, you are thinking old school. ip addresses do not identify you, ip addresses are often dynamic and changing.

You are identified by the information your browser does or does not send. The less information you send the more unique you are, lol.

Try it

---

### Post by Stonecold1995 on 2013-01-31
> **bodhi.zazen said:**
> That is exactly my point, you are thinking old school. ip addresses do not identify you, ip addresses are often dynamic and changing.

You are identified by the information your browser does or does not send. The less information you send the more unique you are, lol.

Try it

Yes they are dynamic, but your ISP records what IP is attached to what account at what time, so for security purposes, a dynamic IP won't help much.  To say that trying to remain anonymous makes you LESS anonymous sounds like bull.

Also, I have a static IP anyways.

---

