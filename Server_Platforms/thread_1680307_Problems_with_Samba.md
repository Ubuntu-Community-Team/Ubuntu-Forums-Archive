---
title: "Problems with Samba"
date: 2011-02-02
forum: Server Platforms
---

### Post by matthewboh on 2011-02-02
I have had Samba installed on my 10.04 LTS server and it's worked flawlessly for quite some time.  I recently did an upgrade (I have no idea which packages, I just trust you all) and I've been having some issues with Samba.

I'm using Windows XP, Windows 7 and Ubuntu 10.10 to connect to the Samba share.  They all were able to get to the share.

I am able to ssh to the server with no problem - so that's not an issue.

I am able to ping each of my PC's from the server using both their IP addresses and their names.

If I run nmblookup on the server, I get

```
nmblookup -A 127.0.0.1
Looking up status of 127.0.0.1
        UBUNTU          <00> -         H <ACTIVE>
        UBUNTU          <03> -         H <ACTIVE>
        UBUNTU          <20> -         H <ACTIVE>
        ..__MSBROWSE__. <01> - <GROUP> H <ACTIVE>
        WORKGROUP       <1d> -         H <ACTIVE>
        WORKGROUP       <1b> -         H <ACTIVE>
        WORKGROUP       <1c> - <GROUP> H <ACTIVE>
        WORKGROUP       <1e> - <GROUP> H <ACTIVE>
        WORKGROUP       <00> - <GROUP> H <ACTIVE>

        MAC Address = 00-00-00-00-00-00

```

```
nmblookup -M -- -
querying __MSBROWSE__ on 192.168.1.255
192.168.1.100 __MSBROWSE__<01>
```

But if I do an nmblookup -S myPC I get nothing.

So it looks like I can get there, but not back to me.  What should I be looking at?

Thanks as always!

---

