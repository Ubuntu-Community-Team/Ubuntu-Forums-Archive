---
title: "Installed packages in upgrade from 11.10 to 12.04"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by d.atanasov on 2012-04-04
Hello, 

I don`t know if this is bug or because the beta2 version of the 12.04, but when I upgraded to it I found that all 32 bit packages not needed (because I use 64 bit Ubuntu) are also installed or downloaded. I was just wondering is this bug or not ?

cheers 

dinko

---

### Post by raja.genupula on 2012-04-04
see this [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Perfect Storm on 2012-04-04
Moved to Ubuntu +1

---

### Post by d.atanasov on 2012-04-04
Thanks for the prompt reply, 

but I don`t get it. Do you say that no matter the of 32bit/64bit of the Ubuntu the packages are all the same. Or in other word: The upgrade process to 12.04 install both 32 and 64 bit packages without the need to know the operating system?

---

### Post by philinux on 2012-04-04
> **d.atanasov said:**
> Thanks for the prompt reply, 

but I don`t get it. Do you say that no matter the of 32bit/64bit of the Ubuntu the packages are all the same. Or in other word: The upgrade process to 12.04 install both 32 and 64 bit packages without the need to know the operating system?

It's to do with multiarch. [https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)

The upgrade will have upgraded the available packages. That doesnt mean they are installed.

---

### Post by oldos2er on 2012-04-04
It's because of multiarch. See [https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)

---

### Post by d.atanasov on 2012-04-04
Thanks for the reply :)

best regards

---

