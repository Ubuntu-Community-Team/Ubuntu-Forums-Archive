---
title: "&quot;Everything&quot; segfaults"
date: 2013-10-26
forum: Server Platforms
---

### Post by LazyBoy on 2013-10-26
**TL/DR:** I had two ssh connections to a 12.04 server.  The shells worked (I could "cd"), but almost every command I tried segfaulted.  Creating a third ssh connection failed.  Here's the story.

Home server running 12.04, with auto security updates.
I installed a PCIe USB 3.0 card and using ssh I backed up a small RAID to a 1TB usb drive.
> $ sudo rsync -av --progress /home /mnt/sdd1/home
I used another ssh to check on the copy and left this running over night. 

In the morning, rsync appeared to have finished.  Both ssh connections were up.
Both shells were functional (I could "cd" and navigate my history). 
But almost every command I tried segfaulted -- **"ls", "df", "gdb", "sudo", "sh", "bash", "busybox", etc.**  
I found two that did not.
> 
$ file
-bash: /usr/bin/file: Input/output error
$ strace ls
-bash: /usr/bin/strace: Input/output error

I tried to create another ssh to the server and saw
> $ ssh mastershake
ssh_exchange_identification: Connection closed by remote host

Now I've rebooted into a memtest and I'm waiting for it to finish.
I don't know what I'm going to see when I reboot again, but I thought I'd ask now since the memtest is going to take a while.

Anyone know what this is?
Thanks,
/tlc

---

### Post by LazyBoy on 2013-10-26
OK.  Memtest passed.  Reboot worked for a couple of minutes then I saw "COMRESET", "failed command: FLUSH CACHE EXT" and "I/O error, dev sda" and my / was remounted read-only.  smartctl short tests failed.
Booted twice and saw the same.

So my / drive is failing.  Maybe not.  I pulled the new PCIe USB 3.0 card and rebooted and it hasn't happened.

Could a wonky PCIe card mess up my SATA traffic?
I had to rearrange some power cables when I put the card in (it has a 4pin input)
and it and sda are next to each other on the power cable.  Could that have an effect?

---

### Post by LazyBoy on 2013-10-26
Put the card back in, rearranged my power cabling and it seems stable now.  Redid the rsync, which went quickly.

---

