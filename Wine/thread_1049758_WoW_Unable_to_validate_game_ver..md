---
title: "WoW Unable to validate game ver."
date: 2009-01-24
forum: Wine
---

### Post by Corey4666 on 2009-01-24
I am in a hurry so i hope i explain all the details needed but i am using the latest version of wine (forgot how to check) as of the date. when i log into WoW it says "unable to validate game version" the game repair tool wont open but on the official wine page for this game some guy had this problem too and he said: > $ chown your-user:your-user -R /path/to/wow/installation
$ chmod 770 -R /path/to/wow/installation

Fixed his problem of the game version error


i typed 

> eviscerate@eviscerate-laptop:~$ $ chown eviscerate:eviscerate-laptop -R /home/eviscerate/.wine/dosdevices/c:/Program Files/World of Warcraft/

bash: $: command not found
eviscerate@eviscerate-laptop:~$ $ chmod 770 -R /home/eviscerate/.wine/dosdevices/c:/Program Files/World of Warcraft/
bash: $: command not found
eviscerate@eviscerate-laptop:~$ 
eviscerate@eviscerate-laptop:~$ 

And it says command not found, i think im not typing it correctly? can someone please help me out? sorry for bad grammer etc i have to run now!

---

### Post by hikaricore on 2009-01-24
You're typing a dollar sign where you shouldn't.

I don't know if this will solve your issue however.  I think something is wrong with your WoW install.

---

### Post by toopi on 2009-01-25
And I think it should be
```
 chown eviscerate:eviscerate 
```
instead of
```
 chown eviscerate:eviscerate-laptop 
```

---

