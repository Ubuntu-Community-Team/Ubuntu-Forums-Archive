---
title: "Network is Bridged but Bitdefender can't connect"
date: 2015-01-08
forum: Virtualisation
---

### Post by Rick St. George on 2015-01-08
Running WinXP-32 in Oracle Vbox and using "Bridged Adapter" for internet setting. Connection OK and able to connect ....

Except BitDefender can not "Login". Using WinXP Firewall. 

I know, you'll probably ask - Why use an AntiVirus program? Because it is Windows, and just for precaution!

Any help appreciated.
Thanks,
Rick

---

### Post by TheFu on 2015-01-09
No, I was thinking - "Are you crazy? XP hasn't been patched in 8+ months!"  The only safe way to run WinXP is without ANY networking at all.

However, it is hard to help without any data at all.  So, how about posting some useful data from the host and guest OSes like ifconfig, route, ipconfi, route and bridge settings?  Firewall settings for the host and guest might be nice too.

---

### Post by Rick St. George on 2015-01-09
Yeah - I know, but I refuse to pay for or give money to Microsoft so Gates and Soros can continue their genocide agenda. Neverheless, I need a windows platform to run my Trading Software (MetaStock) and Live Trading Platform from my broker. 

I believe I have a working compromise. I installed BitDefender in Ubuntu. Now it can scan everything, instead of having it inside the Vbox within WinXP.

Here is how I did it.

> 
sudo sh -c 'echo "deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free" >> /etc/apt/sources.list.d/bitdefender.list'

wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc)

sudo apt-key add bd.key.asc

sudo apt-get update

sudo apt-get install bitdefender-scanner-gui

REBOOT.  

BitDefender crashes right after the scanning engine is initialized. In  order to fix this error you will need to copy and paste this into  terminal:

> 
do touch /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64

sudo ln -fs /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64 /opt/BitDefender-scanner/var/lib/scan/bdcore.so

sudo bdscan --update

This does not specifically solve the problem posed in my original question, but it solves the issue. After install and Scan - it found 5 trojans and viruses.
I will consider it, and click it - - - SOLVED.

Thanks Fu!

Rick

---

