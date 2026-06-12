---
title: "Possible Rootkit and Funny Activity in Firewall"
date: 2009-03-31
forum: Security
---

### Post by BJ_Covert_Action on 2009-03-31
Hi All,

So I have been having some interesting traffic on my firewall lately and its finally gotten to a point that I am concerned about it (the legitimacy of the concern is beyond my knowledge unfortunately so bear with me).

Anyways, as a system introduction, I am running 8.04 ubuntu and have had it for a little over 4 months running now. I have been playing with various security and 'anonymity' tools like moblock and tor and so on. I am using firestarter as my GUI for iptables, though I do fiddle with iptables on the terminal from time to time. I also have clamAV installed but hardly use it.

So, that's an overview of my system. Over the past week I have been downloading a few files via Azureus using torrents downloaded from mininova.org. I noticed that I was getting TCP events on my firestarter GUI from various 'corporate' ip addresses. I found a lot of them were from Comcast in NJ, a few Canadian ISPs, and even one or two from sony. However, since these were on my events log as 'blocked' I was not too worried about it. This evening, however, when I fired up firestarter, and then moblock, and then Azureus, I noticed I was getting some unkown active connections on my firestarter status page: namely, these:

```

Source         Destination    Port    Service    Program
192.168.1.102  97.120.29.66   64342   Unknown
""             72.56.158.199  47037   Unknown
""             12.12.33.34    61942   Unknown
""             90.206.196.84  23223   Unknown

```
...as well as two firefox entries for HTTP on port 80

The source I recognize as my own IP address, however, the destinations I don't recognize.

Doing whois queries on those four destinations returns these owners of the IPs (if you want me to post the full whois output let me know)

Qwest Communications Corporation
Sprint PCS
Sprint PCS
AT&T Communications

So doing some google sleuthing revealed mixed feelings about this kind of activity where some individuals declared it a sure sign of a lawsuit whilst others claimed it to be typical user connections. 

Other IPs I recorded earlier this week include:

99.254.111.53
157.157.183.112
24.245.25.74
190.19.41.39
75.111.49.231
70.68.165.224

I haven't whoised them yet. 

Well all of this may seem like simple paranoia, but then, while torrenting, I noticed one other active connection that ended once I killed Azureus. I had a program called Gatecrasher active on port 6969.

Doing some research I found out that this is a windows trojan, but should not afffect a Linux box. Still, being paranoid, I dug deeper. Some folk suggested that this could, indeed be a rootkit exploit running on a Linux box. Furthermore, this started happening shortly after I posted various log outputs to this forum to help configure my moblock. I am not sure any of the info in those logs matters or can be used to exploit, but its left me thinking.

So here is my predicament, I am by no means a security expert nor a l33t h2xxorz. However, this field has been of intense interest to me and I think this particular event might be a good time to learn a thing or two about securing my linux box. That being said, any information anyone has regarding anything in this post (or other hints and tricks) please feel free to contact me via my user space here, or just reply to this post.

However, the primary concern for me that I feel I need to address now is, is my system compromised?

Any help you all could give me in determining this would be invaluable. I am patient, willing to learn, and am in no rush (I do not have any 'sensitive' information on my network so if I am rooted the best the h4xxor will get is probably some dusty old pictures and a lot of spiderman cartoons). So please, any help anyone could give would be much appreciated.

Also, in case it helps, here is some other possibly related output.

I downloaded and installed chkrootkit and ran it to find 

```

ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `crontab'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not infected
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not found
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not found
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/jvm/.java-6-sun.jinfo
/usr/lib/jvm/java-6-sun-1.6.0.07/.systemPrefs
/usr/lib/firefox/.autoreg
/usr/lib/firefox-3.0.8/.autoreg
/usr/lib/xulrunner-1.9.0.8/.autoreg
/lib/modules/2.6.24-24-generic/volatile/.mounted

Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
Searching for OBSD rk v1... nothing found
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for rootedoor... nothing found
Searching for ENYELKM rootkit default files... nothing found
Searching for anomalies in shell history files... /usr/bin/find: //home/brady/.gvfs: Permission denied
/usr/bin/find: //home/brady/.gvfs: Permission denied
nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[6272], /sbin/dhclient3[6283])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted

```

My most recent netstat command on the terminal yielded (ran while torrenting):

```

...
<cutoff>
...

