---
title: "mitmprotector - Protects you from ManInTheMiddle-Attacks/Arpspoofing"
date: 2014-12-14
forum: Security
---

### Post by jan-helbling on 2014-12-14
Hello, i have written a python-script and want share it :grin:

mitmprotector - protect's you from any kind of MITM-attacks, arpspoofing, ettercap, sslstrip, droidsheep, zAnti, dsploit, etc.

 - It use the arp command to compare MAC and IP -Addresses
 - Execute Command (notify-send?) and Drop the Interface down by Attack
 - Create a Firewall if arptables is installed
 - Run as a Daemon or in Foreground
 - Enable startup/stop on each connect/disconnect from network (wicd & networkmanager)

Configuration-File: /etc/mitmprotector.conf (after first execution)
Logfile: /var/log/mitmprotector.log
Pidfile: /var/run/mitmprotector.pid

Install:
```

$ sudo add-apt-repositority ppa:jan-helbling/mitmprotector
$ sudo apt-get update
$ sudo apt-get install mitmprotector
```

It will automatically detect your networkinterface and add it to /etc/mitmprotector.conf after install.

Install scripts for networkmanager => /etc/network/if-post-down.d/ & /etc/network/if-up.d/ and wicd => /etc/wicd/scripts/predisconnect/ /etc/wicd/scripts/postconnect/:
```

$ sudo mitmprotector.py --nm-aoc
```

To remove the scripts:
```

$ sudo mitmprotector.py --rm-aoc
```

Run it manually in foreground:
```

$ sudo mitmprotector.py -f
or
$ sudo mitmprotector.py --foreground
```

Run it as a daemon:
```

$ sudo mitmprotector.py -d
or
$ sudo mitmprotector.py --daemon
```


And the configfile /etc/mitmprotector.conf looks like that:
```

[attack]
exec = /usr/bin/notify-send "MITM-Attack" "from IP: {0}  MAC: {1}" -u critical -t 3000 -c "Security"
interface = wlan0
put-interface-down = 1
shutdown-interface-command = ifconfig {0} down

[arp-scanner]
timeout = 5
command = arp -an
```

VCS-Repos:
```

bzr branch lp:jan-helbling/+junk/mitmprotector
git clone https://github.com/JanHelbling/mitmprotector.git
```

---

