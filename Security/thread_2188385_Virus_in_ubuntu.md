---
title: "Virus in ubuntu"
date: 2013-11-16
forum: Security
---

### Post by alexying200005 on 2013-11-16
Hi,

I am new to linux/ubuntu.  I think my ubunut caught a virus.  When ever i login to ubunto account, it will automatically download something from an ip with using up all my network bandwidth ( an ip address in China). I can not see which program is downloading data by using nethogs or iftop.  Can somebody help me to find out what is going on?

here is the picture of nethogs and iftop.

NetHogs version 0.8.0


  PID USER     PROGRAM                      DEV        SENT      RECEIVED       
?     root     ..50:56629-117.25.130.43:84             0.000     515.732 KB/sec
?     root     unknown TCP                             0.000       0.000 KB/sec


  TOTAL                                                0.000     515.732 KB/sec 





                191Mb           381Mb           572Mb           763Mb      954Mb
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
ubuntu.local               => 117.25.130.43                 0b      0b      0b
                           <=                            4.91Mb  4.91Mb  4.90Mb
192.168.126.255            => 192.168.126.129               0b      0b      0b
                           <=                               0b    187b     88b
192.168.126.255            => 192.168.126.136               0b      0b      0b
                           <=                               0b    187b     47b
ubuntu.local               => 224.0.0.251                   0b      0b    160b
                           <=                               0b      0b      0b
ubuntu.local               => 192.168.126.2                 0b      0b     44b
                           <=                               0b      0b     80b
255.255.255.255            => 192.168.126.129               0b      0b      0b
                           <=                               0b      0b     66b
255.255.255.255            => 192.168.126.136               0b      0b      0b
                           <=                               0b      0b     66b
ubuntu.local               => 192.168.126.255               0b      0b     52b
                           <=                               0b      0b      0b




&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
TX:             cum:   2.18kB   peak:   1.38kb  rates:      0b      0b    256b
RX:                    29.2MB           4.91Mb           4.91Mb  4.91Mb  4.90Mb
TOTAL:                 29.2MB           4.91Mb           4.91Mb  4.91Mb  4.90Mb

---

### Post by TheFu on 2013-11-17
What does **ss** show?
You should see the sort of traffic and ports.

---

### Post by SeijiSensei on 2013-11-17
I'd start by blocking that IP address by adding these lines to /etc/rc.local and rebooting:

```

/sbin/iptables -I INPUT  -s 117.25.130.43 -j DROP
/sbin/iptables -I OUTPUT -d 117.25.130.43 -j DROP

```

