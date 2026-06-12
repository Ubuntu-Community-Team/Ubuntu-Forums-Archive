---
title: "Configure TATA Photon+ EC1261 HUAWEI on ubuntu"
date: 2010-10-11
forum: Server Platforms
---

### Post by Thyagaraj on 2010-10-11
I'm running ubuntu 10.04. I have a newly purchased TATA Photon+ Internet connection which supports Windows and Mac. On the Internet I found a article saying that it could be configured on Linux. I followed the steps to install it on Ubuntu from this [link text]("http://digitizor.com/2010/06/28/how-to-use-tata-photon-plus-in-ubuntu-10-04-lucid-lynx/"). I am still not able to get online, and need some help.

  Also, it is very slow, but I was told that I would see speeds up to 3.1MB.

  I dont have wvdial installed and cannot install it from apt as I'm not connected to internet

---

### Post by Thyagaraj on 2010-10-16
Booting from windows I dowloaded "wvdial" .deb package and tried to install on ubuntu but it's ended with dependency problem. Automatically, don't know how, I got connected to internet only for once. Immediately I installed wvdial package after this I followed the tutorials(I've uploaded the files) . From then it's showing that the device is connected in the network connections but no internet connection. Once I disable the device, it won't show as connected again and I'll have to restart my system. Sometimes the device itself not detected(wondering if there is any command to re-read the all devices).
 
Output of **wvdialconf /etc/wvdial.cof**:
```
[COLOR=#222222]#wvdialconf /etc/wvdial.conf[/COLOR]
 
[COLOR=#222222]Editing `/etc/wvdial.conf'.[/COLOR]
 
[COLOR=#222222]Scanning your serial ports for a modem.[/COLOR]
 
[COLOR=#222222]ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud[/COLOR]
[COLOR=#222222]ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud[/COLOR]
[COLOR=#222222]ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.[/COLOR]
[COLOR=#222222]Modem Port Scan<*1>: S1   S2   S3   [/COLOR]
[COLOR=#222222]WvModem<*1>: Cannot get information for serial port.[/COLOR]
[COLOR=#222222]ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud[/COLOR]
[COLOR=#222222]ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud[/COLOR]
[COLOR=#222222]ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.[/COLOR]
[COLOR=#222222]WvModem<*1>: Cannot get information for serial port.[/COLOR]
[COLOR=#222222]ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud[/COLOR]
[COLOR=#222222]ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud[/COLOR]
[COLOR=#222222]ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.[/COLOR]
[COLOR=#222222]WvModem<*1>: Cannot get information for serial port.[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: ATQ0 V1 E1 -- OK[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: HUAWEI TECHNOLOGIES CO., LTD[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: Speed 9600: AT -- OK[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: Max speed is 9600; that should be safe.[/COLOR]
[COLOR=#222222]ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK[/COLOR]
 
[COLOR=#222222]Found a modem on /dev/ttyUSB2.[/COLOR]
[COLOR=#222222]Modem configuration written to /etc/wvdial.conf.[/COLOR]
[COLOR=#222222]ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"[/COLOR]
 

```
 
 
 
Output of **wvdial**:
```
[COLOR=#222222]#wvdial[/COLOR]
[COLOR=#222222]--> WvDial: Internet dialer version 1.60[/COLOR]
[COLOR=#222222]--> Cannot get information for serial port.[/COLOR]
[COLOR=#222222]--> Initializing modem.[/COLOR]
[COLOR=#222222]--> Sending: ATZ[/COLOR]
[COLOR=#222222]ATZ[/COLOR]
[COLOR=#222222]OK[/COLOR]
[COLOR=#222222]--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0[/COLOR]
[COLOR=#222222]ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0[/COLOR]
[COLOR=#222222]OK[/COLOR]
[COLOR=#222222]--> Sending: AT+CRM=1[/COLOR]
[COLOR=#222222]AT+CRM=1[/COLOR]
[COLOR=#222222]OK[/COLOR]
[COLOR=#222222]--> Modem initialized.[/COLOR]
[COLOR=#222222]--> Sending: ATDT#777[/COLOR]
[COLOR=#222222]--> Waiting for carrier.[/COLOR]
[COLOR=#222222]ATDT#777[/COLOR]
[COLOR=#222222]CONNECT[/COLOR]
[COLOR=#222222]--> Carrier detected.  Starting PPP immediately.[/COLOR]
[COLOR=#222222]--> Starting pppd at Sat Oct 16 15:30:47 2010[/COLOR]
[COLOR=#222222]--> Pid of pppd: 5681[/COLOR]
[COLOR=#222222]--> Using interface ppp0[/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> local  IP address 14.96.147.104[/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> remote IP address 172.29.161.223[/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> primary   DNS address 121.40.152.90[/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
[COLOR=#222222]--> secondary DNS address 121.40.152.100  [/COLOR]
[COLOR=#222222]--> pppd: (u;[08]@s;[08]`{;[08][/COLOR]
 

```
 
 
Output of log message **/var/log/messages**:
```
[COLOR=#222222]Oct 16 15:29:44 avyakta-desktop pppd[5119]: secondary DNS address 121.242.190.180[/COLOR]
[COLOR=#222222]Oct 16 15:29:58 desktop pppd[5119]: Terminating on signal 15[/COLOR]
[COLOR=#222222]Oct 16 15:29:58 desktop pppd[5119]: Connect time 0.3 minutes.[/COLOR]
[COLOR=#222222]Oct 16 15:29:58 desktop pppd[5119]: Sent 0 bytes, received 177 bytes.[/COLOR]
[COLOR=#222222]Oct 16 15:29:58 desktop pppd[5119]: Connection terminated.[/COLOR]
[COLOR=#222222]Oct 16 15:30:47 desktop pppd[5681]: pppd 2.4.5 started by root, uid 0[/COLOR]
[COLOR=#222222]Oct 16 15:30:47 desktop pppd[5681]: Using interface ppp0[/COLOR]
[COLOR=#222222]Oct 16 15:30:47 desktop pppd[5681]: Connect: ppp0 <--> /dev/ttyUSB2[/COLOR]
[COLOR=#222222]Oct 16 15:30:47 desktop pppd[5681]: CHAP authentication succeeded[/COLOR]
[COLOR=#222222]Oct 16 15:30:47 desktop pppd[5681]: CHAP authentication succeeded[/COLOR]
[COLOR=#222222]Oct 16 15:30:48 desktop pppd[5681]: local  IP address 14.96.147.104[/COLOR]
[COLOR=#222222]Oct 16 15:30:48 desktop pppd[5681]: remote IP address 172.29.161.223[/COLOR]
[COLOR=#222222]Oct 16 15:30:48 desktop pppd[5681]: primary   DNS address 121.40.152.90[/COLOR]
[COLOR=#222222]Oct 16 15:30:48 desktop pppd[5681]: secondary DNS address 121.40.152.100[/COLOR]

```

---

### Post by ashok.ericsson on 2010-10-16
Hi,
 
Did you checked only the CHAP in PPP settings in network manager and also disable all the header compression ? In my case with Ubuntu9.10 and same device I didn't even needed the wvdial and it worked really out of the box after doing the above corrections.
 
BR//Ashok

---

