---
title: "Ubuntu 10.04LTS Server x64 losing connection every 1-2 days."
date: 2013-07-03
forum: Server Platforms
---

### Post by jwright8 on 2013-07-03
Hello everyone,

I'm hoping someone can help me on this as I am out of ideas.  

I have a Ubuntu server that, up until recently, worked just fine.  It started giving trouble of various kinds (sort of hard to pinpoint the problem), one of which was that it would lose connectivity to the outside world until I rebooted it.  I used both OpenVPN and ssh to try to connect to it to no avail.  

I swapped the tower out with a system that I had with pretty much identical hardware.  The PSU was whining a little, so I replaced it.  I also got a new battery backup and connected it to that, just in case.  I put two new PCI ethernet cards in it as well, as well as a new hard drive at the time of switch out.  I wanted to be certain that hardware wasn't an issue, and since I switched the units, I figured that cut out the possibility of CPU/MB/RAM.

Unfortunately, even after reformatting, updating it using apt-get, and reconfiguring everything (I only took the necessary .conf files for OpenVPN and the certificates/keys for it), it still gives a similar problem.  Frankly, I am out of ideas.  

After one or two days, it depends but typically happens overnight (as I'll try it at 7pm and it will work, then try it at 7 am and it won't).  I won't be able to connect to SSH or OpenVPN on the machine.  There's no monitor or keyboard hooked into it, so I just held the button down and forced it to reboot in the past.  Once the machine shut down and came back on, all the connections would be back open again... until it decided to disconnect in the night again.  Lately, I left a monitor/keyboard hooked up to it just to see what was going on with it.  This time when it stopped allowing connections, I went in and hit a button on the keyboard to wake the monitor up.  Naturally, since I really only login to it via ssh, it was at the initial login.  I logged into root and pinged the gateway it was behind and it worked, so I went back to my Windows computer and was able to connect to both ssh and OpenVPN.  

Once I had replaced all the hardware above, I thought I had fixed the problem.  Previously, it was literally every night that it was doing this.  It has been running since Monday afternoon without a problem, but this morning (Wednesday), it was the same problem.  Any help is much appreciated, as I don't know what else to do to it. 

 The following are some log excerpts:

