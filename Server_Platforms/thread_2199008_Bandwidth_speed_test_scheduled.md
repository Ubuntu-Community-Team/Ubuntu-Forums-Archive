---
title: "Bandwidth speed test scheduled"
date: 2014-01-11
forum: Server Platforms
---

### Post by lucas.robb on 2014-01-11
Hi All,

I need some advice.  I'm switching providers for my internet and I want to start scheduled (hourly, daily, weekly, etc.) tests of my new ISP.  So far to test my bandwidth I've used speedtest.net but I don't know if its possible to schedule that one.  Lastly my ubuntu server acts as a functional MySQL server and I was hoping to output the scheduled tests to an SQL table/database.  Any help is appreciated, and anything I accomplish I'm more than happy to share back with the community (in any way that I can).

Thank you,
Lucas

---

### Post by houstonbofh on 2014-01-12
time wget -q [http://www.serv.com/pathtobigfile](http://www.serv.com/pathtobigfile)

Unfortunately, writing that output to a file is a bit challenging, and /usr/bin/time has a different and less useful output.  But it can get you started.

---

### Post by sandyd on 2014-01-12
First, find your city - if its a small city your in, you might want to choose the closest large city.

Then run the following to setup speedtest
```

wget -O speedtest-cli https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py
chmod +x speedtest-cli

```

The issue here is that a lot of ISPs dont report the location of the user correctly, so we must set it ourselves.
```

./speedtest-cli --list | grep -i "replacewithcity"
```

That should output something like (For Atlanta)
```

3595) Tulix Systems, Inc (Atlanta, GA, United States) [119.12 km]
1767) Comcast (Atlanta, GA, United States) [119.12 km]
2618) Colo@ (Atlanta, GA, United States) [119.12 km]
3165) Georgia Institute of Technology (Atlanta, GA, United States) [119.12 km]
```
If it doesn't output anything, keep trying with different large cities

Now, you can test using the server (in this case, dreamhost)
```

./speedtest-cli --server=2618
```

Demo:
```

[root@TinaFey ~]# ./speedtest-cli --list | grep -i "Atlanta"
3595) Tulix Systems, Inc (Atlanta, GA, United States) [119.12 km]
1767) Comcast (Atlanta, GA, United States) [119.12 km]
2618) Colo@ (Atlanta, GA, United States) [119.12 km]
3165) Georgia Institute of Technology (Atlanta, GA, United States) [119.12 km]
[root@TinaFey ~]# ./speedtest-cli --server=2618
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from QuickPacket LLC (<removed>)...
Hosted by Colo@ (Atlanta, GA) [119.12 km]: 17.484 ms
Testing download speed........................................
Download: 730.37 Mbit/s
Testing upload speed..................................................
Upload: 262.17 Mbit/s
[root@TinaFey ~]#

```

For a simpler output, you can add the --simple flag
```

[root@TinaFey ~]# ./speedtest-cli --server=2618 --simple
Ping: 25.749 ms
Download: 731.80 Mbit/s
Upload: 271.71 Mbit/s
[root@TinaFey ~]#

```

For sharing the output, you can add the --share flag
```
[root@TinaFey ~]# ./speedtest-cli --server=2618 --simple --share
Ping: 30.041 ms
Download: 754.68 Mbit/s
Upload: 274.54 Mbit/s
Share results: http://www.speedtest.net/result/<removed>

```
Now, just create a script for it.
For example,
```

#!/bin/bash
echo $(date) >> /home/sandyd/internet_speeds
/home/sandyd/speedtest-cli --server=2618 --simple >> /home/sandyd/internet_speeds

```

Make it executable

Run ```

crontab -e

```
and choose nano (2) when it asks what editor you want to use
add a crontab line there to run the file automatically, and you should have results in /home/sandyd/internet_speeds (or whatever path you specify)

---

### Post by stmiller on 2014-01-13
I have a public iperf server here, if that is helpful:

[http://iperf.scottlinux.com/](http://iperf.scottlinux.com/)


```

$ sudo apt-get install iperf

$ iperf -c iperf.scottlinux.com
```

---

