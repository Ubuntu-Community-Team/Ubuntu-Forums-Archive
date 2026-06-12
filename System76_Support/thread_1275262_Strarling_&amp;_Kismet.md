---
title: "Strarling &amp; Kismet"
date: 2009-09-25
forum: System76 Support
---

### Post by jimmie-watters on 2009-09-25
Hi,

I recently recieved my Starling netbook from System76. I have started loading some networking tools. I frequently use nmap and wireshark on Windows and commercial software for wireless surveys and anaylsis. I wanted to see what capabilities tools like Kismet have on the wireless side. I have followed the readme on Kismet's sites as well as other documentation i could find on links from the Ubuntu forms. I cannot start Kismet and receive the following:

FATAL: Unknown capture source type 'rtl8187b' in source 'rtl8187b,wlan0,InternalNIC'

I believe that from what i have read that the Starling is using the rtl8187b chipset for wireless but am uncertain on what string i am suppose to enter in the source= line in the kismet.conf file. Any help would be great as i have very limited Linux experience.

Thanks

Jim

---

### Post by thomasaaron on 2009-09-25
Yes, the Starling uses the rtl8187b.

I don't know much about kismet, but here's an example of the conf file that I found online...

```
# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=voyager

# Sources are defined as:
**# source=sourcetype,interface,name[,initialchannel]**
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,addme

# Comma-separated list of sources to enable. This is only needed if you defined
# multiple sources and only want to enable some of them. By default, all defined
# sources are enabled.
# For example:
# enablesources=ipw2200,eth1,eth1


# Do we channelhop?
channelhop=true

# How many channels per second do we hop? (1-10)
channelvelocity=5

# By setting the dwell time for channel hopping we override the channelvelocity
# setting above and dwell on each channel for the given number of seconds.
#channeldwell=10
```

You're going to want to put it near the bolded line. And you will want it to be uncommented (#).

---

### Post by jimmie-watters on 2009-09-25
Thanks for your response Thomas. I discovered the problem i was having. I was using the wrong name for the chipset. Once I replaced rtl8187b with rt8187 kismet ran as expected.

source=rt8187,wlan0,wlan0

Jim

---

