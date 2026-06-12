---
title: "Sguil IDS: Installation notes"
date: 2007-06-24
forum: Server Platforms
---

### Post by Ufo on 2007-06-24
I used Ubuntu Dapper server edition for creating Sguil IDS (intrusion detection system). I could not find instructions for installing sguil on Ubuntu or Debian, so I thought I could share my installation notes here. Maybe they could help somebody who is deploying similar system.

This is for Sguil 0.6.1.  Sguil homepage is [http://sguil.sourceforge.net/]("http://sguil.sourceforge.net/")

---

### Post by Ufo on 2007-07-01
One update for installation notes:

 Snort statistics did not show up in client. They get created by snort perfmonitor preprosessor and that was not turned on.

So I edited following line in snort.conf file:
# preprocessor perfmonitor: time 300 file /var/snort/snort.stats pktcnt 10000

to:
preprocessor perfmonitor: time 300 file /nsm/snort_data/raja/snort.stats pktcnt 10000

---

### Post by edward@linpro.no on 2008-02-26
Hi,
I have made some .deb's of squil 0.7.0 and tend to repack them when when 0.7.0 is released stable (qru says it is stable now, just lacks documentation,,,). Tested on Debian Sarge and SID, and on Ubuntu Dapper and Gutsy.

Please help me test more :) to make the packages better!
Input is more than welcome!

My blog about my first release is here : [http://www.gamelinux.org/?p=10]("http://www.gamelinux.org/?p=10")
and you will find my .deb's here :
[http://debs.gamelinux.org/]("http://debs.gamelinux.org/")

Enjoy!

---

