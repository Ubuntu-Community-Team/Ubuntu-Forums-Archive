---
title: "How to check when was last login?"
date: 2014-09-28
forum: Security
---

### Post by andrew102 on 2014-09-28
So I have a server that I mostly access through SSH. I want to check when was the last time somebody logged on via monitor/GUI.

My first guess is to look in the lightDM logs. Is their somewhere else this would be logged?

---

### Post by Doug S on 2014-09-28
The "last" command. Example:```
doug@desk-dev:~$ [COLOR=#ff0000]last[/COLOR]
doug     pts/0        :0               Sun Sep 28 11:25   still logged in
doug     pts/11       doug-xps2.smythi Sun Sep 28 11:25   still logged in
doug     :0           :0               Sun Sep 28 11:24   still logged in
reboot   system boot  3.16.0-18-generi Sun Sep 28 11:24 - 12:59  (01:34)
doug     pts/16       doug-xps2.smythi Sun Sep 28 11:13 - 11:19  (00:06)
doug     pts/12       :0               Sun Sep 28 11:11 - down   (00:12)
doug     pts/6        :0               Sun Sep 28 11:04 - down   (00:19)
doug     :0           :0               Sun Sep 28 11:03 - down   (00:20)
reboot   system boot  3.16.0-17-generi Sun Sep 28 11:03 - 11:24  (00:20)
doug     pts/3        :0               Thu Sep 25 15:43 - down   (04:28)
doug     :0           :0               Thu Sep 25 15:43 - down   (04:28)
reboot   system boot  3.16.0-17-generi Thu Sep 25 15:42 - 20:11  (04:28)
doug     :0           :0               Wed Sep 24 11:41 - down   (02:31)
reboot   system boot  3.16.0-17-generi Wed Sep 24 11:41 - 14:12  (02:31)
doug     pts/16       :0               Wed Sep 24 11:19 - down   (00:21)
doug     :0           :0               Wed Sep 24 11:18 - down   (00:22)
reboot   system boot  3.16.0-16-generi Wed Sep 24 11:18 - 11:41  (00:22)
doug     pts/0        :0               Thu Sep 18 14:26 - down   (00:50)
doug     pts/0        :0               Thu Sep 18 11:41 - 11:44  (00:02)
doug     :0           :0               Thu Sep 18 09:28 - down   (05:49)
reboot   system boot  3.16.0-16-generi Thu Sep 18 09:28 - 15:17  (05:49)
doug     pts/1        :0               Thu Sep 18 08:47 - down   (00:40)
doug     :0           :0               Wed Sep 17 15:41 - down   (17:46)
reboot   system boot  3.16.0-14-generi Wed Sep 17 15:41 - 09:27  (17:46)
reboot   system boot  3.16.0-14-generi Wed Sep 17 15:40 - 15:40  (00:00)
reboot   system boot  3.16.0-14-generi Wed Sep 17 15:34 - 15:40  (00:05)
doug     pts/0        :0               Wed Sep 17 15:18 - down   (00:15)
doug     :0           :0               Wed Sep 17 11:41 - down   (03:52)
reboot   system boot  3.16.0-14-generi Wed Sep 17 11:41 - 15:33  (03:52)
doug     pts/7        doug-xps2.smythi Wed Sep 17 07:56 - down   (03:44)
doug     pts/4        :0               Wed Sep 17 06:56 - down   (04:44)
doug     :0           :0               Wed Sep 17 06:56 - down   (04:45)
reboot   system boot  3.16.0-14-generi Wed Sep 17 06:55 - 11:41  (04:45)
doug     pts/8        doug-xps2.smythi Tue Sep 16 15:26 - down   (04:48)
doug     pts/4        :0               Tue Sep 16 15:23 - down   (04:51)
doug     :0           :0               Tue Sep 16 15:13 - down   (05:01)
reboot   system boot  3.16.0-14-generi Tue Sep 16 15:12 - 20:15  (05:02)
doug     pts/4        :0               Tue Sep 16 15:08 - down   (00:03)
doug     :0           :0               Tue Sep 16 15:00 - down   (00:11)
reboot   system boot  3.16.0-14-generi Tue Sep 16 15:00 - 15:12  (00:11)

wtmp begins Tue Sep 16 15:00:41 2014
```

---

### Post by Habitual on 2014-09-28
type
```
lastlog
``` for a complete "user" report.

---

### Post by andrew102 on 2014-10-03
Thanks for both answers.

---

