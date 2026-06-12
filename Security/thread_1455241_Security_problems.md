---
title: "Security problems?"
date: 2010-04-15
forum: Security
---

### Post by Lakeside5 on 2010-04-15
Does anyone see anything alarming here? I am running Ubuntu Intrepid Ibex and was successfully hosting my Joomal website when suddenly I lost localhost (it tries to load but won't) and also can't access my site at it's site address.
   Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      5383/dovecot    
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      5383/dovecot    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4884/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      5350/smbd       
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      5383/dovecot    
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      5383/dovecot    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      17379/apache2   
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      5964/perl       
tcp        0      0 192.168.1.99:53         0.0.0.0:*               LISTEN      4764/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      4764/named      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      4789/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5301/cupsd      
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN      5662/(squid)    
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      4969/postgres   
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      4764/named      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      5350/smbd       
tcp6       0      0 :::8009                 :::*                    LISTEN      5880/jsvc       
tcp6       0      0 :::8080                 :::*                    LISTEN      5880/jsvc       
tcp6       0      0 :::53                   :::*                    LISTEN      4764/named      
tcp6       0      0 :::22                   :::*                    LISTEN      4789/sshd       
tcp6       0      0 ::1:953                 :::*                    LISTEN      4764/named      
udp        0      0 0.0.0.0:38151           0.0.0.0:*                           4764/named      
udp        0      0 192.168.1.99:137        0.0.0.0:*                           5348/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           5348/nmbd       
udp        0      0 192.168.1.99:138        0.0.0.0:*                           5348/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           5348/nmbd       
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           5964/perl       
udp        0      0 192.168.1.99:53         0.0.0.0:*                           4764/named      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           4764/named      
udp        0      0 0.0.0.0:37432           0.0.0.0:*                           5662/(squid)    
udp        0      0 0.0.0.0:3130            0.0.0.0:*                           5662/(squid)    
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           4738/avahi-daemon: 
udp        0      0 0.0.0.0:33785           0.0.0.0:*                           4738/avahi-daemon: 
udp6       0      0 :::53                   :::*                                4764/named      
udp6       0      0 :::54877                :::*                                4764/named      
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     15104    4884/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     16740    5370/winbindd       /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     17756    5652/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18395    5974/gnome-keyring- /tmp/keyring-mmaleT/socket
unix  2      [ ACC ]     STREAM     LISTENING     18401    5974/gnome-keyring- /tmp/keyring-mmaleT/ssh
unix  2      [ ACC ]     STREAM     LISTENING     18407    5974/gnome-keyring- /tmp/keyring-mmaleT/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     18650    6047/seahorse-agent /tmp/seahorse-8OvG1S/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     18680    5985/x-session-mana /tmp/.ICE-unix/5985
unix  2      [ ACC ]     STREAM     LISTENING     18694    6050/gconfd-2       /tmp/orbit-bosslady/linc-17a2-0-d5e8c35939e3
unix  2      [ ACC ]     STREAM     LISTENING     18944    5985/x-session-mana /tmp/orbit-bosslady/linc-1761-0-7cfc3514b96f2
unix  2      [ ACC ]     STREAM     LISTENING     19087    6056/gnome-settings /tmp/orbit-bosslady/linc-17a8-0-75082b9ee2e15
unix  2      [ ACC ]     STREAM     LISTENING     19173    6057/metacity       /tmp/orbit-bosslady/linc-17a9-0-55b1696040cbf
unix  2      [ ACC ]     STREAM     LISTENING     14878    4738/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     19743    6080/gnome-panel    /tmp/orbit-bosslady/linc-17c0-0-275bdbe0af495
unix  2      [ ACC ]     STREAM     LISTENING     17695    5632/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     18622    6041/dbus-daemon    @/tmp/dbus-TaJZ3sx5s1
unix  2      [ ACC ]     STREAM     LISTENING     21046    6047/seahorse-agent /tmp/orbit-bosslady/linc-179f-0-773a1c1fdbf73
unix  2      [ ACC ]     STREAM     LISTENING     26197    6085/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     26201    6085/pulseaudio     /tmp/pulse-bosslady/native
unix  2      [ ACC ]     STREAM     LISTENING     26242    6102/gconf-helper   /tmp/orbit-bosslady/linc-17d6-0-512fd552ad7ef
unix  2      [ ACC ]     STREAM     LISTENING     26337    6090/bonobo-activat /tmp/orbit-bosslady/linc-17ca-0-775f601d88586
unix  2      [ ACC ]     STREAM     LISTENING     26404    6124/gnome-screensa /tmp/orbit-bosslady/linc-17e1-0-6253d97275c5a
unix  2      [ ACC ]     STREAM     LISTENING     26575    6134/mixer_applet2  /tmp/orbit-bosslady/linc-17f6-0-19e04c27a4713
unix  2      [ ACC ]     STREAM     LISTENING     26682    6146/fast-user-swit /tmp/orbit-bosslady/linc-1802-0-65a4c14c63e0
unix  2      [ ACC ]     STREAM     LISTENING     27369    6207/bluetooth-appl /tmp/orbit-bosslady/linc-183f-0-25f227bac1a0f
unix  2      [ ACC ]     STREAM     LISTENING     27453    6213/gnome-power-ma /tmp/orbit-bosslady/linc-183c-0-6ea549c1da4e9
unix  2      [ ACC ]     STREAM     LISTENING     27484    6198/nm-applet      /tmp/orbit-bosslady/linc-1836-0-3155e1adf08be
unix  2      [ ACC ]     STREAM     LISTENING     27536    6196/evolution-alar /tmp/orbit-bosslady/linc-1834-0-64f40be863a5a
unix  2      [ ACC ]     STREAM     LISTENING     27513    6210/update-notifie /tmp/orbit-bosslady/linc-1842-0-18f4c918a4036
unix  2      [ ACC ]     STREAM     LISTENING     27634    6231/evolution-data /tmp/orbit-bosslady/linc-1857-0-131145f7221f
unix  2      [ ACC ]     STREAM     LISTENING     27752    6238/evolution-exch /tmp/orbit-bosslady/linc-185e-0-6e3d60b2da657
unix  2      [ ACC ]     STREAM     LISTENING     29195    6406/notification-d /tmp/orbit-bosslady/linc-1906-0-10c02fbb89034
unix  2      [ ACC ]     STREAM     LISTENING     166246   20838/firefox       /tmp/orbit-bosslady/linc-5166-0-9981e44f1efc
unix  2      [ ACC ]     STREAM     LISTENING     82106    13815/mono          /tmp/orbit-bosslady/linc-35f7-0-4da6e9c17913
unix  2      [ ACC ]     STREAM     LISTENING     17513    5549/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     206310   23758/gnome-termina /tmp/orbit-bosslady/linc-5cce-0-7ca1b942b23cd
unix  2      [ ACC ]     STREAM     LISTENING     174095   21387/nautilus      /tmp/orbit-bosslady/linc-538b-0-6dca80dca9857
unix  2      [ ACC ]     STREAM     LISTENING     17755    5652/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17509    5549/bluetoothd     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     16742    5370/winbindd       /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     16808    5401/hald           @/var/run/hald/dbus-l47cksY1Dk
unix  2      [ ACC ]     STREAM     LISTENING     90999    5301/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     16795    5383/dovecot        /var/run/dovecot/dict-server
unix  2      [ ACC ]     STREAM     LISTENING     16797    5383/dovecot        /var/run/dovecot/login/default
unix  2      [ ACC ]     STREAM     LISTENING     16802    5383/dovecot        /var/run/dovecot/auth-worker.5400
unix  2      [ ACC ]     STREAM     LISTENING     16835    5401/hald           @/var/run/hald/dbus-uSVwX0pAku
unix  2      [ ACC ]     STREAM     LISTENING     16070    4969/postgres       /var/run/postgresql/.s.PGSQL.5432
unix  2      [ ACC ]     STREAM     LISTENING     14545    4524/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     14834    4718/dbus-daemon    /var/run/dbus/system_bus_socket
root@ubuntu:~# 

what is dovecot and keyring and all that..

---

### Post by Bachstelze on 2010-04-15
You have a Perl script listening on port 10000. Any idea as to what it could be?

Dovecot is a POP/IMAP server. If you didn't install it yourself, you have a big reason to worry, it means someone got root on your server.

---

### Post by Lakeside5 on 2010-04-15
OMG  and THAT'S why I can't see my website or get mylocalhost...I did a dumb thing, at some point I decided to go against my better judgement and do the 'sudo -i' thing so I could change permissions on a bunch of files/folders when building my website and somehow it must have not got changed back...when I woke this morning there was a 'gimp graphics' file open and some drawing started, and I had never done that,  and I live alone, freaky!  What do I do??!!!!  Should I shut my computer off, I don't want people using my computer!

---

### Post by Lakeside5 on 2010-04-15
...I'm still a newbie actually, don't spend much time with this even tho I have an older join date, so I have no idea how bad this is.  How do I uninstall that, can I find out what 'damage' they've done with it etc.

---

### Post by Bachstelze on 2010-04-16
If your machine was compromised, the only thing to do is a reinstall. There's so many things the attacker could have done, you can't investigate them all.

---

### Post by Linuxforall on 2010-04-16
Did you enable apparmor btw?

---

### Post by cdenley on 2010-04-16
You have a lot of services listening for remote connections. If they aren't filtered and aren't secured (security updates, strong passwords, configured correctly), then you could have been compromised. Something being done on your local desktop usually indicates someone connecting to a VNC server, but I don't see any VNC processes. Did you enable "remote desktop" before? It is also possible that someone gained local access via ssh, webmin, or some server exploit to start their own vnc server, but I would expect something a little more subtle.

---

