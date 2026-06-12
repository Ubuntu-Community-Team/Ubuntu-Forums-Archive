---
title: "Weird download behavior with wget on Ubuntu Server ?"
date: 2017-06-09
forum: Server Platforms
---

### Post by soamz on 2017-06-09
I have just installed a Ubuntu Server and its connected with CAT6 Cable to my 10G Huawei S5700 switch at the datacenter. 
I have 300Mbps traffic lying unused. 

I just connected a PC to the same switch with one IP in same subnet and downloaded a 1G test file from digital ocean using IDM APPLICATION, Im getting 150-200Mbps download speed. 

but when I download the same file in Ubuntu server command line using wget, I hardly get 3-4Mbps. 

What could be the reason ?

---

### Post by LHammonds on 2017-06-14
That sounds strange.  I run Ubuntu Server in virtual systems using ESXi and have not seen such a drastic downgrade in bandwidth.

Not sure where to being troubleshooting such a problem since I have not seen that before.  Try a different cable or slot in the switch.  Maybe check your DNS server entries and other settings in /etc/network/interfaces, ping various locations for basic tests such as accessibility and latency, trace route to the destination, try wget to various other sites than just the one.  Check dmesg logs to see if there are any odd errors.  Make sure there are not duplexing issues such as one side thinking it is full duplex, the other 1/2 duplex.  Also make sure your server isn't already soaking up bandwidth with background tasks...check the switch to see how much data is passing through when not issuing the wget command or install and use iftop.  Can also install and use iperf to test bandwidth.   In one case, a network cable was lying on top of a florescent light which caused all kinds of havoc to the data trying to be passed through it but not likely going to be your problem. ;)

Sorry I don't have a genius answer.

LHammonds

---

### Post by soamz on 2017-06-14
perf shows perfectly fine, 981-990Mbps every time I test

---

### Post by Hugo_Serrano on 2017-06-20
Hello!

Do some downloads from another server connected to the same switch and vlan.
Check firewall/router for some rules on server IP. You may be using an old assigned IP with some QoS.
Try to download from other locations.

Cheers,
Hugo.

---

### Post by 1clue on 2017-06-20
[LIST=1]
[*]Is this Ubuntu Server on bare metal or on a VM?
[*]Are you mixing units? 1000 mbps=125 MB/s. Different tools measure bandwidth using different units.
[*]What NIC are you using (brand/model/driver)
[*]What form or storage are the files coming from/going to?  SATA 1/2/3? SSD? USB stick? DVD?
[/LIST]

I've had an issue like this on a VM using the wrong network driver, and when using storage media with inferior transfer rates, and on media which had errors. Check bandwidth on each part of the data pipe individually.

---

