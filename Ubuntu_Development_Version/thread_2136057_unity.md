---
title: "unity"
date: 2013-04-16
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-04-16
last set of updates finally enabled me to run unity. i still have to run  setsid unity from the command line first thought. and  i installed tint2 to enable a bottom panel

---

### Post by rburkartjo on 2013-04-16
is there a way to get unity to work without running the setsid unity?

---

### Post by philinux on 2013-04-16
> **rburkartjo said:**
> is there a way to get unity to work without running the setsid unity?

I would reset unity to it's default config.

```
dconf reset -f /org/compiz/
```

then restart it

```
setsid unity
```

---

### Post by dino99 on 2013-04-16
Also have that issue, and the commands needs to be run each time to get the launcher & dash.

---

### Post by Frogs Hair on 2013-04-16
I have had to reset compiz/unity only once or twice since installing in mid March and have been experimenting with the cube and other effects also. The Nividia  3.10 + 3.8.0-17 header combination has been the only rough spot so far and I was able to switch to the 3.13 driver. 

I did see a partial install installation of the 3.8.0 -18 kernel not reported as such when installing. All the related kernel packages except the Linux signed image were installed. I noticed this in synaptic and manually installed kernel last night. Today brought a compiz update and everything is working.

---

### Post by rburkartjo on 2013-04-16
phil tried that didnt work tks though

---

### Post by rburkartjo on 2013-04-16
yea dino i have had to reset every time i want to use unity since 12.10 but at least it works now. good to know that i wasnt the only one having this problem.

---

### Post by Frogs Hair on 2013-04-16
I read in order for the compiz reset command to work you need the following. ```
sudo apt-get install dconf-tools
```

---

### Post by dino99 on 2013-04-16
> **rburkartjo said:**
> yea dino i have had to reset every time i want to use unity since 12.10 but at least it works now. good to know that i wasnt the only one having this problem.

an idea of mine : we should set a new team  :)

note: here its with i386 + gnome3 ppas

---

### Post by rburkartjo on 2013-04-16
tks frog i already had the dconf-tools still didnt help.

---

