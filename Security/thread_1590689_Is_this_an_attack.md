---
title: "Is this an attack?"
date: 2010-10-08
forum: Security
---

### Post by resander on 2010-10-08
On Ubuntu 10.04 on Compaq PC.

As a normal user, I was downloading using Bit Torrent in the background and reading some documents in the foreground when I noticed the cpu usage had gone up to nearly 100% without reason. I stopped all programs but could still see send and receive internet activity when looking at the System Monitor. I don't know the function of most processes shown by the system monitor, but I could not see any suspect process becoming active. The CPU history fluctuated between 10% and 60%. About 100-200 bytes was sent and received approximately every 10 seconds. 

Turned off PC and turned it on again and logged on. I noticed the screen resolution had changed from 800x600 that is best for my eyesight to 1024x768. Internet send and receive activity was still going on. I also logged out and logged in as another user, but there was still activity. 

Then disconnected from Internet, but there was still activity with CPU history showing around 10-12% (part of that would be for the System Monitor itself).

I have used Ubuntu for 3 years and everything has worked fine without antivirus and firewall.

I have no knowledge about problems like this and would be most grateful for advice.


P.S. Have only one PC and need to reconnect to Internet to send this post.
Connected and saw about 500 bytes sent and 20 seconds later about 600 bytes received. About an hour has gone since I logged on and 93KB has been received and 118KB sent during this period. The Internet activity has stopped with nothing sent and received for about 10 minutes.

---

### Post by CharlesA on 2010-10-08
Idle network activity is normal.

Has the resolution reset itself to 1024x768 again, or was it just that one time?

---

### Post by Rubi1200 on 2010-10-08
> **CharlesA said:**
> Idle network activity is normal.
+1

Also, the process for Update Manager runs in the background after the computer starts and can sometimes bump the CPU up. Again, this is quite normal and nothing to be concerned about.

---

### Post by The Cog on 2010-10-08
If you were using BitTorrent then I wouldn't be surprised to see at least some network activity even after a reboot. Probably lots of peers still trying to talk to you.

A minute or so after booting, a process quite often chews up CPU for a while trying to work out what updates are available - that also uses network of course.

I've never felt comfortable with the system monitor. For some reason, I always have the feeling that maybe it's not telling me everything. So I prefer to use the command line program **top**, or better still (not installed by default, but in the repositories) **htop**.

---

### Post by cariboo on 2010-10-08
System monitor has it's own overhead normally about 6% to 12% usage.

See the screenshot.

---

### Post by resander on 2010-10-08
Thanks CharlesA & Rubi1200

When this happened the torrent was crawling at snail's pace and I was only reading an html document offline using Firefox. Then abruptly the CPU usage shot up to nearly 100% which lasted for about 5 minutes until I stopped the torrent and Firefox. I have never observed this before so got a bit alarmed.

The screen resolution had changed when I logged in after restart. I have never seen this before. It only happened this time.

Would like to learn a bit more...

Q1. what might be causes of sudden spike of activity in this or similar cases? I am not running any cron jobs or requesting automatic updates or running downloaded programs from outside sources (only from the Ubuntu Software Centre and Synaptic) and I do not call the Update manager from my normal user account (only do as a superuser). 

Q2. why is there normal idle network activity? For example, what parties are engaging in this kind of conversation?


I am careful not click on links in emails giving away authentication info etc, but my children sometimes log in and could be carried away at the prospect of getting a price/reward and start clicking carelessly. They have their own accounts and do not know my password and the root password.
If they are fooled and pick up a malicious program will the effect be contained to their home directories? Or is there ANY possibility of the intruder drilling through the wall and get root privileges?

chkrootkit and and rkhunter have been mentioned in this forum. Are these tools for detecting existing infections only? Should I install these? Three years ago I was using ZoneAlarm and Kaspersky on Windows, which I believe (not sure) tried to stop attacks. Is there something similar available for Ubuntu?  

OR, should I stop worrying? I have had three years of peaceful bliss on Ubuntu not having to look over my shoulder for virus attacks all the time.

P.S. I was preparing the above offline and when I got online to the forum there were additional responses. I will look at these tomorrow. Time to go to sleep...(in UK).

Ken

---

### Post by Sporkman on 2010-10-11
The UbuntuOne sync daemon will send/receive big bursts of data whenever the contents of the Ubuntu One sync folder change.

---

### Post by resander on 2010-10-12
Most of the questions in my last post have been answered or mentioned in the sticky threads, but allow me to ask just one more...

When I turned off and turned the PC back on I did not restart the bit torrent client. 

I understand that bit torrent peers would continue to issue requests for data after restart. That would account for incoming data bursts, but I observed pairs of incoming and outgoing data bursts. Where are these coming from? Is there another bit torrent process running on my PC in the background responding to the peers (when the interactive bit torrent client is off)?

Since showing Windows the door three years ago I have had peace on Ubuntu without a single security issue. I think that will continue.

It would be useful though for people like myself coming from Windows to be able read about bursts of activity on Ubuntu that are normal and not symptoms of intruders calling back home. Like what has been mentioned in this thread and a few more maybe.

Regards
Ken

---

