---
title: "automatic reboot"
date: 2009-12-03
forum: Server Platforms
---

### Post by fabiomc on 2009-12-03
hi

im newbie of linux
i have ubuntu server 9.1.0
i want to schedule a automatic reboot. dont ask me why  :)

i have not set password of root because i dont want to use it

i have launched this command from shell:   # crontab -e

then in crontab files, i have add:
0 20 * * * /sbin/shutdown -h now

but it doesnt run, why ?

what can i do ?

Thank you very much

---

### Post by M!K3_$ on 2009-12-03
i'm not at home, so i cant test this out right now but i think i know your problem. 

shtudown is a command that requires root privilages (either through ```
sudo
``` or ```
su -
```)

---

### Post by littlegreiger on 2009-12-03
Try putting it in root's crontab by running```
sudo crontab -e
``` and putting in the same line that you had before.

---

### Post by M!K3_$ on 2009-12-03
You could also change the privilages of the shutdown command. that might not be such a good idea though...

---

