---
title: "Hourly Reboots...Sometimes"
date: 2008-01-20
forum: Server Platforms
---

### Post by digital9ja on 2008-01-20
What could be the cause of hourly boots other than cron? I have a server that occasionally goes into a cycle where it reboots every hour, but there's no cron job that I can see doing it. We move the server to a different location and sometimes it's good for a week, but then starts rebooting hourly again. We reloaded the OS to a new drive, but after the client had it for a week or so it started rebooting again. I put the new drive into a completely new server and it was good for about 6 days, then started rebooting again. I've thought it was software-related all along, but now I'm certain of it. I just don't know where else to look to find a scheduled script that could be causing this. 

Thanks for any advice.

---

### Post by banewman on 2008-01-20
I would think that would show up in the logs... Nothing in there?

---

### Post by digital9ja on 2008-01-20
Immediately preceding each reboot there is a local connection made to the ftp server by ?@127.0.0.1

I thought that was odd, but I can't find any more information about it.

---

### Post by digital9ja on 2008-01-20
I think those local connections to the ftp server are just tests to make sure it's alive, I don't think that it actually is causing the server to reboot. I had stopped the ftp service before and the server still rebooted on the hour.

---

### Post by digital9ja on 2008-01-20
I've also tried different kernels and it still reboots hourly. :(

---

### Post by banewman on 2008-01-20
Does it have a power backup - ups?

---

### Post by digital9ja on 2008-01-20
Our entire data center is on redundant UPS backups, but this is the only server showing this behavior.

---

### Post by x3roconf on 2008-01-20
> **digital9ja said:**
> What could be the cause of hourly boots other than cron? I have a server that occasionally goes into a cycle where it reboots every hour, but there's no cron job that I can see doing it. We move the server to a different location and sometimes it's good for a week, but then starts rebooting hourly again. We reloaded the OS to a new drive, but after the client had it for a week or so it started rebooting again. I put the new drive into a completely new server and it was good for about 6 days, then started rebooting again. I've thought it was software-related all along, but now I'm certain of it. I just don't know where else to look to find a scheduled script that could be causing this. 

Thanks for any advice.

Maybe someone hacked your server? Have you checked for rootkits? check /etc/passwd and /etc/shadow for suspecting entries? Were passwords changed after reinstall? Is SSH enabled?
Any php scripts running?

---

### Post by MJN on 2008-01-20
Post your logs so we can take a look.

I think it sounds like an intermittent hardware problem though.

Mathew

---

### Post by digital9ja on 2008-01-20
It's not hardware related. All hardware has been completely changed with known good parts and the issue persists. 

Yes, PHP is running, ssh is running and the password is the same as it's been all along, which caused me a little suspicion but I haven't checked for any root kits yet. I'll run rkhunter and see if anything turns up.

I still suspect it's more likely to be a rogue script or something, but I'm at the end of the rope with this.

---

### Post by MJN on 2008-01-20
*All* the hardware? Fair enough. (Ah yes - I see you've swapped machines)

Post your logs then (ideally showing a series of reboots, with the context of what was happening before the incidents) to see if there're any clues (without such info we're completely guessing).

Mathew

---

### Post by x3roconf on 2008-01-21
Yes. You should post logs so we can check! :)

---

### Post by zipperback on 2008-01-21
If you have swapped out all your hardware, and then changed locations and then suddenly it starts happening again, yet the reboots are not showing up in the logs, more than likely someone is compromising your box, and gaining root access through some exploit.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-21
You should take a really good look at the software your client is running, including all the scripts that you are allowing them to run. It might be that they've installed something that you are unaware of, which has an exploit in it.

- zipperback
:popcorn:

---

### Post by thecure on 2008-01-21
> **digital9ja said:**
> Our entire data center is on redundant UPS backups, but this is the only server showing this behavior.

Silly questions but does this UPS line condition as well? If you get voltage either up/down or interfence can cause the reboots. I used to have a server that would reboot whenever the freezer in another room would kick on the defrost cycle. Another computer, different make an model, on the same line would keep working as if no problem. Might want to check for faults with your ground also; can get weird spikes even with UPS.

---

### Post by crouton on 2008-01-21
You could try disconnecting the machine from the network and see if that helps.  Shutting down some services (you mentioned FTP in particular) may also help diagnose the problem.

---

### Post by MJN on 2008-01-21
Come on digital9ja - in the absence of any information we're all stabbing in the dark here. Take advantage of all this enthusiasm to help and post your logs!

Mathew

---

