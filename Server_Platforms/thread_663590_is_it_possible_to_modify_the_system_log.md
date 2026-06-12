---
title: "is it possible to modify the system log?"
date: 2008-01-10
forum: Server Platforms
---

### Post by someoneouthere on 2008-01-10
is it? by edting the the../var/log....
so the next time i open system log to "have" modified results?

asking because i've seen weird things.....

---

### Post by k_grdn on 2008-01-10
Hi,

You can use the [COLOR="Black"]logger[/COLOR] command to write directly to syslog:

Regards,

k_grdn

---

### Post by someoneouthere on 2008-01-10
i'd like to check the times my comruter really  turned on...
can i check it without the system.log?

---

### Post by k_grdn on 2008-01-10
HI,

uptime will tell you how long its been running.

k_grdn

---

### Post by someoneouthere on 2008-01-10
> **k_grdn said:**
> HI,

uptime will tell you how long its been running.

k_grdn
thanks
usefull but i  want to check the specific times the computer turned on and the logins...

---

### Post by k_grdn on 2008-01-10
Hi,

Try:

w - Show who is logged on and what they are doing also try lastlog and top will gave similar output.

14:52:05 up 39 days,  2:11,  2 users,  load average: 0.00, 0.00, 0.00

2:11 is how long the systems been running you could write a script to take that value away from the current date(time).

Maybe someone already has?

k_grdn

---

### Post by k_grdn on 2008-01-10
> 
14:52:05 up 39 days, 2:11, 2 users, load average: 0.00,0.00,0.00

date -d "today -2 hours -11 minutes"

date -d "today -`uptime|awk '{print $5}'|sed -e 's/,$//' -e 's/:/ /'|cut -d' ' -f1` hours -`uptime|awk '{print $5}'|sed -e 's/,$//' -e 's/:/ /'|cut -d' ' -f2` minutes"


k_grdn

---

### Post by someoneouthere on 2008-01-10
let me put it this way.... i want to check is someone turned on or  logged in between 
auth.log:
```
Jan 10 00:07:56 someoneouthere gdm[5794]: pam_unix(gdm:session): session closed for user somethink
Jan 10 10:46:25 someoneouthere su[5131]: Successful su for clamav by root
```

without using the system.log...

---

### Post by k_grdn on 2008-01-10
Not sure about that,  what about locking down your logfiles with 600 permissions and ownership, also chattr +a so your logs can only be appended to.

If your system is being tampered with why not install tripwire on R/O media and see what is actually going on or set up a central syslog server or even mail yourself a copy every so often.

Regards,

k_grdn

---

### Post by someoneouthere on 2008-01-10
> **k_grdn said:**
> Not sure about that,  what about locking down your logfiles with 600 permissions and ownership, also chattr +a so your logs can only be appended to.

If your system is being tampered with why not install tripwire on R/O media and see what is actually going on or set up a central syslog server or even mail yourself a copy every so often.

Regards,

k_grdn

nice tool... but where can i find a good tutorial on this one :)

---

### Post by someoneouthere on 2008-01-10
but ... i don't really need a server tool at this point
just want to check this specific thing...

---

### Post by k_grdn on 2008-01-10
Tripwire (as root usr)

apt-get install tripwire

cd /etc/tripwire

twadmin --generate-keys --site-keyfile $HOSTNAME-site.key

twadmin --generate-keys --local-keyfile $HOSTNAME-local.key

edit tw.cfg with key names, and twpol.txt add proc entries, change key name

twcfg.txt:DBFILE        =/etc/tripwire/$(HOSTNAME).twd
twcfg.txt:REPORTFILE    =/var/lib/tripwire/report/$(HOSTNAME)-$(DATE).twr
twcfg.txt:SITEKEYFILE   =/etc/tripwire$(HOSTNAME)-site.key
twcfg.txt:LOCALKEYFILE  =/etc/tripwire/$(HOSTNAME)-local.key

twpol.txt: $(TWVAR)/$(HOSTNAME).twd        -> $(SEC_CONFIG) -i ;
twpol.txt: $(TWETC)/$(HOSTNAME)-local.key  -> $(SEC_BIN) ;

Create tw.cfg - twadmin --create-cfgfile --cfgfile tw.cfg --site-keyfile $HOSTNAME-site.key twcfg.txt

Create tw.pol - twadmin --create-polfile --cfgfile tw.cfg --polfile tw.pol --site-keyfile $HOSTNAME-site.key twpol.txt

Add these entries to twpol.txt:

{
        /dev                     -> $(Device) ;
        /proc/devices            -> $(Device) ;
        /proc/net                -> $(Device) ;
        /proc/sys                -> $(Device) ;
        /proc/cpuinfo            -> $(Device) ;
        /proc/modules            -> $(Device) ;
        /proc/mounts             -> $(Device) ;
        /proc/dma                -> $(Device) ;
        /proc/filesystems        -> $(Device) ;
        /proc/interrupts         -> $(Device) ;
        /proc/driver/rtc         -> $(Device) ;
        /proc/ioports            -> $(Device) ;
        /proc/kcore              -> $(Device) ;
        /proc/self               -> $(Device) ;
        /proc/kmsg               -> $(Device) ;
        /proc/stat               -> $(Device) ;
        /proc/loadavg            -> $(Device) ;
        /proc/uptime             -> $(Device) ;
        /proc/locks              -> $(Device) ;
        /proc/version            -> $(Device) ;
        /proc/mdstat             -> $(Device) ;
        /proc/meminfo            -> $(Device) ;
        /proc/cmdline            -> $(Device) ;
        /proc/misc               -> $(Device) ;

}


Create database - tripwire --init --cfgfile tw.cfg --polfile tw.pol --site-keyfile $HOSTNAME-site.key --local-keyfile $HOSTNAME-local.key (Iron out any errors at this stage by editing twpol.txt, and redo steps, theres entries relating to /root/.* which throw up errors remove or tweak at need)

Above installs to filesystem.

R/O media

Amend twpol.txt:

	TWD = /media/twd;

        $(TWD)/$(HOSTNAME).twd  -> $(SEC_CONFIG) -i ;
        $(TWD)/$(HOSTNAME)-local.key    -> $(SEC_BIN) ;
        $(TWD)/$(HOSTNAME)-site.key             -> $(SEC_BIN) ;

twadmin --create-polfile --cfgfile tw.cfg --polfile tw.pol --site-keyfile $HOSTNAME-site.key twpol.txt

Recreate DB:

tripwire --init --cfgfile tw.cfg --polfile tw.pol --site-keyfile $HOSTNAME-site.key --local-keyfile $HOSTNAME-local.key

*Burn db & keys to disk:

	cdrecord --dev=3,0,0--blank=fast
	mkisofs -r -o cd_image *.twd
	cdrecord -v speed=1 dev=3,0,0 cd_image

Modify twcfg-nw.txt, amend:

	DBFILE        =/media/twd/$(HOSTNAME).twd
	SITEKEYFILE   =/media/twd/$(HOSTNAME)-site.key
	LOCALKEYFILE  =/media/twd/$(HOSTNAME)-local.key

twadmin --create-cfgfile --cfgfile /etc/tripwire/tw-nw.cfg --site-keyfile /media/twd/$HOSTNAME-site.key /etc/tripwire/twcfg-nw.txt

rm /etc/tripwire*.key & /var/lib/tripwire/*.twd

tripwire --check

Regards,

k_grdn

---

### Post by someoneouthere on 2008-01-10
tried several times couldn't install...

---

### Post by k_grdn on 2008-01-10
??? more info ???

sudo apt-get install

---

