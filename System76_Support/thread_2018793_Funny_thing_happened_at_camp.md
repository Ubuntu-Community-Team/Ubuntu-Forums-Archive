---
title: "Funny thing happened at camp"
date: 2012-07-06
forum: System76 Support
---

### Post by nealaustin on 2012-07-06
I have been running MINT version Maya on my Star1 since Maya came out. It has worked rock solid until 2 days ago. All of a sudden it shut down and when booting it would shut down within seconds. After the 20th or so boot I finally got to a fix HD errors screen and on the 3rd try I got it to boot up. Now all is good again. Am I looking at a slowly failing HD or could moisture be the culprit. I did leave it in the hot sun prior to getting it work again.

---

### Post by 3Miro on 2012-07-09
For sudden reboots, I would first look at the temperature. Install "lm_sensors" and "psensors". Run
```
sudo sensors-detect
```
and run psensors to see if the laptop is overheating.

If heat is not an issue, I would run a memtest to see if the RAM is OK. If that's not the problem, then look for bad sectors on the HDD. If you see something wrong, then get an external HDD and immediately backup everything important.

---

### Post by BBQdave on 2012-07-13
> **3Miro said:**
> get an external HDD and immediately backup everything important.

+1

Back up your data :)

---

### Post by nealaustin on 2012-07-18
> **BBQdave said:**
> +1

Back up your data :)

All data is quite well backed up. I think it could have been heat or the HD.I couldn't find any sensor problems so I reinstalled the OS with new formatting and nothing undue has happened ........ yet.

---

