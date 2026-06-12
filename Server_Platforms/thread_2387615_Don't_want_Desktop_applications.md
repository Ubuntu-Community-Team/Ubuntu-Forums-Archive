---
title: "Don't want Desktop applications"
date: 2018-03-21
forum: Server Platforms
---

### Post by sullam on 2018-03-21
i am doing an upgrade from trusty to xenial server. The upgrade informs me that it will automatically install a desktop and tons of desktop applications. Is there some where i could edit the sourceslist so it won't do that? I don't want to install any desktop. I only want the command line.

---

### Post by howefield on 2018-03-21
Thread moved to the "*Server Platforms*" forum.

---

### Post by Tadaen_Sylvermane on 2018-03-25
[https://askubuntu.com/questions/179060/how-to-not-install-recommended-and-suggested-packages](https://askubuntu.com/questions/179060/how-to-not-install-recommended-and-suggested-packages)

```
[COLOR=#000000]APT::Install-Suggests "0";
[/COLOR]APT::Install-Recommends "0";
```

I put this in my /etc/apt/apt.conf

I have the exact same problem as I do have a gui (direct boot to Kodi) but don't want all that other junk from gnome and unity. It remains to be seen if it works as I'm waiting for the xenial to 18.04 upgrade. I never got an answer as to whether or not this works for the release upgrades. I'm assuming it does.

Worst case try it and run the upgrade. Post back and let me know if you could whether or not it stops all that extra stuff from installing.

---

