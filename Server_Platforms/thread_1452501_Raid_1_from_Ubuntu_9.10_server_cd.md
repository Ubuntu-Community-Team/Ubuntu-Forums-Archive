---
title: "Raid 1 from Ubuntu 9.10 server cd"
date: 2010-04-12
forum: Server Platforms
---

### Post by badboy_2083 on 2010-04-12
I am still relatively new to Ubuntu I switched back in October 09 and setup a dual boot with Vista and Karmic on my laptop. I only went back to Vista twice since then and can't wait to install lucid lynx by itself end of this month.

Right now I'm trying to get more familiar with server and I am trying to setup raid 1 following the instructions to do it from the cd here: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID). For Ubuntu Server 9.10

However once it seems like I have the partitions and the raid device done and try to finish. I get an error message saying **"No root file system is defined**." I see my partitions say raid instead of  / for root file system. So I tried to change them and I get a message saying "**In use by software Raid device md0**."

So I am pretty much stuck. Any help will be extremely appreciated.

I also searched the forum and found different ways to setup Raid but none of the how to threads seemed to talk about doing it straight from the 9.10 cd and figure it might be beneficial to others to learn to do it from the cd as well.

---

### Post by badboy_2083 on 2010-04-12
Solved it by changing device #0 to use /. The order in which it presented itself is what seemed to have me confused.

---

### Post by matkosk on 2011-01-31
thanks for this thread, it took me long  time to fix it

---

