---
title: "dovecot: add a userdb - what is this?"
date: 2007-04-27
forum: Server Platforms
---

### Post by wadesmart on 2007-04-27
I installed dovecot yesterday and so I have had a lot of reading to do. I have been following 
[http://wiki.dovecot.org/BasicConfiguration](http://wiki.dovecot.org/BasicConfiguration)   the Basic Configuration setup. I went through the steps of starting dovecot but received the message: Connection closed by foreign host.... something like that. 

I had a power outage and so I had to reboot. After when I try to start dovecot I receive:
dovecot: auth(default): You'll need to add at least one userdb. Im not sure what that means. 

wade

---

### Post by rsermilik on 2007-04-28
It tells you that you must add some kind of user database, look under Authentication in the guide.
Was the power outage during before the installation was finish? If yes then follow the install guide again. Of course you are writing down each step your are doing so its no big problem..........

These guides assume that you know your system, knows how to make permissions, users, groups and much more. If you don't know what a userdb is then you should probably find another guide to follow.

Always remember to read the guides and be sure you understand everything it says before you start.

---

### Post by wadesmart on 2007-04-28
I fixed the userdb error after a few hours of reading.

One last thing, when I telnet in to check if it was running, I checked the Inbox like the tutorial said to and it said 10920 exists, 889 recent.

I havent been able to read my mail since I have been doing this but fetchmail has getting it for me. My /Maildir/new had 889 and now it has 1. What just happened to my email?

---

