---
title: "Ubuntu 9.04 Server with M$ like off-line replication of folders and files"
date: 2009-09-19
forum: Server Platforms
---

### Post by storskogen on 2009-09-19
Can'f find any thread describing what i want, if there is one pleas point me in the right direction to avoid several post about the same thing.

I want my laptop to replicate /home folder to my server when im connected to my local network and when i go from home i want off-line access to my /home and when back home again i want it update the "server-files"

Just like M$ off-line files.


I thinking NFS shares is the way to go but how do i set it up on my laptop. Im connecting to thru wireless network (NetworkManager) and need to logon to be able to connect? One possibility might be to use some command-line configuration to setup the connection to the home network before login in?

Should i set up a domain at home to make it better? (I have a registered domain)

---

### Post by PrivateSNAFU on 2009-09-19
sounds like a network share with a script that uses rsync to make sure both server and home folder on computer are the same.

It would be good if you could write the script so it automatically starts copying the most recent files as soon as it see's the server.

Good luck and keep us informed of your progress.

---

### Post by PrivateSNAFU on 2009-09-19
After writing about rsync I read an article in Linux format about something called Unison which sounds perfect for what you need.  It uses ssh to transfer the files though.

Home page
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

Article about it
[http://www.linuxjournal.com/article/7712](http://www.linuxjournal.com/article/7712)

Hope this helps

---

### Post by storskogen on 2009-09-20
Both setups looks interesting, going to read more about Unison, rsync im using for a backup harddrive so i know that is working too.

PrivateSNAFU: What command should i use to look for the server? A loop with ping until i get a response seems a little to rough :$

---

### Post by ugm6hr on 2009-09-20
You can achieve this, but I do not know how you could run the script on connection to your local network.  It is definitely possible to do this manually each time you connect.

Steps:

1. Create NFS share on server

2. Enable automounting of NFS share: [http://ubuntuforums.org/showthread.php?t=1117131](http://ubuntuforums.org/showthread.php?t=1117131) (you will have to automount outside /home since syncing may create a loop)

3. Run rsync command from script or panel launcher to sync from /home to server share
```
rsync -av /home /server_nfs_mountpoint
```
Use the --delete option if you want to

4. Find some way to run rsync command on each successful connection to specific network (I don't know if this is possible).

---

### Post by PrivateSNAFU on 2009-09-20
What about a cron job that tries to connect, using ssh to your servers local network ip address every 30 min.  If it fails then exits script and wait for next cron.  If succsessfull then run unison or rsync then log succsess to a log.  

I'm not the best at this sort of thing but this might be a better, slightly less dirty way of doing this

---

### Post by scorp123 on 2009-09-20
> **storskogen said:**
>  I want my laptop to replicate /home folder to my server when im connected to my local network and when i go from home i want off-line access to my /home and when back home again i want it update the "server-files"  Sounds like a typical scenario where "iFolder" would be useful.
[http://en.wikipedia.org/wiki/Ifolder](http://en.wikipedia.org/wiki/Ifolder)

There is a guide:
[http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/](http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/)

Pre-made packages for iFolder are available here:
[https://launchpad.net/~weboide/+archive/ifolder](https://launchpad.net/~weboide/+archive/ifolder)

However: I couldn't make it work and I don't have the time to troubleshoot the details and so instead I have settled on Dropbox. It just does what I want and I get to access my files from anywhere I want or need.
[http://www.getdropbox.com](http://www.getdropbox.com)

Other people I know use Wuala:
[http://www.wuala.com/](http://www.wuala.com/)

Another alternative to Dropbox would be e.g. TeamDrive:
[http://www.teamdrive.net](http://www.teamdrive.net)

> **storskogen said:**
>  I thinking NFS shares is the way to go If you really want to run this on your own server then SSH and rsync are all you need. You don't need to bother with NFS or SAMBA. This is of course assuming that both your server and your laptop run Linux?

---

### Post by scorp123 on 2009-09-20
> **PrivateSNAFU said:**
> What about a cron job that tries to connect, using ssh to your servers local network ip address every 30 min.  If it fails then exits script and wait for next cron.

Something like this?

```
#! /bin/bash

while [ 1 ]; do
#
# Replace 192.168.1.2 with the correct IP of the server!
#
	ping -c1 192.168.1.2 > /dev/null
	if [ $? -eq 0 ]
		then
			# Return code was 0
			# So the ping was a success!
			date +"%m-%d-%Y_%H%M%S" >> $HOME/sync-job.log
			echo "Ping succeeded. Starting rsync ..." >> $HOME/sync-job.log
			rsync -alvx username@server:/source /local_target >> $HOME/sync-job.log
		else
			# Return code was not 0!
			# This means ping has failed
			date +"%m-%d-%Y_%H%M%S" >> $HOME/sync-job.log
			echo "Ping failed. Sleeping." >> $HOME/sync-job.log
	fi
		
	# echo Sleeping for 15 minutes ... 
        sleep 15m 1>/dev/null 2>&1
        # echo Retrying ...
done
```

You could put this into a script, e.g. call it "sync-job.sh" ... And then place a reference to it inside $HOME/.xinitrc like this:
```
/path/to/where/you/saved/this/sync-job.sh &
```

If you place this into a cron then make sure you change the script so it really terminates (e.g. remove the "sleep" line and the whole "while" loop!). Because otherwise "cron" will trigger it every few minutes and leave the instance running, thus slowly filling your memory with more and more sleeping instances :D

BTW: The above is just a suggestion that can be used as framework for your own ideas. I take no responsibility for anything you do or don't do with this. Use this script at your own risk ;)

---

