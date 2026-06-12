---
title: "I Think I Broke Something"
date: 2022-04-05
forum: Server Platforms
---

### Post by gimpacause on 2022-04-05
Hi Guys I've been using Ubuntu Server (along with MDADM) for several years , my server is not the fastest when it comes to disk read/writes (200 Mb/sec if im luck) its an older Backblaze v2 box (pcie x1 > port multiupliers) I currently have

15x6tb + 15x18tb both in RAID6 configs , the monthly check cripples my IO and brings the server to a complete crawl once a month, to combat this I tried to edit the mdadm cron job to the following

```
#

# Old schedule

#57 0 * * 0 root if [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ]; then /usr/share/mdadm/checkarray --cron --all --idle --quiet; fi

#

# Begin at 04:00AM on 1st of every 3rd month of the year, starting with January -> Small array

#

0 4 1 Jan,Apr,Jul,Oct root if [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ]; then /usr/share/mdadm/checkarray --cron --idle --quiet /dev/md0; fi

#

# Begin at 04:00AM on 15th of every 3rd month of the year, starting with January -> Big array

#

0 4 15 Jan,Apr,Jul,Oct root if [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ]; then /usr/share/mdadm/checkarray --cron --idle --quiet /dev/md1; fi
```



but the past 2 checks (April 1st/15th 2022) did not kick off, I have done some googling and it appears cron is no longer in control of the mdadm checks, how would I go  about getting this to work so i get a quarterly check on my arrays, about 75% of them are backed up, hence the quarterly checks if i lose anything it wouldn't be impossible to get it all back, as its ,


Many thanks

---

### Post by TheFu on 2022-04-05
You can control the speed of the check effort with mdadm so it doesn't interfere (much) with normal use.
I run weekly disk validation tasks, though I only use RAID1 on any disks over 1TB in size and don't have nearly as many disks as your setup.

I use the **checkarray** script from [email]madduck@debian.org[/email] at idle 
```
Valid options are:
 -a|--all       check all assembled arrays (ignores arrays in command line).
 -s|--status    print redundancy check status of devices.
 -x|--cancel    queue a request to cancel a running redundancy check.
** -i|--idle      perform check in a lowest scheduling class (idle)**
 -l|--slow      perform check in a lower-than-standard scheduling class
 -f|--fast      perform check in higher-than-standard scheduling class
 --realtime     perform check in real-time scheduling class (DANGEROUS!)
 -c|--cron      honour AUTOCHECK setting in /etc/default/mdadm.
 -q|--quiet     suppress informational messages
                (use twice to suppress error messages too).
 -h|--help      show this output.
 -V|--version   show version information.

```
I think this is distributed with mdadm.


A little tuning with blockdev --setra ... should help read performance too.  I spent an afternoon testing each drive with different buffer sizes and determined for my disks, that the defaults were much too small. Vastly better performance was achieved with this:
```
/sbin/blockdev --setra 4096 /dev/sd[abcdefg]
```
It runs at boot time. The values were determined by Alexander Peganz's RAID5/6 tuning script back before I switched to RAID1-only. Not all the drives performed better with that value, but simplicity won. The best value on those disks was close, so it wasn't a bad choice. 

YMMV.

Hope this is helpful.

---

### Post by gimpacause on 2022-04-09
thanks for the reply, the issue I have is the controllers are getting saturated and any tuning of block size will be negated by the I/O saturation, one disk can saturate the entire link, due to the port multiplier architecture  5 disks no matter what i do will saturate the link unless i want to wait weeks for each recheck, if i can schedule each one to kick of on a different day of each third month they will complete a lot quicker, the 15x6tb array used to only take 2 days when it was the only array in the system, but since adding the 2nd 15x18 they do their respective checks at the same time , and tank performance down to 25 MB/s hence why I would like to separate the checks to the 1st and 15t h of every third month (once a quarter)

thanks, 

gimpacause

---