Auth.log:
> 
Jul  2 14:09:16 Alatheia sshd[3044]: Accepted password for justin from XX.XXX.XXX.XXX port 63494 ssh2
Jul  2 14:09:16 Alatheia sshd[3044]: pam_unix(sshd:session): session opened for user justin by (uid=0)
Jul  2 14:09:20 Alatheia su[3130]: Successful su for root by justin
Jul  2 14:09:20 Alatheia su[3130]: + /dev/pts/0 justin:root
Jul  2 14:09:20 Alatheia su[3130]: pam_unix(su:session): session opened for user root by justin(uid=1000)
Jul  2 14:17:01 Alatheia CRON[3165]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 14:17:01 Alatheia CRON[3165]: pam_unix(cron:session): session closed for user root
Jul  2 15:17:01 Alatheia CRON[3239]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 15:17:01 Alatheia CRON[3239]: pam_unix(cron:session): session closed for user root
Jul  2 16:17:01 Alatheia CRON[3244]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 16:17:01 Alatheia CRON[3244]: pam_unix(cron:session): session closed for user root
Jul  2 17:01:01 Alatheia CRON[3248]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 17:17:01 Alatheia CRON[3321]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 17:17:01 Alatheia CRON[3321]: pam_unix(cron:session): session closed for user root
Jul  2 17:30:41 Alatheia sshd[3044]: pam_unix(sshd:session): session closed for user justin
Jul  2 17:30:41 Alatheia su[3130]: pam_unix(su:session): session closed for user root
Jul  2 18:17:01 Alatheia CRON[3326]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 18:17:01 Alatheia CRON[3326]: pam_unix(cron:session): session closed for user root
Jul  2 19:17:01 Alatheia CRON[3330]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 19:17:01 Alatheia CRON[3330]: pam_unix(cron:session): session closed for user root
Jul  2 20:17:01 Alatheia CRON[3334]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 20:17:01 Alatheia CRON[3334]: pam_unix(cron:session): session closed for user root
Jul  2 21:17:01 Alatheia CRON[3338]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 21:17:01 Alatheia CRON[3338]: pam_unix(cron:session): session closed for user root
Jul  2 22:17:01 Alatheia CRON[3342]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 22:17:01 Alatheia CRON[3342]: pam_unix(cron:session): session closed for user root
Jul  2 23:17:01 Alatheia CRON[3346]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  2 23:17:01 Alatheia CRON[3346]: pam_unix(cron:session): session closed for user root
Jul  3 00:17:01 Alatheia CRON[3350]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 00:17:01 Alatheia CRON[3350]: pam_unix(cron:session): session closed for user root
Jul  3 01:17:01 Alatheia CRON[3354]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 01:17:01 Alatheia CRON[3354]: pam_unix(cron:session): session closed for user root
Jul  3 02:17:01 Alatheia CRON[3358]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 02:17:01 Alatheia CRON[3358]: pam_unix(cron:session): session closed for user root
Jul  3 03:17:01 Alatheia CRON[3362]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 03:17:01 Alatheia CRON[3362]: pam_unix(cron:session): session closed for user root
Jul  3 04:17:01 Alatheia CRON[3366]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 04:17:01 Alatheia CRON[3366]: pam_unix(cron:session): session closed for user root
Jul  3 05:17:01 Alatheia CRON[3370]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 05:17:01 Alatheia CRON[3370]: pam_unix(cron:session): session closed for user root
Jul  3 06:17:01 Alatheia CRON[3374]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 06:17:01 Alatheia CRON[3374]: pam_unix(cron:session): session closed for user root
Jul  3 06:25:01 Alatheia CRON[3378]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 06:45:11 Alatheia CRON[3378]: pam_unix(cron:session): session closed for user root
Jul  3 07:17:01 Alatheia CRON[3492]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 07:17:01 Alatheia CRON[3492]: pam_unix(cron:session): session closed for user root
Jul  3 08:17:01 Alatheia CRON[3496]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 08:17:01 Alatheia CRON[3496]: pam_unix(cron:session): session closed for user root
Jul  3 09:17:01 Alatheia CRON[3500]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 09:17:01 Alatheia CRON[3500]: pam_unix(cron:session): session closed for user root
Jul  3 10:01:01 Alatheia CRON[3504]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 10:17:01 Alatheia CRON[3577]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  3 10:53:16 Alatheia login[916]: pam_unix(login:session): session opened for user root by LOGIN(uid=0)
Jul  3 10:53:16 Alatheia login[3646]: ROOT LOGIN  on '/dev/tty1'
Jul  3 11:00:31 Alatheia sshd[3704]: Accepted password for justin from XX.XXX.XXX.XXX port 64562 ssh2
Jul  3 11:00:31 Alatheia sshd[3704]: pam_unix(sshd:session): session opened for user justin by (uid=0)
Jul  3 11:13:12 Alatheia su[3787]: Successful su for root by justin
Jul  3 11:13:12 Alatheia su[3787]: + /dev/pts/0 justin:root
Jul  3 11:13:12 Alatheia su[3787]: pam_unix(su:session): session opened for user root by justin(uid=1000)


Syslog
> 
Jul  3 06:45:10 Alatheia rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="725" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul  3 07:17:01 Alatheia CRON[3494]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 08:17:01 Alatheia CRON[3498]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 09:17:01 Alatheia CRON[3502]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 10:01:01 Alatheia CRON[3506]: (root) CMD (/root/iptables_daytime.sh )
Jul  3 10:17:01 Alatheia CRON[3579]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


Syslog.1
> 
Jul  2 14:16:23 Alatheia crontab[3153]: (root) BEGIN EDIT (root)
Jul  2 14:17:01 Alatheia CRON[3166]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 14:19:05 Alatheia crontab[3153]: (root) REPLACE (root)
Jul  2 14:19:05 Alatheia crontab[3153]: (root) END EDIT (root)
Jul  2 14:19:06 Alatheia crontab[3169]: (root) BEGIN EDIT (root)
Jul  2 14:19:38 Alatheia crontab[3169]: (root) END EDIT (root)
Jul  2 14:20:01 Alatheia cron[837]: (root) RELOAD (crontabs/root)
Jul  2 15:17:01 Alatheia CRON[3241]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 16:17:01 Alatheia CRON[3246]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 17:01:01 Alatheia CRON[3250]: (root) CMD (/root/iptables.sh )
Jul  2 17:17:01 Alatheia CRON[3323]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 18:17:01 Alatheia CRON[3328]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 19:17:01 Alatheia CRON[3332]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 20:17:01 Alatheia CRON[3336]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 21:17:01 Alatheia CRON[3340]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 22:17:01 Alatheia CRON[3344]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 23:17:01 Alatheia CRON[3348]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 00:17:01 Alatheia CRON[3352]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 01:17:01 Alatheia CRON[3356]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 02:17:01 Alatheia CRON[3360]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 03:17:01 Alatheia CRON[3364]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 04:17:01 Alatheia CRON[3368]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 05:17:01 Alatheia CRON[3372]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 06:17:01 Alatheia CRON[3376]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 06:25:01 Alatheia CRON[3380]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))


