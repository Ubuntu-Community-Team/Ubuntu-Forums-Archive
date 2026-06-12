---
title: "php pages"
date: 2009-02-13
forum: Server Platforms
---

### Post by mistypotato on 2009-02-13
Hi,

I have successfully installed ubuntu 8.10 server and everything seems to be working fine EXCEPT....

php.

After doing a little digging I saw where php5.conf references a file called mod_php5.c

However, I can't locate that file in a normal file search.  Could that be the trouble?

thx again

---

### Post by hyper_ch on 2009-02-13
did you enable php by running
```

sudo a2enmod php5

```
and then restart apache?

---

### Post by mistypotato on 2009-02-13
Yes, I tried that a while ago...maybe I should try it again with a few changes I made?.

After a while, one begins to realize it's usually a very small tweak is all that's needed here or there
so I'm sure it'll become apparent soon.



btw...the response when I try to enable mod php5 is that it is already enabled.

---

### Post by LPomfrey on 2009-02-13
Did you add
```

AddType text/html .php .phps
AddHandler application/x-httpd-php .php
AddHandler application/x-httpd-php-source .phps

```
to your site's configuration file yet?

You'll need to restart Apache after you've added it.

---

### Post by hyper_ch on 2009-02-13
did you also install libapache2-mod-php5?

AddType etc. is not necessary if php5 gets enabled in the global config running the command I've given above.

---

### Post by mistypotato on 2009-02-13
> **hyper_ch said:**
> did you also install libapache2-mod-php5?



Yes, it was already installed but a while ago I re-installed it anyway..no change.

---

### Post by hyper_ch on 2009-02-13
what does it return when you run
```

sudo a2enmod php5

```

---

### Post by LPomfrey on 2009-02-13
> **hyper_ch said:**
> 
AddType etc. is not necessary if php5 gets enabled in the global config running the command I've given above.
I figured that should be the case, but I've never got php working on my server *without* adding AddType etc. after using a2enmod.

---

### Post by mistypotato on 2009-02-13
It would seem reasonable that AddType wouldn't need to be explicitly loaded again at each site as it is  read/loaded globally when apache is loading as mentioned.....or not?

---

### Post by hyper_ch on 2009-02-13
a2enmod adds it to the global configuration file so it's available in all (v)hosts and doesn't need to be enabled there.

---

### Post by mistypotato on 2009-02-13
The 2 most obvious clues I have in this are.....

1). Apache reports the php5 module as loaded

2). No errors are returned when opening a php page, it just doesn't process the script.

(or does NOT apache return any kind of notice if a php script is called but cannot execute?)

---

### Post by hyper_ch on 2009-02-13
just install php5-cli and try to run the script from the cli:

php /path/to/file

does that work?

---

