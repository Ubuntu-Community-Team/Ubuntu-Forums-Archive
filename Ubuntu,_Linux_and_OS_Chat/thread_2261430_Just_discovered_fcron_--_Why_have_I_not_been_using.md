---
title: "Just discovered fcron -- Why have I not been using fcron all these years???"
date: 2015-01-19
forum: Ubuntu, Linux and OS Chat
---

### Post by kevdog on 2015-01-19
OK I feel stupid, but I recently discovered a few things and found some new packages.  logrotate is a great package that will once a day rotate various logs, compress them, etc.  I found this to be extremely useful in backing up the rsync logs I do nightly from my various laptops to my server.

In the process of trying to automate all these backup scripts (obnam --- hmmm still testing this one -- much potential but for now my main stay is just plain rsync), I noticed my scripts were not being ran at 3am like they were scheduled on the cron daemon on the various laptops.  Laptops that would appropriately power save -- ie MacBookPro -- the script woudn't run -- and dont even get me started with how personally awful I think Apple's implementation of their scheduler is.  I started reading and found that this problem with missing runs of a script -- particularly from sources like laptops that are not consistently up or hard wired -- is a problem for many.  Numerous information and suggestions have been written on the topic of asynchronous job processing.  Vixie-cron (I believe the default cron daemon -- does not support asynchronous job processing -- meaning if the computer was down when the time for the job was to run, the job will be skipped and hopefully the computer is backup and running when the next interval is specified).  Other cron implementations for this purpose have been written - cronie, anacron, cronwhip, dcron, and fcron. I've tried cronie along with anacron in the past, however I was still getting lost runs.  It was probably my setup, however I could never understand why.

Over the weekend I installed and tested fcron.  Wow was I impressed.  The options that are available are fantastic.  I'm running the fcron daemon along side the cron daemon currently (I believe the default cron implementation is vixie-cron), however I may in time just use fcron as the default drop in replacement for vixie-cron with anacron run on top.  I very suprised that fcron isn't in the standard Ubuntu repositories, yet there is a man page for fcron that specifically states 14.04, 14.10.  This cron implementation would seem a very worthy addition into the standard repositories.  This would seem to be a great cron implementation for laptops and such.

---

