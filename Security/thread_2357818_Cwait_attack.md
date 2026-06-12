---
title: "Cwait attack ?"
date: 2017-04-06
forum: Security
---

### Post by Claymenia on 2017-04-06
Hi everyone, i come here for find an urgently help !

I've contacted OVH and PLESK support, and the both let's me alone with this problem.

Since few week, but really few days, my server (under ubuntu 16.04 and PLesk onyx 17) use progressivly fully ram memory, and after created swap file, fully swap.

For ovh and plesk, seem is an Cwait Attack internal (website 1 to website 2 / 3 / 4 ... inside my server). example :

```
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52550 CLOSE_WAIT 2309/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52510 CLOSE_WAIT 1021/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52272 CLOSE_WAIT 3661/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52590 CLOSE_WAIT 2356/apache2
tcp6 1 0 193.70.73.13:7080 193.70.73.17:53224 CLOSE_WAIT 2328/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52544 CLOSE_WAIT 2341/apache2
tcp6 1 0 193.70.73.13:7080 193.70.73.17:53226 CLOSE_WAIT 2374/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52562 CLOSE_WAIT 17922/apache2
tcp6 0 0 193.70.73.13:7080 193.70.73.17:53242 ESTABLISHED 2358/apache2
tcp6 0 0 193.70.73.12:7080 193.70.73.17:39022 TIME_WAIT -
tcp6 1 0 193.70.73.13:7080 193.70.73.17:52780 CLOSE_WAIT 25829/apache2
tcp6 0 0 193.70.73.13:7081 193.70.73.17:52678 ESTABLISHED 4168/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52164 CLOSE_WAIT 2485/apache2
tcp6 1 0 193.70.73.13:7080 193.70.73.17:53126 CLOSE_WAIT 809/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52496 CLOSE_WAIT 930/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52602 CLOSE_WAIT 2403/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52274 CLOSE_WAIT 3672/apache2
tcp6 0 0 193.70.73.18:7080 193.70.73.17:48888 TIME_WAIT -
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52572 CLOSE_WAIT 1023/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52650 CLOSE_WAIT 862/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52136 CLOSE_WAIT 26306/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52556 CLOSE_WAIT 2304/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52580 CLOSE_WAIT 918/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52546 CLOSE_WAIT 25812/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52578 CLOSE_WAIT 2324/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52560 CLOSE_WAIT 25837/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52156 CLOSE_WAIT 17938/apache2
tcp6 1 0 193.70.73.13:7080 193.70.73.17:52778 CLOSE_WAIT 3633/apache2
tcp6 1 0 193.70.73.13:7080 193.70.73.17:53124 CLOSE_WAIT 369/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52276 CLOSE_WAIT 3668/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52564 CLOSE_WAIT 2313/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52576 CLOSE_WAIT 4005/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52548 CLOSE_WAIT 806/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52298 CLOSE_WAIT 3684/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52144 CLOSE_WAIT 3600/apache2
tcp6 0 0 193.70.73.13:7081 193.70.73.17:52676 ESTABLISHED 2437/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52150 CLOSE_WAIT 405/apache2
tcp6 32 0 193.70.73.13:7081 193.70.73.17:52596 CLOSE_WAIT 4009/apache2
```

Yesterday i llok (when i block and change few website ip) a listen to external ip. example : 

```
tcp6 0 0 193.70.73.13:3306 222.186.58.235:3427 TIME_WAIT -
tcp6 0 0 193.70.73.16:3306 222.186.58.235:2207 TIME_WAIT -
tcp6 0 0 193.70.73.12:3306 222.186.58.235:3186 TIME_WAIT -
tcp6 0 0 193.70.73.17:3306 222.186.58.235:3033 TIME_WAIT -
tcp6 0 0 193.70.73.13:7081 193.70.73.16:48680 TIME_WAIT -
tcp6 0 0 193.70.73.12:3306 222.186.58.235:1888 TIME_WAIT -
tcp6 0 0 193.70.73.18:3306 222.186.58.235:1991 TIME_WAIT -
tcp6 0 0 193.70.73.16:7080 193.70.73.16:52488 TIME_WAIT -
tcp6 0 0 193.70.73.16:7080 193.70.73.16:52476 TIME_WAIT -
tcp6 0 0 193.70.73.13:7081 193.70.73.16:48712 TIME_WAIT -
tcp6 0 0 193.70.73.17:3306 222.186.58.235:1765 TIME_WAIT -
tcp6 0 0 193.70.73.16:7080 193.70.73.16:52484 TIME_WAIT -
tcp6 0 0 193.70.73.16:7080 193.70.73.16:52474 TIME_WAIT -
tcp6 0 0 193.70.73.13:7081 193.70.73.16:48762 TIME_WAIT -
tcp6 0 0 193.70.73.13:3306 222.186.58.235:4088 TIME_WAIT -
tcp6 0 0 193.70.73.16:7080 193.70.73.16:52482 TIME_WAIT -
tcp6 0 0 193.70.73.16:7080 193.70.73.16:52490 TIME_WAIT -
tcp6 0 0 193.70.73.16:3306 222.186.58.235:4308 TIME_WAIT -
```

I've try to reconfigure all domain, repair web, but without any success !

I've change one ip, first target, 193.70.73.16 by 193.70.73.12 and i've limited the saturation.

I've wrok on to 5:00 am, and when i go sleep, all is normal. morning same. And this afternoon, suddently, all my 15 Go of ram are again used (by the first log posted)... and server is too slow, even reboot command doesn't work !

If i make an htop, i've lot of process for /usr/sbin/mysqld and php-fpm: pool sttanding.com (main website in 193.70.73.13 who attack/connect to others !)

Can you help me plz, i'm desesperate !

---

### Post by Habitual on 2017-04-06
Where's there's one, there's another. This blocks that whole netblock:
```
iptables -I INPUT -s 193.70.0.0/17 -j REJECT --reject-with icmp-host-unreachable
```
Rebooting flushes iptables rules.

---

### Post by Claymenia on 2017-04-06
Thx for your answer but if use your command, i block my others websites no ?

On my serveur :
- 193.70.0.13 -> main website
- 193.70.0.12 -> website 02
- 192.70.0.17 -> website 03
- 192.70.0.18 -> website 04
- 149.202.161.120 -> server ip

[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by Habitual on 2017-04-06
Yes. It would block all 193.70.x.x

but not 192.70 nor 149.202.x.x

---

