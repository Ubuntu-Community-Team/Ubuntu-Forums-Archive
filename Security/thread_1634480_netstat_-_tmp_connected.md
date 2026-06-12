---
title: "netstat - tmp connected?"
date: 2010-11-30
forum: Security
---

### Post by arapaho on 2010-11-30
Can you tell me what's that:
```
user@user ~ $ netstat –a
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 chello08907822112:34477 sitecheck2.opera.co:www TIME_WAIT  
tcp        0      0 chello08907822112:58005 209.85.148.99:www       TIME_WAIT  
tcp        0      0 chello08907822112:45982 209.85.148.100:www      TIME_WAIT  
tcp        0      0 chello08907822112:58002 209.85.148.99:www       TIME_WAIT  
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    3075     @/org/kernel/udev/udevd
unix  17     [ ]         DGRAM                    4477     /dev/log
unix  2      [ ]         DGRAM                    8779     @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     90052    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     90051    
unix  3      [ ]         STREAM     CONNECTED     90049    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     90048    
unix  3      [ ]         STREAM     CONNECTED     90047    /tmp/orbit-user/linc-1988-0-5c926f267ea48
unix  3      [ ]         STREAM     CONNECTED     90046    
unix  3      [ ]         STREAM     CONNECTED     90043    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     90042    
unix  3      [ ]         STREAM     CONNECTED     90038    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     90037    
unix  3      [ ]         STREAM     CONNECTED     90034    @/tmp/.ICE-unix/3930
unix  3      [ ]         STREAM     CONNECTED     90033    
unix  3      [ ]         STREAM     CONNECTED     90031    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     90030    
unix  3      [ ]         STREAM     CONNECTED     89359    
unix  3      [ ]         STREAM     CONNECTED     89358    
unix  3      [ ]         STREAM     CONNECTED     89356    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     89355    
unix  3      [ ]         STREAM     CONNECTED     89354    /tmp/orbit-user/linc-1950-0-59dd350bd2440
unix  3      [ ]         STREAM     CONNECTED     89353    
unix  3      [ ]         STREAM     CONNECTED     89350    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     89349    
unix  3      [ ]         STREAM     CONNECTED     89345    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     89344    
unix  3      [ ]         STREAM     CONNECTED     89343    @/tmp/.ICE-unix/3930
unix  3      [ ]         STREAM     CONNECTED     89342    
unix  3      [ ]         STREAM     CONNECTED     89340    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     89339    
unix  3      [ ]         STREAM     CONNECTED     88168    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     88167    
unix  3      [ ]         STREAM     CONNECTED     88165    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     88164    
unix  3      [ ]         STREAM     CONNECTED     39781    /tmp/orbit-user/linc-128e-0-164467cdcd40d
unix  3      [ ]         STREAM     CONNECTED     39780    
unix  3      [ ]         STREAM     CONNECTED     39777    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     39776    
unix  3      [ ]         STREAM     CONNECTED     39771    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     39770    
unix  3      [ ]         STREAM     CONNECTED     39768    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     39767    
unix  3      [ ]         STREAM     CONNECTED     34697    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     34696    
unix  3      [ ]         STREAM     CONNECTED     32418    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     32417    
unix  3      [ ]         STREAM     CONNECTED     31649    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     31648    
unix  3      [ ]         STREAM     CONNECTED     31646    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     31645    
unix  3      [ ]         STREAM     CONNECTED     31643    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     31642    
unix  3      [ ]         STREAM     CONNECTED     31129    @/dbus-vfs-daemon/socket-HChuRAld
unix  3      [ ]         STREAM     CONNECTED     31128    
unix  3      [ ]         STREAM     CONNECTED     31130    @/dbus-vfs-daemon/socket-k1RQNfoT
unix  3      [ ]         STREAM     CONNECTED     31127    
unix  3      [ ]         STREAM     CONNECTED     31119    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     31118    
unix  3      [ ]         STREAM     CONNECTED     31092    @/dbus-vfs-daemon/socket-g3O2HYBb
unix  3      [ ]         STREAM     CONNECTED     31091    
unix  3      [ ]         STREAM     CONNECTED     31090    @/dbus-vfs-daemon/socket-jEeoqZE0
unix  3      [ ]         STREAM     CONNECTED     31089    
unix  3      [ ]         STREAM     CONNECTED     31087    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     31086    
unix  2      [ ]         DGRAM                    31085    
unix  3      [ ]         STREAM     CONNECTED     31074    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     31073    
unix  3      [ ]         STREAM     CONNECTED     31071    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     31070    
unix  3      [ ]         STREAM     CONNECTED     31069    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     31068    
unix  3      [ ]         STREAM     CONNECTED     31067    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     31066    
unix  3      [ ]         STREAM     CONNECTED     31061    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     31060    
unix  3      [ ]         STREAM     CONNECTED     31058    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     31057    
unix  3      [ ]         STREAM     CONNECTED     31056    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     31055    
unix  3      [ ]         STREAM     CONNECTED     31053    /tmp/.esd-1001/socket
unix  3      [ ]         STREAM     CONNECTED     31052    
unix  3      [ ]         STREAM     CONNECTED     31051    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     31050    
unix  3      [ ]         STREAM     CONNECTED     31000    @/tmp/.ICE-unix/3930
unix  3      [ ]         STREAM     CONNECTED     30999    
unix  3      [ ]         STREAM     CONNECTED     30974    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30973    
unix  3      [ ]         STREAM     CONNECTED     30926    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30925    
unix  3      [ ]         STREAM     CONNECTED     30922    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     30921    
unix  3      [ ]         STREAM     CONNECTED     30920    /tmp/orbit-user/linc-1013-0-11c9e41c6dac2
unix  3      [ ]         STREAM     CONNECTED     30919    
unix  3      [ ]         STREAM     CONNECTED     30916    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30915    
unix  3      [ ]         STREAM     CONNECTED     30911    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30910    
unix  3      [ ]         STREAM     CONNECTED     30906    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30905    
unix  3      [ ]         STREAM     CONNECTED     30904    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30903    
unix  3      [ ]         STREAM     CONNECTED     30860    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     30859    
unix  3      [ ]         STREAM     CONNECTED     30858    /tmp/orbit-user/linc-fe1-0-390de0c82074
unix  3      [ ]         STREAM     CONNECTED     30857    
unix  3      [ ]         STREAM     CONNECTED     30856    /tmp/orbit-user/linc-fe1-0-390de0c82074
unix  3      [ ]         STREAM     CONNECTED     30855    
unix  3      [ ]         STREAM     CONNECTED     30854    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30853    
unix  3      [ ]         STREAM     CONNECTED     30852    /tmp/.esd-1001/socket
unix  3      [ ]         STREAM     CONNECTED     30851    
unix  3      [ ]         STREAM     CONNECTED     30848    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30847    
unix  3      [ ]         STREAM     CONNECTED     30845    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     30844    
unix  3      [ ]         STREAM     CONNECTED     30843    /tmp/orbit-user/linc-fc5-0-3177ce4432878
unix  3      [ ]         STREAM     CONNECTED     30842    
unix  3      [ ]         STREAM     CONNECTED     30841    /tmp/orbit-user/linc-fc5-0-3177ce4432878
unix  3      [ ]         STREAM     CONNECTED     30840    
unix  3      [ ]         STREAM     CONNECTED     30839    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30838    
unix  3      [ ]         STREAM     CONNECTED     30837    /tmp/orbit-user/linc-fc5-0-3177ce4432878
unix  3      [ ]         STREAM     CONNECTED     30836    
unix  3      [ ]         STREAM     CONNECTED     30833    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30832    
unix  3      [ ]         STREAM     CONNECTED     30830    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30829    
unix  3      [ ]         STREAM     CONNECTED     30828    @/tmp/.ICE-unix/3930
unix  3      [ ]         STREAM     CONNECTED     30827    
unix  3      [ ]         STREAM     CONNECTED     30825    /home/user/.pulse/dcf720acb4dce022dd6186024ce0ffe1-runtime/native
unix  3      [ ]         STREAM     CONNECTED     30824    
unix  3      [ ]         STREAM     CONNECTED     30780    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30779    
unix  3      [ ]         STREAM     CONNECTED     30774    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30773    
unix  3      [ ]         STREAM     CONNECTED     30756    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30755    
unix  3      [ ]         STREAM     CONNECTED     30741    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30740    
unix  3      [ ]         STREAM     CONNECTED     30738    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30737    
unix  3      [ ]         STREAM     CONNECTED     30736    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     30735    
unix  3      [ ]         STREAM     CONNECTED     30731    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30730    
unix  3      [ ]         STREAM     CONNECTED     30721    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     30720    
unix  3      [ ]         STREAM     CONNECTED     30716    /tmp/orbit-user/linc-fe1-0-390de0c82074
unix  3      [ ]         STREAM     CONNECTED     30715    
unix  3      [ ]         STREAM     CONNECTED     30710    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30709    
unix  3      [ ]         STREAM     CONNECTED     30707    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30706    
unix  3      [ ]         STREAM     CONNECTED     30702    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     30701    
unix  3      [ ]         STREAM     CONNECTED     30692    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     30691    
unix  3      [ ]         STREAM     CONNECTED     30668    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     30667    
unix  3      [ ]         STREAM     CONNECTED     30666    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30665    
unix  3      [ ]         STREAM     CONNECTED     30664    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30663    
unix  3      [ ]         STREAM     CONNECTED     30653    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30652    
unix  3      [ ]         STREAM     CONNECTED     30641    /tmp/orbit-user/linc-fef-0-574612e6da3a2
unix  3      [ ]         STREAM     CONNECTED     30640    
unix  3      [ ]         STREAM     CONNECTED     30637    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30636    
unix  3      [ ]         STREAM     CONNECTED     30631    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30630    
unix  3      [ ]         STREAM     CONNECTED     30626    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     30625    
unix  3      [ ]         STREAM     CONNECTED     30624    /tmp/orbit-user/linc-fdf-0-2bb042986aa09
unix  3      [ ]         STREAM     CONNECTED     30623    
unix  3      [ ]         STREAM     CONNECTED     30622    /tmp/orbit-user/linc-fd5-0-3b0501294c372
unix  3      [ ]         STREAM     CONNECTED     30621    
unix  3      [ ]         STREAM     CONNECTED     30620    /tmp/orbit-user/linc-fdc-0-17e21e885cc1e
unix  3      [ ]         STREAM     CONNECTED     30619    
unix  3      [ ]         STREAM     CONNECTED     30618    /tmp/orbit-user/linc-fdd-0-29b6d08156f59
unix  3      [ ]         STREAM     CONNECTED     30617    
unix  3      [ ]         STREAM     CONNECTED     30616    /tmp/orbit-user/linc-fcf-0-7683e7504fea7
unix  3      [ ]         STREAM     CONNECTED     30615    
unix  3      [ ]         STREAM     CONNECTED     30614    /tmp/orbit-user/linc-fd0-0-3d9ea7b744a9d
unix  3      [ ]         STREAM     CONNECTED     30613    
unix  3      [ ]         STREAM     CONNECTED     30611    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30610    
unix  3      [ ]         STREAM     CONNECTED     30607    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30606    
unix  3      [ ]         STREAM     CONNECTED     30600    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30599    
unix  3      [ ]         STREAM     CONNECTED     30598    /tmp/orbit-user/linc-fdf-0-2bb042986aa09
unix  3      [ ]         STREAM     CONNECTED     30597    
unix  3      [ ]         STREAM     CONNECTED     30596    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30595    
unix  3      [ ]         STREAM     CONNECTED     30593    @/dbus-vfs-daemon/socket-DsMIvTIL
unix  3      [ ]         STREAM     CONNECTED     30592    
unix  3      [ ]         STREAM     CONNECTED     30591    @/dbus-vfs-daemon/socket-KErA5vYx
unix  3      [ ]         STREAM     CONNECTED     30590    
unix  3      [ ]         STREAM     CONNECTED     30589    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30588    
unix  3      [ ]         STREAM     CONNECTED     30587    /tmp/orbit-user/linc-fdf-0-2bb042986aa09
unix  3      [ ]         STREAM     CONNECTED     30586    
unix  3      [ ]         STREAM     CONNECTED     30583    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30582    
unix  3      [ ]         STREAM     CONNECTED     30579    @/dbus-vfs-daemon/socket-2u11DAEk
unix  3      [ ]         STREAM     CONNECTED     30578    
unix  3      [ ]         STREAM     CONNECTED     30577    @/dbus-vfs-daemon/socket-NoMFYCfA
unix  3      [ ]         STREAM     CONNECTED     30576    
unix  3      [ ]         STREAM     CONNECTED     30573    /tmp/orbit-user/linc-fdc-0-17e21e885cc1e
unix  3      [ ]         STREAM     CONNECTED     30572    
unix  3      [ ]         STREAM     CONNECTED     30571    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30570    
unix  3      [ ]         STREAM     CONNECTED     30569    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30568    
unix  3      [ ]         STREAM     CONNECTED     30566    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30565    
unix  3      [ ]         STREAM     CONNECTED     30564    /tmp/orbit-user/linc-fdd-0-29b6d08156f59
unix  3      [ ]         STREAM     CONNECTED     30563    
unix  3      [ ]         STREAM     CONNECTED     30562    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30561    
unix  3      [ ]         STREAM     CONNECTED     30557    /tmp/orbit-user/linc-fdc-0-17e21e885cc1e
unix  3      [ ]         STREAM     CONNECTED     30556    
unix  3      [ ]         STREAM     CONNECTED     30553    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30552    
unix  3      [ ]         STREAM     CONNECTED     30551    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30550    
unix  3      [ ]         STREAM     CONNECTED     30549    /tmp/orbit-user/linc-fcf-0-7683e7504fea7
unix  3      [ ]         STREAM     CONNECTED     30548    
unix  3      [ ]         STREAM     CONNECTED     30547    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30546    
unix  3      [ ]         STREAM     CONNECTED     30545    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30544    
unix  3      [ ]         STREAM     CONNECTED     30543    /tmp/orbit-user/linc-fdd-0-29b6d08156f59
unix  3      [ ]         STREAM     CONNECTED     30542    
unix  3      [ ]         STREAM     CONNECTED     30534    /tmp/orbit-user/linc-fd5-0-3b0501294c372
unix  3      [ ]         STREAM     CONNECTED     30533    
unix  3      [ ]         STREAM     CONNECTED     30532    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30531    
unix  3      [ ]         STREAM     CONNECTED     30530    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30529    
unix  3      [ ]         STREAM     CONNECTED     30527    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30526    
unix  3      [ ]         STREAM     CONNECTED     30525    /tmp/orbit-user/linc-fcf-0-7683e7504fea7
unix  3      [ ]         STREAM     CONNECTED     30524    
unix  3      [ ]         STREAM     CONNECTED     30521    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30520    
unix  3      [ ]         STREAM     CONNECTED     30517    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30516    
unix  3      [ ]         STREAM     CONNECTED     30514    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30513    
unix  3      [ ]         STREAM     CONNECTED     30515    /tmp/orbit-user/linc-fd5-0-3b0501294c372
unix  3      [ ]         STREAM     CONNECTED     30511    
unix  3      [ ]         STREAM     CONNECTED     30519    /tmp/orbit-user/linc-fd0-0-3d9ea7b744a9d
unix  3      [ ]         STREAM     CONNECTED     30507    
unix  3      [ ]         STREAM     CONNECTED     30506    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30505    
unix  3      [ ]         STREAM     CONNECTED     30503    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30502    
unix  3      [ ]         STREAM     CONNECTED     30499    /tmp/orbit-user/linc-fd0-0-3d9ea7b744a9d
unix  3      [ ]         STREAM     CONNECTED     30498    
unix  3      [ ]         STREAM     CONNECTED     30497    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30496    
unix  3      [ ]         STREAM     CONNECTED     30491    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30490    
unix  3      [ ]         STREAM     CONNECTED     30478    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30477    
unix  3      [ ]         STREAM     CONNECTED     30475    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30474    
unix  3      [ ]         STREAM     CONNECTED     30462    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30461    
unix  3      [ ]         STREAM     CONNECTED     30460    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30459    
unix  3      [ ]         STREAM     CONNECTED     30458    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30457    
unix  3      [ ]         STREAM     CONNECTED     30456    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30455    
unix  3      [ ]         STREAM     CONNECTED     30454    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30453    
unix  3      [ ]         STREAM     CONNECTED     30450    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30449    
unix  3      [ ]         STREAM     CONNECTED     30101    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     30100    
unix  3      [ ]         STREAM     CONNECTED     30095    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30094    
unix  3      [ ]         STREAM     CONNECTED     30088    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30087    
unix  3      [ ]         STREAM     CONNECTED     30059    /tmp/orbit-user/linc-f9a-0-6a0b68448d09b
unix  3      [ ]         STREAM     CONNECTED     30058    
unix  3      [ ]         STREAM     CONNECTED     30053    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     30052    
unix  3      [ ]         STREAM     CONNECTED     30045    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30044    
unix  3      [ ]         STREAM     CONNECTED     30013    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     30012    
unix  3      [ ]         STREAM     CONNECTED     30010    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     30009    
unix  3      [ ]         STREAM     CONNECTED     30008    /tmp/orbit-user/linc-fb5-0-41860e816fd68
unix  3      [ ]         STREAM     CONNECTED     30007    
unix  3      [ ]         STREAM     CONNECTED     29903    @/tmp/.ICE-unix/3930
unix  3      [ ]         STREAM     CONNECTED     29902    
unix  3      [ ]         STREAM     CONNECTED     29899    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29898    
unix  3      [ ]         STREAM     CONNECTED     29895    /home/user/.pulse/dcf720acb4dce022dd6186024ce0ffe1-runtime/native
unix  3      [ ]         STREAM     CONNECTED     29894    
unix  3      [ ]         STREAM     CONNECTED     29893    /tmp/orbit-user/linc-fb3-0-657baafbd9262
unix  3      [ ]         STREAM     CONNECTED     29892    
unix  3      [ ]         STREAM     CONNECTED     29889    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     29888    
unix  3      [ ]         STREAM     CONNECTED     29881    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29880    
unix  3      [ ]         STREAM     CONNECTED     29835    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     29834    
unix  3      [ ]         STREAM     CONNECTED     29825    @/dbus-vfs-daemon/socket-4QZBe3s8
unix  3      [ ]         STREAM     CONNECTED     29824    
unix  3      [ ]         STREAM     CONNECTED     29826    @/dbus-vfs-daemon/socket-8TLwbfuc
unix  3      [ ]         STREAM     CONNECTED     29823    
unix  3      [ ]         STREAM     CONNECTED     29817    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29816    
unix  3      [ ]         STREAM     CONNECTED     29811    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29810    
unix  3      [ ]         STREAM     CONNECTED     29789    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29788    
unix  3      [ ]         STREAM     CONNECTED     29787    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29786    
unix  3      [ ]         STREAM     CONNECTED     29785    @/tmp/.ICE-unix/3930
unix  3      [ ]         STREAM     CONNECTED     29784    
unix  3      [ ]         STREAM     CONNECTED     29783    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29782    
unix  3      [ ]         STREAM     CONNECTED     29781    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29780    
unix  3      [ ]         STREAM     CONNECTED     29771    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29770    
unix  3      [ ]         STREAM     CONNECTED     29769    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     29768    
unix  3      [ ]         STREAM     CONNECTED     29763    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     29762    
unix  3      [ ]         STREAM     CONNECTED     29761    /tmp/orbit-user/linc-f9d-0-bfe4c852e367
unix  3      [ ]         STREAM     CONNECTED     29760    
unix  3      [ ]         STREAM     CONNECTED     29757    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     29756    
unix  3      [ ]         STREAM     CONNECTED     29752    /tmp/orbit-user/linc-f95-0-15d7e6ff2baa9
unix  3      [ ]         STREAM     CONNECTED     29751    
unix  3      [ ]         STREAM     CONNECTED     29748    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     29747    
unix  3      [ ]         STREAM     CONNECTED     29743    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29742    
unix  3      [ ]         STREAM     CONNECTED     29740    @/tmp/.ICE-unix/3930
unix  3      [ ]         STREAM     CONNECTED     29739    
unix  3      [ ]         STREAM     CONNECTED     29738    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29737    
unix  3      [ ]         STREAM     CONNECTED     29735    /tmp/orbit-user/linc-f99-0-6d818bb9220b4
unix  3      [ ]         STREAM     CONNECTED     29734    
unix  3      [ ]         STREAM     CONNECTED     29731    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     29730    
unix  3      [ ]         STREAM     CONNECTED     29729    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     29728    
unix  3      [ ]         STREAM     CONNECTED     29726    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29725    
unix  3      [ ]         STREAM     CONNECTED     29707    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     29706    
unix  3      [ ]         STREAM     CONNECTED     29694    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29693    
unix  3      [ ]         STREAM     CONNECTED     29687    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29686    
unix  2      [ ]         DGRAM                    29683    
unix  3      [ ]         STREAM     CONNECTED     29674    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29673    
unix  3      [ ]         STREAM     CONNECTED     29664    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29663    
unix  3      [ ]         STREAM     CONNECTED     29649    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29648    
unix  3      [ ]         STREAM     CONNECTED     29635    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     29634    
unix  3      [ ]         STREAM     CONNECTED     29361    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29360    
unix  3      [ ]         STREAM     CONNECTED     29356    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29355    
unix  3      [ ]         STREAM     CONNECTED     29308    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29307    
unix  3      [ ]         STREAM     CONNECTED     29302    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29301    
unix  3      [ ]         STREAM     CONNECTED     29298    /tmp/orbit-user/linc-f8b-0-39ff6d1397f73
unix  3      [ ]         STREAM     CONNECTED     29297    
unix  3      [ ]         STREAM     CONNECTED     29294    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     29293    
unix  3      [ ]         STREAM     CONNECTED     29287    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29286    
unix  3      [ ]         STREAM     CONNECTED     29284    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29283    
unix  3      [ ]         STREAM     CONNECTED     29276    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     29275    
unix  2      [ ]         DGRAM                    29271    
unix  3      [ ]         STREAM     CONNECTED     29183    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     29182    
unix  3      [ ]         STREAM     CONNECTED     29180    /tmp/orbit-user/linc-f5a-0-22d8912770d0d
unix  3      [ ]         STREAM     CONNECTED     29179    
unix  3      [ ]         STREAM     CONNECTED     29176    /tmp/orbit-user/linc-f85-0-9334c4d66146
unix  3      [ ]         STREAM     CONNECTED     29175    
unix  3      [ ]         STREAM     CONNECTED     29172    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     29171    
unix  3      [ ]         STREAM     CONNECTED     28701    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     28700    
unix  3      [ ]         STREAM     CONNECTED     28661    @/tmp/dbus-BNBwyIYikX
unix  3      [ ]         STREAM     CONNECTED     28660    
unix  3      [ ]         STREAM     CONNECTED     28658    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     28657    
unix  3      [ ]         STREAM     CONNECTED     28654    
unix  3      [ ]         STREAM     CONNECTED     28653    
unix  3      [ ]         STREAM     CONNECTED     28652    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     28651    
unix  3      [ ]         STREAM     CONNECTED     28640    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     28639    
unix  3      [ ]         STREAM     CONNECTED     28485    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     28484    
unix  2      [ ]         DGRAM                    28377    
unix  3      [ ]         STREAM     CONNECTED     28378    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     28376    
unix  3      [ ]         STREAM     CONNECTED     28224    @/tmp/gdm-session-YHWWFudI
unix  3      [ ]         STREAM     CONNECTED     28223    
unix  3      [ ]         STREAM     CONNECTED     28220    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     28219    
unix  3      [ ]         STREAM     CONNECTED     27202    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     27200    
unix  3      [ ]         STREAM     CONNECTED     27189    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     27188    
unix  3      [ ]         STREAM     CONNECTED     27084    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     27083    
unix  3      [ ]         STREAM     CONNECTED     27034    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     27033    
unix  3      [ ]         STREAM     CONNECTED     27029    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     27028    
unix  3      [ ]         STREAM     CONNECTED     27025    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     27024    
unix  3      [ ]         STREAM     CONNECTED     26985    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     26984    
unix  2      [ ]         DGRAM                    21337    
unix  3      [ ]         STREAM     CONNECTED     9592     
unix  3      [ ]         STREAM     CONNECTED     9591     
unix  3      [ ]         STREAM     CONNECTED     9024     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     9023     
unix  3      [ ]         STREAM     CONNECTED     9016     @/var/run/hald/dbus-vpC1fVam4L
unix  3      [ ]         STREAM     CONNECTED     8991     
unix  3      [ ]         STREAM     CONNECTED     8989     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8988     
unix  3      [ ]         STREAM     CONNECTED     8985     @/var/run/hald/dbus-vpC1fVam4L
unix  3      [ ]         STREAM     CONNECTED     8976     
unix  3      [ ]         STREAM     CONNECTED     8945     @/var/run/hald/dbus-vpC1fVam4L
unix  3      [ ]         STREAM     CONNECTED     8872     
unix  3      [ ]         STREAM     CONNECTED     8774     @/var/run/hald/dbus-ooaQrP13a1
unix  3      [ ]         STREAM     CONNECTED     8773     
unix  3      [ ]         STREAM     CONNECTED     8750     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8749     
unix  3      [ ]         STREAM     CONNECTED     8563     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8562     
unix  3      [ ]         STREAM     CONNECTED     8558     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8557     
unix  3      [ ]         STREAM     CONNECTED     7646     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7645     
unix  3      [ ]         STREAM     CONNECTED     7639     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7638     
unix  2      [ ]         DGRAM                    6700     
unix  3      [ ]         STREAM     CONNECTED     6598     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6597     
unix  3      [ ]         STREAM     CONNECTED     6534     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6533     
unix  2      [ ]         DGRAM                    6525     
unix  2      [ ]         DGRAM                    5169     
unix  2      [ ]         DGRAM                    4796     
unix  3      [ ]         STREAM     CONNECTED     4771     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4770     
unix  2      [ ]         DGRAM                    4769     
unix  2      [ ]         DGRAM                    4757     
unix  3      [ ]         STREAM     CONNECTED     4701     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4700     
unix  3      [ ]         STREAM     CONNECTED     4651     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4650     
unix  2      [ ]         DGRAM                    4632     
unix  3      [ ]         STREAM     CONNECTED     4624     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4623     
unix  3      [ ]         STREAM     CONNECTED     4605     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4604     
unix  3      [ ]         STREAM     CONNECTED     4597     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4596     
unix  3      [ ]         STREAM     CONNECTED     4591     
unix  3      [ ]         STREAM     CONNECTED     4590     
unix  3      [ ]         STREAM     CONNECTED     4588     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4587     
unix  2      [ ]         DGRAM                    4575     
unix  3      [ ]         STREAM     CONNECTED     4560     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4559     
unix  2      [ ]         DGRAM                    4556     
unix  2      [ ]         DGRAM                    4537     
unix  3      [ ]         STREAM     CONNECTED     4496     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4495     
unix  3      [ ]         STREAM     CONNECTED     4491     
unix  3      [ ]         STREAM     CONNECTED     4490     
unix  3      [ ]         DGRAM                    3111     
unix  3      [ ]         DGRAM                    3110     
unix  3      [ ]         STREAM     CONNECTED     3054     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     3053     
user@kompik ~ $ 

```
After closing Opera I checked this command and I wonder if it is normal? But when I looked at System monitor Opera was already closed and there was not outbound traffic? I use Gufw and all inbound are blocked and outbound open.

---

### Post by bodhi.zazen on 2010-11-30
That looks as if you ran a command and dumped the output on these forums.

What question do you have about what part or parts of the output ?

---

### Post by arapaho on 2010-12-01
> **bodhi.zazen said:**
> What question do you have about what part or parts of the output ?

I read:
"netstat (network statistics) is a command-line tool that displays network connections (both incoming and outgoing), routing tables, and a number of network interface statistics."
"-a : Displays all active TCP connections and the TCP and UDP ports on which the computer is listening."
[http://en.wikipedia.org/wiki/Netstat](http://en.wikipedia.org/wiki/Netstat)
So, I'm susrprised that there are any connections at all because I run netstat after closing Opera, so now connections should be displeyed at all. I don't now how to interpret those results.

---

### Post by brian_p on 2010-12-01
> **arapaho said:**
> 

So, I'm susrprised that there are any connections at all because I run netstat after closing Opera, so now connections should be displeyed at all. I don't now how to interpret those results.

From the netstat manual:

> TIME_WAIT
              The socket is waiting after close to handle packets still in the network.


If you had looked again a few minutes later those connections wouldn't have been there.

---

