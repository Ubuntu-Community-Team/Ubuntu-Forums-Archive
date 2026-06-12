---
title: "Need help with ethernet card config"
date: 2011-07-03
forum: Server Platforms
---

### Post by TaylorHxx on 2011-07-03
OK i just switched the hard drive with my ubuntu server install from one machine to the other. I have done this before and remember i had to change the ethernet card config file since linux recognizes ethernet cards by mac adresses however i forgot the location and the change i need to make could someone please point me to the right spot

---

### Post by arrrghhh on 2011-07-03
I believe what you're looking for is:

```
/etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by TaylorHxx on 2011-07-03
what change should i be making

---

### Post by TaylorHxx on 2011-07-03
nevermind i got it figured out. thank you for pointing me to the right file

---

