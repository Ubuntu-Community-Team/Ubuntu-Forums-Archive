---
title: "problem with synaptic not loading"
date: 2011-12-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by leeper69 on 2011-12-05
Hi I have a problem with Gnome classic in Ubuntu 12.04.
I have installed synaptic but when I try to open it I get the password prompt and after adding my password synaptic never pops up. I also have KDE loaded and synaptic works fine in that desktop also wont work in Unity desktop.
no bug report pops up with the failure to load synaptic in Gnome classic.
so this forum is my only hope. has anyone else had this problem?

---

### Post by oldos2er on 2011-12-05
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by irv on 2011-12-05
I was having some problem with synaptic, update manager and ubuntu software center, so I ran this command in the terminal,
```
sudo apt-get update
```
and it ran some update/upgrades and I have everything works but USC.
give this a try and see what happens.

---

### Post by coffeecat on 2011-12-05
Synaptic working just fine with Unity in this up-to-date 12.04 install - in fact, just updated using Synaptic. Do you get any error if you try to open Synaptic from the terminal?

```
gksu synaptic
```

---

### Post by ventrical on 2011-12-05
Same here .. works great.

---

### Post by irv on 2011-12-05
> **coffeecat said:**
> Synaptic working just fine with Unity in this up-to-date 12.04 install - in fact, just updated using Synaptic. Do you get any error if you try to open Synaptic from the terminal?

```
gksu synaptic
```

Starting synaptic from the termial will start Ok, but I get this warrning. 
[ATTACH]208597[/ATTACH]

---

### Post by coffeecat on 2011-12-05
> **irv said:**
> Starting synaptic from the termial will start Ok, but I get this warrning. 

I'm getting that too, but repeated four times over for whatever reason, but synaptic opens OK after I enter my password.

---

### Post by irv on 2011-12-05
I get this when I close synaptic.
[ATTACH]208601[/ATTACH]

---

### Post by mc4man on 2011-12-05
If you wanted to test synaptic  from the terminal using the current auth. method then you'd use this command, synaptic no longer uses sudo (though it will continue to open thru it.

```
synaptic-pkexec
```

---

### Post by bluexrider on 2011-12-05
I have a similar issue with not being able to get the software sources GUI to show up in 11.10 classic 
> **leeper69 said:**
> Hi I have a problem with Gnome classic in Ubuntu 12.04.
I have installed synaptic but when I try to open it I get the password prompt and after adding my password synaptic never pops up. I also have KDE loaded and synaptic works fine in that desktop also wont work in Unity desktop.
no bug report pops up with the failure to load synaptic in Gnome classic.
so this forum is my only hope. has anyone else had this problem?

---

### Post by coffeecat on 2011-12-05
> **mc4man said:**
> If you wanted to test synaptic  from the terminal using the current auth. method then you'd use this command, synaptic no longer uses sudo (though it will continue to open thru it.

```
synaptic-pkexec
```

Thanks, but I still get the unable to locate error:

```
coffeecat@vaio-pangolinalpha:~$ synaptic-pkexec

(synaptic:22065): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:22065): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:22065): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:22065): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

But I'm not getting the...

```
Segmentation fault (core dumped)
```

... error on closing synaptic as I do when using gksu (as irv does too.)

Anyway, the OP seems not to be able to get synaptic to open at all, except in KDE, so it will be interesting what they get with "synaptic-pkexec".

---

### Post by vhaarr on 2011-12-05
Try it with

LC_ALL=C gksudo synaptic

---

### Post by Bowmore on 2011-12-05
About the warnings, see to that you have the package gtk2-engines-pixbuf installed.

---

### Post by leeper69 on 2011-12-05
thanks to all who answerd my post I tryed synaptic-pkexec in the terminal and got the following GTK-warning**:cannot open display: :0.0
next I tryed gksu synaptic in terminal and synaptic loaded up and worked to download with no problem. special thanks to irv for his help!!!

---

### Post by irv on 2011-12-05
> **Bowmore said:**
> About the warnings, see to that you have the package gtk2-engines-pixbuf installed.

Just for the record with gt2-engines-pixbuf installed, you will get no errors when starting synaptic or closing it.

[ATTACH]208616[/ATTACH]

---

### Post by mc4man on 2011-12-05
'Warnings' are not 'Errors', in many cases can just be ignored, this is one.

---

