---
title: "nautilus nfs bug? high network load"
date: 2008-03-05
forum: Server Platforms
---

### Post by mbradlcu on 2008-03-05
Hi folks,
I'm not sure were to post this but here's a start,
The lab I'm running Ubuntu 7.10 with home dirs automounted to a Ubuntu nfs server. The strange issue is that sometimes when folks (cleanly) log off, a nautilus process with their users ID continues to run with a very heavy network load (as seen with tcpdump and ntop on the nfs server)
Any suggestions why or what info would be helpful to diagnose this further would be great!,, this issue brings all nfs dependent systems to a crawl.
thanks in advance!
Matt

---

### Post by notwen on 2008-03-05
Are they un-mounting said nfs share before logging off or just logging off?  I'm not quite understanding when you say:
> with home dirs automounted to a Ubuntu nfs server
I mount media shares over my network using nfs to stream audio/video to my laptop and have noticed additional processes running if my laptop disconnects from said server w/o un-mounting the nfs drive first.  I manually check for this zombie processes here and there and kill them should I find any.  Maybe you could setup a cron job to check if said process was active or not and if not kill it?  I'm not familiar enough w/ cron to know it's abilities.  Best of luck w/ your issue.  =]

---

### Post by mbradlcu on 2008-03-05
thanks for the reply,
great question, the users are using the gnome gui to logout. automount keeps their ~/ directory mounted, I would think gdm would kill off any gui process that was active under their gdm session but it's not.
Unfortunately it's very intermittent and I'm not able to reproduce the issue at will.
I just logged on and off a machine several times with a few different accounts, the ~/ dirs are still mounted but with no nfs traffic.

---

### Post by notwen on 2008-03-05
I recall someone requesting a script to be ran before logging off GNOME.  They had wanted it to be built into the shutdown/restart/log off prompt prior to clicking the 'shutdown' button.  I'm wondering if you could have a script un-mount said nfs share prior to the shutdown/restart/log off.  It may be possible to run the NFS client as a daemon, that way it would get properly shutdown during shutdown/restart/log off.  Just some ideas.

---EDIT---
Maybe this [thread]("http://ubuntuforums.org/showthread.php?t=120526") will be of use.  Basically create a script un-mounting the user's nfs share and add it to /etc/gdm/PostSession .  Try this out and let me know the results.  =]

---

### Post by mbradlcu on 2008-03-05
thanks, that is a great suggestion!, I'd still like to find out why the nautilus process is going rouge,,, but until then I'll modify the gdm logoff process.
thanks!

---

