---
title: "Home Server Ideas"
date: 2012-01-04
forum: Server Platforms
---

### Post by bubylou on 2012-01-04
I recently freed up an old desktop in my home and decided to turn it into an Ubuntu home server. So far i have Samba, uShare (Movies on Xbox), and Deluge running on it. All desktops run windows 7 and i dual boot with Ubuntu 11.10 desktop. I was wondering what else i could use this old dell for. I was looking at firefly for iTunes and debating whether or not to change ushare for something else, since its rather basic. Let me know what you think about my current setup and things to add.

Hardware-
Pentium Dual core (need to double check)
1.25 gb ram
75 gb hdd

PS: i get a weird graphical error on screen after the grub menu when it starts to boot. Installed fine, Grub menu's fine, just Ubuntu itself the text is unreadable blocks. Not really a problem since i use putty for everything.

---

### Post by Cookieh on 2012-01-04
For a high speed home server would use bigger hard drive but your setup sounds fine for Ubuntu, but for server it self, I have no idea as I am running all my servers through Mac, works for me...

---

### Post by 2F4U on 2012-01-04
What graphics card is installed? Sometimes it helps to put nomodeset in the grub kernel boot parameters.

With respect to what you can do with your server, you could make backups of your Windows machines to the server. But that would probably require more hard disk space. I've put all my music on the server and let the clients access it through Samba. I've even configured iTunes to not have a local library but instead access the music on the server.

---

### Post by samosamo on 2012-01-04
Could you tell me more about using uShare for movies on your Xbox? I have always wanted to play downloaded movies to mine.

---

### Post by bubylou on 2012-01-05
ushare uses upnp so that your xbox recognizes it so that you can stream movies (or any other media) straight to your device. its really easy to setup just install it and configure the file, restart and your done.
let me know if you need any help setting it up.

---

### Post by bubylou on 2012-01-05
might look into editing the grub if i have time. Backups is over kill because im not really going to put any money into this old system. Im just happy it still runs so well. Just wondering if anyone knows of any good home server apps i should try. also he only problem with you share is that it doesn't let me filter threw my music very well. (artist, album, etc.)

in terms of streaming music i also found [subsonic]("http://subsonic.org/pages/index.jsp") which i think is more than my server can handle. would be kind of nice though since i really don't care for itunes.

---

