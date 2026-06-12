---
title: "Top Panel gone after update"
date: 2012-08-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Hazzabin on 2012-08-18
A recent update for Quantal Quetzal 12.10, I lost the top panel,least the normal info doesn't show ie: date,and other normal icons on right side

this seemed to happen after the update and install of "Preview" in 'Dash'

I've got 12.10 fully installed on a 'testing' computer

Ideas how to fix

regards
Hazz

---

### Post by godhika on 2012-08-18
If you have the preview feature already you also must have the unity-staging ppa activated. So a simpel ppa-purge ppa:unity-team/staging should fix it. You will have to wait til the preview feature is stable enough (and shows the indicators) and land in the regular 12.10 ;)

---

### Post by Hazzabin on 2012-08-18
ok mate thanks for that, 
do I put this command "ppa-purge ppa:unity-team/staging" into the terminal and hit enter?

---

### Post by godhika on 2012-08-19
You need to first install ppa-purge. Type ```
sudo apt-get install ppa-purge
``` in the terminal. Then run ```
sudo ppa-purge ppa:unity-team/staging
```

---

