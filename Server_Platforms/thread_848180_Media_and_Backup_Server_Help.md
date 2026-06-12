---
title: "Media and Backup Server Help"
date: 2008-07-03
forum: Server Platforms
---

### Post by rupek on 2008-07-03
Right first post, not sure if this is in the right place either, if it is wrong can a moderator move it please.

I am looking at using Ubuntu server for my new server, it will be connected to 2x xbox, 2x osx and 2x vista. Some of the machines are wireless but the server will be hard wired in.

The job i am looking for the server to do is to stream to the machines video and music content. I also am going to be using it to backup files on all of the machines.

The video files are mp4 (h264) and the music is mp3, there will also be some jpegs but they wont need streaming.

I am wondering if it is possible to set it up so that the machines auto backup and "synchronise" on log off or shutdown, i have seen some windows setups like this i am wondering if this is possible for the osx and vista machines on ubuntu.

And if this is possible how would i go about doing incremental backups (daily, weekly, monthly etc)

I am looking for help as i have never tried to configure something like this myself, i have briefly played around in ubuntu so i know some of the basics but have no code knowledge.

And help you guys can give would be much appreciated.

---

### Post by hyper_ch on 2008-07-03
it is possible with rsync....

and on vista with cygwin and rsync....

have a look at my little howto: [http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

---

### Post by rupek on 2008-07-08
Can anyone give any more information on how this would be down with rsync?

and can rsync be set to automatically do this as most of the users on the network wont be 100% computer literate.

---

### Post by windependence on 2008-07-08
You can set up Amanda or Bacula to back up everything on the Windoze and Mac boxes without user interaction. Set up on either one isn't trivial for someone with little Linux experience, but once set up, there would be little if anything you would need to do.

-Tim

---

