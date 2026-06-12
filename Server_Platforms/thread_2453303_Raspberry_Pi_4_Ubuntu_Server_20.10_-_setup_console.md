---
title: "Raspberry Pi 4 Ubuntu Server 20.10 - setup consoleblank parameter"
date: 2020-11-07
forum: Server Platforms
---

### Post by jgrincho on 2020-11-07
I am new to Ubuntu Server on Raspberry Pi 4 and I am trying to setup _consoleblank_ to 60secs so my console will black out when not being used. I am using a Raspberry TouchScreen and everything else works fine. I can "_setterm --blank 1_" from the console itself and I get the desired effect but unfortunately I cannot set the parameter at boot. 

I have tried using _/boot/firmware/config.txt_, where I set the lcd-rotate=2 with full success, but nothing happens.
I have tried also to create a _/etc/init.d/setterm_ script but again nothing happens. 

Any hint?

---

### Post by jgrincho on 2020-11-09
And the answer is... (tanks to David C. Rankin post in ArchLinux):

Put this into /etc/systemd/system/setconsole.service... 

``` 
[Unit] 
Description=Enable virtual console blanking and poweroff 

[Service] 
Type=oneshot 
Environment=TERM=linux 
StandardOutput=tty 
TTYPath=/dev/console 
ExecStart=/usr/bin/setterm -blank 1 -powerdown 1 

[Install] 
WantedBy=multi-user.target 
``` 

...then do `systemctl enable setconsole.service`.

---

