---
title: "Upstart-job for psybnc"
date: 2012-04-24
forum: Server Platforms
---

### Post by tmm_dk on 2012-04-24
Hi there.

Basics first.
Software: Ubuntu-10.04.4 LTS server, with stock kernel, psyBNC compiled from latest source.

Hardware: Synology Diskstation ds710 :)

I have been making myself a small server for various purposes at home.
I've  added some services that I would like to have started at boot, so I  wrote an Upstart-script for the job(s), and the first daemon  (unrealircd) are now running exactly as I want it to. No bells, no  whistles, just running, and it is start- and stopable by "initctl start  ircd".

Now the tricky part... I wrote a job for my psyBNC-daemon, but the darn thing just wont do as told.
So  far I've come up to the conclusion that the environment that upstart  uses isn't the user initiating the executable, but init(8)'s own, hence  the daemon can't find the configfile.
Furthermore, I also would like  to start the daemon as an unprivileged user, not the superuser. Easy,  via the setuid stanza, if only it wasn't upstart 0.6.5 in the  lucid-release.
The installed app, is for the time located in my homedir, as in "/home/$user/psybnc.

I've  messed around with the expect stanza. I've tried to set a PATH via env  and export stanzas. I've tried chdir to the dir of the executable, but  so far I'm on the ground.
I've trawled through the documentation for initctl (upstart), but havent found any clues to what I might be doing wrong yet.

Any input would be appreciated at this point.

Kind regards.
tmm_dk

---

