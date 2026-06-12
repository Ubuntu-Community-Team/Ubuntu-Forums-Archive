---
title: "Upgrade to 19.04, Lose sshfs Ability"
date: 2019-06-24
forum: Server Platforms
---

### Post by moore.bryan on 2019-06-24
I have a home server running on an ancient Dell and decided to upgrade to 18.10; I could ssh into the box, but neither scp nor sshfs worked. So, I upgraded to 19.04 and the issue persists. I can ssh into the server fine, but scp and sshfs just hang without errors or interesting logs.

Any ideas?

EDIT: I'm certain the issue lays with sftp-server; has 19.04 done something funky with it?

---

### Post by LHammonds on 2019-06-26
What were you upgrading from?  On 16.04 and lower, network settings were in /etc/network/interfaces.  In 18.04 (maybe 17 as well...but I have not used it) and newer, network settings are in /etc/netplan/*

When on your server, if you cannot ping your gateway IP address, then your network settings are not correct.  Always make sure you can ping out to other active addresses on your network to test network connectivity before trying to reach the server from elsewhere.  Then test to make sure you can reach the Internet by pinging an address on the Internet such as 8.8.8.8.

LHammonds

---

### Post by moore.bryan on 2019-06-27
Thanks for the reply, @LHammonds... I upgraded from 18.04 to 18.10, lost all scp and sshfs, but still had ssh. I figured it was a quirk with 18.10, so I upgraded to 19.04.

I haven't completely ruled out my router as a source of issue, so I'm going to do some more digging and post back. I reverted to 18.04 and everything works as it should, so I'm a bit confused.

---