unix  3      [ ]         STREAM     CONNECTED     65660    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     65659    
unix  3      [ ]         STREAM     CONNECTED     65657    /tmp/.ICE-unix/5993
unix  3      [ ]         STREAM     CONNECTED     65656    
unix  3      [ ]         STREAM     CONNECTED     65602    @/dbus-vfs-daemon/socket-Ci78jWis
unix  3      [ ]         STREAM     CONNECTED     65601    
unix  3      [ ]         STREAM     CONNECTED     65600    @/dbus-vfs-daemon/socket-4RZ1Fpz0
unix  3      [ ]         STREAM     CONNECTED     65599    
unix  3      [ ]         STREAM     CONNECTED     65594    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     65593    
unix  3      [ ]         STREAM     CONNECTED     65559    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     65558    
unix  3      [ ]         STREAM     CONNECTED     65549    @/dbus-vfs-daemon/socket-JGYNgabu
unix  3      [ ]         STREAM     CONNECTED     65548    
unix  3      [ ]         STREAM     CONNECTED     65547    @/dbus-vfs-daemon/socket-o7XTpgRK
unix  3      [ ]         STREAM     CONNECTED     65546    
unix  3      [ ]         STREAM     CONNECTED     65452    /tmp/orbit-brady/linc-17c6-0-3353df74dd17
unix  3      [ ]         STREAM     CONNECTED     65451    
unix  3      [ ]         STREAM     CONNECTED     65450    /tmp/orbit-brady/linc-1830-0-456cc38a1885c
unix  3      [ ]         STREAM     CONNECTED     65449    
unix  3      [ ]         STREAM     CONNECTED     65447    @/dbus-vfs-daemon/socket-VcX3DZQz
unix  3      [ ]         STREAM     CONNECTED     65446    
unix  3      [ ]         STREAM     CONNECTED     65448    @/dbus-vfs-daemon/socket-LsWAfnKP
unix  3      [ ]         STREAM     CONNECTED     65445    
unix  3      [ ]         STREAM     CONNECTED     65438    @/dbus-vfs-daemon/socket-uNqItNHh
unix  3      [ ]         STREAM     CONNECTED     65437    
unix  3      [ ]         STREAM     CONNECTED     65439    @/dbus-vfs-daemon/socket-MR9BqnJL
unix  3      [ ]         STREAM     CONNECTED     65436    
unix  3      [ ]         STREAM     CONNECTED     65429    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65428    
unix  3      [ ]         STREAM     CONNECTED     65421    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65420    
unix  3      [ ]         STREAM     CONNECTED     65399    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65398    
unix  3      [ ]         STREAM     CONNECTED     65392    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65391    
unix  3      [ ]         STREAM     CONNECTED     65390    /tmp/orbit-brady/linc-1830-0-456cc38a1885c
unix  3      [ ]         STREAM     CONNECTED     65389    
unix  3      [ ]         STREAM     CONNECTED     65388    /tmp/orbit-brady/linc-17cc-0-e16a69e89213
unix  3      [ ]         STREAM     CONNECTED     65387    
unix  3      [ ]         STREAM     CONNECTED     65386    /tmp/orbit-brady/linc-1830-0-456cc38a1885c
unix  3      [ ]         STREAM     CONNECTED     65385    
unix  3      [ ]         STREAM     CONNECTED     65303    /tmp/orbit-brady/linc-1819-0-7963692eaf95d
unix  3      [ ]         STREAM     CONNECTED     65302    
unix  3      [ ]         STREAM     CONNECTED     65295    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65293    
unix  3      [ ]         STREAM     CONNECTED     65301    /tmp/orbit-brady/linc-17cc-0-e16a69e89213
unix  3      [ ]         STREAM     CONNECTED     65284    
unix  3      [ ]         STREAM     CONNECTED     65279    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65278    
unix  3      [ ]         STREAM     CONNECTED     65277    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     65276    
unix  3      [ ]         STREAM     CONNECTED     65267    @/dbus-vfs-daemon/socket-l0J4U7GW
unix  3      [ ]         STREAM     CONNECTED     65266    
unix  3      [ ]         STREAM     CONNECTED     65268    @/dbus-vfs-daemon/socket-8xxF1nja
unix  3      [ ]         STREAM     CONNECTED     65265    
unix  3      [ ]         STREAM     CONNECTED     65262    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     65261    
unix  3      [ ]         STREAM     CONNECTED     65254    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65253    
unix  3      [ ]         STREAM     CONNECTED     65212    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     65211    
unix  3      [ ]         STREAM     CONNECTED     65182    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65181    
unix  3      [ ]         STREAM     CONNECTED     65177    /tmp/orbit-brady/linc-1822-0-397ebc847c772
unix  3      [ ]         STREAM     CONNECTED     65176    
unix  3      [ ]         STREAM     CONNECTED     65163    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     65162    
unix  3      [ ]         STREAM     CONNECTED     65161    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65160    
unix  3      [ ]         STREAM     CONNECTED     65159    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     65158    
unix  3      [ ]         STREAM     CONNECTED     65156    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     65155    
unix  3      [ ]         STREAM     CONNECTED     65157    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     65141    
unix  3      [ ]         STREAM     CONNECTED     65125    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     65124    
unix  3      [ ]         STREAM     CONNECTED     65099    /tmp/orbit-brady/linc-1819-0-7963692eaf95d
unix  3      [ ]         STREAM     CONNECTED     65097    
unix  3      [ ]         STREAM     CONNECTED     65094    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     65074    
unix  3      [ ]         STREAM     CONNECTED     65072    /tmp/.ICE-unix/5993
unix  3      [ ]         STREAM     CONNECTED     65071    
unix  3      [ ]         STREAM     CONNECTED     65066    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     65065    
unix  3      [ ]         STREAM     CONNECTED     65047    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     65046    
unix  3      [ ]         STREAM     CONNECTED     65025    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     65024    
unix  3      [ ]         STREAM     CONNECTED     64999    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     64998    
unix  3      [ ]         STREAM     CONNECTED     64983    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     64982    
unix  3      [ ]         STREAM     CONNECTED     64966    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64965    
unix  3      [ ]         STREAM     CONNECTED     64955    /tmp/orbit-brady/linc-17c7-0-3353df794a77
unix  3      [ ]         STREAM     CONNECTED     64954    
unix  3      [ ]         STREAM     CONNECTED     64953    /tmp/orbit-brady/linc-17c6-0-3353df74dd17
unix  3      [ ]         STREAM     CONNECTED     64952    
unix  3      [ ]         STREAM     CONNECTED     64948    /tmp/orbit-brady/linc-17cc-0-e16a69e89213
unix  3      [ ]         STREAM     CONNECTED     64946    
unix  3      [ ]         STREAM     CONNECTED     64947    /tmp/orbit-brady/linc-17cc-0-e16a69e89213
unix  3      [ ]         STREAM     CONNECTED     64945    
unix  3      [ ]         STREAM     CONNECTED     64941    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64940    
unix  3      [ ]         STREAM     CONNECTED     64939    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     64938    
unix  2      [ ]         DGRAM                    64937    
unix  3      [ ]         STREAM     CONNECTED     64935    /tmp/orbit-brady/linc-181d-0-2f0fe6bf846b2
unix  3      [ ]         STREAM     CONNECTED     64934    
unix  3      [ ]         STREAM     CONNECTED     64928    /tmp/.ICE-unix/5993
unix  3      [ ]         STREAM     CONNECTED     64927    
unix  3      [ ]         STREAM     CONNECTED     64931    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     64910    
unix  3      [ ]         STREAM     CONNECTED     64906    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     64905    
unix  3      [ ]         STREAM     CONNECTED     64899    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64898    
unix  3      [ ]         STREAM     CONNECTED     64897    /tmp/orbit-brady/linc-1815-0-30dc72811ed7a
unix  3      [ ]         STREAM     CONNECTED     64896    
unix  3      [ ]         STREAM     CONNECTED     64861    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     64860    
unix  3      [ ]         STREAM     CONNECTED     64856    /tmp/.ICE-unix/5993
unix  3      [ ]         STREAM     CONNECTED     64812    
unix  3      [ ]         STREAM     CONNECTED     64808    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     64807    
unix  3      [ ]         STREAM     CONNECTED     64802    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     64801    
unix  3      [ ]         STREAM     CONNECTED     64605    /tmp/orbit-brady/linc-1811-0-328c2043e784
unix  3      [ ]         STREAM     CONNECTED     64604    
unix  3      [ ]         STREAM     CONNECTED     64601    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     64600    
unix  3      [ ]         STREAM     CONNECTED     64559    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64558    
unix  3      [ ]         STREAM     CONNECTED     64557    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     64555    
unix  3      [ ]         STREAM     CONNECTED     64855    /tmp/.ICE-unix/5993
unix  3      [ ]         STREAM     CONNECTED     64497    
unix  3      [ ]         STREAM     CONNECTED     64479    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     64478    
unix  3      [ ]         STREAM     CONNECTED     64398    /tmp/orbit-brady/linc-1812-0-a0b514f83251
unix  3      [ ]         STREAM     CONNECTED     64397    
unix  3      [ ]         STREAM     CONNECTED     64394    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     64393    
unix  3      [ ]         STREAM     CONNECTED     64388    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     64387    
unix  3      [ ]         STREAM     CONNECTED     64386    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64385    
unix  3      [ ]         STREAM     CONNECTED     64384    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     64382    
unix  3      [ ]         STREAM     CONNECTED     64263    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     64262    
unix  3      [ ]         STREAM     CONNECTED     64228    /tmp/.ICE-unix/5993
unix  3      [ ]         STREAM     CONNECTED     64227    
unix  3      [ ]         STREAM     CONNECTED     64184    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64183    
unix  3      [ ]         STREAM     CONNECTED     64180    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64179    
unix  3      [ ]         STREAM     CONNECTED     64127    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64126    
unix  3      [ ]         STREAM     CONNECTED     64111    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     64110    
unix  3      [ ]         STREAM     CONNECTED     64090    /tmp/orbit-brady/linc-17c7-0-3353df794a77
unix  3      [ ]         STREAM     CONNECTED     64089    
unix  3      [ ]         STREAM     CONNECTED     64086    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     64085    
unix  3      [ ]         STREAM     CONNECTED     64083    /tmp/.ICE-unix/5993
unix  3      [ ]         STREAM     CONNECTED     64082    
unix  3      [ ]         STREAM     CONNECTED     64078    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     64076    
unix  3      [ ]         STREAM     CONNECTED     63997    /tmp/orbit-brady/linc-17c6-0-3353df74dd17
unix  3      [ ]         STREAM     CONNECTED     63996    
unix  3      [ ]         STREAM     CONNECTED     63993    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     63992    
unix  3      [ ]         STREAM     CONNECTED     63988    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     63987    
unix  3      [ ]         STREAM     CONNECTED     63986    /tmp/.ICE-unix/5993
unix  3      [ ]         STREAM     CONNECTED     63985    
unix  3      [ ]         STREAM     CONNECTED     63979    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     63978    
unix  3      [ ]         STREAM     CONNECTED     63843    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     63842    
unix  3      [ ]         STREAM     CONNECTED     63840    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     63839    
unix  3      [ ]         STREAM     CONNECTED     63837    /tmp/orbit-brady/linc-17be-0-34e8fbcc1346c
unix  3      [ ]         STREAM     CONNECTED     63836    
unix  3      [ ]         STREAM     CONNECTED     63833    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     63832    
unix  3      [ ]         STREAM     CONNECTED     63828    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     63827    
unix  3      [ ]         STREAM     CONNECTED     63633    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     63632    
unix  3      [ ]         STREAM     CONNECTED     63629    /tmp/orbit-brady/linc-17b5-0-921f25aed861
unix  3      [ ]         STREAM     CONNECTED     63628    
unix  3      [ ]         STREAM     CONNECTED     63625    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     63624    
unix  3      [ ]         STREAM     CONNECTED     63637    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     63577    
unix  3      [ ]         STREAM     CONNECTED     63108    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     63107    
unix  3      [ ]         STREAM     CONNECTED     61504    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61503    
unix  3      [ ]         STREAM     CONNECTED     61380    /tmp/orbit-brady/linc-17a3-0-8f6d34581128
unix  3      [ ]         STREAM     CONNECTED     61379    
unix  3      [ ]         STREAM     CONNECTED     61376    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     61375    
unix  3      [ ]         STREAM     CONNECTED     61371    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     61370    
unix  3      [ ]         STREAM     CONNECTED     61369    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     61368    
unix  3      [ ]         STREAM     CONNECTED     61329    @/tmp/dbus-pfjwOXRhnF
unix  3      [ ]         STREAM     CONNECTED     61328    
unix  3      [ ]         STREAM     CONNECTED     61327    
unix  3      [ ]         STREAM     CONNECTED     61326    
unix  3      [ ]         STREAM     CONNECTED     61305    /tmp/orbit-brady/linc-1769-0-2c66e73e370bb
unix  3      [ ]         STREAM     CONNECTED     61304    
unix  3      [ ]         STREAM     CONNECTED     61301    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     61300    
unix  3      [ ]         STREAM     CONNECTED     61268    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     61267    
unix  3      [ ]         STREAM     CONNECTED     61210    /tmp/orbit-brady/linc-1769-0-5a436b9baa25c
unix  3      [ ]         STREAM     CONNECTED     61209    
unix  3      [ ]         STREAM     CONNECTED     61206    /tmp/orbit-brady/linc-1766-0-f7f31653061
unix  3      [ ]         STREAM     CONNECTED     61205    
unix  3      [ ]         STREAM     CONNECTED     61199    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     61198    
unix  3      [ ]         STREAM     CONNECTED     61027    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61026    
unix  2      [ ]         DGRAM                    61020    
unix  3      [ ]         STREAM     CONNECTED     61014    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61013    
unix  3      [ ]         STREAM     CONNECTED     15361    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15360    
unix  5      [ ]         STREAM     CONNECTED     15363    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14896    
unix  3      [ ]         STREAM     CONNECTED     14795    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     14794    
unix  4      [ ]         STREAM     CONNECTED     15362    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14779    
unix  3      [ ]         STREAM     CONNECTED     14419    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14418    
unix  2      [ ]         DGRAM                    14417    
unix  3      [ ]         STREAM     CONNECTED     14405    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14404    
unix  2      [ ]         DGRAM                    14403    
unix  3      [ ]         STREAM     CONNECTED     14339    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14338    
unix  2      [ ]         DGRAM                    14323    
unix  3      [ ]         STREAM     CONNECTED     14224    @/var/run/hald/dbus-iryF2PFxyH
unix  3      [ ]         STREAM     CONNECTED     14222    
unix  3      [ ]         STREAM     CONNECTED     14221    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14220    
unix  3      [ ]         STREAM     CONNECTED     14057    @/var/run/hald/dbus-iryF2PFxyH
unix  3      [ ]         STREAM     CONNECTED     14056    
unix  3      [ ]         STREAM     CONNECTED     14055    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14054    
unix  3      [ ]         STREAM     CONNECTED     13936    @/var/run/hald/dbus-iryF2PFxyH
unix  3      [ ]         STREAM     CONNECTED     13935    
unix  3      [ ]         STREAM     CONNECTED     13900    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     13899    
unix  3      [ ]         STREAM     CONNECTED     13894    @/var/run/hald/dbus-iryF2PFxyH
unix  3      [ ]         STREAM     CONNECTED     13893    
unix  3      [ ]         STREAM     CONNECTED     13629    @/var/run/hald/dbus-M5EVUnTHlo
unix  3      [ ]         STREAM     CONNECTED     13628    
unix  3      [ ]         STREAM     CONNECTED     13584    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13583    
unix  3      [ ]         STREAM     CONNECTED     13570    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13569    
unix  3      [ ]         STREAM     CONNECTED     13531    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13530    
unix  2      [ ]         DGRAM                    13529    
unix  3      [ ]         STREAM     CONNECTED     13469    
unix  3      [ ]         STREAM     CONNECTED     13468    
unix  3      [ ]         STREAM     CONNECTED     13375    
unix  3      [ ]         STREAM     CONNECTED     13374    
unix  3      [ ]         STREAM     CONNECTED     13021    /var/run/acpid.socket
unix  4      [ ]         STREAM     CONNECTED     13018    
unix  2      [ ]         DGRAM                    13015    
unix  3      [ ]         STREAM     CONNECTED     12981    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12980    
unix  3      [ ]         STREAM     CONNECTED     12975    
unix  3      [ ]         STREAM     CONNECTED     12974    
unix  2      [ ]         DGRAM                    12972    
unix  3      [ ]         STREAM     CONNECTED     12945    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12944    
unix  3      [ ]         STREAM     CONNECTED     12936    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12935    
unix  3      [ ]         STREAM     CONNECTED     12908    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12907    
unix  2      [ ]         DGRAM                    12903    
unix  3      [ ]         STREAM     CONNECTED     12888    
unix  3      [ ]         STREAM     CONNECTED     12887    
unix  2      [ ]         DGRAM                    12864  

