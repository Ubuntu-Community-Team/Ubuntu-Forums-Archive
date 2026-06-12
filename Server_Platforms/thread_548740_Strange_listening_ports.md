---
title: "Strange listening ports"
date: 2007-09-11
forum: Server Platforms
---

### Post by shiko332 on 2007-09-11
Hi everyone !

I've just discovered that my Ubuntu Feisty has a BUNCH of listening ports. It is really strange, because the are bound to processes like gnome-terminal or firefox-bin.
I searched thorougly this forums and googled about it, but I can't find anything.

If I do a 'netstat -lnp' I get the following:

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     4983/hpiod          
tcp        0      0 127.0.0.1:39265         0.0.0.0:*               LISTEN     5891/gdl_indexer    
tcp        0      0 0.0.0.0:41409           0.0.0.0:*               LISTEN     5869/gnome-cups-ico 
tcp        0      0 0.0.0.0:40641           0.0.0.0:*               LISTEN     5618/bonobo-activat 
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:46338           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:36517           0.0.0.0:*               LISTEN     5594/gnome-panel    
tcp        0      0 0.0.0.0:56166           0.0.0.0:*               LISTEN     5161/gconfd-2       
tcp        0      0 0.0.0.0:42057           0.0.0.0:*               LISTEN     6039/mixer_applet2  
tcp        0      0 0.0.0.0:45131           0.0.0.0:*               LISTEN     5645/gnome-volume-m 
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     5319/smbd           
tcp        0      0 0.0.0.0:45677           0.0.0.0:*               LISTEN     5454/rpc.statd      
tcp        0      0 0.0.0.0:43343           0.0.0.0:*               LISTEN     6586/evolution      
tcp        0      0 0.0.0.0:43567           0.0.0.0:*               LISTEN     5986/gnome-screensa 
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4078/portmap        
tcp        0      0 0.0.0.0:53936           0.0.0.0:*               LISTEN     21290/ekiga         
tcp        0      0 0.0.0.0:45200           0.0.0.0:*               LISTEN     5598/nautilus       
tcp        0      0 0.0.0.0:41520           0.0.0.0:*               LISTEN     5103/x-session-mana 
tcp        0      0 0.0.0.0:47121           0.0.0.0:*               LISTEN     5954/evolution-data 
tcp        0      0 0.0.0.0:47794           0.0.0.0:*               LISTEN     5677/update-notifie 
tcp        0      0 0.0.0.0:57778           0.0.0.0:*               LISTEN     5316/gnome-settings 
tcp        0      0 0.0.0.0:55667           0.0.0.0:*               LISTEN     5580/metacity       
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     5394/vsftpd         
tcp        0      0 0.0.0.0:52663           0.0.0.0:*               LISTEN     5964/evolution-exch 
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4959/cupsd          
tcp        0      0 10.4.0.6:1720           0.0.0.0:*               LISTEN     21290/ekiga         
tcp        0      0 0.0.0.0:52184           0.0.0.0:*               LISTEN     5790/evolution-alar 
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN     5045/postgres       
tcp        0      0 0.0.0.0:793             0.0.0.0:*               LISTEN     5278/rpc.mountd     
tcp        0      0 0.0.0.0:50170           0.0.0.0:*               LISTEN     27248/firefox-bin   
tcp        0      0 0.0.0.0:52634           0.0.0.0:*               LISTEN     5670/gnome-vfs-daem 
tcp        0      0 0.0.0.0:32924           0.0.0.0:*               LISTEN     6071/gnome-terminal 
tcp        0      0 0.0.0.0:58076           0.0.0.0:*               LISTEN     5870/gnome-power-ma 
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     5319/smbd           
tcp        0      0 0.0.0.0:49567           0.0.0.0:*               LISTEN     6113/notification-d 
tcp        0      0 0.0.0.0:42591           0.0.0.0:*               LISTEN     5907/trashapplet    
tcp        0      0 0.0.0.0:43583           0.0.0.0:*               LISTEN     5839/nm-applet      
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     4996/python         
tcp6       0      0 :::22                   :::*                    LISTEN     5354/sshd           
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          4761/avahi-daemon:  
udp        0      0 0.0.0.0:2049            0.0.0.0:*                          -                   
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          -                   
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          5454/rpc.statd      
udp        0      0 172.16.52.1:137         0.0.0.0:*                          5317/nmbd           
udp        0      0 192.168.0.128:137       0.0.0.0:*                          5317/nmbd           
udp        0      0 0.0.0.0:137             0.0.0.0:*                          5317/nmbd           
udp        0      0 172.16.52.1:138         0.0.0.0:*                          5317/nmbd           
udp        0      0 192.168.0.128:138       0.0.0.0:*                          5317/nmbd           
udp        0      0 0.0.0.0:138             0.0.0.0:*                          5317/nmbd           
udp        0      0 0.0.0.0:790             0.0.0.0:*                          5278/rpc.mountd     
udp        0      0 10.4.0.6:5060           0.0.0.0:*                          21290/ekiga         
udp        0      0 0.0.0.0:68              0.0.0.0:*                          4934/dhclient       
udp        0      0 0.0.0.0:966             0.0.0.0:*                          5454/rpc.statd      
udp        0      0 0.0.0.0:5064            0.0.0.0:*                          21290/ekiga         
udp        0      0 0.0.0.0:5071            0.0.0.0:*                          21290/ekiga         
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          4761/avahi-daemon:  
udp        0      0 0.0.0.0:111             0.0.0.0:*                          4078/portmap        
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     19695    5890/gdl_config     /home/john/.google/desktop/a1_sock
unix  2      [ ACC ]     STREAM     LISTENING     20424    5892/gdl_fs_crawler /home/john/.google/desktop/a3_sock
unix  2      [ ACC ]     STREAM     LISTENING     20381    5911/mapping-daemon /tmp/mapping-john
unix  2      [ ACC ]     STREAM     LISTENING     17755    5156/dbus-daemon    @/tmp/dbus-PL3anMcgfG
unix  2      [ ACC ]     STREAM     LISTENING     16851    4793/dbus-daemon    @/tmp/dbus-NaPcEoEYSs
unix  2      [ ACC ]     STREAM     LISTENING     20636    5891/gdl_indexer    /home/john/.google/desktop/a2_sock
unix  2      [ ACC ]     STREAM     LISTENING     20789    5867/gdl_box        /home/john/.google/desktop/a4_sock
unix  2      [ ACC ]     STREAM     LISTENING     15391    4668/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     15156    4498/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     17011    4842/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     15409    4685/hald           @/var/run/hald/dbus-fagT62KjDC
unix  2      [ ACC ]     STREAM     LISTENING     17293    4959/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     16783    4761/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     17065    4848/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17744    5152/ssh-agent      /tmp/ssh-UfrkIi5103/agent.5103
unix  2      [ ACC ]     STREAM     LISTENING     17786    5161/gconfd-2       /tmp/orbit-john/linc-1429-0-3312f81526071
unix  2      [ ACC ]     STREAM     LISTENING     17818    5103/x-session-mana /tmp/orbit-john/linc-13ef-0-448024d356e23
unix  2      [ ACC ]     STREAM     LISTENING     18353    5103/x-session-mana /tmp/.ICE-unix/5103
unix  2      [ ACC ]     STREAM     LISTENING     18362    5314/gnome-keyring- /tmp/keyring-zJeJoy/socket
unix  2      [ ACC ]     STREAM     LISTENING     18414    5316/gnome-settings /tmp/orbit-john/linc-14c4-0-66b7a26c42945
unix  2      [ ACC ]     STREAM     LISTENING     18859    5580/metacity       /tmp/orbit-john/linc-15cc-0-285db7e18f7ba
unix  2      [ ACC ]     STREAM     LISTENING     18908    5594/gnome-panel    /tmp/orbit-john/linc-15da-0-74875a6367f6f
unix  2      [ ACC ]     STREAM     LISTENING     17620    5045/postgres       /var/run/postgresql/.s.PGSQL.5432
unix  2      [ ACC ]     STREAM     LISTENING     18981    5645/gnome-volume-m /tmp/orbit-john/linc-15e3-0-871701b2ff6c
unix  2      [ ACC ]     STREAM     LISTENING     19014    5598/nautilus       /tmp/orbit-john/linc-15de-0-871701b80285
unix  2      [ ACC ]     STREAM     LISTENING     19445    5618/bonobo-activat /tmp/orbit-john/linc-15f2-0-5cbb007987b26
unix  2      [ ACC ]     STREAM     LISTENING     19123    5670/gnome-vfs-daem /tmp/orbit-john/linc-1626-0-1e3815e347a48
unix  2      [ ACC ]     STREAM     LISTENING     19504    5677/update-notifie /tmp/orbit-john/linc-162d-0-7aa82185af8ec
unix  2      [ ACC ]     STREAM     LISTENING     19553    5839/nm-applet      /tmp/orbit-john/linc-16cf-0-275e8083b65e2
unix  2      [ ACC ]     STREAM     LISTENING     19567    5870/gnome-power-ma /tmp/orbit-john/linc-16ae-0-275e8084639a0
unix  2      [ ACC ]     STREAM     LISTENING     19604    5869/gnome-cups-ico /tmp/orbit-john/linc-16ed-0-7b481897244a0
unix  2      [ ACC ]     STREAM     LISTENING     19682    5790/evolution-alar /tmp/orbit-john/linc-169e-0-335cd7d7bd2ae
unix  2      [ ACC ]     STREAM     LISTENING     20437    5907/trashapplet    /tmp/orbit-john/linc-1713-0-56c33a951c3e8
unix  2      [ ACC ]     STREAM     LISTENING     20632    5954/evolution-data /tmp/orbit-john/linc-1742-0-2a7971ba779b7
unix  2      [ ACC ]     STREAM     LISTENING     20985    5964/evolution-exch /tmp/orbit-john/linc-174c-0-e843305290fc
unix  2      [ ACC ]     STREAM     LISTENING     21012    5986/gnome-screensa /tmp/orbit-john/linc-1756-0-6d2157afa0ff4
unix  2      [ ACC ]     STREAM     LISTENING     21106    6039/mixer_applet2  /tmp/orbit-john/linc-1797-0-cce436179196
unix  2      [ ACC ]     STREAM     LISTENING     21222    6071/gnome-terminal /tmp/orbit-john/linc-17b7-0-21f7b10a52c66
unix  2      [ ACC ]     STREAM     LISTENING     21320    6113/notification-d /tmp/orbit-john/linc-17e1-0-790324c7e703f
unix  2      [ ACC ]     STREAM     LISTENING     22849    6586/evolution      /tmp/orbit-john/linc-19ba-0-415ab2637f1e5
unix  2      [ ACC ]     STREAM     LISTENING     18671    5494/hcid           /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     15412    4685/hald           @/var/run/hald/dbus-DjLvY7RkEQ
unix  2      [ ACC ]     STREAM     LISTENING     98028    21290/ekiga         /tmp/orbit-john/linc-532a-0-60806feb170e
unix  2      [ ACC ]     STREAM     LISTENING     131387   27248/firefox-bin   /tmp/orbit-john/linc-6a70-0-22b0008d3caf9


