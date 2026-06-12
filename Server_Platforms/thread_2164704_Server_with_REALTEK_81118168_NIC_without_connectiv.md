---
title: "Server with REALTEK 8111/8168 NIC without connectivity"
date: 2013-08-01
forum: Server Platforms
---

### Post by Max_Beikirch on 2013-08-01
Hello,

I am having trouble setting up a home server with the Realtek 8111/8168 (rev 06) on-board ethernet adapter.

In the home server, there are two HDDs running as a RAID 1, an AMD Phenom II X4 945 and a Geforce 8400.

For the mainboard I am using Gigabyte GA-970A-UD3. I bought all of those components one week ago, so the firmwares should be up to date.

Unfortunately, the network does not work. Independent from whether I use a static or a dhcp configuration, I cannot ping anyone from the local network except myself (i.e. 127.0.0.1 and 192.168.178.34, which is the IP that I use with the static configuration). Resolving addresses and accessing the internet dont not work either.
In addition, using the dhcp configuration, the `sudo ifup p9p1` just hangs up.

I read about similar problems where it was suggested installing the r8168-driver instead of the r8169. Although I already did this, the problem persists.

For the OS Ubuntu Server 13.04 is used. As there is no internet-access, it is obviously not updated.

Strangely enough, when I using a 12.04-livedisk, the access is there without any problems.

I am quite desperate now as I spent so much time on this and still can't seem to get it to work - so I am happy for help ;)

Attached you can find the output of some commands.

---

### Post by Max_Beikirch on 2013-08-01
Comparing the output from ethtool for the 12.04 (working) and 13.04 (not working) configuration, I noticed the following differences:

Whereas the working configuration lists [ TP MII ] as supported ports, 13.04 only lists [ TP ]. Accordingly, 12.04 says 'MII' for 'Port:', whereas 13.04 says 'Twisted Pair'. In the output for the not working configuration, it says 'MDI-X: unknown'. This line is missing in the output for 12.04.

I seriously don't know what that means, but it might contribute to the solution.

---

