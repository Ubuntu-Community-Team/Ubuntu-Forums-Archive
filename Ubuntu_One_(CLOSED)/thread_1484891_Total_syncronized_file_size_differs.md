---
title: "Total syncronized file size differs"
date: 2010-05-16
forum: Ubuntu One (CLOSED)
---

### Post by robbanl on 2010-05-16
I'm synchronizing two folders with the total size of 98,4mb when looking in Nautilus. In the Ubuntu one preferences the total size says 108,9mb. Why does the file size differ?

---

### Post by nikkkko on 2010-05-17
I have the same problem but the other way around.  I have sync'd a folder and it's contents, some 5700 files in total and according to Nautilus, 9.1gb.  Ubuntu One tells me I've successfully sync'd 9.0gb.  Where'd the other 100 odd mb go?

Is there any way to see the total number of files / directories sync'd on Ubuntu One?  How can I be sure everything is there?

---

### Post by nikkkko on 2010-05-17
Just to make it harder, I can organise my Nautilus files according to size, name, type etc., but can't do that in Ubuntu One which means that even a visual check is impossible.  Just how are the folders in Ubuntu One organised?

---

### Post by joshuahoover on 2010-05-18
For those having this problem, can you private message me your username that you sign into Ubuntu One with? We have a bug ([https://launchpad.net/bugs/484142](https://launchpad.net/bugs/484142)) where some users see this problem and we have to run a one time fix to correct it. If that doesn't work, then we have a different problem that we need to look into further. 

Thank you,

Joshua

---

### Post by robbanl on 2010-05-19
Can the problem relate to that i'm only synchronizing folders from my NTFS partition?

---

### Post by joshuahoover on 2010-05-19
> **robbanl said:**
> Can the problem relate to that i'm only synchronizing folders from my NTFS partition?

No, this shouldn't. A developer is looking into this right now on the server side. 

Thank you,

Joshua

---

### Post by joshuahoover on 2010-05-19
To those seeing this issue, can you also let me know what the following command outputs for you?

u1sdtool -s

The last line should show IDLE if Ubuntu One is done syncing files.

Thank you,

Joshua

---

### Post by robbanl on 2010-05-23
Here is the output.

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_METADATA

As a note my ubuntu one client still have status synchronizing after about 2 weeks since it started uploading.

---

### Post by joshuahoover on 2010-05-24
> **robbanl said:**
> Here is the output.

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_METADATA

As a note my ubuntu one client still have status synchronizing after about 2 weeks since it started uploading.

This means Ubuntu One syncdaemon is still processing so it's not done. Since it's been going for 2 weeks, unless you've been changing or adding files a lot, something is not right. Can you file a bug following the steps below and let me know the number? I'll take a look at it and get a developer to look into it ASAP.

1. Run the following from a terminal session: echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; sudo sed -i 's/LOG_LEVEL = logging.INFO/LOG_LEVEL = logging.DEBUG/' /usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/logger.py; u1sdtool -q; u1sdtool -c 

2. File a bug at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

3. Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######

4. Run this command from a terminal session: tar cjf ~/u1logs.tar.bz2 ~/.cache/ubuntuone/log

5. Attach ~/u1logs.tar.bz2 to the bug report

Thank you,

Joshua

---

### Post by robbanl on 2010-05-25
I followed your steps to write a bug report and this is the id: 585518.

Thanks for all your help.

---

### Post by joshuahoover on 2010-05-27
> **robbanl said:**
> I followed your steps to write a bug report and this is the id: 585518.

Thanks for all your help.

I followed up on the bug report. Thanks for filing this. In case others read this thread, the problem appears to be a result of slow file sync performance on the server side. We're working on fixing this. 

Thanks,

Joshua

---

