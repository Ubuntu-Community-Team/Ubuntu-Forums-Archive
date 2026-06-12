---
title: "[SOLVED] Thunderbird won't start"
date: 2007-07-30
forum: Ubuntuzilla
---

### Post by DJI274 on 2007-07-30
Hi, I wonder if you can help me. I just used the ubuntuzilla script to install thunderbird 2. All appeared to work and thunderbird appears in the application/internet menu. However, when I click on the Thunderbird mail item in the list a tab appears saying thunderbird is starting then disappears without starting the app. Any ideas?

---

### Post by nanotube on 2007-07-31
> **DJI274 said:**
> Hi, I wonder if you can help me. I just used the ubuntuzilla script to install thunderbird 2. All appeared to work and thunderbird appears in the application/internet menu. However, when I click on the Thunderbird mail item in the list a tab appears saying thunderbird is starting then disappears without starting the app. Any ideas?

try starting thunderbird from a terminal, and see if any diagnostic messages appear. 

to start tb from a terminal, just enter command
```
thunderbird
```

---

### Post by fluid_motion on 2007-07-31
I am also having that problem but my TB install is via the repository. I get the "segmentation fault (core dumped)" error. Removed, cleaned and installed again and still got the same error.

Edit: Oops, didn't realise this is thread for Ubuntuzilla. Anyway I think I found the problem is related to SCIM after checking out the Ubuntuzilla site. :)

---

### Post by nanotube on 2007-07-31
> **fluid_motion said:**
> I am also having that problem but my TB install is via the repository. I get the "segmentation fault (core dumped)" error. Removed, cleaned and installed again and still got the same error.

Edit: Oops, didn't realise this is thread for Ubuntuzilla. Anyway I think I found the problem is related to SCIM after checking out the Ubuntuzilla site. :)

heh yea, scim is what i'd blame. although i haven't really seen the scim problem coming up with the repositories version of thunderbird, but it couldn't hurt to try the scim workaround from the site just to see if that helps...

---

### Post by DJI274 on 2007-08-01
Thanks nanotube, starting from a terminal gave the following error but started fine.
(thunderbird-bin:6183): Gtk-WARNING **: Locale not supported by C library.
Using the fallback 'C' locale.

---

### Post by nanotube on 2007-08-01
> **DJI274 said:**
> Thanks nanotube, starting from a terminal gave the following error but started fine.
(thunderbird-bin:6183): Gtk-WARNING **: Locale not supported by C library.
Using the fallback 'C' locale.

well, that warning is really nothing to worry about, nothing that'd cause tb not to start...

so it starts from terminal, but not from a menu, that's pretty strange. :)

can you check what your thunderbird menu item is actually pointing to?  (under system>preferences>main menu)

---

### Post by fremmus on 2007-08-08
i have the same problem, it wont start up.... says starting and then disappears..
i ran it in terminal and here's what i got:
> Segmentation fault (core dumped)

what does that mean?





thanks



[i searched but nothing helps]

---

### Post by nanotube on 2007-08-09
> **fremmus said:**
> i have the same problem, it wont start up.... says starting and then disappears..
i ran it in terminal and here's what i got:


what does that mean?





thanks



[i searched but nothing helps]

hi,
take a look in this thread:
[http://ubuntuforums.org/showthread.php?t=423521](http://ubuntuforums.org/showthread.php?t=423521)
it seems likely that the problem is due to SCIM.

take a look on [this section of ubuntuzilla site]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_Thunderbird_doesn.27t_start_at_all._Segmentation_Fault_.28Core_Dumped.29_when_running_from_terminal") for a possible workaround.

---

### Post by fremmus on 2007-08-09
only reinstalling helped.... looking for another email client now.... thanks!

---

