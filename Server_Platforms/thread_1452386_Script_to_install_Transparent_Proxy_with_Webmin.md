---
title: "Script to install Transparent Proxy with Webmin"
date: 2010-04-11
forum: Server Platforms
---

### Post by jaimerosario on 2010-04-11
Hi everyone. I just made a script to install a Transparent Proxy with DHCP Server, Content Filtering and Webmin.

It installs and configures the modules and starts them. I can use from two to five interfaces (eth0, eth1, eth2, eth3 & eth4). I've tested in 8.04 to 9.10 and works fine.

It does not configures BIND and IPTABLES, just install all the modules needed for a transparent proxy, and configures DHCP, SQUID, DANSGUARDIAN and WEBMIN for Ubuntu.

I did it because mostly all configurations I do are transparent proxies.

What does:
1. Installs many packages needed for transparent proxies, and webmin. Also installs perl modules needed.
2. Configures default Squid settings for transparent proxies, and a better Dansguardian content filtering for public access.
3. Configures and fixes Webmin DHCP and Dansguardian modules to work on Ubuntu.
4. Configures DHCP Server subnets.

What doesn't:
1. IPTABLES and BIND. You must configure both manually. IPTABLES can be configured with Firewall Builder or other firewall tool. BIND can be configured using Webmin or the CLI.
2. Configures /etc/network/interfaces. You must configure all network interfaces correctly. Any mistake can screw the automatic configuration.
3. Dansguardian Blacklists. You must use your prefered blacklists. I use URLBigBlacklist with a modified script to work on Ubuntu (downloaded from Danguardians' Extras and fixed up to work on Ubuntu).
4. Check the script if there's something missing.

Any suggestions or additions are welcomed... If you modify it, please let me know because I want to know what other things I can do with it...

The good thing is that I don't have to be in front of the Server typing commands, just watch if something goes wrong.

---

### Post by jaimerosario on 2010-04-11
I forgot...

It does configures Dansguardian IP Filtering Groups, using 4 groups, the first three filtering groups are filtered, and the fourth group is unrestricted (for IP's that need to bypass the content filter).

In Dansguardian configuration, there is some changes like enable Safe Search in Google and other Search engines.

There is more stuff it does, but essentially, it just configures a transparent proxy server.

---

