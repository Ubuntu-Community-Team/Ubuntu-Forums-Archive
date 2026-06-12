---
title: "Is it possible Snort can miss detecting an interesting packet?"
date: 2006-10-13
forum: Server Platforms
---

### Post by johnnydepp74 on 2006-10-13
Hi Snort gurus,

I was just wondering whether Snort can miss detecting an interesting packet because I ran nmap twice within 10 secs i.e. one immediately after another and snort seems to pickup only packets from first nmap execution, it didn't log the second nmap execution.

I installed barnyard 0.2.0 and snort 2.6, so I ran snort with the following command:

# /usr/local/bin/snort -de -c /etc/snort/snort.conf -i eth0 -l /var/log/snort

where writes to snort.log.<timestamp> file in /var/log/snort/ folder.

I ran barnyard:

# /usr/local/bin/barnyard  -d  /var/log/snort/  -c  /etc/snort/barnyard.conf  -g  /etc/snort/gen-msg.map   -s  /etc/snort/sid-msg.map –f  snort.log  -L /var/log/snort/output  -p  /etc/snort/classification.config

barnyard is writing to /var/log/snort/output/logdump.ids file from the snort.log.<timestamp> file.

I do a ls -l /var/log/snort/
and find that snort.log.<timestamp> filesize only increase once if I ran nmap twice within say 10 secs.

Funny, snort didnt say it dropped any packets, anything I may have missed out?

Thanks.

Rgds
John

---

