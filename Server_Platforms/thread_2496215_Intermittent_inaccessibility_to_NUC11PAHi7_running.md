---
title: "Intermittent inaccessibility to NUC11PAHi7 running 20.04 LTS"
date: 2024-03-19
forum: Server Platforms
---

### Post by jctong89 on 2024-03-19
Sorry I'm new here and not sure this is the right place to ask, and if there is a better place I would appreciate your direction there.

I have a NUC running 20.04 headless as my Plex and Roon media servers with files stored on my NAS that has worked flawlessly for nearly a year but 2 nights ago, a movie froze up on my iPad and I noticed that my NUC's yellow HDD activity LED kept blinking repeatedly with the blue power LED constantly on. Prior to this, I noted that the yellow HDD activity LED typically alternated between double blinks and a single blink with the blue power LED constantly on as normal. 

This repeated HDD activity LED blinking persisted several minutes so I tried to SSH into my NUC via PuTTY to troubleshoot, which timed out without the prompt to enter my login. Eventually I forced shutdown and when I started the NUC back up, I was able to SSH into it again and noted nothing out of the ordinary, except for 20-30 updates and upgrades available which I proceeded to perform.

The server seemed to run normally for a little while but has continued going in and out of a series of continuous HDD activity LED blinks, during which other devices would not see my Plex or Roon server and my desktop would not be able to SSH to it, although it still shows up as an attached device on the network with the same static IP on the router management page. Between this point and its stable operation just 3 days ago I have added 7-8 movies and have not changed the frequency of any of the file scanning functions on Plex (once per hour).

Would anyone have some advice how I might be able to figure out what is causing this frequent inaccessibility? I'm noticing maybe 8-10 dropouts a day and have no idea how many times this is occurring overnight.

If it's of any use for troubleshooting, the following is installed in my NUC:
1TB Samsung 980 Pro PCIe4.0 NVMe M.2 SSD
32GB Crucial DDR4-3200MHz RAM

If you require any further information please let me know and I greatly appreciate any and all help you guys can provide!

---

### Post by MAFoElffen on 2024-03-19
Have you checked the filesystem integrity? (if ext4, then fsck)

On my server that has my media for Plex... and my media files are on its own disk, separate from the OS, and other data. (Which are also on separate disks...) I think my media storage is around 7TB right now. I have that all backed up.

I go by a rule of thumb of trying not to have a single point of failure. Too many years of having to put out fires.

---

