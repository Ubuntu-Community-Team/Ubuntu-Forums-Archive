---
title: "apsupsd is not sending mails"
date: 2008-10-18
forum: Server Platforms
---

### Post by NarsilAnduril on 2008-10-18
I'm trying to set up apsupsd to send mails, but I don't get any (8.04 i386 server).

apcupsd does run and see my UPS :

```
diego@pinguin:~$ /etc/init.d/apcupsd status
APC      : 001,044,1103
DATE     : Sat Oct 18 20:10:53 CEST 2008
HOSTNAME : pinguin
RELEASE  : 3.14.2
VERSION  : 3.14.2 (15 September 2007) debian
UPSNAME  : APCCS500
CABLE    : USB Cable
MODEL    : Back-UPS CS 500 
UPSMODE  : Stand Alone
STARTTIME: Sat Oct 18 14:06:09 CEST 2008
STATUS   : ONLINE 
LINEV    : 232.0 Volts
LOADPCT  :  47.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  14.8 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
OUTPUTV  : 230.0 Volts
SENSE    : Medium
DWAKE    : 000 Seconds
DSHUTD   : 000 Seconds
LOTRANS  : 180.0 Volts
HITRANS  : 266.0 Volts
RETPCT   : 000.0 Percent
ITEMP    : 29.2 C Internal
ALARMDEL : Always
BATTV    : 13.5 Volts
LINEFREQ : 50.0 Hz
LASTXFER : Low line voltage
NUMXFERS : 1
XONBATT  : Sat Oct 18 14:06:47 CEST 2008
TONBATT  : 0 seconds
CUMONBATT: 111 seconds
XOFFBATT : Sat Oct 18 14:08:38 CEST 2008
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
SERIALNO : 4B0806P64902  
BATTDATE : 2008-02-01
NOMOUTV  : 230
NOMINV   : 230
NOMBATTV :  12.0
FIRMWARE : 808.q8.I USB FW:q8
APCMODEL : Back-UPS CS 500 
END APC  : Sat Oct 18 20:11:25 CEST 2008

```

and status change are detected :

```
diego@pinguin:~$ /etc/init.d/apcupsd status
APC      : 001,044,1103
DATE     : Sat Oct 18 20:10:53 CEST 2008
HOSTNAME : pinguin
RELEASE  : 3.14.2
VERSION  : 3.14.2 (15 September 2007) debian
UPSNAME  : APCCS500
CABLE    : USB Cable
MODEL    : Back-UPS CS 500 
UPSMODE  : Stand Alone
STARTTIME: Sat Oct 18 14:06:09 CEST 2008
STATUS   : ONLINE 
LINEV    : 232.0 Volts
LOADPCT  :  47.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  14.8 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
OUTPUTV  : 230.0 Volts
SENSE    : Medium
DWAKE    : 000 Seconds
DSHUTD   : 000 Seconds
LOTRANS  : 180.0 Volts
HITRANS  : 266.0 Volts
RETPCT   : 000.0 Percent
ITEMP    : 29.2 C Internal
ALARMDEL : Always
BATTV    : 13.5 Volts
LINEFREQ : 50.0 Hz
LASTXFER : Low line voltage
NUMXFERS : 1
XONBATT  : Sat Oct 18 14:06:47 CEST 2008
TONBATT  : 0 seconds
CUMONBATT: 111 seconds
XOFFBATT : Sat Oct 18 14:08:38 CEST 2008
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
SERIALNO : 4B0806P64902  
BATTDATE : 2008-02-01
NOMOUTV  : 230
NOMINV   : 230
NOMBATTV :  12.0
FIRMWARE : 808.q8.I USB FW:q8
APCMODEL : Back-UPS CS 500 
END APC  : Sat Oct 18 20:11:25 CEST 2008
diego@pinguin:~$ /etc/init.d/apcupsd status
APC      : 001,044,1103
DATE     : Sat Oct 18 20:13:31 CEST 2008
HOSTNAME : pinguin
RELEASE  : 3.14.2
VERSION  : 3.14.2 (15 September 2007) debian
UPSNAME  : APCCS500
CABLE    : USB Cable
MODEL    : Back-UPS CS 500 
UPSMODE  : Stand Alone
STARTTIME: Sat Oct 18 14:06:09 CEST 2008
**STATUS   : ONBATT **
LINEV    : 000.0 Volts
LOADPCT  :  47.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  14.8 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
OUTPUTV  : 230.0 Volts
SENSE    : Medium
DWAKE    : 000 Seconds
DSHUTD   : 000 Seconds
LOTRANS  : 180.0 Volts
HITRANS  : 266.0 Volts
RETPCT   : 000.0 Percent
ITEMP    : 29.2 C Internal
ALARMDEL : Always
BATTV    : 12.8 Volts
LINEFREQ : 50.0 Hz
LASTXFER : Low line voltage
NUMXFERS : 2
XONBATT  : Sat Oct 18 20:13:31 CEST 2008
TONBATT  : 4 seconds
CUMONBATT: 115 seconds
XOFFBATT : Sat Oct 18 14:08:38 CEST 2008
SELFTEST : NO
STATFLAG : 0x07040010 Status Flag
SERIALNO : 4B0806P64902  
BATTDATE : 2008-02-01
NOMOUTV  : 230
NOMINV   : 230
NOMBATTV :  12.0
FIRMWARE : 808.q8.I USB FW:q8
APCMODEL : Back-UPS CS 500 
END APC  : Sat Oct 18 20:13:35 CEST 2008

```

In fact, broadcasts are ok :

```
Broadcast Message from root@pinguin                                            
        (somewhere) at 20:13 ...                                               
                                                                               
Power failure on UPS APCCS500. Running on batteries.                           
                                                                               
                                                                               
Broadcast Message from root@pinguin                                            
        (somewhere) at 20:13 ...                                               
                                                                               
Power has returned on UPS APCCS500... 
```

and scripts are correctly changed (I think, didn't find a lot of infos)

```
#!/bin/sh
#
# This shell script if placed in /etc/apcupsd
# will be called by /etc/apcupsd/apccontrol when the UPS
# goes on batteries.
# We send an email message to root to notify him.
#
SYSADMIN=root
APCUPSD_MAIL="my@fakemail.com"

HOSTNAME=`hostname`
MSG="$HOSTNAME Fonctionnement sur batterie !!!"
#
(
   echo "Subject: $MSG"
   echo " "
   echo "$MSG"
   echo " "
   /sbin/apcaccess status
) | $APCUPSD_MAIL -s "$MSG" $SYSADMIN
exit 0

```

But I don't get any email ...

Of course, both mail and mailx do work and I get all notification emails from mdadm and mysql.

Any suggestion ?

Thanks

Diego

---

