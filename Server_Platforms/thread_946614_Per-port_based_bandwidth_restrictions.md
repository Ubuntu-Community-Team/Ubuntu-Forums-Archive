---
title: "Per-port based bandwidth restrictions"
date: 2008-10-13
forum: Server Platforms
---

### Post by Muppet on 2008-10-13
Hey,

I'm looking for a feature where I can restrict networks speeds on a per-port basis.

I found a thread which specified pretty much what I want to achieve ([http://ubuntuforums.org/showthread.php?t=733683&highlight=limit+bandwidth+protocol](http://ubuntuforums.org/showthread.php?t=733683&highlight=limit+bandwidth+protocol)), however I'm just wondering if anyone knows of a better - ok, easier :p - solution. I've been susprised with the lack of port-based solutions for shaping or limiting network traffic, unless I'm just a bad googler?

I understand that you create different profiles with varying speeds which you can then assign to source ports through iptables. 

Any pointers or tips for the above method also would be appreciated. 

Thanks.

---

### Post by Martje_001 on 2008-10-13
You're looking for a traffic shaper ;). There's one in the Ubuntu repositorys. It's called 'shaper'.

---

### Post by Muppet on 2008-10-13
> **Martje_001 said:**
> You're looking for a traffic shaper ;). There's one in the Ubuntu repositorys. It's called 'shaper'.

Any chance you can elaborate on that? 

I know shaper is CBQ but the documention about shaper is pretty weak and information about it seems almost non-existent.

Can anyone give me an example?

Cheers.

---

### Post by Martje_001 on 2008-10-14
I have to admit I find it really hard myself (yeah! I've got something to do..). Here's the readme:
```
# README
# ------
#
# First of all - this is just a SIMPLE EXAMPLE of CBQ power.
# Don't ask me "why" and "how" :)
#
# This script is meant to simplify setup and management of relatively simple
# CBQ-based traffic control on Linux. Access to advanced networking features
# of Linux kernel is provided by "ip" and "tc" utilities from A. Kuznetsov's
# iproute2 package, available at ftp://ftp.inr.ac.ru/ip-routing. Because the
# utilities serve primarily to translate user wishes to RTNETLINK commands,
# their interface is rather spartan, intolerant and requires quite a lot of
# typing. And typing is what this script attempts to reduce :)
#
# The advanced networking stuff in Linux is pretty flexible and this script
# aims to bring some of its features to the not-so-hard-core Linux users. Of
# course, there is a tradeoff between simplicity and flexibility and you may
# realize that the flexibility suffered too much for your needs -- time to
# face "ip" and "tc" interface.
#
# To speed up the "start" command, simple caching was introduced in version
# 0.6.4. The caching works so that the sequence of "tc" commands for given
# configuration is stored in a file (/var/cache/cbq.init by default) which
# is used next time the "start" command is run to avoid repeated parsing of
# configuration files. This cache is invalidated whenever any of the CBQ
# configuration files changes. If you want to run "shaper start" without
# caching, run it as "shaper start nocache". If you want to force cache
# invalidation, run it as "shaper start invalidate". Caching is disabled
# if you have logging enabled (ie. CBQ_DEBUG is not empty).
#
# If you only want cqb.init to translate your configuration to "tc" commands,
# use "compile" command which will output "tc" commands required to build
# your configuration. Bear in mind that "compile" does not check if the "tc"
# commands were successful - this is done (in certain places) only when the
# "start nocache" command is used, which is also useful when creating the
# configuration to check whether it is completely valid.
#
# All CBQ parameters are valid for Ethernet interfaces only, The script was
# tested on various Linux kernel versions from series 2.1 to 2.4 and several
# distributions with KSI Linux (Nostromo version) as the premier one.
#
#
# HOW DOES IT WORK?
# -----------------
#
# Every traffic class must be described by a file in the $CBQ_PATH directory
# (/etc/shaper by default) - one file per class.
#
# The config file names must obey mandatory format: cbq-<clsid>.<name> where
# <clsid> is two-byte hexadecimal number in range <0002-FFFF> (which in fact
# is a CBQ class ID) and <name> is the name of the class -- anything to help
# you distinguish the configuration files. For small amount of classes it is
# often possible (and convenient) to let <clsid> resemble bandwidth of the
# class.
#
# Example of valid config name:
#	cbq-1280.My_first_shaper
#
#
# The configuration file may contain the following parameters:
#
### Device parameters
#
# DEVICE=<ifname>,<bandwidth>[,<weight>]	mandatory
# DEVICE=eth0,10Mbit,1Mbit
#
#	<ifname> is the name of the interface you want to control
#		traffic on, e.g. eth0
#	<bandwidth> is the physical bandwidth of the device, e.g. for
#		ethernet 10Mbit or 100Mbit, for arcnet 2Mbit
#	<weight> is tuning parameter that should be proportional to
#		<bandwidth>. As a rule of thumb: <weight> = <bandwidth> / 10
#
# When you have more classes on one interface, it is enough to specify
# <bandwidth> [and <weight>] only once, therefore in other files you only
# need to set DEVICE=<ifname>.
#
### Class parameters
#
# RATE=<speed>					mandatory
# RATE=5Mbit
#
#	Bandwidth allocated to the class. Traffic going through the class is
#	shaped to conform to specified rate. You can use Kbit, Mbit or bps,
#	Kbps and Mbps as suffices. If you don't specify any unit, bits/sec
#	are used. Also note that "bps" means "bytes per second", not bits.
#
# WEIGHT=<speed> 				mandatory
# WEIGHT=500Kbit
#
#	Tuning parameter that should be proportional to RATE. As a rule
#	of thumb, use WEIGHT ~= RATE / 10.
#
# PRIO=<1-8>					optional, default 5
# PRIO=5
#
#	Priority of class traffic. The higher the number, the lesser
#	the priority. Priority of 5 is just fine.
#
# PARENT=<clsid>				optional, default not set
# PARENT=1280
#
#	Specifies ID of the parent class to which you want this class be
#	attached. You might want to use LEAF=none for the parent class as
#	mentioned below. By using this parameter and carefully ordering the
#	configuration files, it is possible to create simple hierarchical
#	structures of CBQ classes. The ordering is important so that parent
#	classes are constructed prior to their children.
#
# LEAF=none|tbf|sfq				optional, default "tbf"
#
#	Tells the script to attach specified leaf queueing discipline to CBQ
#	class. By default, TBF is used. Note that attaching TBF to CBQ class
#	shapes the traffic to conform to TBF parameters and prevents the class
#	from borrowing bandwidth from its parent even if you have BOUNDED set
#	to "no". To allow the class to borrow bandwith (provided it is not
#	bounded), you must set LEAF to "none" or "sfq".
#
#	If you want to ensure (approximately) fair sharing of bandwidth among
#	several hosts in the same class, you might want to specify LEAF=sfq to
#	attach SFQ as leaf queueing discipline to that class.
#
# BOUNDED=yes|no				optional, default "yes"
#
#	If set to "yes", the class is not allowed to borrow bandwidth from
#	its parent class in overlimit situation. If set to "no", the class
#	will be allowed to borrow bandwidth from its parent.
#
# Note:	Don't forget to set LEAF to "none" or "sfq", otherwise the class will
#	have TBF attached to itself and will not be able to borrow unused
#	bandwith from its parent.
#
# ISOLATED=yes|no				optional, default "no"
#
#	If set to "yes", the class will not lend unused bandwidth to
#	its children.
#
### TBF qdisc parameters
#
# BUFFER=<bytes>[/<bytes>]			optional, default "10Kb/8"
#
#	This parameter controls the depth of the token bucket. In other
#	words it represents the maximal burst size the class can send.
#	The optional part of parameter is used to determine the length
#	of intervals in packet sizes, for which the transmission times
#	are kept.
#
# LIMIT=<bytes>					optional, default "15Kb"
#
#	This parameter determines the maximal length of backlog. If
#	the queue contains more data than specified by LIMIT, the
#	newly arriving packets are dropped. The length of backlog
#	determines queue latency in case of congestion.
#
# PEAK=<speed>					optional, default not set
#
#	Maximal peak rate for short-term burst traffic. This allows you
#	to control the absolute peak rate the class can send at, because
#	single TBF that allows 256Kbit/s would of course allow rate of
#	512Kbit for half a second or 1Mbit for a quarter of second.
#
# MTU=<bytes>  					optional, default "1500"
#
#	Maximum number of bytes that can be sent at once over the
#	physical medium. This parameter is required when you specify
#	PEAK parameter. It defaults to MTU of ethernet - for other
#	media types you might want to change it.
#
# Note: Setting TBF as leaf qdisc will effectively prevent the class from
#	borrowing bandwidth from the ancestor class, because even if the
#	class allows more traffic to pass through, it is then shaped to
#	conform to TBF.
#
### SFQ qdisc parameters
#
# The SFQ queueing discipline is a cheap way for sharing class bandwidth
# among several hosts. As it is stochastic, the fairness is approximate but
# it will do the job in most cases. If you want real fairness, you should
# probably use WRR (weighted round robin) or WFQ queueing disciplines. Note
# that SFQ does not do any traffic shaping - the shaping is done by the CBQ
# class the SFQ is attached to.
#
# QUANTUM=<bytes>				optional, default not set
#
#	This parameter should not be set lower than link MTU, for ethernet
#	it is 1500b, or (with MAC header) 1514b which is the value used
#	in Alexey Kuznetsov's examples.
#
# PERTURB=<seconds>				optional, default "10"
#
#	Period of hash function perturbation. If unset, hash reconfiguration
#	will never take place which is what you probably don't want. The
#	default value of 10 seconds is probably a good one.
#
### Filter parameters
#
# RULE=[[saddr[/prefix]][:port[/mask]],][daddr[/prefix]][:port[/mask]]
#
#	These parameters make up "u32" filter rules that select traffic for
#	each of the classes. You can use multiple RULE fields per config.
#
#	The optional port mask should only be used by advanced users who
#	understand how the u32 filter works.
#
# Some examples:
#
#	RULE=10.1.1.0/24:80
#		selects traffic going to port 80 in network 10.1.1.0
#
#	RULE=10.2.2.5
#		selects traffic going to any port on single host 10.2.2.5
#
#	RULE=10.2.2.5:20/0xfffe
#		selects traffic going to ports 20 and 21 on host 10.2.2.5
#
#	RULE=:25,10.2.2.128/26:5000
#		selects traffic going from anywhere on port 50 to
#		port 5000 in network 10.2.2.128
#
#	RULE=10.5.5.5:80,
#		selects traffic going from port 80 of single host 10.5.5.5
#
#
#
# REALM=[srealm,][drealm]
#
#	These parameters make up "route" filter rules that classify traffic
#	according to packet source/destination realms. For information about
#	realms, see Alexey Kuznetsov's IP Command Reference. This script
#	does not define any realms, it justs builds "tc filter" commands
#	for you if you need to classify traffic this way.
#
#	Realm is either a decimal number or a string referencing entry in
#	/etc/iproute2/rt_realms (usually).
#
# Some examples:
#
#	REALM=russia,internet
#		selects traffic going from realm "russia" to realm "internet"
#
#	REALM=freenet,
#		selects traffic going from realm "freenet"
#
#	REALM=10
#		selects traffic going to realm 10
#
#
#
# MARK=<mark>
#
#	These parameters make up "fw" filter rules that select traffic for
#	each of the classes accoring to firewall "mark". Mark is a decimal
#	number packets are tagged with if firewall rules say so. You can
#	use multiple MARK fields per config.
#
#
# Note: Rules for different filter types can be combined. Attention must be
#	paid to the priority of filter rules, which can be set below using
#	PRIO_{RULE,MARK,REALM} variables.
#
### Time ranging parameters
#
# TIME=[<dow>,<dow>, ...,<dow>/]<from>-<till>;<rate>/<weight>[/<peak>]
# TIME=0,1,2,5/18:00-06:00;256Kbit/25Kbit
# TIME=60123/18:00-06:00;256Kbit/25Kbit
# TIME=18:00-06:00;256Kbit/25Kbit
#
#	This parameter allows you to differentiate the class bandwidth
#	throughout the day. You can specify multiple TIME parameters, if
#	the times overlap, last match is taken. The fields <rate>, <weight>
#	and <peak> correspond to parameters RATE, WEIGHT and PEAK (which
#	is optional and applies to TBF leaf qdisc only).
#
#	You can also specify days of week when the TIME rule applies. <dow>
#	is numeric, 0 corresponds to sunday, 1 corresponds to monday, etc.
#
###
#
# Sample configuration file: cbq-1280.My_first_shaper
#
# --------------------------------------------------------------------------
# DEVICE=eth0,10Mbit,1Mbit
# RATE=128Kbit
# WEIGHT=10Kbit
# PRIO=5
# RULE=192.128.1.0/24
# --------------------------------------------------------------------------
#
# The configuration says that we will control traffic on 10Mbit ethernet
# device eth0 and the traffic going to network 192.168.1.0 will be
# processed with priority 5 and shaped to rate of 128Kbit.
#
# Note that you can control outgoing traffic only. If you want to control
# traffic in both directions, you must set up CBQ for both interfaces.
#
# Consider the following example:
#
#                    +---------+      192.168.1.1
# BACKBONE -----eth0-|  linux  |-eth1------*-[client]
#                    +---------+
#
# Imagine you want to shape traffic from backbone to the client to 28Kbit
# and traffic in the opposite direction to 128Kbit. You need to setup CBQ
# on both eth0 and eth1 interfaces, thus you need two config files:
#
# cbq-028.backbone-client
# --------------------------------------------------------------------------
# DEVICE=eth1,10Mbit,1Mbit
# RATE=28Kbit
# WEIGHT=2Kbit
# PRIO=5
# RULE=192.168.1.1
# --------------------------------------------------------------------------
#
# cbq-128.client-backbone
# --------------------------------------------------------------------------
# DEVICE=eth0,10Mbit,1Mbit
# RATE=128Kbit
# WEIGHT=10Kbit
# PRIO=5
# RULE=192.168.1.1,
# --------------------------------------------------------------------------
#
# Pay attention to comma "," in the RULE field - it denotes source address!
#
# Enjoy.
```
When I know more, I'll post it here.

---

