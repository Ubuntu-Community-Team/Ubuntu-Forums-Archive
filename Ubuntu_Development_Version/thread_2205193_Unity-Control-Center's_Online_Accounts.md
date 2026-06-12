---
title: "Unity-Control-Center's Online Accounts"
date: 2014-02-12
forum: Ubuntu Development Version
---

### Post by sigmagammapi on 2014-02-12
So a week ago we got Unity-Control-Center to replace the patched Gnome one on the Unity desktop. The problem I'm having is I lost a couple of items: the Date-Time plugin - which I got back by installing unity-control-center-datetime. But I've also lost the Online Accounts plugin and I can't see how to get it back. It doesn't appear in the control center though it does in the dash (but just launches the control center default view). Does anyone have suggestions what to do?

-Shaun

---

### Post by grahammechanical on 2014-02-12
My Trusty Tahr still uses gnome-control-center-unity. The unity-control-center is shown as being available by synaptic but not installed. So, I do not have your problem. The best that I can offer is this.

[http://developer.ubuntu.com/resources/technologies/online-accounts/](http://developer.ubuntu.com/resources/technologies/online-accounts/)

do you still have gnome-control-center-signon installed.

Regards.

---

### Post by Mateusz Stachowski on 2014-02-12
There is a bug that tracks status of migration to the Unity Control Center.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1257505](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1257505)

One of the last remaining pieces is signon replacement and today there were some updates that are most likely a groundwork for landing of that replacement.

[https://launchpad.net/ubuntu/+source/empathy/3.8.6-0ubuntu4](https://launchpad.net/ubuntu/+source/empathy/3.8.6-0ubuntu4)

> empathy (3.8.6-0ubuntu4) trusty; urgency=medium

  * debian/control:
    - recommends ubuntu-control-center-signon (new binary naming)
 -- Sebastien Bacher <seb128@ubuntu.com>   Wed, 12 Feb 2014 15:40:03 +0100

---

### Post by sigmagammapi on 2014-02-12
Ah thanks. I do still have [COLOR=#000000]gnome-control-center-signon installed, and I've found I can force launching Online Accounts from the credentials-preferences.desktop file in /usr/share/applications. I think I got this new unity-control-center because I re-installed from a new daily iso image a few days ago and the package ubuntu-desktop installs it. So I can't switch back to gnome-control-center-unity without removing ubuntu-desktop too. At least I have a workaround until it's fixed and it looks like that will be soon.[/COLOR]

---

### Post by Mateusz Stachowski on 2014-02-13
Yesterday there were some updates which pulled in unity-control-center-signon for me and deleted the gnome named package. Now I have Online accounts in unity-control-center.

[https://launchpad.net/ubuntu/+source/empathy/3.8.6-0ubuntu4](https://launchpad.net/ubuntu/+source/empathy/3.8.6-0ubuntu4)

> empathy (3.8.6-0ubuntu4) trusty; urgency=medium

  * debian/control:
    - recommends ubuntu-control-center-signon (new binary naming)
 -- Sebastien Bacher <seb128@ubuntu.com>   Wed, 12 Feb 2014 15:40:03 +0100

---

### Post by philinux on 2014-02-13
I has this due to clean install from daily live from a few days back.

All sorted with today's updates.

---

### Post by sigmagammapi on 2014-02-13
That was fast, I just noticed Online Accounts had returned after updating earlier today. Now I'd be really happy if the Ubuntu devs pushed out the newer Wacom settings plugin that Gnome 3.10 has.

---

