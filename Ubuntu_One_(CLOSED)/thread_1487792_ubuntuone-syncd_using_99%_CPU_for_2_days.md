---
title: "ubuntuone-syncd using 99% CPU for 2 days"
date: 2010-05-19
forum: Ubuntu One (CLOSED)
---

### Post by kswenson on 2010-05-19
I chose a folder with 1.8 GB for syncing to the ubuntu one server.
I have two questions:
1) ubuntuone-syncd has been using 99% cpu (at times) for two days now.  Is this normal?

2) the syncing is EXTREMELY slow.  I don't have any bandwidth limitations set and there seems to be very little data getting uploaded.  Is this normal?

Thanks for the help.

---

### Post by Pifilatakanemu on 2010-05-19
Try [Dropbox]("https://www.dropbox.com/referrals/NTIxNTQxNzg5").

It won't solve your problems with U1 but you'll have a working cloud storage service until U1 is stable enough.
[]("https://www.dropbox.com/referrals/NTIxNTQxNzg5")

---

### Post by duanedesign on 2010-05-19
The syncdaemon should not be using 100% cpu.

Syncing 1000's of files is not that fast at the moment. The U1 team is working to make the syncing of lots of small files faster.

---

### Post by joshuahoover on 2010-05-20
> **kswenson said:**
> I chose a folder with 1.8 GB for syncing to the ubuntu one server.
I have two questions:
1) ubuntuone-syncd has been using 99% cpu (at times) for two days now.  Is this normal?

2) the syncing is EXTREMELY slow.  I don't have any bandwidth limitations set and there seems to be very little data getting uploaded.  Is this normal?

Thanks for the help.

As Duane said, Ubuntu One should not be using 99% of your CPU, especially not for two days. Can you file a bug to help us get to the bottom of this problem? If so, please follow the steps below and let me know the bug number. I'll make sure it gets some attention right away.

1. Run the following from a terminal session: echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; u1sdtool -q; u1sdtool -c 

2. File a bug at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

3. Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######

4. Run this command from a terminal session: tar cjf ~/u1_logs.tar.bz2 ~/.cache/ubuntuone/log

5. Attach ~/u1_logs.tar.bz2 to the bug report

Thank you,

Joshua

---

### Post by kswenson on 2010-05-21
OK...
  the bug number is #583642

Let me know if you need anything else.

---

### Post by LMendy on 2011-07-18
I'm experiencing this same issue. Sometimes ubuntuone-syncd will use 99% of my CPU and prevent me from doing much else. I have to kill the process to use my PC.

Any suggestions? Has a solution been found? 

I'm running Xubuntu 10.10.

Thanks!

---

### Post by duanedesign on 2011-07-18
You can get more detailed logs to help in troubleshooting issues by doing the following:

1. Open Applications->Accessories->Terminal and run:
```
echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; u1sdtool -q; u1sdtool -c
```

2. Copy files into your ~/Ubuntu One folder and let it run for awhile to collect information.

3. Open your home folder

4. Click the View->Show Hidden Files menu option

5. Open the .cache/ubuntuone/ folder

6. Right click on the log/ folder and select "Compress"

7. Click OK and you should have a file named "log.tar.gz" in the .cache/ubuntuone folder, move this file to your Desktop since it's in a hidden folder which can be hard to find in the next step

8. You can attach the log.tar.gz archive to a bug report or an email to [EMAIL="ubuntuone-support@canonical.com"]U1 support[/EMAIL].

respectfully,
duanedesign

---

### Post by Alexis Wilke on 2012-01-31
Note that we're Jan 2012 and I still have the problem, so I guess this wasn't resolved yet. :(

I'm running with Ubuntu 11.04.

Any reason why I would need to keep that tool? Can't I just remove it?

Also... just wondering, since it is specific to myself (as in, my user), does this means if I have 20 users on my computer, it's doing this work for 20 people?

Thank you.
Alexis

---

