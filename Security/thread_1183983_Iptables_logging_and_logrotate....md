---
title: "Iptables logging and logrotate..."
date: 2009-06-10
forum: Security
---

### Post by sp00ki on 2009-06-10
I just added an Ubuntu system to a network whose traffic i'm not 100% familiar with, and wanted to spend some time logging iptables rules to become conversant with the traffic the network sees on a regular basis.

Since the network is a gigabit one, any extraordinarily chatty traffic (whether valid or an attack) leaves me with a potentially cumbersome logfile which i'd like to avoid if possible (since i want to know most of what's touching my interface, i'm setting the log level to 4).
At the same time, i'd like to separate the logs by day for easy parsing.

So far, the best way i've found to handle this is to:
1) log iptables to a unique location (i'm using /var/log/iptables/iptables.log)
2) configure logrotate with [FONT="Fixedsys"][COLOR="DimGray"]daily[/COLOR][/FONT] and [FONT="Fixedsys"][COLOR="DimGray"]dateext[/COLOR][/FONT] which starts a new log each day (and names old logs by date), and
3) add a second logrotate script to cron.hourly with the [FONT="Fixedsys"][COLOR="DimGray"]size[/COLOR][/FONT] or [FONT="Fixedsys"][COLOR="DimGray"]minsize[/COLOR][/FONT] option to limit the logfile's growth.

My concern with this is that any logfiles which exceed the specified "size" threshold will be rotated, altering the filename format the daily logrotate looks at for normal rotation, or that using dateext in conjunction with size would cause the file to overwrite itself every time the filesize exceeds the limit (or that too much logic could end up interfering with iptables logging or etc or etc).
I could use the date command and if/then logic to add a "seconds" field to any new file created because of size, but i'd like to use standard logrotate options if possible.

I guess what i'm looking for is a "best practices" way to rotate iptables logs if a large filesize is encountered (and for logrotate to check more frequently than daily), but to rotate daily with dateext naming if normal filesizes are encountered.

*ed:  and before anyone says it, i've already configured syslog to write iptables events to the aforementioned path and have configured logrotate for daily rotating.  my question pertains only to adding "size" or "minsize" (or similar) support to the mix; everything else is covered.*

---