```

as far as I can see, they are related to Orbit, but I've not seen before in other computers so many TCP open ports.

Must I worry ? Any hints on how can I close them ? I think not but.. am I compromised ?

Thank you very much for your time !

---

### Post by az on 2007-09-11
Those are local sockets.

To see what your computer is listening to from the network, try 

netstat -tap|grep LISTEN

---

### Post by shiko332 on 2007-09-11
I'm afraid that all those ports are listening on all interfaces (0.0.0.0)

This is the result of running 'netstat -tap|grep LISTEN'

```


tcp        0      0 localhost:2208          *:*                     LISTEN     4983/hpiod          
tcp        0      0 localhost:39265         *:*                     LISTEN     5891/gdl_indexer    
tcp        0      0 *:41409                 *:*                     LISTEN     5869/gnome-cups-ico 
tcp        0      0 *:40641                 *:*                     LISTEN     5618/bonobo-activat 
tcp        0      0 *:nfs                   *:*                     LISTEN     -                   
tcp        0      0 *:46338                 *:*                     LISTEN     -                   
tcp        0      0 *:36517                 *:*                     LISTEN     5594/gnome-panel    
tcp        0      0 *:56166                 *:*                     LISTEN     5161/gconfd-2       
tcp        0      0 *:42057                 *:*                     LISTEN     6039/mixer_applet2  
tcp        0      0 *:5801                  *:*                     LISTEN     5714/vmnet-natd     
tcp        0      0 *:45131                 *:*                     LISTEN     5645/gnome-volume-m 
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     5319/smbd           
tcp        0      0 *:5901                  *:*                     LISTEN     5714/vmnet-natd     
tcp        0      0 *:45677                 *:*                     LISTEN     5454/rpc.statd      
tcp        0      0 *:43343                 *:*                     LISTEN     6586/evolution      
tcp        0      0 *:43567                 *:*                     LISTEN     5986/gnome-screensa 
tcp        0      0 *:sunrpc                *:*                     LISTEN     4078/portmap        
tcp        0      0 *:45200                 *:*                     LISTEN     5598/nautilus       
tcp        0      0 *:41520                 *:*                     LISTEN     5103/x-session-mana 
tcp        0      0 *:47121                 *:*                     LISTEN     5954/evolution-data 
tcp        0      0 *:47794                 *:*                     LISTEN     5677/update-notifie 
tcp        0      0 *:57778                 *:*                     LISTEN     5316/gnome-settings 
tcp        0      0 *:55667                 *:*                     LISTEN     5580/metacity       
tcp        0      0 *:ftp                   *:*                     LISTEN     5394/vsftpd         
tcp        0      0 *:52663                 *:*                     LISTEN     5964/evolution-exch 
tcp        0      0 localhost:ipp           *:*                     LISTEN     4959/cupsd          
tcp        0      0 *:52184                 *:*                     LISTEN     5790/evolution-alar 
tcp        0      0 localhost:postgresql    *:*                     LISTEN     5045/postgres       
tcp        0      0 *:793                   *:*                     LISTEN     5278/rpc.mountd     
tcp        0      0 *:50170                 *:*                     LISTEN     27248/firefox-bin   
tcp        0      0 *:52634                 *:*                     LISTEN     5670/gnome-vfs-daem 
tcp        0      0 *:32924                 *:*                     LISTEN     6071/gnome-terminal 
tcp        0      0 *:58076                 *:*                     LISTEN     5870/gnome-power-ma 
tcp        0      0 *:5500                  *:*                     LISTEN     5714/vmnet-natd     
tcp        0      0 *:47997                 *:*                     LISTEN     28008/gedit         
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     5319/smbd           
tcp        0      0 *:49567                 *:*                     LISTEN     6113/notification-d 
tcp        0      0 *:42591                 *:*                     LISTEN     5907/trashapplet    
tcp        0      0 *:43583                 *:*                     LISTEN     5839/nm-applet      
tcp        0      0 localhost:2207          *:*                     LISTEN     4996/python         
tcp6       0      0 *:sip                   *:*                     LISTEN     32701/gaim          
tcp6       0      0 *:ssh                   *:*                     LISTEN     5354/sshd           



