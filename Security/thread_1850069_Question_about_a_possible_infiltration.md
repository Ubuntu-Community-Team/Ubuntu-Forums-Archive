---
title: "Question about a possible infiltration?"
date: 2011-09-25
forum: Security
---

### Post by mrfeeley on 2011-09-25
I had a run in with a highly targetted infiltration of my box earlier this year and I've been having some concerns lately about something similar going on with my new install.
I've been seeing DDoS attempts show up in my router and large temp files have been showing up. Additionally, there are a number of other strange occurances I can find little evidence of elsewhere on the net (having compiz and compiz-1 on my configured on my computer, etc.)
So here is my netstat output, at the end I'll explain what I find curious (possibly sinister, but I'll leave it to you pros to decide that). I really like linux (esp. Ubuntu) but the constantly changing system setups, my unfamiliarity of its maze of open source packages, the plethora of pre-installed remote access/management packages, and the seeming inefficacy of available firewall software without pro configuration have caused me a lot of anxiety and make me question staying around with it.
Please help allay my fears or let me know what has happened to my computer, it would be greatly appreciated. (Running Ubuntu 11.04)

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        1      0 192.168.1.3:59815       papeda.canonical.co:www CLOSE_WAIT 
tcp        0      0 192.168.1.3:41456       iad04s01-in-f147.1e:www TIME_WAIT  
tcp        1      0 192.168.1.3:38153       barbadine.canonical:www CLOSE_WAIT 
tcp        0      0 192.168.1.3:41457       iad04s01-in-f147.1e:www TIME_WAIT  
tcp       38      0 192.168.1.3:33927       papeda.canonical.:https CLOSE_WAIT 
tcp        1      0 192.168.1.3:60279       barbadine.canonical:www CLOSE_WAIT 
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  17     [ ]         DGRAM                    9237     /dev/log
unix  2      [ ]         DGRAM                    7124     @/org/kernel/udev/udevd
unix  3      [ ]         STREAM     CONNECTED     66002    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     66682    
unix  2      [ ]         DGRAM                    66681    
unix  3      [ ]         STREAM     CONNECTED     65583    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     65278    
unix  3      [ ]         STREAM     CONNECTED     65246    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     65579    
unix  3      [ ]         STREAM     CONNECTED     60177    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     60176    
unix  3      [ ]         STREAM     CONNECTED     55326    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     54929    
unix  3      [ ]         STREAM     CONNECTED     52658    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     52115    
unix  3      [ ]         STREAM     CONNECTED     39123    /tmp/orbit-user/linc-1be8-0-599fb31cf630
unix  3      [ ]         STREAM     CONNECTED     38667    
unix  3      [ ]         STREAM     CONNECTED     38666    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     39121    
unix  3      [ ]         STREAM     CONNECTED     39114    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     39113    
unix  3      [ ]         STREAM     CONNECTED     38661    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     39111    
unix  3      [ ]         STREAM     CONNECTED     39108    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     38657    
unix  3      [ ]         STREAM     CONNECTED     37531    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     37530    
unix  3      [ ]         STREAM     CONNECTED     36471    /home/user/.pulse/f0e6f2df45df5975fef039ae4e7ec9f4-runtime/native
unix  3      [ ]         STREAM     CONNECTED     35780    
unix  3      [ ]         STREAM     CONNECTED     35776    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     35775    
unix  3      [ ]         STREAM     CONNECTED     24384    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     27080    
unix  2      [ ]         DGRAM                    24382    
unix  3      [ ]         STREAM     CONNECTED     21141    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     21140    
unix  3      [ ]         STREAM     CONNECTED     20761    /home/user/.pulse/f0e6f2df45df5975fef039ae4e7ec9f4-runtime/native
unix  3      [ ]         STREAM     CONNECTED     19924    
unix  3      [ ]         STREAM     CONNECTED     18313    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     18312    
unix  3      [ ]         STREAM     CONNECTED     19238    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     18306    
unix  3      [ ]         STREAM     CONNECTED     19234    
unix  3      [ ]         STREAM     CONNECTED     19233    
unix  3      [ ]         STREAM     CONNECTED     19228    /tmp/orbit-usert/linc-96c-0-3a9140016022f
unix  3      [ ]         STREAM     CONNECTED     18303    
unix  3      [ ]         STREAM     CONNECTED     18302    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     19226    
unix  3      [ ]         STREAM     CONNECTED     19220    @/tmp/.ICE-unix/1881
unix  3      [ ]         STREAM     CONNECTED     19219    
unix  3      [ ]         STREAM     CONNECTED     18293    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19215    
unix  3      [ ]         STREAM     CONNECTED     18131    /tmp/orbit-root/linc-8da-0-509bdd9bfba8
unix  3      [ ]         STREAM     CONNECTED     19067    
unix  3      [ ]         STREAM     CONNECTED     19066    /tmp/orbit-root/linc-8e2-0-1e3fb4e374c2
unix  3      [ ]         STREAM     CONNECTED     18129    
unix  3      [ ]         STREAM     CONNECTED     18128    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19063    
unix  3      [ ]         STREAM     CONNECTED     18125    @/tmp/dbus-L6RoDkJHB1
unix  3      [ ]         STREAM     CONNECTED     19054    
unix  3      [ ]         STREAM     CONNECTED     19043    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18116    
unix  3      [ ]         STREAM     CONNECTED     18115    
unix  3      [ ]         STREAM     CONNECTED     18114    
unix  3      [ ]         STREAM     CONNECTED     19037    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18108    
unix  3      [ ]         STREAM     CONNECTED     18104    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19017    
unix  2      [ ]         DGRAM                    19013    
unix  3      [ ]         STREAM     CONNECTED     18060    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     18976    
unix  3      [ ]         STREAM     CONNECTED     18043    /tmp/orbit-user/linc-8d6-0-769e4e29a3513
unix  3      [ ]         STREAM     CONNECTED     18970    
unix  3      [ ]         STREAM     CONNECTED     18969    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     18041    
unix  3      [ ]         STREAM     CONNECTED     18032    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18961    
unix  3      [ ]         STREAM     CONNECTED     17321    @/dbus-vfs-daemon/socket-ogDlUV73
unix  3      [ ]         STREAM     CONNECTED     17574    
unix  3      [ ]         STREAM     CONNECTED     17320    @/dbus-vfs-daemon/socket-xof0PaqV
unix  3      [ ]         STREAM     CONNECTED     17573    
unix  3      [ ]         STREAM     CONNECTED     17446    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     17445    
unix  3      [ ]         STREAM     CONNECTED     17214    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     17443    
unix  3      [ ]         STREAM     CONNECTED     17440    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17213    
unix  3      [ ]         STREAM     CONNECTED     17212    /tmp/orbit-matt/linc-8a9-0-497d76cddfb84
unix  3      [ ]         STREAM     CONNECTED     17439    
unix  3      [ ]         STREAM     CONNECTED     17438    /tmp/orbit-matt/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     17210    
unix  3      [ ]         STREAM     CONNECTED     17201    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17431    
unix  3      [ ]         STREAM     CONNECTED     17159    /home/matt/.pulse/f0e6f2df45df5975fef039ae4e7ec9f4-runtime/native
unix  3      [ ]         STREAM     CONNECTED     16357    
unix  3      [ ]         STREAM     CONNECTED     16337    
unix  3      [ ]         STREAM     CONNECTED     16336    
unix  3      [ ]         STREAM     CONNECTED     17065    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16313    
unix  3      [ ]         STREAM     CONNECTED     17063    /tmp/orbit-matt/linc-86b-0-73d3dac87d652
unix  3      [ ]         STREAM     CONNECTED     16312    
unix  3      [ ]         STREAM     CONNECTED     16311    /tmp/orbit-matt/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     17061    
unix  3      [ ]         STREAM     CONNECTED     16304    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16303    
unix  3      [ ]         STREAM     CONNECTED     17054    @/tmp/.ICE-unix/1881
unix  3      [ ]         STREAM     CONNECTED     16302    
unix  3      [ ]         STREAM     CONNECTED     16296    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16295    
unix  3      [ ]         STREAM     CONNECTED     16799    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16193    
unix  3      [ ]         STREAM     CONNECTED     16183    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16182    
unix  3      [ ]         STREAM     CONNECTED     16780    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16152    
unix  3      [ ]         STREAM     CONNECTED     16149    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16773    
unix  3      [ ]         STREAM     CONNECTED     16146    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16772    
unix  3      [ ]         STREAM     CONNECTED     16144    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16771    
unix  3      [ ]         STREAM     CONNECTED     15897    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16559    
unix  3      [ ]         STREAM     CONNECTED     16553    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16552    
unix  3      [ ]         STREAM     CONNECTED     16551    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15894    
unix  3      [ ]         STREAM     CONNECTED     16546    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15888    
unix  3      [ ]         STREAM     CONNECTED     15886    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16545    
unix  3      [ ]         STREAM     CONNECTED     16525    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15881    
unix  3      [ ]         STREAM     CONNECTED     16520    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16519    
unix  3      [ ]         STREAM     CONNECTED     15880    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16517    
unix  3      [ ]         STREAM     CONNECTED     15798    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16459    
unix  3      [ ]         STREAM     CONNECTED     15789    
unix  3      [ ]         STREAM     CONNECTED     15788    
unix  3      [ ]         STREAM     CONNECTED     15773    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     16441    
unix  3      [ ]         STREAM     CONNECTED     16432    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15765    
unix  3      [ ]         STREAM     CONNECTED     15763    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16431    
unix  3      [ ]         STREAM     CONNECTED     15750    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15360    
unix  3      [ ]         STREAM     CONNECTED     15748    /home/user/.pulse/f0e6f2df45df5975fef039ae4e7ec9f4-runtime/native
unix  3      [ ]         STREAM     CONNECTED     15356    
unix  3      [ ]         STREAM     CONNECTED     15349    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15734    
unix  3      [ ]         STREAM     CONNECTED     15320    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15715    
unix  3      [ ]         STREAM     CONNECTED     15315    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15708    
unix  3      [ ]         STREAM     CONNECTED     15309    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15697    
unix  3      [ ]         STREAM     CONNECTED     15686    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15682    
unix  3      [ ]         STREAM     CONNECTED     15643    /tmp/orbit-user/linc-80b-0-3aabcc1653542
unix  3      [ ]         STREAM     CONNECTED     15642    
unix  3      [ ]         STREAM     CONNECTED     15640    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     15639    
unix  3      [ ]         STREAM     CONNECTED     15279    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15278    
unix  3      [ ]         STREAM     CONNECTED     15277    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15276    
unix  3      [ ]         STREAM     CONNECTED     15262    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15592    
unix  3      [ ]         STREAM     CONNECTED     15261    /tmp/orbit-user/linc-80c-0-33fa24a208d2
unix  3      [ ]         STREAM     CONNECTED     15591    
unix  3      [ ]         STREAM     CONNECTED     15590    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     15259    
unix  3      [ ]         STREAM     CONNECTED     15576    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15248    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15247    
unix  3      [ ]         STREAM     CONNECTED     15575    
unix  3      [ ]         STREAM     CONNECTED     15196    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15526    
unix  3      [ ]         STREAM     CONNECTED     15195    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15525    
unix  3      [ ]         STREAM     CONNECTED     15192    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15524    
unix  3      [ ]         STREAM     CONNECTED     15185    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15184    
unix  3      [ ]         STREAM     CONNECTED     15182    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15511    
unix  3      [ ]         STREAM     CONNECTED     15173    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15496    
unix  3      [ ]         STREAM     CONNECTED     15489    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15488    
unix  3      [ ]         STREAM     CONNECTED     15487    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15486    
unix  3      [ ]         STREAM     CONNECTED     15172    /tmp/orbit-user/linc-7ef-0-2c7cbda058db6
unix  3      [ ]         STREAM     CONNECTED     15171    
unix  3      [ ]         STREAM     CONNECTED     15169    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     15168    
unix  3      [ ]         STREAM     CONNECTED     15163    /tmp/orbit-user/linc-7f2-0-398f40d756f14
unix  3      [ ]         STREAM     CONNECTED     15162    
unix  3      [ ]         STREAM     CONNECTED     15160    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     15159    
unix  3      [ ]         STREAM     CONNECTED     15153    /tmp/orbit-user/linc-7f4-0-5304a5f4550f3
unix  3      [ ]         STREAM     CONNECTED     15152    
unix  3      [ ]         STREAM     CONNECTED     15150    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     15149    
unix  3      [ ]         STREAM     CONNECTED     15441    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15116    
unix  3      [ ]         STREAM     CONNECTED     15440    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15115    
unix  3      [ ]         STREAM     CONNECTED     15112    @/dbus-vfs-daemon/socket-Q7sDsBly
unix  3      [ ]         STREAM     CONNECTED     15439    
unix  3      [ ]         STREAM     CONNECTED     15111    @/dbus-vfs-daemon/socket-TtBVf9zI
unix  3      [ ]         STREAM     CONNECTED     15438    
unix  3      [ ]         STREAM     CONNECTED     15106    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15435    
unix  3      [ ]         STREAM     CONNECTED     15389    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15067    
unix  3      [ ]         STREAM     CONNECTED     15063    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15371    
unix  3      [ ]         STREAM     CONNECTED     14335    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14334    
unix  3      [ ]         STREAM     CONNECTED     14333    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15056    
unix  3      [ ]         STREAM     CONNECTED     14331    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14330    
unix  3      [ ]         STREAM     CONNECTED     15052    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15051    
unix  3      [ ]         STREAM     CONNECTED     15049    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14327    
unix  2      [ ]         DGRAM                    14321    
unix  3      [ ]         STREAM     CONNECTED     14284    /tmp/orbit-user/linc-7f0-0-2ed7f07638727
unix  3      [ ]         STREAM     CONNECTED     14283    
unix  3      [ ]         STREAM     CONNECTED     14281    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14279    
unix  3      [ ]         STREAM     CONNECTED     14256    @/dbus-vfs-daemon/socket-hcdwAdLK
unix  3      [ ]         STREAM     CONNECTED     15038    
unix  3      [ ]         STREAM     CONNECTED     14255    @/dbus-vfs-daemon/socket-lTfD9Pph
unix  3      [ ]         STREAM     CONNECTED     15037    
unix  3      [ ]         STREAM     CONNECTED     14253    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15030    
unix  3      [ ]         STREAM     CONNECTED     14252    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     15029    
unix  3      [ ]         STREAM     CONNECTED     14251    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15024    
unix  3      [ ]         STREAM     CONNECTED     15023    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14250    
unix  3      [ ]         STREAM     CONNECTED     14249    /tmp/orbit-user/linc-7f7-0-2c884a0ad38a3
unix  3      [ ]         STREAM     CONNECTED     15022    
unix  3      [ ]         STREAM     CONNECTED     15021    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14247    
unix  3      [ ]         STREAM     CONNECTED     15015    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14239    
unix  3      [ ]         STREAM     CONNECTED     14235    @/dbus-vfs-daemon/socket-a7Xn0vYp
unix  3      [ ]         STREAM     CONNECTED     14983    
unix  3      [ ]         STREAM     CONNECTED     14982    @/dbus-vfs-daemon/socket-fjHnFC5Q
unix  3      [ ]         STREAM     CONNECTED     14981    
unix  3      [ ]         STREAM     CONNECTED     14977    @/dbus-vfs-daemon/socket-Vk8zcEdi
unix  3      [ ]         STREAM     CONNECTED     14231    
unix  3      [ ]         STREAM     CONNECTED     14976    @/dbus-vfs-daemon/socket-UQkbnFpj
unix  3      [ ]         STREAM     CONNECTED     14230    
unix  3      [ ]         STREAM     CONNECTED     14227    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14975    
unix  3      [ ]         STREAM     CONNECTED     14974    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14225    
unix  3      [ ]         STREAM     CONNECTED     14221    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14967    
unix  3      [ ]         STREAM     CONNECTED     14219    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14966    
unix  3      [ ]         STREAM     CONNECTED     14944    /tmp/orbit-user/linc-7e8-0-674022bb70023
unix  3      [ ]         STREAM     CONNECTED     14943    
unix  3      [ ]         STREAM     CONNECTED     14941    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14940    
unix  3      [ ]         STREAM     CONNECTED     14209    /tmp/orbit-user/linc-7e6-0-c5436b26fe3e
unix  3      [ ]         STREAM     CONNECTED     14208    
unix  3      [ ]         STREAM     CONNECTED     14206    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14205    
unix  3      [ ]         STREAM     CONNECTED     14924    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14190    
unix  3      [ ]         STREAM     CONNECTED     14189    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14188    
unix  3      [ ]         STREAM     CONNECTED     14187    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14922    
unix  3      [ ]         STREAM     CONNECTED     14181    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14914    
unix  3      [ ]         STREAM     CONNECTED     14913    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14179    
unix  3      [ ]         STREAM     CONNECTED     14903    /tmp/orbit-user/linc-7b2-0-31f2c74218a08
unix  3      [ ]         STREAM     CONNECTED     14902    
unix  3      [ ]         STREAM     CONNECTED     14900    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14161    
unix  3      [ ]         STREAM     CONNECTED     14899    /tmp/orbit-user/linc-7df-0-1f6b0d8d5b08
unix  3      [ ]         STREAM     CONNECTED     14898    
unix  3      [ ]         STREAM     CONNECTED     14892    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14159    
unix  3      [ ]         STREAM     CONNECTED     14890    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14889    
unix  3      [ ]         STREAM     CONNECTED     14884    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14112    
unix  3      [ ]         STREAM     CONNECTED     14111    /tmp/orbit-user/linc-7dc-0-3fec6726b474a
unix  3      [ ]         STREAM     CONNECTED     14883    
unix  3      [ ]         STREAM     CONNECTED     14882    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14109    
unix  3      [ ]         STREAM     CONNECTED     14879    @/tmp/.ICE-unix/1881
unix  3      [ ]         STREAM     CONNECTED     14878    
unix  3      [ ]         STREAM     CONNECTED     14097    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14876    
unix  3      [ ]         STREAM     CONNECTED     14049    /tmp/orbit-user/linc-7bc-0-167b3758846b6
unix  3      [ ]         STREAM     CONNECTED     14048    
unix  3      [ ]         STREAM     CONNECTED     14818    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14817    
unix  3      [ ]         STREAM     CONNECTED     14036    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14808    
unix  3      [ ]         STREAM     CONNECTED     14807    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14034    
unix  3      [ ]         STREAM     CONNECTED     14030    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14029    
unix  3      [ ]         STREAM     CONNECTED     14028    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14027    
unix  3      [ ]         STREAM     CONNECTED     14026    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14804    
unix  3      [ ]         STREAM     CONNECTED     14023    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14022    
unix  3      [ ]         STREAM     CONNECTED     14799    @/dbus-vfs-daemon/socket-NWeY24BA
unix  3      [ ]         STREAM     CONNECTED     14019    
unix  3      [ ]         STREAM     CONNECTED     14798    @/dbus-vfs-daemon/socket-1Z4zhQQW
unix  3      [ ]         STREAM     CONNECTED     14018    
unix  3      [ ]         STREAM     CONNECTED     14794    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14015    
unix  3      [ ]         STREAM     CONNECTED     14012    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14793    
unix  3      [ ]         STREAM     CONNECTED     14011    /tmp/orbit-user/linc-7bd-0-340fe17af014f
unix  3      [ ]         STREAM     CONNECTED     14010    
unix  3      [ ]         STREAM     CONNECTED     14787    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14006    
unix  3      [ ]         STREAM     CONNECTED     14786    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13987    
unix  3      [ ]         STREAM     CONNECTED     14008    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     13986    
unix  3      [ ]         STREAM     CONNECTED     13982    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14781    
unix  3      [ ]         STREAM     CONNECTED     13977    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14771    
unix  3      [ ]         STREAM     CONNECTED     13972    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14769    
unix  3      [ ]         STREAM     CONNECTED     14761    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14760    
unix  3      [ ]         STREAM     CONNECTED     13969    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14752    
unix  3      [ ]         STREAM     CONNECTED     13965    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14750    
unix  3      [ ]         STREAM     CONNECTED     14743    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13958    
unix  3      [ ]         STREAM     CONNECTED     13953    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14742    
unix  3      [ ]         STREAM     CONNECTED     14740    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13952    
unix  3      [ ]         STREAM     CONNECTED     14739    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13950    
unix  3      [ ]         STREAM     CONNECTED     14737    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14736    
unix  3      [ ]         STREAM     CONNECTED     13942    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13941    
unix  3      [ ]         STREAM     CONNECTED     13939    /tmp/orbit-user/linc-7af-0-67e4bc3e901a3
unix  3      [ ]         STREAM     CONNECTED     13938    
unix  3      [ ]         STREAM     CONNECTED     13936    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     13935    
unix  3      [ ]         STREAM     CONNECTED     14717    /tmp/orbit-user/linc-7b5-0-208a5a1e89c41
unix  3      [ ]         STREAM     CONNECTED     14716    
unix  3      [ ]         STREAM     CONNECTED     13914    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14715    
unix  2      [ ]         DGRAM                    14705    
unix  2      [ ]         DGRAM                    13905    
unix  3      [ ]         STREAM     CONNECTED     14673    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13857    
unix  3      [ ]         STREAM     CONNECTED     13853    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14587    
unix  3      [ ]         STREAM     CONNECTED     14558    /tmp/orbit-user/linc-7b2-0-31f2c74218a08
unix  3      [ ]         STREAM     CONNECTED     13849    
unix  3      [ ]         STREAM     CONNECTED     13848    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14556    
unix  3      [ ]         STREAM     CONNECTED     14548    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14547    
unix  3      [ ]         STREAM     CONNECTED     13843    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13842    
unix  3      [ ]         STREAM     CONNECTED     13840    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13839    
unix  3      [ ]         STREAM     CONNECTED     13837    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14516    
unix  3      [ ]         STREAM     CONNECTED     13836    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13835    
unix  3      [ ]         STREAM     CONNECTED     13774    /home/user/.pulse/f0e6f2df45df5975fef039ae4e7ec9f4-runtime/native
unix  3      [ ]         STREAM     CONNECTED     14513    
unix  3      [ ]         STREAM     CONNECTED     14512    /tmp/orbit-user/linc-7b3-0-371a1f03ee33b
unix  3      [ ]         STREAM     CONNECTED     14511    
unix  3      [ ]         STREAM     CONNECTED     13772    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14509    
unix  3      [ ]         STREAM     CONNECTED     13701    @/tmp/.ICE-unix/1881
unix  3      [ ]         STREAM     CONNECTED     13700    
unix  3      [ ]         STREAM     CONNECTED     14493    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14492    
unix  3      [ ]         STREAM     CONNECTED     13698    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13697    
unix  3      [ ]         STREAM     CONNECTED     14472    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13694    
unix  3      [ ]         STREAM     CONNECTED     13691    @/tmp/.ICE-unix/1881
unix  3      [ ]         STREAM     CONNECTED     14444    
unix  3      [ ]         STREAM     CONNECTED     14443    /tmp/orbit-user/linc-7aa-0-37ca005b5ef2
unix  3      [ ]         STREAM     CONNECTED     13690    
unix  3      [ ]         STREAM     CONNECTED     13689    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     14441    
unix  3      [ ]         STREAM     CONNECTED     14433    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14432    
unix  3      [ ]         STREAM     CONNECTED     13666    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13665    
unix  3      [ ]         STREAM     CONNECTED     14397    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13619    
unix  3      [ ]         STREAM     CONNECTED     14393    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     14392    
unix  3      [ ]         STREAM     CONNECTED     14388    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13609    
unix  3      [ ]         STREAM     CONNECTED     14354    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13550    
unix  3      [ ]         STREAM     CONNECTED     14352    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13546    
unix  3      [ ]         STREAM     CONNECTED     14348    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13544    
unix  3      [ ]         STREAM     CONNECTED     14342    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13539    
unix  3      [ ]         STREAM     CONNECTED     13538    /tmp/orbit-user/linc-795-0-4f84abbae898a
unix  3      [ ]         STREAM     CONNECTED     14340    
unix  3      [ ]         STREAM     CONNECTED     14339    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     13536    
unix  3      [ ]         STREAM     CONNECTED     13529    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     12283    
unix  3      [ ]         STREAM     CONNECTED     13528    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12281    
unix  3      [ ]         STREAM     CONNECTED     12277    /tmp/orbit-user/linc-759-0-3c43104f670cd
unix  3      [ ]         STREAM     CONNECTED     13416    
unix  3      [ ]         STREAM     CONNECTED     13415    /tmp/orbit-user/linc-78f-0-7b4c0b3f5f5d0
unix  3      [ ]         STREAM     CONNECTED     12275    
unix  3      [ ]         STREAM     CONNECTED     12271    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13413    
unix  3      [ ]         STREAM     CONNECTED     13190    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     12270    
unix  3      [ ]         STREAM     CONNECTED     12245    @/tmp/dbus-RpQJOyZwPj
unix  3      [ ]         STREAM     CONNECTED     13158    
unix  3      [ ]         STREAM     CONNECTED     12244    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13156    
unix  3      [ ]         STREAM     CONNECTED     13155    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13154    
unix  3      [ ]         STREAM     CONNECTED     12241    
unix  3      [ ]         STREAM     CONNECTED     12240    
unix  3      [ ]         STREAM     CONNECTED     12239    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13143    
unix  3      [ ]         STREAM     CONNECTED     12127    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13083    
unix  3      [ ]         STREAM     CONNECTED     12764    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12763    
unix  3      [ ]         STREAM     CONNECTED     12463    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12462    
unix  2      [ ]         DGRAM                    12461    
unix  3      [ ]         STREAM     CONNECTED     12445    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12444    
unix  3      [ ]         STREAM     CONNECTED     12438    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12437    
unix  3      [ ]         STREAM     CONNECTED     11679    @/tmp/gdm-session-aFYSZiqv
unix  3      [ ]         STREAM     CONNECTED     11678    
unix  3      [ ]         STREAM     CONNECTED     11674    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11673    
unix  2      [ ]         DGRAM                    11672    
unix  3      [ ]         STREAM     CONNECTED     11289    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10693    
unix  2      [ ]         DGRAM                    9693     
unix  2      [ ]         DGRAM                    9642     
unix  2      [ ]         DGRAM                    9641     
unix  3      [ ]         STREAM     CONNECTED     9563     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8965     
unix  2      [ ]         DGRAM                    8958     
unix  2      [ ]         DGRAM                    8928     
unix  3      [ ]         STREAM     CONNECTED     8925     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9498     
unix  3      [ ]         STREAM     CONNECTED     8775     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8774     
unix  3      [ ]         STREAM     CONNECTED     9412     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8769     
unix  3      [ ]         STREAM     CONNECTED     8762     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9382     
unix  3      [ ]         STREAM     CONNECTED     8758     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9380     
unix  3      [ ]         STREAM     CONNECTED     9366     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8750     
unix  2      [ ]         DGRAM                    8749     
unix  3      [ ]         STREAM     CONNECTED     8730     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8729     
unix  2      [ ]         DGRAM                    8725     
unix  3      [ ]         STREAM     CONNECTED     8720     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     8718     
unix  2      [ ]         DGRAM                    8715     
unix  3      [ ]         STREAM     CONNECTED     8712     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8711     
unix  3      [ ]         STREAM     CONNECTED     8666     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9318     
unix  3      [ ]         STREAM     CONNECTED     9313     
unix  3      [ ]         STREAM     CONNECTED     9312     
unix  2      [ ]         DGRAM                    9309     
unix  3      [ ]         STREAM     CONNECTED     8626     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9252     
unix  3      [ ]         STREAM     CONNECTED     8624     
unix  3      [ ]         STREAM     CONNECTED     8623     
unix  3      [ ]         DGRAM                    7156     
unix  3      [ ]         DGRAM                    7155     
unix  3      [ ]         STREAM     CONNECTED     7106     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     1578     
```

(I hope the code tag was sufficient to make that bearable.)
Whatever the case, what I am concerned about is the .ICE-unix entries, .X11-unix entries, the pulse entries, and the numerous 'linc' files which this very vague orbit program uses. If I shouldn't be concerned please help me understand what these processes are doing on my computer. I am further annoyed by log files disappearing on occasion and some being inaccessible.

---

### Post by OpSecShellshock on 2011-09-25
I don't see anything to worry about here. In the upper part you've got connections to Canonical, which is the company that develops Ubuntu, and the one that looks like "iad04s01-in-f147" is owned by Google (the domain is actually 1e100.net, which I assure you is indeed Google).

The output displayed below that is a list of internal socket connections between processes running on your computer itself. It's not network traffic. I don't know what all of it does exactly, but I don't see anything that looks out of the ordinary or suspicious.

The reason you see compiz in there is because that's what the Unity desktop by default uses as its compositing window manager.

---

### Post by Dangertux on 2011-09-25
It's perfectly fine.

ICE is designed for merging of permissions and logins, it is found in nearly every Linux distirbution as well as BSD. 

type 

```

man iceauth

```

for more information, your system based on that netstat information (which is not indicative of much) does not appear to be compromised.

---

### Post by cariboo on 2011-09-26
Depending on what version you are running, having /.config/compiz and /.config/compiz-1, are normal directories in /home/$USER.

---

