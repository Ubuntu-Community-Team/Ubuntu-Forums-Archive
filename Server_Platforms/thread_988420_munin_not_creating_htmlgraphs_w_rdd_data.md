---
title: "munin not creating html/graphs w/ rdd data"
date: 2008-11-20
forum: Server Platforms
---

### Post by trmentry on 2008-11-20
I installed Munin on my Hardy 64 bit server.  

```

apt-get install munin munin-none smartmontools 

```

It started up and I started to get graphs with the default set of data points.

I then read about the smart_ and hddtemp_smartctl plugins.

I installed those plugins.

```

ln -s /usr/share/munin/plugins/smart_ smart_sda
(repeat to sds)
ln -s /usr/share/munin/plugins/hddtemp_smartctl 

```

I then restarted munin-node.  I can see it making the RDD data in /var/lib/munin

```

-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sda-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdb-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdc-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdd-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sde-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdf-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdg-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdh-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdi-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdj-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdk-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdl-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdm-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdn-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdo-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdp-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdq-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sdr-g.rrd
-rw-r--r-- 1 munin munin 50824 2008-11-20 19:20 localhost.localdomain-hddtemp_smartctl-sds-g.rrd


```

However it's not creating the graphs/html for these new data points.  

I tried to force this with the following

```

/usr/share/munin/munin-html --force-root
/usr/share/munin/munin-graphs --force-root

```


nothing shows up in the logs munin-graph.log or munin-html.log in /var/log/munin



Anyone have any ideas about why it's not graphing the new plugins but seems to be collecting the data fine?

Thanks

---

