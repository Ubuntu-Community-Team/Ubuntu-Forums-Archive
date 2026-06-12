---
title: "plymouthd stuck, getty not spawning in 10.04 after upgrade from 9.10"
date: 2010-04-30
forum: Server Platforms
---

### Post by ikester on 2010-04-30
I just upgraded a few Dell PowerEdge 1750 servers from an up-to-date base install of 9.10 to 10.04.

First, I noticed that some of the servers where using up to half their memory while others were using only ~10%. And this is on identical hardware/config.

Then I noticed that some of the servers were running different processes. After several reboots I still can't get all the servers to run a predictable set of services. Sometimes they get stuck with a plymouthd process like this:

root       287  0.0  0.2   3904  2412 ?        S    00:41   0:00 /sbin/plymouthd --mode=boot --attach-to-session

When this happens, getty is not spawned. Sometimes the gettys do spawn but I also see a lot of [flush-1] entries in the process list like:

root       223  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:0]
root       224  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:1]
root       225  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:2]
root       226  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:3]
root       227  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:4]
root       228  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:5]
root       229  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:6]
root       230  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:7]
root       231  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:8]
root       232  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:9]
root       233  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:10]
root       234  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:11]
root       235  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:12]
root       236  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:13]
root       237  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:14]
root       238  0.0  0.0      0     0 ?        S    08:02   0:00 [flush-1:15]

Why is plymouth even running on a server install? I thought it's primary function was to manage the boot splash screen. I know that it handles other things but is it really needed on a server install? And what's the story with those flush-1 processes?

Anybody else seeing this?

---

### Post by spronkey on 2010-06-07
Yes.

Searched around for this - found this bug: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/571707?comments=all](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/571707?comments=all)

It appears to be some kind of overload in the messages sent to plymouth and mountall from the fsck process.

The solution for me was to sudo apt-get install mountall updating it from 2.14 to 2.15.

With regards to why plymouth is running, I don't know! Perhaps it was easier to leave it there than segment desktop/server code more? There is a text-based graphical splash that appears sometimes in the server edition?

---

