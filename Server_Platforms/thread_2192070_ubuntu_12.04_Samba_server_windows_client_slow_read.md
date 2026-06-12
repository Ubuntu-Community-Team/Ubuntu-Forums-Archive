---
title: "ubuntu 12.04 Samba server windows client slow read performance"
date: 2013-12-05
forum: Server Platforms
---

### Post by WPtE on 2013-12-05
I've just set up a new little homeserver built with a intel NUC.
It's quite a fast little machine, newest haswell I5 cpu :)

I decided to install ubuntu 12.04 lts for the lts. I'm very familiar with the ubuntu server anyway.
during the installation I checked samba server because I want to share files in my home network.
I left all settings default and logged in with my windows 8.1 machine, to end up in my home directory, cool.

Write speeds are amazing, 110MB/s easily, but when I try to copy something from the server to my pc it's awefully slow!
Well, compared to the 110MB/s it's just rubbish. At the moment I'm able to read 21MB/s.

So I decided to fiddle around with the samba server settings: _tcp options, oplock configuration, server signing_ nothing seems to work.
I double checked that the server wasn't too slow, but the samba process only uses about 3% cpu during read.

I tried upgrading to samba 3.6, since the default samba is 2.x.
I used the packages from enterprise samba: [http://www.enterprisesamba.com/samba-packages/ubuntu/](http://www.enterprisesamba.com/samba-packages/ubuntu/)
All installed, working fine with the same configuration file.
Unfortunately I still have the exact same performance as before.

Does anyone have a solution to improve the read speeds?

---

