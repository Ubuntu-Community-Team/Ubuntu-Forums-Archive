---
title: "&quot;kernel: [xxxx.xxxx] Outbound&quot; entries in syslogs (Hacked?)"
date: 2009-10-25
forum: Security
---

### Post by JamesKube on 2009-10-25
Hi All,

Not sure what the below log entry is indicating (sure looks like "outbound" traffic to a remote desktop session to me...which would really suck since I neither authorized, nor initiated any remote desktop sessions, but being a noob, hopefully I'm wrong):

[LOG]
Oct 25 19:54:24 james-box kernel: [446124.507227] Outbound IN= OUT=eth0 SRC=192.168.1.149 DST=208.203.4.205 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=14020 DF PROTO=TCP SPT=57717 DPT=21 WINDOW=5840 RES=0x00 SYN URGP=0 
[/LOG]

There are several occurances of the above entry, some with different IP's.  I've shutdown the box and am considering reformatting after creating an image for later "analysis".

Also, is it normal for Samba to broadcast to 192.168.1.255?  I have the below log entry on a different box (I'm making the hopeful assumption that this is Samba):

[LOG]
Oct 25 08:10:32 laptop kernel: [455510.488226] Outbound IN= OUT=eth1 SRC=192.168.1.116 DST=192.168.1.255 LEN=258 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP
 SPT=138 DPT=138 LEN=238
[/LOG]


Thanks in advance,
James

---

### Post by JamesKube on 2009-10-25
Just got done running "chkrootkit," which returned mostly reassuring results, althought it did report some potential LKM rootkits (apparently the hits that I received are common and false-positives); however, the below concerns me:

[chkrootkit result]
Checking `z2'...       user username deleted or never logged from lastlog!
[/chkrootkit result]

Checked lastlog and sure enough, my username show's a big "**Never logged in**" next to it.  Is it possible that someone hacked in and intentionally "broke" the logging functionality?

Thanks,
James

P.S.
I ran chkrootkit on my laptop which I believed was clean, the original post was concerning my desktop which I'm pretty confident has been compromised.

---

