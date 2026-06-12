---
title: "Help with Wine"
date: 2009-01-05
forum: Wine
---

### Post by FarmerReg on 2009-01-05
After upgrading my Ubuntu from 7.04 to 8.10 I am having a whole slew of problems.
The latest one is now with Wine. When I go to use any of the wine applications I can't make out what the words are saying in the windows as they are all in jiberish and totally unreadable. As it is now I have to kinda guess what I'm doing and on top of that its making my eyes hurt trying to make out what's what and what it could be.

Does anyone know why this is happening?
I believe I only have to uninstall and reinstall Wine, but I'm not totally sure this will solve the issue.

Any help is greatly appreciated.

---

### Post by blazemore on 2009-01-06
If I were you I'd totally remove wine and reinstall:
```
sudo aptitude purge wine
```

Now install Wine from the Wine repo:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list && sudo apt-get update && sudo apt-get install wine -y --force-yes
```

Yes all in one go :P

---

### Post by FarmerReg on 2009-01-06
Thank you very much for this. I will give this a try ASAP!!!

---

