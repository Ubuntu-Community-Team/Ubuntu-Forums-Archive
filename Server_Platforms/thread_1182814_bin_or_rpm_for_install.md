---
title: "bin or rpm for install"
date: 2009-06-09
forum: Server Platforms
---

### Post by andyrowe on 2009-06-09
Hi everyone
Still new to Ubuntu server. I purchased a UPS (universal power supply) with powerchute software. Basically the UPS includes a cable and software that shuts the computer down if power is lost and the battery begins to run down. The Linux version includes both an RPM file and a bin file. Instructions say I can use either to install the software.
I've only ever used apt-get to install software. Could someone explain which file to install and how to do it.

---

### Post by ajwak95 on 2009-06-09
You cannot use RPM, as they are for Red Hat based distro's, e.g Red Hat, CentOS, or Fedora. Search around on the forums for the tutorials on the .bin (I haven't messed with a bin file for a while :D)

---

### Post by zharmad on 2009-06-09
You may be able to convert that RPM to a .deb with alien.

---

### Post by mocoloco on 2009-06-09
To be technically fair you *can* install an RPM, using a program called alien to convert it to a DEB, but if there's a bin use it instead, I would go for converting an RPM as a last resort.

To install the bin file you may first have to make it executable.
Open a terminal, navigate to the directory where it is.
Do "chmod +x <filename>" to make it executable.  Then do "./<filename>" or "sudo ./<filename>" to install, depending on if you need to do so as root (which you probably do).

---

### Post by cariboo on 2009-06-09
If your ups is manufactured by APC, there is software in the repositories to manage it. the name of the package is apcupsd. once you have installed it all you have to do is configure /etc/apcupsd/apcupsd.conf to tell it what type of cable you are using and what type of interface the ups has.

In my case I had to add:

```
UPSTYPE usb
```

to the config file, and just restarted the service:

```
sudo /etc/init.d/apcupsd restart
```

Once you have the service running, at the prompt type:

```
sudo apcaccess
```

you should get an output that looks something like this:

```
sudo apcaccess
APC      : 001,040,1038
DATE     : Tue Jun 09 12:10:04 PDT 2009
HOSTNAME : willy
RELEASE  : 3.14.4
VERSION  : 3.14.4 (18 May 2008) debian
UPSNAME  : willy
CABLE    : Custom Cable Smart
MODEL    : Back-UPS XS  900 
UPSMODE  : Stand Alone
STARTTIME: Thu Apr 30 16:48:45 PDT 2009
STATUS   : ONLINE 
LINEV    : 123.0 Volts
LOADPCT  :  16.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  55.4 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
SENSE    : Medium
LOTRANS  : 088.0 Volts
HITRANS  : 139.0 Volts
ALARMDEL : Always
BATTV    : 26.9 Volts
LASTXFER : Low line voltage
NUMXFERS : 7
XONBATT  : Wed May 27 15:15:29 PDT 2009
TONBATT  : 0 seconds
CUMONBATT: 16 seconds
XOFFBATT : Wed May 27 15:15:31 PDT 2009
LASTSTEST: Thu May 14 13:43:39 PDT 2009
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
MANDATE  : 2008-04-25
SERIALNO : JB0817017004  
BATTDATE : 2099-00-38
NOMINV   : 120 Volts
NOMBATTV :  24.0 Volts
NOMPOWER : 540 Watts
FIRMWARE : 830.E6 .D USB FW:E6
APCMODEL : Back-UPS XS  900 
END APC  : Tue Jun 09 12:10:56 PDT 2009
```

---

### Post by andyrowe on 2009-06-09
mocoloco: thanks for the step by step including code. Always helpful for a noob
 
cariboo907: Thank you, it is indeed a APC. It came with both cables and although the box does have a serial port I plan to do the usb. Going to try, will let you know how it goes.

---

### Post by andyrowe on 2009-06-10
Well I installed the app and added usb to the upstype line in the conf file but when I type sudo apcaccess I get:
Error contacting apcupsd @ localhost:3551: connection refused
I'm using puTTY to access the headless server with my MS workstation

---

