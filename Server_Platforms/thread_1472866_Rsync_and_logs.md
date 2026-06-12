---
title: "Rsync and logs"
date: 2010-05-04
forum: Server Platforms
---

### Post by kgatan on 2010-05-04
Hi,

Im have some issues with logs for rsync and hope someone can point me in the right direction or suggest other ways of doing it.

Im running ubuntu 9.10 on both machines.

**Setup**,
We take daily backups at my work so instead of setting up backups at home i rsync my www root and mysqldump to the work linux machine.
I have made a script with mailx that send the log from the rsync as confirmation that the backup has run as scheduled.
rsync is done over SSH using command as below:
rsync --delete -zvr -e ssh --log-file=<path> /source /target

The problem is the logs i receive are for all the files synchronized which means a log each time of 1mb which means i have to zip it as well and cant read it from a mobile device.

So my question is if its possible to get a smaller summerised log of the rsync operation?


**Unstable network,**
We have a small office in china which is in need of synchronzation of some files from our head office and i thought of using a linux fileserver there with rsync.

Since its in china im worried regarding the stability of the connection, some times its no problem at all but from time to time its just a pain in the *** china-europe.

How does rsync behave if the connection goes down during synch? Is there any options for auto resume? Scripts?

I tried googling the problem but no result so far.

Again, other options are welcomed.


BR Ola

---

### Post by richardjh on 2010-05-04
You're running the command 

rsync --delete -zvr -e ssh --log-file=<path> /source /target

The v in -zvr means verbose, remove it and you will just get a summary.


If the network goes down during an rsync, rsync stops.
As far as I know, you cannot get rsync to continue from this. However you could write a wrapper around the script that checks for successful completion of the rsync command and if it is not successful, waits for a bit and then tries to start the rsync again. 

If the rsync was mostly done, restarting it from the beginning will still result in only what is left to synchronise being copied across the network.

---

### Post by kgatan on 2010-05-04
Thanks for the reply!

I tried removing the v but it still generates a file list in the log which is at the moment like 12000 rows.

Could it be viable to make a bash script to analyze the log for errors and react accordingly?

---

