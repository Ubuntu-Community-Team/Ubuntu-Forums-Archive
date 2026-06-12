---
title: "How can I find the connecting process and disable it?"
date: 2010-11-06
forum: Security
---

### Post by KonfuseKitty on 2010-11-06
I notice in my logs that on startup and wakeup my computer is connecting to the Canonical servers even though I'm opted out of surveys and auto update checks are disabled.


How can I determine which process is connecting, and once I find it, how do I disable it? I don't want to screw up my ability to manually update my system, so I don't think I can use denyhosts.

---

### Post by CharlesA on 2010-11-06
What log are you looking at?

---

### Post by Rubi1200 on 2010-11-06
Are you using Ubuntu One?

Processes:

```
sudo netstat -tulnp
```

or 

```
sudo lsof -i -n -P
```

---

### Post by KonfuseKitty on 2010-11-07
I don't use Ubuntu One, and the log I'm looking at is messages, listing the startup/wakeup sequence and then the ufw allow/audit lines listing connections.


From "sudo lsof -i -n -P" I get:


```
COMMAND   PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
cupsd    1275    root    5u  IPv6  11988      0t0  TCP [::1]:631 (LISTEN)
cupsd    1275    root    6u  IPv4  11989      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient 1639    root    5u  IPv4  10532      0t0  UDP *:68 
privoxy  1913 privoxy    5u  IPv4  12083      0t0  TCP 127.0.0.1:8118 (LISTEN)

```


From "sudo netstat -tulnp":


```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      1913/privoxy    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1275/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1275/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1639/dhclient

```


These look like lists of listening processes only, plus dhclient. But the connection is outgoing. The process must be lauching on startup and wakeup. At one point I knew where these things were set, but I've lost my reference. If indeed, the startup config file is where I should be looking.

---

### Post by CharlesA on 2010-11-07
dhclient is what's used to grab an IP from a DHCP server and that's the only one that's listening on an external interface. cups and privoxy are listening on the lo interface.

---

### Post by OpSecShellshock on 2010-11-07
Can you post the lines from the log files that reference the server you're concerned about?

---

### Post by KonfuseKitty on 2010-11-07
Here are the lines from message log just after a restart. I'm quoting a fairly lengthy section for completeness, from the network being up, to the end of startup. The relevant ufw lines containing the Canonical IP 91.189.94.4 are at the end:


