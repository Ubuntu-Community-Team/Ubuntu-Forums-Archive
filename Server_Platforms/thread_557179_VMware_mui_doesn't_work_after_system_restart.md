---
title: "VMware mui doesn't work after system restart"
date: 2007-09-22
forum: Server Platforms
---

### Post by fernando_lopes_jr on 2007-09-22
I have successfully installed vmware server and mui on my Ubuntu server but each time i restart the server the mui stop's working it's the latestet version 1.0.4 Can sameone give me a hand with the problem.
Thanks

---

### Post by PilotJLR on 2007-09-22
This is a known issue... if you run the script on the below page on each boot (like thru rc.local), then it fixes the problem:
[http://opensourceheaven.net/?p=217](http://opensourceheaven.net/?p=217)

---

### Post by fernando_lopes_jr on 2007-09-22
The m8 for the help :D

---

### Post by AnRkey on 2008-03-13
> **PilotJLR said:**
> This is a known issue... if you run the script on the below page on each boot (like thru rc.local), then it fixes the problem:
[http://opensourceheaven.net/?p=217](http://opensourceheaven.net/?p=217)

Thanks, that fixed my right up!

R

---

