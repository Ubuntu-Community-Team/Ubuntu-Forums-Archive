---
title: "HOWTO: Install Mathmap Gimp plugin"
date: 2007-05-05
forum: Tutorials
---

### Post by diogosousa on 2007-05-05
This mini HOWTO explains how to compile and install the Mathmap (1.0.1) Gimp Plugin.

(Tested in Ubuntu 7.04 Feisty 32 bits with Gimp 2.2 and 2.3)

**Important:** This is an easy to follow tutorial, but PROCEED AT YOUR OWN RISK

[SIZE="3"]**Pre-Requisites:**[/SIZE]

[LIST]
[*]**Gimp**

If you don't already have it, install it:

```
sudo apt-get install gimp
```

[*]**Other packages (Needed!)**

```
sudo apt-get install flex bison gsl-bin libgsl0-dev libgimp2.0-dev
```

[/LIST]

[SIZE="3"]**Get/Unpack Mathmap plugin:**[/SIZE]

[LIST]
[*]**Get the plugin**
```

wget http://www.complang.tuwien.ac.at/schani/mathmap/mathmap-1.0.1.tar.gz
```
[/LIST]

[LIST]
[*]**Unpack the plugin**
```
tar xvfz mathmap-1.0.1.tar.gz
```
[/LIST]

[SIZE="3"]**Compile/Install Mathmap plugin:**[/SIZE]

Get into the unpacked directory and "do the magic":
```
cd mathmap-1.0.1
make
make install
```

[SIZE="3"]**Where is the plugin?**[/SIZE]

(If you followed correctly all the previous steps) in Gimp, at the image window there is a new menu [Filters]>[Generic]>[Mathmap]

[SIZE="3"]**Troubleshooting**[/SIZE]

If you just installed Gimp, make sure you run it once, so it creates the ~/.gimp-2.2/ directory.

Make sure you have installed all the "pre-requesites"

[SIZE="3"]**Further Reading (Links)**[/SIZE]

[LIST]
[*]**Mathmap Homepage:** [http://www.complang.tuwien.ac.at/schani/mathmap/](http://www.complang.tuwien.ac.at/schani/mathmap/)
[*]**Gimp Homepage:** [http://www.gimp.org/](http://www.gimp.org/)
[*]**Flickr's Mathmap Group:** [http://www.flickr.com/groups/mathmap/](http://www.flickr.com/groups/mathmap/)
[/LIST]

---

### Post by edmondt on 2007-05-09
Looks like a cool plugin :) Geat instructions, I installed it and it works...

---

### Post by pengko.eo on 2008-04-30
hello there. could you please help me? i successfully installed mathmap on my ubuntu using your tutorial. the thing is, its not working well on my hardy heron. when i choose the warp option, nothing changed in my picture. and it seems that under the picture there is a message "cannot read template file new_template.c" 

[IMG]http://farm4.static.flickr.com/3241/2453286557_0dd413ae69.jpg?v=0[/IMG]

do you know what happens? thanks a lot.

---

### Post by evadsllim on 2011-10-09
Did fine until you directed to get into the unpacked directory. Not sure what this means. Could you assist? Thx

---

