---
title: "Help to configure smartmontools for sometimes offline computer"
date: 2007-02-23
forum: Server Platforms
---

### Post by frafu on 2007-02-23
Hello,

I have installed smartmontools and need help to configure it. 

I would like it to automatically monitor 2 ata and 2 sata drives. Further, I want it to notify me if there is a problem with the disk. (I am only interested in the information whether the disks are ok or not). 

I have seen in smartd.conf, that you can have it send an email if there is something wrong. Unfortunately the computer is not always online; so I suppose that this is not an option. 

Further, the ubuntucomputer in question also partly works as a fileserver (it is headless), so how can I be alerted if there was a problem? For example when I connect remotely to it with vnc or when I open an xsession? 

Maybe I should also mention that my main machine is a MacOSX connected to the same lan. The ubuntucomputer and the mac are both not running 24h/24. There are periods of time during the day where they are both turned on, but there are also times where only one of the 2 machines is running. 

Could anybody please help me to configure smartmontools for it to cover my needs? 

Thanks in advance. 

Francesco

---

### Post by frafu on 2007-02-26
Maybe that the best solution is to have smartmontools put a file on the desktop when an error occurs. So I will see it the next time I remotely connect to it! The file on the desktop should then contain the log of the error. 

I tried to use the smart-notifier to see how it works, but was not able to make the test notification appear. Anyhow, maybe the solution with the errorlog on the desktop is better, or does the notification remain open until I remotely connect? 

Thanks in advance. 

Francesco

---

