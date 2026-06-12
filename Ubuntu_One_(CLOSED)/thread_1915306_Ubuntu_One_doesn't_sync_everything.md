---
title: "Ubuntu One doesn't sync everything"
date: 2012-01-25
forum: Ubuntu One (CLOSED)
---

### Post by bookcrazy on 2012-01-25
OK, 

So I uploaded files from my work computer that is running Ubuntu 10.04 to my ubuntu one account thinking it would sync to my home laptop which is running 11.10.

In my ubuntu one control panel it shows both devices (my work and home laptops) as being connected and synced but they are not identical:

I have some videos on my work computer that are not syncing to my home laptop. The videos are visible when I go to my ubuntu one account on-line but they don't show up on in my ubuntu one folder on my home laptop.

I ran: ```
u1sdtool -s
``` and the output is: 
```
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE
```

Anyone have any ideas besides just putting them on my computer with a flash :) I'm in China so dropbox and google docs are not options (they're blocked).

---

### Post by duanedesign on 2012-01-26
Hi,
If the videos show up at your cloud space, they made it from your work computer. The issue looks to be the 11.10 computer. First make sure under the cloud folders tab the folders are checked to Sync Locally.
If that is the case could you please open a Terminal and run the command u1sdtool -c, this connects the syncdaemon. Then after a couple minutes could you run u1sdtool -s. Could you please the output as an attachment to your email.
Thank you,
Duane

---

### Post by bookcrazy on 2012-01-27
Hello Duane and thank you for taking up my cause :)

I opened my Ubuntu One Control Panel and yes, under the "cloud folders" tab I have it checked to sync locally.

I then entered ```
u1sdtool -c
``` waited ten minutes and then ran ```
u1sdtool -s
``` and the output is ```
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE
```

What do you recommend? 

Cheers!

---

### Post by bookcrazy on 2012-02-17
There's nothing I can do about this is there?

---

