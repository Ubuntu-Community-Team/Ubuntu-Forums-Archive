---
title: "Can't access AD Domain User - with AUTOLOGIN  ubuntu 16.04"
date: 2019-01-23
forum: Security
---

### Post by straight-gal on 2019-01-23
Can't access auto-login AD Domain User - ubuntu 16.04




Hello Evereyone!


I configured ubuntu 16.04 with AD Domain user.
I use GNOME display manager and lightdm as login greeter
I can login with the domain user as normal after boot with no problem!
when i configure lightdm for auto login it fail due to authentication problems when reboot


config of /etc/lightdm/lightdm.conf:


> 
[Seat:*]
allow-guest=false
autologin-user=ofk_it_tech@europe.ad.com
autologin-user-timeout=1
autologin-session=lightdm-autologin
user-session=ubuntu






Analyse the lightdm log , shows my domain user : ofk_it_tech  AUTH. FAIL............

/var/log/lightdm/lightdm.log


> 


[+8.83s] DEBUG: Seat seat0: Session authenticated, running command
[+8.83s] DEBUG: Session pid=1328: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+8.83s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+8.83s] DEBUG: Session pid=1328: Logging to /var/log/lightdm/seat0-greeter.log
[+9.03s] DEBUG: Activating VT 7
[+9.03s] DEBUG: Activating login1 session c1
[+9.03s] DEBUG: Seat seat0 changes active session to c1
[+9.04s] DEBUG: Session c1 is already active
[+10.79s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+12.54s] DEBUG: Greeter start authentication for admin_ubuntu
[+12.54s] DEBUG: Session pid=1586: Started with service 'lightdm', username 'admin_ubuntu'
[+12.58s] DEBUG: Session pid=1586: Got 1 message(s) from PAM
[+12.58s] DEBUG: Prompt greeter with 1 message(s)
[+12.84s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+13.05s] DEBUG: Greeter start authentication for [EMAIL="ofk_it_tech@europe.ad.com"]ofk_it_tech@europe.ad.com[/EMAIL]
[+13.05s] DEBUG: Session pid=1586: Sending SIGTERM
[+13.05s] DEBUG: Session pid=1636: Started with service 'lightdm-autologin', username 'ofk_it_tech@europe.ad.com'
[+13.05s] DEBUG: Session pid=1586: Terminated with signal 15
_[+13.05s] DEBUG: Session: Failed during authentication_
[+13.05s] DEBUG: Seat seat0: Session stopped
[+13.53s] DEBUG: Session pid=1636: Authentication complete with return value 7: Authentication failure
[+13.53s] DEBUG: Authenticate result for user [EMAIL="ofk_it_tech@europe.ad.com"]ofk_it_tech@europe.ad.com[/EMAIL]: Authentication failure





switching from local user to the domain use during normal operation also work fine

also when restart the lightdm with :  [COLOR=#242729][FONT=Consolas][/FONT][/COLOR][COLOR=#ff0000][FONT=Consolas][FONT=arial]sudo service lightdm restart [/FONT][/FONT][/COLOR][COLOR=#242729][FONT=Consolas]

[FONT=arial]work fine with auto login of the domain-user.

conclusion:

auto-login with domain user not works with reboot maybe missing some other config.[/FONT]
[/FONT][/COLOR]

---

