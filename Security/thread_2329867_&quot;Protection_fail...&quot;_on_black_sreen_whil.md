---
title: "&quot;Protection fail...&quot; on black sreen while reboot on stuck system"
date: 2016-07-05
forum: Security
---

### Post by banceu_sergiu_ione on 2016-07-05
Hello

I have an Ubuntu 16.04 new install.

While having same issues with LO open huge file, I deiced to download a doc file and test if work.

What happen is that I get this doc file, open it for few seconds, start to scroll down and all my system got stuck.

Decide to do Ctrl+Alt+F1 and run reboot command. But all sudden its start on black screen an alert of " ......protection fail ...." and the system wont shot down, so I had pressed the power off to stop it.
Could not read it all since was scrolling down fast.

I ask what .log files could I open to see what happened or I could upload to your check.

I had to reboot several times cuz of slowness of system, delete the file, run an autoclean/autoremove but nothing had remove, and fstrim my ssd.

Now its look all ok, but I don't really know. Its look I'm short of 5-10 GB too, is there any tree command i could run to check all files size. I only have 27GB used on partition, New install, no data except CS:GO which is around 7GB. 

Here is from where i got the file, use it at your own risk. 
[ATTACH=CONFIG]269978[/ATTACH]

---

### Post by banceu_sergiu_ione on 2016-07-06
Having a look at my syslog here is what I get at system stuck time, when i try to reboot and shutdown, and while the pc turn on back. I'am not sure if this is of any help of what happened.

This is a cut of syslog
[ATTACH]269986[/ATTACH]

At 23:10:21 warning  fail to read path from javaldx

and this is when my system get stuck
you can see after i run a shutdown

Between 23:11:38 -23:13:01 is when the black screen with the "...protection fail ..." pop up. I don't know what happened neither why.
What rsyslogd-222 is, and why it loud 1st when i power on back. And look like it have not full access.

Then at 23:13:01 systemd-fsck detect same possible data corrupt, and few strings down, systemd give me 2 times notice as: clean up any mess left by 0dns-up.

My .steam folder was 20GB and no games installed. Had remove steam and folder deleted. 

Now I am back at 7 GB used disk. I add that this is a new pc, with a few weeks old SSD and have not private data on it.

What you think about?

---

### Post by banceu_sergiu_ione on 2016-07-06
I got another system stuck while try to do same work and needed to use LibreOffice. This time the system got suck as soon I had opened LibreOffice.

The syslog give same output, or almost. I did saved the syslog file if anyone is interested to check it.

Did same search and I believe that all this is related to this ' [LibreOffice vulnerability]("http://www.ubuntu.com/usn/usn-3022-1/") ' . Even if this was a few day install system up to data, so it should already be at the right version. 

Since I have to use LibreOffice, I could not longer wait for someone to give me a replay to this for a possible troubleshot, so I did a new install of OS since that for me was the easiest and fastest way to solve the issues.

For sure, I think to find a replace to LibreOffice if it keep giving trouble loading medium-huge files and for sure I will not more open untrustworthy files. 

For who want to check here is the 2nd cut of syslog, reboot event at 14:19:22
[ATTACH]269990[/ATTACH]

---

