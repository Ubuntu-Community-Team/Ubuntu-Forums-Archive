---
title: "can I use automatix2 to download and install E-sword, and thereby bypass dansgardian?"
date: 2007-01-13
forum: Ubuntu Christian Edition
---

### Post by Scott A on 2007-01-13
can I use automatix2 to download and install E-sword, and thereby bypass dansgardian?

(dansgardian is blocking me from downloading E-sword - ironic, isn't it!)

It says it doesn't like the .exe extension. 

Scott A

---

### Post by meng on 2007-01-13
Are you intending to run Esword under wine (Windows compatibility layer)? Have you gnomesword installed? Or is it not to your liking?

---

### Post by doobit on 2007-01-13
You can put the url on your whitelist.

---

### Post by mhancoc7 on 2007-01-13
> **Scott A said:**
> can I use automatix2 to download and install E-sword, and thereby bypass dansgardian?

(dansgardian is blocking me from downloading E-sword - ironic, isn't it!)

It says it doesn't like the .exe extension. 

Scott A

The dansguardian setup in Ubuntu CE can be easily tweaked using the GUI (System>Administration>Configure Parental Controls). You simply need to open the GUI and click "Blocked File Extensions". This will open the corresponding dansguardian config file in a text editor. Then find .exe and put a # before it. Now save the file and click Save & Exit in the GUI. Now you should be able to download E-Sword just fine.

Hope that helps.

Jereme

---

