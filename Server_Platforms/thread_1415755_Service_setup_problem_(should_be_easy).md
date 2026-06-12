---
title: "Service setup problem (should be easy)"
date: 2010-02-25
forum: Server Platforms
---

### Post by omargomez on 2010-02-25
Hi,

I've been a long time Ubuntu desktop user but now I happen to be working with a server environment in which I don't have too much experience with.

I have this java server (exist-db) which I need to setup as a service. I followed the usual steps of adding a link in /etc/init.d and then calling update-rc.d exist defaults. The linked shell script (exist.sh) has been made executable also.

The issue is that the script can find another program it needs to use:

WRAPPER_CMD="./wrapper"

# after that...

exec $CMDNICE $WRAPPER_CMD $WRAPPER_CONF wrapper.pidfile=$PIDFILE

I've tried everything, but nothing seems to fix this

Thanks for your help

--Omar

---

### Post by i.r.id10t on 2010-02-25
Your script is looking in whatever directory it is in (the ./ part) for a program named "wrapper".  Find that on your system, change the path to it in the script.

---

### Post by omargomez on 2010-02-25
Thanks for your reply,

I'm afraid everything look OK. I mean, the referenced file is where it should. I was wondering if this has to do with other issues like ownerships or permissions of some kind 

--Thanks

---

### Post by joberly on 2010-02-25
So what is the exact error your get when trying to run the script?

---

