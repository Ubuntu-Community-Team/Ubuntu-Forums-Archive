---
title: "APT protocol doesn't work after using Ubuntuzilla"
date: 2009-08-14
forum: Ubuntuzilla
---

### Post by jmzolezzi on 2009-08-14
Thanks for this nice script! It's great, specially for newbies at Ubuntu like myself.

I've installed the latest stable version of Firefox (3.5.2) but I noticed that the apt protocol is not recognized by Firefox anymore (apt://application-name). I searched to see how to associate it manually but had no luck.

Any help will be appreciated!

---

### Post by nanotube on 2009-08-14
Hi
you have to tell firefox about the "ubufox" extension if you want to bring the "ubuntu" modifications to firefox back in.

to do that, cd to your firefox profile's extensions directory. it will be somewhere in ~/.mozilla/firefox/somerandomnumbers.default/extensions

once there, run command
```
ln -s /usr/share/ubufox ubufox@ubuntu.com
```

and restart firefox.

now, in your addons list, you should see "ubuntu firefox extensions" (or something to that effect)

---

### Post by nanotube on 2009-08-14
actually, if you just want the apt protocol, and don't care for all the other bits of ubufox, easier way would be this:

[http://kb.mozillazine.org/Register_protocol#Linux_and_Mac](http://kb.mozillazine.org/Register_protocol#Linux_and_Mac)

which is just to create some entries in about:config:

    *  Type about:config into the address bar and press Enter.
    * Right-click -> New -> Boolean -> Name: network.protocol-handler.external.apt -> Value -> true 
    * Right-click -> New -> String -> Name: network.protocol-handler.app.apt -> Value -> /path/to/app (/path/to/app being whatever it used to open with. synaptic maybe?).
    * Ensure network.protocol-handler.expose-all is set to true.

---

### Post by jmzolezzi on 2009-08-14
Incredible! Thanks for your quick replies nanotube. I must tell that this, being my first real experience with Ubuntu, I'm impressed by Ubuntu itself and by the people helping each other.

I finally decided to install firefox 3.5 through the Synaptic Package Manager to avoid messing around until I feel comfortable enough so I'll try that later.

---

### Post by nanotube on 2009-08-14
good luck, have fun :)

---

