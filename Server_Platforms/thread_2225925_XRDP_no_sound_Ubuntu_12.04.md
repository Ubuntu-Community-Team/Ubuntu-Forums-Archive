---
title: "XRDP no sound Ubuntu 12.04"
date: 2014-05-24
forum: Server Platforms
---

### Post by jmichal on 2014-05-24
I'm trying to configure XRDP with sound redirection. Server doesn't have any sound card, so it have to be emulated.
After clean installation of Ubuntu and XRDP:
```

[COLOR=#2E8B57][FONT=Monaco]sudo apt-get update [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]sudo apt-get upgrade[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]sudo apt-get install ubuntu-desktop[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]sudo apt-get install xrdp[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]adduser test[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]echo "gnome-session &#8211;session=ubuntu-2d" > /home/test/.xsession[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]sudo /etc/init.d/xrdp restart[/FONT][/COLOR]

```

XRDP is running but without sound. In settings I see only "dummy" sound card.
Acordingly to XRDP sugession I've downloaded xrdp sources and compiled xrdp sink modules:
[http://www.xrdp.org/index.php?option=com_content&view=article&id=19:xrdp-pulse-sink&catid=2:documents&Itemid=7](http://www.xrdp.org/index.php?option=com_content&view=article&id=19:xrdp-pulse-sink&catid=2:documents&Itemid=7)

After connecting to XRDP I see sound card "xrdp sink" but sill there is no sound.
I was trying on 32, 64 bit, and also on Debian and everywhere is the same situation: I can connect but I don't have a sound.

In logs I have only such messages:
```

[COLOR=#2E8B57][FONT=Monaco]cat syslog |grep pulse[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]May 23 10:08:48 pulseaudio[2587]: 1 block_usec 30000[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]May 23 10:08:48 pulseaudio[2587]: sink_process_msg: running[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]May 23 10:09:00 pulseaudio[2587]: sink_process_msg: not running[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]May 23 10:09:00 pulseaudio[2587]: close_send:[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]May 23 10:09:06 pulseaudio[2587]: 1 block_usec 30000[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]May 23 10:23:14 pulseaudio[2587]: sink_process_msg: not running[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]May 23 10:23:14 pulseaudio[2587]: close_send:[/FONT][/COLOR]

```

Do you have any ideas, or some suggestions?

---

