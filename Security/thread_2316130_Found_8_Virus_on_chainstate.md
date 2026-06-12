---
title: "Found 8 Virus on chainstate"
date: 2016-03-05
forum: Security
---

### Post by jantaro2 on 2016-03-05
[COLOR=#000000][FONT=Verdana] Hi: I m trying to use bitcoin in the safest way: I learned that the best thing I could do is running bitcoind and bitcoin-qt, as it is a full-node and outcoming transactions are safer because part of the process is done on my computer due to that huge folder (over 60 GB ) where blockchain is stored.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]   [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]   I choosed Linux as Operative System for bitcoind and bitcoin qt and well, the thing is that I found up to 8 virus on this location:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]/home/user/.bitcoin/chainstate/[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]like for instance:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]/home/user/.bitcoin/chainstate/427915.ldb: Gen 981 FOUND[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]well, CLAMAV reports 8 viruses on these .ldb files contained on /home/user/.bitcoin/chainstate/[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]GEN 981, Violetta-B, Gergana-222, Gen 100 Years 1, Phantom, Italian 1, Copyright.2, Syslock.2 are the names[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Tried to find out if some other users where afected or how this could be solved, the only thing I found is a similar problem related with sst files on Windows users and some other reports but no forum discussion.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Would like to ask someone who would know about it what should I do next?.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]of course I can erase them with[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana] sudo clamscan -r --remove/home   [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]but ... will I mess something on bitcoind, bitcoin-qt ?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]What could I do?. I don´t feel like safe using this due to CLAMAV, but little do I understand about virus or malware, apart from scanning. So I m making this post to let the community know about it and in hope I could find a solution and/or explanation.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Kind Regards.[/FONT][/COLOR]

---

### Post by s0urCr34m on 2016-03-05
Have you tried using a free antivirus LiveCD to scan your drive? Remember to take into consideration 'false positives'. You may also seek information at clamav's website, I believe they have mailing lists. Sometimes it could be something as simple as a definitions update for ClamAV detecting false positives, and upgrading the ClamAV definitions to resolve the problem. In addition to several free antivirus LiveCDs available there are also installable antivirus programs for Linux, one example is Sophos, which, IIRC has better results than ClamAV. IMO pretty much anything has better detection rates and less false positives than ClamAV. You can also try some auditing and/or rootkit scanners, some are in the Ubuntu repositories (I like using Synaptic to install new packages). You can try free programs like chkrootkit, rkhunter, tiger, lynis, etc. There are also bitcoin forums, one being [https://bitcointalk.org/](https://bitcointalk.org/) but I've never participated there.

---

