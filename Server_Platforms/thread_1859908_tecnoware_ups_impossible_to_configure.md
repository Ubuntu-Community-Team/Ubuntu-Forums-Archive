---
title: "tecnoware ups impossible to configure"
date: 2011-10-14
forum: Server Platforms
---

### Post by andrew.taylor on 2011-10-14
hi all.
I bought a tecnoware LCD ERA 0.65 ups and I'm trying to configure it with an ubuntu 11.04 server through an usb cable.
I tried nut, upsilon and now apcupsd but none of them worked fine.
I know I'm trying to use apcupsd with a non-APC ups ..

Anyway I bet it's a 'usb permissions' issue .. but I don't know how to work around it ..

This is what I get with the lsusb command ..

```
root@c2s-serv:~# lsusb
..
Bus 003 Device 002: ID 0001:0000 Fry's Electronics 
..
```this is the apcupsd conf ..

```
UPSTYPE usb
DEVICE 
POLLTIME 60
LOCKFILE /var/lock
SCRIPTDIR /etc/apcupsd
PWRFAILDIR /etc/apcupsd
NOLOGINDIR /etc
ONBATTERYDELAY 6
BATTERYLEVEL 5
MINUTES 3
TIMEOUT 0
ANNOY 300
ANNOYDELAY 60
NOLOGON disable
KILLDELAY 0
NISIP 127.0.0.1
NISPORT 3551
EVENTSFILE /var/log/apcupsd.events
EVENTSFILEMAX 10
UPSCLASS standalone
UPSMODE disable
STATTIME 0
STATFILE /var/log/apcupsd.status
LOGSTATS off
DATATIME 0

```system's answer to *apcupsd start* command

```
root@serv:~# /etc/init.d/apcupsd start
Starting UPS power management: apcupsd.
root@serv:~# apctest


2011-10-14 16:21:33 apctest 3.14.8 (16 January 2010) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
apctest error termination completed
root@serv:~# 
```.. and *apcupsd status* ..

```
root@serv:~# /etc/init.d/apcupsd status
Error contacting apcupsd @ localhost:3551: Connection refused
root@serv:~# 
```.. anyone can help me? thanx.

---

