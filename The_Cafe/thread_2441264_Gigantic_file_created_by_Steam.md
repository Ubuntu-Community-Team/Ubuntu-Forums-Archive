---
title: "Gigantic file created by Steam"
date: 2020-04-21
forum: The Cafe
---

### Post by mastablasta on 2020-04-21
tried to turn off the PC and go to bed, but it didn't want to.

I got a disk full message. the disk being full prevented the shutdown. there should still be about 680 GB free space left. there are only a few games installed on this drive, while data is on another disk.  i deleted some files here and there, emptied trash, but it was still kind of full and i could barely do anything. I thought the disk went bust. so i started with some basic diagnostic. I then tried to get more space and deleted some larger files. got 500 MB of space, but the disk soon filled back up.
looks like the file kept growing, growing, and growing... until the disk was full. 

so then i reboot in some way and somehow managed to get back in. it showed 2 MB free. anyway a bit of head scratching, more cleaning and few commands later i found this:

```
username@blackmesa:~$ du -cha --max-depth=1 /home/username/.steam | grep -E "M|G"
9,3M    /home/username/.steam/steamui
256M    /home/username/.steam/package
202M    /home/username/.steam/ubuntu12_64
28M     /home/username/.steam/linux64
4,0M    /home/username/.steam/clientui
58G     /home/username/.steam/steam
766M    /home/username/.steam/ubuntu12_32
2,5M    /home/username/.steam/legacycompat
25M     /home/username/.steam/public
4,4M    /home/username/.steam/friends
424K    /home/username/.steam/WINDOWSTEMPDIR_FONTCONFIG_CACHE
145M    /home/username/.steam/tenfoot
[COLOR=#ff0000]**677G** **   /home/username/.steam/error.log  **[/COLOR] <--- ?!
11M     /home/username/.steam/resource
27M     /home/username/.steam/linux32
1,7M    /home/username/.steam/controller_base
20M     /home/username/.steam/graphics
736G    /home/username/.steam
736G    total
```

it looks like it took it whole afternoon to get there. it was busy filling in lines until it was full. why would anyone design unlimited size log file and moreover, why would they set it by default?!

deleted the file and all is back to normal. just wanted to say i never saw such a large file on home pc. and it created and grew by itself. like some sort of sick malware :)

---

### Post by Shibblet on 2020-04-22
[https://steamcommunity.com/groups/SteamClientBeta/discussions/0/1743394605018860117/]("https://steamcommunity.com/groups/SteamClientBeta/discussions/0/1743394605018860117/")

[https://github.com/ValveSoftware/steam-for-linux/issues/6901]("https://github.com/ValveSoftware/steam-for-linux/issues/6901")

---

