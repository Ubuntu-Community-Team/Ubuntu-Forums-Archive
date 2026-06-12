---
title: "VMWare just... stopped"
date: 2006-12-07
forum: Server Platforms
---

### Post by sp0nge on 2006-12-07
I installed VMWare Server a few weeks ago to mount a seperate winXP partition  to easliy solve the debacle I faced when trying to get my machine to dual boot. 

That being said, the software has worked wonders until this afternoon. I tried to start the program and there was just NOTHING! I had been on this partition for a few hours last night and it was working seamlessly, but today, nothing. 

Any suggestions to troubleshoot this issue?

---

### Post by Peturrr on 2006-12-07
I would suggest you do the following:
```
sudo /etc/init.d/vmware restart
```If this doesn't give you errors the server itself is working correctly.

Open up a terminal and enter 
```
vmware
```This will start the vmware server console, just like the shortcut in your menu, but with 'debug' output. Please post what errors it gives if any.

---

### Post by melancholeric on 2006-12-07
Start VMware from the terminal to see possible error messages.

edit: too slow. As usual.

---

### Post by Peturrr on 2006-12-07
> **melancholeric said:**
> 
edit: too slow. As usual.
I spot a melancholic tendency in your edit ;)

---

### Post by sp0nge on 2006-12-07
After saying all was done, I get:

```
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

```

I tried to do this and got:

```
/usr/bin/vmware-config.pl.
bash: /usr/bin/vmware-config.pl.: No such file or directory

```

---

### Post by melancholeric on 2006-12-07
Did you type

```
/usr/bin/vmware-config.pl.
```

or 

```
/usr/bin/vmware-config.pl
```
Because you're not supposed to have a period in the end.

Oh, and you need to use sudo with that.

---

### Post by sp0nge on 2006-12-07
Apparently, I coppied the period as well... Now it seems to work- THanks!
/usr/bin/vmware-config.pl
I noticed references to the linux headers which were modified through synaptic last night. Apparently re-configuring was ll that I needed!

---

