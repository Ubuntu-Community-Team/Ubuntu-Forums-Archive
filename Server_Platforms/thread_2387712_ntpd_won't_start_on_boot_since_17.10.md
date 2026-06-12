---
title: "ntpd won't start on boot since 17.10"
date: 2018-03-22
forum: Server Platforms
---

### Post by xWEkxhW on 2018-03-22
Hi Folks,

ntpd isn't starting on boot since upgrading to 17.10. I'm having to start the service manually as a temporary workaround. Any ideas what might be causing this? Thanks

There is nothing much in journalctl other than:

Mar 22 18:02:04 miranda systemd[1]: Starting Network Time Service...
Mar 22 18:02:04 miranda systemd[1]: Stopping Network Time Synchronization...

---

### Post by xWEkxhW on 2018-03-23
Just for the records I solved this after discovering timedatectl

I removed ntpdate firstly (apt purge ntpdate)
Then disabled timesyncd (timedatectl set-ntp false)

ntpd now loads when the system boots

---

