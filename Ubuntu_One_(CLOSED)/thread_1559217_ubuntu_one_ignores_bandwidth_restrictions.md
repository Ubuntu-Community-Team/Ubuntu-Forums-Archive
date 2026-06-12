---
title: "ubuntu one ignores bandwidth restrictions"
date: 2010-08-23
forum: Ubuntu One (CLOSED)
---

### Post by Docaltmed on 2010-08-23
Right now, I have Ubuntu One backing up about 20 GB of data. In the process, it is eating up the available bandwidth. I'm using Ubuntu 10.04.1.

It utterly ignores the bandwidth limits I have set. It also, at varying intervals, eats up all the available CPU, causing other applications to freeze. I have tried deleting the appropriate configuration file, with no change in behavior. 

any other suggestions?

---

### Post by Docaltmed on 2010-08-23
Holy kwap!!! Now it's not only eating all the bandwidth, it's eating all the freakin' CPU!! My laptop has overheated twice in the past 2 hours because of that unholy syncdaemon.

Is there anyway to get this beast under control, or am I going to have to punt it?

---

### Post by ratcheer on 2010-08-24
> **Docaltmed said:**
> 

any other suggestions?

Submit a question on Launchpad?

Tim

---

### Post by Docaltmed on 2010-08-24
> **ratcheer said:**
> Submit a question on Launchpad?

Tim

You're right, I probably should. Usually all that happens is that it gets ignored for a few months and then somebody shows up and says that whatever bug I reported is an upstream problem, and they don't really care.

{yawn}

I'll just go with dropbox. If this were actual FOSS, I'd go the extra mile to help the devs. But I can get the same thing from dropbox for the same price, so I'm just going to remove Ubuntu One, sign up with dropbox, and ask for a refund.

---

### Post by ratcheer on 2010-08-24
Hmmm, sorry. My questions on Launchpad have gotten prompt and useful responses. I have only asked a couple, though.

Also, if you are really sure that your limits aren't being honored, you could report it as a bug, but then you have to try to give them a lot of supporting information.

Tim

---

### Post by Docaltmed on 2010-08-24
> **ratcheer said:**
> Hmmm, sorry. My questions on Launchpad have gotten prompt and useful responses. I have only asked a couple, though.

Also, if you are really sure that your limits aren't being honored, you could report it as a bug, but then you have to try to give them a lot of supporting information.

Tim

Turns out that the larger problem is that the client software eats all of the available CPU, causing overheating and emergency shutdown. Just happened again 5 minutes ago.

This bug has already been reported, but apparently there is some argument as to whether it actually happens in Lucid or is just a Maverick issue.

I would be more than happy to supply logs, etc to help solve the problem, but that has already been done and it remains a problem that has been "fixed" in Lucid. 

As I said before, when we're talking free software, I consider it my responsibility to pitch in where I can to help everything work, and I really don't mind providing any info the developers need, despite the fact that the outcome is less than optimal, from my point of view.

But if I'm paying for the service, as I'm paying for Ubuntu One, I expect the service to be functional. I don't pay a mechanic to change my tires, only to have to put the truck up on the lift and do it myself.

---

### Post by mc4man on 2010-08-24
> Turns out that the larger problem is that the client software eats all of the available CPU, causing overheating and emergency shutdown. Just happened again 5 minutes ago.

I'm mainly using maverick where the cpu use is definitely an issue, though it only affects 1 cpu (core in core2duo, thread in p4 ht),, and only after starting ubuntuone preferences

Actually don't see any issue in lucid (htop shows no significant usage

Anyway i only use the 'free' account for filesharing, as far as "backup", well, don't see ubuntuone being very useful there, at least not something worth paying for.

As a side note - I'd be concerned if my machine couldn't run at 100% cpu usage without overheating, ect. (even more so if it was only 1 core or thread if that's the case for you.

---

### Post by Docaltmed on 2010-08-25
Another day of fighting with the doggone syncdaemon, as it continued to try and steal every resource that wasn't chained down.

So I punted it. sudo apt-get purge.

I feel much better now.

One of these days, Ubuntu One will be a pretty handy tool. Just not yet.

---

### Post by ratcheer on 2010-08-26
You know, I opened a bug on this same problem a week or so ago and, from your original description of the problem, I couldn't tell we were talking about the same problem.

My bug was 620584. They determined that it was a duplicate of an existing bug and attached it to that one, 617041.

Tim

---

### Post by ratcheer on 2010-08-26
I just got an email this morning saying ubuntuone-client release 1.3.90-0 has resolved the problem, at least for one user.

Tim

---

### Post by Docaltmed on 2010-08-26
> **ratcheer said:**
> I just got an email this morning saying ubuntuone-client release 1.3.90-0 has resolved the problem, at least for one user.

Tim

I know my problem recitation was a little sloppy, but it was an evolving thing, and managing the IT stuff is just one of the 6,342 job responsibilities I fill in my little company. It would be about my speed, though, to have the resolution come down the pipe when I've just left the station. 

Ah, well. I'll give it a while to mature, then take a second look at it. In the meantime, I'll just use a hand-carried usb disk for my off-site backups. Not as convenient -- that's the issue I was hoping U1 would resolve -- but as it was, Ubuntu One was making things less convenient, not more.

---

### Post by Docaltmed on 2010-08-26
> **mc4man said:**
> As a side note - I'd be concerned if my machine couldn't run at 100% cpu usage without overheating, ect. (even more so if it was only 1 core or thread if that's the case for you.


Yeah, I normally would, but we're talking one core at 100% and the other running between 65-80% for 30 minutes or more. That's a long time to rev the engine, and I'm not surprised that it choked.

---

### Post by ratcheer on 2010-08-26
> **ratcheer said:**
> I just got an email this morning saying ubuntuone-client release 1.3.90-0 has resolved the problem, at least for one user.

Tim

It fixed it for me, as well.

Tim

---

