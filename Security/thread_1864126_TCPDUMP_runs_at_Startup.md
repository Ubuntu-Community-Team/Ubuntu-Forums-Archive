---
title: "TCPDUMP runs at Startup"
date: 2011-10-18
forum: Security
---

### Post by SparTacux on 2011-10-18
I've recently installed a couple of system monitor  panel apps to monitor my network and hard drives ( neat little apps  too  :-) )  and I noticed some writing to my hard drive when I first logged in. It turned out I'd clicked on the broadcast accounts and a **** load of traffic was writing back to loopback port 127.0.0.1 . There's nothing like more security apps to give one a dose of paranoia ;-)

Before I realised my mistake I did some digging around in my log files and noticed references to TCPDUMP being loaded on startup. I haven't a clue why TCPDUMP should be running ( if it was indeed running ) . Here's a sample of my messages file:

Oct 18 17:55:16 UngaBonga kernel: [   12.778374] Console: switching to colour frame buffer device 80x30
Oct 18 17:55:16 UngaBonga kernel: [   12.796053] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 18 17:55:16 UngaBonga kernel: [   12.991492] nf_conntrack version 0.5.0 (6945 buckets, 27780 max)
Oct 18 17:55:16 UngaBonga kernel: [   12.993856] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Oct 18 17:55:16 UngaBonga kernel: [   12.993863] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Oct 18 17:55:16 UngaBonga kernel: [   12.993866] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Oct 18 17:55:16 UngaBonga kernel: [   14.163448] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Oct 18 17:55:16 UngaBonga kernel: [   14.163456] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Oct 18 17:55:16 UngaBonga kernel: [   14.163480] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Oct 18 17:55:16 UngaBonga kernel: [   14.284553] ip6_tables: (C) 2000-2006 Netfilter Core Team
Oct 18 17:55:17 UngaBonga kernel: [   27.797160] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Oct 18 17:55:17 UngaBonga kernel: [   28.033256] type=1505 audit(1318956917.235:8):  operation="profile_load" pid=885 name="/usr/share/gdm/guest-session/Xsession"
Oct 18 17:55:17 UngaBonga kernel: [   28.037883] type=1505 audit(1318956917.239:9):  operation="profile_replace" pid=887 name="/sbin/dhclient3"
Oct 18 17:55:17 UngaBonga kernel: [   28.038278] type=1505 audit(1318956917.239:10):  operation="profile_replace" pid=887 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 18 17:55:17 UngaBonga kernel: [   28.038513] type=1505 audit(1318956917.239:11):  operation="profile_replace" pid=887 name="/usr/lib/connman/scripts/dhclient-script"
Oct 18 17:55:17 UngaBonga kernel: [   28.160549] type=1505 audit(1318956917.363:12):  operation="profile_load" pid=888 name="/usr/bin/evince"
Oct 18 17:55:17 UngaBonga kernel: [   28.166493] type=1505 audit(1318956917.367:13):  operation="profile_load" pid=888 name="/usr/bin/evince-previewer"
Oct 18 17:55:17 UngaBonga kernel: [   28.170123] type=1505 audit(1318956917.371:14):  operation="profile_load" pid=888 name="/usr/bin/evince-thumbnailer"
Oct 18 17:55:17 UngaBonga kernel: [   28.218929] type=1505 audit(1318956917.419:15):  operation="profile_load" pid=890 name="/usr/lib/cups/backend/cups-pdf"
Oct 18 17:55:17 UngaBonga kernel: [   28.219413] type=1505 audit(1318956917.419:16):  operation="profile_load" pid=890 name="/usr/sbin/cupsd"
Oct 18 17:55:17 UngaBonga kernel: [   28.244200] type=1505 audit(1318956917.447:17):  operation="profile_load" pid=891 name="/usr/sbin/tcpdump"
Oct 18 17:55:18 UngaBonga kernel: [   28.872577] [drm] Initialized drm 1.1.0 20060810
Oct 18 17:55:18 UngaBonga kernel: [   28.986492] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 18 17:55:18 UngaBonga kernel: [   28.987739] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
Oct 18 17:55:18 UngaBonga kernel: [   28.990465] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Oct 18 17:55:18 UngaBonga kernel: [   28.990492] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x

I checked quite a few of my old messages logs and TCPDUMP always seems to run along with cupsd. Is this normal? Does it have something to do with using CUPS? or is a nasty little program capturing my network traffic without my consent?

