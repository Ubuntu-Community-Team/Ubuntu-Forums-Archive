---
title: "ubuntu 20.04 LTS stability on release?"
date: 2020-03-14
forum: Ubuntu Development Version
---

### Post by jebi on 2020-03-14
Hi

Could anyone tell me will the ubuntu 20.04 LTS be stable from the release date? Or should I wait a month for any bugs to be worked out?

thx

---

### Post by Frogs Hair on 2020-03-14
Moved to ***Ubuntu Development Version***.

---

### Post by paulycalvinmiller on 2020-03-14
don't use it. It's very unstable.

---

### Post by VMC on 2020-03-14
For me its stable right now. Both Ubuntu, and Kubuntu. I have issue with Lubuntu.

---

### Post by kurt18947 on 2020-03-14
> **jebi said:**
> Hi

Could anyone tell me will the ubuntu 20.04 LTS be stable from the release date? Or should I wait a month for any bugs to be worked out?

thx

If you have the software updater set to notify you of new LTS releases and are using 18.04.4 now,  my understanding is that you won't be notified about a new LTS until 20.04.1 is released. I would interpret that to mean that Ubuntu feels there may be glitches after the initial release date. I have 20.04 running on two machines, A Ryzen 3 2200G and Thinkpad T430. To my surprise the Ryzen machine is pretty stable. The Thinkpad, normally a very good Ubuntu machine has had some issues, I've had to re-install twice. It does look to me that Ryzen machines benefit from the newer kernel, Xorg and device drivers in 20.04. It also appears to me based solely on gut feeling that Wayland is working better than X. X certainly had some issues with 18.04 using integral graphics on my machine with suspend/resume. Wayland wasn't perfect but it was better.

---

### Post by TheFu on 2020-03-14
> **jebi said:**
> Hi

Could anyone tell me will the ubuntu 20.04 LTS be stable from the release date? Or should I wait a month for any bugs to be worked out?

thx

Nobody knows.  Generally, I wait until mid-June or July before loading a new LTS for testing.  Really comes down to what you need in the new release and how well tested and fixed those aspects are by the team.  For me, some issues in 18.04 still aren't working, so we are still running 16.04 on all our production systems.  Tested the current 18.04 installer about 2 months ago, and the issues still exist.

**Update April**: Did a fresh install of 18.04 Server a few days ago and the 2 huge problems that have been broken by the prior installers were both corrected by the "download new installer" option presented a few days ago.  Storage setup was almost a joy to use, which was surprising AND the setup for static IPs actually created a working netplan.  Call me shocked. Progress.  I didn't have to manually create any LVs, resize any LVs or fix a broken netplan.yaml file for the first time!  Now I just need to get non-trivial, multiple network bridges working in the netplan to consider 18.04 "ready."  Here's hoping 20.04 is production ready much sooner.

Just comes down to what you need and what works for your environment.  If you want the best chance for those things you care about to be handled, test now. Constantly. Open bug reports. Help the team.

---

### Post by him610 on 2020-03-14
> Ubuntu 20.04 release date
Ubuntu 20.04 codenamed Focal Fossa will be released on April 23, 2020. Here’s the release schedule for Ubuntu 20.04 with important milestones:

Testing week: January 9, 2020
Feature Freeze: February 27, 2020
User Interface Freeze: March 19, 2020
Ubuntu 20.04 Beta: April 2, 2020
Kernel Freeze: April 9, 2020
Release Candidate: April 16, 2020
Final stable release of Ubuntu 20.04: April 23, 2020
from [https://itsfoss.com/ubuntu-20-04-release-features/]("https://itsfoss.com/ubuntu-20-04-release-features/")

I have Xubuntu 20.04 installed on three different machines. Have not encountered any more issues than normally encountered in LTS 16.04-4, LTS 18.04-2(?), or 19.10.

---

### Post by iamjiwjr on 2020-03-15
Every Ubuntu release, LTC or not, always hits me with error messages at boot but, other than that, 20.04 is already pretty stable. 

It's the Gnome Extensions (they're not Ubuntu, but the affect Ubuntu greatly) that will take a bit longer than release date to update and stabilize. They're pretty rough at this stage. Because of them I'll wait a month or so to update.

---

### Post by sudodus on 2020-03-15
> **TheFu said:**
> If you want the best chance for those things you care about to be handled, test now. Constantly. Open bug reports. Help the team.

+1 :-)

---

### Post by corradoventu on 2020-03-15
I'm using Ubuntu 20.04 on my desktop and laptop (both Intel CPU, NO additional graphic card) since the first alpha and it seems very stable.

---

### Post by VeloxNeb on 2020-04-01
personally, i'm confident it will be rock solid.
you can always just run a live session and see for yourself. 
or create a separate partition for 20.04 and keep your 18.04 for as long as you like.

---

### Post by kevdog on 2020-04-03
If you aren't really into running the latest and greatest, a general rule of thumb is to wait until after the first LTS point release prior to upgrading.  Usually al lot of bugs have been worked out in the first point release.  This in general is usually about 2-3 months after the main release however the time frame may vary.

---

