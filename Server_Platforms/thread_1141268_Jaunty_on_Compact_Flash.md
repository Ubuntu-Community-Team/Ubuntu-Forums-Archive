---
title: "Jaunty on Compact Flash"
date: 2009-04-28
forum: Server Platforms
---

### Post by Zeroone on 2009-04-28
hi all

i'm waiting to receive an alix.1d embedded board to make a little ubuntu server
it uses compact flash so i would like to install ubuntu server or xubuntu on it

someone of you have experienced to install *ubuntu on compact flash?

do you a valid howto? i tried to search but i didn't find anything i could use

thanks
regards

---

### Post by antikristian on 2009-04-28
Chech out netbook howtos for tips on reducing IO, read and write are slower on CF. Get a fast CF, at least 250x.

Set harddrives to noatime in fstab
enable tmpfs for /tmp
discurage swapping (nice to have swap, just in case, but discuraging it helps speed)
reduce logging to hinder syslog filling up the disk, implement logrotate
remember, extensive writing wears out the CF!!
I would use ext3 since it's a server, and non journaling FS sucks after a poweroutage, some people recommend ext2 though, since it's kinder on IO

I think you have to choose between what is most valuable to you, and try to tune your system after that priority. is the data, the reliability, speed or the CF most valuable to you?

Good luck:)

---

