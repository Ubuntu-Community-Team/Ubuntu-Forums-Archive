---
title: "Ubuntu Server 12.04 LTS DHCP Issue"
date: 2012-10-14
forum: Server Platforms
---

### Post by pegruder on 2012-10-14
So I've searched and searched, and can't figure out for the life of me why something I've setup in the past is giving me such a hard time.  So I just loaded up 12.04 Server x64, and am setting up my DHCP and DNS servers.  DNS worked ok, however, Im having a heck of a time on DHCP.  I've followed the help guides here as well as multiple sites, and just cant seem to get it.  Whats really irking me is it worked before I powered down to move the server.  When I start the server, it reports that the server has started, however it must crash immediately, as it does not show up as a process.  When I run sudo netstat -uap, there is no dhcpd there either.  I've never had such a hard time before with something that should be relatively simple.  The only difference from the last time I setup a dhcp server on ubuntu, is that it was version 3 instead of the now current version 4.  I've tried reinstalling and deleting and recreating the configs as well.  Im at a total loss.  Any help is much appreciated!

---

### Post by Doug S on 2012-10-14
While I have been using 12.04 server edition since early testing days, I only just two days ago migrated my main server (router, firewall, web server, fileserver, internal DNS, DHCP server) to 12.04. As per the [12.04 server guide]("https://help.ubuntu.com/12.04/serverguide/dhcp.html") , I used```
sudo apt-get install isc-dhcp-server
```I am using my old dhcpd.conf file, without any new edits and (as far as I know, so far) everything is fine. Is that the dhcp server you installed?
 
Is there any information in /var/log that might give any insight into your issues?

---

### Post by pegruder on 2012-10-14
That would be the one.  Oddly enough right before I went to bed last night, I put my old config in and it randomly started to work....  Strange even with a basic config or no config that it wouldnt start at all.  Then again well see if it continues to work..

---

### Post by Doug S on 2012-10-14
I suspect you will find that it works O.K. now.
It doesn't work with the default /etc/dhcp/dhcpd.conf file, as it needs to be edited for your specifics first. Myself, I don't think I would want the dhcp server to run unless I had specifically configured it. On my test 12.04 server, I restored the original dhcpd.conf and, upon re-boot, observed this in /var/log/kern.log:```
... Doug edited in this note: loop repeats about 20 times, ending with...
Oct 14 14:25:26 s15 kernel: [   30.899113] init: isc-dhcp-server main process ended, respawning
Oct 14 14:25:26 s15 kernel: [   31.048638] init: isc-dhcp-server main process (2250) terminated with status 1
Oct 14 14:25:26 s15 kernel: [   31.048654] init: isc-dhcp-server main process ended, respawning
Oct 14 14:25:27 s15 kernel: [   31.248056] init: isc-dhcp-server main process (2259) terminated with status 1
Oct 14 14:25:27 s15 kernel: [   31.248071] init: isc-dhcp-server respawning too fast, stopped

```

---

