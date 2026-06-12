---
title: "Script to email me if storage runs out"
date: 2007-10-08
forum: Server Platforms
---

### Post by hagen00 on 2007-10-08
Hi there

Can anyone help me out and give me code for a bash script to email me if the storage on my server is about to run out?

i.e. if storage is at 90%, email me. 

Thanks a lot. I've had a look in Google, but haven't found much. 

h

---

### Post by MJN on 2007-10-08
The following should suffice.
 
```

#!/bin/sh
# Script to check disk usage of a partition and notify by e-mail if a pre-defined limit is exceeded
# v0.3
 
# Define partition (/dev device or mount point) to check, threshold trigger (in %) and address to alert
PARTITION=/dev/hda1
THRESHOLD=90
ADDRESS=yourem@iladdress
 
# Use df to find disk usage of PARTITION and extract the figure
USAGE=`df |grep $PARTITION |sed 's/.* \([0-9]*\)%.*/\1/'`
 
# Compare the USAGE with THRESHOLD and send an e-mail if exceeded
case `echo "$USAGE >= $THRESHOLD" |bc` in
   1) df -h |mail -s "Warning: $PARTITION usage is greater than $THRESHOLD% (=$USAGE%)!" $ADDRESS;
      ;;
esac
 
exit

```Set the values of PARTITION, THRESHOLD and ADDRESS to suit.
 
Having defined the variables for the script, it checks the current usage of your partition using the **df** command - the output of this is then stripped of everything bar the figure before the %. This is then sent to **bc** to compare it with your threshold. If this is met/exceeded (change >= to > if you only want exceeded) then bc returns 1 which is then used to trigger the sending of a mail to you. The mail takes the subject form *'Warning: /dev/hda1 usage is greater than 90% (=95%)!*" and includes the output of df -h (showing disk usage of all drives in a human-friendly format) in the message body.
 
I'm not at my machine right now to check it works but it should do (famous last words!).
 
Any questions just shout.
 
Mathew

---

### Post by hagen00 on 2007-10-08
thanks! perfect! I also appreciate that you took the time to explain the code.

---

### Post by MJN on 2007-10-08
No problem - it's always worth learning how something works as before you know it you'll be able to write it yourself.
 
Have you tried it? Obviously the best way to test is by setting a low threshold and giving it a shot.
 
Edit 1: You might prefer to use the mount point (e.g. /home) as opposed to device partition (/dev/hda1) as this will probably make more immediate sense in an e-mail (particularly if you're going to be checking multiple partitions).
Edit 2: I've noticed a missing ` on the end of the usage line so have amended the code above.
 
Mathew

---

### Post by MJN on 2007-10-08
Hagen00,

I've got home now and found the script didn't work (half expected it - script writing on theory often doesn't!) It was simply a case of me not realising that the df output gave a header line even when asking just for the one partition. It's fixed now (added a grep to extract just the line we need) and so you should be good to go with v0.3 above.

Mathew

---

