---
title: "Where is my diskspace?"
date: 2012-10-15
forum: Virtualisation
---

### Post by Codeless on 2012-10-15
I installed a natty guest OS with virtualbox giving it 8gigs of hdd space (fixed) and I tried downloading to my desktop and theres no space available! where is my hdd space?

I had to download directly to the folder I share with my host OS, but where is my space on ubuntu?

thanks

---

### Post by Cheesemill on 2012-10-15
What size files are you downloading?
8GB isn't a lot of space for a full installation.

Can you post the output of:
```
df -h
```
(on the VM).

---

### Post by Codeless on 2012-10-15
> **Cheesemill said:**
> What size files are you downloading?
8GB isn't a lot of space for a full installation.

Can you post the output of:
```
df -h
```
(on the VM).

sure thing

Codeless@Pengu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.5G  4.3G  926M  83% /
udev                  1.3G  4.0K  1.3G   1% /dev
tmpfs                 495M  756K  495M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.3G  320K  1.3G   1% /run/shm
Shared                120G   74G   46G  63% /media/sf_Shared
/dev/sr0               53M   53M     0 100% /media/VBOXADDITIONS_4.2.0_80737
Shared                120G   74G   46G  63% C:UsersCodelessDesktopMagicBoxVirtualBoxShared
Shared                120G   74G   46G  63% /media/Shared
Codeless@Pengu:~$ 

8gigs was the recommendation... Why would the minimum be recommended? I chose fixed size because I heard there is a slight performance benefit.

My shared file is empty, what is that 74gigs? is that from my host OS? my laptop is a week old today it should be clean as a whistle.

I have a question. I'm using my guest OS for web browsing, I reload my ubuntu "safe" state when I'm done which only has chrome and iplist installed.

Will this practice protect me from malware? and I know this is probably a very silly question but if I download directly to my shared folder is my host OS safe?

provided of course I don't open it in my host OS and it has a virus attached to it

I'm not good with this stuff, could you explain it to me and any security issues

thank you

---

