---
title: "fstrim"
date: 2018-03-11
forum: Ubuntu Development Version
---

### Post by mc4man on 2018-03-11
the weekly fstrim has been moved from cron (anacron) to a systemd timer.service
to check past
```

journalctl -u fstrim
```
To check date of  next & last 
```
systemctl list-timers
```
or ```
systemctl list-timers |grep fstrim
```
For former systemctl command use q to return prompt

---

### Post by #&amp;thj^% on 2018-03-11
Thanks mc4man>>> I for one VERY much appreciate your continued contributions! ;)

---

### Post by cruzer001 on 2018-03-11
```
systemctl list-timers |grep fstrim
```
Nice and easy on the eyes.

Thanks

---

