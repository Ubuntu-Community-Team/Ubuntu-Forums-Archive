---
title: "Windows machine somehow able to &quot;log on&quot; without ssh or credentials"
date: 2009-10-19
forum: Security
---

### Post by daniel.pool on 2009-10-19
Hi,

I'm duplicating this post as I'd originally put it in the general help area. I think that it pretty much got lost in all the noise there, so I'm hoping that I'll get more of a response here?

----------------------

I wanted to post about a strange issue that I'm having and can't seem to get to the bottom of.

I'm running an Ubuntu minimal build with both mythtv backend and XBMC installed on it. I have a script which is run by myth to make sure that XBMC is idle and that no users are logged on. If this is the case then myth will shut the box down, setting a wake up timer for the next time I want the PVR to come on and record ... all good.

However, recently the HTPC hasn't been shutting down. From the log files my scripts write, I've tracked the reason down as being that my wife's windows vista laptop is showing as logged onto the HTPC. This she's managed to do without having the user credentials or having Putty installed! I'm sure that she isn't that good at hacking ... unless there is a side of here that I really don't know :confused:

```

htpc@htpc:/home/htpc# last | grep -i karla
htpc     pts/0        karlas-laptop.ho Mon Sep 28 18:56 - down   (03:22)
htpc     pts/0        karlas-laptop.ho Mon Sep 28 18:34 - down   (00:20)
htpc     pts/0        karlas-laptop.ho Thu Sep 24 22:47 - down   (00:00)
htpc     pts/0        karlas-laptop.ho Thu Sep 24 18:04 - 22:46  (04:42)

```* Yes, the logs are pretty old. This issue seems to come and go, and I can't seem to find a way to replicate it reliably ... woohoo :)

Thinking about what was installed on the HTPC about the only thing that I thought that could cause this sort of thing would be the UPnP server in myth (though I wouldn't have thought this would show up as a registered user, particularly the htpc user as myth runs under it's own account). I've disabled it anyway. However, as this issue isn't easily replicable, I can't be sure that that will fix it.

If anyone has any pointers or help they could offer in tracking it down that would be awesome. Whilst I'm not a complete n00b at linux, this one is slightly outside of my comfort zone.

Thanks in advance,
~Dan

---

### Post by __p1n__ on 2009-10-19
Perhaps she's watching some movies.

---

### Post by koenn on 2009-10-19
the logged on user is "htpc" - so probably an it's an audio/video player connecting to your service ?

---

### Post by daniel.pool on 2009-10-19
> **__p1n__ said:**
> Perhaps she's watching some movies.

Nah, I don't make any movies available that way. The HTPC box drives our flat screen TV, if we watch any movies we sit down in front of the TV to watch. In the nicest way possible, it would sort of be beyond her to stream movies off the machine anyway.

> **koenn said:**
> the logged on user is "htpc" - so probably an it's an audio/video player connecting to your service ?

I don't think that it's this for the above reason; no a/v players were running at the time. Also there are three users on the box. One general purpose user which I use to maintain the box; the "htpc" account, and then one for xbmc and one for myth. All the services either run under the myth or xbmc user accounts. The fact that the pts/0 is under the htpc credential is more a worry for me than if it had been either the myth or xbmc accounts.

As I mentioned though, it might have been a UPnP connection, but as this service ran under the myth account (it's disabled now) I'd expect to see that as the user credential.

Any other suggestions or hints to track this down?

---

### Post by koenn on 2009-10-19
do these serves keep activity logs, session logs, ...  showing what they serve up, to whom, when, ... ?

---

### Post by daniel.pool on 2009-10-20
As I'm at work at the moment this list is from memory, but these are the services I've installed on the box and how they are run:


[LIST]
[*]XBMC Live - started via init.d script. Runs under XBMC user, does not show up as logged in user when running (I guess due to the live script);
[*]Go Ahead web server - an embedded web server which runs within XBMC to provide UDP event services and an HTTP command listener service.
[*]MythBackend daemon - Runs under the Myth user, does not show up as logged in user when running;
[*]OpenSSH - daemon running as root(?) provides ssh connection for me to manage the box (no desktop manager is installed)
[*]MySQL - daemon running as root
[*]Apache Web Server - installed by myth, used to deliver myth web and the myth:// protocol. Runs under root.
[*]Lirc - daemon running as root - provides IR functionality
[*]Rsync - I have a NAS drive which pulls files off the HTPC to be processed; daemon running as root I beleive.
[/LIST]
*I really should change the identities that most of these services run under, but I am still in the process of building the box and getting it stable.

That's pretty much it. I guess I should run ps to get the proper list when I get a chance. Of those services I guess apache is the only one which logs authenticated sessions. I can't find enough information on Go Ahead to be sure if it'll log anything outside of the XBMC logs.

In terms of usage, I never envisaged using the HTPC box to stream any media to other computers and to my knowledge it doesn't have anything installed that should allow that to happen, it ultimately consumes media from a network NAS. Whilst the machine does make recordings, I will eventually have my rsync service running on the NAS copy from the HTPC HDD to the NAS where it'll be processed overnight and then made available to XBMC via the media files on the NAS.

I've build the HTPC box from scratch using Ubuntu 9.04 Minimal. I then installed the XBMC Live components and then the Mythbackend components to get it operating as desired.

Myth used to make content available via UPnP, but as mentioned before I've disabled this. Bar ssh, I don't know that any of the other services would generate a "user logged on" entry in last ... :confused:

---

### Post by modorf on 2009-10-20
what does netstat give you?
It should give you the port that the laptop is connecting to.
This will give you an idea of which service it is connecting to.

---

### Post by daniel.pool on 2009-10-23
> **modorf said:**
> what does netstat give you?
It should give you the port that the laptop is connecting to.
This will give you an idea of which service it is connecting to.

Sorry that it's taken so long to reply, work has been quite busy recently and I've not had any time to look into this. Unfortunately, I can't seem to reproduce this problem. Booting up my Wife's laptop and trying various things that my wife might do don't seem to produce anything similar (she effectively uses the laptop for surfing the net, writing letters or editing photos). I've also tried actively getting to the HTPC from it (without installing an ssh client of course).

If I can get a situation where the laptop is connecting again, I'll be sure to run netstat. Otherwise, I'm going to ignore the issue for the moment, continue getting the machine working and then work to lock down any unused ports etc. Maybe that'll mop it up.

Oh well, thanks for your help guys.

---

### Post by movieman on 2009-10-23
I think you can configure tcpdump to dump all packets to or from a particular IP address to a file, so you could log things that way and then load the file into wireshark to see what's going on.

Another possibility is that the reverse DNS lookup is confused so it's translating some other IP address into the hostname for your wife's laptop.

---

