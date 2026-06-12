---
title: "What the hell does this mean!? :/"
date: 2008-10-07
forum: Server Platforms
---

### Post by nedge2k on 2008-10-07
Sorry I couldn't give a more descriptive title but I've no idea what's going on here!

Pictured is my Ubuntu 8 Server, VMWare install. Recently it's started doing this for no reason. Anyone know how I can fix it?

I've tried searching the various strings outputted but not got any closer to an answer. Usually it doesn't result in a panic, just keep outputting text. Only way to stop it is a reboot but on the occasion it panicked, I the fs then corrupted!

---

### Post by nedge2k on 2008-10-08
bump

anyone?

---

### Post by smileypaul on 2008-10-08
Interesting, its random? or when doing somethign specific?

---

### Post by windependence on 2008-10-08
Looks like hardware to me. What version of VMware are you running. I take it if you are running Ubuntu it must be VMware Server. You may want to look at ESXi, it's free and much more stable and efficient. How about the guests, what OS are they and are they 64 bit or 32 bit? 

From your description it appears this is on the host system and not the guests, correct?

-Tim

---

### Post by nedge2k on 2008-10-09
Hi guys,

Yeah it was a random thing and yep vmware server. The host OS is SBS 2003 running on an Opteron 64 server. The only guest is the x86-x64 Ubuntu install - i'm using it for web development.

I may have fixed the issue by re-installing the Kernel. However, not long after I did that, I got a huge FS corruption that wiped everything out when I fsck'd it. Luckily I was able to just roll back to the previous day's backup and but I lost everything I did that day.

Will have a look at EXSi, cheers :)

---

### Post by windependence on 2008-10-09
FYI, it would be much better if you have to run VMware Server to use a Linux host rather than Windoze as it will be much more stable that way. 

I have one Dual Opteron 64 box running Server with 4 64 bit guests. This one has been running  fine for two years. The host OS is SuSE 10.3 though.

ESXi is really the way to go if your hardware supports it. It won't load on IDE drives, SATA and SCSI or fiber channel and iSCSI only.

-Tim

---

### Post by promodus on 2008-10-09
Was this VM always on this machine?

Did you take it from an intel machine to this machine? Was it ever suspended?

---

### Post by nedge2k on 2008-10-10
No, it was a fresh install and hasn't been suspended.

The problem has now returned. It was fine yesterday but when I tried to ssh into it just now, it wouldn't connect so I RDP'd into the host and rebooted. Everything was fine for a minute but then apache returned internal server misconfiguration error and the vmware console had all that text scrolling in the window again :( Rebooted again and the fsck failed!

---

### Post by promodus on 2008-10-10
what version of vmware? 
Do you mind posting your .vmx configuration of that VM ?

---

### Post by nedge2k on 2008-10-10
right, i *think* its fixed now.

re-installed the kernel again and fsck'd the fs in recovery shell

time will tell...

---

