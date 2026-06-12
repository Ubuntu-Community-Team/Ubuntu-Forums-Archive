---
title: "Server won't install anything"
date: 2012-05-05
forum: Server Platforms
---

### Post by roffisserver on 2012-05-05
I am trying to in webmin on my server and it won't work. I also tried the landscape client and that didn't work. Can some please help.

---

### Post by Cheesemill on 2012-05-06
We need more details please.
How are you trying to install things? What commands are you using?
What happens when the installation fails? Please post the error messages you are getting and then we'll be able to help.

---

### Post by roffisserver on 2012-05-06
Well I edit the sources file and add these linesdeb [COLOR="Red"]http://download.webmin.com/download/repository sarge contrib
deb [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge contrib[/COLOR]

Then I add the GPG key
```
wget http://www.webmin.com/jcameron-key.asc

sudo apt-key add jcameron-key.asc
```

I update the sources list

Then I install
```
sudo apt-get install webmin
```



Then it says

```
W: Failed the fetch deb http://download.webmin.com/download/repository sarge contrib
```

---

### Post by roffisserver on 2012-05-07
I reinstalled! It worked but I wonder why I couldn't?

---

### Post by CharlesA on 2012-05-07
> **roffisserver said:**
> I reinstalled! It worked but I wonder why I couldn't?
That's so strange. Did you upgrade this originally, or was it a clean install?

---

### Post by roffisserver on 2012-05-07
It was a clean install but I think there was how the networking was setup.

---

