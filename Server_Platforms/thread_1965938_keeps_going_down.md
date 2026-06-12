---
title: "keeps going down"
date: 2012-04-26
forum: Server Platforms
---

### Post by RefinersFire on 2012-04-26
I am running fresh install of ubuntu 10.04LTS Desktop, Webmin 1.580, Apache, Bind, Postfix, and a few other server software.

Every day either my computer freezes, or  my web server goes down... Just goes down. No log files that I could find. Apache and Bind will be running, but there is NO way to connect to my site, by IP or domain. It is almost like both Apache AND Bind go down -- but they're not. If it's not that, then it's Wordpress not showing the styles in the style sheet. I literally have to, after rebooting, reinstall the site. Then everything (except Postfix) works just fine. I installed SMF BB as a test, and it works just fine -- except when "the site goes down".

I need to figure this out and get my site stable, and postfix configured correctly. This will be my bread and butter.

First things first. The site "going down"

---

### Post by RefinersFire on 2012-04-27
No one has any ideas?

---

### Post by cortman on 2012-04-27
I don't think I can be helpful with exactly WHY your system is falling apart, but if I were in your place I think I'd do a backup and a clean wipe and reinstallation. Since the new LTS (12.04) just came out, it might be a good time to do that upgrade as well. Starting with a clean installation  is often the best fix.

---

### Post by RefinersFire on 2012-04-27
It's a fresh installation, and I don't like the new ubuntu. That's why I am sticking with this release. Unity is too resource intensive, and a bad execution of a good idea. Plus, I would have 500+ GB to back up, and no place to put it. I reinstalled when my other HDDs were failing, leaving me with one 1TB SATA II.

Thanks anyway.

---

### Post by jerome1232 on 2012-04-27
Who said you had to use Unity? There are a plethora of other desktop environments to choose from. There is gnome-failback, Mate (a gnome2 fork), KDE4, Gnome-shell, LXDE, XFCE, Openbox, fluxbox, Ice, and many more to choose from.

---

### Post by RefinersFire on 2012-04-27
> **jerome1232 said:**
> Who said you had to use Unity? There are a plethora of other desktop environments to choose from. There is gnome-failback, Mate (a gnome2 fork), KDE4, Gnome-shell, LXDE, XFCE, Openbox, fluxbox, Ice, and many more to choose from.

I used the new 11.04 and 12.04, and the other DEs just don't play well will Unity. My wife's laptop is prime example. I have to downgrade it. Too buggy. It was the same on my desktop before I downgraded to 10.04. We like Ubuntu, we just don't like where it has been heading since 10.04.

---

### Post by jerome1232 on 2012-04-27
> **RefinersFire said:**
> I used the new 11.04 and 12.04, and the other DEs just don't play well will Unity.

See that just doesn't make sense to me as they don't interact at all. Could you clarify?

For example I have a netbook running 12.04 using LXDE (aka Lubuntu), this main desktop I have running 11.10 with Unity (I'm going to sit on it for a bit, maybe a month), I have another computer running 11.10 with KDE4 (aka Kubuntu)

I personally would never suggest running anything as heavy as Gnome3, Gnome2, or kde on a server machine. At the most I would run a thread bare gui with maybe openbox as my window manager. These full blown desktop environments add to much that can be broken into the mix.

Once again, I'm just tossing out suggestions at you. Take it all with a grain of salt

edit: Have you checked through your logs to see if there are useful errors in them? Try syslog, and apache's log for starters.

---

