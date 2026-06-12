---
title: "How do I completely uninstall Guarddog ?"
date: 2005-07-05
forum: Server Platforms
---

### Post by ssck on 2005-07-05
Hi ALL,

How do I completely uninstall Guarddog ? I have already done that in Synaptics.Yet, when I boot my laptop, I see the message 'cannot find firewall. something.Why is it so ?

thanks

---

### Post by ssck on 2005-07-05
[QUOTE=ssck]Hi ALL,

How do I completely uninstall Guarddog ? I have already done that in Synaptics.Yet, when I boot my laptop, I see the message 'cannot find firewall. something.Why is it so ?

thanks[/QUOTE]

in ubuntu's boot up sequence, i still get the message 'unable to start guarddog ... rc.firewall does not exist'

why is this so ?

---

### Post by Xian on 2005-07-05
[QUOTE=ssck]in ubuntu's boot up sequence, i still get the message 'unable to start guarddog ... rc.firewall does not exist'

why is this so ?[/QUOTE]
Try to purge the package:
```
$ sudo dpkg --purge packagename
```

---

### Post by ssck on 2005-07-05
[QUOTE=Xian]Try to purge the package:
```
$ sudo dpkg --purge packagename
```[/QUOTE]

thanks.i'll try it out.

---

### Post by ssck on 2005-07-05
[QUOTE=ssck]thanks.i'll try it out.[/QUOTE]

yes, it works.thanks

---

