---
title: "Dansguardian"
date: 2010-07-05
forum: Security
---

### Post by Bgineur on 2010-07-05
Hi,

I want to know how to desactivate Dansguardian or how to modify level security.

I have found the configuration file /etc/dansguardian/dansguardian.conf, but when i modify it and I want to restart the service I've got the following message : I seem to be running already!

Do you know if it's normal, or how I do to modify this service ? Thanks

---

### Post by bodhi.zazen on 2010-07-05
```
sudo service dansguardian stop
```

What are you trying to do exactly ?

---

### Post by Script Warlock on 2010-07-06
wew dansguardian is too strict on some "sex" tags on youtube... can i exclude the word "sex"?....

---

### Post by bodhi.zazen on 2010-07-06
> **Script Warlock said:**
> wew dansguardian is too strict on some "sex" tags on youtube... can i exclude the word "sex"?....

LOL

Yes, you can configure dansguardian, but you will have to read through the configuration files.

See : [http://dansguardian.org/downloads/detailedinstallation2.html#further](http://dansguardian.org/downloads/detailedinstallation2.html#further)

---