```

---

### Post by nowshining on 2007-09-11
0.0.0.0 is your machines local ip - loopback ip and the other one for IPV4 is 127.0.0.1

---

### Post by shiko332 on 2007-09-12
Thanks.

I already know what 0.0.0.0 means.  :)

The original post was because that I dont really know why there are SO MANY listening ports on my machine.

Please, any hints ? Must I worry about it ?

---

### Post by nowshining on 2007-09-12
if it makes you feel any better.. :)


```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 dialup-4.245.99.8:60163 8.12.96.25:www          ESTABLISHED
tcp        0      0 dialup-4.245.99.8:44395 profileedit.myspace:www ESTABLISHED
tcp        0      0 dialup-4.245.99.8:42150 8.12.96.33:www          ESTABLISHED
tcp        0      0 dialup-4.245.99.8:44380 profileedit.myspace:www ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    8154     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    8436     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    16752    @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     29833    
unix  3      [ ]         STREAM     CONNECTED     29832    
unix  3      [ ]         STREAM     CONNECTED     29830    /tmp/orbit-nowshining/linc-1451-0-3b165226552ca
unix  3      [ ]         STREAM     CONNECTED     29829    
unix  3      [ ]         STREAM     CONNECTED     29828    /tmp/orbit-nowshining/linc-12f9-0-3524495f39609
unix  3      [ ]         STREAM     CONNECTED     29827    
unix  3      [ ]         STREAM     CONNECTED     29826    /tmp/orbit-nowshining/linc-1451-0-3b165226552ca
unix  3      [ ]         STREAM     CONNECTED     29825    
unix  3      [ ]         STREAM     CONNECTED     29822    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     29821    
unix  3      [ ]         STREAM     CONNECTED     29815    /tmp/.ICE-unix/4783
unix  3      [ ]         STREAM     CONNECTED     29814    
unix  3      [ ]         STREAM     CONNECTED     29810    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29809    
unix  2      [ ]         DGRAM                    27172    
unix  3      [ ]         STREAM     CONNECTED     21417    /tmp/orbit-nowshining/linc-13dc-0-2b61976e380d2
unix  3      [ ]         STREAM     CONNECTED     21416    
unix  3      [ ]         STREAM     CONNECTED     21413    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     21412    
unix  3      [ ]         STREAM     CONNECTED     21389    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21388    
unix  3      [ ]         STREAM     CONNECTED     20953    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     20952    
unix  3      [ ]         STREAM     CONNECTED     20670    /tmp/.ICE-unix/dcop5012-1189584482
unix  3      [ ]         STREAM     CONNECTED     20669    
unix  3      [ ]         STREAM     CONNECTED     20637    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     20636    
unix  3      [ ]         STREAM     CONNECTED     20495    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20494    
unix  3      [ ]         STREAM     CONNECTED     20489    /tmp/.ICE-unix/dcop5012-1189584482
unix  3      [ ]         STREAM     CONNECTED     20488    
unix  3      [ ]         STREAM     CONNECTED     20481    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20480    
unix  3      [ ]         STREAM     CONNECTED     20471    /tmp/.ICE-unix/dcop5012-1189584482
unix  3      [ ]         STREAM     CONNECTED     20470    
unix  3      [ ]         STREAM     CONNECTED     20468    
unix  3      [ ]         STREAM     CONNECTED     20467    
unix  3      [ ]         STREAM     CONNECTED     20416    /tmp/orbit-nowshining/linc-12f5-0-70a72d7a42d19
unix  3      [ ]         STREAM     CONNECTED     20415    
unix  3      [ ]         STREAM     CONNECTED     20414    /tmp/orbit-nowshining/linc-1387-0-7fae190144e59
unix  3      [ ]         STREAM     CONNECTED     20413    
unix  3      [ ]         STREAM     CONNECTED     20401    /tmp/orbit-nowshining/linc-1387-0-7fae190144e59
unix  3      [ ]         STREAM     CONNECTED     20400    
unix  3      [ ]         STREAM     CONNECTED     20399    /tmp/orbit-nowshining/linc-12f9-0-3524495f39609
unix  3      [ ]         STREAM     CONNECTED     20398    
unix  3      [ ]         STREAM     CONNECTED     20397    /tmp/orbit-nowshining/linc-1387-0-7fae190144e59
unix  3      [ ]         STREAM     CONNECTED     20396    
unix  3      [ ]         STREAM     CONNECTED     20393    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     20392    
unix  3      [ ]         STREAM     CONNECTED     20388    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20387    
unix  3      [ ]         STREAM     CONNECTED     20372    /tmp/orbit-nowshining/linc-12f5-0-70a72d7a42d19
unix  3      [ ]         STREAM     CONNECTED     20371    
unix  3      [ ]         STREAM     CONNECTED     20370    /tmp/orbit-nowshining/linc-137f-0-c411bedd1cc1
unix  3      [ ]         STREAM     CONNECTED     20369    
unix  3      [ ]         STREAM     CONNECTED     20362    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     20361    
unix  3      [ ]         STREAM     CONNECTED     20360    /tmp/orbit-nowshining/linc-137f-0-c411bedd1cc1
unix  3      [ ]         STREAM     CONNECTED     20359    
unix  3      [ ]         STREAM     CONNECTED     20358    /tmp/orbit-nowshining/linc-12f9-0-3524495f39609
unix  3      [ ]         STREAM     CONNECTED     20357    
unix  3      [ ]         STREAM     CONNECTED     20356    /tmp/orbit-nowshining/linc-137f-0-c411bedd1cc1
unix  3      [ ]         STREAM     CONNECTED     20355    
unix  3      [ ]         STREAM     CONNECTED     20352    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     20351    
unix  3      [ ]         STREAM     CONNECTED     20346    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20345    
unix  3      [ ]         STREAM     CONNECTED     19411    /tmp/orbit-nowshining/linc-12f5-0-70a72d7a42d19
unix  3      [ ]         STREAM     CONNECTED     19410    
unix  3      [ ]         STREAM     CONNECTED     19409    /tmp/orbit-nowshining/linc-1375-0-28688fd7d2c6b
unix  3      [ ]         STREAM     CONNECTED     19408    
unix  3      [ ]         STREAM     CONNECTED     19401    /tmp/orbit-nowshining/linc-1375-0-28688fd7d2c6b
unix  3      [ ]         STREAM     CONNECTED     19400    
unix  3      [ ]         STREAM     CONNECTED     19399    /tmp/orbit-nowshining/linc-12f9-0-3524495f39609
unix  3      [ ]         STREAM     CONNECTED     19398    
unix  3      [ ]         STREAM     CONNECTED     19397    /tmp/orbit-nowshining/linc-1375-0-28688fd7d2c6b
unix  3      [ ]         STREAM     CONNECTED     19396    
unix  3      [ ]         STREAM     CONNECTED     19393    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     19392    
unix  3      [ ]         STREAM     CONNECTED     19387    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19386    
unix  3      [ ]         STREAM     CONNECTED     19373    /tmp/mapping-nowshining
unix  3      [ ]         STREAM     CONNECTED     19365    
unix  3      [ ]         STREAM     CONNECTED     19360    /tmp/.ICE-unix/4783
unix  3      [ ]         STREAM     CONNECTED     19359    
unix  3      [ ]         STREAM     CONNECTED     19340    /tmp/orbit-nowshining/linc-12f5-0-70a72d7a42d19
unix  3      [ ]         STREAM     CONNECTED     19339    
unix  3      [ ]         STREAM     CONNECTED     19338    /tmp/orbit-nowshining/linc-1369-0-47a53b797613
unix  3      [ ]         STREAM     CONNECTED     19337    
unix  3      [ ]         STREAM     CONNECTED     19342    /tmp/.ICE-unix/4783
unix  3      [ ]         STREAM     CONNECTED     19332    
unix  3      [ ]         STREAM     CONNECTED     19329    /tmp/orbit-nowshining/linc-1369-0-47a53b797613
unix  3      [ ]         STREAM     CONNECTED     19328    
unix  3      [ ]         STREAM     CONNECTED     19327    /tmp/orbit-nowshining/linc-12f9-0-3524495f39609
unix  3      [ ]         STREAM     CONNECTED     19326    
unix  3      [ ]         STREAM     CONNECTED     19325    /tmp/orbit-nowshining/linc-1369-0-47a53b797613
unix  3      [ ]         STREAM     CONNECTED     19324    
unix  3      [ ]         STREAM     CONNECTED     19321    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     19320    
unix  3      [ ]         STREAM     CONNECTED     19316    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19315    
unix  3      [ ]         STREAM     CONNECTED     19304    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19303    
unix  3      [ ]         DGRAM                    19301    
unix  3      [ ]         DGRAM                    19300    
unix  3      [ ]         STREAM     CONNECTED     19299    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19298    
unix  3      [ ]         STREAM     CONNECTED     19283    /tmp/orbit-nowshining/linc-12f7-0-62df158510ae1
unix  3      [ ]         STREAM     CONNECTED     19282    
unix  3      [ ]         STREAM     CONNECTED     19281    /tmp/orbit-nowshining/linc-12f9-0-3524495f39609
unix  3      [ ]         STREAM     CONNECTED     19280    
unix  3      [ ]         STREAM     CONNECTED     19275    /tmp/orbit-nowshining/linc-12f5-0-70a72d7a42d19
unix  3      [ ]         STREAM     CONNECTED     19274    
unix  3      [ ]         STREAM     CONNECTED     19273    /tmp/orbit-nowshining/linc-12f9-0-3524495f39609
unix  3      [ ]         STREAM     CONNECTED     19272    
unix  3      [ ]         STREAM     CONNECTED     19082    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19081    
unix  3      [ ]         STREAM     CONNECTED     19076    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     19075    
unix  3      [ ]         STREAM     CONNECTED     19073    /tmp/orbit-nowshining/linc-1312-0-54ffef0386074
unix  3      [ ]         STREAM     CONNECTED     19072    
unix  3      [ ]         STREAM     CONNECTED     19069    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     19068    
unix  3      [ ]         STREAM     CONNECTED     19067    /tmp/.ICE-unix/4783
unix  3      [ ]         STREAM     CONNECTED     19045    
unix  3      [ ]         STREAM     CONNECTED     19041    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19040    
unix  3      [ ]         STREAM     CONNECTED     19037    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19036    
unix  3      [ ]         STREAM     CONNECTED     19035    /tmp/orbit-nowshining/linc-1318-0-3f4301a52ddae
unix  3      [ ]         STREAM     CONNECTED     19034    
unix  3      [ ]         STREAM     CONNECTED     19031    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     19030    
unix  3      [ ]         STREAM     CONNECTED     19027    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     19026    
unix  3      [ ]         STREAM     CONNECTED     19009    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     19008    
unix  3      [ ]         STREAM     CONNECTED     19004    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19003    
unix  3      [ ]         STREAM     CONNECTED     19002    /tmp/orbit-nowshining/linc-1314-0-62df158541f2b
unix  3      [ ]         STREAM     CONNECTED     19001    
unix  3      [ ]         STREAM     CONNECTED     18998    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     18997    
unix  3      [ ]         STREAM     CONNECTED     18985    /tmp/orbit-nowshining/linc-12f7-0-62df158510ae1
unix  3      [ ]         STREAM     CONNECTED     18984    
unix  3      [ ]         STREAM     CONNECTED     18981    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     18980    
unix  3      [ ]         STREAM     CONNECTED     18978    /tmp/.ICE-unix/4783
unix  3      [ ]         STREAM     CONNECTED     18977    
unix  3      [ ]         STREAM     CONNECTED     18973    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18972    
unix  3      [ ]         STREAM     CONNECTED     18911    /tmp/.ICE-unix/4783
unix  3      [ ]         STREAM     CONNECTED     18910    
unix  3      [ ]         STREAM     CONNECTED     18879    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     18878    
unix  3      [ ]         STREAM     CONNECTED     18876    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18875    
unix  3      [ ]         STREAM     CONNECTED     18873    /tmp/orbit-nowshining/linc-12f6-0-70a72d7a50e1a
unix  3      [ ]         STREAM     CONNECTED     18872    
unix  3      [ ]         STREAM     CONNECTED     18869    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     18868    
unix  3      [ ]         STREAM     CONNECTED     18867    /tmp/.ICE-unix/4783
unix  3      [ ]         STREAM     CONNECTED     18866    
unix  3      [ ]         STREAM     CONNECTED     18857    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18856    
unix  3      [ ]         STREAM     CONNECTED     18851    /tmp/orbit-nowshining/linc-12f5-0-70a72d7a42d19
unix  3      [ ]         STREAM     CONNECTED     18850    
unix  3      [ ]         STREAM     CONNECTED     18847    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     18846    
unix  3      [ ]         STREAM     CONNECTED     18845    /tmp/.ICE-unix/4783
unix  3      [ ]         STREAM     CONNECTED     18844    
unix  3      [ ]         STREAM     CONNECTED     18840    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18839    
unix  3      [ ]         STREAM     CONNECTED     18834    /tmp/orbit-nowshining/linc-12f4-0-7a8d68502321c
unix  3      [ ]         STREAM     CONNECTED     18833    
unix  3      [ ]         STREAM     CONNECTED     18830    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     18829    
unix  3      [ ]         STREAM     CONNECTED     18825    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18824    
unix  3      [ ]         STREAM     CONNECTED     18816    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18815    
unix  3      [ ]         STREAM     CONNECTED     18814    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     18813    
unix  3      [ ]         STREAM     CONNECTED     18812    /tmp/orbit-nowshining/linc-12ee-0-35df3af1b8a1f
unix  3      [ ]         STREAM     CONNECTED     18811    
unix  3      [ ]         STREAM     CONNECTED     18808    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     18807    
unix  3      [ ]         STREAM     CONNECTED     18803    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18802    
unix  2      [ ]         STREAM                   18778    
unix  4      [ ]         STREAM     CONNECTED     18757    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18756    
unix  3      [ ]         STREAM     CONNECTED     18721    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     18720    
unix  3      [ ]         STREAM     CONNECTED     18719    /tmp/orbit-nowshining/linc-12da-0-57a9a0b9807a0
unix  3      [ ]         STREAM     CONNECTED     18718    
unix  3      [ ]         STREAM     CONNECTED     18715    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     18714    
unix  3      [ ]         STREAM     CONNECTED     18710    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18709    
unix  3      [ ]         STREAM     CONNECTED     18700    @/tmp/dbus-dMPrBA3zxb
unix  3      [ ]         STREAM     CONNECTED     18699    
unix  3      [ ]         STREAM     CONNECTED     18698    
unix  3      [ ]         STREAM     CONNECTED     18697    
unix  3      [ ]         STREAM     CONNECTED     18659    /tmp/orbit-nowshining/linc-12af-0-3452abadce07f
unix  3      [ ]         STREAM     CONNECTED     18658    
unix  3      [ ]         STREAM     CONNECTED     18657    /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  3      [ ]         STREAM     CONNECTED     18500    
unix  3      [ ]         STREAM     CONNECTED     18481    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18480    
unix  3      [ ]         STREAM     CONNECTED     18418    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18417    
unix  3      [ ]         STREAM     CONNECTED     18273    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18272    
unix  4      [ ]         STREAM     CONNECTED     18345    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18214    
unix  3      [ ]         STREAM     CONNECTED     18181    @/var/run/hald/dbus-UTgGp4n5mC
unix  3      [ ]         STREAM     CONNECTED     18178    
unix  3      [ ]         STREAM     CONNECTED     18177    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18176    
unix  3      [ ]         STREAM     CONNECTED     18166    @/var/run/hald/dbus-UTgGp4n5mC
unix  3      [ ]         STREAM     CONNECTED     18165    
unix  3      [ ]         STREAM     CONNECTED     18164    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18163    
unix  3      [ ]         STREAM     CONNECTED     18114    @/var/run/hald/dbus-UTgGp4n5mC
unix  3      [ ]         STREAM     CONNECTED     18111    
unix  3      [ ]         STREAM     CONNECTED     18110    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18109    
unix  3      [ ]         STREAM     CONNECTED     17703    @/var/run/hald/dbus-UTgGp4n5mC
unix  3      [ ]         STREAM     CONNECTED     17702    
unix  3      [ ]         STREAM     CONNECTED     17699    @/var/run/hald/dbus-UTgGp4n5mC
unix  3      [ ]         STREAM     CONNECTED     17302    
unix  3      [ ]         STREAM     CONNECTED     16747    @/var/run/hald/dbus-5QrpdKC02d
unix  3      [ ]         STREAM     CONNECTED     16746    
unix  3      [ ]         STREAM     CONNECTED     16745    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16744    
unix  3      [ ]         STREAM     CONNECTED     16740    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16739    
unix  3      [ ]         STREAM     CONNECTED     16743    @/tmp/dbus-wDZLgcwGWv
unix  3      [ ]         STREAM     CONNECTED     16737    
unix  3      [ ]         STREAM     CONNECTED     16733    
unix  3      [ ]         STREAM     CONNECTED     16732    
unix  3      [ ]         STREAM     CONNECTED     16707    
unix  3      [ ]         STREAM     CONNECTED     16706   