```
Nov  7 16:07:50 kkitty-desktop kernel: [   14.441370] r8169: eth1: link up
Nov  7 16:07:50 kkitty-desktop kernel: [   14.441376] r8169: eth1: link up
Nov  7 16:07:50 kkitty-desktop kernel: [   14.446440] type=1505 audit(1289142470.645:5):  operation="profile_load" pid=1127 name="/bin/ping"
Nov  7 16:07:50 kkitty-desktop kernel: [   14.447705] type=1505 audit(1289142470.645:6):  operation="profile_load" pid=1128 name="/usr/share/gdm/guest-session/Xsession"
Nov  7 16:07:50 kkitty-desktop kernel: [   14.448720] type=1505 audit(1289142470.645:7):  operation="profile_replace" pid=1129 name="/sbin/dhclient3"
Nov  7 16:07:50 kkitty-desktop kernel: [   14.448935] type=1505 audit(1289142470.645:8):  operation="profile_replace" pid=1129 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Nov  7 16:07:50 kkitty-desktop kernel: [   14.449056] type=1505 audit(1289142470.645:9):  operation="profile_replace" pid=1129 name="/usr/lib/connman/scripts/dhclient-script"
Nov  7 16:07:50 kkitty-desktop kernel: [   14.449963] type=1505 audit(1289142470.645:10):  operation="profile_load" pid=1130 name="/sbin/klogd"
Nov  7 16:07:50 kkitty-desktop kernel: [   14.450877] type=1505 audit(1289142470.645:11):  operation="profile_load" pid=1131 name="/sbin/syslog-ng"
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676193] ------------[ cut here ]------------
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676201] WARNING: at /build/buildd/linux-2.6.32/mm/page_alloc.c:1806 __alloc_pages_slowpath+0x43b/0x580()
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676203] Hardware name: System Product Name
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676205] Modules linked in: snd_hda_codec_atihdmi snd_hda_codec_via ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype xt_state ip6table_filter snd_hda_intel snd_pcm_oss ip6_tables snd_hda_codec snd_mixer_oss snd_hwdep nf_nat_irc snd_pcm nf_conntrack_irc snd_seq_dummy nf_nat_ftp nf_nat snd_seq_oss nf_conntrack_ipv4 snd_seq_midi nf_defrag_ipv4 snd_rawmidi joydev nf_conntrack_ftp snd_seq_midi_event nf_conntrack snd_seq iptable_filter ppdev snd_timer ip_tables snd_seq_device x_tables fbcon tileblit font bitblit softcursor parport_pc asus_atk0110 wacom fglrx(P) vga16fb vgastate psmouse snd serio_raw edac_core edac_mce_amd soundcore snd_page_alloc i2c_piix4 shpchp lp parport usbhid hid ohci1394 pata_atiixp r8169 ieee1394 mii ahci
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676241] Pid: 1170, comm: Xorg Tainted: P           2.6.32-25-generic #45-Ubuntu
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676243] Call Trace:
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676248]  [<ffffffff81065efb>] warn_slowpath_common+0x7b/0xc0
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676251]  [<ffffffff81065f54>] warn_slowpath_null+0x14/0x20
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676254]  [<ffffffff810f9eab>] __alloc_pages_slowpath+0x43b/0x580
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676295]  [<ffffffffa013d742>] ? firegl_trace+0x72/0x1e0 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676298]  [<ffffffff810fa14e>] __alloc_pages_nodemask+0x15e/0x1a0
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676303]  [<ffffffff8112cfc7>] alloc_pages_current+0x87/0xd0
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676305]  [<ffffffff810f905e>] __get_free_pages+0xe/0x50
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676331]  [<ffffffffa010f3d5>] KCL_MEM_AllocContiguousPageFrames+0x15/0x20 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676359]  [<ffffffffa01165e3>] drm_alloc_pages+0xb3/0x230 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676390]  [<ffffffffa012a71a>] ? MCIL_AllocateContiguousMemory+0x3a/0xe0 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676432]  [<ffffffffa01b4028>] ? _ZN7GpsBase28GPS_AllocateContiguousMemoryEPvmjP15_ULARGE_INTEGERmmm+0x98/0xd0 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676472]  [<ffffffffa01c30b6>] ? _ZN23PageTableGartVmptSysMem4InitEv+0x66/0x160 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676512]  [<ffffffffa01c0f42>] ? _ZN13GartVmptRS78015CreatePageTableEP9GpsConfig+0x52/0x200 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676553]  [<ffffffffa01b4fdd>] ? _ZN10GPSContext18InitializeAsicGartEv+0x3d/0xf0 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676593]  [<ffffffffa01b0a63>] ? Gps_GartInitialization+0x23/0x40 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676623]  [<ffffffffa01303db>] ? __gart_init+0x2eb/0x6f0 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676654]  [<ffffffffa012dda0>] ? gal_init+0xc0/0x160 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676683]  [<ffffffffa0133ba2>] ? mc_heap_init+0xe2/0x200 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676712]  [<ffffffffa0121fea>] ? firegl_init_pcie+0x16a/0x3e0 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676715]  [<ffffffff810f5dce>] ? generic_file_aio_write+0xbe/0xe0
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676719]  [<ffffffff81251d9a>] ? security_capable+0x2a/0x30
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676746]  [<ffffffffa0121e80>] ? firegl_init_pcie+0x0/0x3e0 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676774]  [<ffffffffa011db5a>] ? firegl_ioctl+0x1ea/0x250 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676800]  [<ffffffffa01138d6>] ? ip_firegl_ioctl+0x16/0x20 [fglrx]
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676804]  [<ffffffff811531ac>] ? vfs_ioctl+0x7c/0xa0
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676806]  [<ffffffff81153401>] ? do_vfs_ioctl+0x81/0x380
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676809]  [<ffffffff81143122>] ? vfs_write+0x132/0x1a0
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676811]  [<ffffffff81153781>] ? sys_ioctl+0x81/0xa0
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676814]  [<ffffffff810121b2>] ? system_call_fastpath+0x16/0x1b
Nov  7 16:07:50 kkitty-desktop kernel: [   14.676816] ---[ end trace 1b6b497c322125a7 ]---
Nov  7 16:07:50 kkitty-desktop kernel: [   14.693333] [fglrx] Firegl kernel thread PID: 1238
Nov  7 16:07:50 kkitty-desktop kernel: [   14.693705] [fglrx] IRQ 27 Enabled
Nov  7 16:07:51 kkitty-desktop kernel: [   14.985959] [fglrx] Gart USWC size:1279 M.
Nov  7 16:07:51 kkitty-desktop kernel: [   14.985962] [fglrx] Gart cacheable size:508 M.
Nov  7 16:07:51 kkitty-desktop kernel: [   14.985966] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Nov  7 16:07:51 kkitty-desktop kernel: [   14.985968] [fglrx] Reserved FB block: Unshared offset:7bfa000, size:401000 
Nov  7 16:07:51 kkitty-desktop kernel: [   14.985970] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000 
Nov  7 16:07:53 kkitty-desktop kernel: [   17.666209] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=46076 DF PROTO=TCP SPT=36126 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0 
Nov  7 16:07:53 kkitty-desktop kernel: [   17.666226] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=46076 DF PROTO=TCP SPT=36126 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0 
Nov  7 16:07:55 kkitty-desktop kernel: [   18.842045] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  7 16:08:03 kkitty-desktop kernel: [   27.187646] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=37274 DF PROTO=TCP SPT=36128 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0 
Nov  7 16:08:03 kkitty-desktop kernel: [   27.187664] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=37274 DF PROTO=TCP SPT=36128 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0 
Nov  7 16:08:03 kkitty-desktop kernel: [   27.249839] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=3035 DF PROTO=TCP SPT=36130 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0 
Nov  7 16:08:03 kkitty-desktop kernel: [   27.249856] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=3035 DF PROTO=TCP SPT=36130 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0 
Nov  7 16:08:04 kkitty-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Nov  7 16:08:04 kkitty-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Nov  7 16:08:08 kkitty-desktop kernel: [   31.924535] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.1.34 DST=192.168.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38728 DF PROTO=UDP SPT=37385 DPT=53 LEN=40 
Nov  7 16:08:08 kkitty-desktop kernel: [   31.924545] [UFW ALLOW] IN= OUT=eth1 SRC=192.168.1.34 DST=192.168.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38728 DF PROTO=UDP SPT=37385 DPT=53 LEN=40 
Nov  7 16:08:08 kkitty-desktop kernel: [   31.968256] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.1.34 DST=192.168.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38732 DF PROTO=UDP SPT=54986 DPT=53 LEN=40 
Nov  7 16:08:08 kkitty-desktop kernel: [   31.968264] [UFW ALLOW] IN= OUT=eth1 SRC=192.168.1.34 DST=192.168.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38732 DF PROTO=UDP SPT=54986 DPT=53 LEN=40 
Nov  7 16:08:08 kkitty-desktop kernel: [   32.003130] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.1.34 DST=192.168.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38736 DF PROTO=UDP SPT=49503 DPT=53 LEN=40 
Nov  7 16:08:08 kkitty-desktop kernel: [   32.003137] [UFW ALLOW] IN= OUT=eth1 SRC=192.168.1.34 DST=192.168.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38736 DF PROTO=UDP SPT=49503 DPT=53 LEN=40 
Nov  7 16:08:08 kkitty-desktop kernel: [   32.129147] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.1.34 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Nov  7 16:08:08 kkitty-desktop kernel: [   32.129156] [UFW ALLOW] IN= OUT=eth1 SRC=192.168.1.34 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Nov  7 16:08:11 kkitty-desktop pulseaudio[1620]: ratelimit.c: 7 events suppressed

```

