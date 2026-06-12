---
title: "noob server questions"
date: 2007-04-29
forum: Server Platforms
---

### Post by nonewmsgs on 2007-04-29
ok i followed a lot of guides and installed a lot of the lamp services and even ftpprosomething, but now i am lost.  can i simply login with an ftp client? 
what are the problems i will come accross if i dont make a static ip? (i tried it once and i could no longer conect to internet.) can i play mp3s from the server without downloading them? (this and making my own server were two of the three main reasons i wanted to do this in the first place). 

i am a little lost, but i feel proud for doing as much as i have (even though it was a lot reading and just typing in the same things).

---

### Post by RichGuk on 2007-04-30
Hello,

If you setup your FTP server is setup correctly, I assumed you followed a guide you should be able to just connect with an FTP client to your Linux box using its IP (or, even the name of the box).

If you're attempt to connect to your box from the internet and you're behind a router then you might want to have static IP so your router can forward the ports correctly. When you set it up could you ping other computers on the network? Was it just the internet that was not working? You might want to check that your DNS was setup correctly.

If you're attempt to listen to MP3's from a Windows box, then look at some samba guides that will let you share folders for use on the network and will quite happily play your media over the network.

---

### Post by az on 2007-04-30
You can't reach your computer from the outside?  Do you have a residential high-speed connection?

If so, then you don't have a static IP address.  You can still reach your computer using dynamiic dns

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

