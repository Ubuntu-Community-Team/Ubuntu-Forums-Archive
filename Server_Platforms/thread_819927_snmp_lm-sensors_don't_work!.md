---
title: "snmp lm-sensors don't work!"
date: 2008-06-05
forum: Server Platforms
---

### Post by andremzenun on 2008-06-05
Hello all!
This is my first message to this forum!

I have installed a new copy of Ubuntu 8.04LTS Server Edition
and I had it with all the updates available at the present moment!

Today I have installed lm_sensors and snmp by apt:

ii  libsensors3  1:2.10.5-3ubuntu1
ii  libsensors4  1:3.0.0-4ubuntu1
ii  lm-sensors   1:3.0.0-4ubuntu1
ii  snmp         5.4.1~dfsg-4ubuntu4
ii  snmpd        5.4.1~dfsg-4ubuntu4

I configure the sensors and have some output from the sensors command! The snmp works also, because I have cacti monitoring it's interface.

Today I try to use snmp to monitor the sensors from cacti and have no success, I also tried in the command line using snmpwalk but no success!

Some one can give some help? I have a debian server with similar setup and the snmp + lm_sensors works! I don't know if the version of the package lm-sensors and libsensors have some influence here, because the packages on ubuntu are newer!

Thanks in advance!

André

---

### Post by andremzenun on 2008-06-09
Wow!! No one??

---

### Post by gtdaqua on 2008-06-10
whats the output of snmpwalk?

can you post your "/etc/snmp/snmpd.conf" and "etc/default/snmpd"?

---

### Post by andremzenun on 2008-06-10
[B][U]Hello thanks for the reply!
Well here is my configuration files:

/etc/default/snmpd - it's almost the default[/U][/B]
# This file controls the activity of snmpd and snmptrapd

# MIB directories.  /usr/share/snmp/mibs is the default, but
# including it here avoids some strange problems.
export MIBDIRS=/usr/share/snmp/mibs

# snmpd control (yes means start daemon).
SNMPDRUN=yes

# snmpd options (use syslog, close stdin/out/err).
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 0.0.0.0'

# snmptrapd control (yes means start daemon).  As of net-snmp version
# 5.0, master agentx support must be enabled in snmpd before snmptrapd
# can be run.  See snmpd.conf(5) for how to do this.
TRAPDRUN=no

# snmptrapd options (use syslog).
TRAPDOPTS='-Lsd -p /var/run/snmptrapd.pid'

# create symlink on Debian legacy location to official RFC path
SNMPDCOMPAT=yes


**_/etc/snmp/snmpd.conf - Just what I modify, others are default_**
####
# First, map the community name (COMMUNITY) into a security name
# (local and mynetwork, depending on where the request is coming
# from):

#       sec.name  source          community
com2sec readonly  localhost         public
com2sec readonly  default         public
#com2sec paranoid  default         public
#com2sec readwrite default         private

**_My output from the snmpwalk when using the LM-SENSORS-MIB:_**

andre@linux:~$ sudo snmpwalk -v2c -c public localhost LM-SENSORS-MIB::lmTempSensorsTable
LM-SENSORS-MIB::lmTempSensorsTable = No Such Object available on this agent at this OID

**_Just for comparison, here is my output from the IF-MIB_**
andre@linux:~$ sudo snmpwalk -v2c -c public localhost IF-MIB::ifTable

IF-MIB::ifIndex.1 = INTEGER: 1
IF-MIB::ifIndex.2 = INTEGER: 2
IF-MIB::ifDescr.1 = STRING: lo
IF-MIB::ifDescr.2 = STRING: eth0
IF-MIB::ifType.1 = INTEGER: softwareLoopback(24)
IF-MIB::ifType.2 = INTEGER: ethernetCsmacd(6)
IF-MIB::ifMtu.1 = INTEGER: 16436
IF-MIB::ifMtu.2 = INTEGER: 1500
IF-MIB::ifSpeed.1 = Gauge32: 10000000
IF-MIB::ifSpeed.2 = Gauge32: 10000000

Well thanks for any help you (some one) can give! ;)

---

### Post by gtdaqua on 2008-06-11
In /etc/snmp/snmpd.conf, a simple:
```

rocommunity public 10.10.10.1

```
would be ok, where the IP address is your snmp-based NMS server. com2sec is granular level access control - or for mostly paranoid admins!

in /etc/default/snmpd
Denoting 0.0.0.0 means all I guess, but still take it out and try:
```

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid'

```

Stop and start SNMPD. Let me know how it went.

---

