---
title: "Dansguardian - No Internet Access via browser (Karmic Koala)"
date: 2009-11-26
forum: Ubuntu Christian Edition
---

### Post by JoeIsuzu on 2009-11-26
I've searched the related threads, and even re-installed dansguardian and dansguardian-gui using dpkg.

If I stop dansguardian via the GUI, I can browse just fine.  With it started, I can't.  However, dansguardian is not showing anything in the "denied" log.  That leads me to believe that the proxy or firewall are not cooperating and the http requests never make it to dansguardian.

Do I need to manually set the Firefox proxy, or is that done during the .deb install?

And this seems odd to me: with dansguardian running, I can still use wget from the command line.

I'm very comfortable with command line, although 99% of my experience has been on RedHat (CentOS) systems.  So I'm kinda lost with the tools that are in the Debian-based distros.

Thanks in advance.
Jack

---

### Post by david_kt on 2009-11-27
> **JoeIsuzu said:**
> I've searched the related threads, and even re-installed dansguardian and dansguardian-gui using dpkg.

If I stop dansguardian via the GUI, I can browse just fine.  With it started, I can't.  However, dansguardian is not showing anything in the "denied" log.  That leads me to believe that the proxy or firewall are not cooperating and the http requests never make it to dansguardian.

Do I need to manually set the Firefox proxy, or is that done during the .deb install?

And this seems odd to me: with dansguardian running, I can still use wget from the command line.

I'm very comfortable with command line, although 99% of my experience has been on RedHat (CentOS) systems.  So I'm kinda lost with the tools that are in the Debian-based distros.

Thanks in advance.
Jack

There is a bug in dansguardian. If you want to use it in karmic, follow my post below:

[http://ubuntuforums.org/showthread.php?t=1310351&page=3](http://ubuntuforums.org/showthread.php?t=1310351&page=3)

DK

---

### Post by JoeIsuzu on 2009-11-27
Did that, couldn't get it to work.  I guess I should have been a little more specific about what I'd tried.  But I downloaded the Jaunty-based ISO today and just installed it on our home desktop.  So far, so good.

Thanks.
Jack

---

### Post by david_kt on 2009-11-27
> **JoeIsuzu said:**
> Did that, couldn't get it to work.  I guess I should have been a little more specific about what I'd tried.  But I downloaded the Jaunty-based ISO today and just installed it on our home desktop.  So far, so good.

Thanks.
Jack

You could use Jaunty CE or wait for karmic CE release, I plan to release beta version next week, if everything ok.

If you want to pursue the karmic yourself, check:

```
dansguardian --version.
```

On karmic box that has been updated using CE repos.

DK

---

### Post by JoeIsuzu on 2009-11-27
Yep, that's what I did.  I installed the Jaunty distro-based CE and I'll just be patient for the Karmic release.  If you're the guy behind this, I really appreciate it!

Thanks.
Jack

---

### Post by Carl Hamlin on 2009-11-29
> **JoeIsuzu said:**
> Yep, that's what I did.  I installed the Jaunty distro-based CE and I'll just be patient for the Karmic release.  If you're the guy behind this, I really appreciate it!

Thanks.
Jack

*blink*

No kidding?

Tell you what - if you're waiting because you don't want your kids surfing bestiality sites, etc... disable access to the wireless device in their user accounts, and re-enable it when you're around to keep an eye on their surfing habits. No need to hold off on karmic over something so silly as web filtering software.

---

### Post by JoeIsuzu on 2009-11-29
> **Carl Hamlin said:**
> *blink*

No kidding?

Tell you what - if you're waiting because you don't want your kids surfing bestiality sites, etc... disable access to the wireless device in their user accounts, and re-enable it when you're around to keep an eye on their surfing habits. No need to hold off on karmic over something so silly as web filtering software.
Was that sarcasm?  Sorry, so much nuance is lost in this medium and I'm perhaps a little sarcasm-impaired.  It's not the bestiality sites I'm concerned about.

I'm missing something.  Is the Jaunty version of Ubuntu CE not working?  It seems to be working fine, albeit the DansGuardian GUI doesn't have as many features as the newer (broken) version.

As for wireless, they don't have any wireless devices, they just use a desktop computer that's in a very open part of the house.

Jack

---

### Post by Carl Hamlin on 2009-11-30
> **JoeIsuzu said:**
> Was that sarcasm? Sorry, so much nuance is lost in this medium and I'm perhaps a little sarcasm-impaired.

Nope. I'm legitimately confused as to why internet filtering software is so important as to impede your upgrade.

> **JoeIsuzu said:**
> As for wireless, they don't have any wireless devices, they just use a desktop computer that's in a very open part of the house.

Sounds like the problem is largely solved already, then.

---

### Post by david_kt on 2009-11-30
> **Carl Hamlin said:**
> Nope. I'm legitimately confused as to why internet filtering software is so important as to impede your upgrade.


For people having no time to observe their kids when accessing Internet, internet filtering software is very important. As such, dansguardian install and turn on by default is one of the easy choice.

I plan to release Karmic CE today (if there is no problem), or delay for a few days if I face some problem. Karmic CE would have dansguardian install and enable by default.

DK

---

