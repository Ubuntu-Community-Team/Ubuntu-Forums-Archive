---
title: "UPS with Ubuntu"
date: 2008-08-24
forum: Server Platforms
---

### Post by mansonthomas on 2008-08-24
Hi,

  How well is supported the link between an UPS and a ubuntu server over the USB port ? 

  I've to replace my UPS (which is dead) by a new one, and I wonder if I should look for specific hardware, so that the ubuntu server would be able to shut itself down when the UPS is out of battery.

  Any experience to share? 

Regards,
Thomas.

---

### Post by mrmorris on 2008-08-24
Hey Thomas,

I've only ever played with UPS and desktop, not for server. However let me just say that I was pleasantly surprised to see that when I plugged in my new cheap APC Back-UPS CS 350, Ubuntu 8.04 immediately recognized it and even gave me controls for it up in the Gnome panel, letting me monitor power conditions etc. So I think it's safe to say that the APC units are probably well supported by the generic kernel.

Regards,
Casper

---

### Post by mansonthomas on 2008-08-24
Thanks, that's good news ;)

---

### Post by Heicron on 2008-08-24
Greetings,

I am a new Ubuntu user and just installed an APC backups es. When I plugged in the usb cable nothing happened but the unit does showup on the USB bus. Using Synaptic I installed three apcupsd files. After the installation I could't find anything to configure the UPS with Gnome or anything else. No listing anywhere for UPS.
What am I missing?

Thanks.

---

### Post by mrmorris on 2008-08-24
> **Heicron said:**
> Greetings,

I am a new Ubuntu user and just installed an APC backups es. When I plugged in the usb cable nothing happened but the unit does showup on the USB bus. Using Synaptic I installed three apcupsd files. After the installation I could't find anything to configure the UPS with Gnome or anything else. No listing anywhere for UPS.
What am I missing?

Thanks.

Not even in System > Preferences > Power Management? Perhaps you have more sophisticated configuring requirements but on my machine, Ubuntu (automatically) added a new tab called "On UPS Power" which allows me to specify default actions, alarms etc.

/Casper

---

### Post by Heicron on 2008-08-24
Now I have it. Thanks.
But there is no setting for how long after it goes "on battery" before it begins shutdown. Just a setting for low battery, right?

---

### Post by mrmorris on 2008-08-24
> **Heicron said:**
> Now I have it. Thanks.
But there is no setting for how long after it goes "on battery" before it begins shutdown. Just a setting for low battery, right?

Yeah. I don't know how "low" and "critically low" is defined. I have only seen it "in effect" once during a thunderstorm, but to be perfectly honest I did not feel like sitting around waiting for it to shut down by itself ;)

/Casper

---

### Post by Heicron on 2008-08-24
I don't wait either but there are times when I'm not around to shut it down. That's why I use the shut down time while on battery. I have the two Windows boxes set for about 5 minutes.

Joe

---

### Post by mcaycedo on 2008-09-14
I used to able to see it in 7.04 but I did a fresh install of 8.04 LTS and does not come up at all, dont't have a tab for it.  Any suggestions?  the unit is an APC model 350.

---

### Post by schettj on 2008-09-14
I like apcupsd. It's in the repo...

Mine (I have a couple - on on the main server and one on my PVR) look like this:

[http://www.schettino.us/ups/multimon.cgi](http://www.schettino.us/ups/multimon.cgi)

Edit - sorry missread the question. Most APC UPSs (well modern ones) are very accurate at determining their run time till empty. They talk to the apcupsd and pretty much count down their remaining run time... once it gets to five minutes left you'll get shut down. So it's not "how long until shutdown" its how much time left, which depends on load.

You *can* just edit the config file for it, it's not that complex. Plus that nifty multimon will tell you what apcupsd thinks your runtime on battery is.

---

### Post by KiLaHuRtZ on 2008-09-15
I use CyberPower Systems UPS units with all my servers and desktops.  Most of them are on the network for Nagios to catch SNMP traps and process a shutdown event handler.  However, they have a linux daemon that you can download from their site, pwrstatd, which monitors the UPS via serial or USB.  It also includes some default scripts, which you can edit, to shutdown your system cleanly.  Here is an example of the 'status' and 'config' options.

[USER@HOST ~]$ sudo pwrstat -status

The UPS information shows as following:

	Properties:
		Model Name...................  850VA
		Firmwarm Number.............. 2.202
		Rating Voltage............... 120 V
		Rating Power................. 785 VA (510 Watt)

	Current UPS status:
		State ....................... Normal
		Power Supply by ............. Utility Power
		Utility Voltage ............. 120 V
		Output Voltage............... 119 V
		Utility Frequency ........... 59 Hz
		Battery Capacity ............ 100 %
		Load ........................ 28 %
		Line Interaction............. None

[USER@HOST ~]$ sudo pwrstat -config

Daemon Configuration:

Alarm .............................................. On

Action for Power Failure:

	Delay time since Power failure ............. 300 sec.
	Run script command ......................... On
	Path of script command ..................... /etc/pwrstatd-powerfail.sh
	Duration of command running ................ 0 sec.
	Enable shutdown system ..................... On

Action for Battery Low:

	Dealy time since Battery Low ............... 15 sec.
	Run script command ......................... On
	Path of command ............................ /etc/pwrstatd-lowbatt.sh
	Duration of command running ................ 0 sec.
	Enable shutdown system ..................... On

---

### Post by cariboo on 2008-09-15
I just bought an APC BackUp XS 900 for my server. IT took about five minutes to set it up. Apcupsd is in the repositories. I used this page to set it up:

[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

This is the output of apcaccess:

```
APC      : 001,039,1023
DATE     : Sun Sep 14 23:56:05 PDT 2008
HOSTNAME : Willy
RELEASE  : 3.14.2
VERSION  : 3.14.2 (15 September 2007) debian
UPSNAME  : backup_willy
CABLE    : USB Cable
MODEL    : Back-UPS XS  900 
UPSMODE  : Stand Alone
STARTTIME: Fri Sep 12 22:29:13 PDT 2008
STATUS   : ONLINE 
LINEV    : 126.0 Volts
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
BATTV    : 27.1 Volts
LASTXFER : Automatic or explicit self test
NUMXFERS : 1
XONBATT  : Fri Sep 12 22:30:08 PDT 2008
TONBATT  : 0 seconds
CUMONBATT: 9 seconds
XOFFBATT : Fri Sep 12 22:30:17 PDT 2008
LASTSTEST: Fri Sep 12 22:30:08 PDT 2008
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
MANDATE  : 2008-04-25
SERIALNO : JB0817017004  
BATTDATE : 2099-00-38
NOMINV   : 120
NOMBATTV :  24.0
FIRMWARE : 830.E6 .D USB FW:E6
APCMODEL : Back-UPS XS  900 
END APC  : Sun Sep 14 23:56:41 PDT 2008
```

Jim

---

### Post by kustomjs on 2008-09-15
so if I bought one of this ups would I be able to use a usb cable for the power cord? and still able to use the regular power outlet?

---

### Post by cariboo on 2008-09-15
The usb cable is only for data transfer, you also need a power cable from your computer to the ups. Just as a point of interest usb can only transfer low voltages up to 5v dc.

Jim

---

