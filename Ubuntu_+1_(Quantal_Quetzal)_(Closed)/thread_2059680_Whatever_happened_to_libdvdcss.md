---
title: "Whatever happened to libdvdcss?"
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by semperfried76 on 2012-09-18
What happened to libdvdcss? apt-get install says there is no installation candidate...

---

### Post by Guardian978 on 2012-09-18
I am not currently running the beta (building now) but on the previous releases you had to install libdvdread-dev and then as root you could navigate to /usr/share/doc/libdvdread4 and run the install-css.sh script. This then brought down the libdvdcss package. It was done a few releases back due to issues with including decryption of dvds in the repositories.

---

### Post by semperfried76 on 2012-09-18
> **Guardian978 said:**
> I am not currently running the beta (building now) but on the previous releases you had to install libdvdread-dev and then as root you could navigate to /usr/share/doc/libdvdread4 and run the install-css.sh script. This then brought down the libdvdcss package. It was done a few releases back due to issues with including decryption of dvds in the repositories.

Much obliged Guardian, you solved my issue. Which release did this change in? I installed libdvdcss through apt in 12.04 (although, I might've added a non-standard repository...)

---

### Post by 67GTA on 2012-09-18
It is only available in the Medibuntu repo. They haven't updated for 12.10 yet. [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by jbicha on 2012-09-18
[https://help.ubuntu.com/12.04/ubuntu-help/video-dvd-restricted.html](https://help.ubuntu.com/12.04/ubuntu-help/video-dvd-restricted.html)

---

