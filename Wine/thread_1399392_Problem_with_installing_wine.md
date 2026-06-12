---
title: "Problem with installing wine"
date: 2010-02-05
forum: Wine
---

### Post by infla on 2010-02-05
Hello,

I've installed Wine long time ago. but i had to update it to instal a Program (a friend of me said that i could only install that program with the last version of wine). but I couldn't update it. then I found something on a website to update it. i've done that, but now there is something wrong with my wine. I can't install or open programs anymore with wine (my wine isn't installed anymore :O.

So i tried to reinstall it, but I can't install it anymore. so I went to /usr/share to delete the map Wine, but I'm not allowed to do it.. so i was trying it in Terminal. but I think that I use the wrong Terminal Code. 

any ideas?

---

### Post by beastrace91 on 2010-02-05
```
sudo apt-get purge wine
``` to fully remove all traces of Wine - then reinstall it.

~Jeff

---

### Post by infla on 2010-02-06
> **beastrace91 said:**
> ```
sudo apt-get purge wine
``` to fully remove all traces of Wine - then reinstall it.

~Jeff

Hello,

I've tried that. but when i do that i get a message witch says that wine isn't installed.

Greetings,

Infla

---

### Post by beastrace91 on 2010-02-06
How did you install Wine? Also could you post the output from running:

dkpg -l wine*

In terminal?

Regards, 
~Jeff

---

### Post by dino99 on 2010-02-07
if you are using an old wine release (actual is "1.1.38"), better to backup all you need to save from ~/.wine, then remove that hidden file (.wine) and the others: .winetricks, .winedoors.(if installed)

Recent release now don't generaly need these old things and don't need to be customized.

Add in synaptic repo: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa) for the latest wine, then update/upgrade and install wine with synaptic.

Then you only need to execute your windows apps to be loaded with wine. It's as simple as ...

If your system has not been installed from scratch, maybe it's a good idea to clean it with bleachbit( but take care to understand what you do, it's powerfull and risky if not used properly)

---