### Post by andremzenun on 2008-06-11
Hey! I have tested, but theses configurations I had already tested before, but just for have 100% sure I configure it again as you suggested and the result was the same! :(

```
andre@linux:~$ sudo snmpwalk -v2c -c public localhost LM-SENSORS-MIB::lmTempSensorsTable
LM-SENSORS-MIB::lmTempSensorsTable = No Such Object available on this agent at this OID

```

I just don't know what is happening with this server!
I have two other servers with similar hardware, but using debian, and the snmp + lm-sensors work without problems! This is weird!

Have you any other clue of what could be?
Thanks for your help! ;)

---

### Post by gtdaqua on 2008-06-12
Bump! 

Remove, purge and reinstall. 

Are you using snmpconf to configure the snmpd.conf file?

---

### Post by andremzenun on 2008-06-13
Hello my friend!

Sorry for take so long to respond!
To configure the snmp I'm doing by hand, as always!

I'll try to do what you suggest but don't think this will work!
In my debian this was just the time to configure lm-sensors and start using!
I don't have a clue what could cause this error, with just this mib! :confused:

Have you seen something like this before?

Well I hope to have the time to post here soon!
Thanks again!

André

---

### Post by andremzenun on 2008-06-13
I just execute this command

```
andre@linux:~$ sudo apt-get remove snmpd --purge ; sudo apt-get clean ; sudo apt-get install snmpd

```

After the reinstalling (it download the package again) the result was the same!

```
andre@linux:~$ sudo snmpwalk -v2c -c public localhost LM-SENSORS-MIB::lmTempSensorsTable
LM-SENSORS-MIB::lmTempSensorsTable = No Such Object available on this agent at this OID
andre@linux:~$ sudo snmpwalk -v2c -c public localhost IF-MIB::ifTable
IF-MIB::ifIndex.1 = INTEGER: 1
IF-MIB::ifIndex.2 = INTEGER: 2
IF-MIB::ifDescr.1 = STRING: lo
IF-MIB::ifDescr.2 = STRING: eth0

```

Well I think graph the temperature with snmp is not that important! :p
I will have to live with the fact of don't graph this on my ubuntu server!

---

### Post by gtdaqua on 2008-06-16
Sorry - cant see why it wont happen! May be you could PM some of the 'masters' in this forum.

---

### Post by aliby19 on 2008-06-19
This is a known bug and has been fixed in the latest version of net-snmp

[https://bugs.launchpad.net/ubuntu/+source/net-snmp/+bug/192745](https://bugs.launchpad.net/ubuntu/+source/net-snmp/+bug/192745)

-Aliby

---

### Post by afunix on 2008-06-27
Bug fixed only in intrepid.
But there is still no update in hardy!!
I haven't found any way to install intrepid package in hardy (some packages depend on perl5.10)

---

### Post by gtdaqua on 2008-07-03
> **afunix said:**
> Bug fixed only in intrepid.
But there is still no update in hardy!!
I haven't found any way to install intrepid package in hardy (some packages depend on perl5.10)

But you could install perl 5.1. Anything is installable, if you are willing to compile from source and go about!

---

### Post by Meserias on 2008-07-26
After parsing this subject I understand that it's a Known Bug for Lm-sensors, and SNMP on Ubuntu 8.04 (HARDY)

```

root@Meserias:~# snmpwalk -v1 -c public localhost LM-SENSORS-MIB::lmTempSensorsTable
root@Meserias:~#

```

Simply NO answer or error or anything....JUST nothing.:lolflag:
**I wait to be solved using SNMP not using scripts to get data.**
](*,)=D>:roll:

---

### Post by eliosh on 2009-04-24
Solution for Hardy Heron:
```

$ sudo ln -s /etc/sensors3.conf /etc/sensors.conf 
$ sudo /etc/init.d/snmpd restart

```

