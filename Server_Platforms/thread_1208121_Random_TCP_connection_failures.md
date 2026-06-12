---
title: "Random TCP connection failures"
date: 2009-07-08
forum: Server Platforms
---

### Post by Booink on 2009-07-08
I'm getting random connection failures between two servers. 

Setup: frontend initiates the TCP connection to the backend. Rate is about 20/sec. Local port numbers do not wrap around before TIME_WAIT is over. tcp_tw_recycle / reuse are off, all tcp options are on defaults.

uname -a
Linux frontend01 2.6.24-24-server #1 SMP Tue Jun 30 20:24:57 UTC 2009 x86_64 GNU/Linux

The setup is 8.04 LTS Ubuntu server edition, x64.


The problem occurs after a load spike, when the backend cannot handle the incoming requests within reasonable time, but even after the load drops to normal, sockets randomly "time out". It is as if the TCP SYN's are never sent, netstat -s doesn't show dropped SYN's due to listen queue overflows. Running netstat -an | grep 1245 | sort (1245 = port number on backend), I noticed something weird:

tcp        0      0 87.253.133.193:39022    87.253.133.191:1245     TIME_WAIT
tcp        0      0 87.253.133.193:**39024**    87.253.133.191:1245     TIME_WAIT
tcp        0      0 87.253.133.193:**39024**    87.253.133.191:1245     TIME_WAIT
tcp        0      0 87.253.133.193:39063    87.253.133.191:1245     TIME_WAIT

Is this legal, using duplicate local port numbers at the same moment, to the same destination ip+port?

The random connection failures are gone after a reboot of the frontend, but this is quite annoying. Restarting apache (connection is made from within an apache child, hosting python) or the backend app doesn't make the problem go away, but rebooting the frontend fixes it until the next time it breaks. The connection drop occurs even in a standalone python script, so it's unlikely that this is a problem in userspace.

Test case:

```
#!/usr/bin/python

import socket, urllib2, time, datetime
socket.setdefaulttimeout(1)

def ping():
        start = time.time()
        try:
                urllib2.urlopen("http://87.253.133.191:1245/")
        except Exception, e:
                print e
        print "%s - %.3f ms" % (datetime.datetime.now(), (time.time() - start) * 1000)

while True:
        ping()
        time.sleep(0.2)

```The timeout is set low on 1 second, but increasing it doesn't help, the normal response time is within 10ms. Running the same script from another machine that isn't affected gives no packet loss, neither does running the script from frontend01 before a load spike triggers the bug.


I'm not sure where to post this to get someone looking at it, so I just dumped it on the forums of the OS we use. If this isn't the right place, a reply with a pointer to the appropriate place would be nice.

---

