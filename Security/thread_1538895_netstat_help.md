---
title: "netstat help"
date: 2010-07-25
forum: Security
---

### Post by andthewicked on 2010-07-25
Even when I'm not connect to any website or even when I manually take the wireless adapter down it still shows a whole mess of things can someone take a look at this netstat file I just ran with nothing open and tell me what I'm looking at?

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    2910     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    5138     @/org/freedesktop/hal/udev_event
unix  16     [ ]         DGRAM                    4284     /dev/log
unix  3      [ ]         STREAM     CONNECTED     12274    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12273    
unix  2      [ ]         DGRAM                    12272    
unix  3      [ ]         STREAM     CONNECTED     12121    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12120    
unix  3      [ ]         STREAM     CONNECTED     12019    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     12018    
unix  3      [ ]         STREAM     CONNECTED     12017    /tmp/orbit-kyle/linc-b3f-0-1bedf9f8961e9
unix  3      [ ]         STREAM     CONNECTED     12016    
unix  3      [ ]         STREAM     CONNECTED     12015    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     12014    
unix  3      [ ]         STREAM     CONNECTED     12013    /tmp/orbit-kyle/linc-9af-0-2b793fe7a5d37
unix  3      [ ]         STREAM     CONNECTED     12012    
unix  3      [ ]         STREAM     CONNECTED     12011    /tmp/orbit-kyle/linc-b3f-0-1bedf9f8961e9
unix  3      [ ]         STREAM     CONNECTED     12010    
unix  3      [ ]         STREAM     CONNECTED     12009    /tmp/orbit-kyle/linc-b3b-0-19cdf3cd6123b
unix  3      [ ]         STREAM     CONNECTED     12008    
unix  3      [ ]         STREAM     CONNECTED     12006    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     12005    
unix  3      [ ]         STREAM     CONNECTED     12004    /tmp/orbit-kyle/linc-b3f-0-1bedf9f8961e9
unix  3      [ ]         STREAM     CONNECTED     12003    
unix  3      [ ]         STREAM     CONNECTED     12002    /tmp/orbit-kyle/linc-998-0-29e5093e64fb3
unix  3      [ ]         STREAM     CONNECTED     11999    
unix  3      [ ]         STREAM     CONNECTED     11947    /tmp/orbit-kyle/linc-b3b-0-19cdf3cd6123b
unix  3      [ ]         STREAM     CONNECTED     11946    
unix  3      [ ]         STREAM     CONNECTED     11945    /tmp/orbit-kyle/linc-998-0-29e5093e64fb3
unix  3      [ ]         STREAM     CONNECTED     11944    
unix  3      [ ]         STREAM     CONNECTED     11942    /tmp/orbit-kyle/linc-b3b-0-19cdf3cd6123b
unix  3      [ ]         STREAM     CONNECTED     11941    
unix  3      [ ]         STREAM     CONNECTED     11938    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     11937    
unix  3      [ ]         STREAM     CONNECTED     11935    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     11934    
unix  3      [ ]         STREAM     CONNECTED     11933    @/tmp/.ICE-unix/2286
unix  3      [ ]         STREAM     CONNECTED     11932    
unix  3      [ ]         STREAM     CONNECTED     11928    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11927    
unix  3      [ ]         STREAM     CONNECTED     11920    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11919    
unix  3      [ ]         STREAM     CONNECTED     11918    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     11917    
unix  3      [ ]         STREAM     CONNECTED     11915    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     11914    
unix  3      [ ]         STREAM     CONNECTED     11913    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11912    
unix  3      [ ]         STREAM     CONNECTED     11869    /tmp/orbit-kyle/linc-9af-0-2b793fe7a5d37
unix  3      [ ]         STREAM     CONNECTED     11868    
unix  3      [ ]         STREAM     CONNECTED     11867    /tmp/orbit-kyle/linc-998-0-29e5093e64fb3
unix  3      [ ]         STREAM     CONNECTED     11866    
unix  3      [ ]         STREAM     CONNECTED     11863    /tmp/orbit-kyle/linc-9af-0-2b793fe7a5d37
unix  3      [ ]         STREAM     CONNECTED     11862    
unix  3      [ ]         STREAM     CONNECTED     11859    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     11858    
unix  3      [ ]         STREAM     CONNECTED     11856    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     11855    
unix  3      [ ]         STREAM     CONNECTED     11854    @/tmp/.ICE-unix/2286
unix  3      [ ]         STREAM     CONNECTED     11853    
unix  3      [ ]         STREAM     CONNECTED     11849    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11848    
unix  3      [ ]         STREAM     CONNECTED     11455    
unix  3      [ ]         STREAM     CONNECTED     11454    
unix  3      [ ]         STREAM     CONNECTED     11451    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     11450    
unix  3      [ ]         STREAM     CONNECTED     11443    /tmp/orbit-kyle/linc-af2-0-7618c8139752f
unix  3      [ ]         STREAM     CONNECTED     11442    
unix  3      [ ]         STREAM     CONNECTED     11439    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     11438    
unix  3      [ ]         STREAM     CONNECTED     11433    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     11432    
unix  3      [ ]         STREAM     CONNECTED     11431    @/tmp/.ICE-unix/2286
unix  3      [ ]         STREAM     CONNECTED     11430    
unix  3      [ ]         STREAM     CONNECTED     11428    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11427    
unix  3      [ ]         STREAM     CONNECTED     11128    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     11127    
unix  2      [ ]         DGRAM                    11079    
unix  3      [ ]         STREAM     CONNECTED     11013    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     11012    
unix  3      [ ]         STREAM     CONNECTED     10938    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10935    
unix  3      [ ]         STREAM     CONNECTED     10919    @/dbus-vfs-daemon/socket-0NdbN1Aa
unix  3      [ ]         STREAM     CONNECTED     10918    
unix  3      [ ]         STREAM     CONNECTED     10920    @/dbus-vfs-daemon/socket-8vTbIEFN
unix  3      [ ]         STREAM     CONNECTED     10917    
unix  3      [ ]         STREAM     CONNECTED     10909    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10908    
unix  3      [ ]         STREAM     CONNECTED     10883    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10882    
unix  2      [ ]         DGRAM                    10881    
unix  3      [ ]         STREAM     CONNECTED     10880    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10879    
unix  3      [ ]         STREAM     CONNECTED     10874    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10873    
unix  3      [ ]         STREAM     CONNECTED     10872    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10869    
unix  3      [ ]         STREAM     CONNECTED     10868    /tmp/orbit-kyle/linc-9f1-0-615bded99848d
unix  3      [ ]         STREAM     CONNECTED     10867    
unix  3      [ ]         STREAM     CONNECTED     10864    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10863    
unix  3      [ ]         STREAM     CONNECTED     10857    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10853    
unix  3      [ ]         STREAM     CONNECTED     10852    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10851    
unix  3      [ ]         STREAM     CONNECTED     10840    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     10837    
unix  3      [ ]         STREAM     CONNECTED     10836    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10834    
unix  3      [ ]         STREAM     CONNECTED     10835    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10833    
unix  3      [ ]         STREAM     CONNECTED     10823    @/tmp/.ICE-unix/2286
unix  3      [ ]         STREAM     CONNECTED     10822    
unix  3      [ ]         STREAM     CONNECTED     10824    /tmp/orbit-kyle/linc-992-0-27ec9fa657aa5
unix  3      [ ]         STREAM     CONNECTED     10821    
unix  3      [ ]         STREAM     CONNECTED     10832    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10819    
unix  3      [ ]         STREAM     CONNECTED     10815    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10814    
unix  3      [ ]         STREAM     CONNECTED     10806    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     10805    
unix  3      [ ]         STREAM     CONNECTED     10797    @/dbus-vfs-daemon/socket-uCXLsrVR
unix  3      [ ]         STREAM     CONNECTED     10796    
unix  3      [ ]         STREAM     CONNECTED     10798    @/dbus-vfs-daemon/socket-TiNlub0E
unix  3      [ ]         STREAM     CONNECTED     10795    
unix  3      [ ]         STREAM     CONNECTED     10793    @/tmp/.ICE-unix/2286
unix  3      [ ]         STREAM     CONNECTED     10791    
unix  3      [ ]         STREAM     CONNECTED     10792    /tmp/orbit-kyle/linc-992-0-27ec9fa657aa5
unix  3      [ ]         STREAM     CONNECTED     10788    
unix  3      [ ]         STREAM     CONNECTED     10781    /tmp/orbit-kyle/linc-9e1-0-b221b9312331
unix  3      [ ]         STREAM     CONNECTED     10780    
unix  3      [ ]         STREAM     CONNECTED     10784    /tmp/orbit-kyle/linc-9e3-0-20502ed0123fd
unix  3      [ ]         STREAM     CONNECTED     10777    
unix  3      [ ]         STREAM     CONNECTED     10773    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10772    
unix  3      [ ]         STREAM     CONNECTED     10764    /tmp/orbit-kyle/linc-9e1-0-b221b9312331
unix  3      [ ]         STREAM     CONNECTED     10763    
unix  3      [ ]         STREAM     CONNECTED     10762    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10761    
unix  3      [ ]         STREAM     CONNECTED     10759    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10758    
unix  3      [ ]         STREAM     CONNECTED     10757    /tmp/orbit-kyle/linc-9e3-0-20502ed0123fd
unix  3      [ ]         STREAM     CONNECTED     10756    
unix  3      [ ]         STREAM     CONNECTED     10755    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10754    
unix  3      [ ]         STREAM     CONNECTED     10752    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10751    
unix  3      [ ]         STREAM     CONNECTED     10749    /tmp/orbit-kyle/linc-9e3-0-20502ed0123fd
unix  3      [ ]         STREAM     CONNECTED     10748    
unix  3      [ ]         STREAM     CONNECTED     10750    /tmp/orbit-kyle/linc-9e1-0-b221b9312331
unix  3      [ ]         STREAM     CONNECTED     10747    
unix  3      [ ]         STREAM     CONNECTED     10745    /tmp/orbit-kyle/linc-998-0-29e5093e64fb3
unix  3      [ ]         STREAM     CONNECTED     10742    
unix  3      [ ]         STREAM     CONNECTED     10743    /tmp/orbit-kyle/linc-998-0-29e5093e64fb3
unix  3      [ ]         STREAM     CONNECTED     10739    
unix  3      [ ]         STREAM     CONNECTED     10732    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10731    
unix  3      [ ]         STREAM     CONNECTED     10730    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10727    
unix  3      [ ]         STREAM     CONNECTED     10641    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10639    
unix  3      [ ]         STREAM     CONNECTED     10633    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10632    
unix  3      [ ]         STREAM     CONNECTED     10630    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10629    
unix  3      [ ]         STREAM     CONNECTED     10624    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10623    
unix  3      [ ]         STREAM     CONNECTED     10614    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10613    
unix  3      [ ]         STREAM     CONNECTED     10607    /tmp/orbit-kyle/linc-992-0-27ec9fa657aa5
unix  3      [ ]         STREAM     CONNECTED     10606    
unix  3      [ ]         STREAM     CONNECTED     10572    /tmp/orbit-kyle/linc-9c7-0-275ea8e81231f
unix  3      [ ]         STREAM     CONNECTED     10571    
unix  3      [ ]         STREAM     CONNECTED     10564    @/dbus-vfs-daemon/socket-NMKf8boS
unix  3      [ ]         STREAM     CONNECTED     10563    
unix  3      [ ]         STREAM     CONNECTED     10565    @/dbus-vfs-daemon/socket-YFIVlMN1
unix  3      [ ]         STREAM     CONNECTED     10562    
unix  3      [ ]         STREAM     CONNECTED     10557    @/dbus-vfs-daemon/socket-sS0fcKY2
unix  3      [ ]         STREAM     CONNECTED     10556    
unix  3      [ ]         STREAM     CONNECTED     10558    @/dbus-vfs-daemon/socket-Y8Z5288s
unix  3      [ ]         STREAM     CONNECTED     10555    
unix  3      [ ]         STREAM     CONNECTED     10548    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10547    
unix  3      [ ]         STREAM     CONNECTED     10546    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10545    
unix  3      [ ]         STREAM     CONNECTED     10544    /tmp/orbit-kyle/linc-9c7-0-275ea8e81231f
unix  3      [ ]         STREAM     CONNECTED     10543    
unix  3      [ ]         STREAM     CONNECTED     10542    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10541    
unix  3      [ ]         STREAM     CONNECTED     10539    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10538    
unix  3      [ ]         STREAM     CONNECTED     10534    /tmp/orbit-kyle/linc-9c7-0-275ea8e81231f
unix  3      [ ]         STREAM     CONNECTED     10533    
unix  3      [ ]         STREAM     CONNECTED     10532    /tmp/orbit-kyle/linc-998-0-29e5093e64fb3
unix  3      [ ]         STREAM     CONNECTED     10524    
unix  3      [ ]         STREAM     CONNECTED     10517    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10515    
unix  3      [ ]         STREAM     CONNECTED     10470    /tmp/orbit-kyle/linc-9ad-0-243da650ea67b
unix  3      [ ]         STREAM     CONNECTED     10469    
unix  3      [ ]         STREAM     CONNECTED     10462    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10461    
unix  3      [ ]         STREAM     CONNECTED     10456    @/dbus-vfs-daemon/socket-z2r5Sq7Q
unix  3      [ ]         STREAM     CONNECTED     10455    
unix  3      [ ]         STREAM     CONNECTED     10457    @/dbus-vfs-daemon/socket-u3NrKofO
unix  3      [ ]         STREAM     CONNECTED     10454    
unix  3      [ ]         STREAM     CONNECTED     10448    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10447    
unix  3      [ ]         STREAM     CONNECTED     10446    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10445    
unix  3      [ ]         STREAM     CONNECTED     10442    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10441    
unix  3      [ ]         STREAM     CONNECTED     10422    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10421    
unix  3      [ ]         STREAM     CONNECTED     10419    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10418    
unix  3      [ ]         STREAM     CONNECTED     10417    /tmp/orbit-kyle/linc-992-0-27ec9fa657aa5
unix  3      [ ]         STREAM     CONNECTED     10416    
unix  3      [ ]         STREAM     CONNECTED     10463    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10415    
unix  3      [ ]         STREAM     CONNECTED     10409    /tmp/orbit-kyle/linc-9b7-0-78542c39ecc9f
unix  3      [ ]         STREAM     CONNECTED     10408    
unix  3      [ ]         STREAM     CONNECTED     10407    /home/kyle/.pulse/5518d7dea7209b6728c03b614a8b1585-runtime/native
unix  3      [ ]         STREAM     CONNECTED     10406    
unix  3      [ ]         STREAM     CONNECTED     10401    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10400    
unix  3      [ ]         STREAM     CONNECTED     10399    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10398    
unix  3      [ ]         STREAM     CONNECTED     10395    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10394    
unix  3      [ ]         STREAM     CONNECTED     10379    /tmp/orbit-kyle/linc-9b7-0-78542c39ecc9f
unix  3      [ ]         STREAM     CONNECTED     10378    
unix  3      [ ]         STREAM     CONNECTED     10377    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10376    
unix  3      [ ]         STREAM     CONNECTED     10375    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10374    
unix  3      [ ]         STREAM     CONNECTED     10369    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10368    
unix  3      [ ]         STREAM     CONNECTED     10365    /tmp/orbit-kyle/linc-9a2-0-503306bef1666
unix  3      [ ]         STREAM     CONNECTED     10364    
unix  3      [ ]         STREAM     CONNECTED     10367    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10360    
unix  3      [ ]         STREAM     CONNECTED     10361    /tmp/orbit-kyle/linc-9a9-0-6c08fcd0f0cd6
unix  3      [ ]         STREAM     CONNECTED     10359    
unix  3      [ ]         STREAM     CONNECTED     10366    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10353    
unix  3      [ ]         STREAM     CONNECTED     10356    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10352    
unix  3      [ ]         STREAM     CONNECTED     10355    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10348    
unix  3      [ ]         STREAM     CONNECTED     10354    /tmp/orbit-kyle/linc-9b7-0-78542c39ecc9f
unix  3      [ ]         STREAM     CONNECTED     10343    
unix  3      [ ]         STREAM     CONNECTED     10342    /tmp/orbit-kyle/linc-998-0-29e5093e64fb3
unix  3      [ ]         STREAM     CONNECTED     10339    
unix  3      [ ]         STREAM     CONNECTED     10335    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10334    
unix  3      [ ]         STREAM     CONNECTED     10333    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10332    
unix  3      [ ]         STREAM     CONNECTED     10331    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10330    
unix  3      [ ]         STREAM     CONNECTED     10327    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10326    
unix  3      [ ]         STREAM     CONNECTED     10324    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10323    
unix  3      [ ]         STREAM     CONNECTED     10320    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10319    
unix  3      [ ]         STREAM     CONNECTED     10318    /tmp/orbit-kyle/linc-996-0-790bf200c64df
unix  3      [ ]         STREAM     CONNECTED     10317    
unix  3      [ ]         STREAM     CONNECTED     10314    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10313    
unix  3      [ ]         STREAM     CONNECTED     10305    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10304    
unix  3      [ ]         STREAM     CONNECTED     10302    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10301    
unix  3      [ ]         STREAM     CONNECTED     10300    /tmp/orbit-kyle/linc-9a7-0-6382005bb9dd2
unix  3      [ ]         STREAM     CONNECTED     10299    
unix  3      [ ]         STREAM     CONNECTED     10296    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10295    
unix  3      [ ]         STREAM     CONNECTED     10259    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10257    
unix  3      [ ]         STREAM     CONNECTED     10258    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10253    
unix  3      [ ]         STREAM     CONNECTED     10254    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10251    
unix  3      [ ]         STREAM     CONNECTED     10243    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10242    
unix  3      [ ]         STREAM     CONNECTED     10241    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10240    
unix  3      [ ]         STREAM     CONNECTED     10138    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10137    
unix  3      [ ]         STREAM     CONNECTED     10136    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10132    
unix  3      [ ]         STREAM     CONNECTED     10133    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10131    
unix  3      [ ]         STREAM     CONNECTED     10097    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10095    
unix  3      [ ]         STREAM     CONNECTED     10062    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10061    
unix  3      [ ]         STREAM     CONNECTED     10063    @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     10058    
unix  3      [ ]         STREAM     CONNECTED     10056    /tmp/orbit-kyle/linc-9a4-0-1521facf8d840
unix  3      [ ]         STREAM     CONNECTED     10027    
unix  3      [ ]         STREAM     CONNECTED     10022    /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     10021    
unix  3      [ ]         STREAM     CONNECTED     10057    /tmp/orbit-kyle/linc-99b-0-4fc0d8ff8a763
unix  3      [ ]         STREAM     CONNECTED     10016    
unix  3      [ ]         STREAM     CONNECTED     9980     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     9979     
unix  3      [ ]         STREAM     CONNECTED     9974     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9973     
unix  3      [ ]         STREAM     CONNECTED     9939     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9938     
unix  3      [ ]         STREAM     CONNECTED     9845     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9844     
unix  3      [ ]         STREAM     CONNECTED     9828     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9827     
unix  3      [ ]         STREAM     CONNECTED     9755     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9754     
unix  3      [ ]         STREAM     CONNECTED     9742     /tmp/orbit-kyle/linc-992-0-27ec9fa657aa5
unix  3      [ ]         STREAM     CONNECTED     9741     
unix  3      [ ]         STREAM     CONNECTED     9737     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9736     
unix  3      [ ]         STREAM     CONNECTED     9739     /tmp/orbit-kyle/linc-998-0-29e5093e64fb3
unix  3      [ ]         STREAM     CONNECTED     9734     
unix  3      [ ]         STREAM     CONNECTED     9720     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9685     
unix  3      [ ]         STREAM     CONNECTED     9617     @/tmp/.ICE-unix/2286
unix  3      [ ]         STREAM     CONNECTED     9616     
unix  3      [ ]         STREAM     CONNECTED     9614     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9613     
unix  3      [ ]         STREAM     CONNECTED     9540     @/tmp/.ICE-unix/2286
unix  3      [ ]         STREAM     CONNECTED     9539     
unix  3      [ ]         STREAM     CONNECTED     9535     /tmp/orbit-kyle/linc-994-0-2f1c1ef6202ac
unix  3      [ ]         STREAM     CONNECTED     9534     
unix  3      [ ]         STREAM     CONNECTED     9531     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     9530     
unix  3      [ ]         STREAM     CONNECTED     9524     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9523     
unix  3      [ ]         STREAM     CONNECTED     9522     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9521     
unix  3      [ ]         STREAM     CONNECTED     9516     /tmp/orbit-kyle/linc-991-0-5aca2d9d5c70
unix  3      [ ]         STREAM     CONNECTED     9515     
unix  3      [ ]         STREAM     CONNECTED     9512     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     9511     
unix  3      [ ]         STREAM     CONNECTED     9504     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9503     
unix  3      [ ]         STREAM     CONNECTED     9500     /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     9499     
unix  3      [ ]         STREAM     CONNECTED     9497     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9496     
unix  3      [ ]         STREAM     CONNECTED     9494     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9493     
unix  3      [ ]         STREAM     CONNECTED     9492     /tmp/orbit-kyle/linc-992-0-27ec9fa657aa5
unix  3      [ ]         STREAM     CONNECTED     9491     
unix  3      [ ]         STREAM     CONNECTED     9488     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     9487     
unix  3      [ ]         STREAM     CONNECTED     9485     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9484     
unix  3      [ ]         STREAM     CONNECTED     9480     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9478     
unix  3      [ ]         STREAM     CONNECTED     9479     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9477     
unix  3      [ ]         STREAM     CONNECTED     9445     @/tmp/.ICE-unix/2286
unix  3      [ ]         STREAM     CONNECTED     9444     
unix  3      [ ]         STREAM     CONNECTED     9294     /home/kyle/.pulse/5518d7dea7209b6728c03b614a8b1585-runtime/native
unix  3      [ ]         STREAM     CONNECTED     9293     
unix  3      [ ]         STREAM     CONNECTED     9288     /tmp/orbit-kyle/linc-94c-0-7d4a753848c17
unix  3      [ ]         STREAM     CONNECTED     9287     
unix  3      [ ]         STREAM     CONNECTED     9284     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     9283     
unix  3      [ ]         STREAM     CONNECTED     9278     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9277     
unix  3      [ ]         STREAM     CONNECTED     9272     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9269     
unix  2      [ ]         DGRAM                    9230     
unix  3      [ ]         STREAM     CONNECTED     9229     /tmp/orbit-kyle/linc-945-0-b49d15b3eb56
unix  3      [ ]         STREAM     CONNECTED     9228     
unix  3      [ ]         STREAM     CONNECTED     9224     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9223     
unix  3      [ ]         STREAM     CONNECTED     9225     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     9222     
unix  3      [ ]         STREAM     CONNECTED     9190     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9189     
unix  3      [ ]         STREAM     CONNECTED     9188     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9185     
unix  3      [ ]         STREAM     CONNECTED     9157     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9156     
unix  3      [ ]         STREAM     CONNECTED     9155     /tmp/orbit-kyle/linc-943-0-421aa42e3380a
unix  3      [ ]         STREAM     CONNECTED     9154     
unix  3      [ ]         STREAM     CONNECTED     9151     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     9150     
unix  3      [ ]         STREAM     CONNECTED     9144     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9143     
unix  3      [ ]         STREAM     CONNECTED     9141     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9140     
unix  3      [ ]         STREAM     CONNECTED     9131     /tmp/orbit-kyle/linc-8df-0-1784f5cd2b1a3
unix  3      [ ]         STREAM     CONNECTED     9130     
unix  3      [ ]         STREAM     CONNECTED     9127     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     9125     
unix  3      [ ]         STREAM     CONNECTED     9122     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9121     
unix  3      [ ]         STREAM     CONNECTED     9119     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     9118     
unix  3      [ ]         STREAM     CONNECTED     8992     /tmp/orbit-kyle/linc-931-0-1a37c0517e7ee
unix  3      [ ]         STREAM     CONNECTED     8991     
unix  3      [ ]         STREAM     CONNECTED     8988     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     8987     
unix  3      [ ]         STREAM     CONNECTED     8983     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8982     
unix  3      [ ]         STREAM     CONNECTED     8978     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8977     
unix  3      [ ]         STREAM     CONNECTED     8973     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8972     
unix  3      [ ]         STREAM     CONNECTED     8971     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8970     
unix  3      [ ]         STREAM     CONNECTED     8969     /tmp/orbit-kyle/linc-8ee-0-445572e74449c
unix  3      [ ]         STREAM     CONNECTED     8968     
unix  3      [ ]         STREAM     CONNECTED     8965     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     8964     
unix  3      [ ]         STREAM     CONNECTED     8924     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8922     
unix  3      [ ]         STREAM     CONNECTED     8916     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8915     
unix  3      [ ]         STREAM     CONNECTED     8879     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8878     
unix  3      [ ]         STREAM     CONNECTED     8876     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8875     
unix  3      [ ]         STREAM     CONNECTED     8850     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8849     
unix  3      [ ]         STREAM     CONNECTED     8837     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8836     
unix  3      [ ]         STREAM     CONNECTED     8826     /tmp/orbit-kyle/linc-925-0-6b8e72af972c
unix  3      [ ]         STREAM     CONNECTED     8825     
unix  3      [ ]         STREAM     CONNECTED     8822     /tmp/orbit-kyle/linc-927-0-7be365a8e959e
unix  3      [ ]         STREAM     CONNECTED     8821     
unix  3      [ ]         STREAM     CONNECTED     8815     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8814     
unix  3      [ ]         STREAM     CONNECTED     8479     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8478     
unix  3      [ ]         STREAM     CONNECTED     8465     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8464     
unix  3      [ ]         STREAM     CONNECTED     8419     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8417     
unix  3      [ ]         STREAM     CONNECTED     8415     @/tmp/dbus-lxE2olCxFM
unix  3      [ ]         STREAM     CONNECTED     8414     
unix  3      [ ]         STREAM     CONNECTED     8406     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8405     
unix  3      [ ]         STREAM     CONNECTED     8390     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8389     
unix  3      [ ]         STREAM     CONNECTED     8388     
unix  3      [ ]         STREAM     CONNECTED     8387     
unix  3      [ ]         STREAM     CONNECTED     8376     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8375     
unix  3      [ ]         STREAM     CONNECTED     8178     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8177     
unix  2      [ ]         DGRAM                    8176     
unix  2      [ ]         DGRAM                    8164     
unix  3      [ ]         STREAM     CONNECTED     7717     @/tmp/gdm-session-sUlvuMVC
unix  3      [ ]         STREAM     CONNECTED     7715     
unix  3      [ ]         STREAM     CONNECTED     7254     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7253     
unix  3      [ ]         STREAM     CONNECTED     7250     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7249     
unix  3      [ ]         STREAM     CONNECTED     7188     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7187     
unix  3      [ ]         STREAM     CONNECTED     7174     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7173     
unix  2      [ ]         DGRAM                    7147     
unix  3      [ ]         STREAM     CONNECTED     7032     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7031     
unix  3      [ ]         STREAM     CONNECTED     6979     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     6971     
unix  3      [ ]         STREAM     CONNECTED     6972     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6970     
unix  3      [ ]         STREAM     CONNECTED     6965     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     6964     
unix  3      [ ]         STREAM     CONNECTED     6963     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     6962     
unix  3      [ ]         STREAM     CONNECTED     6955     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     6954     
unix  2      [ ]         DGRAM                    6926     
unix  3      [ ]         STREAM     CONNECTED     6924     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6923     
unix  3      [ ]         STREAM     CONNECTED     6896     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6895     
unix  3      [ ]         STREAM     CONNECTED     6458     
unix  3      [ ]         STREAM     CONNECTED     6457     
unix  3      [ ]         STREAM     CONNECTED     6165     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     6164     
unix  3      [ ]         STREAM     CONNECTED     6162     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6161     
unix  3      [ ]         STREAM     CONNECTED     6149     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     6148     
unix  3      [ ]         STREAM     CONNECTED     6146     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6145     
unix  2      [ ]         DGRAM                    5838     
unix  2      [ ]         DGRAM                    5830     
unix  3      [ ]         STREAM     CONNECTED     5785     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     5784     
unix  3      [ ]         STREAM     CONNECTED     5782     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5781     
unix  3      [ ]         STREAM     CONNECTED     5771     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     5770     
unix  3      [ ]         STREAM     CONNECTED     5759     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5758     
unix  3      [ ]         STREAM     CONNECTED     5748     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     5747     
unix  3      [ ]         STREAM     CONNECTED     5745     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5744     
unix  3      [ ]         STREAM     CONNECTED     5733     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     5732     
unix  3      [ ]         STREAM     CONNECTED     5730     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5729     
unix  3      [ ]         STREAM     CONNECTED     5705     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5704     
unix  3      [ ]         STREAM     CONNECTED     5698     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     5693     
unix  3      [ ]         STREAM     CONNECTED     5697     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     5683     
unix  3      [ ]         STREAM     CONNECTED     5673     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     5671     
unix  3      [ ]         STREAM     CONNECTED     5534     @/var/run/hald/dbus-nnaapNDZ7U
unix  3      [ ]         STREAM     CONNECTED     5489     
unix  3      [ ]         STREAM     CONNECTED     5476     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5475     
unix  2      [ ]         DGRAM                    5474     
unix  3      [ ]         STREAM     CONNECTED     5089     @/var/run/hald/dbus-KL1NvTlrwB
unix  3      [ ]         STREAM     CONNECTED     5088     
unix  3      [ ]         STREAM     CONNECTED     5061     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5060     
unix  3      [ ]         STREAM     CONNECTED     5053     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5051     
unix  3      [ ]         STREAM     CONNECTED     5039     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5038     
unix  2      [ ]         DGRAM                    5023     
unix  3      [ ]         STREAM     CONNECTED     5014     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5012     
unix  3      [ ]         STREAM     CONNECTED     5004     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5003     
unix  3      [ ]         STREAM     CONNECTED     5000     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4999     
unix  2      [ ]         DGRAM                    4996     
unix  3      [ ]         STREAM     CONNECTED     4993     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4992     
unix  3      [ ]         STREAM     CONNECTED     4987     
unix  3      [ ]         STREAM     CONNECTED     4986     
unix  2      [ ]         DGRAM                    4983     
unix  3      [ ]         STREAM     CONNECTED     4952     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4943     
unix  3      [ ]         STREAM     CONNECTED     4940     
unix  3      [ ]         STREAM     CONNECTED     4939     
unix  3      [ ]         DGRAM                    2942     
unix  3      [ ]         DGRAM                    2941     
unix  3      [ ]         STREAM     CONNECTED     2907     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     2904
```

---

### Post by CharlesA on 2010-07-25
You are fine. Those are just open UNIX sockets, not active internet connections.

---

### Post by iponeverything on 2010-07-25
As @CharlesA said, just sockets. 

Sockets are the UNIX way of doing IPC (inter-process communication).

---

### Post by andthewicked on 2010-07-25
thank you

---

### Post by CharlesA on 2010-07-25
Don't forget to mark the thread as solved: Thread Tools > Mark as Solved.

---

