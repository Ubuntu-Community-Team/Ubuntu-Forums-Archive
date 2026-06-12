---
title: "First time with a VPS - problems with useradd"
date: 2014-07-21
forum: Server Platforms
---

### Post by Issam2204 on 2014-07-21
Hello everyone! I decided to buy a one month VPS, given the low price and my willingness to learn more about hosting. I've been using it a couple of days now but I still didn't figure out how to "properly" create a user. 

The VPS was deliverd with root access. First thing I did was to create a standard user. However, it seems like there are some problems of compatibility: when I press "up" I don't get the last command but this "^[[A", there is no color output, the name of the folder I am in is not visible (whatever folder I am in it shows only this "$"). Also it doesn't recognize "tab" input to autocomplete folders/files name.

Why all this problems?

This is how I created the user:

```
# useradd pippo

# passwd pippo

# mkdir /home/pippo

# chown pippo:pippo /home/pippo
```


What did I miss?

---

### Post by steeldriver on 2014-07-21
IIRC useradd command sets the user's login shell to /bin/sh not /bin/bash. You can change it after the fact using

```

chsh -s /bin/bash 

```
or (as root)

```

chsh -s /bin/bash *username*

```

If you use adduser instead of useradd the account is created with /bin/bash plus a number of other things like copying the default startup files from /etc/skel

---

### Post by Issam2204 on 2014-07-21
> **steeldriver said:**
> IIRC useradd command sets the user's login shell to /bin/sh not /bin/bash. You can change it after the fact using

```

chsh -s /bin/bash 

```
or (as root)

```

chsh -s /bin/bash *username*

```

If you use adduser instead of useradd the account is created with /bin/bash plus a number of other things like copying the default startup files from /etc/skel

Thank you so much **steeldriver**! Thank you also for taking the time to explaining why it was happening! Great!

---

