---
title: "pptp call problem"
date: 2006-06-05
forum: Server Platforms
---

### Post by fantry on 2006-06-05
root@fantry:~/Desktop/pptp-linux-1.4.0# cat /etc/ppp/peers/ppp_nmlab
remotename ppp_nmlab
linkname ppp_nmlab
ipparam ppp_nmlab
pty "pptp 10.214.49.150 --nolaunchpppd"
name vpn
noauth
file /etc/ppp/options.pptp
root@fantry:~/Desktop/pptp-linux-1.4.0# cat /etc/ppp/options.pptp
lock
noauth
nobsdcomp
nodeflate
root@fantry:~/Desktop/pptp-linux-1.4.0# cat /etc/ppp/chap-secrets
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
vpn   ppp_nmlab npv *
root@fantry:~/Desktop/pptp-linux-1.4.0# pppd call ppp_nmlab logfd 1 updetach
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
LCP: timeout sending Config-Requests
Connection terminated.
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
tcflush failed: Bad file descriptor




what's possible reason cause this ,i really crawl at it.
thx !

---

### Post by fantry on 2006-06-05
root@fantry:~/Desktop/pptp-linux-1.4.0# vi /var/log/daemon.log
Sent control packet type is 5 'Echo-Request'
write error: Broken pipe
Closing connection
 Closing PPTP connection
write error: Bad file descriptor
 The synchronous pptp option is NOT activated
Sent control packet type is 1 'Start-Control-Connection-Request'
Received Start Control Connection Reply
Client connection established.
Sent control packet type is 7 'Outgoing-Call-Request'
Received Outgoing Call Reply.
Outgoing call established (call ID 0, peer's call ID 9472).
The synchronous pptp option is NOT activated
Sent control packet type is 7 'Outgoing-Call-Request'
Jun  5 15:10:21 localhost pptp[10116]: anon log[pptp_send_ctrl_packet:pptp_ctrl.c:599]: write error: Broken pipe
Jun  5 15:10:21 localhost pptp[10116]: anon log[call_callback:pptp_callmgr.c:77]: Closing connection

---

