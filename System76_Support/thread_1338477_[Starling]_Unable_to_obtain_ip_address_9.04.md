---
title: "[Starling] Unable to obtain ip address 9.04"
date: 2009-11-26
forum: System76 Support
---

### Post by Random201801 on 2009-11-26
I'm at my dad's for thanksgiving, and Since my arrival I've been unable to obtain a ip address while trying to connect to his encrypted network. In addition I had the same issue at my mom's the night before. At home, my wireless was running fine before I left. 
 
I'm running Wicd 2.0. 
Helppp :(

---

### Post by thomasaaron on 2009-11-27
Are you running 9.04?

If so, have you tried this...

```
Establish a wired Internet connection. Then go to Administration > Update Manager. Click the "Check" button, and then install any updates. Then reboot your computer.

Now go to Administration > System76 Driver. Click the "Install" tab and the "Install" button. When the driver finishes, reboot your computer.

Your wireless LED now should be on, and you should be able to see wireless access points. If you cannot, there is a spring-loaded toggle switch on the right-hand side of the leading edge of your Starling. Toggle it *ONCE* to the right, and then release it. Now, reboot your computer.

Did that fix it?
```

---

### Post by Random201801 on 2009-11-27
Yes, I tried it out. I'm back at my mom's today and It turns out my mom's router was WEP encrypted and I was typing it out in WPA format. But it still doesn't solve the issue that my dad's house was WPA encrypted (definitely) and was not working. Does wicd 2.0 have an issue with this?

---

### Post by thomasaaron on 2009-11-30
I guess it's possible. However, we do not test with wicd, so I'm pretty unfamiliar with it.

[http://www.google.com/search?q=wicd+wpa+bugs&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=wicd+wpa+bugs&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

...shows some interesting bugs. But I imagine you can find the same sort of listing with network manager.

I know the Starling with network manager works fine with WPA, so it could just be something with his particular router configuration.

---

