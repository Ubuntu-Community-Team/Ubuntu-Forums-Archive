---
title: "Ubuntu One for Windows is quite the resource hog"
date: 2011-10-26
forum: Ubuntu One (CLOSED)
---

### Post by DeadWolf on 2011-10-26
I use Ubuntu at work and on other devices. I take advantage of Ubuntu One as it is a nice way to transfer files back and forth with out the need of a thumb drive. My desktop at home is a custom built gaming rig that I had recently installed the Ubuntu One for Windows on. I must say that it is a great application and it is nice to be able to save a document at work and automatically have it at home. I couldn't ask for a better service.

My problem comes with the thin client. This desktop has a Phenom II x6 Processor OCed at 4GHz and 8GB of RAM. I had noticed that my desktop would idle rather high and I just that it was because I have a lot of things open. I don't get any kind of slow down nor lag so I didn't think too much of it. It wasn't until I restarted and decided to check the resource monitor and notice that my CPU was idling at 34% and RAM at 44% with nothing open. I check to see what was hogging so much and it turns out that the Ubuntu One Daemon was right there at the top. I killed the application and uninstall it. With in seconds my CPU idles at 1% and RAM at 17%. A pretty significant change if you ask me.

Is any one else experiencing issues with this? I don't think it is normal for this application to have 2GB of RAM dedicated to it.

---

### Post by exsysprog on 2011-10-29
U1 Windows client 2.0.1 running on windows 7 : i3 dual cores at 2.4GHz with 4G memory laptop.  Machine idles at 25% cpu utilization by the sync daemon and 2Gb working set memory.  Client stuck at (something to the effect of) file sync starting.  Client sits there and syncs nothing.  Not sure how to locate logs and stuff on the windows bx to try to find better diagnostic / debug information

---

### Post by CaptainFuzzyFace on 2011-10-31
I've Ubuntu One SyncDaemon (2.0.1.0) running on Windows 7 and it is endlessly eating memory. I let it get up to 1.5gig before I killed it. It always does this and generally takes 25% CPU whilst doing so.

The client window reports "File Sync Starting..." throughout.

I think that also counts as being a little resource hog...

---

### Post by guhcampos on 2011-11-01
I can confirm this. 1.5GB of memory use for absolutely nothing. I believe there are serious memory leaks or worse.

---

### Post by alco75 on 2011-11-02
> **DeadWolf said:**
> I use Ubuntu at work and on other devices. I take advantage of Ubuntu One as it is a nice way to transfer files back and forth with out the need of a thumb drive.

Give Dropbox a try? Since moving to Xubuntu and signing up for Spotify Premium, I've abandoned Ubuntu One entirely.

---

