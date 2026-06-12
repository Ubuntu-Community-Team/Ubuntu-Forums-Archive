---
title: "Bind9 zone transfer fail"
date: 2009-03-15
forum: Server Platforms
---

### Post by sgla1 on 2009-03-15
Bind9 will not perform all required zone transfers between ubuntu 8.04 master and 8.04 slave dns servers.  There are at least two problems.  

With the standard apparmor install, the master sends notifies for the fwd zone but not the reverse zone.
```
Mar 15 15:17:55 ns1 named[19381]: zone foo.local/IN: sending notifies (serial 2009031401)
```
There's no log entries for the reverse zone file.

After disabling apparmor on both servers, I now see notifies for the reverse zone on the master, so that indicates there is something wrong with the 'named' profile in apparmor.

Manual zone transfers from the master to the slave server (i.e. dig -t axfr my_reverse_zone) work fine.

Here's the second problem:  with apparmor disabled I see the notify for the reverse zone occur on the master, but it's not received on the slave server.

Anyone got any ideas here?

---

### Post by netsetandgo on 2009-05-22
I'm seeing this a couple of months on from the OP.

[MASTER] = local Ubuntu 8.10 server
[SLAVE] = BIND9 running on a (spit) Windows box.

Was running flawlessly without any problems. No obvious changes seen, then for no reason the upstream stops transfering complaining;

```
22-May-2009 12:25:52.067 general: info: zone <munged>/IN: refresh: skipping zone transfer as master <munged>#53 (source 0.0.0.0#0) is unreachable (cached)
```

Obviously there are no issues with the master as far as connectivity are concerned, that is up and running. You can dig / nslookup it from the slave without any problems. I don't have Apparmor in the mix (I pulled that out weeks ago). For some random reason xfers stopped working on the 20th. Ummmmm.

I have suspicions around rndc here....

---

