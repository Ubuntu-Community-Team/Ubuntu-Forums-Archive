---
title: "DISPLAY=:0 gnome-terminal &amp; not opening terminal in Ubuntu 18.04"
date: 2019-07-17
forum: Ubuntu, Linux and OS Chat
---

### Post by mehsham on 2019-07-17
In the earlier versions, I was able to open a terminal session in the Ubuntu environment using ssh protocol via putty. I noticed that once I upgraded to graphical gui Ubuntu 18.04 DISPLAY=:0 gnome-terminal & or DISPLAY=:1 gnome-terminal & does not open a terminal session in the Ubuntu. These instructions do not return an error however it doesn't do anything either. This is scenario:
- Using windows computer via putty I ssh into Ubuntu computer
- I then run this command nano DISPLAY... command
- I am expecting in the remote computer the ssh terminal should pop-up but it does not. 

Your help is greatly appreciated.

---

### Post by TheFu on 2019-07-17
Is your Windows desktop running an X/Server?
I understand that putty has X-Forward capabilities now, is that enabled for the specific connection?
You shouldn't need to touch the DISPLAY environment variable.  Putty+ssh should handle that for you.

Just saw an article specifically about this somewhere today.

Of course, if you are doing a Linux desktop with X/Windows running (I don't know if Wayland works or not) to a remote server, then you can just do something like this:
```
uxterm  -sb -geometry 80x25+820+60 $XTERM_OPTS -e ssh -X userid@remote-server-name
```
Which terminal you use is completely up to you.  I've never used gnome-terminal.

---