The contents of root's crontab -e:

> 
# m h  dom mon dow   command
SHELL=/bin/bash
01 10 * * 1-5 /root/iptables_day.sh
# 10:01 am every weekday
01 17 * * 1-5 /root/iptables.sh
# 5:01 pm every weekday
01 09 * * 6-7 /root/iptables_day.sh
# 9:01 am to 12:01 pm every weekend day
01 12 * * 6-7 /root/iptables.sh
# 9:01 am to 12:01 pm every weekend day



There are no entries in openvpn.log past me starting it on July 1st.  Please let me know if you need me to post anything else.  Thanks!

---

### Post by DJ_Max on 2013-07-03
Explain your setup more. Are you using/running a DHCP server or is it static?

Install smokeping and monitor when exactly it drops. look in /etc/cron.d/ for any scripts which run at that time.

Look in around the time it drops.
/var/log/daemon.log
/var/log/kern.log
/var/log/messages
/var/log/syslog

---

### Post by jwright8 on 2013-07-03
The box is static IP'd, the setup is:

Client computers -> Switch -> Linux server eth3 -> Linux server eth2 -> Modem/router combo -> Internet

ifconfig (tap used by OpenVPN):
> 


br0       Link encap:Ethernet  HWaddr -----------------------
          inet addr:10.1.10.70  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: ----------------------- Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1254675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2332979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:161506585 (161.5 MB)  TX bytes:1261775937 (1.2 GB)


eth2      Link encap:Ethernet  HWaddr -----------------------
          inet6 addr: ----------------------- Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9069844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1218171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9105263068 (9.1 GB)  TX bytes:78997080 (78.9 MB)
          Interrupt:19 Base address:0x6000


eth3      Link encap:Ethernet  HWaddr -----------------------
          inet6 addr: ----------------------- Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1237594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2481403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:176844310 (176.8 MB)  TX bytes:1385073123 (1.3 GB)
          Interrupt:20 Base address:0xa000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22116 (22.1 KB)  TX bytes:22116 (22.1 KB)


tap0      Link encap:Ethernet  HWaddr -----------------------
          inet6 addr: ----------------------- Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:1175414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2277036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:73828065 (73.8 MB)  TX bytes:3085053180 (3.0 GB)




daemon.log:
> 


Jul  1 11:23:37 Alatheia ntpdate[1400]: name server cannot be used, reason: Temporary failure in name resolution
Jul  1 11:23:37 Alatheia init: ssh main process (1078) terminated with status 255
Jul  1 11:24:54 Alatheia init: apport pre-start process (795) terminated with status 1
Jul  1 11:24:54 Alatheia init: apport post-stop process (810) terminated with status 1
Jul  1 11:24:54 Alatheia init: Failed to spawn ufw pre-start process: unable to execute: No such file or directory
Jul  1 11:24:54 Alatheia init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory
Jul  1 11:24:55 Alatheia init: Failed to spawn ufw pre-start process: unable to execute: No such file or directory
Jul  1 11:24:55 Alatheia init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory
Jul  1 11:25:10 Alatheia ntpdate[999]: name server cannot be used, reason: Temporary failure in name resolution
Jul  1 11:25:10 Alatheia init: ssh main process (726) terminated with status 255
Jul  3 11:48:54 Alatheia init: apport pre-start process (804) terminated with status 1
Jul  3 11:48:54 Alatheia init: apport post-stop process (823) terminated with status 1
Jul  3 11:48:54 Alatheia init: Failed to spawn ufw pre-start process: unable to execute: No such file or directory
Jul  3 11:48:54 Alatheia init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory
Jul  3 11:48:55 Alatheia init: Failed to spawn ufw pre-start process: unable to execute: No such file or directory
Jul  3 11:48:55 Alatheia init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory
Jul  3 11:49:11 Alatheia init: ssh main process (538) terminated with status 255
Jul  3 11:49:11 Alatheia ntpdate[1028]: name server cannot be used, reason: Temporary failure in name resolution
Jul  3 12:40:10 Alatheia ntfs-3g[1991]: Version 2010.3.6 external FUSE 28
Jul  3 12:40:10 Alatheia ntfs-3g[1991]: Mounted /dev/sdb1 (Read-Write, label "Lexar", NTFS 3.1)
Jul  3 12:40:10 Alatheia ntfs-3g[1991]: Cmdline options: rw
Jul  3 12:40:10 Alatheia ntfs-3g[1991]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,bl$
Jul  3 12:40:10 Alatheia ntfs-3g[1991]: Ownership and permissions disabled, configuration type 1
Jul  3 12:43:44 Alatheia ntfs-3g[1991]: Unmounting /dev/sdb1 (Lexar)



