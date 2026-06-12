---
title: "[SOLVED] User Password"
date: 2008-04-25
forum: Security
---

### Post by Elcid247 on 2008-04-25
hi, im new to ubuntu and basically all linux based OS, i was using windows.

neway i have 2 questions.

1st, I cant install any program!:lolflag: i mean when i try to open any .exe file, nothing happens, and i need to run some .msi files but i cant :(

2nd, how can i remove the password requiered for login? i really dont like the fact tht i have to enter the pass everytime considering this is my home PC and im the only user.

---

### Post by kostkon on 2008-04-25
> **Elcid247 said:**
> hi, im new to ubuntu and basically all linux based OS, i was using windows.
Welcome to the community! :)
> **Elcid247 said:**
> neway i have 2 questions.
> **Elcid247 said:**
> 1st, I cant install any program!:lolflag: i mean when i try to open any .exe file, nothing happens, and i need to run some .msi files but i cant :(
You can install applications from *Add/Remove* (*Applications -> Add/Remove*) or *Synaptic* (*System -> Administration -> Synaptic Package Manager*).

Now, if you want to use *Windows* programs in *Ubuntu*, you will have to install *Wine*. By installing *Wine* you will get the ability to run .exe and .msi files.

Another option would be to use *Windows* inside a virtual machine (like *VMware*, *Virtualbox*, etc.)
> **Elcid247 said:**
> 2nd, how can i remove the password requiered for login? i really dont like the fact tht i have to enter the pass everytime considering this is my home PC and im the only user.
Go to *System -> Adminstration -> Login Window* and in the *Security* tab activate the *Enable Automatic Login* option and select your username from the drop-down menu.

The next time you'll boot your system, it will go straight to your desktop without giving you a login screen.

---

