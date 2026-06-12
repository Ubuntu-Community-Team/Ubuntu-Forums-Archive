---
title: "Quick way to add and install from a PPA"
date: 2013-09-18
forum: Tutorials
---

### Post by GrouchyGaijin on 2013-09-18
OK 99% of people here absolutely do not need this script.
Admittedly, I am one of the few who cannot seem to remember the code to add a ppa.
Every time I  need to click the little tab about installing software just be be reminded about what to put before the name of the ppa.

So I came up with a script to make my life easier. I made a quicklist to launch it and have it in that side dock like thing Unity uses.

```

#!/bin/bash
# by GrouchyGaijin
echo "This script is for adding a ppa"
var1="sudo add-apt-repository"
read -p "Enter the PPA name: " var2
var3="$var1 $var2"
echo $var3
sudo $var3
sudo apt-get update
read -p "Enter the name of the software to install. " var4
sudo apt-get install $var4

```

---

### Post by ranger1021994 on 2013-09-18
Good

---

### Post by ibjsb4 on 2013-09-18
I tried making a launcher on my gnome-classic panel.  The terminal will only flash on my screen for a split second then disappear.

---

### Post by GrouchyGaijin on 2013-09-19
> **ibjsb4 said:**
> I tried making a launcher on my gnome-classic panel.  The terminal will only flash on my screen for a split second then disappear.
Try adding this at the end of the script.
```


echo "Press Enter to quit"


read n
case $n enter 
exit
esac


```

---

### Post by ibjsb4 on 2013-09-20
Thanks

---

