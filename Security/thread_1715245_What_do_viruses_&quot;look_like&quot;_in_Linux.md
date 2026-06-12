---
title: "What do viruses &quot;look like&quot; in Linux?"
date: 2011-03-26
forum: Security
---

### Post by Rachel_Eliason on 2011-03-26
I have read enough about computer security to know that viruses are platform specific and there are no Linux viruses in the wild. Since I use Ubuntu I am not too worried about my computer. However I am curious, what it would look like if I went to a website that had a Window's virus, or tried to download one? Would the website work at all? Would there be someway to tell that a windows virus was there?

I ask for two reasons:
My son goes to lots of gaming sites and sometimes they don't work right on Linux. (It's all he uses too. another generation of Linux user in the making.) I assume most of the time when a site doesn't work, it's using non open source plug-ins, but could there also be virus software that is screwing up because it can't load onto our Linux system? 

I am also writing an article for a local paper about computer viruses. It's not a technical paper, so it will be aimed at Windows users that aren't very technically knowledgeable. If I visit a site that has Window's viruses on it will I know and be able to warn my readers? 

Thanks in advance for any help.

---

### Post by Boondoklife on 2011-03-26
You prolly will not be able to tell as most of the web spread viruses  are done through activex, brower, or plugin exploits. These, for the  most part, do not exist in Linux.

Now there are plenty of destructive apps or scripts out there that  people will try to get newbies to run. kinda like the old windows
```
format c:\ /y
```
If a user happens to run some malicious code like this then they/you will know right away there is an issue.

---

### Post by HermanAB on 2011-03-27
Windows viruses look like programs that won't work on Linux - so they don't amount to anything at all usually.

Using Linux, you can browse to pretty much any web site and click things with wild abandon and nothing will happen.  So Windows viruses are pretty boring things on Linux.

---

### Post by handy on 2011-03-27
I always like reading your posts HermanAB. :D

& I've been reading them for a long time too. lol

---

### Post by dacoolio on 2011-03-27
I remember once I accidentally downloaded a Windows virus executable on Linux. I took one look at the filename (something like YouTubeDLTool.exe) and nearly laughed, since it was pretty obvious it wasn't kosher. I ended up scanning it with the online Anubis binary scanner, and it was some botnet malware. 

Long story short, binary based viruses are sort of funny when looking at them on Linux. Plugin and other web based ones will probably result in a crash of some sort, so they're a little more interesting I guess?

---

### Post by SeijiSensei on 2011-03-27
In general, downloaded files don't have the execute bit enabled by default, so even double-clicking them won't do anything either.  You can probably run a .exe file in Wine if that's installed, but it really can't do much either.  Often the virus falls over when it tries to manipulate the Windows Registry which is emulated in Wine.  At worst, you can just blow away ~/.wine, restore it from backups, and start over.

I've also had the "privilege" of encountering the "Antivirus 2010" trojan which uses Javascript to redirect your browser at close.  It opens another browser window and navigates to a website that looks like a Windows file manager box that finds allegedly finds hundreds of infections on your C: drive. (I believe it's just displaying an animated GIF.)  Where's my C: drive again?

---

### Post by Rubi1200 on 2011-03-27
> **SeijiSensei said:**
> I've also had the "privilege" of encountering the "Antivirus 2010" trojan which uses Javascript to redirect your browser at close.  It opens another browser window and navigates to a website that looks like a Windows file manager box that finds hundreds of infections on your C: drive.  Where's my C: drive again?

I also had something similar, just once. Quite amusing really.

---

### Post by Rachel_Eliason on 2011-03-27
Excellent information. Thanks everyone. :D

---

### Post by FrankenCub on 2011-03-27
The only viruses I've seen in any Linux system :

Your typical Windows Virus
[[IMG]http://i306.photobucket.com/albums/nn244/FrankenCub/Computer%20Issues/th_WindowsVirus.jpg[/IMG]]("http://s306.photobucket.com/albums/nn244/FrankenCub/Computer%20Issues/?action=view&current=WindowsVirus.jpg")

[SIZE=2]The scariest virus
[[IMG]http://i306.photobucket.com/albums/nn244/FrankenCub/Computer%20Issues/th_virus.gif[/IMG]]("http://s306.photobucket.com/albums/nn244/FrankenCub/Computer%20Issues/?action=view&current=virus.gif")

[/SIZE][SIZE=2]And your basic trojan/virus protection that you might find useful 
[[IMG]http://i306.photobucket.com/albums/nn244/FrankenCub/Computer%20Issues/th_anti-virus.jpg[/IMG]]("http://s306.photobucket.com/albums/nn244/FrankenCub/Computer%20Issues/?action=view&current=anti-virus.jpg")

:lolflag:
[/SIZE]

---

