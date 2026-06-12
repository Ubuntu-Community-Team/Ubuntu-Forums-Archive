---
title: "Iplist - Nat"
date: 2007-12-04
forum: Server Platforms
---

### Post by ekimregnirps on 2007-12-04
Hi,  
 I'm trying to use IPLIST on a linux box setup as a NAT router, to block clients p2p activites. But by default iplist only blocks in/out ips on the server box. Is there a way to have iplist block these NAT clients? 
 
( I've tired to insert in position 1, and append, the input/output match/queue chain in the FORWARD chain of iptables, but no luck. I think I might be putting it in wrong chain of position, or wrong something.) 
 
Any advice of iptables commands i can use to get this going, examples would be nice to? 
 
And if someone could give me a quick synopsis on how iplist works? So I can get my head around this, and I also plan to write a HOWTO once i figure this out, as it seems useful.

---

### Post by ekimregnirps on 2007-12-10
Well after eliminating my other problems, i got my head around this. Not to bad after all, ipblock shell script was my eureka! 
 
I add two firewall rules to the forward chain, and modified the script like so: 
 
```
#!/bin/sh 
# Copyright (C) 2007 Serkan Sakar <uljanow@users.sourceforge.net> 
# ipblock 0.15 
 
set -e 
 
PATH=/sbin:/usr/sbin:/bin:/usr/bin 
 
# This script only rejects packets from hosts specified in files 
# and the rest is handled by the existing iptables configuration. 
 
[ -f /etc/ipblock.conf ] && . /etc/ipblock.conf 
 
INPUT_QUEUE=0 
INPUT_POLICY=REPEAT 
INPUT_POLICY_MARK=0xfffe 
INPUT_TARGET=REPEAT 
INPUT_TARGET_MARK=0xffff 
 
OUTPUT_QUEUE=1 
OUTPUT_POLICY=REPEAT 
OUTPUT_POLICY_MARK=0xfffe 
OUTPUT_TARGET=REPEAT 
OUTPUT_TARGET_MARK=0xffff 
 
NICE=-5 
NEW="-m state --state NEW" 
#NEW="" 
 
export IPLIST_LISTDIR 
 
# {{{ do_start() 
do_start() 
{ 
! [ -f /var/run/iplist.pid ] || { iplist -k; sleep 1; } 
 
nice -n ${NICE} iplist --daemon ${VERBOSE} -f ${LOGFILE} -l ${LOGLEVEL} 
 
iplist -i -p ${INPUT_POLICY} -P ${INPUT_POLICY_MARK} -t ${INPUT_TARGET} \ 
-T ${INPUT_TARGET_MARK} -n ${INPUT_QUEUE} ${INPUT_FILES} 
 
iplist -i -p ${OUTPUT_POLICY} -P ${OUTPUT_POLICY_MARK} -t ${OUTPUT_TARGET} \ 
-T ${OUTPUT_TARGET_MARK} -n ${OUTPUT_QUEUE} ${OUTPUT_FILES} 
 
iptables -N input_match 
iptables -N input_queue 
 
iptables -N output_match 
iptables -N output_queue 
 
iptables -I INPUT 1 -m mark --mark ${INPUT_TARGET_MARK} -j input_match 
iptables -I INPUT 2 ${NEW} -m mark ! --mark ${INPUT_POLICY_MARK} -j input_queue 
 
iptables -I OUTPUT 1 -m mark --mark ${OUTPUT_TARGET_MARK} -j output_match 
iptables -I OUTPUT 2 ${NEW} -m mark ! --mark ${OUTPUT_POLICY_MARK} -j output_queue 
 
[B]iptables -I FORWARD 1 -m mark --mark ${OUTPUT_TARGET_MARK} -j output_match 
iptables -I FORWARD 2 ${NEW} -m mark ! --mark ${OUTPUT_POLICY_MARK} -j output_queue [/B]
 
iptables -A input_match -p tcp -j REJECT --reject-with tcp-reset 
iptables -A input_match -j REJECT --reject-with icmp-port-unreachable 
 
iptables -A output_match -p tcp -j REJECT --reject-with tcp-reset 
iptables -A output_match -j REJECT --reject-with icmp-port-unreachable 
 
for port in ${IGN_TCP_PORT_IN}; do 
iptables -A input_queue -p tcp --sport ${port} -j RETURN 
done 
for port in ${IGN_UDP_PORT_IN}; do 
iptables -A input_queue -p udp --sport ${port} -j RETURN 
done 
iptables -A input_queue -j NFQUEUE --queue-num ${INPUT_QUEUE} 
 
for port in ${IGN_TCP_PORT_OUT}; do 
iptables -A output_queue -p tcp --dport ${port} -j RETURN 
done 
for port in ${IGN_UDP_PORT_OUT}; do 
iptables -A output_queue -p udp --dport ${port} -j RETURN 
done 
iptables -A output_queue -j NFQUEUE --queue-num ${OUTPUT_QUEUE} 
} 
# }}} 
 
# {{{ do_stop() 
do_stop() 
{ 
iplist -k 
 
iptables -D INPUT -m mark --mark ${INPUT_TARGET_MARK} -j input_match 
iptables -D INPUT ${NEW} -m mark ! --mark ${INPUT_POLICY_MARK} -j input_queue 
 
iptables -D OUTPUT -m mark --mark ${OUTPUT_TARGET_MARK} -j output_match 
iptables -D OUTPUT ${NEW} -m mark ! --mark ${OUTPUT_POLICY_MARK} -j output_queue 
 
[B]iptables -D FORWARD -m mark --mark ${OUTPUT_TARGET_MARK} -j output_match 
iptables -D FORWARD ${NEW} -m mark ! --mark ${OUTPUT_POLICY_MARK} -j output_queue [/B]
 
iptables -D input_match -p tcp -j REJECT --reject-with tcp-reset 
iptables -D input_match -j REJECT --reject-with icmp-port-unreachable 
 
iptables -D output_match -p tcp -j REJECT --reject-with tcp-reset 
iptables -D output_match -j REJECT --reject-with icmp-port-unreachable 
 
for port in ${IGN_TCP_PORT_IN}; do 
iptables -D input_queue -p tcp --sport ${port} -j RETURN 
done 
for port in ${IGN_UDP_PORT_IN}; do 
iptables -D input_queue -p udp --sport ${port} -j RETURN 
done 
iptables -D input_queue -j NFQUEUE --queue-num ${INPUT_QUEUE} 
 
for port in ${IGN_TCP_PORT_OUT}; do 
iptables -D output_queue -p tcp --dport ${port} -j RETURN 
done 
for port in ${IGN_UDP_PORT_OUT}; do 
iptables -D output_queue -p udp --dport ${port} -j RETURN 
done 
iptables -D output_queue -j NFQUEUE --queue-num ${OUTPUT_QUEUE} 
 
iptables -X input_match 
iptables -X input_queue 
 
iptables -X output_match 
iptables -X output_queue 
} 
# }}} 
 
# {{{ update_file() 
update_file() 
{ 
local url file list 
 
grep '^[^#]' ${URL_FILE} | \ 
while read url; do 
file=`basename $url .php` 
list=`basename $1` 
if [ "$file" = "$list" ]; then 
wget -t 2 -T 60 -w 1 -a /dev/stdout -nv -N ${url} || \ 
echo "error: update of $list failed" >&2 
break 
fi 
done 
} 
# }}} 
 
# {{{ do_update() 
do_update() 
{ 
if [ -d ${IPLIST_LISTDIR} ]; then 
cd ${IPLIST_LISTDIR} 
 
for file in ${INPUT_FILES}; do 
update_file $file 
done 
 
if [ "${INPUT_FILES}" != "${OUTPUT_FILES}" ]; then 
for file in ${OUTPUT_FILES}; do 
update_file $file 
done 
fi 
touch ${IPLIST_LISTDIR}/.update-stamp  
else 
echo "error: can't access ${IPLIST_LISTDIR}" >&2 && exit 1 
fi 
} 
# }}} 
 
# {{{ do_gui() 
do_gui() 
{ 
exec java -Xmx512M -jar /usr/share/java/ipblockUI.jar 
} 
# }}} 
 
# {{{ convert_file() 
convert_file() 
{ 
iplist ${VERBOSE} -o $1 $1 
} 
# }}} 
 
# {{{ do_convert() 
do_convert() 
{ 
if [ -d ${IPLIST_LISTDIR} ]; then 
cd ${IPLIST_LISTDIR} 
 
for file in ${INPUT_FILES}; do 
echo -n "converting $file..." 
convert_file $file 
echo "done." 
done 
 
if [ "${INPUT_FILES}" != "${OUTPUT_FILES}" ]; then 
for file in ${OUTPUT_FILES}; do 
echo -n "converting $file..." 
convert_file $file 
echo "done." 
done 
fi 
else 
echo "error: can't access ${IPLIST_LISTDIR}" >&2 && exit 1 
fi 
} 
# }}} 
 
if [ "$(id -u)" != "0" ]; then 
echo "error: You must be root to use ipblock" >&2 && exit 1 
fi 
 
while getopts "sdrucglh" opt; do 
case "$opt" in 
s)  
echo -n "Starting ipblock..." 
do_start 
echo "done." 
;; 
d) 
echo -n "Stopping ipblock..." 
do_stop 
echo "done." 
;; 
r) 
$0 -d 
sleep 1 
$0 -s 
;;  
u) 
do_update 
;; 
c) 
do_convert 
;; 
g) 
do_gui 
;; 
l) 
iplist -s 
echo 
iptables -L input_match -v 
echo 
iptables -L output_match -v 
if [ -e ${LOGFILE} ]; then 
echo 
echo "Last log messages..." 
tail -n 10 ${LOGFILE} 
fi 
;;  
\?|*) 
echo "Usage: `basename $0` [options]" >&2 
echo "Options:" >&2 
echo " -s start blocking" >&2 
echo " -d stop blocking" >&2 
echo " -r restart script" >&2 
echo " -u update lists" >&2 
echo " -c convert lists to ipl format" >&2 
echo " -g start ipblock GUI" >&2 
echo " -l show status" >&2 
echo " -h show this help" >&2 
exit 1 
;; 
esac 
done 
 
[ "$OPTIND" -gt "$#" ] && exit 0 
 
shift $(( $OPTIND - 1 )) 
 
case "$1" in 
start) 
$0 -s 
;; 
stop) 
$0 -d 
;; 
restart) 
$0 -r 
;;  
update) 
$0 -u 
;; 
convert) 
$0 -c 
;; 
status) 
$0 -l 
;;  
*) 
echo "Usage: `basename $0` {start|stop|restart|update|convert|status}" >&2 
exit 1 
;; 
esac 
 
exit 0
``` 


This adds the Iplist chains to the FORWARD chain, so all forwarded packets are filtered through the blocklists. Hope this helps someone.

---

### Post by uljanow on 2007-12-11
Version 0.16 has an IPTABLES_CHAIN option to select the build-in chains in the filter table.
```
...
IPTABLES_CHAIN="INPUT OUTPUT FORWARD"
...
```If it's just a router INPUT and OUTPUT may not be needed.

---