```

My blockcontrol status otuput is:

```

Current IPv4 iptables rules (this may take a while):

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
   11  1203 ACCEPT     udp  --  *      *       192.168.1.1          0.0.0.0/0           
   68  2856 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  wlan0  *       0.0.0.0/0            255.255.255.255     
    3   705 DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
  463  404K INBOUND    all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.102        192.168.1.1         tcp dpt:53 
   11   709 ACCEPT     udp  --  *      *       192.168.1.102        192.168.1.1         udp dpt:53 
   68  2856 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
  490 79210 OUTBOUND   all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  463  404K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:6881:6889 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:6881:6889 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25544 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25544 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25544 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25544 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8080 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:8080 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8118 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:8118 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:9050 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:9050 
    0     0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
  465 78110 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
   25  1100 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Current IPv6 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 6 packets, 368 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 6 packets, 368 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Please check if the above printed iptables rules are correct!

 * moblock is running

```

my clamAV log reads:

```

Mon Mar 30 01:54:46 2009 -> Socket file removed.
Mon Mar 30 01:54:46 2009 -> Pid file removed.
Mon Mar 30 01:54:46 2009 -> --- Stopped at Mon Mar 30 01:54:46 2009
Mon Mar 30 16:48:08 2009 -> +++ Started at Mon Mar 30 16:48:08 2009
Mon Mar 30 16:48:08 2009 -> clamd daemon 0.92.1 (OS: linux-gnu, ARCH: i386, CPU: i486)
Mon Mar 30 16:48:08 2009 -> Log file size limit disabled.
Mon Mar 30 16:48:08 2009 -> Reading databases from /var/lib/clamav
Mon Mar 30 16:48:08 2009 -> Not loading PUA signatures.
Mon Mar 30 16:48:12 2009 -> Loaded 233110 signatures.
Mon Mar 30 16:48:12 2009 -> Unix socket file /var/run/clamav/clamd.ctl
Mon Mar 30 16:48:12 2009 -> Setting connection queue length to 15
Mon Mar 30 16:48:12 2009 -> Archive: Archived file size limit set to 10485760 bytes.
Mon Mar 30 16:48:12 2009 -> Archive: Recursion level limit set to 5.
Mon Mar 30 16:48:12 2009 -> Archive: Files limit set to 1000.
Mon Mar 30 16:48:12 2009 -> Archive: Compression ratio limit set to 250.
Mon Mar 30 16:48:12 2009 -> Archive support enabled.
Mon Mar 30 16:48:12 2009 -> Algorithmic detection enabled.
Mon Mar 30 16:48:12 2009 -> Portable Executable support enabled.
Mon Mar 30 16:48:12 2009 -> ELF support enabled.
Mon Mar 30 16:48:12 2009 -> Mail files support enabled.
Mon Mar 30 16:48:12 2009 -> Mail: Recursion level limit set to 64.
Mon Mar 30 16:48:12 2009 -> OLE2 support enabled.
Mon Mar 30 16:48:12 2009 -> PDF support disabled.
Mon Mar 30 16:48:12 2009 -> HTML support enabled.
Mon Mar 30 16:48:12 2009 -> Self checking every 3600 seconds.
Mon Mar 30 18:07:24 2009 -> +++ Started at Mon Mar 30 18:07:24 2009
Mon Mar 30 18:07:24 2009 -> clamd daemon 0.92.1 (OS: linux-gnu, ARCH: i386, CPU: i486)
Mon Mar 30 18:07:24 2009 -> Log file size limit disabled.
Mon Mar 30 18:07:24 2009 -> Reading databases from /var/lib/clamav
Mon Mar 30 18:07:24 2009 -> Not loading PUA signatures.
Mon Mar 30 18:07:29 2009 -> Loaded 233110 signatures.
Mon Mar 30 18:07:29 2009 -> Unix socket file /var/run/clamav/clamd.ctl
Mon Mar 30 18:07:29 2009 -> Setting connection queue length to 15
Mon Mar 30 18:07:29 2009 -> Archive: Archived file size limit set to 10485760 bytes.
Mon Mar 30 18:07:29 2009 -> Archive: Recursion level limit set to 5.
Mon Mar 30 18:07:29 2009 -> Archive: Files limit set to 1000.
Mon Mar 30 18:07:29 2009 -> Archive: Compression ratio limit set to 250.
Mon Mar 30 18:07:29 2009 -> Archive support enabled.
Mon Mar 30 18:07:29 2009 -> Algorithmic detection enabled.
Mon Mar 30 18:07:29 2009 -> Portable Executable support enabled.
Mon Mar 30 18:07:29 2009 -> ELF support enabled.
Mon Mar 30 18:07:29 2009 -> Mail files support enabled.
Mon Mar 30 18:07:29 2009 -> Mail: Recursion level limit set to 64.
Mon Mar 30 18:07:29 2009 -> OLE2 support enabled.
Mon Mar 30 18:07:29 2009 -> PDF support disabled.
Mon Mar 30 18:07:29 2009 -> HTML support enabled.
Mon Mar 30 18:07:29 2009 -> Self checking every 3600 seconds.

