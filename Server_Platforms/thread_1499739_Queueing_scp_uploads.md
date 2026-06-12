---
title: "Queueing scp uploads?"
date: 2010-06-02
forum: Server Platforms
---

### Post by dmafcoi on 2010-06-02
ubuntu desktop, sshd, scp, motion, v4linux device... detects motion and uploads pics/video to remote site.

The motion app allows for an on_picture_save event where you can pipe the filename to a script, and mine goes to upload.sh where I scp to remote... the cam can save easily 10-12 pictures per second, so i'm wondering if my loop is sending one picture at a time or all at once as they happen... it seems to work fine... below is the part of the script i'm wondering about... there is more to it, but posted just this for easy answering

```
 find /home/remoteme/motion/ -type f -name "[[:digit:]]*.jpg" | while read file
do
                        BATCHKEY="/home/me/.ssh/batchkey"
                        export BATCHKEY
                        REMOTEHOST="me@myip"
                        export REMOTEHOST
                        REMOTEDIR="~/public_html/me"
                        export REMOTEDIR
                        scp -2 -i ${BATCHKEY} -P $myport $file \
                        ${REMOTEHOST}:${REMOTEDIR} >> $file 2>&1
done
```While I want the pictures to upload fast, I dont' want connections refused because I'm connecting too many times at once... does what i have send one at a time?  if not, how can i queue the uploads, so it's a controlled but steady fast upload?



Sorry if this is asked in the wrong place.

---

