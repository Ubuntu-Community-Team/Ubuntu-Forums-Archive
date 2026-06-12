---
title: "flexget always return accepted 0"
date: 2013-09-16
forum: Server Platforms
---

### Post by geuli on 2013-09-16
Hi,
I have install flexget and can't find any torrents with it.
Can you please tell me what i'm doing wrong?
Here is the config file from /var/lib/deluge/.flexget/config.yml:
presets:
tv:
series:
settings:
720p:
quality: hdtv

720p:
- Dexter
- Broadwalk Empire

deluge:
path: /mnt/nas/BitTorrent/tmp/
user: deluge
pass: deluge

tasks:
EZRSS:
preset: tv
rss: [http://www.ezrss.it/feed/](http://www.ezrss.it/feed/)

here is the command line:

geuli_admin@MediaServer:~$ sudo -H -u deluge flexget --test -v


and the output:

2013-09-16 06:40 INFO     manager                       Test mode, creating a copy from database ...
2013-09-16 06:40 INFO     manager                       Test database created
2013-09-16 06:40 INFO     deluge                        Using deluge 1.2 api
2013-09-16 06:40 VERBOSE  details       EZRSS           Produced 30 entries.
2013-09-16 06:40 VERBOSE  details       EZRSS           Summary - Accepted: 0 (Rejected: 0 Undecided: 30 Failed: 0)
2013-09-16 06:40 INFO     deluge        EZRSS           Connecting to daemon at localhost:58846..
2013-09-16 06:40 INFO     deluge        EZRSS           Connected to daemon at 127.0.0.1:58846..
2013-09-16 06:40 INFO     deluge        EZRSS           Connection lost to daemon at localhost:58846 reason: Connection was closed cleanly.
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `The Newsroom 2012 2x9 [HDTV - REPACK - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Aqua Teen Hunger Force 10x5 [HDTV - EVOLVE]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Devious Maids 1x12 [HDTV - EVOLVE]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Low Winter Sun US 1x6 [HDTV - ASAP]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Copper 2x12 [HDTV - EVOLVE]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `The Newsroom 2012 2x9 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Breaking Bad 5x14 [720P - HDTV - IMMERSE]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Ray Donovan 1x11 [HDTV - ASAP]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `The X Factor US 3x2 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Americas Next Top Model 20x8 [HDTV - BAJSKORV]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Americas Got Talent 8x25 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Americas Got Talent 8x24 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Anthony Bourdain Parts Unknown 2x1 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Breaking Bad 5x14 [HDTV - ASAP]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Boardwalk Empire 4x2 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Real Time with Bill Maher 2013-09-13 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Cedar Cove 1x8 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Dont Trust The Bitch In Apartment 23 - Monday June 2x13 [HDTV - FOV]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Big School 1x5 [HDTV - FOV]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Peaky Blinders 1x1 [HDTV - REPACK - TLA]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Chickens 1x4 [HDTV - TLA]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `QI 11x2 [HDTV - FTP]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Hot in Cleveland 4x24 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Graceland 1x12 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Rookie Blue 4x13 [HDTV - ASAP]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `The Colbert Report - Philip Mudd 2013-09-12 [HDTV - LMAO]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `The Colbert Report - Sheryl Crow 2013-09-11 [HDTV - 2HD]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `Camp 1x10 [HDTV - LOL]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `The Daily Show - Billy Crystal 2013-09-12 [HDTV - LMAO]`
2013-09-16 06:40 VERBOSE  verbose       EZRSS           UNDECIDED: `A&E The Real Godfathers - The Gambinos 1x4`
2013-09-16 06:40 INFO     verbose       EZRSS           Undecided entries have not been accepted or rejected. If you expected these to reach output, you must set up                                 filter plugin(s) to accept them.
2013-09-16 06:40 INFO     manager                       Removed test database
 
appreciate your help :-)

---

