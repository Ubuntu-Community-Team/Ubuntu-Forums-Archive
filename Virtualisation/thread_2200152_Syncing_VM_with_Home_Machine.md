---
title: "Syncing VM with Home Machine"
date: 2014-01-17
forum: Virtualisation
---

### Post by ghatt on 2014-01-17
I am fairly new to Linux, just started using Xubuntu about two or three weeks ago. I am a full-time student and use Xubuntu at school with VMWare player with a VM I created; the problem is, it is becoming aggravating trying to keep both systems configured as I like them. I was wondering if anyone could think of any simple way I could syncronize my VM with my home machine. My home machine uses a 105Gb SSD, 25 for /, 8 for Swap and the rest for /home. (I have a 1TB HDD storage partition for Storage). Any suggestions or recommedations would be greatly appreciated!

 - Greg

---

### Post by TheFu on 2014-01-17
"Simple way" is subjective.

I don't use vmware-player, but other VM tools will export an appliance that can be imported into a different machine running the same VM tools. The issue with this is that total storage INSIDE the VM is involved.

Another option is to synchronize your $HOME between the systems. That is where personal settings are stored. Be certain that the same programs are installed on both sides.  Check my signature for links on how to do that via backups and lists of programs.

I've been using the same VMs since 2008 and only have 15G total for my primary desktop. It holds settings and documents, NOT media. I do web-app development in that storage too. Plenty of room. Media like audio and video files are stored on the network - OUTSIDE the VM(s).  
The key to having great VMs is allocating exactly what is needed, not more. That applies to CPU, RAM, swap and storage.

Hope these ideas are helpful. Perhaps a few others will come up with better ideas.

---

### Post by ghatt on 2014-01-18
That is helpful actually. Mostly I use the Eclipse IDE to work on Java at school and while some of the settings are stored in the workspace, many are not. After reading your post I'm starting to think I made my /home directory on my physical machine too big. I guess I could shrink it with a partitioning tool. Since I have your attention TheFu would you have any recommendations for creating symbolic links? I think that's what it's called; what I'm trying to do is having my folders in my /home directory point to the storage drive I have mounted at /media/storage. For example, I have a directory called "/media/storage/Documents". It's possible to have the folders in my /home directory point to these directories?

---

### Post by TheFu on 2014-01-18
Yes, but ... there are many caveats.

---

