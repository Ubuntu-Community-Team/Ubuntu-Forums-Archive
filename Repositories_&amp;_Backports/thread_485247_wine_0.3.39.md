---
title: "wine 0.3.39"
date: 2007-06-26
forum: Repositories &amp; Backports
---

### Post by PCFascist on 2007-06-26
Does anyone have wine 0.3.39? winehq.org stated it was in back ports but I have done an apt-get update after checking off 'unsupported updates' in synaptic and I am still only seeing 0.3.33.

Any feedback would be appreciated.

Cheers, 
Jesse James

---

### Post by PCFascist on 2007-06-26
[http://www.winehq.org/site/download-deb:](http://www.winehq.org/site/download-deb:)
```
Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Feisty (7.04):
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Edgy (6.10): *64-bit packages not available*
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06): *64-bit packages not available*
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0): *64-bit packages not available*
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/etch.list -O /etc/apt/sources.list.d/winehq.list

Then, you can install Wine from WineHQ like it were any other package, such as by using the Synaptic Package Manager under System->Administration. Alternatively, you can install from the terminal by running 'sudo apt-get update' to update APT's package information and then 'sudo apt-get install wine'.
```


Im installing now... let you know how it goes.....

---

### Post by PCFascist on 2007-06-26
Seems to work just as good as 0.3.33.

---

### Post by DizzyTech on 2007-06-26
You mean 0.9.39?  For me, it fixed a screw-up I had in 0.9.38 where only the first word of UI text would be displayed.

---

