---
title: "All setup; now what?"
date: 2013-04-21
forum: Server Platforms
---

### Post by docJ on 2013-04-21
Hello,
as the title implies, my new computer running Ubuntu 12.04 desktop seem all setup and doing fine (because of the tremendous help I received here so far; thanks to all involved!)
Its role is mainly to act as a media server, so it will be left powered on 24/7
I have automounted its internal data drives, then shared them so they could be accesses from other home network WIndows7 pc's.
I have setup uFW firewall to deny in and out, with only minimal exceptions rules
I have also installed and setup a third party backup application that sends backups to a Network Attached Storage (NAS)

Here is my very first post on the forum from about 2 week ago:
[http://ubuntuforums.org/showthread.php?t=2131730](http://ubuntuforums.org/showthread.php?t=2131730)
The very first reply I got was from an established and respected member ([**[COLOR=#000000]DuckHook[/COLOR]**]("http://ubuntuforums.org/member.php?u=1256508")) warned me about no such thing as a maintenance free server

Soon, this computer will be moved from my cramped, busy, and soon to become very hot home office, to a nice big, quiet and _cool_ basement, and my interactions with it should decrease.
Apart from the occasionnal software updates notifications I get (and act upon), what kind of maintenance routine would be appropriate in my situation, considering all of the above?

 Thanks in advance!
DocJ

---

### Post by wildmanne39 on 2013-04-21
*Thread moved to **Server Platforms**.*

---

### Post by CharlesA on 2013-04-21
Checking SMART Data on drives is a good idea, as is running fsck every now and then (I have mine set to notify me every month).

Otherwise, as long as you are keeping up-to-date, you should be good to go.

---

### Post by docJ on 2013-04-22
> **CharlesA said:**
> running fsck every now and then (I have mine set to notify me every month).

Thanks, but what do you mean exactly by "set to notify"?

---

### Post by CharlesA on 2013-04-22
> **docJ said:**
> Thanks, but what do you mean exactly by "set to notify"?

I changed interval between checks to be every month. I usually run a fsck manually whenever I am doing my monthly backups.

See here:
[http://linux.die.net/man/8/tune2fs](http://linux.die.net/man/8/tune2fs)

-i flag.

---

