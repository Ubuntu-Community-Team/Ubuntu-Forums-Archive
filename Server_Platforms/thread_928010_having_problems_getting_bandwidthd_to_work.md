---
title: "having problems getting bandwidthd to work"
date: 2008-09-23
forum: Server Platforms
---

### Post by kustomjs on 2008-09-23
Hi Guys
I just installed bandwidthd and I am having problems I cant view it on my server like jbodyconnection.com/...... it just gives me a 404 so how can I fix this problem?

but I can see it under:file/show.cgi/var/lib/bandwidthd/htdocs/Subnet-1-192.168.1.0.html  not under jbodyconnection.com/

here is my bandwidthd conf.

```
####################################################
# Bandwidthd.conf
# 
# Commented out options are here to provide
# documentation and represent defaults

# Subnets to collect statistics on.  Traffic that 
# matches none of these subnets will be ignored.
# Syntax is either IP Subnet Mask or CIDR
#subnet 192.168.0.0/24

subnet 192.168.1.0/24


# Device to listen on
# Bandwidthd listens on the first device it detects
# by default.  Run "bandwidthd -l" for a list of 
# devices. 
#dev "eth0"

dev "eth0"

###################################################
# Options that don't usually get changed

# An interval is 2.5 minutes, this is how many 
# intervals to skip before doing a graphing run
#skip_intervals 0

# Graph cutoff is how many k must be transfered by an
# ip before we bother to graph it
#graph_cutoff 1024

#Put interface in promiscuous mode to score to traffic
#that may not be routing through the host machine.
#promiscuous true

promiscuous false

#Log data to cdf file htdocs/log.cdf
#output_cdf false

output_cdf true

#Set the cdf log output directory
#log_dir "/var/lib/bandwidthd"

#Read back the cdf file on startup
#recover_cdf false

recover_cdf true

#Libpcap format filter string used to control what bandwidthd see's
#Please always include "ip" in the string to avoid strange problems
#filter "ip"

#Draw Graphs - This default to true to graph the traffic bandwidthd is recording
#Usually set this to false if you only want cdf output or
#you are using the database output option.  Bandwidthd will use very little
#ram and cpu if this is set to false.
#graph true

#Set META REFRESH for static pages in seconds(default 150, use 0 to disable).
#meta_refresh 150

meta_refresh 150

#Set the static html output directory
#htdocs_dir "/var/lib/bandwidthd/htdocs"




```

---

### Post by cariboo on 2008-09-23
If you look at the bottom of the configuration file your documents are located in /var/lib/bandwidthd/htdoc. To view them using a browser you will probably have to create a symlink from /var/ww to /var/lib/bandwidthd/htdoc. To create a symlink do something like this:

```
sudo ln -s /var/lib/bandwidthd/htdocs bandwidth
```

in /var/www, then point your browser to jbodyconnection.com/bandwidth.

For more info:

```
man ln
```

and

```
man symlink
```

Jim

---

### Post by kustomjs on 2008-09-23
thank you for your help!!!!

---

