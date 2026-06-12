---
title: "Updating drivers"
date: 2012-02-23
forum: Server Platforms
---

### Post by firedragoneater on 2012-02-23
Hi,
I have just recieved my new, basic spec home server board and after swapping the HDD over from my previous server have realised that I need to install some new drivers. One of the drivers I need is the LAN one as I can't currently access the network. I am trying to use the [Intel D525MW]("http://www.amazon.co.uk/gp/product/B0041RSC94/ref=oh_o00_s01_i00_details").

If this isn't possible would someone please tell me how to mount an external HDD as I have had no success with that either.


Many thanks,
Jordan

---

### Post by winh8r on 2012-02-23
Cannot offer an instant solution unfortunately as servers are not something I do much of anymore but a quick search turned this up:

[http://communities.intel.com/message/118448#118448]("http://communities.intel.com/message/118448#118448")

it appears that there were some issues with Intel boards recognising linux drives as they seem to look for a FAT partition prior to booting.

Hope that link takes you in the right direction.

There might be someone else reading this who is able to give you a more definitive answer.

---

### Post by roelforg on 2012-02-23
Assuming your HDD has 1 partition and that partition is /dev/sdb1.
```

sudo mkdir -p /media/external
sudo mount /dev/sdb1 /media/external
#... do your stuff with the hdd ...
sudo umount /media/external

```
That should work.

---

### Post by firedragoneater on 2012-02-23
Fixed using these instructions(delete file) - [http://www.linuxquestions.org/questions/linux-server-73/does-a-new-nic-need-to-be-manually-configured-in-ubuntu-server-643580/](http://www.linuxquestions.org/questions/linux-server-73/does-a-new-nic-need-to-be-manually-configured-in-ubuntu-server-643580/)

---

### Post by firedragoneater on 2012-02-26
> **roelforg said:**
> Assuming your HDD has 1 partition and that partition is /dev/sdb1.
```

sudo mkdir -p /media/external
sudo mount /dev/sdb1 /media/external
#... do your stuff with the hdd ...
sudo umount /media/external

```
That should work.

Thanks for the reply, that's helped me a lot.

---

