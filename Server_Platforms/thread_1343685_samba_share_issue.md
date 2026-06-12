---
title: "samba share issue"
date: 2009-12-02
forum: Server Platforms
---

### Post by Fredrik_b on 2009-12-02
Setup

**PC A** 
Ubuntu server 9.10 (lott of crap on tis instllation. will re-install soon and use a barbone instalaltion + vmware server for webserver etc) 
Raid 5 array mounted to /media/storage

Samba.conf

```

# Global Parameters
[global]
workgroup = workgroup
security = SHARE

#[storage]
#path = /media/storage
#guest account = smbuser
#force user = smbuser
#writable = yes
#create mode = 0777


[storage2]
path = /media/storage/
#force user = ad
guest ok = yes
allow host = all
writable = yes
create mask = 0777
directory mask = 0777

```

**Pc B**
JeOS 8.04 on Virtiual machine on pc A)

fstab

```
//192.168.1.105/storage2 /media/storage cifs password=,_netdev 0 0

```

My problem is that users on B can do annyting on the monted share
but rtorrent have no write acces to the share.

why is this?


.rtorrent.rc
```
scgi_port = localhost:5000

# Move completed torrents to /home/rt/torrents/done/
#on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/rt/torrents/done/ ;d.set_directory=/home/rt/torrents/done/"
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Default directory to save the downloaded torrents.
directory =/media/storage/temp/torrent/downloading/


# Move compleate
schedule = watch_directory_1,10,10,"load_start=/media/storage/temp/torrent/load/default/*.torrent,d.set_custom1=/media/storage/downloads/"


# On completion, move the torrent to the directory from custom.

on_finished = move_complete,"d.set_directory=$d.get_custom1= ;execute=mv,-u,$d.get_base_path=,$d.get_custom1="

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

session =/media/storage/temp/torrent/.session

# Port range to use for listening.
#port_range = 6890-6999

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
#use_udp_trackers = yes

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

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
# 
# dht = auto

# UDP port to use for DHT. 
# 
# dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
# peer_exchange = yes

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

```

---

