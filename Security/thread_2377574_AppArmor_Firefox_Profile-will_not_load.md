---
title: "AppArmor Firefox Profile-will not load"
date: 2017-11-14
forum: Security
---

### Post by pointy2 on 2017-11-14
Apparmor is installed on a fresh updated AA 17.10, with utils and profiles downloaded from the repository. I cannot load the firefox profile using the command - **sudo aa-enforce /ect/apparmor.d/usr.bin.firefox**.  The terminal comes back as "Profile fo /ect/apparmor.d/usr.bin.firefox not found. skipping.

A search of the directory shows the the profile in that directory. How do I load the firefox profile and activate in apparmor? Or, do I have to move or look elsewhere for the proper location? 

Please pardon if this uestion has been asked and solved. My checks have found several threads on this problem, however, without a solution that works for this noob.

---

### Post by &amp;KyT$0P# on 2017-11-14
Try removing the path? -
```
sudo aa-enforce usr.bin.firefox
```

Also you have a typo in the path, it should be [FONT=Courier New]/**etc**/apparmor.d/usr.bin.firefox[/FONT]

---

### Post by pointy2 on 2017-11-15
> **halogen2 said:**
> Try removing the path? -
```
sudo aa-enforce usr.bin.firefox
```

Also you have a typo in the path, it should be [FONT=Courier New]/**etc**/apparmor.d/usr.bin.firefox[/FONT]


Great response, halogen! Firefox now in enforce mode.

---

