---
title: "linux-firmware-nonfree"
date: 2014-12-12
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2014-12-12
been getting this error message when running updates for a couple of days

E: /var/cache/apt/archives/linux-firmware_1.139_all.deb: trying to overwrite '/lib/firmware/sms1xxx-hcw-55xxx-dvbt-02.fw', which is also in package linux-firmware-nonfree 1.16

---

### Post by zika on 2014-12-12
> **rburkartjo said:**
> been getting this error message when running updates for a couple of days

E: /var/cache/apt/archives/linux-firmware_1.139_all.deb: trying to overwrite '/lib/firmware/sms1xxx-hcw-55xxx-dvbt-02.fw', which is also in package linux-firmware-nonfree 1.16That happened here too. I simply purged linux-firmware-nonfree after cheking if all my HW is supported in linux-firmware.

---

### Post by rburkartjo on 2014-12-12
zika tks that worked like a charm

---

### Post by zika on 2014-12-12
> **rburkartjo said:**
> zika tks that worked like a charmYou can install linux-firmware-nonfree back (linux-firmware 1.140 has that bug corrected).

---

### Post by rburkartjo on 2014-12-13
zika tks for the info

---

