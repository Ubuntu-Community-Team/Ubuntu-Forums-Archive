---
title: "How to tail a windows DHCP Log"
date: 2018-05-21
forum: Server Platforms
---

### Post by kev4n on 2018-05-21
I have a need to tail a windows DHCP log from my ubuntu server. The problem I have run into is that the log is named DhcoSrvLog-<dayOfTheWeek>.log so when I try to tail it I am good for 24 hours and then it stops due to the name change.

I have tried multitail as well.

I haven't been able to figure out a way to tail the log so that it follows the log file. I assume this will take some bash-foo and a cronjob to accomplish this but not sure where to start.  Can anyone point me in a good direction or give me an idea how to accomplish this??

---

### Post by LHammonds on 2018-05-21
What is the purpose of using "tail" to look at the logs?

If you are needing to process a single log file, I suppose you could have a script that looks at that directory for any new files being created and append the contents into a single log file.  It can be tricky with data being streamed to the latest file though.

I could easily see a script grabbing the 2nd to last file created and appending into the single log which will ensure you always get the full log file but would be up to 24 hours stale.

If you want to dump the daily log into the single log file, you would need to analyze both the daily and single log and determine what lines have not been appended before doing an append.

Another possible idea is to output the tail to the single log and have another script watch for the creation of a new log, then kill the tail script and kick off another tail script that will grab the newest daily log and start appending to the single log.

LHammonds

---