```


and to your answer - Linux has a lot of stuff as servers so yeah I believe myself it's just things listening onto itself such as X logon server - X server - xserver is what you are using now... Yeah :) however netstat gives me a cannot identify processes what Are you running, what version Feisty or the The in Development NOT OUT yet Gutsy. I myself am a Gutsy Gibbon Tester. Some things in the permissions box say Suse, some things in the above may show unix - unix is what linux came from..

Unless you see or hear strange noises and things coming from your computer than no there is no worry as long as you have a good firewall for inbound protection... iptables is already installed however to use it it is a tedious task, arno-iptables-firewall is what I recommend , easy to setup, configure and add rules and custom blocked ips - easy and then restart iptables = what it does is configures Iptables itself.

it's in the system repositories.. So again nothing to worry about unless again strange unkown things are going out to the net..

---

### Post by nowshining on 2007-09-12
lolz the above was netstat and that's it..

here is the one of ur original post from myside..

```

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     18204    -                   /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18491    4819/gconfd-2       /tmp/orbit-nowshining/linc-12d3-0-410ba841b518d
unix  2      [ ACC ]     STREAM     LISTENING     18501    4783/x-session-mana /tmp/orbit-nowshining/linc-12af-0-3452abadce07f
unix  2      [ ACC ]     STREAM     LISTENING     18675    4783/x-session-mana /tmp/.ICE-unix/4783
unix  2      [ ACC ]     STREAM     LISTENING     18684    4822/gnome-keyring- /tmp/keyring-RIng2W/socket
unix  2      [ ACC ]     STREAM     LISTENING     18716    4826/gnome-settings /tmp/orbit-nowshining/linc-12da-0-57a9a0b9807a0
unix  2      [ ACC ]     STREAM     LISTENING     18779    4844/esd            /tmp/.esd/socket
unix  2      [ ACC ]     STREAM     LISTENING     18809    4851/gnome-screensa /tmp/orbit-nowshining/linc-12ee-0-35df3af1b8a1f
unix  2      [ ACC ]     STREAM     LISTENING     18831    4852/metacity       /tmp/orbit-nowshining/linc-12f4-0-7a8d68502321c
unix  2      [ ACC ]     STREAM     LISTENING     18848    4853/gnome-panel    /tmp/orbit-nowshining/linc-12f5-0-70a72d7a42d19
unix  2      [ ACC ]     STREAM     LISTENING     18870    4858/gnome-volume-m /tmp/orbit-nowshining/linc-12f6-0-70a72d7a50e1a
unix  2      [ ACC ]     STREAM     LISTENING     18982    4855/nautilus       /tmp/orbit-nowshining/linc-12f7-0-62df158510ae1
unix  2      [ ACC ]     STREAM     LISTENING     18999    4884/glipper        /tmp/orbit-nowshining/linc-1314-0-62df158541f2b
unix  2      [ ACC ]     STREAM     LISTENING     19032    4888/gnome-vfs-daem /tmp/orbit-nowshining/linc-1318-0-3f4301a52ddae
unix  2      [ ACC ]     STREAM     LISTENING     19070    4909/gnome-power-ma /tmp/orbit-nowshining/linc-1312-0-54ffef0386074
unix  2      [ ACC ]     STREAM     LISTENING     19269    4857/bonobo-activat /tmp/orbit-nowshining/linc-12f9-0-3524495f39609
unix  2      [ ACC ]     STREAM     LISTENING     19322    4969/stickynotes_ap /tmp/orbit-nowshining/linc-1369-0-47a53b797613
unix  2      [ ACC ]     STREAM     LISTENING     19369    4979/mapping-daemon /tmp/mapping-nowshining
unix  2      [ ACC ]     STREAM     LISTENING     19394    4981/multiload-appl /tmp/orbit-nowshining/linc-1375-0-28688fd7d2c6b
unix  2      [ ACC ]     STREAM     LISTENING     20353    4991/trashapplet    /tmp/orbit-nowshining/linc-137f-0-c411bedd1cc1
unix  2      [ ACC ]     STREAM     LISTENING     20394    4999/mixer_applet2  /tmp/orbit-nowshining/linc-1387-0-7fae190144e59
unix  2      [ ACC ]     STREAM     LISTENING     20442    5007/kdeinit Runnin /tmp/ksocket-nowshining/kdeinit__0
unix  2      [ ACC ]     STREAM     LISTENING     20444    5007/kdeinit Runnin /tmp/ksocket-nowshining/kdeinit-:0
unix  2      [ ACC ]     STREAM     LISTENING     20454    5012/dcopserver [kd /tmp/.ICE-unix/dcop5012-1189584482
unix  2      [ ACC ]     STREAM     LISTENING     20478    5015/klauncher [kde /tmp/ksocket-nowshining/klauncherTu3Lqa.slave-socket
unix  2      [ ACC ]     STREAM     LISTENING     33896    5224/gnome-terminal /tmp/orbit-nowshining/linc-1468-0-3106b3407e405
unix  2      [ ACC ]     STREAM     LISTENING     21414    5084/firefox-bin    /tmp/orbit-nowshining/linc-13dc-0-2b61976e380d2
unix  2      [ ACC ]     STREAM     LISTENING     16704    -                   /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     16731    -                   @/tmp/dbus-wDZLgcwGWv
unix  2      [ ACC ]     STREAM     LISTENING     16738    -                   @/var/run/hald/dbus-UTgGp4n5mC
unix  2      [ ACC ]     STREAM     LISTENING     18696    4824/dbus-daemon    @/tmp/dbus-dMPrBA3zxb
unix  2      [ ACC ]     STREAM     LISTENING     18089    -                   /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     16741    

```

---

### Post by nowshining on 2007-09-12
okay after taking a look

LISTEN  = non connected - they are waiting for a connection and by default many will ALWAYS wait and never connect..

It must say established or connected for it to connected to anyone out in the outside world..

---

### Post by shiko332 on 2007-09-12
Thank you again for your time (and your patience)

Again, It's clear that for the connection to be established it must appears in a netstat -np, and not in a netstat -lnp

If you look at your netstat output, you will see that ALL your listening ports are Unix sockets, witch it's fine. It's normal that many processes open unix sockets for communicate between them.

But if you look at my first post, you will see that the listening ports on my computer are TCP ports. and you can see clearly at your computer that they are not the same.

The reason for being worried is that I've neved heard that orbit opened so many listening TCP ports, instead of using Unix sockets.

---

### Post by shiko332 on 2007-09-12
Ok, I've found and OLD thread regarding this issue.

[http://www.security-express.com/archives/freebsd/2000-09/0113.html](http://www.security-express.com/archives/freebsd/2000-09/0113.html)

Thanks again :)

---

### Post by nowshining on 2007-09-12
we can both learn, oh and It says on mine that they cannot be determined and to run as root to see them, and then nothing after that, however one post shows my tcp dialup outs -  :)

oh and ssh and netbios are services.. and I said I am running a Non officially announced version of Ubuntu in Development..

---

### Post by nowshining on 2007-09-12
by the way thanks to you I'm learning more about them myself.. :)

---

### Post by nowshining on 2007-09-12
oh and there is no /usr/local/etc/orbitrc on my computer and orbit reveals the following when locating in terminal via locate orbit

```

/var/lib/dpkg/info/python-pyorbit.list
/var/lib/dpkg/info/liborbit2.md5sums
/var/lib/dpkg/info/liborbit2.shlibs
/var/lib/dpkg/info/python-pyorbit.md5sums
/var/lib/dpkg/info/liborbit2.list
/var/lib/dpkg/info/liborbit2.postrm
/var/lib/dpkg/info/liborbit2.postinst
/var/cache/apt/archives/python-pyorbit_2.14.3-1ubuntu1_i386.deb
/usr/share/doc/liborbit2
/usr/share/doc/liborbit2/changelog.gz
/usr/share/doc/liborbit2/changelog.Debian.gz
/usr/share/doc/liborbit2/AUTHORS
/usr/share/doc/liborbit2/TODO
/usr/share/doc/liborbit2/copyright
/usr/share/doc/liborbit2/README
/usr/share/doc/liborbit2/NEWS.gz
/usr/share/doc/python-pyorbit
/usr/share/doc/python-pyorbit/examples
/usr/share/doc/python-pyorbit/examples/everything_client.py.gz
/usr/share/doc/python-pyorbit/examples/everything_server.py.gz
/usr/share/doc/python-pyorbit/examples/c-inproc
/usr/share/doc/python-pyorbit/examples/c-inproc/testcall.idl
/usr/share/doc/python-pyorbit/examples/c-inproc/Makefile.in.gz
/usr/share/doc/python-pyorbit/examples/c-inproc/c-impl.c
/usr/share/doc/python-pyorbit/examples/c-inproc/Makefile.am
/usr/share/doc/python-pyorbit/examples/c-inproc/test-c-inproc.py
/usr/share/doc/python-pyorbit/examples/Makefile.in.gz
/usr/share/doc/python-pyorbit/examples/constants.py
/usr/share/doc/python-pyorbit/examples/everything_inprocess.py
/usr/share/doc/python-pyorbit/examples/Makefile.am
/usr/share/doc/python-pyorbit/changelog.gz
/usr/share/doc/python-pyorbit/changelog.Debian.gz
/usr/share/doc/python-pyorbit/TODO
/usr/share/doc/python-pyorbit/copyright
/usr/share/doc/python-pyorbit/README
/usr/share/doc/python-pyorbit/NEWS.gz
/usr/share/app-install/icons/orbital-eunuchs-sniper.png
/usr/share/app-install/desktop/space-orbit.desktop
/usr/share/app-install/desktop/orbital-eunuchs-sniper.desktop
/usr/lib/orbit-2.0
/usr/lib/orbit-2.0/GNOME_Speech_module.la
/usr/lib/orbit-2.0/Bonobo_module.so
/usr/lib/orbit-2.0/GNOME_Speech_module.so
/usr/lib/orbit-2.0/Everything_module.so
/usr/lib/orbit-2.0/Accessibility_module.so
/usr/lib/orbit-2.0/GNOME_Magnifier_module.so
/usr/lib/orbit-2.0/Accessibility_LoginHelper_module.so


```

---

### Post by p_quarles on 2007-09-12
Just FYI, the best way to find out what services are actually listening for requests from the WAN/internet:
```
sudo apt-get install nmap
```
Determine your *public *IP address, and then type:
```
nmap -P0 public-IP-address
```
It'll take a couple minutes to scan the address, but will return with a listing of open ports, if any. Ports listed as filtered or closed are secure.

---

### Post by nowshining on 2007-09-12
p_quarles thanks from both of us. :)

---

### Post by nowshining on 2007-09-12
by the way change

```

nmap -P0 public-IP-address

```

change the public-ip-address to ur ip example would be..

```

nmap -P0 2.133.200.5

```

than hit enter and My results were..

All 1697 scanned ports on dialup-4.246.210.31.Dial1.SanJose1.Level3.net (4.246.210.31) are closed

Nmap finished: 1 IP address (1 host up) scanned in 1.067 seconds

---

