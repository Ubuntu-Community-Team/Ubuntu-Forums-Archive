---
title: "Mouse4/5 buttons, Wine 1.3.15"
date: 2011-03-09
forum: Wine
---

### Post by 8Kuula on 2011-03-09
In 1.3.15, mouse buttons 4 and 5 stoped working, atleast on Black Ops, HL2 and Alien Swarm.

No errors in console.

OS: Ubuntu 10.04.2 LTS
Wine: 1.3.15

Any suggestions?

Yes, mouse buttons work in desktop.

Downgrading wine to 1.3.14 solves problem.
CODBO:
Had to pull old ~/.wine-codbo prefix from backup, did not agree on starting anymore (or I wasn't patient enough, stoped to steam "launching..." screen, canceled out), 1.3.15 updated prefix at first launch.

---

### Post by chip616 on 2011-03-12
I have problems with 1.3.15 as well and I am also using 10.04.  I now want to downgrade to 1.3.14, which worked perfectly for the app I needed.  How do I go back to the previous version?  I installed from the Ubuntu Wine PPA.

Thanks.

Frank.

---

### Post by 8Kuula on 2011-03-12
[http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/)
There is older packages.

for example:
wine1.3_1.3.14-0ubuntu1~lucidppa1_amd64.deb

download

remove current with:
$ sudo apt-get remove wine1.3

and then install downloaded one, GUI way is just to doubleclick that icon whitch should start 'package installer'.

---

### Post by chip616 on 2011-03-13
8Kuula:

> [http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/)
There is older packages.

Fantastic!  That is what I needed.  Now safely back to 1.3.14, and all is working as it should.

I disabled the Ubuntu WINE PPA this time to prevent a future upgrade from breaking things again.  :)  I had it disabled on my other three machines, but forgot this one.

Thanks again.

Frank.

---

