---
title: "Decentralized Sync"
date: 2012-05-20
forum: The Cafe
---

### Post by sandyd on 2012-05-20
Currently, a lot of people use Ubuntu One to sync their documents, pictures, .etc .etc between computers

This is a highly inefficient way of syncing files across computers, as it follows the path

Computer 1 -> (uploads changed file to Ubuntu One) -> (Notices changes and downloads) -> Computer 2

Unnecessary space, bandwidth, and other resources on Ubuntu One are wasted, and the process is slow and inefficient.

Instead, we should have a method to allow direct computer-to-computer sync through something similar to a p2p network. Sort of like Windows Live Mesh.

Support and check out the current ideas at

[[IMG]http://brainstorm.ubuntu.com/idea/29743/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/29743/)

---

### Post by juancarlospaco on 2012-05-21
I have seen this feature on the long-roadmap somewhere, i dunno what happened, but i think they got take over by Mobile features request.

---

### Post by rai4shu2 on 2012-05-21
I think that idea might have transformed into [Landscape]("https://landscape.canonical.com/").

---

### Post by sandyd on 2012-07-23
bump

---

### Post by CharlesA on 2012-07-23
> **rai4shu2 said:**
> I think that idea might have transformed into [Landscape]("https://landscape.canonical.com/").
Nah Landscape is just monitoring and remote access, not exactly syncing different machines/devices.

+1 to the idea.

---

### Post by juancarlospaco on 2012-07-23
The client is Libre, and it suppose to be a client to client mesh-y thing, 
so we can do it.

---

### Post by sffvba[e0rt on 2012-07-24
One benefit of the way Dropbox and U1 works currently is an off-line backup of files (which also makes access from a system not synced easy via the web).


But more choice is always welcome :)



404

---

### Post by HermanAB on 2012-07-24
Dropbox also does sync on LAN.

---

### Post by sandyd on 2012-07-24
> **HermanAB said:**
> Dropbox also does sync on LAN.
Dropbox is limited to 2G + the number of invites you get.

---

### Post by Paddy Landau on 2012-07-24
As already mentioned, Dropbox does as you suggest (and backs up to the cloud).

A Brainstorm has been raised to suggest doing the same thing with Ubuntu One.

---

### Post by ssam on 2012-07-25
There is conduit. had great potential, but each time I tried to use it I would hit some awkward problem (for example it could not sync a file with a '#' in its filename) [https://live.gnome.org/Conduit/](https://live.gnome.org/Conduit/)

would be great if someone would pick it up and finish it.

and also there is [http://www.syncany.org/](http://www.syncany.org/)

---

### Post by Paddy Landau on 2012-07-25
@ssam: I don't know why, but your post made me think about [rsync]("apt:rsync").

Although it is not user-friendly (no GUI, and you will probably have to write a script), rsync combined with [incron]("apt:incron") can do exactly what the OP wants.

---

### Post by ssam on 2012-07-25
incron is very interesting, i had not heard of that. thanks

there is the grsync GUI front end to rsync.

the trouble with rsync is that it requires you to think in terms of explicit pushes and pulls. the ideal tool would work in terms of syncs between 2 places, figure out what has changed, and if there are any conflicting changes. find a way to resolve the changes and do the necessary transfers.

---

### Post by Paddy Landau on 2012-07-25
> **ssam said:**
> the trouble with rsync is that it requires you to think in terms of explicit pushes and pulls.
Indeed, because a tool does not already exist to do that (unless you want to use Dropbox, SpiderOak, Ubuntu One, etc.).

The process flow would be simple. On each machine:

[LIST]
[*]Start incron for the folders in question.
[*]Each time there is a change, call a script. That script will...
[*]Connect to the remote machine.
[*]Use rsync to connect to the remote machine's rsync daemon and push updates.
[/LIST]
As both machines are doing this, you do not have to think of pull, only of push. The script should be very simple provided that you set up your SSH correctly beforehand.

The only complication is to prevent race conditions between the two machines, so some kind of set-up to prevent a script running twice at the same time, or at the same time as the remote machine is running.

Alternatively, if immediate response is not required, forget about incron. Instead, set up only the one machine to run rsync, and call it for both push and pull every (say) five minutes.

---

### Post by ssam on 2012-07-25
looks like the way to stop races is to wrap your rsync command with flock
[http://serverfault.com/questions/82857/prevent-duplicate-cron-jobs-running](http://serverfault.com/questions/82857/prevent-duplicate-cron-jobs-running)
though I am not sure what would happen if both computers try to push to each other at the same time.

you would also want to queue up changes when you are offline, or online but not on your LAN, or one of the machines is off.

It looks to me like conduit and syncany both wrote their own sync mechanism. I'd guess that it could be more efficient than having rsync scan the whole at both ends directory on every change.

---

### Post by Paddy Landau on 2012-07-25
Thanks for pointing out flock. I had not known about it.

> **ssam said:**
> ... it could be more efficient than having rsync scan the whole at both ends directory on every change.
If you use incron, there is no scanning except when you first start it up. incron uses the inotify system calls, which notices whenever a file is created, deleted or modified.

---

### Post by ssam on 2012-07-25
yes, but if incron calls rsync, then rsync has to scan everything to see what needs to be transferred. unless you can pass through the name of the file that is changed only run rsync on the single file, in which case you could probably just use scp.

---

### Post by Paddy Landau on 2012-07-25
> **ssam said:**
> yes, but if incron calls rsync, then rsync has to scan everything to see what needs to be transferred. unless you can pass through the name of the file that is changed only run rsync on the single file, in which case you could probably just use scp.
Of course, I had forgotten about that. :oops:

In that case, forget about incron. The best way would be to write a script to use inotify directly and, as you say, call rsync with just the changed files or folders. It is not difficult to do the actual process, but the method of validating the input (from the user, i.e. which folders to watch) adds complexity.

There would also have to be an initial scanning when the computers first connect. :(

Hmm... It becomes more complex. How does Ubuntu One scan for changes when it starts up? Perhaps it monitors Zeigeist directly? That would be the most efficient solution of all!

---