and it works like a charm:
```

snmpwalk -v 1 192.168.11.1 -c public 1.3.6.1.4.1.2021.13.16
LM-SENSORS-MIB::lmTempSensorsIndex.1 = INTEGER: 0
LM-SENSORS-MIB::lmTempSensorsIndex.2 = INTEGER: 1
LM-SENSORS-MIB::lmTempSensorsIndex.3 = INTEGER: 2
LM-SENSORS-MIB::lmTempSensorsDevice.1 = STRING: Chip Temp
LM-SENSORS-MIB::lmTempSensorsDevice.2 = STRING: CPU Temp
LM-SENSORS-MIB::lmTempSensorsDevice.3 = STRING: Sys Temp
LM-SENSORS-MIB::lmTempSensorsValue.1 = Gauge32: 35000
LM-SENSORS-MIB::lmTempSensorsValue.2 = Gauge32: 48000
LM-SENSORS-MIB::lmTempSensorsValue.3 = Gauge32: 43000
LM-SENSORS-MIB::lmFanSensorsIndex.1 = INTEGER: 0
LM-SENSORS-MIB::lmFanSensorsIndex.2 = INTEGER: 1
LM-SENSORS-MIB::lmFanSensorsDevice.1 = STRING: fan1
LM-SENSORS-MIB::lmFanSensorsDevice.2 = STRING: fan2
LM-SENSORS-MIB::lmFanSensorsValue.1 = Gauge32: 0
LM-SENSORS-MIB::lmFanSensorsValue.2 = Gauge32: 0
LM-SENSORS-MIB::lmVoltSensorsIndex.1 = INTEGER: 0
LM-SENSORS-MIB::lmVoltSensorsIndex.2 = INTEGER: 1
LM-SENSORS-MIB::lmVoltSensorsIndex.3 = INTEGER: 2
LM-SENSORS-MIB::lmVoltSensorsIndex.4 = INTEGER: 3
LM-SENSORS-MIB::lmVoltSensorsIndex.5 = INTEGER: 4
LM-SENSORS-MIB::lmVoltSensorsIndex.6 = INTEGER: 5
LM-SENSORS-MIB::lmVoltSensorsIndex.7 = INTEGER: 6
LM-SENSORS-MIB::lmVoltSensorsIndex.8 = INTEGER: 7
LM-SENSORS-MIB::lmVoltSensorsDevice.1 = STRING: +2.5V
LM-SENSORS-MIB::lmVoltSensorsDevice.2 = STRING: VCore
LM-SENSORS-MIB::lmVoltSensorsDevice.3 = STRING: +3.3V
LM-SENSORS-MIB::lmVoltSensorsDevice.4 = STRING: +5V
LM-SENSORS-MIB::lmVoltSensorsDevice.5 = STRING: +12V
LM-SENSORS-MIB::lmVoltSensorsDevice.6 = STRING: VCC
LM-SENSORS-MIB::lmVoltSensorsDevice.7 = STRING: +1.5V
LM-SENSORS-MIB::lmVoltSensorsDevice.8 = STRING: +1.8V
LM-SENSORS-MIB::lmVoltSensorsValue.1 = Gauge32: 2539
LM-SENSORS-MIB::lmVoltSensorsValue.2 = Gauge32: 1147
LM-SENSORS-MIB::lmVoltSensorsValue.3 = Gauge32: 3266
LM-SENSORS-MIB::lmVoltSensorsValue.4 = Gauge32: 4921
LM-SENSORS-MIB::lmVoltSensorsValue.5 = Gauge32: 12188
LM-SENSORS-MIB::lmVoltSensorsValue.6 = Gauge32: 3282
LM-SENSORS-MIB::lmVoltSensorsValue.7 = Gauge32: 1570
LM-SENSORS-MIB::lmVoltSensorsValue.8 = Gauge32: 1780
LM-SENSORS-MIB::lmMiscSensorsIndex.1 = INTEGER: 0
LM-SENSORS-MIB::lmMiscSensorsIndex.2 = INTEGER: 1
LM-SENSORS-MIB::lmMiscSensorsIndex.3 = INTEGER: 2
LM-SENSORS-MIB::lmMiscSensorsDevice.1 = STRING: vid
LM-SENSORS-MIB::lmMiscSensorsDevice.2 = STRING: vrm
LM-SENSORS-MIB::lmMiscSensorsDevice.3 = STRING: alarms
LM-SENSORS-MIB::lmMiscSensorsValue.1 = Gauge32: 2049
LM-SENSORS-MIB::lmMiscSensorsValue.2 = Gauge32: 8199
LM-SENSORS-MIB::lmMiscSensorsValue.3 = Gauge32: 3000


```

---

### Post by samosamo on 2009-05-01
very nice work.  very nice.

---

### Post by jotica on 2009-06-27
I'm getting a similar behaviour on Ubuntu Jaunty. Anyone knows how I might get lmSensors+snmp to work?

Here's the output of a few commands that may be relevant. 