```

(which seems like a lot of activity for a program I never actively manage)

I am sure there are other logs that might be mroe helpful, but that's all I know of for now. I am looking for some kind of netstat or iptables activity log but can't find it.

Pleas let me know if you can help or anything else you might need to help me address this problem.

Cheers,
Brady

---

### Post by BJ_Covert_Action on 2009-03-31
One other thing I just noticed. Wehn running ifconfig -v , I noticed this output:

```

eth0      Link encap:Ethernet  HWaddr 00:0c:76:e4:9e:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1345049 (1.2 MB)  TX bytes:1345049 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:9d:9a:d6  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe9d:9ad6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:549654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:424562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:390131679 (372.0 MB)  TX bytes:54234515 (51.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-9D-9A-D6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

.which seems normal to me except that wmaster0 entry. I am not sure I have ever seen that before. It shows up on the "Network" section of the firestarter GUI as well. Any ideas?

---

### Post by jre on 2009-03-31
wmaster0 is normal to be shown by ifconfig.

I would not worry about a rootkit. There are so many other harmless reasons for connections, especially after torrenting.
But I noticed this: In your iptables rules there is nothing related to moblock/blockcontrol. So although MoBlock (the daemon) is running no traffic gets to it to be checked. Did you (re-)start blockcontrol after your firewall?

Please note that I did not look at your complete logfiles. I'm no security expert.

---

### Post by BJ_Covert_Action on 2009-04-01
Yes, I tend to do a blockcontrol restart every time I open firestarter.

---

### Post by jre on 2009-04-01
Well, if you make a "blockcontrol restart" and directly after that the blockcontrol iptables rules are still missing, then something is wrong.
Is iptables insertion enabled (blockcontrol show_config)?

---

### Post by BJ_Covert_Action on 2009-04-02
I don't know. I will have to take a look at it when I get home. Unfortunately, my Internet Service seems to have tanked indefinitely. My modem isn't getting a signal from the DSL line anymore. I have to get it cracked out with AT&T over when I will have internet again. Right now, I am posting from work. I'll post my show_config results as soon as I can.

Thanks for the patience and continued existence.

---

### Post by BJ_Covert_Action on 2009-04-02
So I fired up iptables first and then moblock second and when I did, my status read as:

```

Current IPv4 iptables rules (this may take a while):

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 blockcontrol_in  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
    0     0 ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
    0     0 ACCEPT     udp  --  *      *       192.168.1.1          0.0.0.0/0           
   34  1428 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  wlan0  *       0.0.0.0/0            255.255.255.255     
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
    0     0 INBOUND    all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 blockcontrol_fw  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 blockcontrol_out  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
    0     0 ACCEPT     tcp  --  *      *       192.168.1.102        192.168.1.1         tcp dpt:53 
    0     0 ACCEPT     udp  --  *      *       192.168.1.102        192.168.1.1         udp dpt:53 
   34  1428 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 OUTBOUND   all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:6881:6889 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:6881:6889 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25544 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25544 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25544 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25544 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8080 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:8080 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8118 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:8118 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:9050 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:9050 
    0     0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain blockcontrol_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.1         
    0     0 RETURN     all  --  *      *       192.168.1.0/24       192.168.1.0/24      
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 RETURN     all  --  *      *       192.168.1.0/24       0.0.0.0/0           
    0     0 RETURN     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           source IP range 192.168.1.100-192.168.1.110 
    0     0 RETURN     all  --  *      *       192.168.1.0/24       0.0.0.0/0           
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.1         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.0/24      
    0     0 RETURN     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           destination IP range 192.168.1.100-192.168.1.110 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.0/24      
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Current IPv6 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Please check if the above printed iptables rules are correct!

 * moblock is running


```

So the rules get loaded when I fire them up in the right order.  When I restart the firewall, but not moblock, the blockcontrol rules disappear.

Then when I restart blockcontrol, I get:

```

Current IPv4 iptables rules (this may take a while):

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 blockcontrol_in  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
    0     0 ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
    0     0 ACCEPT     udp  --  *      *       192.168.1.1          0.0.0.0/0           
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  wlan0  *       0.0.0.0/0            255.255.255.255     
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
    0     0 INBOUND    all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 blockcontrol_fw  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 blockcontrol_out  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
    0     0 ACCEPT     tcp  --  *      *       192.168.1.102        192.168.1.1         tcp dpt:53 
    0     0 ACCEPT     udp  --  *      *       192.168.1.102        192.168.1.1         udp dpt:53 
    0     0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    1    68 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 OUTBOUND   all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:6881:6889 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:6881:6889 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25544 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25544 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25544 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25544 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8080 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:8080 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8118 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:8118 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:9050 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:9050 
    0     0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain blockcontrol_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.1         
    0     0 RETURN     all  --  *      *       192.168.1.0/24       192.168.1.0/24      
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 RETURN     all  --  *      *       192.168.1.0/24       0.0.0.0/0           
    0     0 RETURN     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           source IP range 192.168.1.100-192.168.1.110 
    0     0 RETURN     all  --  *      *       192.168.1.0/24       0.0.0.0/0           
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.1         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.0/24      
    0     0 RETURN     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           destination IP range 192.168.1.100-192.168.1.110 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.0/24      
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Current IPv6 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Please check if the above printed iptables rules are correct!

 * moblock is running


```

And the blockcontrol rules are loaded again. So I think when I posted my last log I had failed to restart (I know, epic fail on my part). Anyways, it seems to me like it is running fine now, but if I am mistaken on this (and I well may be) please let me know.

Thanks for all the help jre, if you ever come to the central coast of cali I'll buy you a beer.

Cheers.

---

### Post by jre on 2009-04-03
> **BJ_Covert_Action said:**
> So I think when I posted my last log I had failed to restart (I know, epic fail on my part). Anyways, it seems to me like it is running fine now, but if I am mistaken on this (and I well may be) please let me know.

You got it right now. Glad it was "just" a user mistake.

> **BJ_Covert_Action said:**
> Thanks for all the help jre, if you ever come to the central coast of cali I'll buy you a beer.
That's nice, thanks! Anyone paying the flight from Germany? ;-)

---

### Post by BJ_Covert_Action on 2009-04-04
> **jre said:**
> 
That's nice, thanks! Anyone paying the flight from Germany? ;-)

At the rate we're going.....the U.S. Federal Government as part of the economic stimulus package....Heyo!.....

---

### Post by albinootje on 2009-04-04
> **BJ_Covert_Action said:**
> This evening, however, when I fired up firestarter, and then moblock, and then Azureus, I noticed I was getting some unkown active connections on my firestarter status page: namely, these:

```

Source         Destination    Port    Service    Program
192.168.1.102  97.120.29.66   64342   Unknown
""             72.56.158.199  47037   Unknown
""             12.12.33.34    61942   Unknown
""             90.206.196.84  23223   Unknown

```
...as well as two firefox entries for HTTP on port 80

If you start up Firefox, do you use the default homepage, which uses the google search bar embedded ?
What about Azureus ? Is that not making any connections at startup, perhaps unfinished downloads, or searching for Azureus updates ?
And what about update manager ?
Are the ip addresses related to e.g. us.archive.ubuntu.com perhaps ?

---

### Post by albinootje on 2009-04-04
And I forgot about Skype, as a sysadmin it drives me crazy to have users at work who use Skype.
Skype produces quite some udp connections to all kind of machines worldwide (...).

---

### Post by BJ_Covert_Action on 2009-04-10
I don't actually use Skype at all. I suppose it could be update manager or Azureus. It wouldn't be firefox's embedded google search bar because I disabled that loading in firefox.

Those unkown types of connections only show up after I have used tor or Azureus, I wonder if most of them are just hanging proxies or something like that. Though, I would hope that once I closed those particular services, all connections they opened would also close. If not, could anyone give me some advice on how to ensure that they do close their connections upon ending the service?

---

