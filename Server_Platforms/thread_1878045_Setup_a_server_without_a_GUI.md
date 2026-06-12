---
title: "Setup a server without a GUI"
date: 2011-11-09
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-11-09
Intend to try and setup a server on a spare box without installing a desktop.

Two obvious questions immediately and no doubt more to follow:-

How do you edit files?
How do you setup a CRON job?

TIA

---

### Post by haqking on 2011-11-09
> **ChrisRChamberlain said:**
> Intent to try and setup a server on a spare box without a installing a desktop.

Two obvious questions immediately and no doubt more to follow:-

How do you edit files?
How do you setup a CRON job?

TIA

nano, vi/vim would be most popular CLI editors, i use vi or nano to edit files even in a gui, occasionally gedit (gui app).

rather type about cronjobs see here:

```
man crontab
```

and these links
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
 [http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)

---

### Post by ChrisRChamberlain on 2011-11-09
haqking

Thanks for your reply.

So```
sudo gedit /path/filename
```will work as expected, as 'gedit' is in the distro?

---

### Post by nothingspecial on 2011-11-09
> **ChrisRChamberlain said:**
> haqking

Thanks for your reply.

So```
sudo gedit /path/filename
```will work as expected, as 'gedit' is in the distro?

No because gedit is a gui app.
```

sudo nano /path/filename
```

is what you want.

btw, you should use gksudo with graphical apps.

```
gksudo gedit
```

---

### Post by haqking on 2011-11-09
> **ChrisRChamberlain said:**
> haqking

Thanks for your reply.

So```
sudo gedit /path/filename
```will work as expected, as 'gedit' is in the distro?

no as mentioned above, it was my wording in my first post, i meant even in a GUI i still use nano/vi etc and sometimes gedit.

From a pure CLI then no gedit is not there.

nano/vi would be your options, sorry to confuse you.

---

### Post by ChrisRChamberlain on 2011-11-09
```

```nothingspecial, haqking

Thanks for the clarification.

So```
sudo crontab -e
```will bring up choice of editor first time, thereafter behaviour as per Terminal in a GUI?

---

### Post by nothingspecial on 2011-11-09
Yep.

All terminal applications will work exactly the same because they are the same.

The difference is that it doesn't pop up in a window.

---

### Post by ChrisRChamberlain on 2011-11-09
Thanks both for your help.

---

