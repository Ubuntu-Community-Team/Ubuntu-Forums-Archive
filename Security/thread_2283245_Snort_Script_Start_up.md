---
title: "Snort Script Start up"
date: 2015-06-20
forum: Security
---

### Post by nick201 on 2015-06-20
Hi, Im looking for a little help with the snort start up script. Im new to linux and snort. Been living in a windows world so to speak. I have been following the instructions at this site.

[http://sublimerobots.com/2014/12/installing-snort-part-7/]("http://exec /usr/local/bin/barnyard2 -c /etc/snort/barnyard2.conf -d /var/log/snort -f snort.u2 -w /var/log/snort/barnyard2.waldo -g snort -u snort -D")

When i follow the directions on this page i get the error

sudo vi /etc/init/snort.conf

description "Snort NIDS service"
stop on runlevel [!2345]
start on runlevel [2345]
script
    exec /usr/sbin/snort -q -u snort -g snort -c /etc/snort/snort.conf -i eth0 -D
end script

sudo chmod +x /etc/init/snort.conf

initctl list | grep snort
    snort stop/waiting






 --== Initializing Snort ==--
Initializing Output Plugins!
Snort BPF option: stop/waiting
[COLOR=#ff0000]ERROR: Failed to lookup interface: no suitable device found. Please specify one with -i switch[/COLOR]
Fatal Error, Quitting..

When i run the command from terminal it works perfectly no problems. I run as sudo and remove the exec.
[COLOR=#0000cd]sudo /usr/sbin/snort -q -u snort -g snort -c /etc/snort/snort.conf -i eth0 -D[/COLOR]
=============================================================================

Then i try the barnyard2 Script

sudo vi /etc/init/barnyard2.conf





description "barnyard2 service"
stop on runlevel [!2345]
start on runlevel [2345]
script

    [COLOR=#0000cd]exec /usr/local/bin/barnyard2 -c /etc/snort/barnyard2.conf -d /var/log/snort -f snort.u2 -w /var/log/snort/barnyard2.waldo -g snort -u snort -D[/COLOR]

end script

sudo chmod +x /etc/init/barnyard2.conf
initctl list | grep barnyard
    barnyard2 stop/waiting






Error 
  ______   -*> Barnyard2 <*-
 / ,,_  \  Version 2.1.14 (Build 336)
 |o"  )~|  By Ian Firns (SecurixLive): [http://www.securixlive.com/](http://www.securixlive.com/)
 + '''' +  (C) Copyright 2008-2013 Ian Firns <firnsy@securixlive.com>

USAGE: barnyard2 [-options] <filter options>
Gernal Options:
        -c <file>  Use configuration file <file>
        -C <file>  Read the classification map from <file>
        -D         Run barnyard2 in background (daemon) mode
        -e         Display the second layer header info
        -F         Turn off fflush() calls after binary log writes
        -g <gname> Run barnyard2 gid as <gname> group (or gid) after initialization
        -G <file>  Read the gen-msg map from <file>
        -h <name>  Define the hostname <name>. For logging purposes only
        -i <if>    Define the interface <if>. For logging purposes only
        -I         Add Interface name to alert output
        -l <ld>    Log to directory <ld>
        -m <umask> Set umask = <umask>
        -O         Obfuscate the logged IP addresses
        -q         Quiet. Don't show banner and status report
        -r <id>    Include 'id' in barnyard2_intf<id>.pid file name
        -R <file>  Read the reference map from <file>
        -S <file>  Read the sid-msg map from <file>
        -t <dir>   Chroots process to <dir> after initialization
        -T         Test and report on the current barnyard2 configuration
        -u <uname> Run barnyard2 uid as <uname> user (or uid) after initialization
        -U         Use UTC for timestamps
        -v         Be verbose
        -V         Show version number
        -y         Include year in timestamp in the alert and log files
        -?         Show this information

Continual Processing Options:
        -a <dir>   Archive processed files to <dir>
        -f <base>  Use <base> as the base filename pattern
        -d <dir>   Spool files from <dir>
        -n         Only process new events
        -w <file>  Enable bookmarking using <file>

Batch Processing Mode Options:
        -o         Enable batch processing mode

Longname options and their corresponding single char version
   --disable-alert-on-each-packet-in-stream  Alert once per event
   --event-cache-size <integer>      Set Spooler MAX event cache size 
   --reference <file>                Same as -R
   --classification <file>           Same as -C
   --gen-msg <file>                  Same as -G
   --sid-msg <file>                  Same as -S
   --process-new-records-only        Same as -n
   --pid-path <dir>                  Specify the directory for the barnyard2 PID file
   --help                            Same as -?
   --version                         Same as -V
   --create-pidfile                  Create PID file, even when not in Daemon mode
   --nolock-pidfile                  Do not try to lock barnyard2 PID file


[COLOR=#ff0000]Uh, you need to tell me to do something...

ERROR: Fatal Error, Quitting..[/COLOR]
Barnyard2 exiting
===============================================================================
Record Totals:
   Records:           0
   Events:           0 (0.000%)
   Packets:           0 (0.000%)
   Unknown:           0 (0.000%)
   Suppressed:           0 (0.000%)
===============================================================================
Packet breakdown by protocol (includes rebuilt packets):
      ETH: 0          (0.000%)
  ETHdisc: 0          (0.000%)
     VLAN: 0          (0.000%)
     IPV6: 0          (0.000%)
  IP6 EXT: 0          (0.000%)
  IP6opts: 0          (0.000%)
  IP6disc: 0          (0.000%)
      IP4: 0          (0.000%)
  IP4disc: 0          (0.000%)
    TCP 6: 0          (0.000%)
    UDP 6: 0          (0.000%)
    ICMP6: 0          (0.000%)
  ICMP-IP: 0          (0.000%)
      TCP: 0          (0.000%)
      UDP: 0          (0.000%)
     ICMP: 0          (0.000%)
  TCPdisc: 0          (0.000%)
  UDPdisc: 0          (0.000%)
  ICMPdis: 0          (0.000%)
     FRAG: 0          (0.000%)
   FRAG 6: 0          (0.000%)
      ARP: 0          (0.000%)
    EAPOL: 0          (0.000%)
  ETHLOOP: 0          (0.000%)
      IPX: 0          (0.000%)
    OTHER: 0          (0.000%)
  DISCARD: 0          (0.000%)
InvChkSum: 0          (0.000%)
   S5 G 1: 0          (0.000%)
   S5 G 2: 0          (0.000%)
    Total: 0         

Again when i run the command from terminal i get no error and it works great. 

[COLOR=#0000cd]sudo /usr/local/bin/barnyard2 -c /etc/snort/barnyard2.conf -d /var/log/snort  -f snort.u2 -w /var/log/snort/barnyard2.waldo -g snort -u snort -D[/COLOR]


Ive been googling for 2 days but its hard to find an error when you know it works everyplace else.

---

### Post by ant2ne on 2015-06-26
Maybe not the solution you are looking for, but why not run it as root's cron
```
ps -A | grep barnyard2 ||  /usr/local/bin/barnyard2 -c /etc/snort/barnyard2.conf -d /var/log/snort -f snort.u2 -w /var/log/snort/barnyard2.waldo -g snort -u snort -D
```
This will check to see if barnyard is running, and then launch it if it isn't.

Or you could launch it manually as a nohup.

---

