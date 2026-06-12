---
title: "Basic Iptables Log Monitor Script"
date: 2013-01-08
forum: Security
---

### Post by emiller12345 on 2013-01-08
I thought it would be nice to have some kind of a simple log reader for iptables logs.
Usually they aren't seen until way later, and this give the user a much faster response time to firewall log entries.

Just an FYI, its really simple, and may still be buggy. Let me know if you see anything.

```
#!/bin/bash
#This script monitors the syslog for iptables log entries
#  and displays unique entries on the Desktop using notify-osd
# ***NOTE***  --This is not a firewall
# ./notify_iptables_log Version 0.1
#Copyright (C) 2013  by emiller
#
#This program is free software; you can redistribute it and/or
#modify it under the terms of the GNU General Public License
#as published by the Free Software Foundation; either version 2
#of the License, or (at your option) any later version.
#
#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.
#
#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

array=()
tail -n0 -f /var/log/syslog | \
    grep --line-buffered "IN=" | \
    grep --line-buffered "OUT=" | \
    grep --line-buffered "SRC=" | \
    grep --line-buffered "DST=" |  \
    while IFS= read -r LINE; do 
        FINAL_NOTIFY_MSG=""
        IPT_LINE_DATE="$(echo "$LINE" | awk '{print $1" "$2" "$3}')"
        IPT_LINE_DATE="$(date --date="$IPT_LINE_DATE" +%b' '%d' '%I':'%M':'%S' '%p)" #Convert 24-hour to 12-hour + am/pm
        IS_INCOMMING="$(echo "$LINE" | grep -o 'IN=\([^ ]\+\) ' | cut -d= -f2)"
        IS_OUTGOING="$(echo "$LINE" | grep -o 'OUT=\([^ ]\+\) ' | cut -d= -f2)"
        IS_TCP="$(echo "$LINE" | grep 'PROTO=TCP')"
        IS_UDP="$(echo "$LINE" | grep 'PROTO=UDP')"
        IS_ICMP="$(echo "$LINE" | grep 'PROTO=ICMP')"
        SRC="$(echo $LINE | grep -o 'SRC=\([^ ]\+\) ' | cut -d= -f2)"
        DST="$(echo $LINE | grep -o 'DST=\([^ ]\+\) ' | cut -d= -f2)"
        DPT="$(echo $LINE | grep -o 'DPT=\([^ ]\+\) ' | cut -d= -f2)"
        if [ -n "$IS_TCP" ]; then
            #TCP will display Adapter, Protocol, Direction, Remote IP, and Dest Port
            if [ -n "$IS_INCOMMING" ]; then
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""INBOUND $IS_INCOMMING TCP BLOCK\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""SRC=$SRC\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""DPT=$DPT\n"
            fi
            if [ -n "$IS_OUTGOING" ]; then
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""OUTBOUND $IS_OUTGOING TCP BLOCK\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""DST=$DST\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""DPT=$DPT\n"
            fi
        fi
        if [ -n "$IS_UDP" ]; then
            #UDP will display Adapter, Protocol, Direction, Remote IP, and Dest Port
            if [ -n "$IS_INCOMMING" ]; then
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""INBOUND $IS_INCOMMING UDP BLOCK\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""SRC=$SRC\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""DPT=$DPT\n"
            fi
            if [ -n "$IS_OUTGOING" ]; then
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""OUTBOUND $IS_OUTGOING UDP BLOCK\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""DST=$DST\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""DPT=$DPT\n"
            fi
        fi
        if [ -n "$IS_ICMP" ]; then
            #ICMP will display Adapter, Protocol, Direction, and Remote IP
            if [ -n "$IS_INCOMMING" ]; then
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""INBOUND $IS_INCOMMING ICMP BLOCK\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""SRC=$SRC\n"
            fi
            if [ -n "$IS_OUTGOING" ]; then
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""OUTBOUND $IS_OUTGOING ICMP BLOCK\n"
                FINAL_NOTIFY_MSG="$FINAL_NOTIFY_MSG""DST=$DST\n"
            fi
        fi
        #A rate limiting measure, will only display 1 unique log entry to avoid notify-send flooding
        if [ -z "$(echo "${array[@]}" | grep "$(echo "$FINAL_NOTIFY_MSG" | tr ' ' '~' | sed 's/\\n/#/g')")" ]; then
            array=( "${array[@]}" "$(echo "$FINAL_NOTIFY_MSG" | tr ' ' '~' | sed 's/\\n/#/g')" )
            notify-send --expire-time=10000 --urgency=normal "firewall: $IPT_LINE_DATE" "$FINAL_NOTIFY_MSG" 
        fi
    done

```

---

