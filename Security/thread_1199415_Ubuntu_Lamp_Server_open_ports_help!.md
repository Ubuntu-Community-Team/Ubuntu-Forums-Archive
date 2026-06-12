---
title: "Ubuntu Lamp Server open ports help!"
date: 2009-06-28
forum: Security
---

### Post by waloshin on 2009-06-28
I ran netstat -a and got:
Any thing alarming?
Also I am running an Smf forum.

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:webcache              *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        1      0 192.168.1.5:44761       gx-in-f100.google.c:www CLOSE_WAIT 
udp        0      0 *:42766                 *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*                                
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     15619    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     17134    /tmp/orbit-server1/linc-1941-0-3998b248a8224
unix  2      [ ACC ]     STREAM     LISTENING     17165    /tmp/seahorse-mI8Zvi/S.gpg-agent
unix  11     [ ]         DGRAM                    14370    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     21290    /tmp/orbit-server1/linc-19f8-0-7ada7c813494b
unix  2      [ ACC ]     STREAM     LISTENING     21328    /tmp/orbit-server1/linc-1a02-0-5afa030953fd0
unix  2      [ ACC ]     STREAM     LISTENING     14648    /var/run/mysqld/mysqld.sock
unix  2      [ ]         DGRAM                    7974     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     17203    /tmp/orbit-server1/linc-1941-0-2cd235c0de27a
unix  2      [ ACC ]     STREAM     LISTENING     21626    /tmp/orbit-server1/linc-1a3b-0-354dcf32cee85
unix  2      [ ACC ]     STREAM     LISTENING     24581    /tmp/orbit-server1/linc-1b96-0-13dc9b6168d65
unix  2      [ ACC ]     STREAM     LISTENING     27387    /tmp/orbit-server1/linc-1c12-0-26a1283dbc5c
unix  2      [ ACC ]     STREAM     LISTENING     15669    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     16520    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  2      [ ACC ]     STREAM     LISTENING     17207    /tmp/.ICE-unix/6465
unix  2      [ ACC ]     STREAM     LISTENING     17273    /tmp/orbit-server1/linc-19aa-0-28503cf73d068
unix  2      [ ACC ]     STREAM     LISTENING     24613    /tmp/orbit-server1/linc-1b98-0-50bc90b57bdee
unix  2      [ ACC ]     STREAM     LISTENING     20157    /tmp/orbit-server1/linc-19ba-0-1d090733c59ec
unix  2      [ ]         DGRAM                    8200     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     20326    /tmp/orbit-server1/linc-19c2-0-536fcbc52a60
unix  2      [ ACC ]     STREAM     LISTENING     20389    /tmp/orbit-server1/linc-19c3-0-4ce1968c246e0
unix  2      [ ACC ]     STREAM     LISTENING     14460    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     21425    /tmp/orbit-server1/linc-1a14-0-5afa0309a6404
unix  2      [ ACC ]     STREAM     LISTENING     21050    /tmp/orbit-server1/linc-19ee-0-7edf0be1c8716
unix  2      [ ACC ]     STREAM     LISTENING     27792    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     20418    /tmp/orbit-server1/linc-19bf-0-4cdb5411613c3
unix  2      [ ACC ]     STREAM     LISTENING     14245    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     20690    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  2      [ ACC ]     STREAM     LISTENING     21193    /tmp/orbit-server1/linc-1a05-0-28cd09add4865
unix  2      [ ACC ]     STREAM     LISTENING     17224    @/tmp/dbus-MP0DS5A5UM
unix  2      [ ACC ]     STREAM     LISTENING     21647    /tmp/orbit-server1/linc-1a3e-0-66091c8a18d00
unix  2      [ ACC ]     STREAM     LISTENING     16530    /tmp/orbit-server1/linc-193c-0-748fc6636d4f
unix  2      [ ACC ]     STREAM     LISTENING     16752    /tmp/keyring-QQmSWZ/socket
unix  2      [ ACC ]     STREAM     LISTENING     14559    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     16754    /tmp/keyring-QQmSWZ/ssh
unix  2      [ ACC ]     STREAM     LISTENING     16756    /tmp/keyring-QQmSWZ/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     26635    /tmp/orbit-server1/linc-1be3-0-4f66ae084a2c
unix  3      [ ]         STREAM     CONNECTED     27789    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     27788    
unix  3      [ ]         STREAM     CONNECTED     27403    
unix  3      [ ]         STREAM     CONNECTED     27402    
unix  3      [ ]         STREAM     CONNECTED     27395    /tmp/orbit-server1/linc-1c12-0-26a1283dbc5c
unix  3      [ ]         STREAM     CONNECTED     27393    
unix  3      [ ]         STREAM     CONNECTED     27392    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     27391    
unix  3      [ ]         STREAM     CONNECTED     27390    /tmp/orbit-server1/linc-1c12-0-26a1283dbc5c
unix  3      [ ]         STREAM     CONNECTED     27389    
unix  3      [ ]         STREAM     CONNECTED     27386    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     27385    
unix  3      [ ]         STREAM     CONNECTED     27383    /tmp/.ICE-unix/6465
unix  3      [ ]         STREAM     CONNECTED     27382    
unix  3      [ ]         STREAM     CONNECTED     27378    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     27377    
unix  3      [ ]         STREAM     CONNECTED     26638    /tmp/orbit-server1/linc-1be3-0-4f66ae084a2c
unix  3      [ ]         STREAM     CONNECTED     26637    
unix  3      [ ]         STREAM     CONNECTED     26634    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     26633    
unix  3      [ ]         STREAM     CONNECTED     26631    /tmp/.ICE-unix/6465
unix  3      [ ]         STREAM     CONNECTED     26630    
unix  3      [ ]         STREAM     CONNECTED     26626    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26625    
unix  3      [ ]         STREAM     CONNECTED     24836    @/dbus-vfs-daemon/socket-7TthACAJ
unix  3      [ ]         STREAM     CONNECTED     24835    
unix  3      [ ]         STREAM     CONNECTED     24834    @/dbus-vfs-daemon/socket-GD3qk9PC
unix  3      [ ]         STREAM     CONNECTED     24833    
unix  3      [ ]         STREAM     CONNECTED     24622    @/dbus-vfs-daemon/socket-EqaYQpKl
unix  3      [ ]         STREAM     CONNECTED     24621    
unix  3      [ ]         STREAM     CONNECTED     24623    @/dbus-vfs-daemon/socket-Qlcq6gju
unix  3      [ ]         STREAM     CONNECTED     24620    
unix  3      [ ]         STREAM     CONNECTED     24616    /tmp/orbit-server1/linc-1b98-0-50bc90b57bdee
unix  3      [ ]         STREAM     CONNECTED     24615    
unix  3      [ ]         STREAM     CONNECTED     24612    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     24611    
unix  3      [ ]         STREAM     CONNECTED     24605    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     24604    
unix  3      [ ]         STREAM     CONNECTED     24586    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     24585    
unix  3      [ ]         STREAM     CONNECTED     24584    /tmp/orbit-server1/linc-1b96-0-13dc9b6168d65
unix  3      [ ]         STREAM     CONNECTED     24583    
unix  3      [ ]         STREAM     CONNECTED     24580    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     24579    
unix  3      [ ]         STREAM     CONNECTED     24574    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     24573    
unix  3      [ ]         STREAM     CONNECTED     24571    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     24570    
unix  3      [ ]         STREAM     CONNECTED     24256    @/dbus-vfs-daemon/socket-j3lHQBYz
unix  3      [ ]         STREAM     CONNECTED     24255    
unix  3      [ ]         STREAM     CONNECTED     24257    @/dbus-vfs-daemon/socket-UennRxlo
unix  3      [ ]         STREAM     CONNECTED     24254    
unix  3      [ ]         STREAM     CONNECTED     24246    @/dbus-vfs-daemon/socket-2RWOK9hx
unix  3      [ ]         STREAM     CONNECTED     24245    
unix  3      [ ]         STREAM     CONNECTED     24247    @/dbus-vfs-daemon/socket-C8dFTnhU
unix  3      [ ]         STREAM     CONNECTED     24244    
unix  3      [ ]         STREAM     CONNECTED     24240    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     24239    
unix  3      [ ]         STREAM     CONNECTED     24235    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     24234    
unix  3      [ ]         STREAM     CONNECTED     21852    /tmp/orbit-server1/linc-19c2-0-536fcbc52a60
unix  3      [ ]         STREAM     CONNECTED     21851    
unix  3      [ ]         STREAM     CONNECTED     21841    /tmp/.ICE-unix/6465
unix  3      [ ]         STREAM     CONNECTED     21840    
unix  3      [ ]         STREAM     CONNECTED     21843    /tmp/orbit-server1/linc-19c2-0-536fcbc52a60
unix  3      [ ]         STREAM     CONNECTED     21839    
unix  3      [ ]         STREAM     CONNECTED     21838    /tmp/orbit-server1/linc-1a3e-0-66091c8a18d00
unix  3      [ ]         STREAM     CONNECTED     21837    
unix  3      [ ]         STREAM     CONNECTED     21836    /tmp/orbit-server1/linc-1a3b-0-354dcf32cee85
unix  3      [ ]         STREAM     CONNECTED     21835    
unix  3      [ ]         STREAM     CONNECTED     21654    /tmp/orbit-server1/linc-1a3e-0-66091c8a18d00
unix  3      [ ]         STREAM     CONNECTED     21653    
unix  3      [ ]         STREAM     CONNECTED     21652    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     21651    
unix  3      [ ]         STREAM     CONNECTED     21650    /tmp/orbit-server1/linc-1a3e-0-66091c8a18d00
unix  3      [ ]         STREAM     CONNECTED     21649    
unix  3      [ ]         STREAM     CONNECTED     21646    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     21645    
unix  3      [ ]         STREAM     CONNECTED     21641    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21640    
unix  3      [ ]         STREAM     CONNECTED     21633    /tmp/orbit-server1/linc-1a3b-0-354dcf32cee85
unix  3      [ ]         STREAM     CONNECTED     21632    
unix  3      [ ]         STREAM     CONNECTED     21631    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     21630    
unix  3      [ ]         STREAM     CONNECTED     21629    /tmp/orbit-server1/linc-1a3b-0-354dcf32cee85
unix  3      [ ]         STREAM     CONNECTED     21628    
unix  3      [ ]         STREAM     CONNECTED     21625    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     21624    
unix  3      [ ]         STREAM     CONNECTED     21620    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21619    
unix  3      [ ]         STREAM     CONNECTED     21519    /tmp/orbit-server1/linc-19ee-0-7edf0be1c8716
unix  3      [ ]         STREAM     CONNECTED     21518    
unix  3      [ ]         STREAM     CONNECTED     21517    /tmp/orbit-server1/linc-1a14-0-5afa0309a6404
unix  3      [ ]         STREAM     CONNECTED     21516    
unix  3      [ ]         STREAM     CONNECTED     21515    /tmp/orbit-server1/linc-1a02-0-5afa030953fd0
unix  3      [ ]         STREAM     CONNECTED     21514    
unix  3      [ ]         STREAM     CONNECTED     21513    /tmp/orbit-server1/linc-1a14-0-5afa0309a6404
unix  3      [ ]         STREAM     CONNECTED     21512    
unix  3      [ ]         STREAM     CONNECTED     21511    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     21510    
unix  3      [ ]         STREAM     CONNECTED     21503    @/dbus-vfs-daemon/socket-zpyXeM9Q
unix  3      [ ]         STREAM     CONNECTED     21502    
unix  3      [ ]         STREAM     CONNECTED     21501    @/dbus-vfs-daemon/socket-kbAaMHs1
unix  3      [ ]         STREAM     CONNECTED     21500    
unix  3      [ ]         STREAM     CONNECTED     21473    @/dbus-vfs-daemon/socket-GQOnAiEy
unix  3      [ ]         STREAM     CONNECTED     21471    
unix  3      [ ]         STREAM     CONNECTED     21472    @/dbus-vfs-daemon/socket-iC4WohOA
unix  3      [ ]         STREAM     CONNECTED     21470    
unix  3      [ ]         STREAM     CONNECTED     21428    /tmp/orbit-server1/linc-1a14-0-5afa0309a6404
unix  3      [ ]         STREAM     CONNECTED     21427    
unix  3      [ ]         STREAM     CONNECTED     21424    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     21423    
unix  3      [ ]         STREAM     CONNECTED     21345    /tmp/orbit-server1/linc-19c2-0-536fcbc52a60
unix  3      [ ]         STREAM     CONNECTED     21344    
unix  3      [ ]         STREAM     CONNECTED     21343    /tmp/orbit-server1/linc-1a05-0-28cd09add4865
unix  3      [ ]         STREAM     CONNECTED     21342    
unix  3      [ ]         STREAM     CONNECTED     21336    /tmp/orbit-server1/linc-1a02-0-5afa030953fd0
unix  3      [ ]         STREAM     CONNECTED     21335    
unix  3      [ ]         STREAM     CONNECTED     21334    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     21333    
unix  3      [ ]         STREAM     CONNECTED     21331    /tmp/orbit-server1/linc-1a02-0-5afa030953fd0
unix  3      [ ]         STREAM     CONNECTED     21330    
unix  3      [ ]         STREAM     CONNECTED     21327    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     21326    
unix  3      [ ]         STREAM     CONNECTED     21324    /tmp/.ICE-unix/6465
unix  3      [ ]         STREAM     CONNECTED     21323    
unix  3      [ ]         STREAM     CONNECTED     21318    @/dbus-vfs-daemon/socket-OK1KIKS7
unix  3      [ ]         STREAM     CONNECTED     21317    
unix  3      [ ]         STREAM     CONNECTED     21319    @/dbus-vfs-daemon/socket-9w69O4A1
unix  3      [ ]         STREAM     CONNECTED     21316    
unix  3      [ ]         STREAM     CONNECTED     21315    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21314    
unix  3      [ ]         STREAM     CONNECTED     21308    @/dbus-vfs-daemon/socket-zYzbGBnD
unix  3      [ ]         STREAM     CONNECTED     21307    
unix  3      [ ]         STREAM     CONNECTED     21309    @/dbus-vfs-daemon/socket-BF2JZMJf
unix  3      [ ]         STREAM     CONNECTED     21306    
unix  3      [ ]         STREAM     CONNECTED     21297    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     21296    
unix  3      [ ]         STREAM     CONNECTED     21293    /tmp/orbit-server1/linc-19f8-0-7ada7c813494b
unix  3      [ ]         STREAM     CONNECTED     21292    
unix  3      [ ]         STREAM     CONNECTED     21289    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     21288    
unix  3      [ ]         STREAM     CONNECTED     21284    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     21283    
unix  3      [ ]         STREAM     CONNECTED     21274    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     21273    
unix  3      [ ]         STREAM     CONNECTED     21249    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     21248    
unix  3      [ ]         STREAM     CONNECTED     21245    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     21244    
unix  3      [ ]         STREAM     CONNECTED     21241    /tmp/orbit-server1/linc-1a05-0-28cd09add4865
unix  3      [ ]         STREAM     CONNECTED     21240    
unix  3      [ ]         STREAM     CONNECTED     21239    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     21238    
unix  3      [ ]         STREAM     CONNECTED     21227    @/dbus-vfs-daemon/socket-66s1CgP3
unix  3      [ ]         STREAM     CONNECTED     21226    
unix  3      [ ]         STREAM     CONNECTED     21228    @/dbus-vfs-daemon/socket-Nh8vs1pI
unix  3      [ ]         STREAM     CONNECTED     21225    
unix  3      [ ]         STREAM     CONNECTED     21218    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     21217    
unix  3      [ ]         STREAM     CONNECTED     21199    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     21198    
unix  3      [ ]         STREAM     CONNECTED     21196    /tmp/orbit-server1/linc-1a05-0-28cd09add4865
unix  3      [ ]         STREAM     CONNECTED     21195    
unix  3      [ ]         STREAM     CONNECTED     21192    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     21187    
unix  3      [ ]         STREAM     CONNECTED     21180    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21179    
unix  3      [ ]         STREAM     CONNECTED     21096    /tmp/orbit-server1/linc-19ee-0-7edf0be1c8716
unix  3      [ ]         STREAM     CONNECTED     21095    
unix  3      [ ]         STREAM     CONNECTED     21094    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     21093    
unix  3      [ ]         STREAM     CONNECTED     21092    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     21091    
unix  3      [ ]         STREAM     CONNECTED     21053    /tmp/orbit-server1/linc-19ee-0-7edf0be1c8716
unix  3      [ ]         STREAM     CONNECTED     21052    
unix  3      [ ]         STREAM     CONNECTED     21049    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     21047    
unix  3      [ ]         STREAM     CONNECTED     21001    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21000    
unix  3      [ ]         STREAM     CONNECTED     20916    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     20915    
unix  3      [ ]         STREAM     CONNECTED     21003    /tmp/.ICE-unix/6465
unix  3      [ ]         STREAM     CONNECTED     20837    
unix  3      [ ]         STREAM     CONNECTED     20833    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20832    
unix  3      [ ]         STREAM     CONNECTED     20769    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     20768    
unix  3      [ ]         STREAM     CONNECTED     20767    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20766    
unix  3      [ ]         STREAM     CONNECTED     20700    /tmp/orbit-server1/linc-19c3-0-4ce1968c246e0
unix  3      [ ]         STREAM     CONNECTED     20699    
unix  3      [ ]         STREAM     CONNECTED     20698    /tmp/orbit-server1/linc-19c2-0-536fcbc52a60
unix  3      [ ]         STREAM     CONNECTED     20697    
unix  3      [ ]         STREAM     CONNECTED     20696    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     20695    
unix  3      [ ]         STREAM     CONNECTED     20694    /tmp/orbit-server1/linc-19c7-0-3775ea3dd6302
unix  3      [ ]         STREAM     CONNECTED     20693    
unix  3      [ ]         STREAM     CONNECTED     20542    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     20541    
unix  3      [ ]         STREAM     CONNECTED     20539    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     20538    
unix  3      [ ]         STREAM     CONNECTED     20452    /tmp/.ICE-unix/6465
unix  3      [ ]         STREAM     CONNECTED     20451    
unix  3      [ ]         STREAM     CONNECTED     20429    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     20428    
unix  3      [ ]         STREAM     CONNECTED     20422    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     20421    
unix  3      [ ]         STREAM     CONNECTED     20426    /tmp/orbit-server1/linc-19bf-0-4cdb5411613c3
unix  3      [ ]         STREAM     CONNECTED     20420    
unix  3      [ ]         STREAM     CONNECTED     20417    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     20416    
unix  3      [ ]         STREAM     CONNECTED     20412    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20411    
unix  3      [ ]         STREAM     CONNECTED     20392    /tmp/orbit-server1/linc-19c3-0-4ce1968c246e0
unix  3      [ ]         STREAM     CONNECTED     20391    
unix  3      [ ]         STREAM     CONNECTED     20388    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     20387    
unix  3      [ ]         STREAM     CONNECTED     20385    /tmp/.ICE-unix/6465
unix  3      [ ]         STREAM     CONNECTED     20384    
unix  3      [ ]         STREAM     CONNECTED     20380    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20378    
unix  3      [ ]         STREAM     CONNECTED     20329    /tmp/orbit-server1/linc-19c2-0-536fcbc52a60
unix  3      [ ]         STREAM     CONNECTED     20328    
unix  3      [ ]         STREAM     CONNECTED     20325    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     20324    
unix  3      [ ]         STREAM     CONNECTED     20322    /tmp/.ICE-unix/6465
unix  3      [ ]         STREAM     CONNECTED     20320    
unix  3      [ ]         STREAM     CONNECTED     20316    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20315    
unix  3      [ ]         STREAM     CONNECTED     20212    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     20211    
unix  3      [ ]         STREAM     CONNECTED     20160    /tmp/orbit-server1/linc-19ba-0-1d090733c59ec
unix  3      [ ]         STREAM     CONNECTED     20159    
unix  3      [ ]         STREAM     CONNECTED     20156    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     20155    
unix  3      [ ]         STREAM     CONNECTED     20151    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20150    
unix  2      [ ]         DGRAM                    17280    
unix  2      [ ]         DGRAM                    17279    
unix  3      [ ]         STREAM     CONNECTED     17276    /tmp/orbit-server1/linc-19aa-0-28503cf73d068
unix  3      [ ]         STREAM     CONNECTED     17275    
unix  3      [ ]         STREAM     CONNECTED     17272    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     17271    
unix  3      [ ]         STREAM     CONNECTED     17267    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     17266    
unix  3      [ ]         STREAM     CONNECTED     17264    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17263    
unix  3      [ ]         STREAM     CONNECTED     17234    @/tmp/dbus-MP0DS5A5UM
unix  3      [ ]         STREAM     CONNECTED     17233    
unix  3      [ ]         STREAM     CONNECTED     17232    
unix  3      [ ]         STREAM     CONNECTED     17231    
unix  2      [ ]         STREAM     CONNECTED     17211    /tmp/keyring-QQmSWZ/socket
unix  3      [ ]         STREAM     CONNECTED     17206    /tmp/orbit-server1/linc-1941-0-2cd235c0de27a
unix  3      [ ]         STREAM     CONNECTED     17205    
unix  3      [ ]         STREAM     CONNECTED     17202    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     17201    
unix  3      [ ]         STREAM     CONNECTED     17171    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17170    
unix  3      [ ]         STREAM     CONNECTED     17137    /tmp/orbit-server1/linc-1941-0-3998b248a8224
unix  3      [ ]         STREAM     CONNECTED     17136    
unix  3      [ ]         STREAM     CONNECTED     17133    /tmp/orbit-server1/linc-193e-0-3378a48af0fd1
unix  3      [ ]         STREAM     CONNECTED     17132    
unix  3      [ ]         STREAM     CONNECTED     17128    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17127    
unix  3      [ ]         STREAM     CONNECTED     16768    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16767    
unix  3      [ ]         STREAM     CONNECTED     16760    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16759    
unix  3      [ ]         STREAM     CONNECTED     16199    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16198    
unix  2      [ ]         DGRAM                    15707    
unix  3      [ ]         STREAM     CONNECTED     15680    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     15679    
unix  4      [ ]         STREAM     CONNECTED     16200    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15671    
unix  2      [ ]         STREAM     CONNECTED     15185    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     14944    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14943    
unix  3      [ ]         STREAM     CONNECTED     14914    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14913    
unix  2      [ ]         DGRAM                    14912    
unix  2      [ ]         DGRAM                    14823    
unix  2      [ ]         DGRAM                    14646    
unix  3      [ ]         STREAM     CONNECTED     14562    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14561    
unix  3      [ ]         STREAM     CONNECTED     14556    
unix  3      [ ]         STREAM     CONNECTED     14555    
unix  2      [ ]         DGRAM                    14553    
unix  3      [ ]         STREAM     CONNECTED     14522    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14521    
unix  3      [ ]         STREAM     CONNECTED     14515    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14514    
unix  3      [ ]         STREAM     CONNECTED     14487    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14486    
unix  2      [ ]         DGRAM                    14482    
unix  3      [ ]         STREAM     CONNECTED     14470    
unix  3      [ ]         STREAM     CONNECTED     14469    
unix  2      [ ]         DGRAM                    14438

---

### Post by bodhi.zazen on 2009-06-29
It all looks normal to me ;)

FYI, I like the output of :

```
sudo lsof -i -n -P
```Or scanning from a second box on your LAN (if you scan from your server you get "false positives, like the X server I assume you are running, via the lo interface).

---

