---
title: "Zentyal proxy server"
date: 2014-01-10
forum: Server Platforms
---

### Post by dao.alinker.tz on 2014-01-10
Dear pros, 

I'm very new to linux and now I'm working as a network engineer in a small business company. The problem is .., I use Zentyal 3.2 as a proxy server in my environment. Everything is going fine, but one thing, that makes me bother is getting slow my network. I definitely know almost everybody loves to download things they like. 

Therefore, I need to monitor my clients right? and I'm now trying to install and use "Bandwidthd" on Zentyal proxy server. But I can't make it work. I've faced many problems. Although now I've finished installation "bandwidthd", I cannot make it to configure on browser like [https://192.168.xx.xx/bandwidth](https://192.168.xx.xx/bandwidth). Does anybody know the way to help me out of this problem? The followings are the way how I install and configure bandwidthd.

xxxxxxxxxxxxxxxxxx
- apt-get install bandwidthd
- sudo cp /usr/share/doc/bandwidthd/bandwidthd.conf /etc/bandwidthd/bandwidthd.conf (because I couldn't find the conf file under /etc/bandwidth/) 
#then I made configuration like the following.
- etc/init.d/bandwidthd start
- ln -s /var/lib/bandwidthd/htdocs /var/www/bandwidth

Then I didn't find any work was done.  :( 

###################################################
# Bandwidthd.conf
# 
# Commented out options are here to provide
# documentation and represent defaults

# Subnets to collect statistics on.  Traffic that 
# matches none of these subnets will be ignored.
# Syntax is either IP Subnet Mask or CIDR
subnet [192.168.2.0/24]("http://192.168.2.0/24")

#DEBCONF_SUBNETS#

# Device to listen on
# Bandwidthd listens on the first device it detects
# by default.  Run "bandwidthd -l" for a list of 
# devices. 
dev "eth1"

#DEBCONF_DEVS#

###################################################
# Options that don't usually get changed

# An interval is 2.5 minutes, this is how many 
# intervals to skip before doing a graphing run
skip_intervals 0

# Graph cutoff is how many k must be transfered by an
# ip before we bother to graph it
graph_cutoff 1024

#Put interface in promiscuous mode to score to traffic
#that may not be routing through the host machine.
promiscuous true

#DEBCONF_PROMISC#

#Log data to cdf file htdocs/log.cdf
output_cdf false

#DEBCONF_OUTPUTCDF#

#Set the cdf log output directory
log_dir "/var/lib/bandwidthd"

###################################################
# Bandwidthd.conf
# 
# Commented out options are here to provide
# documentation and represent defaults

# Subnets to collect statistics on.  Traffic that 
# matches none of these subnets will be ignored.
# Syntax is either IP Subnet Mask or CIDR
subnet [192.168.2.0/24]("http://192.168.2.0/24")

#DEBCONF_SUBNETS#

# Device to listen on
# Bandwidthd listens on the first device it detects
# by default.  Run "bandwidthd -l" for a list of 
# devices. 
dev "eth1"

#DEBCONF_DEVS#

###################################################
# Options that don't usually get changed

# An interval is 2.5 minutes, this is how many 
# intervals to skip before doing a graphing run
skip_intervals 0

# Graph cutoff is how many k must be transfered by an
# ip before we bother to graph it
graph_cutoff 1024

#Put interface in promiscuous mode to score to traffic
#that may not be routing through the host machine.
promiscuous true

#DEBCONF_PROMISC#

#Log data to cdf file htdocs/log.cdf
output_cdf false

#DEBCONF_OUTPUTCDF#

#Set the cdf log output directory
log_dir "/var/lib/bandwidthd"

---