Around the same time as the ssh termination in daemon.log, this is from kern.log:

> 
Jul  3 11:48:52 Alatheia kernel: [    5.870600] r8169: eth3: link up
Jul  3 11:48:52 Alatheia kernel: [    5.872939] device eth2 entered promiscuous mode
Jul  3 11:48:52 Alatheia kernel: [    5.874306] r8169: eth2: link up
Jul  3 11:48:52 Alatheia kernel: [    5.876358] br0: port 2(eth2) entering learning state
Jul  3 11:48:52 Alatheia kernel: [    5.876363] br0: port 1(eth3) entering learning state
Jul  3 11:48:52 Alatheia kernel: [    5.988006] vga16fb: initializing
Jul  3 11:48:52 Alatheia kernel: [    5.988014] vga16fb: mapped to 0xffff8800000a0000
Jul  3 11:48:52 Alatheia kernel: [    5.988021] vga16fb: not registering due to another framebuffer present
Jul  3 11:48:52 Alatheia kernel: [    6.165739] hda_codec: ALC888: BIOS auto-probing.
Jul  3 11:48:52 Alatheia kernel: [    6.167109] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4
Jul  3 11:48:52 Alatheia kernel: [    6.494644] Console: switching to colour frame buffer device 180x56
Jul  3 11:48:55 Alatheia kernel: [    9.594079] device tap0 entered promiscuous mode
Jul  3 11:48:55 Alatheia kernel: [    9.596283] br0: port 3(tap0) entering learning state
Jul  3 11:49:01 Alatheia kernel: [   15.960010] eth2: no IPv6 routers present
Jul  3 11:49:02 Alatheia kernel: [   16.360010] eth3: no IPv6 routers present
Jul  3 11:49:02 Alatheia kernel: [   16.470015] br0: no IPv6 routers present
Jul  3 11:49:06 Alatheia kernel: [   20.560017] tap0: no IPv6 routers present
Jul  3 11:49:06 Alatheia kernel: [   20.870011] br0: port 2(eth2) entering forwarding state
Jul  3 11:49:06 Alatheia kernel: [   20.870016] br0: port 1(eth3) entering forwarding state
Jul  3 11:49:10 Alatheia kernel: [   24.590017] br0: port 3(tap0) entering forwarding state
Jul  3 11:55:05 Alatheia kernel: [  379.920088] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  3 11:55:05 Alatheia kernel: [  379.963235] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul  3 11:55:05 Alatheia kernel: [  379.963685] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jul  3 11:55:05 Alatheia kernel: [  379.963691] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jul  3 11:55:05 Alatheia kernel: [  379.963696] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.



There are no scripts in /etc/cron.d/.  There is just the normal default stuff that comes install on Ubuntu and the root crontab I posted above.

I'm actually pretty certain, judging by the time in the log entry on July 3rd, that I restarted the computer then.  I had thought there might be a setting in the BIOS putting it into a suspended state or something independent of the OS.  The most recent loss of connectivity happened sometime between the night of July 2nd and the early morning hours of July 3rd.

Other than those entries, there is nothing else in the logs other than from July 1st when I was booting and getting everything back running... that's why it's so confusing, since I was certain there should be an entry in the logs.

The actual full syslog from the night of the 2nd to the morning of the 3rd is as follows (complete, nothing omitted):

