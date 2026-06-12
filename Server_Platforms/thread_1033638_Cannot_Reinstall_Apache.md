---
title: "Cannot Reinstall Apache"
date: 2009-01-07
forum: Server Platforms
---

### Post by tetsujin on 2009-01-07
Hello Everyone,

In all my infinite wisdom I decided to uninstall apache2 and reinstall it so I could get clean conf files. Sadly to my dismay now when I attempt to reinstall apache2 it will not recreate the /etc/apache2 folder. So any suggestions beyond reinstalling Ubuntu...which I know I shouldn't have to do in this situation.

Cameron

---

### Post by lykwydchykyn on 2009-01-07
Have you tried:
```

sudo aptitude purge apache2
sudo aptitude install apache2

```

I'm guessing a purge might fix it, since apt may think you still have old configs installed.

---

### Post by tetsujin on 2009-01-07
Thanks for the reply but the purge option did not help. I in fact attempted that before but forgot to mention it. Any other ideas?

---

### Post by lykwydchykyn on 2009-01-07
And there were no errors when you tried those commands?  A reinstall of apache2 *should* put the config files back, so something is preventing that.

---

### Post by tetsujin on 2009-01-07
It installs perfectly and successfully. Just for some reason there is no /etc/apache2 folder. I also have now hand deleted my /var/www folder just in case and that also did not help.

---

### Post by cdenley on 2009-01-07
The apache2 package doesn't contain much.
```

sudo apt-get purge apache2.2-common
sudo apt-get install apache2.2-common

```

---

### Post by tetsujin on 2009-01-07
Brilliant! Thank you very much! No clue that was there, thanks again!

---

