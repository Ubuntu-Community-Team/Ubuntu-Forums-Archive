---
title: "Local Repo on 24.04"
date: 2024-07-09
forum: Server Platforms
---

### Post by polgara2 on 2024-07-09
I've been running local repositories on Ubuntu 20.04 and 22.04.  I wanted to experiment with adding a local repo for 24.04 on one of my existing repos, as well as set up a local repo on Ubuntu 24.04.  Unfortunately, I have been unable to get either option to work, and can't find any write up on how to set up a repo for 24.04 or how to create a local repo on 24.04.

Does anyone know where to find this information (either option, but both preferably)?

---

### Post by darkod on 2024-07-09
I haven't tried this myself but maybe if you post what worked for you in 22.04 and doesn't work on 24.04, someone can try to help more. I wouldn't say there should be big difference in setting it up compared with the previous LTS version, but then again, I might be totally wrong. :)

---

### Post by 0f4d0335 on 2024-07-09
I imagine you're doing this for repository caching, so you don't need to download the same package twice for multiple installations?

---

### Post by #&amp;thj^% on 2024-07-09
I'm on 24.10 and just starting my local cache:
```
sudo apt update
Get:1 file:/var/lib/local-apt-repository ./ InRelease
Ign:1 file:/var/lib/local-apt-repository ./ InRelease
Get:2 file:/var/lib/local-apt-repository ./ Release [1,279 B]
Get:2 file:/var/lib/local-apt-repository ./ Release [1,279 B]
Get:3 file:/var/lib/local-apt-repository ./ Release.gpg
Ign:3 file:/var/lib/local-apt-repository ./ Release.gpg
Hit:4 http://archive.ubuntu.com/ubuntu oracular InRelease
Hit:5 http://archive.ubuntu.com/ubuntu oracular-updates InRelease              
Hit:6 https://ocean.surfshark.com/debian stretch InRelease                     
Hit:7 http://security.ubuntu.com/ubuntu oracular-security InRelease            
Hit:8 https://brave-browser-apt-release.s3.brave.com stable InRelease          
Hit:9 https://packages.mozilla.org/apt mozilla InRelease                       
Hit:10 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease           
Hit:11 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble InRelease
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```

+1 with darko reply need what worked before, and what dose not work.

---

### Post by emeliaee3 on 2024-07-19
Setting up local repositories on Ubuntu 24.04 is similar to other versions. Working perfectly fine with baobao technology industrial touchscreen monitor Start with guides for Ubuntu 20.04 or 22.04, adjusting as needed. For specific queries, try the Ubuntu Community Forums or consult official Ubuntu documentation. Good luck with your setup!

---

