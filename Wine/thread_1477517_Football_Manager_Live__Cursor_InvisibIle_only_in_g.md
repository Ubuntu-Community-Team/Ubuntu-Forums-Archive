---
title: "Football Manager Live / Cursor InvisibIle only in game."
date: 2010-05-08
forum: Wine
---

### Post by iain187 on 2010-05-08
Hi All,

I have got an HP6735s laptop (ati flgrx driver if that helps) and i've installed ubuntu 10.04 on it (lynx)

I've installed Wine 1.1.42 on it and then I downloaded and installed Footy Manager Live 

the setup worked perfectly and i can use winecfg without any problems 

but once I startup FML i cannot see my mouse when i move it over the window - although i can see it highlighting buttons and i can click them but it's obviously hard!

i've changed the xorg.conf to vesa drivers but still the same problems

cursor works normally in notepad too. 


any ideas folks?
thanks
iain

---

### Post by rcayea on 2010-05-08
I have the same exact problem with Football Manager 2010 via Steam. Sorry I haven't found any workaround. I thought I would let you know you are not alone.

---

### Post by iain187 on 2010-05-08
heh, gutted

i tried SWCursor in xorg.conf and that didn't help either :( I'm running out of clues.

---

### Post by iain187 on 2010-05-08
i have solved this:

go to a terminal and run
sudo apt-get remove --purge wine

then go to this link [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

download wine 1.1.24 (i picked this version because it was tested ok in the wine app db)

then just double click the file to install it and it should be ok.


not sure if you use any other programs in wine that create another problem but i dont :p

---

### Post by Eadster on 2010-08-02
Hey guys I recently upgraded to Ubuntu 10.04 and installed wine 1.1.42. However when I start the Football Manager Live launcher it goes through start up only to give Program error. Stating FML.exe had encountered a serious problem and needs to close.

Any ideas how to fix this? I previously had the invisible cursor problem to, this is the only application I need Wine for so any help would be appreciated!

---