---

### Post by Dangertux on 2011-10-18
I would wager that a nasty little program is capturing traffic with your consent. What were those new security monitoring apps you installed? If you installed an IDS of any kind there is a good chance that it is running tcpdump for you.

---

### Post by SparTacux on 2011-10-18
> **Dangertux said:**
> I would wager that a nasty little program is capturing traffic with your consent. What were those new security monitoring apps you installed? If you installed an IDS of any kind there is a good chance that it is running tcpdump for you.


I hope you aren't being serious.

I added the system monitor panel apps by right clicking on the panel and selecting add to panel. I then added the system monitor panel apps and configured them to observe the network and hard drive. I put them on a couple of days ago. I think I'll go and check some older message logs and see if the tcpdump is being loaded before I installed the panel apps.

---

### Post by Dangertux on 2011-10-18
> **SparTacux said:**
> I hope you aren't being serious.

I added the system monitor panel apps by right clicking on the panel and selecting add to panel. I then added the system monitor panel apps and configured them to observe the network and hard drive. I put them on a couple of days ago. I think I'll go and check some older message logs and see if the tcpdump is being loaded before I installed the panel apps.

I was being serious, however I was being serious after misreading your post. I read that you installed some "security apps" not that you installed system monitor apps.

To answer your other question though, no tcpdump does NOT start by default with cups why would it?

---

### Post by SparTacux on 2011-10-18
ok - I dug out an older messages log file dating back to Sept 21st and it had references to tcpdump being loaded. this is well before I put the panel apps on. 

I don't have any software installed to monitor my traffic other than wireshark which I installed a couple of days ago. I can't think of anything that I may have done to cause tcpdump to load.

---

### Post by Dangertux on 2011-10-18
> **SparTacux said:**
> ok - I dug out an older messages log file dating back to Sept 21st and it had references to tcpdump being loaded. this is well before I put the panel apps on. 

I don't have any software installed to monitor my traffic other than wireshark which I installed a couple of days ago. I can't think of anything that I may have done to cause tcpdump to load.

Ok well forget about the apps for a second because they are probably an irrelevancy. 

If you want to figure out what is loading tcpdump you can do the following

Check /etc/init for tcpdump upstart job

```

ls -al /etc/init | grep tcpdump

```and here

```

ls -al /etc/init.d | grep tcpdump

```Check cron

```

sudo crontab -e

```Check /etc/rc.local

```

sudo cat /etc/rc.local

```

You may also want to check your network interface up and down scripts to see if you daemonized tcpdump there.

Or alternatively uninstall tcpdump and see what breaks

```

sudo apt-get remove tcpdump

```

Hope that helps.

---

### Post by emiller12345 on 2011-10-18
I think what your seeing is Apparmor profiles being loaded, not actual programs running.  Run this ...
```
ls /etc/apparmor.d/
```
.. and see if the same programs are the ones you listed above.

---

### Post by Dangertux on 2011-10-18
> **emiller12345 said:**
> I think what your seeing is Apparmor profiles being loaded, not actual programs running.  Run this ...
```
ls /etc/apparmor.d/
```.. and see if the same programs are the ones you listed above.

Very good catch, I'm going to agree with you on this one. I'm almost positive that is correct.

---

### Post by emiller12345 on 2011-10-18
> **Dangertux said:**
> Very good catch, I'm going to agree with you on this one. I'm almost positive that is correct.
I've had my share of AA fears also.  \"someone's DoS'ing me!! Oh wait, I made a change to AA and forgot about it... Doh\" Looking for those audit lines is the first thing i go to now when something isn't working quite right.

You can also run...
```
sudo aa-status
```
... to list all of the apparmor profiles that are loaded.

---

### Post by SparTacux on 2011-10-19
> **emiller12345 said:**
> I've had my share of AA fears also.  \"someone's DoS'ing me!! Oh wait, I made a change to AA and forgot about it... Doh\" Looking for those audit lines is the first thing i go to now when something isn't working quite right.

You can also run...
```
sudo aa-status
```... to list all of the apparmor profiles that are loaded.

Yoooooooooo !

You hit the nail on the head my dear fellow - nice one :-)

The output of that little command line was:

apparmor module is loaded.
10 profiles are loaded.
10 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession

Those are the same entries in the messages log. 

I had my doubts about tcpdump running as it didn't show up in the list of running processes on system monitor or using top.

Thanks guys - saved me another reinstall ;-)

---