> Jul  2 06:37:26 Alatheia rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="725" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type '$
Jul  2 07:17:01 Alatheia CRON[2502]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 08:17:01 Alatheia CRON[2506]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 09:17:01 Alatheia CRON[2510]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 10:17:01 Alatheia CRON[3029]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 11:17:01 Alatheia CRON[3033]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 12:17:01 Alatheia CRON[3038]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 13:17:01 Alatheia CRON[3042]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 14:16:23 Alatheia crontab[3153]: (root) BEGIN EDIT (root)
Jul  2 14:17:01 Alatheia CRON[3166]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 14:19:05 Alatheia crontab[3153]: (root) REPLACE (root)
Jul  2 14:19:05 Alatheia crontab[3153]: (root) END EDIT (root)
Jul  2 14:19:06 Alatheia crontab[3169]: (root) BEGIN EDIT (root)
Jul  2 14:19:38 Alatheia crontab[3169]: (root) END EDIT (root)
Jul  2 14:20:01 Alatheia cron[837]: (root) RELOAD (crontabs/root)
Jul  2 15:17:01 Alatheia CRON[3241]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 16:17:01 Alatheia CRON[3246]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 17:01:01 Alatheia CRON[3250]: (root) CMD (/root/iptables.sh )
Jul  2 17:17:01 Alatheia CRON[3323]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 18:17:01 Alatheia CRON[3328]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 19:17:01 Alatheia CRON[3332]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 20:17:01 Alatheia CRON[3336]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 21:17:01 Alatheia CRON[3340]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 22:17:01 Alatheia CRON[3344]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 23:17:01 Alatheia CRON[3348]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 00:17:01 Alatheia CRON[3352]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 01:17:01 Alatheia CRON[3356]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 02:17:01 Alatheia CRON[3360]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 03:17:01 Alatheia CRON[3364]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 04:17:01 Alatheia CRON[3368]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 05:17:01 Alatheia CRON[3372]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 06:17:01 Alatheia CRON[3376]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 06:25:01 Alatheia CRON[3380]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jul  3 06:45:10 Alatheia rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="725" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type '$
Jul  3 07:17:01 Alatheia CRON[3494]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 08:17:01 Alatheia CRON[3498]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 09:17:01 Alatheia CRON[3502]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 10:01:01 Alatheia CRON[3506]: (root) CMD (/root/iptables_day.sh )
Jul  3 10:17:01 Alatheia CRON[3579]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 11:17:01 Alatheia CRON[3805]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 11:17:07 Alatheia crontab[3807]: (root) BEGIN EDIT (root)
Jul  3 11:17:50 Alatheia crontab[3807]: (root) END EDIT (root)
Jul  3 11:44:21 Alatheia kernel: Kernel logging (proc) stopped.
Jul  3 11:48:51 Alatheia kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul  3 11:48:51 Alatheia rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="633" x-info="http://www.rsyslog.com"] (re)start
Jul  3 11:48:51 Alatheia rsyslogd: rsyslogd's groupid changed to 103
Jul  3 11:48:52 Alatheia rsyslogd: rsyslogd's userid changed to 101
Jul  3 11:48:51 Alatheia rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) 



As you can see, I did restart it around 11:48 am on July 3rd... but other than that, there's nothing there in the logs indicating any problems.

I will install smokeping tomorrow and see where I get with it.. I'm not too familiar with it so I want to read up a little first.

---

### Post by DJ_Max on 2013-07-04
What's the purpose of you running iptables.sh via cron? What are the rules?

---

### Post by jwright8 on 2013-07-05
I just block and unblock certain ports based on the time of day... I've been using it for a long time with no problems.

As a potentially embarrassing follow-up, I believe I have the problem solved (fingers crossed).  With the first tower, one or both of the NICs were actually bad... this was causing that one to lose connection routinely.  After replacing them, I switched to an identical (newer) tower at the same time as I also replaced the hard drive.  What I didn't do, however, is go into the BIOS and disable the "Power Management" feature.  It also said something like S3 (which I understand to be hibernation), and gave me a choice so I switched it to S1.  It shouldn't take effect, since I disabled the power management completely, but I figured it couldn't hurt.  Since I changed that, it's been up... I just hope it stays that way.  

Thanks for the help, hopefully this can help someone else from making a retarded mistake in the future!

---

### Post by DJ_Max on 2013-07-06
I was going to suggest bad hardware, but I saw you replaced them. Didn't think about the BIOS

---

### Post by jwright8 on 2013-07-11
Well, I apparently did not get things completely fixed... it's still doing it.  I discovered that internally I can ssh into the IP, and then the external ssh will work AFTER that.  It's almost like the NIC facing the outside world itself is going to sleep... which frankly makes no sense, as both are PCI NICs.  They are separate brands, sure, but I've never heard of a card that automatically shuts itself off.

---

