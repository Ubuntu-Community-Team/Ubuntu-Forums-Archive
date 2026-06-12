---
title: "Security Issue ?"
date: 2006-01-10
forum: Server Platforms
---

### Post by kmifflin on 2006-01-10
Hi! I am new to using to using Linux but I like it and want to learn as much as I can.

I ran Nessus against my own ip and it said I was running a web server on my system.

Well, I didn't want to do this so:

1)  How do I stop the services and 

2) I ran a netstat on my computer and came up with the following output:

tmp/orbit-rimsey/linc-1c02-0-305d4e9862908
unix  2      [ ACC ]     STREAM     LISTENING     10402    7172/nautilus       / tmp/orbit-rimsey/linc-1c04-0-305d4e98ec130
unix  2      [ ACC ]     STREAM     LISTENING     10446    7174/update-notifie / tmp/orbit-rimsey/linc-1c06-0-62088784c1b37
unix  2      [ ACC ]     STREAM     LISTENING     10474    7187/trashapplet    / tmp/orbit-rimsey/linc-1c13-0-620887852c3a
unix  2      [ ACC ]     STREAM     LISTENING     10484    7183/gnome-vfs-daem / tmp/orbit-rimsey/linc-1c0f-0-18a943f19a97
unix  2      [ ACC ]     STREAM     LISTENING     10537    7185/wnck-applet    / tmp/orbit-rimsey/linc-1c11-0-4d03729f7e91c
unix  7      [ ]         DGRAM                    7458     6073/syslogd        / dev/log
unix  2      [ ACC ]     STREAM     LISTENING     10598    7176/gnome-cups-ico / tmp/orbit-rimsey/linc-1c08-0-7f924c0c89b89
unix  2      [ ACC ]     STREAM     LISTENING     10622    7201/mapping-daemon / tmp/mapping-rimsey
unix  2      [ ACC ]     STREAM     LISTENING     10653    7180/evolution-alar / tmp/orbit-rimsey/linc-1c0c-0-30276bc537f42
unix  2      [ ACC ]     STREAM     LISTENING     10686    7206/evolution-data / tmp/orbit-rimsey/linc-1c26-0-62709fc418fb0
unix  2      [ ACC ]     STREAM     LISTENING     10710    7208/notification-a / tmp/orbit-rimsey/linc-1c28-0-62709fc4d29a2
unix  2      [ ACC ]     STREAM     LISTENING     10727    7210/mixer_applet2  / tmp/orbit-rimsey/linc-1c2a-0-4c08481414380
unix  2      [ ACC ]     STREAM     LISTENING     10744    7212/clock-applet   / tmp/orbit-rimsey/linc-1c2c-0-4c08481431641
unix  2      [ ACC ]     STREAM     LISTENING     10812    7217/evolution-exch / tmp/orbit-rimsey/linc-1c31-0-7dce2bf8ab8f2
unix  2      [ ACC ]     STREAM     LISTENING     10892    7233/mozilla-bin    / tmp/orbit-rimsey/linc-1c41-0-5937bea437421
unix  2      [ ACC ]     STREAM     LISTENING     12049    7945/gnome-terminal / tmp/orbit-rimsey/linc-1f09-0-5756db9929c7e
unix  2      [ ACC ]     STREAM     LISTENING     7507     6105/dbus-daemon    / var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     9945     7114/dbus-daemon    @ /tmp/dbus-3ai9pTBZEg
unix  2      [ ACC ]     STREAM     LISTENING     9881     7046/sdpd           / var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     10239    7130/gam_server     @ /tmp/fam-rimsey-
unix  2      [ ACC ]     STREAM     LISTENING     7523     6118/hald           @ /tmp/hald-local/dbus-l8xRrItlBL
unix  2      [ ]         DGRAM                    3884     3083/udevd          @ udevd
unix  2      [ ACC ]     STREAM     LISTENING     7433     6058/acpid          / var/run/acpid.socket
unix  2      [ ]         DGRAM                    7524     6118/hald           @ /var/run/hal/hotplug_socket2
unix  3      [ ]         STREAM     CONNECTED     12064    7946/gnome-pty-help
unix  3      [ ]         STREAM     CONNECTED     12063    7945/gnome-terminal
unix  3      [ ]         STREAM     CONNECTED     12061    7121/esd            / tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12060    7945/gnome-terminal
unix  3      [ ]         STREAM     CONNECTED     12056    7945/gnome-terminal / tmp/orbit-rimsey/linc-1f09-0-5756db9929c7e
unix  3      [ ]         STREAM     CONNECTED     12055    7125/bonobo-activat
unix  3      [ ]         STREAM     CONNECTED     12054    7125/bonobo-activat / tmp/orbit-rimsey/linc-1bd5-0-50ef54a4d7067
unix  3      [ ]         STREAM     CONNECTED     12053    7945/gnome-terminal
unix  3      [ ]         STREAM     CONNECTED     12052    7945/gnome-terminal / tmp/orbit-rimsey/linc-1f09-0-5756db9929c7e
unix  3      [ ]         STREAM     CONNECTED     12051    7116/gconfd-2
unix  3      [ ]         STREAM     CONNECTED     12048    7116/gconfd-2       / tmp/orbit-rimsey/linc-1bcc-0-69f8da1d8710c
unix  3      [ ]         STREAM     CONNECTED     12047    7945/gnome-terminal
unix  3      [ ]         STREAM     CONNECTED     12046    7072/x-session-mana / tmp/.ICE-unix/7072
unix  3      [ ]         STREAM     CONNECTED     12045    7945/gnome-terminal
unix  3      [ ]         STREAM     CONNECTED     12041    6597/X              / tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12040    7945/gnome-terminal
unix  3      [ ]         STREAM     CONNECTED     10895    7233/mozilla-bin    / tmp/orbit-rimsey/linc-1c41-0-5937bea437421
unix  3      [ ]         STREAM     CONNECTED     10894    7116/gconfd-2
unix  3      [ ]         STREAM     CONNECTED     10891    7116/gconfd-2       / tmp/orbit-rimsey/linc-1bcc-0-69f8da1d8710c
unix  3      [ ]         STREAM     CONNECTED     10890    7233/mozilla-bin
unix  3      [ ]         STREAM     CONNECTED     10884    6597/X              / tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10883    7233/mozilla-bin
unix  3      [ ]         STREAM     CONNECTED     10826    7180/evolution-alar / tmp/orbit-rimsey/linc-1c0c-0-30276bc537f42
unix  3      [ ]         STREAM     CONNECTED     10825    7206/evolution-data
unix  3      [ ]         STREAM     CONNECTED     10824    7206/evolution-data / tmp/orbit-rimsey/linc-1c26-0-62709fc418fb0
unix  3      [ ]         STREAM     CONNECTED     10823    7180/evolution-alar
unix  3      [ ]         STREAM     CONNECTED     10820    7217/evolution-exch / tmp/orbit-rimsey/linc-1c31-0-7dce2bf8ab8f2
unix  3      [ ]         STREAM     CONNECTED     10819    7125/bonobo-activat
unix  3      [ ]         STREAM     CONNECTED     10818    7125/bonobo-activat / tmp/orbit-rimsey/linc-1bd5-0-50ef54a4d7067
unix  3      [ ]         STREAM     CONNECTED     10817    7217/evolution-exch
unix  3      [ ]         STREAM     CONNECTED     10815    7217/evolution-exch / tmp/orbit-rimsey/linc-1c31-0-7dce2bf8ab8f2
unix  3      [ ]         STREAM     CONNECTED     10814    7116/gconfd-2
unix  3      [ ]         STREAM     CONNECTED     10811    7116/gconfd-2       / tmp/orbit-rimsey/linc-1bcc-0-69f8da1d8710c
unix  3      [ ]         STREAM     CONNECTED     10810    7217/evolution-exch
unix  3      [ ]         STREAM     CONNECTED     10809    7072/x-session-mana / tmp/.ICE-unix/7072
unix  3      [ ]         STREAM     CONNECTED     10808    7217/evolution-exch
unix  3      [ ]         STREAM     CONNECTED     10804    6597/X              / tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10803    7217/evolution-exch
unix  3      [ ]         STREAM     CONNECTED     10799    7121/esd            / tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     10798    7208/notification-a
unix  3      [ ]         STREAM     CONNECTED     10797    7170/gnome-panel    / tmp/orbit-rimsey/linc-1c02-0-305d4e9862908
unix  3      [ ]         STREAM     CONNECTED     10796    7208/notification-a
unix  3      [ ]         STREAM     CONNECTED     10795    7208/notification-a / tmp/orbit-rimsey/linc-1c28-0-62709fc4d29a2
unix  3      [ ]         STREAM     CONNECTED     10794    7170/gnome-panel
unix  3      [ ]         STREAM     CONNECTED     10789    7121/esd            / tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     10788    7210/mixer_applet2
unix  3      [ ]         STREAM     CONNECTED     10784    7206/evolution-data / tmp/orbit-rimsey/linc-1c26-0-62709fc418fb0
unix  3      [ ]         STREAM     CONNECTED     10783    7125/bonobo-activat
unix  3      [ ]         STREAM     CONNECTED     10782    7125/bonobo-activat / tmp/orbit-rimsey/linc-1bd5-0-50ef54a4d7067
unix  3      [ ]         STREAM     CONNECTED     10781    7206/evolution-data
unix  3      [ ]         STREAM     CONNECTED     10778    7170/gnome-panel    / tmp/orbit-rimsey/linc-1c02-0-305d4e9862908
unix  3      [ ]         STREAM     CONNECTED     10777    7210/mixer_applet2
unix  3      [ ]         STREAM     CONNECTED     10776    7210/mixer_applet2  / tmp/orbit-rimsey/linc-1c2a-0-4c08481414380
unix  3      [ ]         STREAM     CONNECTED     10774    7170/gnome-panel
unix  3      [ ]         STREAM     CONNECTED     10763    7121/esd            / tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     10762    7212/clock-applet
unix  3      [ ]         STREAM     CONNECTED     10761    7170/gnome-panel    / tmp/orbit-rimsey/linc-1c02-0-305d4e9862908
unix  3      [ ]         STREAM     CONNECTED     10760    7212/clock-applet
unix  3      [ ]         STREAM     CONNECTED     10759    7212/clock-applet   / tmp/orbit-rimsey/linc-1c2c-0-4c08481431641
unix  3      [ ]         STREAM     CONNECTED     10757    7170/gnome-panel
unix  3      [ ]         STREAM     CONNECTED     10751    7212/clock-applet   / tmp/orbit-rimsey/linc-1c2c-0-4c08481431641
unix  3      [ ]         STREAM     CONNECTED     10750    7125/bonobo-activat
unix  3      [ ]         STREAM     CONNECTED     10749    7125/bonobo-activat / tmp/orbit-rimsey/linc-1bd5-0-50ef54a4d7067
unix  3      [ ]         STREAM     CONNECTED     10748    7212/clock-applet
unix  3      [ ]         STREAM     CONNECTED     10747    7212/clock-applet   / tmp/orbit-rimsey/linc-1c2c-0-4c08481431641
unix  3      [ ]         STREAM     CONNECTED     10746    7116/gconfd-2
unix  3      [ ]         STREAM     CONNECTED     10743    7116/gconfd-2       / tmp/orbit-rimsey/linc-1bcc-0-69f8da1d8710c
unix  3      [ ]         STREAM     CONNECTED     10742    7212/clock-applet
unix  3      [ ]         STREAM     CONNECTED     10738    6597/X              / tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10737    7212/clock-applet
unix  3      [ ]         STREAM     CONNECTED     10734    7210/mixer_applet2  / tmp/orbit-rimsey/linc-1c2a-0-4c08481414380
unix  3      [ ]         STREAM     CONNECTED     10733    7125/bonobo-activat
unix  3      [ ]         STREAM     CONNECTED     10732    7125/bonobo-activat / tmp/orbit-rimsey/linc-1bd5-0-50ef54a4d7067
unix  3      [ ]         STREAM     CONNECTED     10731    7210/mixer_applet2
unix  3      [ ]         STREAM     CONNECTED     10730    7210/mixer_applet2  / tmp/orbit-rimsey/linc-1c2a-0-4c08481414380
unix  3      [ ]         STREAM     CONNECTED     10729    7116/gconfd-2
unix  3      [ ]         STREAM     CONNECTED     10726    7116/gconfd-2       / tmp/orbit-rimsey/linc-1bcc-0-69f8da1d8710c
unix  3      [ ]         STREAM     CONNECTED     10725    7210/mixer_applet2
unix  3      [ ]         STREAM     CONNECTED     10721    6597/X              / tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10720    7210/mixer_applet2
unix  3      [ ]         STREAM     CONNECTED     10717    7208/notification-a / tmp/orbit-rimsey/linc-1c28-0-62709fc4d29a2
unix  3      [ ]         STREAM     CONNECTED     10716    7125/bonobo-activat
unix  3      [ ]         STREAM     CONNECTED     10715    7125/bonobo-activat / tmp/orbit-rimsey/linc-1bd5-0-50ef54a4d7067
unix  3      [ ]         STREAM     CONNECTED     10714    7208/notification-a
unix  3      [ ]         STREAM     CONNECTED     10713    7208/notification-a / tmp/orbit-rimsey/linc-1c28-0-62709fc4d29a2
unix  3      [ ]         STREAM     CONNECTED     10712    7116/gconfd-2
unix  3      [ ]         STREAM     CONNECTED     10709    7116/gconfd-2       / tmp/orbit-rimsey/linc-1bcc-0-69f8da1d8710c
unix  3      [ ]         STREAM     CONNECTED     10708    7208/notification-a
unix  3      [ ]         STREAM     CONNECTED     10704    6597/X              / tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10703    7208/notification-a
unix  3      [ ]         STREAM     CONNECTED     10689    7206/evolution-data / tmp/orbit-rimsey/linc-1c26-0-62709fc418fb0
unix  3      [ ]         STREAM     CONNECTED     10688    7116/gconfd-2
unix  3      [ ]         STREAM     CONNECTED     10685    7116/gconfd-2       / tmp/orbit-rimsey/linc-1bcc-0-69f8da1d8710c
unix  3      [ ]         STREAM     CONNECTED     10684    7206/evolution-data
unix  3      [ ]         STREAM     CONNECTED     10676    7130/gam_server     @ /tmp/fam-rimsey-
unix  3      [ ]         STREAM     CONNECTED     10675    7174/update-notifie
unix  3      [ ]         STREAM     CONNECTED     10674    6105/dbus-daemon    / var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10673    7174/update-notifie
unix  3      [ ]         STREAM     CONNECTED     10664    7180/evolution-alar / tmp/orbit-rimsey/linc-1c0c-0-30276bc537f42
unix  3      [ ]         STREAM     CONNECTED     10663    7125/bonobo-activat
unix  3      [ ]         STREAM     CONNECTED     10662    7125/bonobo-activat / tmp/orbit-rimsey/linc-1bd5-0-50ef54a4d7067
unix  3      [ ]         STREAM     CONNECTED     10661    7180/evolution-alar
unix  3      [ ]         STREAM     CONNECTED     10656    7180/evolution-alar / tmp/orbit-rimsey/linc-1c0c-0-30276bc537f42
unix  3      [ ]         STREAM     CONNECTED     10655    7116/gconfd-2
unix  3      [ ]         STREAM     CONNECTED     10652    7116/gconfd-2       / tmp/orbit-rimsey/linc-1bcc-0-69f8da1d8710c
unix  3      [ ]         STREAM     CONNECTED     10651    7180/evolution-alar
unix  3      [ ]         STREAM     CONNECTED     10650    7072/x-session-mana / tmp/.ICE-unix/7072
unix  3      [ ]         STREAM     CONNECTED     10649    7180/evolution-alar
unix  3      [ ]         STREAM     CONNECTED     10644    6597/X              / tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10643    7180/evolution-alar
unix  3      [ ]         STREAM     CONNECTED     10640    7121/esd            / tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     10639    7172/nautilus
unix  3      [ ]         STREAM     CONNECTED     10631    7130/gam_server     @ /tmp/fam-rimsey-
unix  3      [ ]         STREAM     CONNECTED     10630    7170/gnome-panel
unix  3      [ ]         STREAM     CONNECTED     10626    7201/mapping-daemon / tmp/mapping-rimsey
unix  3      [ ]         STREAM     CONNECTED     10620    7170/gnome-panel    / tmp/orbit-rimsey/linc-1c02-0-305d4e9862908
unix  3      [ ]         STREAM     CONNECTED     10619    7183/gnome-vfs-daem
unix  3      [ ]         STREAM     CONNECTED     10618    7183/gnome-vfs-daem / tmp/orbit-rimsey/linc-1c0f-0-18a943f19a97
unix  3      [ ]         STREAM     CONNECTED     10617    7170/gnome-panel
unix  3      [ ]         STREAM     CONNECTED     10612    7172/nautilus
unix  3      [ ]         STREAM     CONNECTED     10605    7176/gnome-cups-ico / tmp/orbit-rimsey/linc-1c08-0-7f924c0c89b89
unix  3      [ ]         STREAM     CONNECTED     10604    7125/bonobo-activat
unix  3      [ ]         STREAM     CONNECTED     10603    7125/bonobo-activat / tmp/orbit-rimsey/linc-1bd5-0-50ef54a4d7067

While I ran this I wqas connected to the internet.  Can someone help and tell me if this is normal or do I have too many services running ?

---

### Post by drogoh on 2006-01-11
All of that output there is your desktop and a couple of other (mostly) essential daemons, and it's all benign.

To make sure Nessus isn't just being silly, see if httpd shows up when you do ps -ax | grep httpd in a terminal.  If it is running, you can temporarily issue "sudo /etc/init.d/apache2 stop" to kill it, but it will continue to start whenever you boot.

To get rid of Apache altogether, you can remove it via Synaptic or just disable it from booting by issuing this command:

sudo update-rc.d -f apache2 remove

---

