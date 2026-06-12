---
title: "Auto Restart"
date: 2011-11-15
forum: Server Platforms
---

### Post by mandza on 2011-11-15
hi,
i am running ubuntu server 11.10 with no problems for now.
I want to restart my server every day at 1AM automaticaly, is it posible and how?

My server is running 24h at day. and i just want to restart it daily one time.

---

### Post by Jonathan L on 2011-11-15
> **mandza said:**
> hi,
i am running ubuntu server 11.10 with no problems for now.
I want to restart my server every day at 1AM automaticaly, is it posible and how?

My server is running 24h at day. and i just want to restart it daily one time.

Hi Mandza

Sounds like a funny thing to do to me, but simple enough.  You use root's crontab to reboot.  Edit it with
```
sudo crontab -e
```And add
```
0 1 * * * /sbin/reboot
```

Or perhaps more elegantly:
```
55 12 * * * /sbin/shutdown -r 01:00 'Daily reboot'
```

Hope that helps.  Why do you want to reboot it?

Kind regards,
Jonathan.

---

### Post by mandza on 2011-11-15
Thank you very much, it was very helpfull for me.

---

