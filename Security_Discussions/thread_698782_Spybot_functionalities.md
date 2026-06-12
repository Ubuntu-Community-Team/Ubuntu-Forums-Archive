---
title: "Spybot functionalities?"
date: 2008-02-16
forum: Security Discussions
---

### Post by ubacct3 on 2008-02-16
I know that Spybot Search and Destroy can also automatically block certain cookies, popups, images, etc.  

I found that HOSTS file sometimes completely blocks sites on hot deals sites, so I don't like to use it.  

Spybot has a large database of websites to block for cookies, popups, images, etc., and I know it's not as necessary to use them on Ubuntu as on Windows, but I'd still like to know if there is an app that allows similar functionality.

BTW, I already use adblock and noscript, but I'd also like a list to automatically block cookies in firefox, flock, seamonkey, and opera as well.

---

### Post by ajgreeny on 2008-02-16
Firefox Preferences, Privacy allows you to block cookies from particular sites so if you know the domain of the bad sites you can block them.  It will need to be done manually as far as I can see, but it is possible.

---

### Post by p_quarles on 2008-02-16
An easier way to selectively deny cookies is to use the "CookieSafe" Firefox extension, then turn off all cookies. The CookieSafe button at the bottom of the browser will allow you to enable cookies whenever you specifically need them.

---

### Post by ubacct3 on 2008-02-16
Thanks.  But the whole point of having some kind of a spybot like application would be to automate that process.  Spybot has hundreds of cookie blocking entries, and to do that manually is completely impractical.  The real issue is in being able to automate the entry of an already-made blacklist database.  I guess outside of Spybot or Spywareblaster in Windows, no solution comes close.

---

### Post by p_quarles on 2008-02-16
> **ubacct3 said:**
> Thanks.  But the whole point of having some kind of a spybot like application would be to automate that process.  Spybot has hundreds of cookie blocking entries, and to do that manually is completely impractical.
Erm, I think you have it backwards. What I was suggesting is that you allow cookies manually, not block them manually. I've been doing this for awhile, and I can vouch for its practicality.

---

### Post by gaten on 2008-02-17
Whitelists are always preferred to whitelists. 

It sounds like you might benefit from a proxy server. Squid may be able to do the things you describe, or if you have another system lying around you might want to look into some gateway/firewall distros (m0n0wall, Smoothwall, ipcop, Untangle etc)

---

### Post by bodhi.zazen on 2008-02-18
This is how I do it : [http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

+1 on a hosts file, if there is a specific site you like, remove it from the hosts file. If you have a large file, use sed

sed -i -e 's_GoodSite.com_#GoodSite.com_g' /etc/hosts

+1 on block all and manually generating a white list. It takes very little time.

---

### Post by pietjanjaap on 2008-02-18
firefox noscript plugin and adblock.
In de rightcorner you give permission to the site.

Ipblock has a big list with sites to block.(something like peerguardian)

---

### Post by ubacct3 on 2008-02-20
> **p_quarles said:**
> Erm, I think you have it backwards. What I was suggesting is that you allow cookies manually, not block them manually. I've been doing this for awhile, and I can vouch for its practicality.

I agree that manual whitelisting is useful.  However, having to block cookies manually is still more than I'm willing to do.  With Spybot, I just set it and forget it because I set it to update by itself.  I'm pretty happy with NoScript, but a lot of manual work starts get tiresome when I start to browse new sites.

---

