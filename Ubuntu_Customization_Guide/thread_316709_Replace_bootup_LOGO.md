---
title: "Replace bootup LOGO"
date: 2006-12-11
forum: Ubuntu Customization Guide
---

### Post by ghepardo on 2006-12-11
Hi, I have ubuntu 6.10 installed. I installed and then remove kubuntu-desktop, but this changed my logo start from the ubuntu one to the kubunto one. How do I restore the ubuntu logo!?

---

### Post by Ben Sprinkle on 2006-12-11
```

sudo apt-get install ubuntu-desktop

```

---

### Post by ghepardo on 2006-12-11
there isn't another way than reinstalling all ubuntu in this way!?

---

### Post by deadlydeathcone on 2006-12-12
```
sudo apt-get --purge kubuntu-artwork-usplash
sudo apt-get --reinstall usplash-theme-ubuntu
```

...and you'll be just fine.

---

### Post by kapilg_it on 2006-12-12
That was the exact same problem with me you saved me posting me a new thread , OS started as kubuntu but shuts down as ubuntu :-D 

Looks nice though :mrgreen:

---

### Post by ghepardo on 2006-12-12
> **deadlydeathcone said:**
> ```
sudo apt-get --purge kubuntu-artwork-usplash
sudo apt-get --reinstall usplash-theme-ubuntu
```

...and you'll be just fine.


Nice, thank you.

---

