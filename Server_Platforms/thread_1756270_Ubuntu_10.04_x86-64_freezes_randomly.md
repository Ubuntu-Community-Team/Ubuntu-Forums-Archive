---
title: "Ubuntu 10.04 x86-64 freezes randomly"
date: 2011-05-12
forum: Server Platforms
---

### Post by xensystems on 2011-05-12
Hello!

Our Ubuntu 10.04 x86-64 based server blows my mind - it freezes randomly (avg. 1 time per week): machine become network unreachable, no video output to IP-KVM (just black screen). So we have to phone DC Support and ask them to hard-reset server.

Unfortunately, i can't understand why it happens, system log has no records that may help.
It very strange, but we have 3 Ubuntu 10.04 X86-64 servers with almost the same hardware configuration, and only one freezes periodically. One difference-  server that hangs up has SAS HDDs instead of SATA.

Does anybody know is it possible to debug this behavior ?:confused:

---

### Post by terarmt on 2011-05-12
I did not understand too, hoping to have a good response!

---

### Post by amgugten on 2011-05-27
Same here: Ubuntu Server 10.04 LTS x86_64 + 3ware RAID + SAS locks up every other day. Exact same OS, but with SATA instead runs without any problem.

There are no clues in the log files whatsoever, no kernel dump (just a blank screen on the console). First ran memtest for about 8 hours, so I am reasonably sure the memory is ok. I suspected ntpd, but other server works with ntpd. Now looking at KVM and testing with no domU's started at the moment.

Really hope to find a solution to this soon, since the server is not ready for production as it is now. Will post details if I find out more.

---

### Post by satworld on 2011-06-04
i was going to buy a ide hard drive because of sata problem until i read your post.
its not stable in sata too.
sometime it will notbott or wont detect seagate 2 tb hdd sata 3-6gbs
maybe your problem is a memory problem
sometimes with 4gb of memory its not stable then it freeze it has nothing to do with ide or sata hdd.
i think it will be better to go back to an older version until it get stable .

---

### Post by z00m1n on 2011-07-19
same here:

kubuntu 10.04 64 bit keeps freezing reproducibly after a certain amount of time, something between a couple of minutes and 1 or 2 hours.

i've been using [k]ubuntu since 2008 and it never ever froze on me like that - unless there was a hardware issue, that's why i assumed a similar problem in this case as well. however, i have now replaced all hardware in the machine and the system still freezes. moreover, i do not get any freezes with openSUSE 11.4 x86_64 nor with Kubuntu 10.04 32 bit. this thread shows i'm not the only one with that problem.

i think this suggests this is a bug in the OS and not a problem with flaky hardware.

what i am doing to reproduce the freeze is start a live system from a usb stick, mount a number of harddrives read-only and run 2 diffs at the same time over 2 folders, each about 500 GB in size.

when i do that, i do not get beyond 90 minutes of uptime.

no messages in the logs, no kernel panics in the shell, no other clue to what's happening anywhere else i know of. REISUB shows no reaction. not even the display comes back up from standby when i hit a key or move the mouse.

the hardware is now obviously brandnew and very recently. nothing exotic, just plain off-the-shelf from the shop down the block. can provide details if that helps.

i am happy to re-test this with some other setup, some debug messages enabled or whatever else might help to trace down the cause of the problem.

has anyone filed a bug report about this yet ?

---

### Post by z00m1n on 2011-07-19
update: noticed the freeze intially with _K_ubuntu-10.04.2-desktop-amd64, now I've downloaded _U_buntu-10.04.2-desktop-amd64, run it from a live usb stick and did the same massive diffs again --> after 50 minutes uptime, the system freezes unrecoverably.

---

### Post by tannedin on 2011-08-17
*bump*

Running 2x amd opterons
10.04.3 LTS (64 bit server)

I get about 30 minutes of up time before a complete system freeze and router won't get a positive ping back

---

