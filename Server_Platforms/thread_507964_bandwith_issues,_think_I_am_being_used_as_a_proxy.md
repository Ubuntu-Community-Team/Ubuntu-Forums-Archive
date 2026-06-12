---
title: "bandwith issues, think I am being used as a proxy"
date: 2007-07-23
forum: Server Platforms
---

### Post by twistedtwig on 2007-07-23
Hi all,

I think I have a real issue.  I have noticed that my bandwidth is being sucked up hugely.  I am sending LOTS of packets when there is nothing really happening on the network.

I am averaging 720KiB/s.

I installed darkstat and it has listed a LOT of connections houseofhawkins.com:666

(at this point I am not worried at keeping that live for the mo, for analysis).

I also installed wireshark and it shows that (on ETH0 my external IP) UDP is 60-80% ARP 30% on average

the log (only ran for 30 secs or so has 116 entries.. tons of source and destination IPs all external to my network.  ARP DNS and TCP protocol

Don't really know what I am looking at but I think I am being used as a proxy server or something of the kind.

Can anyone help me please?

Should I wipe the box and start again?  would need to backup a lot of conf files as its been a long while since I have done a server install.

Thanks for the help

---

### Post by twistedtwig on 2007-07-23
I have killed samba and apache2 but that has made no difference


EDIT: very confused.. ps ax | grep apache only shows the grep but darkstat still runs... main site doesn't.... is this a bad thing?

---

### Post by murraymca on 2007-07-23
If you use netstat -an then

sudo lsof -i4:a_port_number (example sudo lsof -i4:666)

you can see what is making those connections.

Are you running iptables at all?

Cheers.

---

### Post by twistedtwig on 2007-07-24
thank you for your reply... yes IP tables is running which blocks most ports, does a little forwarding and lets in vnc and web etc.

here is my netstat rather worried how long it is:

[PHP]Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:46721         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 217.44.127.70:53        0.0.0.0:*               LISTEN     
tcp        0      0 192.168.10.1:53         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:666             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:953                 :::*                    LISTEN     
tcp6       0      0 ::ffff:192.168.10.1:22  ::ffff:192.168.10:57294 ESTABLISHED
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          
udp        0      0 0.0.0.0:10000           0.0.0.0:*                          
udp        0      0 0.0.0.0:177             0.0.0.0:*                          
udp        0      0 217.44.127.70:53        0.0.0.0:*                          
udp        0      0 192.168.10.1:53         0.0.0.0:*                          
udp        0      0 127.0.0.1:53            0.0.0.0:*                          
udp        0      0 0.0.0.0:3130            0.0.0.0:*                          
udp        0      0 0.0.0.0:67              0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp6       0      0 :::32769                :::*                               
raw        0      0 0.0.0.0:1               0.0.0.0:*               7          
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     10833    public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     9732     /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     9761     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8426     @/tmp/hald-local/dbus-v30NZaMdF5
unix  10     [ ]         DGRAM                    123652   /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     10840    private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     10845    private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     10031    @/tmp/dbus-mlVCOda1qN
unix  2      [ ACC ]     STREAM     LISTENING     10023    /tmp/ssh-zhxNmQ4058/agent.4058
unix  2      [ ACC ]     STREAM     LISTENING     10026    /tmp/ssh-GdFYUj4058/agent.4058
unix  2      [ ACC ]     STREAM     LISTENING     10115    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  2      [ ACC ]     STREAM     LISTENING     10130    /tmp/orbit-jon/linc-fda-0-66f510294353e
unix  2      [ ACC ]     STREAM     LISTENING     10469    /tmp/.ICE-unix/4058
unix  2      [ ACC ]     STREAM     LISTENING     10483    /tmp/keyring-6E9i9w/socket
unix  2      [ ACC ]     STREAM     LISTENING     10562    /tmp/orbit-jon/linc-10e3-0-5aeaa0955f694
unix  2      [ ACC ]     STREAM     LISTENING     10849    private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     10853    private/defer
unix  2      [ ACC ]     STREAM     LISTENING     13186    /tmp/mapping-jon
unix  2      [ ]         DGRAM                    4570     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     10857    private/trace
unix  2      [ ACC ]     STREAM     LISTENING     10861    private/verify
unix  2      [ ACC ]     STREAM     LISTENING     10865    public/flush
unix  2      [ ACC ]     STREAM     LISTENING     10309    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     10871    private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     10875    private/smtp
unix  2      [ ]         DGRAM                    4789     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     12915    /var/run/sdp
unix  2      [ ]         DGRAM                    8435     @/org/freedesktop/hal/udev_event
unix  2      [ ACC ]     STREAM     LISTENING     10879    private/relay
unix  2      [ ACC ]     STREAM     LISTENING     10883    public/showq
unix  2      [ ACC ]     STREAM     LISTENING     10923    private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     10887    private/error
unix  2      [ ACC ]     STREAM     LISTENING     10891    private/discard
unix  2      [ ACC ]     STREAM     LISTENING     10895    private/local
unix  2      [ ACC ]     STREAM     LISTENING     10899    private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     10903    private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     10907    private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     10911    private/scache
unix  2      [ ACC ]     STREAM     LISTENING     10915    private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     10919    private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     10927    private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     10931    private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     10935    private/mailman
unix  2      [ ACC ]     STREAM     LISTENING     8427     @/tmp/hald-runner/dbus-8bNqMT7Ml8
unix  2      [ ACC ]     STREAM     LISTENING     37579    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     8408     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     12519    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  2      [ ACC ]     STREAM     LISTENING     12542    /tmp/orbit-jon/linc-1396-0-6c6558355631f
unix  2      [ ACC ]     STREAM     LISTENING     12597    /tmp/orbit-jon/linc-139a-0-56d08fa82f3de
unix  2      [ ACC ]     STREAM     LISTENING     12679    /tmp/orbit-jon/linc-13d0-0-cd57ea0aaf09
unix  2      [ ACC ]     STREAM     LISTENING     12691    /tmp/orbit-jon/linc-13d8-0-cd57ea0b4b64
unix  2      [ ACC ]     STREAM     LISTENING     12757    /tmp/orbit-jon/linc-13e1-0-7e4915b11773f
unix  2      [ ACC ]     STREAM     LISTENING     12797    /tmp/orbit-jon/linc-1426-0-5704f7a54245a
unix  2      [ ACC ]     STREAM     LISTENING     4571     @/com/ubuntu/upstart/logd
unix  2      [ ACC ]     STREAM     LISTENING     12832    /tmp/orbit-jon/linc-141e-0-7e4915b16c419
unix  2      [ ACC ]     STREAM     LISTENING     12930    /tmp/orbit-jon/linc-1423-0-7e4915b1bb14b
unix  2      [ ACC ]     STREAM     LISTENING     12945    /tmp/orbit-jon/linc-143d-0-7e4915b1c2877
unix  2      [ ACC ]     STREAM     LISTENING     13012    /tmp/orbit-jon/linc-1490-0-200d9707483fb
unix  2      [ ACC ]     STREAM     LISTENING     13141    /tmp/orbit-jon/linc-1432-0-200d9707e74eb
unix  2      [ ACC ]     STREAM     LISTENING     13182    /tmp/orbit-jon/linc-14cf-0-52428e7283d9e
unix  2      [ ACC ]     STREAM     LISTENING     13216    /tmp/orbit-jon/linc-14d8-0-43666c373015
unix  2      [ ACC ]     STREAM     LISTENING     13466    /tmp/orbit-jon/linc-155a-0-18b814db51588
unix  2      [ ACC ]     STREAM     LISTENING     13679    /tmp/orbit-jon/linc-15cf-0-53b12982e850a
unix  2      [ ACC ]     STREAM     LISTENING     38020    /tmp/orbit-jon/linc-1b4e-0-580406e27f5d2
unix  2      [ ]         DGRAM                    240274   
unix  3      [ ]         STREAM     CONNECTED     240271   
unix  3      [ ]         STREAM     CONNECTED     240270   
unix  2      [ ]         DGRAM                    239934   
unix  2      [ ]         DGRAM                    156313   
unix  2      [ ]         DGRAM                    149955   
unix  3      [ ]         STREAM     CONNECTED     149950   
unix  3      [ ]         STREAM     CONNECTED     149949   
unix  3      [ ]         STREAM     CONNECTED     149948   
unix  3      [ ]         STREAM     CONNECTED     149947   
unix  3      [ ]         STREAM     CONNECTED     149946   
unix  3      [ ]         STREAM     CONNECTED     149945   
unix  3      [ ]         STREAM     CONNECTED     149944   
unix  3      [ ]         STREAM     CONNECTED     149943   
unix  3      [ ]         STREAM     CONNECTED     149942   
unix  3      [ ]         STREAM     CONNECTED     149941   
unix  3      [ ]         STREAM     CONNECTED     149940   
unix  3      [ ]         STREAM     CONNECTED     149939   
unix  3      [ ]         STREAM     CONNECTED     149938   
unix  3      [ ]         STREAM     CONNECTED     149937   
unix  3      [ ]         STREAM     CONNECTED     149936   
unix  3      [ ]         STREAM     CONNECTED     149935   
unix  3      [ ]         STREAM     CONNECTED     149934   
unix  3      [ ]         STREAM     CONNECTED     149933   
unix  3      [ ]         STREAM     CONNECTED     149932   
unix  3      [ ]         STREAM     CONNECTED     149931   
unix  3      [ ]         STREAM     CONNECTED     149930   
unix  3      [ ]         STREAM     CONNECTED     149929   
unix  3      [ ]         STREAM     CONNECTED     149928   
unix  3      [ ]         STREAM     CONNECTED     149927   
unix  3      [ ]         STREAM     CONNECTED     149926   
unix  3      [ ]         STREAM     CONNECTED     149925   
unix  3      [ ]         STREAM     CONNECTED     149924   
unix  3      [ ]         STREAM     CONNECTED     149923   
unix  3      [ ]         STREAM     CONNECTED     149922   
unix  3      [ ]         STREAM     CONNECTED     149921   
unix  3      [ ]         STREAM     CONNECTED     149920   
unix  3      [ ]         STREAM     CONNECTED     149919   
unix  3      [ ]         STREAM     CONNECTED     149918   
unix  3      [ ]         STREAM     CONNECTED     149917   
unix  3      [ ]         STREAM     CONNECTED     149916   
unix  3      [ ]         STREAM     CONNECTED     149915   
unix  3      [ ]         STREAM     CONNECTED     149914   
unix  3      [ ]         STREAM     CONNECTED     149913   
unix  3      [ ]         STREAM     CONNECTED     149912   
unix  3      [ ]         STREAM     CONNECTED     149911   
unix  3      [ ]         STREAM     CONNECTED     149910   
unix  3      [ ]         STREAM     CONNECTED     149909   
unix  3      [ ]         STREAM     CONNECTED     149908   
unix  3      [ ]         STREAM     CONNECTED     149907   
unix  3      [ ]         STREAM     CONNECTED     149906   
unix  3      [ ]         STREAM     CONNECTED     149905   
unix  3      [ ]         STREAM     CONNECTED     149904   
unix  3      [ ]         STREAM     CONNECTED     149903   
unix  3      [ ]         STREAM     CONNECTED     149902   
unix  3      [ ]         STREAM     CONNECTED     149901   
unix  3      [ ]         STREAM     CONNECTED     149900   
unix  3      [ ]         STREAM     CONNECTED     149899   
unix  3      [ ]         STREAM     CONNECTED     149898   
unix  3      [ ]         STREAM     CONNECTED     149897   
unix  3      [ ]         STREAM     CONNECTED     149896   
unix  3      [ ]         STREAM     CONNECTED     149895   
unix  2      [ ]         DGRAM                    149747   
unix  2      [ ]         DGRAM                    149356   
unix  2      [ ]         DGRAM                    128006   
unix  2      [ ]         DGRAM                    126480   
unix  3      [ ]         STREAM     CONNECTED     123489   
unix  3      [ ]         STREAM     CONNECTED     123488   
unix  3      [ ]         STREAM     CONNECTED     123487   
unix  3      [ ]         STREAM     CONNECTED     123486   
unix  3      [ ]         STREAM     CONNECTED     123484   
unix  3      [ ]         STREAM     CONNECTED     123483   
unix  3      [ ]         STREAM     CONNECTED     123482   
unix  3      [ ]         STREAM     CONNECTED     123481   
unix  3      [ ]         STREAM     CONNECTED     123480   
unix  3      [ ]         STREAM     CONNECTED     123479   
unix  2      [ ]         DGRAM                    123447   
unix  3      [ ]         STREAM     CONNECTED     38025    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     38024    
unix  3      [ ]         STREAM     CONNECTED     38023    /tmp/orbit-jon/linc-1b4e-0-580406e27f5d2
unix  3      [ ]         STREAM     CONNECTED     38022    
unix  3      [ ]         STREAM     CONNECTED     38019    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     38018    
unix  3      [ ]         STREAM     CONNECTED     38014    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     38013    
unix  3      [ ]         STREAM     CONNECTED     37584    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     37583    
unix  3      [ ]         STREAM     CONNECTED     13686    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13685    
unix  3      [ ]         STREAM     CONNECTED     13684    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     13683    
unix  3      [ ]         STREAM     CONNECTED     13682    /tmp/orbit-jon/linc-15cf-0-53b12982e850a
unix  3      [ ]         STREAM     CONNECTED     13681    
unix  3      [ ]         STREAM     CONNECTED     13678    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     13677    
unix  3      [ ]         STREAM     CONNECTED     13673    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13672    
unix  2      [ ]         DGRAM                    13649    
unix  2      [ ]         DGRAM                    13645    
unix  3      [ ]         STREAM     CONNECTED     13594    /tmp/orbit-jon/linc-13d0-0-cd57ea0aaf09
unix  3      [ ]         STREAM     CONNECTED     13593    
unix  3      [ ]         STREAM     CONNECTED     13592    /tmp/orbit-jon/linc-155a-0-18b814db51588
unix  3      [ ]         STREAM     CONNECTED     13591    
unix  3      [ ]         STREAM     CONNECTED     13473    /tmp/orbit-jon/linc-155a-0-18b814db51588
unix  3      [ ]         STREAM     CONNECTED     13472    
unix  3      [ ]         STREAM     CONNECTED     13471    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     13470    
unix  3      [ ]         STREAM     CONNECTED     13469    /tmp/orbit-jon/linc-155a-0-18b814db51588
unix  3      [ ]         STREAM     CONNECTED     13468    
unix  3      [ ]         STREAM     CONNECTED     13465    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     13464    
unix  3      [ ]         STREAM     CONNECTED     13460    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13459    
unix  3      [ ]         STREAM     CONNECTED     13232    /tmp/orbit-jon/linc-1432-0-200d9707e74eb
unix  3      [ ]         STREAM     CONNECTED     13231    
unix  3      [ ]         STREAM     CONNECTED     13230    /tmp/orbit-jon/linc-14cf-0-52428e7283d9e
unix  3      [ ]         STREAM     CONNECTED     13229    
unix  3      [ ]         STREAM     CONNECTED     13226    /tmp/orbit-jon/linc-14d8-0-43666c373015
unix  3      [ ]         STREAM     CONNECTED     13225    
unix  3      [ ]         STREAM     CONNECTED     13224    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     13223    
unix  3      [ ]         STREAM     CONNECTED     13219    /tmp/orbit-jon/linc-14d8-0-43666c373015
unix  3      [ ]         STREAM     CONNECTED     13218    
unix  3      [ ]         STREAM     CONNECTED     13215    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     13214    
unix  3      [ ]         STREAM     CONNECTED     13212    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     13211    
unix  3      [ ]         STREAM     CONNECTED     13207    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13206    
unix  3      [ ]         STREAM     CONNECTED     13197    /tmp/orbit-jon/linc-14cf-0-52428e7283d9e
unix  3      [ ]         STREAM     CONNECTED     13196    
unix  3      [ ]         STREAM     CONNECTED     13195    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     13194    
unix  3      [ ]         STREAM     CONNECTED     13190    /tmp/mapping-jon
unix  3      [ ]         STREAM     CONNECTED     13185    /tmp/orbit-jon/linc-14cf-0-52428e7283d9e
unix  3      [ ]         STREAM     CONNECTED     13184    
unix  3      [ ]         STREAM     CONNECTED     13181    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     13180    
unix  3      [ ]         STREAM     CONNECTED     13171    
unix  3      [ ]         STREAM     CONNECTED     13160    /tmp/orbit-jon/linc-1432-0-200d9707e74eb
unix  3      [ ]         STREAM     CONNECTED     13159    
unix  3      [ ]         STREAM     CONNECTED     13158    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     13157    
unix  3      [ ]         STREAM     CONNECTED     13156    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     13155    
unix  3      [ ]         STREAM     CONNECTED     13144    /tmp/orbit-jon/linc-1432-0-200d9707e74eb
unix  3      [ ]         STREAM     CONNECTED     13143    
unix  3      [ ]         STREAM     CONNECTED     13140    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     13139    
unix  3      [ ]         STREAM     CONNECTED     13137    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     13136    
unix  3      [ ]         STREAM     CONNECTED     13124    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13123    
unix  3      [ ]         STREAM     CONNECTED     13093    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13092    
unix  3      [ ]         STREAM     CONNECTED     13078    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13077    
unix  3      [ ]         STREAM     CONNECTED     13061    /tmp/orbit-jon/linc-13d0-0-cd57ea0aaf09
unix  3      [ ]         STREAM     CONNECTED     13060    
unix  3      [ ]         STREAM     CONNECTED     13059    /tmp/orbit-jon/linc-1490-0-200d9707483fb
unix  3      [ ]         STREAM     CONNECTED     13058    
unix  2      [ ]         DGRAM                    13042    
unix  3      [ ]         STREAM     CONNECTED     13034    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     13033    
unix  3      [ ]         STREAM     CONNECTED     13025    /tmp/orbit-jon/linc-1490-0-200d9707483fb
unix  3      [ ]         STREAM     CONNECTED     13024    
unix  3      [ ]         STREAM     CONNECTED     13022    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     13021    
unix  3      [ ]         STREAM     CONNECTED     13015    /tmp/orbit-jon/linc-1490-0-200d9707483fb
unix  3      [ ]         STREAM     CONNECTED     13014    
unix  3      [ ]         STREAM     CONNECTED     13011    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     13010    
unix  3      [ ]         STREAM     CONNECTED     13006    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13005    
unix  3      [ ]         STREAM     CONNECTED     12986    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     12985    
unix  3      [ ]         STREAM     CONNECTED     12982    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     12981    
unix  3      [ ]         STREAM     CONNECTED     12980    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12979    
unix  2      [ ]         DGRAM                    12978    
unix  3      [ ]         STREAM     CONNECTED     12967    /tmp/orbit-jon/linc-1423-0-7e4915b1bb14b
unix  3      [ ]         STREAM     CONNECTED     12966    
unix  3      [ ]         STREAM     CONNECTED     12965    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     12964    
unix  3      [ ]         STREAM     CONNECTED     12951    /tmp/orbit-jon/linc-143d-0-7e4915b1c2877
unix  3      [ ]         STREAM     CONNECTED     12950    
unix  2      [ ]         DGRAM                    12949    
unix  3      [ ]         STREAM     CONNECTED     12944    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12943    
unix  3      [ ]         STREAM     CONNECTED     12941    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     12940    
unix  3      [ ]         STREAM     CONNECTED     12933    /tmp/orbit-jon/linc-1423-0-7e4915b1bb14b
unix  3      [ ]         STREAM     CONNECTED     12932    
unix  3      [ ]         STREAM     CONNECTED     12929    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12928    
unix  3      [ ]         STREAM     CONNECTED     12926    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     12925    
unix  3      [ ]         STREAM     CONNECTED     12918    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12917    
unix  3      [ ]         STREAM     CONNECTED     12904    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12903    
unix  2      [ ]         DGRAM                    12899    
unix  3      [ ]         STREAM     CONNECTED     12893    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12891    
unix  2      [ ]         DGRAM                    12881    
unix  3      [ ]         STREAM     CONNECTED     12868    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12867    
unix  3      [ ]         STREAM     CONNECTED     12837    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     12836    
unix  3      [ ]         STREAM     CONNECTED     12835    /tmp/orbit-jon/linc-141e-0-7e4915b16c419
unix  3      [ ]         STREAM     CONNECTED     12834    
unix  3      [ ]         STREAM     CONNECTED     12831    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12830    
unix  3      [ ]         STREAM     CONNECTED     12829    /tmp/orbit-jon/linc-13e1-0-7e4915b11773f
unix  3      [ ]         STREAM     CONNECTED     12828    
unix  3      [ ]         STREAM     CONNECTED     12827    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     12826    
unix  3      [ ]         STREAM     CONNECTED     12825    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     12819    
unix  3      [ ]         STREAM     CONNECTED     12811    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12810    
unix  3      [ ]         STREAM     CONNECTED     12802    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12801    
unix  3      [ ]         STREAM     CONNECTED     12800    /tmp/orbit-jon/linc-1426-0-5704f7a54245a
unix  3      [ ]         STREAM     CONNECTED     12799    
unix  3      [ ]         STREAM     CONNECTED     12796    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12795    
unix  3      [ ]         STREAM     CONNECTED     12790    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     12789    
unix  3      [ ]         STREAM     CONNECTED     12774    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     12772    
unix  3      [ ]         STREAM     CONNECTED     12760    /tmp/orbit-jon/linc-13e1-0-7e4915b11773f
unix  3      [ ]         STREAM     CONNECTED     12759    
unix  3      [ ]         STREAM     CONNECTED     12756    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12755    
unix  3      [ ]         STREAM     CONNECTED     12753    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     12752    
unix  3      [ ]         STREAM     CONNECTED     12740    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12739    
unix  3      [ ]         STREAM     CONNECTED     12729    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     12728    
unix  3      [ ]         STREAM     CONNECTED     12719    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12718    
unix  3      [ ]         STREAM     CONNECTED     12697    /tmp/orbit-jon/linc-13d0-0-cd57ea0aaf09
unix  3      [ ]         STREAM     CONNECTED     12696    
unix  3      [ ]         STREAM     CONNECTED     12694    /tmp/orbit-jon/linc-13d8-0-cd57ea0b4b64
unix  3      [ ]         STREAM     CONNECTED     12693    
unix  3      [ ]         STREAM     CONNECTED     12695    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     12690    
unix  3      [ ]         STREAM     CONNECTED     12689    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12688    
unix  3      [ ]         STREAM     CONNECTED     12687    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     12686    
unix  3      [ ]         STREAM     CONNECTED     12682    /tmp/orbit-jon/linc-13d0-0-cd57ea0aaf09
unix  3      [ ]         STREAM     CONNECTED     12681    
unix  3      [ ]         STREAM     CONNECTED     12678    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12677    
unix  3      [ ]         STREAM     CONNECTED     12676    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12675    
unix  3      [ ]         STREAM     CONNECTED     12674    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     12673    
unix  3      [ ]         STREAM     CONNECTED     12667    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12666    
unix  3      [ ]         STREAM     CONNECTED     12630    /tmp/.ICE-unix/4058
unix  3      [ ]         STREAM     CONNECTED     12629    
unix  3      [ ]         STREAM     CONNECTED     12628    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12627    
unix  3      [ ]         STREAM     CONNECTED     12600    /tmp/orbit-jon/linc-139a-0-56d08fa82f3de
unix  3      [ ]         STREAM     CONNECTED     12599    
unix  3      [ ]         STREAM     CONNECTED     12596    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12595    
unix  3      [ ]         STREAM     CONNECTED     13101    /tmp/orbit-jon/linc-1396-0-6c6558355631f
unix  3      [ ]         STREAM     CONNECTED     12575    
unix  3      [ ]         STREAM     CONNECTED     12549    /tmp/orbit-jon/linc-1396-0-6c6558355631f
unix  3      [ ]         STREAM     CONNECTED     12548    
unix  3      [ ]         STREAM     CONNECTED     12547    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     12546    
unix  3      [ ]         STREAM     CONNECTED     12545    /tmp/orbit-jon/linc-1396-0-6c6558355631f
unix  3      [ ]         STREAM     CONNECTED     12544    
unix  3      [ ]         STREAM     CONNECTED     12541    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     12540    
unix  3      [ ]         STREAM     CONNECTED     12536    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12535    
unix  3      [ ]         STREAM     CONNECTED     12525    /tmp/orbit-jon/linc-fda-0-66f510294353e
unix  3      [ ]         STREAM     CONNECTED     12524    
unix  3      [ ]         STREAM     CONNECTED     12523    /tmp/orbit-jon/linc-1391-0-72acf9aa14bd8
unix  3      [ ]         STREAM     CONNECTED     12522    
unix  2      [ ]         DGRAM                    11393    
unix  2      [ ]         DGRAM                    10952    
unix  3      [ ]         STREAM     CONNECTED     10574    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     10573    
unix  3      [ ]         STREAM     CONNECTED     10565    /tmp/orbit-jon/linc-10e3-0-5aeaa0955f694
unix  3      [ ]         STREAM     CONNECTED     10564    
unix  3      [ ]         STREAM     CONNECTED     10561    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     10560    
unix  3      [ ]         STREAM     CONNECTED     10545    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10544    
unix  3      [ ]         STREAM     CONNECTED     10486    @/tmp/dbus-mlVCOda1qN
unix  3      [ ]         STREAM     CONNECTED     10485    
unix  2      [ ]         DGRAM                    10304    
unix  3      [ ]         STREAM     CONNECTED     10298    /tmp/orbit-jon/linc-fda-0-66f510294353e
unix  3      [ ]         STREAM     CONNECTED     10297    
unix  3      [ ]         STREAM     CONNECTED     10296    /tmp/orbit-jon/linc-10be-0-63ace1d324e17
unix  3      [ ]         STREAM     CONNECTED     10129    
unix  2      [ ]         DGRAM                    10110    
unix  3      [ ]         STREAM     CONNECTED     10099    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10098    
unix  3      [ ]         STREAM     CONNECTED     10036    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10035    
unix  3      [ ]         STREAM     CONNECTED     10034    
unix  3      [ ]         STREAM     CONNECTED     10033    
unix  2      [ ]         DGRAM                    9883     
unix  5      [ ]         STREAM     CONNECTED     9889     /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9766     
unix  3      [ ]         STREAM     CONNECTED     9651     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9650     
unix  3      [ ]         STREAM     CONNECTED     9642     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9641     
unix  3      [ ]         STREAM     CONNECTED     9643     @/tmp/hald-local/dbus-v30NZaMdF5
unix  3      [ ]         STREAM     CONNECTED     9640     
unix  3      [ ]         STREAM     CONNECTED     9614     @/tmp/hald-local/dbus-v30NZaMdF5
unix  3      [ ]         STREAM     CONNECTED     9609     
unix  3      [ ]         STREAM     CONNECTED     8430     @/tmp/hald-runner/dbus-8bNqMT7Ml8
unix  3      [ ]         STREAM     CONNECTED     8429     
unix  3      [ ]         STREAM     CONNECTED     8411     
unix  3      [ ]         STREAM     CONNECTED     8410     [/PHP]

---

### Post by koenn on 2007-07-24
You probably have a trojan using port 666, [http://www.seifried.org/security/ports/0/666.html](http://www.seifried.org/security/ports/0/666.html) , or someone 's using you as a server for Doom (also port 666). You ought to start worrying.

---

### Post by murraymca on 2007-07-24
Perhaps you could check the mysql and dns logs...or for peace of mind the best thing is to just blow it all away (if you are worried...) and start fresh - that's the best way to make sure...

You could run pstree and see if you notice anything out of the ordinary.

---

### Post by Modernity on 2007-07-24
Is 192.168.10.1 your router? Looks like they were able to access to it.

---

### Post by twistedtwig on 2007-07-25
the modem passes the ip address to the server which is eth0.  eth1 the internal network card is eth1 which is static as 192.168.10.1

I have come to the conclusion fresh install would be best as well. Just making sure I have everything backed up.. ie.. etc folder and all media etc.

---

