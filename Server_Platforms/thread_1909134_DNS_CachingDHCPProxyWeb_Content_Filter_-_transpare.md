---
title: "DNS Caching/DHCP/Proxy/Web Content Filter - transparent, BASIC and NTLM capable"
date: 2012-01-14
forum: Server Platforms
---

### Post by jaimerosario on 2012-01-14
Hello every one.

Please, read this completely before running the program.

I've been working in this script for a long time. Done many changes. Now the script has been divided and added other features and configurations.

First, this series of scripts do the following:

1. 'apt-get update' and 'apt-get dselect-upgrade'
2. Installs bridging and vlans packages for those who configure servers with encapsulation.
3. Installs BIND as a DNS Caching server with OpenDNS Family Shield forwards.
4. Installs DHCP3-Server and automatically configures from eth1 to eth4 if the are available.
5. Installs and configures Squid3 proxy server as Transparent server, but the configuration included provide Basic and NTLM authentication. Also, I added some ACL that allows Windows Updates, and access to antivirus sites and added some Java workarounds.
6. Installs Dansguardian Web Content filter with 6 Filter Groups, but only 4 are enabled. Plus, I added a customized expression url dictionary with English/Spanish words and expressions. This dictionary allows safe access to normally blocked words like 'butter', which is often blocked by Dansguardian because of the first 4 words. Also added MIME Types for Live Messenger, Yahoo Messenger, and Torrents to allow more control instead of TCP/UDP Port blocking only. All site and url lists uses URLBigBlacklist and both lists are organized by categories, so you can enable or disable access to sites following the categories and not looking up and down in the lists.
7. It includes automatic updates for URLBlacklists and other AntiMalware lists that are online.
8. It installs Webmin with Dansguardian webmin plugin.

WHAT IT DOESN'T DO (But I would like):
1. Configures network interfaces - At this moment, you have to do it BEFORE running the script. Otherwise, the script may fail or simply install packages but DHCP and Dansguardian would have unexpected results.
2. Configures DNS Domain - Not in this script. Too much work.
3. Configures NAT/IPTables - Try Firewall Builder...
4. Makes you coffee.

There are a lot of things this scripts does not do, but I reminding you, this is a WORK-IN-PROGRESS.

BENEFITS:
1. If you want a quick-dirty Web Content Filter, this is for you. What could take hours and days, in less than 45 minutes, you have a up and running Proxy/DHCP/Content Filter server with Filter Groups.
2. If you need to automatically block PORN and MALWARE combining Dansguardian and OpenDNS, this is what you need.
3. If you need a content filtering server without blocking most legitimate and safe content, then consider testing it.

------------------------------------

How to run?

1. Install it in Ubuntu 10.04 LTS (x86 or x64). I Tried already with 11.10 but there are still things to tweak, and I prefer to wait for 12.04 LTS.
2. After install 10.04, configure the eth0 as your "Outside" or "Internet" network interface. Then, configure eth1 to eth4 as "Local" or "Internal" network adapters. At this time, is the way ot works.
3. Create a folder and copy the file, uncompress it and run 'proxy-install.sh'. When all processes finish, it will reboot automatically.

-------------------------------------

Any comment, recomendation, worries, kudos, etc., will be received well. I hope that this will help a lot of people who, like me, had long nights figuring out things when answers were not found at the time.

---

### Post by krishanthan on 2012-01-18
Dear Friends,

Thanks for all reply and updated scripts also,i am attach a image with  this massage, that image contain my Internet cafe network plan, so i  want can any one change script for my network plan and IP ranges. That  mean my Internet connection IP range 192.168.2.1 this IP range connect  with Proxy server after proxy server will release the Internet to  clients 192.168.3.x range with squid transparent proxy. Because i don't  know Ubuntu IP routing or network interfaces and apply NAT rules, or you  can use Firewall Builder to active NAT with iptables. this script  contain every think also i want it and  So please this time also help  me.

---

### Post by krishanthan on 2012-01-20
Dear Friends,

I was try to install this script but still installing, how long time is take for full install.

Thanks

---

### Post by jaimerosario on 2012-01-31
If you don't see any output, the script went in a loop. You must first configure the eth0 as the internet gateway. Then, check with 'dig' if you can resolve 'google.com' or 'yahoo.com'.

---

### Post by marcelorider on 2012-06-05
There is something that i still don't understand, does it do all the work to have a server out of the box? I mean a transparent proxy server ;)

Thanks ;)

---

### Post by marcelorider on 2012-06-06
BTW, will you release the script for the 12.04LTS?
I'm having so much trubble with the config of these utils =/

---

### Post by jaimerosario on 2012-07-27
10.04 works great... 12.04 still have some issues with Squid3 configuration... but I'm on it.

---

