---
title: "This morning's 70MB OpenOffice update..."
date: 2008-05-07
forum: The Cafe
---

### Post by Phil Airtime on 2008-05-07
...why?!

Some of us have internet connections that could generously be described as lethargic. Mine, for example, lurches nauseatingly between 2Mbps and 256kbps, tending towards the latter thanks to the UK's frankly knackered phone network. Fine if an update is 5-10MB or so, but 70MB of downloads to fix one bug seems a little excessive. It isn't just speed, either; many people are on internet connections that severely limit what they can download in a month. And I'm sure Ubuntu's servers could do without the hammering.

Surely there's some better way of managing updates rather than this humongous re-download of an entire app. If there isn't, perhaps Ubuntu should consider bundling an office app that isn't OpenOffice!

PS. I'm still using Feisty; perhaps this update is just for that version.

---

### Post by SupaSonic on 2008-05-07
Hmm. If Gentoo is source based, than to fix the bug one would need to change the source file which would be like a couple KB and recompile the whole thing. That's in theory, I actually never used Gentoo.

Apt downloads debs which are binary. So an updated version of openoffice with even one line of code changed would still be 70 MB. 

Anyway, might as well not download updates at all. I almost never use openoffice for instance, so if my dl speed was low I just wouldn't download the update.

---

### Post by Phil Airtime on 2008-05-07
I tend to use OpenOffice fairly irregularly, too; if I'm writing something destined for digital delivery such as email or a blog post, I tend to use Zoho Writer on the browser. That way, I can't lose the document by losing my USB stick! (I can't be the only one who does this on an alarmingly regular basis.) OpenOffice only ever tends to come out when I'm writing something directly for print, such as a quick snailmail letter. Gentoo sounds like they might have the answer in downloading a small patch file to add to the offending app, but it has a bit of a scary, techie reputation...!

---

### Post by insane_alien on 2008-05-07
IIRC there are develpers looking into a way to have a deb just change a couple of files in the package. this will probably take some time to come to maturity but should reduce update sizes.

---

### Post by mivo on 2008-05-07
I haven't gotten that update for Hardy, so may be only for Feisty and other previous releases. Or it may not yet have prompted me, but updates usually occur in my morning also.

---

### Post by Raven_Oscar on 2008-05-07
Well there is delta RPM in some RPM based distributions. All you need to update any package in such distro is to download only part of original package. But it is in theory.

---

### Post by bikeboy on 2008-05-07
> **Phil Airtime said:**
> Gentoo sounds like they might have the answer in downloading a small patch file to add to the offending app, but it has a bit of a scary, techie reputation...!

Note what the other poster said about having to recompile. It could take in the order of hours longer than the 70 mb download depending on how powerful your machine is. Someone please correct me if I'm wrong.

---

### Post by Half-Left on 2008-05-07
70mb dont take long at all on a 2Mbp connection(which is what I have), change your server or uninstall it if you dont use it.

---

### Post by Phil Airtime on 2008-05-07
> **Half-Left said:**
> 70mb dont take long at all on a 2Mbp connection(which is what I have), change your server or uninstall it if you dont use it.

My connection fluctuates wildly, though. You know those convoluted "IP Profiles" you get on British ADSL Max connections? Mine has its rare moments of brightness at 2000kbps, but for the vast majority of the time it's stuck at either 250kbps or 500kbps. I'm sure it's an underhand way of stopping people using too much bandwidth, I don't think they have them in other countries. I can live with it most of the time, although even heavier web pages such as forums and the new BBC site are sluggish at 256kb, but things like Google Earth, YouTube or even some internet radio stations are non-starters. 70MB suddenly seems pretty big!

---

### Post by ynnhoj on 2008-05-07
do you ever use the other bits of openoffice (calc, impress, etc)?  if not, you might as well turf it and install abiword.  if you occasionally need to work with spreadsheets, you can install gnumeric too.

---

### Post by Kingsley on 2008-05-07
Apt-get needs something like yum-presto.

---

### Post by K.Mandla on 2008-05-07
Download it elsewhere and install it manually ... ?

---

### Post by [h2o] on 2008-05-07
Isn't there an option to not install the suggested updates? Feisty was some time ago, but surely you were asked before the download began?

---

### Post by sports fan Matt on 2008-05-07
I didnt get those updates from OOO...

---

### Post by blithen on 2008-05-07
Thank god I don't use OO, Abiword for me.

---

### Post by Miguel on 2008-05-07
All those OOo downloads are a fix of a vulnerability in hsql and OOo <2.4.0. That's why Hardy users didn't have to download anything.

If you are complaining about download sizes, you won't like to hear that most packages downloaded in security updates are identical to the previous one safe a version number. In the case of updates to complex pieces of software, like OOo or nautilus, the version number of intimately related packages are also bumped by a bit to ensure dependency hell is controlled and that everybody is running more or less the same packages. 

As an example, let's say there is a bad string in nautilus-data, and that it is absolutely required to fix it. In this case, it's very likely that you'd have to download nautilus and libnautilus-extension1, even though these have only changed their version numbers.

---

### Post by Phil Airtime on 2008-05-07
> **'[h2o] said:**
> Isn't there an option to not install the suggested updates? Feisty was some time ago, but surely you were asked before the download began?

You can choose not to download them, but then you get that silly little red icon in the corner of your screen all the time. I left them downloading earlier while I went out, but it took a while to do! I'd install Hardy, but I want to try it in a VM to make sure everything works as it should first. (I'm looking at you, Firefox fonts.)

---

### Post by mivo on 2008-05-07
I had a hell of a time with browser fonts in Gutsy and spent hours tweaking and fiddling around. I'm happy to say that browser fonts in Hardy worked out of the box and I didn't have to tweak anything at all. :) (It was a clean install, but I had my old font config backuped, just in case, but it wasn't needed.)

---

### Post by SuperSon!c on 2008-05-07
> **blithen said:**
> Thank god I don't use OO, Abiword for me.

one of these days you'll need more than just a word processor.  shhh.  yes, you will.

---

### Post by Acglaphotis on 2008-05-07
Now im depressed... my connection tops at 100kb/s.

---

### Post by Tom Mann on 2008-05-07
I like the point this guy is making - could it not be feasible for delta versions of applications where the package would point to a reference .deb and only update specific files from there?

i.e. 
- Mozilla Firefox 3 beta 5 is the standard package in Hardy.
- Beta 6 comes out, with several bug fixes. The package says that it's installation is dependant on the previous version being available.
- Anyone who installs Firefox on, say Kubuntu (where it'd be a fresh installation) would find apt would download both 3b5 and the 3b6 update, and apply 3b6 to 3b5.
- In the future Mozilla Firefox 3 final comes out, the beta packages (both initial and delta) are removed from the repositories and the final version takes it's place, apt would respond like it does now to this.

---

