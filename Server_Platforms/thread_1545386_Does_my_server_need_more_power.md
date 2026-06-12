---
title: "Does my server need more power?"
date: 2010-08-03
forum: Server Platforms
---

### Post by wlraider70 on 2010-08-03
I running Ubuntu desktop on an old AMD 32bit with 1 gig of ram. Its being used as a server.

I'm backing up my laptops (via a shared folder and client program)
streaming music to my xbox via ustream
sharing folders i have 2 HDD and a usb hard drive via samba
im running DNS and DHCP via Bind9

I have... 
a windows XP laptop
a mac OS X 10.4
A ununtu 10.04 lappy
an XBOX 360
2 iphones

So I'm having two problems...
1) last night the server froze (im not sure why, I couldn't find a pertinent error log or i was looking in the wrong place...
However i do know it was during or shortly after my windows laptop backed up. 



2) after the reboot I was trying to stream music to my xbox and it kept stopping. once i think because i told my unubtu lappy to 
update. It is using wireless G



So could i be doing too much?
I do have a DD-WRT router but its not running DHCP
I also run the Ubuntu GUI 9 im just getting the hang of SSH and command line.

Any thoughts?

---

### Post by WinstonChurchill on 2010-08-04
Did you check these log files for the times/dates your server froze? You'll see some of the same entries in more than one of these files, but  if you know what time/date your looking for, it shouldn't be too hard  to sift through:
```

/var/log/messages
/var/log/kern.log
/var/log/syslog
/var/log/daemon.log

```If you could attach a copy of your server's '/var/log/dmesg' file, that might help as well.

I doubt your problem is with your server being too lightweight... it's probably due to some sort of hardware issue. How exactly does it behave when it freezes? Does the HDD light in the case keep blinking? Is there any text on the console screen? Can you still ping it?

---

### Post by tgalati4 on 2010-08-04
Do you have an UPS on the computer?  My UPS has tracked 44 micro-outages since May 29th.  Of course, the utility company was replacing lines in the neighborhood.  They do it live--sporting job!

APC      : 001,050,1239
DATE     : Tue Aug 03 21:59:11 PDT 2010
HOSTNAME : washme
RELEASE  : 3.14.2
VERSION  : 3.14.2 (15 September 2007) debian
UPSNAME  : bckpr420
CABLE    : Custom Cable Smart
MODEL    : BACK-UPS PRO 420
UPSMODE  : Stand Alone
STARTTIME: Sat May 29 22:21:24 PDT 2010
STATUS   : ONLINE 
LINEV    : 117.3 Volts
LOADPCT  :  11.7 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  23.0 Minutes
MBATTCHG : 30 Percent
MINTIMEL : 10 Minutes
MAXTIME  : 0 Seconds
MAXLINEV : 118.0 Volts
MINLINEV : 117.3 Volts
OUTPUTV  : 117.3 Volts
SENSE    : High
DWAKE    : 000 Seconds
DSHUTD   : 020 Seconds
DLOWBATT : 02 Minutes
LOTRANS  : 106.0 Volts
HITRANS  : 127.0 Volts
RETPCT   : 000.0 Percent
ALARMDEL : 5 seconds
BATTV    : 13.8 Volts
LINEFREQ : 60.0 Hz
LASTXFER : Unacceptable line voltage changes
NUMXFERS : 44
XONBATT  : Mon Aug 02 18:36:29 PDT 2010
TONBATT  : 0 seconds
CUMONBATT: 71 seconds
XOFFBATT : Mon Aug 02 18:36:30 PDT 2010
SELFTEST : NO
STESTI   : 336
STATFLAG : 0x07000008 Status Flag
REG1     : 0x00 Register 1
REG2     : 0x00 Register 2
REG3     : 0x00 Register 3
MANDATE  : 04/02/98
SERIALNO : FB9814345084
BATTDATE : 27/10/09
NOMOUTV  : 115
NOMBATTV :  12.0
FIRMWARE : 11.1.D
APCMODEL : DWD
END APC  : Tue Aug 03 22:00:06 PDT 2010

All it takes is one micro-outage for your machine to freeze.

---

### Post by LightningCrash on 2010-08-04
"2) after the reboot I was trying to stream music to my xbox and it kept stopping. once i think because i told my unubtu lappy to
update. It is using wireless G"

When my laptop would backup over WiFi, my Xbox would do the same thing. Also, Netflix on the Wii would die.
I moved the Wii to ethernet and it was fine.
ETA: My XBOX was on WiFi as well.

---

