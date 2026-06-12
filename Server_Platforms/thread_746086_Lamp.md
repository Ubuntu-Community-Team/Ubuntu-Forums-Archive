---
title: "Lamp"
date: 2008-04-05
forum: Server Platforms
---

### Post by chrisbish on 2008-04-05
ok i have installed lamp and i would like to know if there is a way to have lamp running on my server to the local networkgroup and to be able to set there windows pc's homepage to the servers lamp directory.

i hope this makes sence

---

### Post by tmillic on 2008-04-05
Usually, once you've installed LAMP, all you need to do is enter the server's IP address in the browser of your other machines, assuming the LAMP machine has a static IP address. 
For example, our Ubuntu server here at work has the address 192.168.0.9
To reach it, we type this into our browser on the Windows machines: 
[http://192.168.0.9/](http://192.168.0.9/)
You'll see a listing of the directories listed under DocumentRoot and <Directory ...> for your config file.
Once there, just go to the options/preferences for your browser and set that current page as the homepage.

---

