---
title: "Right click encryption"
date: 2010-01-05
forum: Security
---

### Post by minerbog on 2010-01-05
Hi All,

Happy New Year.

I've just started using ubuntu one.  However, some of the files I store on there are sensitive so I encrypt them using seahorse. Right click, encrypt etc etc.

My question is, is there a way to automatically get the encrypt process to delete the un-encrypted file when it makes the new encrypted copy??

Many Thanks

Gav.

---

### Post by Sarmacid on 2010-01-05
You could create your own script and add it to the nautilus menu.

---

### Post by BkkBonanza on 2010-01-05
I don't know how to make the seahorse plugin do the delete but I do know how to add another right-click item for running srm (secure-delete). That's what I have. Just let me know if you want the details for that using Nautilus Actions Config.

---

### Post by minerbog on 2010-01-07
Thanks BkkBonaza, That would be great if you could let me know that.

---

### Post by BkkBonanza on 2010-01-07
Select menu item System, Preferences, Nautilus Actions Config.

Click Add. Set values as follows,

Label: Secure Delete
Tooltip: Use the srm utility to securely erase files
Icon: gtk-delete
(you can choose a different icon if you like)
Path: srm
Parameters: -rlz %M

Choose the Conditions tab, select "Both", and enable "Appears if selection has multiple files".

Advanced Conditions tab should just have Local files checked.

Save. You may need to logout/in to get it to show up. Don't recall now.
That's it. Now should have that item on right click menu.

It's also possible to make one for secure empty trash as follows, 
select Add again,

Label: Secure Empty Trash
Tooltip: Use srm utility to securely empty the trash
Icon: gtk-clear
Path: /usr/local/bin/srm-trash
Parameters: %m

Conditions same as above.
Advanced conditions - remove all checks and click + to add a new one named "trash", and make it enabled.

Now create the script /usr/local/bin/srm-trash and chmod +x it

```
#!/bin/bash
if [ $# -eq 0 ]; then
  srm -lrz ~/.local/share/Trash/*/*
else
  for f in "$@"; 
  do
    srm -lrz ~/.local/share/Trash/files/"$f"
    srm -lrz ~/.local/share/Trash/info/"$f".trashinfo
  done
fi

```

This script handles two cases. If you have selected and right-clicked files in the Trash  then it uses srm on them. But also if it is called from the File menu then it uses srm on all the trash.

---

### Post by minerbog on 2010-01-08
> **BkkBonaza said:**
> Select menu item System, Preferences, Nautilus Actions Config.



Don't have this on my menu. Is it a package??

---

### Post by BkkBonanza on 2010-01-08
Ah, yes, I forgot. I must have installed that some time back.

sudo apt-get install nautilus-actions

or use Synaptics.

---