---

### Post by CharlesA on 2010-11-07
That address hosts a NTP server, it's probably just syncing up the clock. If you want to confirm look at the network traffic.

According to the log, it's sending packets to destination port 123, which is NTP.

See here: [http://www.robtex.com/ip/91.189.94.4.html](http://www.robtex.com/ip/91.189.94.4.html)

---

### Post by OpSecShellshock on 2010-11-07
Excellent, that's exactly what I was looking for. The first chunk of lines you'll notice are UDP traffic with a destination port of 53. Those are just DNS lookups in preparation for the final two lines. The final two, you can see that the destination port is 123, which means that these are NTP requests. NTP is just what keeps your system's clock synchronized. It's not gathering or reporting any information. Preventing it will cause your computer's clock to slowly but steadily drift away from what the actual time is, so disabling it would not be a good idea.

Main point is that this is all perfectly normal, and isn't related to any kind of system updates or machine information reporting or anything like that. It's just the clock.

---

### Post by KonfuseKitty on 2010-11-07
Oh, that's great, it's just the clock. I'm impressed by your investigative ability, guys, thanks. Let's take this just one step further - how do I disable it? I have my Time and Date configuration set to Manual, so it shouldn't be connecting. Is there another setting somewhere that I'm missing?


Never mind synching of the clock... I'm always late anyway! :-P

---

### Post by CharlesA on 2010-11-07
That's how you would normally disable the clock sync.

You could always uninstall the ntp service from synaptic.

---

### Post by KonfuseKitty on 2010-11-08
I would rather disable its automatic run at startup than uninstall it, so I can still run it manually from Terminal or bash script.


How do I disable it? I have found a script file - /etc/networkd/if-up.d/ntpdate, is this what gets the ntp active when networking is started? I can't make much sense of the script.

---

### Post by CharlesA on 2010-11-08
Check to see if it's listed under "start up applications"

---

### Post by KonfuseKitty on 2010-11-08
It isn't listed in "Startup Programs" (in System->Preferences->Startup Applications Preferences).

---

### Post by cariboo on 2010-11-08
Ntpdate, is the package you are looking for, the command is located in /etc/default, so it is run on startup. Removing the package should solve your problem.

---

### Post by OpSecShellshock on 2010-11-08
Go to System-->Administration-->Time & Date

Then click on the lock icon and put in your password. After that, go to the drop-down menu underneath where it has the time zone and select Manual. I don't know if that will actually make a difference since mine was already set that way and my system clock is fine, but I can't really think of anything else.

---

### Post by KonfuseKitty on 2010-11-09
As stated previously, I'm already set to Manual. I've now removed the ntpdate file from the /etc/default/ folder and on restart the connection indeed does not take place. Good, but now when trying to run "sudo ntpdate -q" in the Terminal, I get the response "9 Nov 09:32:39 ntpdate[1807]: no servers can be used, exiting".



Have I caused this by removing the file? I really just want to disable the automatic connections, but keep the ntp functionality for manual use. Why is this proving so difficult?

---

### Post by KonfuseKitty on 2010-11-09
Actually, I've moved the file back in the folder and get the same error in Terminal, so it doesn't seem related. It seems I have a separate issue with ntpdate.

---

### Post by SeijiSensei on 2010-11-09
What are the server entries in /etc/ntp.conf?

---

### Post by KonfuseKitty on 2010-11-09
The file (or folder) doesn't exist.


I do have usr/sbin/ntpdate and usr/sbin/ntpdate-debian, and the Ubuntu Software Center shows the ntpdate package as installed, but none of the others like ntp (ntpdate and ntp being two different packages apparently). Also, "man ntpdate" in Terminal brings up the manual page.


So I take it I have ntpdate installed for sure, and I haven't been deleting any of its files. I tend to leave the system alone, unless following instructions, as in this thread. So how come I'm missing ntp.conf?

---

### Post by SeijiSensei on 2010-11-09
Well, a bit further investigation shows that the ntpdate configuration is rather strange.  In /etc/default/ntpdate there's an entry for Ubuntu's NTP server, ntp.ubuntu.com.  However at the top of the configuration file it says this file is read only by "ntpdate-debian" and not by "ntpdate" itself.

If I run ntpdate-debian it connects with the Ubuntu server; running ntpdate by itself gives me the same "no servers can be reached" error you get.  If I use "ntpdate ntp.ubuntu.com" ntpdate does connect and gives me the same result as ntpdate-debian.

---

### Post by CharlesA on 2010-11-09
Only thing I can figure is that ntpdate is pulling the NTP server from somewhere else.

---

### Post by KonfuseKitty on 2010-11-09
Great! I've again removed ntpdate from etc/default to stop automatic connections, and running "sudo ntpdate ntp.ubuntu.com" in the Terminal connects and sets the time. Problem solved.


Many thanks to all the helpers! :-)

---

### Post by cariboo on 2010-11-09
> **KonfuseKitty said:**
> Great! I've again removed ntpdate from etc/default to stop automatic connections, and running "sudo ntpdate ntp.ubuntu.com" in the Terminal connects and sets the time. Problem solved.


Many thanks to all the helpers! :-)

Thats exactly what the ntpdate command in /etc/default does, so instead of automating it, you are doing it manually. :) I thought the idea of using computers was to let them do most of the work for you. :)

---

### Post by SeijiSensei on 2010-11-09
No, it actually runs "ntpdate-debian" not "ntpdate".  See [above](http://ubuntuforums.org/showpost.php?p=10095029&postcount=21).

---

