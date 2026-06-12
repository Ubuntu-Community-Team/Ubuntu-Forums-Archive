---
title: "Redundant servers - Simplest way?"
date: 2012-11-18
forum: Server Platforms
---

### Post by flycast on 2012-11-18
I have been learning and experimenting with Ubuntu server. I am curious about a couple of things regarding redundant samba fileservers and redundant IMAP email.

I have three physical locations on a vLan (let's say ...LA, NY, Paris) and need to have a Samba fileserver at each one. Ideally I want the files on each server to be mirrored on the other two servers so that all three locations would have all files. The files are quite large and the bandwidth is limited between locations. Usually the users at one location do not need files from the other two locations until the next day. We want fileservers at each location so the bandwidth does not slow down their daily work. The users in LA would get their files from LA server, etc. I have some experience running a Ubuntu/Samba server using Webmin.

I would also be interested in running a mail server for POP3 and IMAP with on two machines at one location only. One machine would be the primary server. If a failure happened then the service would come from the secondary machine until the primary could be restored. All locations would get mail from this one location.

What would be the simplest way to accomplish these two tasks? What should I look at?

---

### Post by madverb on 2012-11-18
That would be a bit of a complicated setup in terms of the file server. You can set up mirrors of the data so that it is updated instantly but if bandwidth is an issue that's not going to work.
Since they won't be accessing the data a lot from each site I would just have a file server at each site and make the other file servers accessible over the WAN.
With email servers I would be looking at something like Zimbra [http://www.zimbra.com/](http://www.zimbra.com/)

---

### Post by SeijiSensei on 2012-11-20
If the files do not have be replicated in real time, then I'd just run an rsync job to copy the files.  Finding the right time of day to do this is a bit complicated since you'll have machines in UTC+1, UTC-5, and UTC-8 timezones.  But moving files from Paris at 4 am to NY at 10 pm might not cause bandwidth issues in NY depending on how your organization's workflow is distributed over the day.

For email, replication is more difficult.  There is no easy way to synchronize users' mail folders in real-time.  The best you can do is use rsync periodically to copy /var/spool/mail and /home from the primary to the backup.  You also have the problem if the primary dies of where new incoming messages should go.  If you make your secondary also the secondary MX, then messages it receives during an outage on the primary will no longer appear on the primary when it is brought back into service.

Personally I don't bother with any of this.  If the mail server goes down, people just have to wait for mail until it is fixed.  If you really want bullet-proof performance, invest in some expensive server hardware with hardware RAID and redundant power supplies.  Most of my servers run unattended for months or even years at a time without needing service.

---