Then you can do some forensics without having to worry about what kinds of traffic you are sending to that address.  Do any of [these domains](http://domaingoat.com/ip/117.25.130.43) look familiar?

---

### Post by alexying200005 on 2013-11-17
Hi TheFu,

Thanks for helping.  Here is the ss result.  Not sure what to look for.


```

Netid  State      Recv-Q Send-Q   Local Address:Port       Peer Address:Port   
u_str  ESTAB      0      0                    * 15782                 * 15783  
u_str  ESTAB      0      0                    * 15470                 * 15471  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 9699                  * 9698   
u_str  ESTAB      0      0                    * 20370                 * 20369  
u_str  ESTAB      0      0                    * 20333                 * 20334  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 17783                 * 16898  
u_str  ESTAB      0      0                    * 11585                 * 10064  
u_str  ESTAB      0      0                    * 9727                  * 10666  
u_str  ESTAB      0      0                    * 16682                 * 16339  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15601                 * 15600  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15112                 * 15110  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 13587                 * 13586  
u_str  ESTAB      0      0                    * 20039                 * 21639  
u_str  ESTAB      0      0                    * 16312                 * 16673  
u_str  ESTAB      0      0                    * 16636                 * 16261  
u_str  ESTAB      0      0                    * 8802                  * 8801   
u_str  ESTAB      0      0                    * 18084                 * 19792  
u_str  ESTAB      0      0                    * 15557                 * 15558  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16388                 * 15915  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 8730                  * 698    
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16387                 * 15914  
u_str  ESTAB      0      0                    * 20372                 * 20371  
u_str  ESTAB      0      0                    * 15784                 * 15785  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15558                 * 15557  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16625                 * 16208  
u_str  ESTAB      0      0                    * 16904                 * 17788  
u_str  ESTAB      0      0                    * 14250                 * 14251  
u_str  ESTAB      7381   0                    * 15117                 * 15122  
u_str  ESTAB      0      0                    * 16047                 * 16526  
u_str  ESTAB      0      0                    * 20374                 * 20373  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 14696                 * 14085  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16692                 * 16691  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 15913                 * 15912  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 15641                 * 15152  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16617                 * 16181  
u_str  ESTAB      0      768    @/tmp/.X11-unix/X0 19787                 * 18076  
u_str  ESTAB      0      0      @/dbus-vfs-daemon/socket-mQcOWs76 17781                 * 16858  
u_str  ESTAB      0      0      /var/run/acpid.socket 9848                  * 9847   
u_str  ESTAB      0      0                    * 15777                 * 15778  
u_str  ESTAB      0      0                    * 20314                 * 20313  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 20034                 * 20033  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16104                 * 16560  
u_str  ESTAB      0      0                    * 16398                 * 16399  
u_str  ESTAB      0      0                    * 14251                 * 14250  
u_str  ESTAB      0      0                    * 16275                 * 16276  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15539                 * 15538  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 12102                 * 12101  
u_str  ESTAB      0      0                    * 20318                 * 20319  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 15911                 * 15910  
u_str  ESTAB      0      0                    * 638                   * 639    
u_str  ESTAB      0      0                    * 20313                 * 20314  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15272                 * 15245  
u_str  ESTAB      0      0                    * 14914                 * 14913  
u_str  ESTAB      0      0                    * 15398                 * 15399  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 8972                  * 8970   
u_str  ESTAB      0      0                    * 15780                 * 15781  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 14951                 * 15382  
u_str  ESTAB      0      0                    * 8537                  * 8546   
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 18002                 * 18001  
u_str  ESTAB      0      0                    * 14886                 * 14887  
u_str  ESTAB      0      0                    * 19785                 * 19786  
u_str  ESTAB      0      0      @/tmp/.ICE-unix/2952 17788                 * 16904  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16308                 * 16307  
u_str  ESTAB      0      0                    * 15275                 * 15276  
u_str  ESTAB      0      0                    * 15602                 * 15603  
u_str  ESTAB      0      0                    * 14972                 * 14973  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15754                 * 15753  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 15586                 * 15585  
u_str  ESTAB      0      0                    * 20362                 * 20361  
u_str  ESTAB      0      0                    * 16858                 * 17781  
u_str  ESTAB      0      0                    * 16232                 * 16233  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 16461                 * 16460  
u_str  ESTAB      0      0                    * 15273                 * 15274  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16337                 * 16679  
u_str  ESTAB      0      0                    * 20329                 * 20330  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 21639                 * 20039  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 17924                 * 17042  
u_str  ESTAB      0      0                    * 14997                 * 15401  
u_str  ESTAB      0      0                    * 17743                 * 17744  
u_str  ESTAB      0      0                    * 20364                 * 20363  
u_str  ESTAB      0      0                    * 16606                 * 16145  
u_str  ESTAB      0      0                    * 16067                 * 16528  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 17998                 * 19771  
u_str  ESTAB      0      0                    * 16855                 * 16856  
u_str  ESTAB      0      0                    * 9847                  * 9848   
u_str  ESTAB      0      0                    * 15693                 * 15694  
u_str  ESTAB      0      0                    * 20334                 * 20333  
u_str  ESTAB      0      0                    * 19789                 * 19790  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16389                 * 15359  
u_str  ESTAB      0      0                    * 20366                 * 20365  
u_str  ESTAB      0      0                    * 17795                 * 17796  
u_str  ESTAB      0      0                    * 16181                 * 16617  
u_str  ESTAB      0      0                    * 16307                 * 16308  
u_str  ESTAB      0      0                    * 14314                 * 14320  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15075                 * 15074  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 9539                  * 10445  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 17606                 * 16840  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16639                 * 16270  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15276                 * 15275  
u_str  ESTAB      0      0                    * 18274                 * 19885  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15411                 * 15410  
u_str  ESTAB      0      0                    * 19795                 * 19796  
u_str  ESTAB      0      0                    * 20368                 * 20367  
u_str  ESTAB      0      0                    * 20328                 * 20327  
u_str  ESTAB      0      0      @/com/ubuntu/upstart-session/1000/2686 14319                 * 14935  
u_str  ESTAB      0      0                    * 16773                 * 16775  
u_str  ESTAB      0      0                    * 16077                 * 16559  
u_str  ESTAB      0      0                    * 9214                  * 9215   
u_str  ESTAB      0      0                    * 16073                 * 16529  
u_str  ESTAB      0      0                    * 698                   * 8730   
u_str  ESTAB      0      0                    * 15885                 * 15355  
u_str  ESTAB      0      0                    * 18085                 * 19793  
u_str  ESTAB      0      0                    * 20352                 * 20351  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16905                 * 17791  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16144                 * 16577  
u_str  ESTAB      0      0                    * 20323                 * 20324  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16673                 * 16312  
u_str  ESTAB      0      0                    * 22576                 * 22577  
u_str  ESTAB      0      0                    * 15689                 * 0      
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15002                 * 15408  
u_str  ESTAB      0      0                    * 14935                 * 14319  
u_str  ESTAB      0      0                    * 15691                 * 15692  
u_str  ESTAB      0      0                    * 15979                 * 15980  
u_str  ESTAB      0      0                    * 20354                 * 20353  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 17790                 * 17789  
u_str  ESTAB      0      0                    * 16837                 * 17598  
u_str  ESTAB      0      0                    * 930                   * 8975   
u_str  ESTAB      0      0      @/dbus-vfs-daemon/socket-JD5WCS5s 16775                 * 16773  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15800                 * 15295  
u_str  ESTAB      0      0                    * 15005                 * 15006  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 14244                 * 14873  
u_str  ESTAB      0      0                    * 15408                 * 15002  
u_str  ESTAB      0      0                    * 16343                 * 16344  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16470                 * 16024  
u_str  ESTAB      0      0                    * 15277                 * 15795  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15598                 * 15597  
u_str  ESTAB      0      0                    * 15074                 * 15075  
u_str  ESTAB      0      0                    * 20356                 * 20355  
u_str  ESTAB      0      0                    * 19886                 * 19887  
u_str  ESTAB      0      0                    * 17789                 * 17790  
u_str  ESTAB      0      0                    * 15359                 * 16389  
u_str  ESTAB      0      0                    * 14085                 * 14696  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 16247                 * 16246  
u_str  ESTAB      0      0                    * 15897                 * 16386  
u_str  ESTAB      0      0                    * 14947                 * 14323  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 14973                 * 14972  
u_str  ESTAB      0      0                    * 15658                 * 15659  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 14939                 * 14938  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 18275                 * 19888  
u_str  ESTAB      0      0                    * 16632                 * 16633  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 21576                 * 21575  
u_str  ESTAB      0      0                    * 16819                 * 17573  
u_str  ESTAB      0      0                    * 20358                 * 20357  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 8975                  * 930    
u_str  ESTAB      0      0                    * 18005                 * 19775  
u_str  ESTAB      0      0                    * 16691                 * 16692  
u_str  ESTAB      0      0                    * 14718                 * 14719  
u_str  ESTAB      0      0                    * 20339                 * 20340  
u_str  ESTAB      0      0                    * 16270                 * 16639  
u_str  ESTAB      0      0                    * 15864                 * 15360  
u_str  ESTAB      0      0      @/dbus-vfs-daemon/socket-zQZmhXvc 17595                 * 16828  
u_str  ESTAB      0      0      @/tmp/.ICE-unix/2952 15980                 * 15979  
u_str  ESTAB      0      0      @/com/ubuntu/upstart-session/1000/2686 15370                 * 14948  
u_str  ESTAB      0      0                    * 15660                 * 15661  
u_str  ESTAB      0      0                    * 20360                 * 20359  
u_str  ESTAB      0      0                    * 16462                 * 16463  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16396                 * 16394  
u_str  ESTAB      0      0                    * 20342                 * 20341  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16809                 * 16808  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 17464                 * 17463  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16130                 * 16562  
u_str  ESTAB      0      0                    * 15217                 * 15749  
u_str  ESTAB      0      0                    * 649                   * 650    
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15920                 * 15919  
u_str  ESTAB      0      0                    * 16780                 * 16781  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 15905                 * 15904  
u_str  ESTAB      0      0                    * 8970                  * 8972   
u_str  ESTAB      0      0                    * 20344                 * 20343  
u_str  ESTAB      0      0                    * 17791                 * 16905  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15087                 * 15086  
u_str  ESTAB      32     0                    * 18076                 * 19787  
u_str  ESTAB      0      0                    * 15007                 * 15008  
u_str  ESTAB      0      0                    * 639                   * 638    
u_str  ESTAB      0      0                    * 20332                 * 20331  
u_str  ESTAB      0      0      @/tmp/.ICE-unix/2952 16812                 * 16811  
u_str  ESTAB      0      0                    * 17463                 * 17464  
u_str  ESTAB      0      0                    * 15218                 * 15750  
u_str  ESTAB      0      0      @/com/ubuntu/upstart-session/1000/2686 14323                 * 14947  
u_str  ESTAB      0      0                    * 20320                 * 20321  
u_str  ESTAB      0      0                    * 15919                 * 15920  
u_str  ESTAB      0      0      @/com/ubuntu/upstart 8714                  * 8644   
u_str  ESTAB      0      0                    * 20346                 * 20345  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16815                 * 16814  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 16233                 * 16232  
u_str  ESTAB      0      0                    * 16562                 * 16130  
u_str  ESTAB      0      0                    * 14413                 * 13773  
u_str  ESTAB      0      0                    * 19771                 * 17998  
u_str  ESTAB      0      0      @/com/ubuntu/upstart 9115                  * 9113   
u_str  ESTAB      0      0                    * 20331                 * 20332  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 14998                 * 15402  
u_str  ESTAB      0      0                    * 20319                 * 20318  
u_str  ESTAB      0      0                    * 17042                 * 17924  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 17566                 * 16804  
u_str  ESTAB      0      0                    * 20348                 * 20347  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 19792                 * 18084  
u_str  ESTAB      0      0                    * 16530                 * 16074  
u_str  ESTAB      0      0                    * 15902                 * 15903  
u_str  ESTAB      0      0                    * 15399                 * 15398  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 8907                  * 8906   
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16216                 * 16215  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 15401                 * 14997  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 15588                 * 15587  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15785                 * 15784  
u_str  ESTAB      0      0                    * 9196                  * 9197   
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 17569                 * 16806  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 14930                 * 14310  
u_str  ESTAB      0      0                    * 20350                 * 20349  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 16207                 * 16206  
u_str  ESTAB      0      0                    * 16577                 * 16144  
u_str  ESTAB      0      0                    * 20315                 * 20316  
u_str  ESTAB      0      0                    * 16637                 * 16262  
u_str  ESTAB      0      0                    * 13560                 * 13299  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 14887                 * 14886  
u_str  ESTAB      0      0                    * 16898                 * 17783  
u_str  ESTAB      0      0                    * 16206                 * 16207  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15286                 * 15278  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15781                 * 15780  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 8885                  * 835    
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15783                 * 15782  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 9197                  * 9196   
u_str  ESTAB      0      0                    * 20371                 * 20372  
u_str  ESTAB      0      0                    * 20335                 * 20336  
u_str  ESTAB      0      0                    * 16208                 * 16625  
u_str  ESTAB      0      0                    * 16394                 * 16396  
u_str  ESTAB      0      0                    * 14963                 * 14964  
u_str  ESTAB      0      0                    * 13586                 * 13587  
u_str  ESTAB      0      0                    * 15086                 * 15087  
u_str  ESTAB      0      0                    * 20033                 * 20034  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 19885                 * 18274  
u_str  ESTAB      0      0                    * 15915                 * 16388  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15424                 * 15423  
u_str  ESTAB      0      0                    * 20373                 * 20374  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16022                 * 16466  
u_str  ESTAB      0      0                    * 15914                 * 16387  
u_str  ESTAB      0      0                    * 20326                 * 20325  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16609                 * 16174  
u_str  ESTAB      0      0                    * 15278                 * 15286  
u_str  ESTAB      0      0                    * 10445                 * 9539   
u_str  ESTAB      0      0                    * 15538                 * 15539  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 14964                 * 14963  
u_str  ESTAB      0      0      @/com/ubuntu/upstart 8546                  * 8537   
u_str  ESTAB      0      0                    * 20338                 * 20337  
u_str  ESTAB      0      0                    * 20327                 * 20328  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16528                 * 16067  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16339                 * 16682  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16856                 * 16855  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16633                 * 16632  
u_str  ESTAB      0      0                    * 16471                 * 16472  
u_str  ESTAB      0      0                    * 16174                 * 16609  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 19793                 * 18085  
u_str  ESTAB      0      0                    * 15912                 * 15913  
u_str  ESTAB      0      0      @/com/ubuntu/upstart-session/1000/2686 14320                 * 14314  
u_str  ESTAB      0      0                    * 20337                 * 20338  
u_str  ESTAB      0      0      /run/user/1000/pulse/native 16399                 * 16398  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 15471                 * 15470  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 9453                  * 9191   
u_str  ESTAB      0      0                    * 8801                  * 8802   
u_str  ESTAB      0      0                    * 16466                 * 16022  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15778                 * 15777  
u_str  ESTAB      0      0                    * 14938                 * 14939  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 16262                 * 16637  
u_str  ESTAB      0      0                    * 15910                 * 15911  
u_str  ESTAB      0      0                    * 15100                 * 15101  
u_str  ESTAB      0      0                    * 15295                 * 15800  
u_str  ESTAB      0      0                    * 20361                 * 20362  
u_str  ESTAB      0      0                    * 17796                 * 17795  
u_str  ESTAB      0      0                    * 16452                 * 15982  
u_str  ESTAB      0      0                    * 15003                 * 15004  
u_str  ESTAB      0      0                    * 15152                 * 15641  
u_str  ESTAB      0      0                    * 12097                 * 12098  
u_str  ESTAB      0      37888  @/com/ubuntu/upstart-session/1000/2686 15122                 * 15117  
u_str  ESTAB      0      0                    * 17571                 * 17572  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 15469                 * 15468  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 17923                 * 17922  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 9215                  * 9214   
u_str  ESTAB      0      0                    * 20363                 * 20364  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 15982                 * 16452  
u_str  ESTAB      0      0                    * 9369                  * 9160   
u_str  ESTAB      0      0                    * 16752                 * 16767  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15274                 * 15273  
u_str  ESTAB      0      0                    * 15600                 * 15601  
u_str  ESTAB      0      0                    * 19786                 * 19785  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 19784                 * 18030  
u_str  ESTAB      0      0                    * 14256                 * 14890  
u_str  ESTAB      0      0                    * 16024                 * 16470  
u_str  ESTAB      0      0                    * 20365                 * 20366  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16145                 * 16606  
u_str  ESTAB      0      0      /run/user/1000/pulse/native 15953                 * 15952  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 19775                 * 18005  
u_str  ESTAB      0      0                    * 12101                 * 12102  
u_str  ESTAB      0      0                    * 20340                 * 20339  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15694                 * 15693  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 16779                 * 16778  
u_str  ESTAB      0      0                    * 20367                 * 20368  
u_str  ESTAB      0      0                    * 16840                 * 17606  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 16607                 * 16605  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 9160                  * 9369   
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 724                   * 8807   
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 12098                 * 12097  
u_str  ESTAB      0      0                    * 19796                 * 19795  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 16559                 * 16077  
u_str  ESTAB      0      0                    * 14873                 * 14244  
u_str  ESTAB      0      0                    * 18030                 * 19784  
u_str  ESTAB      0      0                    * 15110                 * 15112  
u_str  ESTAB      0      0                    * 14913                 * 14914  
u_str  ESTAB      0      0                    * 690                   * 691    
u_str  ESTAB      0      0                    * 20369                 * 20370  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 19790                 * 19789  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 16529                 * 16073  
u_str  ESTAB      0      0      @/tmp/.ICE-unix/2952 16472                 * 16471  
u_str  ESTAB      0      0                    * 8644                  * 8714   
u_str  ESTAB      0      0                    * 16828                 * 17595  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 15661                 * 15660  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 650                   * 649    
u_str  ESTAB      0      0                    * 20325                 * 20326  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15355                 * 15885  
u_str  ESTAB      0      0                    * 15597                 * 15598  
u_str  ESTAB      0      0                    * 15410                 * 15411  
u_str  ESTAB      0      0                    * 21986                 * 21987  
u_str  ESTAB      0      0                    * 20353                 * 20354  
u_str  ESTAB      0      0                    * 16608                 * 16172  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 15004                 * 15003  
u_str  ESTAB      0      6144   @/tmp/.X11-unix/X0 11519                 * 11518  
u_str  ESTAB      0      0                    * 9698                  * 9699   
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 17598                 * 16837  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16344                 * 16343  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15795                 * 15277  
u_str  ESTAB      0      0                    * 15587                 * 15588  
u_str  ESTAB      0      0      @/dbus-vfs-daemon/socket-yR3jWo2E 16767                 * 16752  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15692                 * 15691  
u_str  ESTAB      0      0                    * 20355                 * 20356  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 17572                 * 17571  
u_str  ESTAB      0      0                    * 16460                 * 16461  
u_str  ESTAB      0      0                    * 15585                 * 15586  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 10666                 * 9727   
u_str  ESTAB      0      0      @/dbus-vfs-daemon/socket-fRmQ1PzB 17744                 * 17743  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 14890                 * 14256  
u_str  ESTAB      0      0                    * 9191                  * 9453   
u_str  ESTAB      0      0      @/dbus-vfs-daemon/socket-IGrACA5Z 22577                 * 22576  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 691                   * 690    
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16526                 * 16047  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 15603                 * 15602  
u_str  ESTAB      0      0                    * 20336                 * 20335  
u_str  ESTAB      0      0                    * 15245                 * 15272  
u_str  ESTAB      0      0                    * 21575                 * 21576  
u_str  ESTAB      0      0                    * 18001                 * 18002  
u_str  ESTAB      0      0                    * 20357                 * 20358  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16463                 * 16462  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 19887                 * 19886  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15360                 * 15864  
u_str  ESTAB      0      0                    * 15423                 * 15424  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 14719                 * 14718  
u_str  ESTAB      0      0                    * 16246                 * 16247  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15807                 * 15304  
u_str  ESTAB      0      0                    * 14937                 * 14940  
u_str  ESTAB      320    0                    * 11518                 * 11519  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 15659                 * 15658  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16781                 * 16780  
u_str  ESTAB      0      0                    * 20359                 * 20360  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 17573                 * 16819  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 16276                 * 16275  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 13773                 * 14413  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 13485                 * 13484  
u_str  ESTAB      0      0                    * 19888                 * 18275  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 15101                 * 15100  
u_str  ESTAB      0      0      @/tmp/.ICE-unix/2952 19791                 * 18083  
u_str  ESTAB      0      0                    * 16778                 * 16779  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 13299                 * 13560  
u_str  ESTAB      0      0                    * 20343                 * 20344  
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 16172                 * 16608  
u_str  ESTAB      0      0                    * 16811                 * 16812  
u_str  ESTAB      0      0                    * 15468                 * 15469  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15749                 * 15217  
u_str  ESTAB      0      0                    * 20341                 * 20342  
u_str  ESTAB      0      0                    * 15952                 * 15953  
u_str  ESTAB      0      0                    * 15904                 * 15905  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 14940                 * 14937  
u_str  ESTAB      0      0                    * 20345                 * 20346  
u_str  ESTAB      0      0                    * 17785                 * 17786  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 16074                 * 16530  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15750                 * 15218  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 16261                 * 16636  
u_str  ESTAB      0      0                    * 9113                  * 9115   
u_str  ESTAB      0      0      @/tmp/.X11-unix/X0 15006                 * 15005  
u_str  ESTAB      0      0                    * 16814                 * 16815  
u_str  ESTAB      0      0      /var/run/dbus/system_bus_socket 10064                 * 11585  
u_str  ESTAB      0      0                    * 20321                 * 20320  
u_str  ESTAB      0      0                    * 17921                 * 17039  
u_str  ESTAB      0      0                    * 20347                 * 20348  
u_str  ESTAB      0      0                    * 20316                 * 20315  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 17786                 * 17785  
u_str  ESTAB      0      0                    * 16804                 * 17566  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 15903                 * 15902  
u_str  ESTAB      0      0                    * 18083                 * 19791  
u_str  ESTAB      0      0                    * 15753                 * 15754  
u_str  ESTAB      0      0                    * 15382                 * 14951  
u_str  ESTAB      0      0                    * 835                   * 8885   
u_str  ESTAB      0      0                    * 20330                 * 20329  
u_str  ESTAB      0      0                    * 17922                 * 17923  
u_str  ESTAB      0      0                    * 14948                 * 15370  
u_str  ESTAB      0      0                    * 8906                  * 8907   
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 21987                 * 21986  
u_str  ESTAB      0      0                    * 16806                 * 17569  
u_str  ESTAB      0      0                    * 20349                 * 20350  
u_str  ESTAB      0      0                    * 20324                 * 20323  
u_str  ESTAB      0      0                    * 16215                 * 16216  
u_str  ESTAB      0      0                    * 16605                 * 16607  
u_str  ESTAB      0      0                    * 9538                  * 0      
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 15008                 * 15007  
u_str  ESTAB      0      0      @/tmp/dbus-HysINZGdbr 16386                 * 15897  
u_str  ESTAB      0      0                    * 15402                 * 14998  
u_str  ESTAB      0      0                    * 15304                 * 15807  
u_str  ESTAB      0      0      @/tmp/dbus-dvQCtMLigc 17039                 * 17921  
u_str  ESTAB      0      0                    * 16679                 * 16337  
u_str  ESTAB      0      0                    * 20351                 * 20352  
u_str  ESTAB      0      0                    * 16808                 * 16809  
u_str  ESTAB      0      0                    * 16560                 * 16104  
u_str  ESTAB      0      0                    * 14310                 * 14930  
u_str  ESTAB      0      0                    * 13484                 * 13485  
u_str  ESTAB      0      0                    * 8807                  * 724    


```

---

### Post by alexying200005 on 2013-11-17
Hi SeijiSensei,

Thanks for the info.  No, i don't see any familiar site in the domains list. What are those domains? Virus sites?  I might go to one of the sites by mistake. I don't know.  I will add the lines to the rc.local file. thanks.

---

### Post by TheFu on 2013-11-17
Holy crap!!!!  My desktop had 5 lines - all were to specific IP addresses either inside or outside my network. It was clear that http, ssh, ftp, samba or imap were being used. 

I don't have any of that dbus crap. Unity? I can't imagine trying to secure all that stuff.

---

### Post by alexying200005 on 2013-11-17
Hi SeijiSensei,

After i added the two lines to the rc.local file and rebooted.  It still downloads data from the Chinese IP.

```


NetHogs version 0.8.0


  PID USER     PROGRAM                      DEV        SENT      RECEIVED       
?     root     ..50:56629-117.25.130.43:84             0.000     540.868 KB/sec
?     root     unknown TCP                             0.000       0.000 KB/sec


  TOTAL                                                0.000     540.868 KB/sec 

















                191Mb           381Mb           572Mb           763Mb      954Mb
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
ubuntu.local               => 117.25.130.43                 0b      0b      0b
                           <=                            4.91Mb  4.42Mb  4.42Mb
ubuntu.local               => 192.168.126.2                 0b    288b    288b
                           <=                               0b    463b    463b
ubuntu.local               => 224.0.0.251                 568b    645b    645b
                           <=                               0b      0b      0b
ubuntu.local               => 91.189.89.199                 0b     76b     76b
                           <=                               0b     76b     76b
ubuntu.local               => 91.189.94.4                   0b     76b     76b
                           <=                               0b     76b     76b
ubuntu.local               => 224.0.0.22                    0b     40b     40b
                           <=                               0b      0b      0b












&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
TX:             cum:   1.10kB   peak:   1.41kb  rates:    568b   1.10kb  1.10kb
RX:                    4.42MB           4.91Mb           4.91Mb  4.42Mb  4.42Mb
TOTAL:                 4.42MB           4.91Mb           4.91Mb  4.42Mb  4.42Mb





```

---

### Post by alexying200005 on 2013-11-17
Hi TheFu,

I am not sure if i understand what you are saying. Can you be more specific? Thanks

---

### Post by TheFu on 2013-11-17
Well, the fact that is controlled by root is just scary.
**sudo iptables -L**
should show the REJECT rules entered before.  If not, perhaps a different control channel is sending everything outbound.
Have you installed any software from outside the Canonical repos?

---

### Post by alexying200005 on 2013-11-17
Hi TheFu,

try sudo iptables -L.  Here is the result.  I always use the software center or apt-get install command to install new applications.
 
I am not sure how i got this virus.  It must be the time when i browse the internet.

```


ubuntu2@ubuntu:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
DROP       all  --  117.25.130.43        anywhere            
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            


Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             117.25.130.43       
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            


Chain ufw-after-forward (1 references)
target     prot opt source               destination         


Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         


Chain ufw-after-output (1 references)
target     prot opt source               destination         


Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            


Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             state INVALID
DROP       all  --  anywhere             anywhere             state INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere            


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         


Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            


Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             state INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere            


Chain ufw-reject-forward (1 references)
target     prot opt source               destination         


Chain ufw-reject-input (1 references)
target     prot opt source               destination         


Chain ufw-reject-output (1 references)
target     prot opt source               destination         


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            


Chain ufw-track-input (1 references)
target     prot opt source               destination         


Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             state NEW
ACCEPT     udp  --  anywhere             anywhere             state NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination         


Chain ufw-user-input (1 references)
target     prot opt source               destination         
DROP       tcp  --  117.25.130.43        117.25.130.43        tcp spt:84 dpt:200
DROP       udp  --  117.25.130.43        117.25.130.43        udp spt:84 dpt:200


Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         


Chain ufw-user-output (1 references)
target     prot opt source               destination         



```

---

### Post by alexying200005 on 2013-11-18
ok.  Looks like nobody has any idea.  I better delete the whole ubuntu image and try opensuse to see if it is safer.

---

### Post by Iowan on 2013-11-18
That would be your decision - good luck with whatever you decide.

---

### Post by 1clue on 2013-11-18
Welcome to the club of Linux users who have found out that it's NOT automatically secure enough as-installed.  Been there, done that.

At this point if it were my system there's no way I'd trust it anymore, so a system re-install would definitely be in the cards.

That said, you did something -- or didn't do something -- that enabled this to happen, and then somehow caught the attention of a bad guy.  Following the same pattern and finding a bad guy with any other distro is going to yield pretty much the same results.

Whatever you decide with respect to a future distro, google "<distro> security" and start reading.  Pay attention to anything that would make sense for your situation.

Bare-bones stock Linux distros are reasonably secure, but they're all trying to find a balance between real security and usability.  They can't lock it down tight without knowing the situation the end user is in.

Not only that, but chances are the thing that caused your system to be vulnerable was facilitated by you or another user on the system in some way.  Bad passwords, or you fell for a phishing scheme of some sort are the two biggies I think.

---

### Post by TheFu on 2013-11-18
> **alexying200005 said:**
> ok.  Looks like nobody has any idea.  I better delete the whole ubuntu image and try opensuse to see if it is safer.

OpenSUSE is a fine distro, but I wouldn't expect it to be any more or less secure.  It is definitely less used, at least around my Linux groups, so getting help might be a little more difficult.  You may have THE SUSE expert living in your neighborhood. It could happen.

As far as security goes, there are some fairly standard things. The Ubuntu team has done a great job of documenting **basic security** stuff. See my signature for links.  1clue has many good points. I suspect you've already reviewed those.

A member of my LUG, Bob Toxen, _wrote the book_ on Linux security. You can find it at Amazon and most other booksellers. It is an old-school security techniques book, but still relevant today.

Anyway, good luck to you. I sincerely wish you well and hope you find what you seek.

---

### Post by alexying200005 on 2013-11-18
Thank you all for helping. 

I have been a windows user for many years.  I never use linux except in school time ( used unix at that time).  I don't like the idea of Microsoft joining the prism spy program. So, i try to use linux.  Ubuntu is the first linux system that i tried since many people are saying ubuntu is easy for newbies.  Yes, i agree that ubuntu is very easy to use, i love it so far.

The only problem i have is safety with ubuntu.  I did not use ubuntu to do weird thing. i did not install program from unknown person or sites.  I just use it to browse the web like i did with windows.  With windows, i haven't had problem with virus for the last three years.  I remember when my windows got the virus three year ago,  i used restore point in windows to fix the issue, quite easy.

Now, with ubuntu, i have been using it for last two months and got a virus.  I have no idea how to fix it. And it looks like nobody in the community has any idea how to fix it.  I don't have time to learn all linux knowledge to fix the problem. I just need an easy and safe OS to continue my daily life.  So, i need to find a way out. Maybe, two months later, i will find out opensuse is as vulnerable as ubuntu. Then, i will need to try an other version of linux until i run out of  choices.

I just want to give a middle finger to the US government and prism program.  They make my life harder. I am not a terrorist, but i do not want to be spied on.

---

### Post by 1clue on 2013-11-19
I've been using Linux since about 1996.  I completely support the idea of trying every distro you can get your hands on.  But what you're saying here, you're not going to be happy.

First thing:  Computer security is more about your practices and your caution than it is about ANY computer software.  You could be on the most secure operating system on the planet, and if you do something that you shouldn't, you're vulnerable.  Most security incidents on Linux are human error.  You can choose to believe me or not, but if you continue with your quest as you name it you'll either find out I'm right or you'll be lucky and not get bit again.

Second thing: You don't learn those practices without some research.  Most of that research applies pretty much equally across all operating systems, since it deals more with networking than with any particular operating system.  The details of implementation depend on the operating system, but not so much the concepts.

Third thing:  Internet spying by government the way it's been portrayed in the news has almost nothing to do with your personal computer.  They're monitoring the places you go, which is a much easier target.  It doesn't matter what operating system you use, if you go to google or gmail or microsoft or any of those other sites, OR any of the sites they own, OR go through a network they own, then you're susceptible.  That has nothing to do with Linux.

---

### Post by alexying200005 on 2013-11-19
For the spying program, i believe Microsfot reports bugs to NSA before they fix it.   So,  NSA can use the bug to do what they want before it gets fixed.

But, yes, mainly NSA spying on where you go, what you write on the web, your emails and instant messages.

I agree that an OS gets a virus because user does a stupid thing.  But, i mainly use ubuntu to browser the web,  i don't think i did something unwisely when browsing the web.

---

### Post by Irihapeti on 2013-11-19
Have you by any chance used the remote desktop program? Or installed the ssh server?

---

### Post by 1clue on 2013-11-19
> **alexying200005 said:**
> For the spying program, i believe Microsfot reports bugs to NSA before they fix it.   So,  NSA can use the bug to do what they want before it gets fixed.

But, yes, mainly NSA spying on where you go, what you write on the web, your emails and instant messages.

I agree that an OS gets a virus because user does a stupid thing.  But, i mainly use ubuntu to browser the web,  i don't think i did something unwisely when browsing the web.

Um...  Not exactly, but sort of.

[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

Every operating system, every piece of software has bugs.  People find bugs, and some of them are reported by the finder to the authors, or to some sort of central organization like CERT.  Some of them are ignored, and some are sent to ... let's just call the bad guys "black hats" and the good guys "white hats."  So the black hats get some of the bugs, and the white hats get some of the bugs.  Probably both colors of hats get most of the bugs.

So about that list above, or CERT advisories, or whatever list you want.  There are lots of lists.

Most of the issues you see in those lists are already solved in some fashion:  Either there's a bug fix available for the appropriate versions, or a new version of software, or some work-around is available.  Sometimes a big vulnerability which is being actively exploited "in the wild" will cause the white hats who maintain these public lists to make an announcement when there's no fix.

So, what you have to worry about:
[LIST=1]
[*]Vulnerabilities on the list which do not have a known fix.
[*]Vulnerabilities having a solution that you have not yet applied to your system.
[*]Vulnerabilities known to black hats but not the white hats.
[*]Vulnerabilities not yet known.
[/LIST]

There are more, but I'm sure you get the idea.

The common gossip says that if you keep your software updated then you have nothing to worry about.  That's not true, not for ANY operating system.  You have to worry about the stuff for which fixes have not been applied on your system.  Software updates will fix a vulnerability, but they won't undo the intrusion on your system that happened before the fix was applied.

The thing is, as I said there are lots of lists.  Most of the "white hat" lists are public, or at least parts of them are public.  These lists generally keep a lot of stuff off the public part until they're fixed or at least until they're verified to exist.  That said, there are surely black-hat lists as well, and you won't hear about them unless you're hanging out with black hats.

As well, we could suppose that there are "gray hats" which would be overzealous security experts trying to hunt down the [s]Communists[/s] terrorists.  These are supposedly well intentioned but perhaps a bit too eager to see crimes where none have been committed.

---

### Post by alexying200005 on 2013-11-19
Hi, Irihapeti,

No, i did not install remote desktop or ssh server. i remember i installed a shared folder program to share a folder with windows network, called samba??

---

### Post by craig10x on 2013-11-19
Sounds like you must have gone to a really bad website...i don't know...i surf like crazy and been running either ubuntu or an ubuntu based distro for years (since 2008) and never got anything on them...
I don't think going to say Open Suse or Fedora or PCLinuxOS (etc) is going to improve your security...but as was pointed out, just be a bit more cautious then perhaps you have been...for example: i don't going to XXX sites even in linux...so just stick to shall we say "conventional sites" and you shouldn't have a problem...

The only thing i do is download GUFW and turn on the linux firewall and that's it...so i can only assume you probably went to a really risky site....also, only download programs from the software center or TRUSTED linux websites...

At this point, i'd just do a nice clean install of Ubuntu... ;)

---

### Post by Irihapeti on 2013-11-19
The reason I ask is that poorly-configured servers are a frequent cause of security breaches. Remote desktop and ssh seem to be the most common ones. Incidentally, you don't have to install remote desktop. It's already there, and I've seen a number of people get into trouble by playing with it. I don't know very much about samba, but it's possible that it's the culprit in your case. We need to hear what some of the other posters have to say - they no doubt know a lot more about Samba than I do.

---

### Post by medior on 2013-11-19
Hi,
Well, done for spotting this! That's the hard bit done :-)
It would be good to know which process is responsible. Can you try this command:
```
sudo netstat -nap | grep 117.25
```
The output could look something like this (the last two items being process ID and name):
```
tcp        0      0 192.168.1.20:51246      117.25.130.43:84     ESTABLISHED 5265/ssh
```

The process shown isn't necessary evil, you might have to trace back to find the parent process. pstree should help with that.
```
pstree -p
```

---

### Post by TheFu on 2013-11-19
He posted the output from **ss** already. I didn't see anything from the suspect IP inside that.

Perhaps I'm a little paranoid compared to others. Before 2002, I was hacked twice. Once while on a government network (before firewalls were used) and the other time when running a DNS server that was 3 months behind on patches.

The things that a smart computer user does to be secure are the same across every OS that I know.
#1 - backups. 100%, known-good, easy to restore backups. There are thousands of issues that backups solve, not just a broken HDD.
#2 - don't run services that you don't need/understand.
#3 - stay patched.  The easy way on Ubuntu is to only run LTS releases, so patches are available 5 yrs. Most of the other releases only get 5-9 months of support.
For more things to do, check my signature and blog. [Securing a web browser]("http://blog.jdpfu.com/pages/secure-browser-settings").

Whatever happened to this PC - and I can't tell from here - is definitely unusual.  Could a bittorrent client be running?  Samba usually is not dangerous because ISPs where I live all block those ports on the internet.  Perhaps your ISP doesn't? I've been to places in the world where ISPs are just a connection and average computer users hang themselves. How is the machine connected to the internet? Is there are router with a firewall and NAT or is it directly connected. Security is a little different/harder if it is directly attached. Allowing any desktop computer to be directly connected to the internet is a mistake, IMHO.

If you don't live or work with Chinese, I'd put up a firewall rule that blocks the entire subnet. Let me check ... 117.24.0.0/11. That's the entire ISP subnet for the offending IP over 2M IPs.

---

### Post by alexying200005 on 2013-11-19
Hi All,

Thx for helping.  I have installed[COLOR=#000000] Gufw before getting the virus.  I always browse the web with Gufw on.  After i got the virus, i set up a rule in Gufw to block in and out traffic to the Chinese ip.  However, no use.

My computer connects to my router at home, then router connects to internet.  My router has a firewall, but i did not do any custom configuration on it, just use its default setting.

For the spying issue, i don't know in what list that Microsfot reports bug to NSA. I[/COLOR][COLOR=#000000]n bark or white list, does not matter[/COLOR][COLOR=#000000]. But helping a spy agency to spy on its customers is not acceptable.  I am not an American. So, my privacy is not protected under US laws.  NSA can screw with my privacy in any way they want. 

By the way, i executed the commands on fixubuntu.com site to disable sending data from my desktop to ubuntu main site.  It is not that i don't trust ubuntu.  It is because i don't want to take the risk.[/COLOR]

---

### Post by alexying200005 on 2013-11-19
From TheFu suggestion,

#1 i did not use backup on ubuntu
#2 i normally do not run any service or app i do not know. never install anything outside of ubuntu repos
#3 i always keep updating ubuntu patch by using update app in ubuntu.  probably, every 2 or 3 days, i will do an update.

---

### Post by TheFu on 2013-11-19
> **alexying200005 said:**
> I am not an American. So, my privacy is not protected under US laws.  NSA can screw with my privacy in any way they want. 

I am a US citizen and it appears that US laws do not protect me either.  

I cannot blame any US-based company for following legally required requests from the government. The hard part is determining "what is actually legal" when the companies are placed under a gag order - prevented from discussing it even with their own lawyers! As a citizen, this concerns me. Free speech should only be refrained for a few weeks when public safety is at immediate risk, not indefinitely.  Covering up something embarrassing or illegal should never be prevented by "questionable laws."

Sorry for the OT post. Best to close this thread, I fear.

---

### Post by QIII on 2013-11-19
This has taken a political turn.  However, since I want to make sure the OP's issue is fully addressed, I'm not closing it just yet.

No more political drifting.

---

### Post by alexying200005 on 2013-11-19
Thank you all for your suggestions.  if any one needs any info or data, please post on the thread.  Mean while, i will try opensuse and see what happens.

---

### Post by cariboo on 2013-11-19
@alexying200005, how do you connect to the internet?

---

### Post by alexying200005 on 2013-11-19
hi, Cariboo907,

my computer connects to my router, my router connects to my modem, then connects to my isp -> outside internet

---

### Post by 1clue on 2013-11-19
So getting things back to the strictly technical:

You can pretty much guarantee that EVERY technically adept nation monitors Internet traffic just before it leaves their borders or just after it enters.  You can also be pretty sure that any large mail server is going to be monitored, either directly with cooperation of the provider or through some subpoena that will inevitably be served on some user or other.  Or through a wiretap.

IMO getting around monitoring is not a task I'd willingly undertake.  You not only have to avoid all the sites you'll want to visit anyway (or your kids:  facebook, twitter, mail, news sites, whatever are all going to be monitored) but EVERYONE you talk to will have to do the same.  You could spend thousands of dollars setting up your own equipment, but then the guy you email uses gmail and you went through all that trouble for nothing.

One thing is absolutely certain:  If you intend to get Internet without being monitored by SOMEBODY (almost any larger government, YOUR government, your ISP, Google, Yahoo, Microsoft, ..........) you'll have to research enough to qualify for just about any computer security job in the world.  It's not going to be easy, and I'm going to go so far as to say it's not going to be possible.

---

### Post by QIII on 2013-11-19
... which is all well and good, but offers little in the way of helping the OP.

---

### Post by alexying200005 on 2013-11-19
1clue,

Thanks for your suggestions.  I agree with you that avoiding being monitored is not possible.

All I can do is to use the services in my own country as much as possible instead of in US.  In my own country, we still have some sort of rights of privacy protection.  Police needs to get a warrant to search peoples' email or personal data.  Well, i am not living in China or North Korea obviously where privacy does not exist.
 
Anyway, to use open source OS, i am hoping i can get a more secure OS than windows.  I am not sure that is too much to ask for. I am willing to try.

---

### Post by 1clue on 2013-11-19
OK that sounds much more achievable.

Theoretically, those of us in the USA also have some of those rights.  Can't go there, too political but you can probably imagine.  :)

FWIW I personally don't care so much about my government spying on me or even some other government.  They tend to be interested in lawbreakers or national security, which I'm pretty sure I have nothing helpful for them anyway.  What I'm afraid of are the "private entities" who want my information so they can buy a house using my identity and then try to get me to pay for it.

"More secure" is achievable.  You just have to start reading a bit at a time, and then adjust your behavior and your computer settings as you go.  You can take incremental steps, try one thing and then another to see what works best for you.

I've been questing for "more secure" for years now, and generally speaking I think I do pretty well at it.

My definition of "more secure" isn't yours.  I'm more worried about intrusion into my space than I am about monitoring from outside.  But again, you can achieve "more secure" by your own definition and you can get real results that mean something.

The bad news is, you need to actually do something.  You have to research and understand technical information.  Most of that information can be applied to any operating system, but some of it depends on a platform.

The first step IMO is that you cannot "pass the buck" of security to some third party.  Windows and its antivirus obsession is a perfect example.  Linux isn't susceptible to viruses, but as you discovered there are plenty of other types of malware.

Second step, you have to install and become intimate with your detection software.  You have to not only configure some of it manually, but you have to pay attention to what it says.

You were lucky in a way.  Your intrusion was noisy and obnoxious:  It generated so much traffic your Internet connection was saturated, making your system unusable.  Most "serious" malware tries to be undetectable.  They want a platform from which to attack some other site, or they want your financial information or your email addresses, or something else, and they DO NOT want you to detect them.  IMO most Linux intrusions go unnoticed because the owner/maintainer of the system leaves it bone stock.

---

### Post by alexying200005 on 2013-11-19
My definition of "more secure" is no backdoor of my OS. so, Miscrosfot reports bugs to NSA before fixing it is totally unacceptable to me.  It is kind of temp backdoors to me.

I am not happy with being monitored outside either.  I might need to vpn or tor to surf one day.

Yes, the virus i got so far does not seem to steal any personal infor from me.  It just downloads data from an Chinese ip.

I guess i have a lot to learn in linux world.  *sigh*

---

### Post by 1clue on 2013-11-19
There is no direct reporting to the NSA that I know of.  And it's not just Microsoft reporting bugs.  There are mechanisms in place to collect vulnerabilities and possible vulnerabilities and report them to "white hat" entities.  Those entities include the developers of the software, antivirus/security firms, etc.  If I subscribe to a Microsoft developer service, I'd probably get access to those bugs before the general public does.  There are institutions such as CERT which provide warnings of vulnerabilities to anyone who wants to subscribe, for free.  The US government and many others also subscribe to these services, since a government is probably the single largest consumer of computers and software in any given nation.  It's an indirect relationship.

My point is that these bug reporting mechanisms are cross platform.  They report on Windows and Mac OS X and Solaris and Linux and whatever else you can find.  All those bugs are in some pretty massive databases and different institutions collect and share them with each other, and each of these institutions has a different slant on how that data should be used.

On top of that, you can be pretty sure any military is going to have a department to find vulnerabilities in just about any operating system, including every flavor of Linux.

Full disclosure:  The United States government is one of the biggest contributors of Open Source software out there.  NASA and other scientific research groups (Los Alamos National Labs for example) contribute a massive amount of Open Source and Public Domain scientific software.  You want an outrageously complicated CAD program for Linux that is used to design military hardware?  Open Source, courtesy of the US government.  Too complicated to use unless you're a professional, but it's there.

They know about Linux.  They use it heavily, especially in supercomputing applications.  This alleged backdoor you're talking about with Microsoft, it's in Linux too.  There's no special group of Linux developers writing a report per se, but there are plenty of Linux developers working for governments in pretty much any country.  They report to someone.

---

### Post by Bucky Ball on 2013-11-19
> **alexying200005 said:**
> Thank you all for your suggestions.  if any one needs any info or data, please post on the thread.  Mean while, i will try opensuse and see what happens.

After all this, I really wonder whether any of it has sunk in. You can distro hop as much as you like, but the moment you replicate whatever it is you did you are going to have exactly the same issue. Any of the distros are going to be just as vulnerable, this has been mentioned umpteen times on this thread, yet you appear to remain completely ignorant to the fact and persist in thinking that leaping to another distro is going to solve anything. This is a complete misconception. 

Still, your time to waste. Good luck. Please mark this thread as 'solved' using thread tools as there is really nothing more to say here and as QIII mentions, it is veering off into repetition and politics. This thread has gone way off topic. Spying is stealth and you wouldn't have noticed ... this was bells and whistles and you were simply being used to transfer data by the looks. Paranoia gone ... well, paranoid!

(PS: Besides which, why would anyone want to spy on you??? As also mentioned, the servers you deal with get spied on, governments need/want a (very) good reason to spy on one, single, iddy biddy citizen. More trouble than it's worth and they are not sitting about going 'let's spy on Frank A. Nobody today' or sticking a pin in the phone book for someone to spy on.)

PPS: Read this carefully people:

[QUOTE=alexying200005]Yes, the virus i got so far _does not seem to steal any personal infor from me_.  It just _downloads data from an Chinese ip_.[/QUOTE]

I would say it downloads and then sends right along this data. All this carry on about spying is completely off topic. This thread has a limited lifespan.

---

### Post by cariboo on 2013-11-20
Actually I'd still like to track down how this problem happened, the discussion about countries monitoring internet traffic really has no place in this sub-forum. @alexying200005, did you have any ports forwarded through your router, or have PnP enabled in the router?

---

### Post by medior on 2013-11-20
Hi alexying200005,

Not sure if you missed my post in between all the off topic noise. But when you notice that the downloads/uploads are happening again could try the commands mentioned in [post #23]("http://ubuntuforums.org/showthread.php?t=2188385&page=3&p=12851760#post12851760").
And yes, I am aware he already posted the output of ss, but that didn't yield any results and there is no harm in trying it again with netstat.

---

### Post by alexying200005 on 2013-11-20
Hi Cariboo907,

No, no port forwarded in my router. Sorry, not sure what PnP is.

I don't think the virus is because of a application i installed.  I think I caught it when browsing the web.  If you know how to list all the applications installed in my ubuntu, i will do it for you.

---

### Post by alexying200005 on 2013-11-20
hi, Medior,

Here is the result of netstat and pstree.  Thx


```

ubuntu2@ubuntu:~$ sudo netstat -nap | grep 117.25
[sudo] password for ubuntu2: 
ubuntu2@ubuntu:~$ pstree -p
init(1)&#9472;&#9516;&#9472;NetworkManager(972)&#9472;&#9516;&#9472;dhclient(1019)
        &#9474;                     &#9500;&#9472;dnsmasq(2407)
        &#9474;                     &#9500;&#9472;{NetworkManager}(976)
        &#9474;                     &#9500;&#9472;{NetworkManager}(977)
        &#9474;                     &#9492;&#9472;{NetworkManager}(979)
        &#9500;&#9472;accounts-daemon(1605)&#9472;&#9516;&#9472;{accounts-daemon}(1613)
        &#9474;                       &#9492;&#9472;{accounts-daemon}(1614)
        &#9500;&#9472;acpid(1228)
        &#9500;&#9472;anacron(1227)
        &#9500;&#9472;avahi-daemon(643)&#9472;&#9472;&#9472;avahi-daemon(644)
        &#9500;&#9472;bluetoothd(614)
        &#9500;&#9472;colord(704)&#9472;&#9516;&#9472;{colord}(734)
        &#9474;             &#9492;&#9472;{colord}(736)
        &#9500;&#9472;console-kit-dae(2226)&#9472;&#9516;&#9472;{console-kit-dae}(2227)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2228)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2229)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2230)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2231)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2232)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2233)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2234)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2235)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2236)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2237)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2238)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2239)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2240)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2241)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2242)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2243)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2244)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2245)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2246)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2247)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2248)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2249)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2250)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2251)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2252)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2253)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2254)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2255)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2256)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2257)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2258)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2259)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2260)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2261)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2262)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2263)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2264)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2265)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2266)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2267)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2268)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2269)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2270)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2271)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2272)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2273)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2274)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2275)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2276)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2277)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2278)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2279)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2280)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2281)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2282)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2283)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2284)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2285)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2286)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2287)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(2288)
        &#9474;                       &#9492;&#9472;{console-kit-dae}(2293)
        &#9500;&#9472;cron(1231)
        &#9500;&#9472;cups-browsed(1047)
        &#9500;&#9472;cupsd(680)&#9472;&#9516;&#9472;dbus(783)
        &#9474;            &#9492;&#9472;dbus(784)
        &#9500;&#9472;dbus-daemon(565)
        &#9500;&#9472;dbus-daemon(2804)
        &#9500;&#9472;dbus-launch(2802)
        &#9500;&#9472;getty(1128)
        &#9500;&#9472;getty(1135)
        &#9500;&#9472;getty(1154)
        &#9500;&#9472;getty(1156)
        &#9500;&#9472;getty(1161)
        &#9500;&#9472;getty(1586)
        &#9500;&#9472;gnome-keyring-d(2687)&#9472;&#9516;&#9472;{gnome-keyring-d}(2688)
        &#9474;                       &#9500;&#9472;{gnome-keyring-d}(3044)
        &#9474;                       &#9500;&#9472;{gnome-keyring-d}(3045)
        &#9474;                       &#9500;&#9472;{gnome-keyring-d}(3059)
        &#9474;                       &#9492;&#9472;{gnome-keyring-d}(3186)
        &#9500;&#9472;lightdm(1290)&#9472;&#9516;&#9472;Xorg(1333)
        &#9474;               &#9500;&#9472;lightdm(1906)&#9472;&#9516;&#9472;init(2689)&#9472;&#9516;&#9472;/usr/bin/termin(3314)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;/usr/bin/termin(3439)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;at-spi-bus-laun(2862)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;at-spi2-registr(2877)&#9472;&#9472;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;bamfdaemon(2855)&#9472;&#9516;&#9472;{bamf+
        &#9474;               &#9474;               &#9474;            &#9474;                  &#9500;&#9472;{bamf+
        &#9474;               &#9474;               &#9474;            &#9474;                  &#9492;&#9472;{bamf+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;dbus-daemon(2821)
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;dconf-service(3125)&#9472;&#9516;&#9472;{d+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9492;&#9472;{d+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;evolution-calen(3219)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;evolution-sourc(3177)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gconfd-2(3227)
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gnome-screensav(3123)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gnome-session(2958)&#9472;&#9516;&#9472;co+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;de+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;gn+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;na+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;nm+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;po+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;te+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;up+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;ze+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;{g+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;{g+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9500;&#9472;{g+
        &#9474;               &#9474;               &#9474;            &#9474;                     &#9492;&#9472;{g+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gnome-settings-(2949)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gvfs-afc-volume(3249)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gvfs-gphoto2-vo(3259)&#9472;&#9472;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gvfs-mtp-volume(3239)&#9472;&#9472;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gvfs-udisks2-vo(3216)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gvfsd(2880)&#9472;&#9472;&#9472;{gvfsd}(28+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gvfsd-burn(3309)&#9472;&#9472;&#9472;{gvfs+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gvfsd-fuse(2893)&#9472;&#9516;&#9472;{gvfs+
        &#9474;               &#9474;               &#9474;            &#9474;                  &#9500;&#9472;{gvfs+
        &#9474;               &#9474;               &#9474;            &#9474;                  &#9500;&#9472;{gvfs+
        &#9474;               &#9474;               &#9474;            &#9474;                  &#9492;&#9472;{gvfs+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;gvfsd-trash(3269)&#9472;&#9516;&#9472;{gvf+
        &#9474;               &#9474;               &#9474;            &#9474;                   &#9492;&#9472;{gvf+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;hud-service(2954)&#9472;&#9516;&#9472;{hud+
        &#9474;               &#9474;               &#9474;            &#9474;                   &#9492;&#9472;{hud+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-appli(3075)&#9472;&#9472;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-bluet(3050)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-datet(3066)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-keybo(3062)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-messa(3063)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9500;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-power(3064)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-print(3067)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-sessi(3051)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-sound(3065)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;indicator-sync-(3028)&#9472;&#9472;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;notify-osd(3176)&#9472;&#9516;&#9472;{noti+
        &#9474;               &#9474;               &#9474;            &#9474;                  &#9492;&#9472;{noti+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;pulseaudio(3095)&#9472;&#9516;&#9472;{puls+
        &#9474;               &#9474;               &#9474;            &#9474;                  &#9492;&#9472;{puls+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;ssh-agent(2818)
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;unity-panel-ser(2964)&#9472;&#9516;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9474;                       &#9492;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;upstart-dbus-br(2859)
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;upstart-dbus-br(2860)
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;upstart-event-b(2827)
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;upstart-file-br(2856)
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;vmtoolsd(3162)&#9472;&#9516;&#9472;{vmtool+
        &#9474;               &#9474;               &#9474;            &#9474;                &#9492;&#9472;{vmtool+
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;window-stack-br(2830)
        &#9474;               &#9474;               &#9474;            &#9500;&#9472;zeitgeist-daemo(3414)&#9472;&#9472;&#9472;+
        &#9474;               &#9474;               &#9474;            &#9492;&#9472;zeitgeist-fts(3422)&#9472;&#9516;&#9472;ca+
        &#9474;               &#9474;               &#9474;                                  &#9492;&#9472;{z+
        &#9474;               &#9474;               &#9492;&#9472;{lightdm}(2656)
        &#9474;               &#9500;&#9472;{lightdm}(1322)
        &#9474;               &#9492;&#9472;{lightdm}(1334)
        &#9500;&#9472;master(1428)&#9472;&#9516;&#9472;pickup(2644)
        &#9474;              &#9492;&#9472;qmgr(2645)
        &#9500;&#9472;modem-manager(913)
        &#9500;&#9472;nmbd(2607)
        &#9500;&#9472;polkitd(981)&#9472;&#9516;&#9472;{polkitd}(984)
        &#9474;              &#9492;&#9472;{polkitd}(986)
        &#9500;&#9472;rsyslogd(630)&#9472;&#9516;&#9472;{rsyslogd}(633)
        &#9474;               &#9500;&#9472;{rsyslogd}(636)
        &#9474;               &#9492;&#9472;{rsyslogd}(637)
        &#9500;&#9472;rtkit-daemon(2210)&#9472;&#9516;&#9472;{rtkit-daemon}(2212)
        &#9474;                    &#9492;&#9472;{rtkit-daemon}(2213)
        &#9500;&#9472;smbd(832)&#9472;&#9472;&#9472;smbd(860)
        &#9500;&#9472;systemd-localed(3121)
        &#9500;&#9472;systemd-logind(616)
        &#9500;&#9472;systemd-udevd(534)
        &#9500;&#9472;tpvmlp(1145)&#9472;&#9472;&#9472;tpvmlp(3568)
        &#9500;&#9472;udisksd(3222)&#9472;&#9516;&#9472;{udisksd}(3223)
        &#9474;               &#9500;&#9472;{udisksd}(3225)
        &#9474;               &#9500;&#9472;{udisksd}(3228)
        &#9474;               &#9492;&#9472;{udisksd}(3230)
        &#9500;&#9472;upowerd(1839)&#9472;&#9516;&#9472;{upowerd}(1845)
        &#9474;               &#9492;&#9472;{upowerd}(1846)
        &#9500;&#9472;upstart-file-br(742)
        &#9500;&#9472;upstart-socket-(1018)
        &#9500;&#9472;upstart-udev-br(530)
        &#9492;&#9472;whoopsie(1233)&#9472;&#9516;&#9472;{whoopsie}(1234)
                         &#9500;&#9472;{whoopsie}(1238)
                         &#9492;&#9472;{whoopsie}(3577)




```

---

### Post by alexying200005 on 2013-11-20
hi,

i am wondering if it is true that different linux version has the same kernel but different default applications installed. 

Different combinations of applications installed may make your computer harder to get virus. That is what i think.  Of course, if the virus attacks at the kernel level, then yes, no other linux version will behave differently.

I am just telling why i would like to try linux, not want to start a political talk in the thread.  When somebody asks me why someone wants to spy on you, i want to laugh. It is like asking why you want freedom, i keep you alive but monitoring everything you do, isn't it a beautiful thing?  

For the virus i got, i did not see any data uploading in nethogs or iftop.  So, i suspect it did not steal my personal info.  but again, the virus may just steal it already at the beginning.

---

### Post by cariboo on 2013-11-20
@alexying200005, you can check if you have UPnP enabled by going [here]("https://www.grc.com/x/ne.dll?rh1dkyd2").

---

### Post by Irihapeti on 2013-11-20
Cariboo907

Your link gives a page reload error. To the OP, to access the function, you need to go to [www.grc.com](www.grc.com), then choose "Shields up" from the Services menu.

---

### Post by alexying200005 on 2013-11-20
Hi Cariboo907,

here is the result of uPnp.


THE EQUIPMENT AT THE TARGET IP ADDRESS
ACTIVELY REJECTED OUR UPnP PROBES!

---

### Post by bashiergui on 2013-11-21
Find out what services are installed & running on your system. 
```
sudo service --status-all
```


Then find out what TCP and UDP ports are listening for connections:
```
ss -t -l
```
```
ss -u -l
```


You want to know if any cron jobs have been created and run:
```
grep CRON /var/log/syslog
```


Then let's see who we have logged into the computer right now.
```
w
```


Do you see any unexpected users created on the computer? This is a big file. 
```
more /etc/passwd
```


Then open the Log File Viewer application from your Dash. Look at the auth logs for successful and failed logon attempts from anyone other than yourself.
(View the /var/log/auth.log)

---

### Post by alexying200005 on 2013-11-21
Bashiergui,

Thanks for the info. here is the service command.


```

ubuntu2@ubuntu:~$ sudo service --status-all
[sudo] password for ubuntu2: 
 [ + ]  acpid
 [ + ]  anacron
 [ + ]  apparmor
 [ ? ]  apport
 [ + ]  avahi-daemon
 [ ? ]  binfmt-support
 [ + ]  bluetooth
 [ - ]  brltty
 [ + ]  console-font
 [ + ]  console-setup
 [ + ]  cron
 [ + ]  cups
 [ + ]  cups-browsed
 [ - ]  dbus
 [ ? ]  dns-clean
 [ + ]  friendly-recovery
 [ - ]  grub-common
 [ ? ]  irqbalance
 [ - ]  kerneloops
 [ ? ]  killprocs
 [ + ]  kmod
 [ ? ]  lightdm
 [ ? ]  networking
 [ + ]  nmbd
 [ ? ]  ondemand
 [ + ]  postfix
 [ ? ]  pppd-dns
 [ - ]  procps
 [ - ]  pulseaudio
 [ ? ]  rc.local
 [ + ]  resolvconf
 [ + ]  rfkill-restore
 [ + ]  rfkill-store
 [ - ]  rsync
 [ + ]  rsyslog
 [ + ]  samba
 [ + ]  saned
 [ ? ]  sendsigs
 [ + ]  setvtrgb
 [ + ]  smbd
 [ ? ]  speech-dispatcher
 [ - ]  sudo
 [ + ]  udev
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
 [ - ]  x11-common
ubuntu2@ubuntu:~$ 




```

---

### Post by alexying200005 on 2013-11-21
The grep cron command.

```

ubuntu2@ubuntu:~$ grep CRON /var/log/syslog
Nov 16 09:17:01 ubuntu CRON[5556]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 16 10:17:01 ubuntu CRON[8058]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 16 11:17:01 ubuntu CRON[11683]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 16 11:21:04 ubuntu cron[1108]: (CRON) INFO (pidfile fd = 3)
Nov 16 11:21:04 ubuntu cron[1192]: (CRON) STARTUP (fork ok)
Nov 16 11:21:04 ubuntu cron[1192]: (CRON) INFO (Running @reboot jobs)
Nov 16 12:14:33 ubuntu cron[1138]: (CRON) INFO (pidfile fd = 3)
Nov 16 12:14:33 ubuntu cron[1214]: (CRON) STARTUP (fork ok)
Nov 16 12:14:33 ubuntu cron[1214]: (CRON) INFO (Running @reboot jobs)
Nov 16 14:01:24 ubuntu cron[1132]: (CRON) INFO (pidfile fd = 3)
Nov 16 14:01:24 ubuntu cron[1244]: (CRON) STARTUP (fork ok)
Nov 16 14:01:24 ubuntu cron[1244]: (CRON) INFO (Running @reboot jobs)
Nov 16 14:18:37 ubuntu cron[1134]: (CRON) INFO (pidfile fd = 3)
Nov 16 14:18:37 ubuntu cron[1231]: (CRON) STARTUP (fork ok)
Nov 16 14:18:37 ubuntu cron[1231]: (CRON) INFO (Running @reboot jobs)
Nov 16 14:29:42 ubuntu cron[1189]: (CRON) INFO (pidfile fd = 3)
Nov 16 14:29:42 ubuntu cron[1273]: (CRON) STARTUP (fork ok)
Nov 16 14:29:42 ubuntu cron[1273]: (CRON) INFO (Running @reboot jobs)
Nov 16 14:33:53 ubuntu cron[1143]: (CRON) INFO (pidfile fd = 3)
Nov 16 14:33:53 ubuntu cron[1222]: (CRON) STARTUP (fork ok)
Nov 16 14:33:53 ubuntu cron[1222]: (CRON) INFO (Running @reboot jobs)
Nov 16 23:28:12 ubuntu cron[1137]: (CRON) INFO (pidfile fd = 3)
Nov 16 23:28:12 ubuntu cron[1211]: (CRON) STARTUP (fork ok)
Nov 16 23:28:12 ubuntu cron[1211]: (CRON) INFO (Running @reboot jobs)
Nov 16 23:43:38 ubuntu cron[1124]: (CRON) INFO (pidfile fd = 3)
Nov 16 23:43:38 ubuntu cron[1189]: (CRON) STARTUP (fork ok)
Nov 16 23:43:38 ubuntu cron[1189]: (CRON) INFO (Running @reboot jobs)
Nov 17 08:45:00 ubuntu cron[1134]: (CRON) INFO (pidfile fd = 3)
Nov 17 08:45:00 ubuntu cron[1214]: (CRON) STARTUP (fork ok)
Nov 17 08:45:00 ubuntu cron[1214]: (CRON) INFO (Running @reboot jobs)
Nov 17 08:50:51 ubuntu cron[1130]: (CRON) INFO (pidfile fd = 3)
Nov 17 08:50:51 ubuntu cron[1208]: (CRON) STARTUP (fork ok)
Nov 17 08:50:51 ubuntu cron[1208]: (CRON) INFO (Running @reboot jobs)
Nov 17 09:17:01 ubuntu CRON[46389]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 17 10:44:50 ubuntu cron[1131]: (CRON) INFO (pidfile fd = 3)
Nov 17 10:44:50 ubuntu cron[1192]: (CRON) STARTUP (fork ok)
Nov 17 10:44:50 ubuntu cron[1192]: (CRON) INFO (Running @reboot jobs)
Nov 17 10:46:42 ubuntu cron[1137]: (CRON) INFO (pidfile fd = 3)
Nov 17 10:46:42 ubuntu cron[1199]: (CRON) STARTUP (fork ok)
Nov 17 10:46:42 ubuntu cron[1199]: (CRON) INFO (Running @reboot jobs)
Nov 17 11:17:01 ubuntu CRON[4091]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 17 11:19:03 ubuntu cron[1144]: (CRON) INFO (pidfile fd = 3)
Nov 17 11:19:03 ubuntu cron[1207]: (CRON) STARTUP (fork ok)
Nov 17 11:19:03 ubuntu cron[1207]: (CRON) INFO (Running @reboot jobs)
Nov 17 11:33:56 ubuntu cron[1154]: (CRON) INFO (pidfile fd = 3)
Nov 17 11:33:56 ubuntu cron[1216]: (CRON) STARTUP (fork ok)
Nov 17 11:33:56 ubuntu cron[1216]: (CRON) INFO (Running @reboot jobs)
Nov 20 09:20:12 ubuntu cron[1148]: (CRON) INFO (pidfile fd = 3)
Nov 20 09:20:12 ubuntu cron[1209]: (CRON) STARTUP (fork ok)
Nov 20 09:20:12 ubuntu cron[1209]: (CRON) INFO (Running @reboot jobs)
Nov 20 09:21:36 ubuntu cron[1138]: (CRON) INFO (pidfile fd = 3)
Nov 20 09:21:36 ubuntu cron[1231]: (CRON) STARTUP (fork ok)
Nov 20 09:21:36 ubuntu cron[1231]: (CRON) INFO (Running @reboot jobs)
Nov 20 16:01:35 ubuntu cron[1147]: (CRON) INFO (pidfile fd = 3)
Nov 20 16:01:36 ubuntu cron[1211]: (CRON) STARTUP (fork ok)
Nov 20 16:01:36 ubuntu cron[1211]: (CRON) INFO (Running @reboot jobs)
Nov 20 17:58:49 ubuntu cron[1140]: (CRON) INFO (pidfile fd = 3)
Nov 20 17:58:49 ubuntu cron[1218]: (CRON) STARTUP (fork ok)
Nov 20 17:58:49 ubuntu cron[1218]: (CRON) INFO (Running @reboot jobs)
Nov 20 19:35:00 ubuntu cron[1052]: (CRON) INFO (pidfile fd = 3)
Nov 20 19:35:00 ubuntu cron[1232]: (CRON) STARTUP (fork ok)
Nov 20 19:35:01 ubuntu cron[1232]: (CRON) INFO (Running @reboot jobs)
Nov 20 20:59:02 ubuntu cron[1112]: (CRON) INFO (pidfile fd = 3)
Nov 20 20:59:03 ubuntu cron[1208]: (CRON) STARTUP (fork ok)
Nov 20 20:59:03 ubuntu cron[1208]: (CRON) INFO (Running @reboot jobs)
Nov 20 21:17:01 ubuntu CRON[4672]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 20 22:17:01 ubuntu CRON[5950]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 20 23:17:01 ubuntu CRON[7310]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 21 06:12:51 ubuntu cron[1050]: (CRON) INFO (pidfile fd = 3)
Nov 21 06:12:51 ubuntu cron[1198]: (CRON) STARTUP (fork ok)
Nov 21 06:12:51 ubuntu cron[1198]: (CRON) INFO (Running @reboot jobs)
Nov 21 06:15:58 ubuntu cron[1050]: (CRON) INFO (pidfile fd = 3)
Nov 21 06:15:58 ubuntu cron[1134]: (CRON) STARTUP (fork ok)
Nov 21 06:15:58 ubuntu cron[1134]: (CRON) INFO (Running @reboot jobs)
Nov 21 06:17:01 ubuntu CRON[3656]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
ubuntu2@ubuntu:~$ 



```

---

### Post by alexying200005 on 2013-11-21
w command. why it says 2 users? does anybody know? I only login as ubuntu2

```


ubuntu2@ubuntu:~$ w
 06:21:52 up 6 min,  2 users,  load average: 0.01, 0.15, 0.11
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
ubuntu2  tty7     :0               06:16    5:55   5.91s  0.04s init --user
ubuntu2  pts/1    :0               06:16    0.00s  0.03s  0.00s w
ubuntu2@ubuntu:~$ 



```

---

### Post by alexying200005 on 2013-11-21
more passwd command.  It is not too big for me.

```

ubuntu2@ubuntu:~$ more /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:106:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
usbmux:x:104:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq:x:105:65534:dnsmasq,,,:/var/lib/misc:/bin/false
whoopsie:x:106:110::/nonexistent:/bin/false
kernoops:x:107:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit:x:108:114:RealtimeKit,,,:/proc:/bin/false
speech-dispatcher:x:109:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/
sh
lightdm:x:110:116:Light Display Manager:/var/lib/lightdm:/bin/false
avahi:x:111:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
colord:x:112:120:colord colour management daemon,,,:/var/lib/colord:/bin/false
pulse:x:113:121:PulseAudio daemon,,,:/var/run/pulse:/bin/false
hplip:x:114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:115:123::/home/saned:/bin/false
ubuntu2:x:1000:1000:ubuntu2,,,:/home/ubuntu2:/bin/bash
testing:x:1001:1001:testing,,,:/home/testing:/bin/bash
guest-G5t3Pm:x:116:125:Guest,,,:/tmp/guest-G5t3Pm:/bin/bash
postfix:x:117:126::/var/spool/postfix:/bin/false
ubuntu2@ubuntu:~$ 




```

---

### Post by alexying200005 on 2013-11-21
ss command.

```


ubuntu2@ubuntu:~$ ss -t -l
State      Recv-Q Send-Q                     Local Address:Port                         Peer Address:Port   
LISTEN     0      50                                     *:microsoft-ds                                 *:*       
LISTEN     0      50                                     *:netbios-ssn                                 *:*       
LISTEN     0      5                              127.0.1.1:domain                                  *:*       
LISTEN     0      128                            127.0.0.1:ipp                                     *:*       
LISTEN     0      100                                    *:smtp                                    *:*       
LISTEN     0      50                                    :::microsoft-ds                                :::*       
LISTEN     0      50                                    :::netbios-ssn                                :::*       
LISTEN     0      128                                  ::1:ipp                                    :::*       
LISTEN     0      100                                   :::smtp                                   :::*       
ubuntu2@ubuntu:~$ ss -u -l
State      Recv-Q Send-Q                     Local Address:Port                         Peer Address:Port   
UNCONN     0      0                                      *:48036                                   *:*       
UNCONN     0      0                                      *:mdns                                    *:*       
UNCONN     0      0                              127.0.1.1:domain                                  *:*       
UNCONN     0      0                                      *:bootpc                                  *:*       
UNCONN     0      0                        192.168.126.255:netbios-ns                                 *:*       
UNCONN     0      0                        192.168.126.150:netbios-ns                                 *:*       
UNCONN     0      0                                      *:netbios-ns                                 *:*       
UNCONN     0      0                        192.168.126.255:netbios-dgm                                 *:*       
UNCONN     0      0                        192.168.126.150:netbios-dgm                                 *:*       
UNCONN     0      0                                      *:netbios-dgm                                 *:*       
UNCONN     0      0                                      *:47501                                   *:*       
UNCONN     0      0                                      *:ipp                                     *:*       
UNCONN     0      0                                     :::mdns                                   :::*       
UNCONN     0      0                                     :::43466                                  :::*       
UNCONN     0      0                                     :::35583                                  :::*       
ubuntu2@ubuntu:~$ 



```

iftop command.

```








&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
ubuntu.local                              => 117.25.130.43                                0b      0b      0b
                                          <=                                           4.91Mb  4.91Mb  4.81Mb
ubuntu.local                              => 224.0.0.251                                296b    581b    621b
                                          <=                                              0b      0b      0b
ubuntu.local                              => 192.168.126.2                                0b    174b    249b
                                          <=                                              0b    314b    417b
192.168.126.255                           => 192.168.126.129                              0b      0b      0b
                                          <=                                              0b    163b    117b




















&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
TX:             cum:   1.49kB   peak:   1.41kb                                rates:    296b    755b    870b
RX:                    9.02MB           4.91Mb                                         4.91Mb  4.91Mb  4.81Mb
TOTAL:                 9.03MB           4.91Mb                                         4.91Mb  4.91Mb  4.81Mb


```

nethogs command.


```

NetHogs version 0.8.0


  PID USER     PROGRAM                                                    DEV        SENT      RECEIVED       
?     root     192.168.126.150:56629-117.25.130.43:84                                0.000     591.181 KB/sec
?     root     unknown TCP                                                           0.000       0.000 KB/sec


  TOTAL                                                                              0.000     591.181 KB/sec 

```

---

### Post by bashiergui on 2013-11-21
> **alexying200005 said:**
> w command. why it says 2 users? does anybody know? I only login as ubuntu2 
That's just you (1) logged into the system and you (2) running "w" in a terminal.

So far I don't see anything alarming. You could look at the /etc/cron.hourly file and the auth logs (see my first post) if you wanted to keep digging. Check the syslogs and auth logs for missing blocks of time you know you were active or wrong time stamps.

Looks to me like you were the client in that original TCP connection to China. I wonder if it's just a remnant from an ad you encountered in a browsing session. If you were the server then I'd be more concerned. You blocked the IP in iptables. If it were me I would probably watch my internet traffic for any other odd behavior, maybe run this sometimes when I'm browsing```
 sudo watch ss -t -l
``` I'd use an ad blocker or a javascript blocker in my browser.

---

### Post by alexying200005 on 2013-11-22
[COLOR=#000000]Hi, Bashiergui,

Thank you very much for helping. what you said makes sense to me.  do you know how to get rid of this remnant behavior ? I know that internet traffic to that IP is blocked.  but, everytime i login, i see full network bandwidth in the system monitor, it make me feel uncomfortable. I know i can re-install ubuntu. I just wonder if there is an alternative way.[/COLOR]

---

### Post by bashiergui on 2013-11-22
> **alexying200005 said:**
> [COLOR=#000000] everytime i login, i see full network bandwidth in the system monitor, it make me feel uncomfortable. I know i can re-install ubuntu. [/COLOR] you feel uncomfortable without any evidence? figure out what is using the bandwidth. Use ```
top
``` and ```
ss
``` to see the processes and connections.  Google the IPs and the services. If any of them are not typical for Ubuntu then you should feel uncomfortable.

---

### Post by alexying200005 on 2013-11-22
I have my system monitor open at the top bar. I use the system monitor to monitor cpu, disk read/write and network activity. Whenever i login, the network activity monitor shows full download bandwidth. I believe there is nothing that is downloading since the remote ip is block. But I can not use the network monitor to monitor network activity since it is at full bandwidth all the time.

---

### Post by leeper69 on 2013-11-22
It may be to late for this but firestarter has a good port watcher I also had problemes with a hacker from china on my machine about 3 years ago after formatting and reinstalling my desktop, installing firestarter and changing my sudo  or root password I closed down his intrusion on my system. I dont know if this is a virus or just a hack but if all else fails this may work for you too. be shure to change your sudo password.
here is a good site on linux viruses [http://www.tecmint.com/linux-operating-system-is-virus-free/](http://www.tecmint.com/linux-operating-system-is-virus-free/)
if you decide to use firestarter and need help setting it up let me know. ( I could only find it in the ubuntu 12.4 repositoryes what a shame as this is such a fine graphical port watcher and firewall to use for intrusion problems. )
here are 5 more for ubuntu at omgubuntu.co.uk/2011/11/5-system-monitoring-tools-for-ubuntu

---

### Post by alexying200005 on 2013-11-23
Hi Leeper69,

Thanks for the info.  Can not find firestarter in software center. So, i don't know how to install it.  also, it is not under active development.  it looks like all firewalls are script editor of iptables in linux.

---

### Post by leeper69 on 2013-11-23
Hi alix200005
 what version of ubuntu are you using?
I just downloaded a copy 2 days ago using xubuntu version 12.4 but if you are using 13.10 or 14.04 it has ben removed, what a shame as it was a fine tcp and udp port watcher.
if you arnt terminal shy there are netstat and tracerout tools and a lot more. it would be nice if ubuntu would come out with a security and grubrepair in a buntu.
I found another tool or two that can be used to find out what ports are comprimized on your system, just follow the links below.

[http://www.unixmen.com/how-to-blok-port-scan-attacks-with-psad-on-ubuntu-debian/](http://www.unixmen.com/how-to-blok-port-scan-attacks-with-psad-on-ubuntu-debian/)

[http://www.binarytides.com/top-port-scanners-on-ubuntu-linux/](http://www.binarytides.com/top-port-scanners-on-ubuntu-linux/)

these tools wil help you find the tcp or udp ports your hacker has used to get in then there are terminal tools to track down and isolate the server your hacker is using
such as netstat and tracerout,or you can use psad to set up iptabels and finaly you can use gufw firewall to denie service from his ip address. sory things just got a lot more complicated with the removal of firestarter.

---

### Post by alexying200005 on 2013-11-27
Hi Leeper69,

Thanks a lot for helping. I was using ubuntu 13.1. Now, I am using Kubuntu 13.1.  I gave up ubuntu 13.1 already.
I used clamTk to scan for virus in Kubuntu 13.1 and the program gave some warnings in firefox cache directory. I always use firefox to access internet. so, i am thinking making firefox more secure may be worth spending my time.

One thing concerns me though. Prism-break does not list ubuntu as a recommended OS.  The reason may be ubuntu's intention of gathering personal data from users for business purpose.  Well, for now, i choose to trust ubuntu. But i will use Kubuntu only.  We will see what will happen in future.  

Any tips on how to use firefox in a secure way?  i use firefox 25.0.1.

---

### Post by claracc on 2013-11-27
Here, [http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604), you have a very good tutorial written by bodhi.zazen about how to do firefox more secure.

---

### Post by alexying200005 on 2013-11-27
I will disable javascript and java applet in my firefox for now. Hopefully, it wil stop most of  viruses.

---

### Post by leeper69 on 2013-11-27
Hi I found a good site on linux security here is the url
[http://www.linuxsecurity.com/content/view/160436/169/](http://www.linuxsecurity.com/content/view/160436/169/)
komoto antivirus now for linux check it out if you have used it in windows.

---

### Post by alexying200005 on 2013-11-29
Hi leeper69,

thanks for the info.  can not find komoto in software center in Kubuntu.   The only anti-virus app i can find is clamTk( same as calmAV ).  I  installed clamTk. it works ok. but i did not know how to upgrade it to  the new version( 5.0)

---

### Post by thatredbird on 2013-11-29
Mis posted my mistake and appologies

---

### Post by leeper69 on 2013-11-29
Hi you can download komodo antivirus from there web page. I am using it now in ubuntu 12.4  just click on the url below. pick 32 bit or 64 bit download and open the saved .deb file with ubuntu software center. cant get it to run in 13.10.
[http://www.comodo.com/home/internet-security/antivirus-for-linux.php](http://www.comodo.com/home/internet-security/antivirus-for-linux.php)

---

### Post by monkeybrain20122 on 2013-11-29
> **alexying200005 said:**
> Hi Leeper69,

One thing concerns me though. Prism-break does not list ubuntu as a recommended OS.  The reason may be ubuntu's intention of gathering personal data from users for business purpose.  Well, for now, i choose to trust ubuntu. But i will use Kubuntu only.  We will see what will happen in future.  
.

There is no collection of personal data, it is that your dash search gets sent to Canonical's server which then gets relay to the targetted servers like Amazon, there is no tracking or anything and Canonical doesn't go through your /home. If you are uncomfortable with it you can simply disable the feature by one click from System Settings > Privacy Settings.

---

### Post by leeper69 on 2013-11-29
Hi monkeybrain20122 what are you talking about? I will need to look up prisem-break I am not worried about ubuntu it is more inportent to dule booters still using windows and wine to use antivirus, but thanks for the tip! here is the url for prism-break
[http://www.prism-break.org](http://www.prism-break.org)
Hi alexying200005
after reading your full post I have found a lot of terminal commands i did not know about but havent seen anyone have you  try this,( sudo netstat -punt )  this command will tell you what pid number is assined to each open udp and tcp port if you run it without being connected to the net with firefox or any other local program you should be able to find the ip that is reciving your data. then you can eather put the ip in your firewall to block it or just disconect from the ip by opening gnome system monitor and finding the pid which is in the id fild under the processes tab  and right clicking on it to kill or disable the pid which will stop the program your hacker is using.
hope this helps!

---

### Post by alexying200005 on 2013-12-01
Hi Leeper69,

Thanks a lot for your help.

I just logged in to ubuntu.  Surprisingly, ubuntu did not receive data from the Chinese ip like it did in the past.  I did not do anything.  It just stopped itself.   So, i can't see if your command is useful.  I will try it time to time.  But as I say, i am using Kubuntu from now on.

---

### Post by leeper69 on 2013-12-01
Hi alexying200005 glad to be of service. found anoher url about the new worm in linux, 
[http://www.pcworld.com/article/2067700/worm-targets-linux-pcs-and-embeded-devices.html](http://www.pcworld.com/article/2067700/worm-targets-linux-pcs-and-embeded-devices.html)

---

### Post by theDaveTheRave on 2013-12-09
Hi all,

just adding my few pennies worth of info.

I had a lot of issues in one location I used to be at, and I got into a lot of network monitoring stuff.

the 2 things I found most usefull where nmap and  traceroute, below are sample outputs for my machine.

```

~$ nmap 127.0.0.1

Starting Nmap 6.00 ( http://nmap.org ) at 2013-12-09 21:40 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0013s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
80/tcp   open  http
631/tcp  open  ipp
3306/tcp open  mysql
9090/tcp open  zeus-admin

Nmap done: 1 IP address (1 host up) scanned in 0.37 seconds

```
As you can see it lists any services with thier open ports.
You should try this on the remote IP that is / was sending you data, it may be interesting.
You don't want to do this too often to a single site, as it is also something hackers do, and can result in getting your ip blacklisted as it pulls a lot of resources off of terminal you are mapping.

a traceroute to google is always interesting...
```

~$ traceroute www.google.com
traceroute to www.google.com (173.194.40.210), 30 hops max, 60 byte packets
 1  xxx.xxx.x.x (xxx.xxx.x.x)  2.064 ms  2.750 ms  2.666 ms
 2  xxx.xxx.x.x (xxx.xxx.x.x)  10.011 ms  14.395 ms  15.085 ms
 3  mrs1rj-ae0.100.numericable.net (80.236.6.22)  14.917 ms  14.792 ms  14.702 ms
 4  ip-214.net-80-236-0.static.numericable.fr (80.236.0.214)  14.658 ms  14.624 ms  14.529 ms
 5  ip-209.net-80-236-0.static.numericable.fr (80.236.0.209)  16.673 ms  16.566 ms  16.405 ms
 6  * 172.19.128.170 (172.19.128.170)  13.286 ms  10.916 ms
 7  ip-161.net-80-236-1.static.numericable.fr (80.236.1.161)  10.101 ms  10.734 ms  13.521 ms
 8  72.14.239.205 (72.14.239.205)  42.388 ms  22.008 ms  21.993 ms
 9  209.85.243.51 (209.85.243.51)  14.360 ms  14.329 ms  14.291 ms
10  par10s12-in-f18.1e100.net (173.194.40.210)  14.057 ms  20.304 ms  21.372 ms

```

it may be interesting to see where the IP address that is being connected to is passing through.
Reputable ISPs aren't keen to have 'rogue' or 'hacker' IP addresses connecting via them, so they may be equally interested in getting this IP address blacklisted.

Good luck with your security searches, and with Ubuntu (or for you apparently K).

David

---

### Post by cariboo on 2013-12-09
+1 for using nmap, although to get the proper result, it should be run from another system on your internal network, as you will get different results form when run form localhost.

I prefer mtr over traceroute, see the screenshot, it's less to type. :-)

---

### Post by leeper69 on 2013-12-12
Hi alexying200005 you might want to run rkhunter to see if a rootkit has ben installed it can be downloaded from ubuntu software center and can be found with the serch bar at the top of the page. this is good software.
good luck and let me know if this helped.

---

### Post by alexying200005 on 2013-12-17
David, cariboo907 and leeper69,

thank you all for helping. I will try all your methods.

---

### Post by Irihapeti on 2013-12-17
If you're going to run rkhunter, first of all [read up about the false positives]("http://ubuntuforums.org/showthread.php?t=2105390").  Many people jump to the conclusion that they've been infected when in fact the result is a known false positive.

Also read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") in this forum, if you haven't already.

---