> root@ubuntu64srv:/home/jota# sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.07 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.84 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.39 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +3.09 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +2.14 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +3.17 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.09 V
fan1:        894 RPM  (min =   10 RPM)
fan2:          0 RPM  (min =   10 RPM)  ALARM
temp1:       +38.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermistor
temp2:       +24.0Â°C  (low  = +127.0Â°C, high = +80.0Â°C)  sensor = thermal diode
temp3:        -2.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermistor
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +35.0Â°C  (high = +76.0Â°C, crit = +100.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +33.0Â°C  (high = +76.0Â°C, crit = +100.0Â°C)> root@ubuntu64srv:/home/jota# ls -l /etc/ | grep sensors
-rw-r--r-- 1 root root    71449 2009-03-05 18:30 sensors3.conf
lrwxrwxrwx 1 root root       18 2009-06-25 09:26 sensors.conf -> /etc/sensors3.conf

> root@ubuntu64srv:/home/jota# snmpwalk -v1 -c public localhost lmSensors
root@ubuntu64srv:/home/jota#> root@ubuntu64srv:/home/jota# apt-cache show snmpd lm-sensors | grep '\(Package\)\|\(Version\)'
Package: snmpd
Version: 5.4.1~dfsg-12ubuntu3
Package: lm-sensors
Version: 1:3.0.2-2ubuntu4

---

### Post by robgolding63 on 2009-12-22
> **jotica said:**
> I'm getting a similar behaviour on Ubuntu Jaunty. Anyone knows how I might get lmSensors+snmp to work?

Here's the output of a few commands that may be relevant.

I have the *exact* same versions and problem as you - did you ever find a solution? I know this is an old thread, but my SNMP/lmsensors just broke after I upgraded the server to Jaunty.

Cheers

Rob

---

### Post by raphoun on 2010-01-13
And it still doesnt work in Karmic.

> raphael@francois-desktop:~$ sudo snmpwalk -v2c -c public localhost 1.3.6.1.4.1.2021.13.16
LM-SENSORS-MIB::lmSensors = No Such Object available on this agent at this OID


> raphael@francois-desktop:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.34 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.22 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +5.04 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.20 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    1048 RPM  (min =  600 RPM)
CHASSIS FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:     0 RPM  (min =  600 RPM)
CPU Temperature:   +46.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:    +36.0°C  (high = +45.0°C, crit = +95.0°C)


> raphael@francois-desktop:~$ apt-cache show snmpd lm-sensors | grep '\(Package\)\|\(Version\)'
Package: snmpd
Version: 5.4.1~dfsg-12ubuntu7
Package: lm-sensors
Version: 1:3.0.2-2ubuntu4

---

### Post by robgolding63 on 2010-01-14
I ended up writing a Perl program to interpret the output of the `sensors` command and used that to import the data into Cacti. My graphs are working once again!

Most of the work was in making the data queries/templates and graph templates in cacti, the program was basically a complicated "grep" on multiple lines.

Good luck everyone :)

Rob

---

### Post by raphoun on 2010-01-19
Hey Rob could you share your program with us? :) 

> **robgolding63 said:**
> I ended up writing a Perl program to interpret the output of the `sensors` command and used that to import the data into Cacti. My graphs are working once again!

Most of the work was in making the data queries/templates and graph templates in cacti, the program was basically a complicated "grep" on multiple lines.

Good luck everyone :)

Rob

---

### Post by robgolding63 on 2010-01-19
> **raphoun said:**
> Hey Rob could you share your program with us? :)

Sure! Remember though, as I said most of the work is in the Cacti configuration - and I'm not skilled enough to be exporting my templates for others to use (I only just managed to get it working for myself!).

Anyway, I altered a program I found on a forum somewhere else and, unfortunately, I can't remember where or who it was - but they deserve full credit for this! I just modified it to work with the current version of Cacti, and a system with a dual-core CPU. I have one graph for CPU temperature - Core 1 & 2, and one graph for motherboard temperature.

Obviously you will probably need to modify the script to make it work if your system is configured differently.

[HTML]
#!/usr/bin/perl

@sensoroutput=`/usr/bin/sensors`;

foreach(@sensoroutput) {
  chomp();
  split();
  if ( $_[0] eq 'temp1:' ) {
        $temp1 = $_[1];
  }
  if ( $_[0] eq 'temp2:' ) {
        $temp2 = $_[1];
  }
  if ( $_[0] eq 'Core' ) {
    if ( $_[1] eq '0:' ) {
        $core0 = $_[2];
    }
    if ( $_[1] eq '1:' ) {
        $core1 = $_[2];
    }
  }
}
$temp1 =~ s/\+//;
$temp1 =~ s/\°C//;
$temp2 =~ s/\+//;
$temp2 =~ s/\°C//;
$core0 =~ s/\+//;
$core0 =~ s/\°C//;
$core1 =~ s/\+//;
$core1 =~ s/\°C//;

print "temp1:$temp1 temp2:$temp2 core0:$core0 core1:$core1";
[/HTML]

Hope it works for you :)

Rob

---

