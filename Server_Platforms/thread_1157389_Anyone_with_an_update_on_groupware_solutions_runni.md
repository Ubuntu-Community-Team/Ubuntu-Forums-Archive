---
title: "Anyone with an update on groupware solutions running on Ubuntu?"
date: 2009-05-12
forum: Server Platforms
---

### Post by Macchi on 2009-05-12
I have to confess that the promise of a holy grail appeals to me. 
Specially if it is a nice _Open Source Groupware_ running on an Ubuntu server.

Has anyone an update of the status of latest groupware solutions that run nicely on Ubuntu? 
I have previously tested conflux, zimbra, phpgrouware, citadel and hula but was never impressed. The functionality was limited, the installation and configuration could be very time-consuming. Sometimes the performance was bad or the appearance could be very lousy.

Thank you for comments, suggestions or ideas!

---

### Post by a9k3d on 2009-05-12
It's been a year since I went through reviewing a bunch of "groupwares". I had a similar reaction. Some had more features than I needed but each module felt like a new country with a different language. Nothing got me excited.

I found my biggest problem is getting the groupware users to "buy-in". Everyone has a different idea of what groupware is going to do for them. I installed 3 different groupware in one company - none worked well for them.

One person's groupware is mediawiki, another's is a bug tracker and calendar. Bosses want a "project manager" but often have never used one before. It's hard to make them everyone happy.

Sometimes a mix of well polished pieces that aren't well integrated together works best and often looks better. Mature software tend to support CSS and themes. Make all the pieces use a similar look and it feels like integrated groupware.

If you have a list of features you are going to need, please post it - it will make it easier to make suggestions.

---

### Post by windependence on 2009-05-13
> **Macchi said:**
> I have to confess that the promise of a holy grail appeals to me. 
Specially if it is a nice _Open Source Groupware_ running on an Ubuntu server.

Has anyone an update of the status of latest groupware solutions that run nicely on Ubuntu? 
I have previously tested conflux, zimbra, phpgrouware, citadel and hula but was never impressed. The functionality was limited, the installation and configuration could be very time-consuming. Sometimes the performance was bad or the appearance could be very lousy.

Thank you for comments, suggestions or ideas!

I'd like to hear what your thoughts are on Zimbra. I have installed the OSS version in several places including a 100 bed nursing home and it has been well received. The new version is also a breeze to install too.

-Tim

---

### Post by glotz on 2009-05-13
Here's one solution not yet mentioned. I don't have first hand experiece though.

[http://kolab.org/](http://kolab.org/)

---

### Post by Macchi on 2009-05-19
> **windependence said:**
> I'd like to hear what your thoughts are on Zimbra. I have installed the OSS version in several places including a 100 bed nursing home and it has been well received. The new version is also a breeze to install too.

-Tim

Dear Tim/Windependence,
I may have to try again Zimbra, but here are some thoughts and concerns:

A couple of years ago when I attempted to start an evaluation I had the impression that integration towards Ubuntu/Debian did not feel so solid. If I recall correctly Zimbra installed its own versions of everything needed. Thus I became immediately concerned with compatibility problems because I had other critical functions on the same server. I guess that things might have improved regarding compatibility issues, since Zimbra has now specific packages for the Ubuntu LTS server. Anyway it is easier and safer to have a dedicated server or virtual machine only for Zimbra.

Furthermore, the present issues that prevent me to use Zimbra are not of technical character. I do have concerns on licensing, pricing, and continuity of that product in the future. Remember that Zimbra has been acquired by Yahoo that was about to be acquired by Microsoft Corporation. 
The Open Source version of Zimbra is released under the YPL, a license type that is not approved by the open source initiative because it keeps a strong leash in the hands of the owner, a corporation that may withdraw the license or reformulate conditions at any time. It is easy to guess what might happen if Microsoft Corporation buys parts of Yahoo that was Zimbra...

Anyway, I still hope to find a good groupware released under the GPL and working out-of-the-box on the Ubuntu server. That would be a fantastic win-win combination for Canonical and for the suppliers/developers of the groupware.

---

