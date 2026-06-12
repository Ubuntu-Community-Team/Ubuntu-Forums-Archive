---
title: "Samba - Ubuntu box will not open on Windows boxes"
date: 2010-02-18
forum: Server Platforms
---

### Post by Zidaps on 2010-02-18
Hi,

I've been trying to fix this problem for over a month, on irc chats and searching google for forum threads, all leading me in different directions all bringing me nowhere.

In trying to connect from my Windows machine I get the following error:
> Windows cannot access \\ubuntu

Check the spelling of the name. Otherwise, there might be a problem with your network. To try to identify and resolve the network problems, click Diagnose.Well, clicking "Diagnose" is a huge waste of time.
I've paste binned by /etc/samba/smb.conf file and it can be found below -

smb.conf here: [http://pastebin.ubuntu.com/379518/](http://pastebin.ubuntu.com/379518/)

Also, when I am on the Ubuntu machine attempting to browse the machines on the network and go to Places >> Network >> Windows Network
I get the following error:

> Unable to mount location

Failed to retreive share list from serverIf there is anyone out there who knows how to resolve this issue. Please help. Thanks.

---

### Post by suseendran.rengabashyam on 2010-02-19
Hi,

An active thread regarding SAMBA and Windows Share, [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Hope this helps.

---

### Post by Zidaps on 2010-02-20
Hi, I've tried that link and came up with nothing but trouble... Winbind causes my machine to freeze and affects the file manager so that it no longer responds.. See this post I left in this thread. Someone else was having similar issues after installing Winbind.

[http://ubuntuforums.org/showthread.php?t=1406033](http://ubuntuforums.org/showthread.php?t=1406033)

I take it that without Winbind, windows machines will not be able to open/mount a connection with my linux machine? All I want to do it share files and my printer... :(

---

