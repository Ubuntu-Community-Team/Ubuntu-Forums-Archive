---
title: "iptables firewall script [example]"
date: 2005-03-10
forum: Server Platforms
---

### Post by pinnockio on 2005-03-10
Hello,


As there doesn't seem to be any iptables script which saves and restores the rules on startup/ and shutdown, I've adapted an iptables script used by Gento [gentoo](http://www.gentoo.org).

```
#!/bin/sh
#
#This is a ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
# under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.

IPTABLES_SAVE="/etc/default/iptables-rules"
SAVE_RESTORE_OPTIONS="-c"
SAVE_ON_STOP="yes"

checkrules() {
	if [ ! -f ${IPTABLES_SAVE} ]
	then
		echo "Not starting iptables. First create some rules then run"
		echo "\"/etc/init.d/iptables save\""
		return 1
	fi
}

save() {
  echo "Saving iptables state"
  /sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
}

start(){
	checkrules || return 1
	  echo  "Loading iptables state and starting firewall"
	  echo -n "Restoring iptables ruleset"
	  start-stop-daemon --start --quiet --exec /sbin/iptables-restore -- ${SAVE_RESTORE_OPTIONS} < ${IPTABLES_SAVE}
}

case "$1" in
  save)
        save
        echo "."
        ;;

  start)
  	start
	echo "."
	;;
  stop)
	  if [ "${SAVE_ON_STOP}" = "yes" ]; then
		  save || exit 1
	  fi
	  echo -n "Stopping firewall"
		for a in `cat /proc/net/ip_tables_names`; do
			/sbin/iptables -F -t $a
			/sbin/iptables -X -t $a
	
			if [ $a == nat ]; then
				/sbin/iptables -t nat -P PREROUTING ACCEPT
				/sbin/iptables -t nat -P POSTROUTING ACCEPT
				/sbin/iptables -t nat -P OUTPUT ACCEPT
			elif [ $a == mangle ]; then
				/sbin/iptables -t mangle -P PREROUTING ACCEPT
				/sbin/iptables -t mangle -P INPUT ACCEPT
				/sbin/iptables -t mangle -P FORWARD ACCEPT
				/sbin/iptables -t mangle -P OUTPUT ACCEPT
				/sbin/iptables -t mangle -P POSTROUTING ACCEPT
			elif [ $a == filter ]; then
				/sbin/iptables -t filter -P INPUT ACCEPT
				/sbin/iptables -t filter -P FORWARD ACCEPT
				/sbin/iptables -t filter -P OUTPUT ACCEPT
			fi
		done
    start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/iptables
    echo "."
    ;;

  restart)
	  echo -n "Flushing firewall"
		  for a in `cat /proc/net/ip_tables_names`; do
			  /sbin/iptables -F -t $a
  			  /sbin/iptables -X -t $a
	  	done;
	  start
    echo "."
    ;;
  *)
    echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
    exit 1
    ;;
esac

exit 0
```

Just copy this file to /etc/init.d/iptables and add it to the boot runlevel before any other networking is started by issuing the following command:
```
sudo update-rc.d iptables start 37 S . stop 37 0 .
```

How to use?
first time:
1. add you rules to iptables ("sudo iptables -A INPUT etc...")
2. then issue "sudo /etc/init.d/iptables save
afterwards:
nothing has to be done any-more ;)

Note that if you issue "sudo /etc/init.d/iptables stop"; it saves the current rules to "/etc/default/iptables-rules" and flushes iptables (meaning setting everything to accept).  So if you issue "sudo /etc/init.d/iptables stop" 2 x after eachother, this file will be empty!

I hope it helps you (and not forget this script originally came from gentoo-linux!).

Kind regards,

Maurits

---

### Post by nate on 2005-03-11
Very nice of you. I'd recommend everyone have a copy of the /etc/default/iptables-rules file somewhere else to make sure you can restore your rules if you accidentially stop it twice in a row.

If someone wanted to try and improve it further, maybe only write to iptables-save if what is being written does not match the default iptables rules?  There should be a number of options for testing whether the rules are in their default state or not. This would still mean that the rules you want can get overwritten if you "stop", change the rules as a test, then "stop" again but it would eliminate overwriting the save with the default of accepting any.

---

### Post by huggy77 on 2007-09-01
this is a GREAT script  - thankyou!!!  perfect

---

### Post by nowshining on 2007-09-02
i recommend arno-iptables-firewall :) does it automatically - can setup from a config file to enable/disable options and even set your own rules in a custom rules files already made out just input any rules there - stop and restart the firewall REALLY EASY to get going.. :)

---

### Post by phil_websurfer on 2007-09-25
Version with IPv6 support. Thank you Gentoo!
:)

