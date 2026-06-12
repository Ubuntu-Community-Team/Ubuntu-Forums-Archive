---
title: "Steam in Wine"
date: 2011-01-13
forum: Wine
---

### Post by sigma_z_1980 on 2011-01-13
hi, I got this problem now: I've installed Steam and Civilization V, launched Civ5 and it was Ok. Then I restarted the computer and launched Steam again, and it takes a heinous long time so I lose patioence and click it off. I tried a few different ways to do it, but the situation persists. Additionally, when I run 

wine Steam 

in its folder, I get the text message 'Cannot open blob archive file CMultiFieldBlob(mem-mapped file):File does not exist and failed to create new file'
 
Does anyone have any idea what to do? I'd hate to reinstall Steam 'cause it took heaps of time for some reason

cjeers

alex

---

### Post by cogadh on 2011-01-14
If you don't exit gracefully out of Steam when running it within Wine, it will have problems like this. Additionally, if you didn't configure Steam to NOT launch at startup, it will not only have issues, it can cause issues with other apps run in Wine. 

I would recommend you delete the ClientRegistry.blob file, which puts Steam nearly back into a "freshly installed" state without actually needing to re-install it, then launch Steam and log in. If it takes a while, don't get impatient and force it to quit, walk away and let it do its thing if you have to. After it has launched completely, first go into the Steam options and make sure you set it to not launch at startup, then exit out of it normally. The next time you launch it, it should work much better.

---

