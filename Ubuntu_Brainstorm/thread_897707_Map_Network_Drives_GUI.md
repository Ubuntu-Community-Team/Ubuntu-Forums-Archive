---
title: "Map Network Drives GUI"
date: 2008-08-22
forum: Ubuntu Brainstorm
---

### Post by NTolerance on 2008-08-22
Persistent network mounts are useful for obvious reasons.  The current method is to hand-edit /etc/fstab.  

My personal application is that I stream MP3s and other media from a central server on my LAN.  Manually mounting the shares via Nautilus is not convenient because music players and other software depend on a data directory always being available.  If you run the program before the network volume is mounted you will have problems and may even lose metadata that's collected by various music applications.

The current fstab method is not ideal for two reasons.

1.  Each type of network share (SMB, NFS, SFTP, etc) has a different syntax in fstab.  This can be quite confusing and is very error-prone.

2.  Because of problem #1, testing fstab settings is tedious because of semi-necessary reboots.  Sure, you can mount things manually via the command line without a reboot, but to truly test your changes you need to reboot the machine.

A simple GUI available via context menu in Nautilus to permanently mount a network share would be great.  If a directory is visible in Nautilus, the type of share and credentials to access it are already known, so a GUI could take this information and store it in the proper place.

---

### Post by zekopeko on 2008-08-24
for mp3 streaming (DAAP) try [http://www.fireflymediaserver.org/index.php](http://www.fireflymediaserver.org/index.php)

it's called mt-daapd in the repos

---

### Post by NTolerance on 2008-08-28
Thanks for the suggestion.  I think Exaile has a DAAP client, but I have some other purposes for having all filetypes available via a persistent share.  

In Windows the "map network drive" feature works quite well and is extremely easy to set up.  Would be great to see this feature in Ubuntu.

---

### Post by littlethingsdontkill on 2008-08-29
i think what NTolerance is refering to is that mapping network drives is one of the last aspects that confusees soneone who does not want to know how the operating system works (just a user). 
For those users it would be very handy to present a consistent way to find and attach e.g. an NAS drive to your system without any typing. (Not that I believe the explanations on the web to do this are hard to understand). 
One major problem I have encountered is that my router, where the NAS drive (a buffalo linkstation) is attached, changes the local IP adress depending on how many of these drives are switched on. One is smb one needs cifs (correct me if i am wrong) to be mounted. But they have a name assigned to them. It would be very cool to have a tool that recognizes the drive by some unique feature (name?) and than takes care of this mounting process. (Something in the line of a message popping up:"found new network drive with name xyz, want to mount/look at it?")
right now I mostly change the entries in the Fstab file depending which drives I have switched on, kind on a pain....

---

### Post by Guilden_NL on 2008-09-14
And I say "oh yeah!"  I just nuked Samba because I only have one client that has Windows on it and it runs Linux 99% of the time.  So went to set up NFS (I used to do this 12 years ago under HPUX and Solaris) but it's a royal PITA to set up via terminal on 6 clients without making mistakes, while double and triple tasking in several rooms.

GUI is good for a visual check and doesn't require me to run around to various rooms with a Post It note full of information to set up the clients.

Making noobs get into the intricacies of NFS is defeating the purpose of Ubuntu bringing Linux to the masses.  Heck I know how to do it, but I'll take a GUI set up over terminal any day.

---

### Post by Ice Dragon on 2008-11-10
Agreed, things like this need to be done through 100% GUI.

---

