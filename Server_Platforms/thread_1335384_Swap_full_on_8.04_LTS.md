---
title: "Swap full on 8.04 LTS?"
date: 2009-11-23
forum: Server Platforms
---

### Post by mindsizzlers on 2009-11-23
Could some kind sole please confirm what the correct interpretation of this data is on our 8.04LTS Ubuntu server? I've not seen this before on any other linux we run so am unclear as to the issue.

The server has been up for 57 days. Normally it reports a small amount of memory free (perhaps 80% utilisation) and swap has been slowly creeping up day by day. Now it seems to be reporting lots of memory free, but the swap is totally full? The server is just a webserver so I'm a bit puzzled by this activity under Ubuntu and am wondering what has gone wrong?

$free
             total       used       free     shared    buffers     cached
Mem:       1747764    1376628     371136          0      23476     320132
-/+ buffers/cache:    1033020     714744
Swap:       917496     917496          0

$cat /etc/fstab
# Legacy /etc/fstab
# Supplied by: ec2-ami-tools-1.3-34544
/dev/sda1 /     ext3    defaults 1 1
/dev/sda2 /mnt  ext3    defaults 0 0
/dev/sda3 swap  swap    defaults 0 0
none      /proc proc    defaults 0 0
none      /sys  sysfs   defaults 0 0

$blkid

/dev/sda2: UUID="5b189ce7-f654-4bca-a6ab-21a4d547c2d1" TYPE="ext3"
/dev/sda3: TYPE="swap"
/dev/sda1: UUID="77c5dff1-17d2-4f00-a615-3fcc9fc40910" TYPE="ext3"

I'm puzzled as to why ubuntu is gradually eating all the swap? Does something have a memory leak?

Ahhhhhhhh hang on ... I've just twigged something. I'm running apache with mod_perl and ubuntu defaults to a different memory model to the one I am used to (prefork) ... I wonder if I have a leak there ... BINGO - just done a full apache restart rather than a graceful one and all my memory and swap has come back to normal ... looks like I'm off to examine my apache config!

Hope this might help someone else.

Roger

---

