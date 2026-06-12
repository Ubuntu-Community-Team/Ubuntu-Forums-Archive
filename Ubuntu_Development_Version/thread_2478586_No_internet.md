---
title: "No internet"
date: 2022-08-30
forum: Ubuntu Development Version
---

### Post by TenPlus1 on 2022-08-30
Run today's update for Lubuntu 22.10 and got some brand new systemd files which on reboot messed up my internet connection.  Said it was connecting fine to wifi or ethernet but nothing could use it.

---

### Post by jbicha on 2022-08-30
Do you have [FONT=lucida console]iwd[/FONT] installed? It's ok if the answer is no.

---

### Post by amroesam on 2022-09-02
i think you have Broadcom network adapters in your machine , verify the adapter using following command and bring result here ```
[COLOR=var(--black-800)][FONT=var(--ff-mono)]lspci -knn | grep Net -A2[/FONT][/COLOR]


```

---

### Post by TenPlus1 on 2022-09-04
The laptop has an Intel wifi adaptor which is fully compatible with linux, so not a driver issue.

Also, without opening another thread, Transmission-Qt is showing the progress bar as vertical instead of horizontal, so things are breaking with updates.

---

### Post by QIII on 2022-09-04
Please ***do*** start another thread for the Transmission question.  One topic per thread avoids the confusion that is inevitable if several people are trying to answer more than one question.

---

