---
title: "FWANALOG (logging UFW issue)"
date: 2010-05-29
forum: Server Platforms
---

### Post by lordyarox on 2010-05-29
I'm having issues with auto-logging with fwanalog. Basically it logs the firewall activities in the fwanalog.all.log file, but it doesn't update today.txt (a very nicely layed-out daily log in the "/var/log/fwanalog" folder.

My question is - how can I get it to update today.txt with the newest firewall events?

I connect & manage my server using SSH (Putty) and sometimes WinSCP (GUI file manager - mostly for viewing due to lack of root privileges).

What I have tried:

Deleting the lock file in the fwanalog directory and starting it by typing "sudo fwanalog" and "sudo fwanalog -t"


> leon@leon-server:~$ sudo fwanalog -h

fwanalog ver. 0.6.9
This is a program to parse firewall logs and analyze them with Analog.

Usage: fwanalog [-h | --help] [-c conffile] [-r] [-t] [-y] [-a IP-addr] [-p packet]

Options:

-h, --help    Display this help message and exit.
-c conffile   Use this config file instead of fwanalog.opts
-r            Rotate log cache (not necessary anymore)
-t            Only update statistics for today (e.g. for hourly use)
                  The sep_hosts and sep_packets commands in fwanalog.opts
                  are ignored.
-y            The same as -t, only for yesterday
-a IP-addr    Create a separate report for this host
-p packet     Create a separate report for this packet
              Format: target/protocol/portnumber
  e.g. 192.168.0.1/tcp/21 or firewall/udp/137

NOTE: You must be the superuser to run this script, or have at least
  read rights to the firewall log. (See README.sudo for how to
  do this as a normal user.)
leon@leon-server:~$


I was configuring my server up to about 4AM yesterday, and when configuring the logging, today.txt was generated (as visible at the top of the following log - the time):

> Block statistics of your firewall, created by fwanalog 0.6.9
============================================================

Analyzed blocked packets from Sat, May 29 2010 at  3:21 AM to Sat, May 29
  2010 at  3:37 AM (0.01 days).
----------------------------------------------------------------------------

General Summary
---------------
Blocked packets: 159
Distinct blocked packets: 11
Distinct hosts blocked: 51
Size of all dropped packets together: 15.65 kilobytes
----------------------------------------------------------------------------

Blocked Packet Report
---------------------
Listing blocked packets, sorted by the number of blocked packets.

#blocks: %blocks: kbytes:          last time: blocked packet
-------: -------: ------: ------------------: --------------
    109:  68.55%:  12.34: May/29/10  3:37 AM: 89.142.221.137
     90:  56.60%:  11.35: May/29/10  3:37 AM:   89.142.221.137/udp
     57:  35.85%:   7.29: May/29/10  3:37 AM:     89.142.221.137:30106/udp
     31:  19.50%:   3.81: May/29/10  3:37 AM:     89.142.221.137:26785/udp
      2:   1.26%:   0.25: May/29/10  3:23 AM:     89.142.221.137:22559/udp
     18:  11.32%:   0.93: May/29/10  3:37 AM:   89.142.221.137/tcp
      9:   5.66%:   0.42: May/29/10  3:35 AM:     89.142.221.137:22559/tcp
      6:   3.77%:   0.35: May/29/10  3:31 AM:     89.142.221.137:10011/tcp
      3:   1.89%:   0.15: May/29/10  3:37 AM:     89.142.221.137:59110/tcp
      1:   0.63%:   0.06: May/29/10  3:31 AM:   89.142.221.137/icmp
      1:   0.63%:   0.06: May/29/10  3:31 AM:     89.142.221.137/icmp/echo (8)
     16:  10.06%:   1.04: May/29/10  3:36 AM: 193.189.160.13
     16:  10.06%:   1.04: May/29/10  3:36 AM:   193.189.160.13/udp
     16:  10.06%:   1.04: May/29/10  3:36 AM:     193.189.160.13:domain (53)/udp
     14:   8.81%:   0.82: May/29/10  3:35 AM: 193.2.1.88
     14:   8.81%:   0.82: May/29/10  3:35 AM:   193.2.1.88/tcp
     14:   8.81%:   0.82: May/29/10  3:35 AM:     193.2.1.88:http (80)/tcp
     12:   7.55%:   0.98: May/29/10  3:37 AM: 213.250.19.90
     12:   7.55%:   0.98: May/29/10  3:37 AM:   213.250.19.90/icmp
     12:   7.55%:   0.98: May/29/10  3:37 AM:     213.250.19.90/icmp/echo (8)
      8:   5.03%:   0.47: May/29/10  3:35 AM: 208.78.70.70
      8:   5.03%:   0.47: May/29/10  3:35 AM:   208.78.70.70/tcp
      8:   5.03%:   0.47: May/29/10  3:35 AM:     208.78.70.70:http (80)/tcp
----------------------------------------------------------------------------

Packet Source Host Report
-------------------------
Listing hosts with at least 0.5% of the blocked packets, sorted by the
  number of blocked packets.

 #: #blocks: %blocks: kbytes:          last time: host
--: -------: -------: ------: ------------------: ----
 1:      50:  31.45%:   3.31: May/29/10  3:37 AM: bsn-142-221-137.dial-up.dsl.siol.net
 2:      28:  17.61%:   3.45: May/29/10  3:37 AM: 222.63.34.65
 3:       6:   3.77%:   0.35: May/29/10  3:31 AM: tsviewer.com
 4:       6:   3.77%:   0.28: May/29/10  3:35 AM: bsn-142-7-9.dsl.siol.net
 5:       3:   1.89%:   0.38: May/29/10  3:36 AM: 97.106.115.196
 6:       3:   1.89%:   0.14: May/29/10  3:34 AM: bsn-142-81-226.dial-up.dsl.siol.net
 7:       3:   1.89%:   0.15: May/29/10  3:37 AM: adsl.viettel.vn
 8:       2:   1.26%:   0.26: May/29/10  3:31 AM: 190-176-48-156.speedy.com.ar
 9:       2:   1.26%:   0.26: May/29/10  3:35 AM: cc1091720-a.hnglo1.ov.home.nl
10:       2:   1.26%:   0.26: May/29/10  3:33 AM: ip-89-250-203-146.rev.snt.net.pl
11:       2:   1.26%:   0.26: May/29/10  3:34 AM: 118.172.141.146.adsl.dynamic.totbb.net
12:       2:   1.26%:   0.26: May/29/10  3:31 AM: 109.173.40.85
13:       2:   1.26%:   0.26: May/29/10  3:33 AM: cpe-76-172-92-131.socal.res.rr.com
14:       2:   1.26%:   0.25: May/29/10  3:31 AM: host-89-228-131-96.gorzow.mm.pl
15:       2:   1.26%:   0.26: May/29/10  3:32 AM: ti0154a340-0157.bb.online.no
16:       2:   1.26%:   0.25: May/29/10  3:31 AM: 175.106.176.241
17:       2:   1.26%:   0.25: May/29/10  3:26 AM: 119.139.187.24
18:       2:   1.26%:   0.26: May/29/10  3:37 AM: 18715045094.user.veloxzone.com.br
19:       2:   1.26%:   0.26: May/29/10  3:37 AM: 93.180.123.8
20:       2:   1.26%:   0.26: May/29/10  3:31 AM: 16.8.95-79.rev.gaoland.net
21:       2:   1.26%:   0.26: May/29/10  3:33 AM: 111-240-7-55.dynamic.hinet.net
22:       2:   1.26%:   0.26: May/29/10  3:31 AM: 92-249-216-15.pool.digikabel.hu
23:       2:   1.26%:   0.25: May/29/10  3:23 AM: 114-34-126-24.hinet-ip.hinet.net
24:       1:   0.63%:   0.13: May/29/10  3:22 AM: 75-141-88-67.dhcp.knwk.wa.charter.com
25:       1:   0.63%:   0.13: May/29/10  3:27 AM: 66.183.216.33
26:       1:   0.63%:   0.13: May/29/10  3:23 AM: c-76-101-50-202.hsd1.fl.comcast.net
27:       1:   0.63%:   0.13: May/29/10  3:28 AM: 52puntacana95.codetel.net.do
28:       1:   0.63%:   0.13: May/29/10  3:22 AM: cpc3-sand8-2-0-cust120.wolv.cable.virginmedia.com
29:       1:   0.63%:   0.13: May/29/10  3:22 AM: a145-178.me.chu.edu.tw
30:       1:   0.63%:   0.13: May/29/10  3:29 AM: athedsl-165299.home.otenet.gr
31:       1:   0.63%:   0.13: May/29/10  3:30 AM: pool-71-184-112-131.bstnma.fios.verizon.net
32:       1:   0.63%:   0.13: May/29/10  3:21 AM: aannecy-158-1-31-139.w90-42.abo.wanadoo.fr
33:       1:   0.63%:   0.13: May/29/10  3:21 AM: 173-18-131-91.client.mchsi.com
34:       1:   0.63%:   0.13: May/29/10  3:25 AM: s0106001e8c3652ae.ca.shawcable.net
35:       1:   0.63%:   0.13: May/29/10  3:21 AM: 78-23-2-27.access.telenet.be
36:       1:   0.63%:   0.13: May/29/10  3:23 AM: dsl-5-12.wholesaledsl.com.au
37:       1:   0.63%:   0.13: May/29/10  3:24 AM: p5ddcd881.dip.t-dialin.net
38:       1:   0.63%:   0.13: May/29/10  3:25 AM: 184-78-142-179.sea.clearwire-wmx.net
39:       1:   0.63%:   0.13: May/29/10  3:27 AM: dsl-189-171-4-158-dyn.prod-infinitum.com.mx
40:       1:   0.63%:   0.13: May/29/10  3:25 AM: 52.60.in-addr.arpa.tm.net.my
41:       1:   0.63%:   0.13: May/29/10  3:31 AM: c-67-183-5-181.hsd1.wa.comcast.net
42:       1:   0.63%:   0.13: May/29/10  3:28 AM: 178.128.246.7.dsl.dyn.forthnet.gr
43:       1:   0.63%:   0.13: May/29/10  3:28 AM: 159-10.gp.evo.bg
44:       1:   0.63%:   0.13: May/29/10  3:21 AM: 201-24-165-148.cpece705.dsl.brasiltelecom.net.br
45:       1:   0.63%:   0.06: May/29/10  3:31 AM: bsn-176-191-232.dial-up.dsl.siol.net
46:       1:   0.63%:   0.13: May/29/10  3:21 AM: 87.68.172.18.cable.012.net.il
47:       1:   0.63%:   0.13: May/29/10  3:23 AM: 201-75-82-71-ma.cpe.vivax.com.br
48:       1:   0.63%:   0.13: May/29/10  3:23 AM: 195.189.107.1
49:       1:   0.63%:   0.13: May/29/10  3:21 AM: 98.160.66.189.isp.timbrasil.com.br
50:       1:   0.63%:   0.13: May/29/10  3:22 AM: pool-72-87-212-208.lsanca.dsl-w.verizon.net
51:       1:   0.63%:   0.12: May/29/10  3:22 AM: 118.249.53.142
----------------------------------------------------------------------------

Organization Report
-------------------
Listing organizations with at least 0.5% of the blocked packets, sorted by 
  the number of blocked packets.

 #: #blocks: %blocks: kbytes:          last time: organization
--: -------: -------: ------: ------------------: ------------
 1:      60:  37.74%:   3.79: May/29/10  3:37 AM: siol.net
 2:      28:  17.61%:   3.45: May/29/10  3:37 AM: 222.63
 3:       6:   3.77%:   0.35: May/29/10  3:31 AM: tsviewer.com
 4:       4:   2.52%:   0.51: May/29/10  3:33 AM: hinet.net
 5:       3:   1.89%:   0.38: May/29/10  3:36 AM: 97
 6:       3:   1.89%:   0.15: May/29/10  3:37 AM: vn
 7:       2:   1.26%:   0.25: May/29/10  3:30 AM: verizon.net
 8:       2:   1.26%:   0.25: May/29/10  3:31 AM: 175.106
 9:       2:   1.26%:   0.26: May/29/10  3:31 AM: gaoland.net
10:       2:   1.26%:   0.26: May/29/10  3:37 AM: 93
11:       2:   1.26%:   0.26: May/29/10  3:34 AM: totbb.net
12:       2:   1.26%:   0.26: May/29/10  3:32 AM: online.no
13:       2:   1.26%:   0.26: May/29/10  3:31 AM: speedy.com.ar
14:       2:   1.26%:   0.26: May/29/10  3:37 AM: veloxzone.com.br
15:       2:   1.26%:   0.26: May/29/10  3:31 AM: 109
16:       2:   1.26%:   0.25: May/29/10  3:31 AM: gorzow.mm.pl
17:       2:   1.26%:   0.26: May/29/10  3:31 AM: comcast.net
18:       2:   1.26%:   0.26: May/29/10  3:31 AM: digikabel.hu
19:       2:   1.26%:   0.26: May/29/10  3:35 AM: home.nl
20:       2:   1.26%:   0.26: May/29/10  3:33 AM: rr.com
21:       2:   1.26%:   0.26: May/29/10  3:33 AM: snt.net.pl
22:       2:   1.26%:   0.25: May/29/10  3:26 AM: 119
23:       1:   0.63%:   0.13: May/29/10  3:28 AM: evo.bg
24:       1:   0.63%:   0.13: May/29/10  3:22 AM: chu.edu.tw
25:       1:   0.63%:   0.13: May/29/10  3:28 AM: net.do
26:       1:   0.63%:   0.13: May/29/10  3:23 AM: 195.189
27:       1:   0.63%:   0.13: May/29/10  3:27 AM: prod-infinitum.com.mx
28:       1:   0.63%:   0.13: May/29/10  3:22 AM: charter.com
29:       1:   0.63%:   0.13: May/29/10  3:22 AM: virginmedia.com
30:       1:   0.63%:   0.13: May/29/10  3:25 AM: clearwire-wmx.net
31:       1:   0.63%:   0.13: May/29/10  3:21 AM: brasiltelecom.net.br
32:       1:   0.63%:   0.13: May/29/10  3:23 AM: vivax.com.br
33:       1:   0.63%:   0.13: May/29/10  3:21 AM: mchsi.com
34:       1:   0.63%:   0.13: May/29/10  3:21 AM: telenet.be
35:       1:   0.63%:   0.13: May/29/10  3:24 AM: t-dialin.net
36:       1:   0.63%:   0.13: May/29/10  3:25 AM: tm.net.my
37:       1:   0.63%:   0.13: May/29/10  3:21 AM: 012.net.il
38:       1:   0.63%:   0.13: May/29/10  3:21 AM: wanadoo.fr
39:       1:   0.63%:   0.13: May/29/10  3:28 AM: forthnet.gr
40:       1:   0.63%:   0.13: May/29/10  3:29 AM: otenet.gr
41:       1:   0.63%:   0.13: May/29/10  3:27 AM: 66.183
42:       1:   0.63%:   0.13: May/29/10  3:21 AM: timbrasil.com.br
43:       1:   0.63%:   0.13: May/29/10  3:23 AM: wholesaledsl.com.au
44:       1:   0.63%:   0.12: May/29/10  3:22 AM: 118
45:       1:   0.63%:   0.13: May/29/10  3:25 AM: shawcable.net
----------------------------------------------------------------------------

Hourly Summary
--------------
Each unit (+) represents 4 blocked packets or part thereof.

hour: #blocks: %blocks: kbytes: 
----: -------: -------: ------: 
   0:       0:        :   0.00: 
   1:       0:        :   0.00: 
   2:       0:        :   0.00: 
   3:     159:    100%:  15.65: ++++++++++++++++++++++++++++++++++++++++
   4:       0:        :   0.00: 
   5:       0:        :   0.00: 
   6:       0:        :   0.00: 
   7:       0:        :   0.00: 
   8:       0:        :   0.00: 
   9:       0:        :   0.00: 
  10:       0:        :   0.00: 
  11:       0:        :   0.00: 
  12:       0:        :   0.00: 
  13:       0:        :   0.00: 
  14:       0:        :   0.00: 
  15:       0:        :   0.00: 
  16:       0:        :   0.00: 
  17:       0:        :   0.00: 
  18:       0:        :   0.00: 
  19:       0:        :   0.00: 
  20:       0:        :   0.00: 
  21:       0:        :   0.00: 
  22:       0:        :   0.00: 
  23:       0:        :   0.00: 
----------------------------------------------------------------------------

Packet Size Report
------------------

       size: #blocks: %blocks: kbytes: %bytes:          last time: 
-----------: -------: -------: ------: ------: ------------------: 
          0:       0:        :   0.00:       :                   : 
   1B-  10B:       0:        :   0.00:       :                   : 
  11B- 100B:      69:  43.40%:   4.30: 27.47%: May/29/10  3:37 AM: 
 101B-  1kB:      90:  56.60%:  11.35: 72.53%: May/29/10  3:37 AM: 
----------------------------------------------------------------------------

Interface Report
----------------
Listing interfaces with at least 5 blocked packets, sorted by the number of
  blocked packets.

#blocks: %bytes: interface
-------: ------: ---------
    159:   100%: ppp0
----------------------------------------------------------------------------

This analysis was produced by analog 6.0.


Why was it generated then, and how can I get it to update the file / generate a new daily log?

---

### Post by lordyarox on 2010-05-29
I would also like to emphasize (as mentioned in my first post) that the other logging capabilities are functioning correctly, but the time & effort needed to manually generate a report such as "today.txt" outweighs the purpose of having a logger, which is why I desperately need the "today.txt" to be updated, or at least knowledge of why it isn't updating.

Thanks in advance for any replies!

Edit: The error-log only registers one exit

> analog: Received interrupt signal: exiting


---

### Post by lordyarox on 2010-05-30
I have no idea what went wrong last time, running

> sudo fwanalog

seems to update all logs. Solved?

---

