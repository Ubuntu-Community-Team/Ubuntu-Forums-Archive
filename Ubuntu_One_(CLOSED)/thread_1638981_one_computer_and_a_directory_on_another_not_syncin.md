---
title: "one computer and a directory on another not syncing"
date: 2010-12-06
forum: Ubuntu One (CLOSED)
---

### Post by jbeiter on 2010-12-06
this is the first app I have ever seen that *requires* the gnome key deamon (irritating thing that needs to be shot) but I'm trying to sync things on three systems and this just doesn't work. One system just stopped working.. no errors, nothing in /messages. 

The other two haven't synced a directory in months and I can't see any reason why not.

Great idea but this app is a FAIL. Anyone doing this successfully through something else before I set up scripts and cron?

---

### Post by duanedesign on 2010-12-07
jbeiter,
sorry to hear Ubuntu One is not working as expected. Lets start with the one computer that "just stopped working" then we can address the ones that are having trouble with syncing a directory.

Can you look at the following file and if their is anything in it please post it. (Please eclose log files in the CODE tags, the hash symbol in the Post Editor)
~/.cache/ubuntuone/log/syncdaemon-exceptions.log
if this is empty could you post your
~/.cache/ubuntuone/log/syncdaemon.log

thank you,
duanedesign

NOTE: On the two computers that are not sycing a particular directory could you run this command from the Terminal and see if it helps:

u1sdtool --refresh-volumes

---

