---
title: "map network drive to specific folder"
date: 2008-12-01
forum: Server Platforms
---

### Post by rico2k_uk on 2008-12-01
I have installed Ubuntu server onto an old laptop to run as a file/media server. So far so good! i have got twonky media installed and running (although had to install it with an older version first then upgrade before it would work). However, I have 2 NAS drives (a WD MyBookWorld 1tb and a Freecom Network Drive Pro 1tb). I have them connected to the laptop via a dedicated network switch. However, on the server i have 4 folders shared using samba - Music, Videos, Pictures, Documents. What I want to do is have these folders mapped to a network drive folder, so i can click on any of these via a vista client (which has mapped these drives) or so twonky media can see them and stream contents to my xbox.

Is this actually possible, or do i need to dissasemble these NAS drives and fit them into a sata caddy?

---

### Post by zotkop on 2008-12-01
Can't you mount them in the samba directory?

---

### Post by rico2k_uk on 2008-12-01
errr... how? lol! i'm newbie at all this! i managesd to mount it by following a guide online, but when i do - ie make the music folder on the NAS drive to be mounted on the music folder on the server, the directory says i dont have access any longer (thats including root!)

---

### Post by ilrudie on 2008-12-01
As long as the NAS devices get mounted to the same place every time you can simply soft link them like so:
```

ln -s <path_to_NAS_Directory> <path_to_SAMBA_Directory>

```

---

### Post by rico2k_uk on 2008-12-01
tried that - couldnt get it to work...

the directory on the server is under /mediaserver/Music

the one on the network drive is //netdrive2/Music - however on putty is more like /shares/internal/SHARED/Music

i need the share setup permanently at bootup of the server.

i have a password/username to access the network drives as well.. completly perplexed at getting this to work! :D

---

### Post by ilrudie on 2008-12-01
For the soft/symbolic links to work the NAS share will have to be mounted.  Once its mounted properly they will work.  You link the mount point (/shares/internal/SHARED/Music) not the network connection string(//netdrive2/Music which looks like its windows shorthand for SAMBA although windows uses \\<server>\<path> for its shorthand).  If you don't know how to get your NAS to mount reliably to the same location you should post what protocol (which I'd guess is SAMBA) you are using and ask for suggestions.

---

