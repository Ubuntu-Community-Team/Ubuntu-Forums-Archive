---
title: "hacked?"
date: 2006-02-22
forum: Server Platforms
---

### Post by benlen on 2006-02-22
I have a Unbuntu 5.10 desktop box runnig apache 2.0.54 with mysql and php.
In Firestarter I have opend incomming ports 80, 8080 and 22.
outbound is all open.

today i noticed that there was a connection at port 6668 (ircd) that had transfered over 100 MB.

I got scared and blocked all outbound ports and pulled out the internet cable.

do you think i have been hacked?

---

### Post by nocturn on 2006-02-22
[QUOTE=benlen]I have a Unbuntu 5.10 desktop box runnig apache 2.0.54 with mysql and php.
In Firestarter I have opend incomming ports 80, 8080 and 22.
outbound is all open.

today i noticed that there was a connection at port 6668 (ircd) that had transfered over 100 MB.

I got scared and blocked all outbound ports and pulled out the internet cable.

do you think i have been hacked?[/QUOTE]

I'm 99.99% sure of it.

I recommend running something like rkhunter, also inspect your /etc/passwd file for new accounts.

---

### Post by LordHunter317 on 2006-02-22
Disconnect the box now.

Boot off a live CD and run forensics.

---

### Post by benlen on 2006-02-22
I ran the chkrootkit -r /mnt/hda1 from Knoppix STD live cd and it found nothing.

Other test i should run?

---

### Post by LordHunter317 on 2006-02-22
Wait, were you running a torrent?  If so, false alarm.

---

### Post by ice60 on 2006-02-22
i thought the same thing the other day. what i had done was try to cancel a wget download, instead of doing Ctrl/c i closed terminal and the download continued in the background. 

i captured a sample using Ethereal, but it was solved when i asked a network expert friend about the IP i was downloading from and he confirmed it was connected to the IP i started the download from.

---

### Post by nalmeth on 2006-02-26
benlen -- what's the dil? False alarm?

---

### Post by RavenOfOdin on 2006-04-25
That last reply was very stupid and immature.

---

### Post by towsonu2003 on 2006-04-25
strongly agree w. raven on harlemdevil's post...

PS. /me is monitoring this thread, and not happy to be "waken up" by weird offtopic comments.

---

