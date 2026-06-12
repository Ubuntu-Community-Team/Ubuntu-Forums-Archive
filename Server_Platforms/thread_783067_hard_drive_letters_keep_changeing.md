---
title: "hard drive letters keep changeing"
date: 2008-05-05
forum: Server Platforms
---

### Post by mgrvln on 2008-05-05
Hi added a couple of drives to an old box to use as a media server. The drives are formated ext3 and mount fine but the problem is each time the system reboots the drive letters change. If it were just a server it wouldnt be such a big problem but the other computers and xbox are set to look for music in the music mount, movies in the movies mount etc. is there a way to make sure the drives keep the same letter? There are 5 hard drives and 3 are on an pci ide card. I am running Ubuntu 8.04 fresh install. thanks

---

### Post by bluefrog on 2008-05-05
letters? we are talking ubuntu not windows, please describe a bit more precisely your problem with examples maybe.

if you are talking about the peripheral numbering (/dev/sdax, sdbx) then you should use uuid in the fstab to identify your partitions

example
vol_id /dev/sda1
will provide you with the uuid, then use it to update your fstab accordingly.

---

### Post by mgrvln on 2008-05-05
yes the /dev/sda not letters my bad.so the uuid will in the fstab will solve this prob after each reboot then?

---

### Post by bluefrog on 2008-05-05
uuid does not change even if the peripheral name does.

example
/etc/fstab
# /dev/sda1
UUID=e983f881-b1cd-438b-9043-4d7eedd38d89 /boot           ext3    defaults    0       2
# /dev/mapper/vg01-lvhome
UUID=5989f573-3e24-4beb-ab2e-97703deaef3d /home           ext3    acl,defaults        0       2
# /dev/mapper/vg01-lvswap
UUID=fc876ecd-681b-4fb2-bf42-18eec37643b7 none            swap    sw              0       0

---

### Post by mgrvln on 2008-05-05
cool tyvm. we will see how this goes.

---

### Post by mgrvln on 2008-05-05
you the man bluefrog! worked like a charm:)

---

