---
title: "rtorrent seeding problem"
date: 2007-10-12
forum: Server Platforms
---

### Post by Falmarri on 2007-10-12
I have no idea where to put this, but it's running on my server so I guess I'll put it here. Thing is, I'm actually running Slackware on my server, but this really shouldn't have anything to do with the distro and I will probably get the most views here.

The problem is that once my torrents are done downloading, they won't seed anymore. While they're downloading they seed correctly. This is normally a problem with port forwards, but my ports are forwarded correctly, so it has to be something else. This is my .rtorrent.rc file. Is there anything else that will prevent seeders from connecting? Not running a firewall on my slack box, and my router's ports are forwarded correctly.

```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
#max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 80

# Default directory to save the downloaded torrents.
directory = /mnt/hda/falmarri/Azureus

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
#session = ./session

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,1,1,load_start=/mnt/hda/torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,stop_on_ratio=200,200M,2000

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
port_range = 16778-16778

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
# encryption = allow_incoming,enable_retry,prefer_plaintext

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10

# Max number of files to keep open simultaniously.
#max_open_files = 128

# Number of sockets to simultaneously keep open.
#max_open_sockets = <no default>


# Example of scheduling commands: Switch between two ip's every 5
# seconds.
#schedule = "ip_tick1,5,10,ip=torretta"
#schedule = "ip_tick2,10,10,ip=lampedusa"

# Remove a scheduled event.
#schedule_remove = "ip_tick1"

```

Thanks, this is really ruining my ratio.

---

### Post by banewman on 2007-10-12
My rtorrent rc file is commented where it says to stop uploads at a certain percent. Maybe you should comment that line and try again. :)

---

### Post by Darkriser on 2007-10-12
I'm using rtorrent and being very happy with it.
These are my advices for you:

1) create a folder (e.g. in your homedir) with name like session (choose any). uncomment and enter the path to your session folder to the following line (i'm using full path instead of relative one):
```
#session = /home/darkriser/session/
```

2) this is the line you're looking for (regarding seeding):
```
schedule = ratio,60,60,stop_on_ratio=200,200M,2000
```
Note: I'm using latest rTorrent (0.7.7) and libTorrent (0.11.7) and had to change the line following when upgraded from previous version (added quoutes):
```
schedule = ratio,60,60,"stop_on_ratio=150,100M,200"
```

3) ideally, uncomment following line and enter your public IP address or domain name (e.g. I'm using dyndns service):
```
#ip = rakshasa.no
```

4) I saw your rtorrent config to be listening on port 16778. Just check if opened on router/iptables (incomming connections for port 16778, TCP protocol must be allowed)

5) that should be enough. just save the config file to ~/.rtorrent.rc and try running rtorrent again.

Regards,
Marcel

---

### Post by codmate on 2007-10-12
How's your iptables set-up?
Try switching off iptables (or any other firewall) and trying again.

This line may also be causing problems:
schedule = ratio,60,60,stop_on_ratio=200,200M,2000

It looks OK - but try commenting it out just to see what happens.

---

