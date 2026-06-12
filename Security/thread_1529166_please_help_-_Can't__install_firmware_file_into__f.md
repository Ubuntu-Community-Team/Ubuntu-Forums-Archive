---
title: "please help - Can't  install firmware file into  file system - not accessable"
date: 2010-07-11
forum: Security
---

### Post by robberto on 2010-07-11
Hi

I'm only just starting out with the Linux ubunto 10.04 OS after yeas of wasted time on Microsoft os's,

I hope I'm posting this request for help in the right forum thread, if not please accept my apologies, 

I have tried searching everywhere for help in installing a firmware file into the File System / lib / firmware directory and each time I get an access denied result. 

The file is for a DVB board and I have managed to track down the right Linux fw file for this particular piece of equipment, 

Could some kind helpful person either explain how to get this firmware file into the Root System directory or even send a link to another site that deals with this sort of problem

I've downloaded all the programs via the Ubuntu Software Center that should be able to perform this task however all to no avail.

The reason why I posted this thread in this forum board is that it (in my own personal opinion which may be wrong) seems to me to be a security problem, 

Thanks for reading 
and again if I have posted this in the wrong directory please accept my apologies 

:)

---

### Post by Bachstelze on 2010-07-11
```
sudo cp firmware.file /lib/firmware
```

---

