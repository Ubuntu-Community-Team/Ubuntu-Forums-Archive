---
title: "Problems accessing a .php website."
date: 2010-07-05
forum: Server Platforms
---

### Post by mattc9305 on 2010-07-05
Hi,
     Just have to say I have been using ubuntu on and off for some time but I would say I'm still pretty much a novice.

I recently installed 'Gallery2' on my ubuntu server to allow family to view photos online.  It is being hosted by the program Apache2 and works fine from within the network.  However when you try to access it from outside of the network a problem occurs.

When you enter the web address (which is a free one for now) the server is found but the address in the address bar changes to a local address of 192.168.1.6/main.php (the main.php bit is right) and there is a blank screen.

I really don't know what to do and would appreciate it if someone could give me a hand.  Thanks :)

---

### Post by confusedstingray on 2010-07-06
need alittle more info, 
by the sounds of it the free web address needs to point to your global ip address you can check using
[http://www.whatismyip.com/](http://www.whatismyip.com/) . Then set your router to all port 80 (www) be forward to server. 
also check the file permissions in gallery they may be set for root or you only not global. do you have a default web page try that address first if it works them you know the problem is in the gallery setup

---

### Post by mattc9305 on 2010-07-06
Other websites work fine, even other .php pages.  It is just this website, it appears to load but the screen is just white.

---

### Post by y@w on 2010-07-07
To be clear, you mean that other websites work from outside the network the way you want Gallery2 to work?

If so, this is likely a question to post on the Gallery2 forums, but I'm assuming you'll want to check out your config.php in the Gallery2 webroot. Particularly the line that probably reads something like:
```
$gallery->setConfig('baseUri', 'http://192.168.1.6/main.php');

```

I would hardly call myself an expert in Gallery2, but there's also likely an option to force the browser to redirect to what is set in the baseUri property.

It should work just fine to set that URL to whatever you want it to be externally and just use that address all the time.

---

