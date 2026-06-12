---
title: "Embedded fonts not shown in Firefox 20 after upgrade to 13.04 from 12.10"
date: 2013-04-27
forum: Ubuntu Development Version
---

### Post by JoZ3 on 2013-04-27
After upgrade ubuntu to 13.04 from Ubuntu 12.10 the websites with embedded fonts not shown in firefox but show fine in Chromium and Epiphany. look at the following pictures to understand me better:

Firefox (not shown the fonts)
[IMG]http://i.imgur.com/eetm3DZ.jpg[/IMG]

Chromium (work fine)
[IMG]http://i.imgur.com/SVU9ios.png[/IMG]

Epiphany (work fine)
[IMG]http://i.imgur.com/0Hk4D3N.png[/IMG]

This is my second day searching on the web, but can not find a solution :(

---

### Post by dino99 on 2013-04-27
maybe you can take smaller screenshots  :lolflag:

---

### Post by Gavin77 on 2013-04-27
I'm using Firefox 21 beta and that page works correctly for me.
Do you use the NoScript extension?  Just as by default NS blocks font-face attributes.

---

### Post by bdisraeli on 2013-05-02
I'm also having this same problem on one of my machines with 13.04 and not other. I'm running Firefox 21 (from the mozillateam/firefox-next ppa) both, and I'd love to know if anyone's figured out why this is happening.

---

### Post by vhaarr on 2013-05-04
Same problem here, and had the problem in Raring, too. I don't know what is causing the issue but it might be because Firefox uses fontconfig and WebKit does not?
Perhaps if we downgrade Fontconfig to the version in Quantal it works?

---

### Post by JoZ3 on 2013-05-04
> **dino99 said:**
> maybe you can take smaller screenshots  :lolflag:

lol!!!

but seriously, the error persists after a few days and try the firefox with extensions disabled and also happens with firefox download from the official website. Try and aurora versions and happend the same. I send the bug to launchpad mozilla and I say they can not reproduce the error ...

---

### Post by JMB74 on 2013-05-04
Have you created a new blank firefox profile and tested with that?

---

### Post by JoZ3 on 2013-05-04
> **JMB74 said:**
> Have you created a new blank firefox profile and tested with that?

Yes, but  searching for google a few minutes ago I found this link that talks about the bug - [https://bugzilla.redhat.com/show_bug.cgi?id=946859]("https://bugzilla.redhat.com/show_bug.cgi?id=946859")

Same thing happens to me, I use the package fontconfig 2.10.92-0ubuntu1~13.04~ricotz1 included in ppa:gnome3-team/gnome3-staging (I use the GS, I hate unity) and is causing the error appears. I'll try removing the ppa and making a regression of the packages.

---

### Post by JoZ3 on 2013-05-04
After much wandering around and discover the cause of the error, I could solve my problem, but not the cleanest way ...

When I discovered that the error was caused by the version of fontconfig that I had installed, delete the repository where was, so the first thing was to follow the instructions recommended in the ppa to remove

```
sudo apt-get purge libpam-&#8203;&#8203;systemd
sudo apt-get install libpam-&#8203;&#8203;xdg-support
```

then uninstall the repository ppa: gnome3-team/gnome3-staging
```

sudo ppa-purge ppa: gnome3-team/gnome3-staging
```

and then to be safer
```

sudo apt-get install ubuntu-gnome-desktop ubuntu-gnome-default-settings
```

Now all work fine :)

---

