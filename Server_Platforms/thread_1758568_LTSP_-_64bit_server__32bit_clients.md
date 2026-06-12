---
title: "LTSP - 64bit server / 32bit clients"
date: 2011-05-14
forum: Server Platforms
---

### Post by wirefly on 2011-05-14
Hey All,

I have a bit of a question that I'm wondering if someone knows the answer too before I start.

I have a new AMD Quad core machine with 8Gb of ram currently running 64bit Ubuntu and have a load of other machines all P4 < 3Ghz (32bits) around the house which I'm looking at running off the big AMD box now.

My question is LTSP how does/will it/what if?  The AMD is running 64bit software, how is that going to affect the clients who obviously are only 32bits.  Or do I need to have 32bit running on the AMD in order to run 32bit clients?

Thanks!!

Damian

---

### Post by damormino on 2011-09-19
Yes. You can run 32-bit thin clients on a 64-bit LTSP server.

On the server, do this:
```

sudo -s
su -
ltsp-build-client --arch i386
exit

```

Power off or disconnect any thin clients you have running, then do:
```
sudo /etc/init.d/nbd-server restart
```

Here is a good explanation of the whole process of setting up a 64-bit server with 32-bit clients:
[INDENT][How to create a Ubuntu 11.04 x64 LTSP server with 32bit thin clients]("http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients")[/INDENT]

---

