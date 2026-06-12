---
title: "Feisty segfault"
date: 2007-02-28
forum: Ubuntu System Panel
---

### Post by PWill on 2007-02-28
When I have the terminal plugin with USP, I get
```

paul@bel-air:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
Loading plugin 'places' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'terminal' : successful
Segmentation fault (core dumped)

```
I removed USPterm after I realized I don't even use it, but it's still broken.

---

### Post by Malac on 2007-02-28
> **PWill said:**
> When I have the terminal plugin with USP, I get
```

paul@bel-air:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
Loading plugin 'places' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'terminal' : successful
Segmentation fault (core dumped)

```I removed USPterm after I realized I don't even use it, but it's still broken.
It looks like you are using USP 1.9x but USPterm is for version 0.4x only.
You will need to remove any plugins that begin with USP in capital letters, as these are for the USP 0.41 version only.
The Extra/Add-On plugins for USP 1.9x are available here:
[http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2)

Hope this helps.

---

### Post by AtrejuT on 2007-02-28
Hey Malac,

I get the same error using the terminal plugin from your link...
If I remove it everything is fine.

Atreju

---

### Post by PWill on 2007-02-28
> **AtrejuT said:**
> Hey Malac,

I get the same error using the terminal plugin from your link...
If I remove it everything is fine.

Atreju

Yep, I did the same.

---

