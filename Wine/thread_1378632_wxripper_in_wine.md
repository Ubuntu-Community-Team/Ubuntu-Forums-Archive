---
title: "wxripper in wine"
date: 2010-01-11
forum: Wine
---

### Post by 2LSS on 2010-01-11
Hi, 
I use wxripper in windows to back up my xbox 360 games. I would use xbox backup creator but I don't have a compatible drive and the wxripper method works fine for me. The only problem is that I have to boot into windows whenever I want to back up a game, so I want to try to get wxripper to work under wine. Wxripper requires .net framework 2.0 so I installed mono 2.4.2.3 using winetricks. Everything went smooth but when I ran wxripper, it started ok but never opened the gui. There were no errors and it continued to run but without any window/ gui. Here is the terminal output.
[http://pastebin.com/f3b36255 ]("http://pastebin.com/f3b36255")

Here is what was running under system monitor
explorer.exe     sleeping
mono.exe         running
winedevice.exe   sleeping
winedevice.exe   sleeping
crypserv.exe     sleeping
services.exe     sleeping
wineserver       sleeping
wxRipper.exe     sleeping

I'm running wine version 1.1.36 and the os is set to windows xp. I tried searching around for a solution but couldn't find anything related. 
Here is the wxRipper site (I think)
[http://gael360.free.fr/]("http://gael360.free.fr/")
I know mono has a debug mode but I am not sure how to run it from wine. If I figure it out I will post that as well.
If anyone has any ideas they would be appreciated. ;)

---