The updated script:
```

#! /bin/sh

#This is an Ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
#under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.

. /lib/lsb/init-functions


IPTABLES_SAVE="/etc/iptables"
IP6TABLES_SAVE="/etc/ip6tables"
SAVE_RESTORE_OPTIONS="-c"


checkrules() {
    if [ ! -f ${IPTABLES_SAVE} ]
    then
        echo "Not starting iptables. First create some rules then run"
        echo "\"/etc/init.d/iptables save\""
        return 1
    fi
}

save() {
    /sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
    /sbin/ip6tables-save ${SAVE_RESTORE_OPTIONS} > ${IP6TABLES_SAVE}
    return $?
}

start(){
    checkrules || return 1
    /sbin/iptables-restore ${SAVE_RESTORE_OPTIONS} < ${IPTABLES_SAVE}
    /sbin/ip6tables-restore ${SAVE_RESTORE_OPTIONS} < ${IP6TABLES_SAVE}
    return $?
}


case "$1" in
    save)
        echo -n "Saving iptables state..."
        save
        if [ $? -eq 0 ] ; then
            echo " ok"
        else
            echo " error !"
        fi
    ;;

    start)
        log_begin_msg "Loading iptables state and starting firewall..."
        start
        log_end_msg $?
    ;;
    stop)
        log_begin_msg "Stopping firewall..."
        for a in `cat /proc/net/ip_tables_names`; do
            /sbin/iptables -F -t $a
            /sbin/iptables -X -t $a

            if [ $a = nat ]; then
                /sbin/iptables -t nat -P PREROUTING ACCEPT
                /sbin/iptables -t nat -P POSTROUTING ACCEPT
                /sbin/iptables -t nat -P OUTPUT ACCEPT
            elif [ $a = mangle ]; then
                /sbin/iptables -t mangle -P PREROUTING ACCEPT
                /sbin/iptables -t mangle -P INPUT ACCEPT
                /sbin/iptables -t mangle -P FORWARD ACCEPT
                /sbin/iptables -t mangle -P OUTPUT ACCEPT
                /sbin/iptables -t mangle -P POSTROUTING ACCEPT
            elif [ $a = filter ]; then
                /sbin/iptables -t filter -P INPUT ACCEPT
                /sbin/iptables -t filter -P FORWARD ACCEPT
                /sbin/iptables -t filter -P OUTPUT ACCEPT
            fi
        done
        for a in `cat /proc/net/ip6_tables_names`; do
            /sbin/ip6tables -F -t $a
            /sbin/ip6tables -X -t $a

            if [ $a = nat ]; then
                /sbin/ip6tables -t nat -P PREROUTING ACCEPT
                /sbin/ip6tables -t nat -P POSTROUTING ACCEPT
                /sbin/ip6tables -t nat -P OUTPUT ACCEPT
            elif [ $a = mangle ]; then
                /sbin/ip6tables -t mangle -P PREROUTING ACCEPT
                /sbin/ip6tables -t mangle -P INPUT ACCEPT
                /sbin/ip6tables -t mangle -P FORWARD ACCEPT
                /sbin/ip6tables -t mangle -P OUTPUT ACCEPT
                /sbin/ip6tables -t mangle -P POSTROUTING ACCEPT
            elif [ $a = filter ]; then
                /sbin/ip6tables -t filter -P INPUT ACCEPT
                /sbin/ip6tables -t filter -P FORWARD ACCEPT
                /sbin/ip6tables -t filter -P OUTPUT ACCEPT
            fi
        done
        log_end_msg 0
    ;;

    restart)
        log_begin_msg "Restarting firewall..."
        for a in `cat /proc/net/ip_tables_names`; do
            /sbin/iptables -F -t $a
            /sbin/iptables -X -t $a
        done;
        for a in `cat /proc/net/ip6_tables_names`; do
            /sbin/ip6tables -F -t $a
            /sbin/ip6tables -X -t $a
        done;
        start
        log_end_msg $?
    ;;

    *)
        echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
        exit 1
        ;;
esac

exit 0

```iptables configuration sample from Fedora
```

# Firewall configuration written by system-config-securitylevel
# Manual customization of this file is not recommended.
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:FW-INPUT-RULE - [0:0]
-A INPUT -j FW-INPUT-RULE
-A FW-INPUT-RULE -i lo -j ACCEPT
-A FW-INPUT-RULE -p icmp --icmp-type any -j ACCEPT
#-A FW-INPUT-RULE -p 50 -j ACCEPT
#-A FW-INPUT-RULE -p 51 -j ACCEPT
#-A FW-INPUT-RULE -p udp --dport 5353 -d 224.0.0.251 -j ACCEPT
#-A FW-INPUT-RULE -p udp -m udp --dport 631 -j ACCEPT
#-A FW-INPUT-RULE -p tcp -m tcp --dport 631 -j ACCEPT
-A FW-INPUT-RULE -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FW-INPUT-RULE -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT
-A FW-INPUT-RULE -m state --state NEW -m tcp -p tcp --dport 8010 -j ACCEPT
-A FW-INPUT-RULE -j REJECT --reject-with icmp-host-prohibited
-A FORWARD -j REJECT --reject-with icmp-host-prohibited
COMMIT

```ip6tables configuration sample from Fedora
```

# Firewall configuration written by system-config-securitylevel
# Manual customization of this file is not recommended.
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:FW-INPUT-RULE - [0:0]
-A INPUT -j FW-INPUT-RULE
-A FW-INPUT-RULE -i lo -j ACCEPT
-A FW-INPUT-RULE -p icmpv6 -j ACCEPT
#-A FW-INPUT-RULE -p 50 -j ACCEPT
#-A FW-INPUT-RULE -p 51 -j ACCEPT
#-A FW-INPUT-RULE -p udp --dport 5353 -d ff02::fb -j ACCEPT
#-A FW-INPUT-RULE -p udp -m udp --dport 631 -j ACCEPT
#-A FW-INPUT-RULE -p tcp -m tcp --dport 631 -j ACCEPT
-A FW-INPUT-RULE -p udp -m udp --dport 32768:61000 -j ACCEPT
-A FW-INPUT-RULE -p tcp -m tcp --dport 32768:61000 -j ACCEPT
-A FW-INPUT-RULE -m tcp -p tcp --dport 22 -j ACCEPT
-A FW-INPUT-RULE -m tcp -p tcp --dport 8010 -j ACCEPT
-A FW-INPUT-RULE -j REJECT --reject-with icmp6-port-unreachable
-A FORWARD -j REJECT --reject-with icmp6-port-unreachable
COMMIT

```To make it run in the startup. It must be run before vmware init script (90):
```
update-rc.d iptables start 91 2 3 5 .
```

---

### Post by misterhaan on 2008-01-16
thanks, this is the 3rd or so thing i tried and finally something worked!

---

