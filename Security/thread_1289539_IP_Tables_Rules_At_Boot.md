---
title: "IP Tables Rules At Boot"
date: 2009-10-12
forum: Security
---

### Post by zemon_ on 2009-10-12
I want to restore my ip table rules at boot.

I restore them manually by this.

```
iptables-restore < rules.txt
```

I need an init.d script to restore these rules at boot, can anyone help?

---

### Post by kemra on 2009-10-13
First your going to need to create a script that does what you want, so something like:

```
#!/bin/bash
#Script for loading IP Tables rules on system boot up.
iptables-restore < rules.txt
```

This will need saving to the /etc/init.d directory. Bear in mind you should refert to the absolute path of the text file.

Now lets assume you called your script iptablesrules.sh follow the below:

```
chmod +x /etc/init.d/iptablesrules.sh
```
```
update-rc.d iptablesrules.sh defaults
```

This should amke sure your script runs in the default run levels of 2, 3, 4 and 5. If you want it to start in differant run levels run the follwoing for more info:

```
man update-rc.d
```

Hope this works for you.

---

### Post by aos101 on 2009-10-13
Rather than using an init.d script, it's easier to use a pre-up command in your /etc/network/interfaces file:

[https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup](https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup)

---

### Post by kevdog on 2009-10-15
Could you not just reference this script, or just cut and paste the contents of the script into /etc/rc.local -- that runs at the end of all run-levels?

---

### Post by Agent ME on 2009-10-15
> **aos101 said:**
> Rather than using an init.d script, it's easier to use a pre-up command in your /etc/network/interfaces file:

[https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup](https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup)

That would happen every time you connected to a network though. Might be annoying if your wireless connection falters suddenly and it decides to run again.

---

