---
title: "ufw rules change without my input — Ubuntu 14.01"
date: 2020-09-11
forum: Security
---

### Post by hess88 on 2020-09-11
I've seen some very strange behavior in ufw repeatedly over the past few months.  I run Ubuntu 14.01 because it's a server for a 2015 website.  

I set some very simple rules after "ufw reset":

    ```

    sudo ufw default deny incoming
    sudo ufw default deny outgoing
    sudo ufw allow from 192.168.1.39 to any port 4200
```


When I do this, all is well and I see status:

    ```
4200                       ALLOW       192.168.1.39
```


But **after about 2 days I see a status change**:

    ```

    4200                       ALLOW       192.168.1.39
    4200                       ALLOW       Anywhere
    4200 (v6)                  ALLOW       Anywhere (v6)
```

I haven't touched the machine, so I don't understand why it's allowing 4200 from/to anywhere now. 


If I try to now deny using ```
sudo ufw deny 4200
```, I see status:


    ```

    4200                       ALLOW       192.168.1.39
    4200                       DENY        Anywhere
    4200 (v6)                  DENY        Anywhere (v6)
```


but then the **next day it's allowing** "4200 Anywhere" again. 


Any ideas why it's changing?  Has my machine been attacked somehow?

I've attached the iptables file from when it is in the "good" state I first set up.

---

### Post by EuclideanCoffee on 2020-09-11
I don't think it's due to your computer being hacked... but I need to know, are you an ESM member? Here's information on protecting your machine now that 14.04 LTS is outdated: [https://ubuntuforums.org/showthread.php?t=2450318](https://ubuntuforums.org/showthread.php?t=2450318) Take care of this first thing. :)

After ESM is enabled, go ahead and delete the last two rules. Instead of denying you need to do the following steps.

$ ufw status numbered

The output will show you numbers, which you can then remove.

So if you want to delete 2, this is how.

$ ufw delete 2

---

