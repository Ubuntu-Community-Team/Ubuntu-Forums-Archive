---
title: "Problem synchronising second computer"
date: 2010-05-20
forum: Ubuntu One (CLOSED)
---

### Post by nikkkko on 2010-05-20
I work in two locations with two computers, both running Ubuntu.  My goal is to be able to open a file in one location, work on it, close it, go to the second location, open it and have those changes be available to me. I have previously done this using Unison, but with U1 I have the added advantage of an off site back up.

So, starting from the first computer I synchronised my work, (which took forever, but that's another thread), and then on the second I created a folder with the same ~/ name and synchronised that.  What happened was that all the sub-folders appeared correctly on the second computer and, after leaving the computer on over night, some of the files.  Out of the original 9.6gb of files on the first computer, being some 5900 items, about 1.9gb has sync'd on the second computer, being some 1900 items. (U1 web site reports only 9.5gb but that too is another thread). U1 preferences reports "Synchronization Complete" and the ' sync'd ' folders on the second machine show a green 'tick' icon.

What is going on?

---

### Post by buellman on 2010-05-20
Per default you just have 2Gb storage. To get 50GB storrage you have to pay 10$/month.

Greets. Buellman

---

### Post by nikkkko on 2010-05-20
I am a paying customer and have 50gb storage, which is how I managed to sync 9.6gb from my first computer.

---

### Post by buellman on 2010-05-20
Oh well... :-)

Another idea... if you don't know it already:
> Folders with a lot files (100's) are known to be slow and are targeted to be fixed for Maverick. Only see empty folders syncing? This is related to file sync being a little slower than we'd like while we improve our abilities to scale with the new users.
[https://wiki.ubuntu.com/UbuntuOne/Status#Files](https://wiki.ubuntu.com/UbuntuOne/Status#Files)

Greets. Buellman

---

### Post by nikkkko on 2010-05-20
Yeah, I saw that and posted in that thread I think. My problem is slightly different in that one computer sync's but the other doesn't.  Maybe related, who knows? I also posted that I don't want to upgrade to Maverick because it doesn't have long term support which, seeing as I am using this for work, is quite important to me.

---

### Post by joshuahoover on 2010-05-20
> **nikkkko said:**
> I work in two locations with two computers, both running Ubuntu.  My goal is to be able to open a file in one location, work on it, close it, go to the second location, open it and have those changes be available to me. I have previously done this using Unison, but with U1 I have the added advantage of an off site back up.

So, starting from the first computer I synchronised my work, (which took forever, but that's another thread), and then on the second I created a folder with the same ~/ name and synchronised that.  What happened was that all the sub-folders appeared correctly on the second computer and, after leaving the computer on over night, some of the files.  Out of the original 9.6gb of files on the first computer, being some 5900 items, about 1.9gb has sync'd on the second computer, being some 1900 items. (U1 web site reports only 9.5gb but that too is another thread). U1 preferences reports "Synchronization Complete" and the ' sync'd ' folders on the second machine show a green 'tick' icon.

What is going on?

There's a possibility you're affected by bug #571548 which we are going to be releasing a fix for soon. There is a workaround documented in the description of that bug that you can try. If that does not solve the problem for you, can you please file a bug and let me know the number here so I can be sure it gets looked into ASAP?

1. Run the following from a terminal session: echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; u1sdtool -q; u1sdtool -c 

2. File a bug at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

3. Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######

4. Run this command from a terminal session: tar cjf ~/u1_logs.tar.bz2 ~/.cache/ubuntuone/log

5. Attach ~/u1_logs.tar.bz2 to the bug report

Thank you,

Joshua

---

### Post by nikkkko on 2010-05-31
I found an easier solution : 

1 cancel ubuntu one account
2 create dropbox account

I would love to support Ubuntu financially and perhaps will do in the future when the service works as it should.  Until then, as a paying customer, I will use dropbox, which works perfectly.

---

