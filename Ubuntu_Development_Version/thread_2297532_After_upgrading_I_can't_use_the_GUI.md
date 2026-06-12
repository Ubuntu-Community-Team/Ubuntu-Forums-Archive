---
title: "After upgrading I can't use the GUI"
date: 2015-10-04
forum: Ubuntu Development Version
---

### Post by giruzz on 2015-10-04
Hi,

I have just upgraded to 15.10 and everything went well up until my first reboot.

It seems I can't get into the GUI, my screen only shows a black bacground with four 'orange' dots (the ones that you see when Ubuntu is loading at the very beginning). No other prompts or any activity on my drives....

I have tried to reboot and I can manage to login via terminal but I can't use 'startx' because when I do type it the system crashes...

Any suggestions what to do or where to look?

thanks,
g.

---

### Post by ventrical on 2015-10-04
> **giruzz said:**
> Hi,

I have just upgraded to 15.10 and everything went well up until my first reboot.

It seems I can't get into the GUI, my screen only shows a black bacground with four 'orange' dots (the ones that you see when Ubuntu is loading at the very beginning). No other prompts or any activity on my drives....

I have tried to reboot and I can manage to login via terminal but I can't use 'startx' because when I do type it the system crashes...

Any suggestions what to do or where to look?

thanks,
g.

 I would first try :

```

sudo service lightdm restart

```

if that does not work then  I would install razorqt de and see if that comes up.

```

sudo apt-get install razorqt

```
perhaps you could troubleshoot from there.

Regards..

---

### Post by giruzz on 2015-10-17
Unfortunately it doesn't seems to be working :-(

Any suggestions?

---

### Post by tista on 2015-10-17
Greetings,

Please git it a try:
```
mv ~/.config/dconf/{user,user.bak}
```
This renames dconf file from 'user' to 'user.bak'. Sometimes it might be useful within dist-upgrade for Unity7...
And re-login to Unity7.

Regards.
Tista

---

### Post by zika on 2015-10-17
> **ventrical said:**
> I would first try :```

sudo service lightdm restart
``````
sudo systemctl restart lightdm.service
```in 15.10... Isn't it SystemD default?

---

### Post by giruzz on 2015-10-17
> **tista said:**
> Greetings,

Please git it a try:
```
mv ~/.config/dconf/{user,user.bak}
```
This renames dconf file from 'user' to 'user.bak'. Sometimes it might be useful within dist-upgrade for Unity7...
And re-login to Unity7.

Regards.
Tista

File not found....

:-(

Giruzz

---

### Post by giruzz on 2015-10-17
Service not found.....

Also...tried apt-get updadate & apt-get upgrade and I get a bluethoot error 'no such service'

---

### Post by mc4man on 2015-10-17
> **tista said:**
> Greetings,

Please git it a try:
```
mv ~/.config/dconf/{user,user.bak}
```
This renames dconf file from 'user' to 'user.bak'. Sometimes it might be useful within dist-upgrade for Unity7...
And re-login to Unity7.

Regards.
Tista
Something like that should be done from a tty > reboot. If done from a session then the user file will be restored/written from memory on log out/restart or immediately from any action writing to dconf

---

### Post by sgage on 2015-10-17
> **zika said:**
> ```
sudo systemctl restart lightdm.service
```in 15.10... Isn't it SystemD default?

The old syntax still works - it gets automagically mapped to systemctl. :KS

---

### Post by zika on 2015-10-17
> **sgage said:**
> The old syntax still works - it gets automagically mapped to systemctl. :KS```
# When this machine is running systemd, standard service calls are turned into# systemctl calls.
if [ -n "$is_systemd" ]
then
   UNIT="${SERVICE%.sh}.service"
```Yeap, I know that but it is time for us to get used to Systemd... ;)

---

