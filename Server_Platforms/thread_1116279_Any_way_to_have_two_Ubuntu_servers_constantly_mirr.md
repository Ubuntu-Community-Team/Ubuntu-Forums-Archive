---
title: "Any way to have two Ubuntu servers constantly mirror each other?"
date: 2009-04-04
forum: Server Platforms
---

### Post by jamieh on 2009-04-04
Just in case one craps out for any reason. Can this be done easily? Same hardware and same LAN.

---

### Post by HermanAB on 2009-04-04
The simplest way is a daily rsync cron job.  Read the rsync man page for details - very easy - rsync is a better kind of copy.

The most complex way is with the Linux High Availability project.  Some Googling will find it.

---

### Post by BkkBonanza on 2009-04-05
Why daily? I'd do it more often then that if you're worried about failure. Maybe hourly or every 10 minutes. You decide how much time you care to lose upon failure. Also you may do it less often but then for mysql data (if you have sites using mysql) setup replication. It's quite easy to config and it will keep you mere seconds behind for often changing mysql data.

Just ask if you need more details. Both these things are fairly easy.

---

### Post by hyper_ch on 2009-04-05
there is mysql replication that replicates mysql data virtually on the fly. If your server is driven by databases then once a day rsyncing the rest should be sufficient.

---

### Post by jamieh on 2009-04-05
Thanks guys
I'll have a look and get back to you.

---

