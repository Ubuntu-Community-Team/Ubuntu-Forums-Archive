---
title: "Hardware monitoring - HP Proliant server"
date: 2007-01-24
forum: Server Platforms
---

### Post by NigO on 2007-01-24
We are installing an ubuntu-based system, Dapper 6.06 LTS with a 686-smp kernel on an HP Proliant DL380 G5.

Most of it has gone smoothly, but system sensor monitoring is hitting a brick wall!

It seems lm-sensors etc are not suitable for the HP hardware (no sensors detected), so I have tried installing the HP monitoring software (openipmi, hpasm).  This comes in rpms, I have used alien on the SuSE 10 and RHEL 4 packages to produce debs.  

Does anyone have a note of what worked for them, there are so many error messages appearing at the moment that it seems hopeless!

I'd like to be able to monitor temperature, no other features needed at this stage, any pointers to a better method would be welcome!

---

### Post by phillips321 on 2007-08-23
[not sure if ur still looking for a solution but i got this working fine, please see here]("http://ubuntuforums.org/showthread.php?t=521911")

[http://ubuntuforums.org/showthread.php?t=521911]("http://ubuntuforums.org/showthread.php?t=521911")

---

