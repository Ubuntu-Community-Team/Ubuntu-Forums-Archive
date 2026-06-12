---
title: "Installing Ubuntu server 10.4 64bit on Fujitsu siemens X300 s2"
date: 2010-07-16
forum: Server Platforms
---

### Post by Almeida80 on 2010-07-16
Hi Guys,

i am trying to install ubuntu server 10.4 on a fujitsu siemens x300 s2, but when it comes to dectcting the hard disk it cant find them. it says i have to load the scsi drivers. i have gone threw the list that appears on the list but none work. Has anyone got any ideas of were i can get the drivers from. 

thanks for all the future help.

oh and i am a newbie to linux.

---

### Post by Ficc on 2010-07-19
Hi,

i've had the same problem. My server is exactly the same as yours.

Here's what i did.

Boot the server with the Primergy ServerView Suite (ServerStart CD).
Proceed with the normal configuration as if you were about to install Windows Server 2003, up to the part where you are requested to configure the HDD Partitions.
After that (making sure that the partitions are created and formatted) you can restart the server, this time booting up with a Ubuntu Server DVD.

It should now recognize the drives and you can partition them as you wish.

Hope this helps.

Best regards

---

### Post by Almeida80 on 2010-07-29
thank you will just have to find the cd and give it try

---

