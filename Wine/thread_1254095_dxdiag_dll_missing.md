---
title: "dxdiag dll missing"
date: 2009-08-30
forum: Wine
---

### Post by sunshine1 on 2009-08-30
picture 

and the agp texture accerelation not available

---

### Post by sunshine1 on 2009-08-30
i allready have installed the latest graphic card and i reinstalled direct x

---

### Post by sunshine1 on 2009-08-30
why me every body got too many answers until now

---

### Post by DeMus on 2009-08-30
> **sunshine1 said:**
> why me every body got too many answers until now

You expect to get an answer in 10 minutes about a Microsoft problem in a Ubuntu forum?
Be patient, not every body is 100% of the time on-line to help you. We are all volunteers here, trying to help others without getting paid just because we like to do so.
Can you figure out in Windows which file you are missing and copy it over to the Wine directory?

---

### Post by sunshine1 on 2009-08-31
thanks for answer you mean downoad it

---

### Post by LiamWilson on 2009-08-31
What is the full name of the file that is missing? Could you expand the 'name' column and tell us what the full file name is please?

---

### Post by sunshine1 on 2009-08-31
/usr/bin/wget [http://howto.landure.fr/gnu-linux/installer-directx-9-0c-avec-wine/ddraw.dll]("http://howto.landure.fr/gnu-linux/installer-directx-9-0c-avec-wine/msctf.dll")
    --output-document=$HOME/.wine/drive_c/windows/system32/ddraw.dll
i used this to download and that what happened

---

### Post by sunshine1 on 2009-08-31
i reinstalled direct x from here [http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine](http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine)

and this happened again









i dont know how to get the full name of the dll

---

### Post by LiamWilson on 2009-08-31
To get the full name of the DLL, where it says 'name' at the top of the column, the gap between that and 'version' drag that so the column gets bigger.

---

### Post by ackanao on 2009-08-31
It's not recommended nor supported by WineHQ to install DirectX in Wine - please read this:

[http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2]("http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2")

Almost 100% of DirectX 9 is already implemented in Wine - you'll render your Wine setup useless if you choose to install native DirectX libraries.

---

### Post by sunshine1 on 2009-08-31
the name is ddrawex.dll

---

### Post by sunshine1 on 2009-08-31
this what i read what can i do then 

**8.1. Does Wine support DirectX?  Can I install Microsoft's DirectX under Wine?**

 Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway. 
[IMG]http://wiki.winehq.org/wiki/winehq/img/alert.png[/IMG] **If you attempt to install Microsoft's DirectX, you will run into problems.** It is not recommended nor supported by Wine HQ to attempt this. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Additionally these DLLs are now part of the Wine tree. So, as Wine improves these DLLs will only become less relevant. 
That said, there are some guides out there which describe how you can install Microsoft's DirectX. I reiterate: It is not recommended nor supported by Wine HQ to attempt this. Furthermore it is considered off topic in Wine HQ support mediums (such as the forums). Please use a clean Wine configuration folder before seeking help. (You may need to rm -rf ~/.wine and re-install your Windows applications.)

---

### Post by sunshine1 on 2009-08-31
what to do the name of dll was ddrawex.dll

---

### Post by sunshine1 on 2009-08-31
thereis no missing dll i have downloaded it inyo system 32 and its fine now the problem is 

agp texture accerelation not available

any help

---

### Post by 00arthuryu on 2009-08-31
I really have to ask, but why are you installing DirectX?
Or run Dxdiag? Dxdiag is a diagnostic tool for Windows, not Linux, it will not work.
And natively, Ubuntu/Linux will not run DirectX games.
If you're going to try and play DX Games on wine, then go for it, There is no need for Dxdiag, and use wine's application database to check for compatibility.

---

### Post by sunshine1 on 2009-08-31
do you mean that there is another program like dx in ubuntu if that what you mean please give me the link

---

### Post by 00arthuryu on 2009-08-31
Wine is a DirectX compatibility layer for you to run Windows programs on Ubuntu
There is no alternative to DirectX on Ubuntu that can run windows games.

I am still failing to understand what you are trying to do.

---

### Post by sunshine1 on 2009-08-31
i want to run conquer i=online game and that is what happen i know how to open it from athread in this site but its problem that 
agp texture accerelation not available

i think you want me to unitall dx but how ? and will the game run without dx?

---

### Post by 00arthuryu on 2009-08-31
can you find on [http://appdb.winehq.org/](http://appdb.winehq.org/) ?
If its in there, theres probably instructions on what works and what doesn't work.

---

### Post by sunshine1 on 2009-08-31
it counld work on wine see here [http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=distribution&iId=527&sAction=view&sTitle=View+Distribution](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=distribution&iId=527&sAction=view&sTitle=View+Distribution)

---

### Post by bl33d on 2009-08-31
you can install directx and dxdiag under wine if you do it right. the problem is people just read some old guides and think that is the answer. you dont have to install directx for a lot of games, but in the long run it makes more sense to. it will save you endlessly hunting for d3dx9_XX.dll when a certain game needs it.

---

### Post by sunshine1 on 2009-08-31
tell me how to unintaled it and installed it well

---

### Post by NightMKoder on 2009-08-31
> **bl33d said:**
> you can install directx and dxdiag under wine if you do it right. the problem is people just read some old guides and think that is the answer. you dont have to install directx for a lot of games, but in the long run it makes more sense to. it will save you endlessly hunting for d3dx9_XX.dll when a certain game needs it.

Which is why instead of winetricks lets you just extract those dlls from the archive and not install the whole thing:

d3dx9         MS d3dx9_??.dll (from DirectX 9 user redistributable)

Consider using that instead of the full blown directx install.

---

### Post by bl33d on 2009-08-31
> **NightMKoder said:**
> Which is why instead of winetricks lets you just extract those dlls from the archive and not install the whole thing:

d3dx9         MS d3dx9_??.dll (from DirectX 9 user redistributable)

Consider using that instead of the full blown directx install.

ive tried winetricks before. i find my way to be much better :P

---

### Post by hikaricore on 2009-09-01
> **bl33d said:**
> ive tried winetricks before. i find my way to be much better :P

Please stop poisoning threads with your concept of directx installation fixing everything, it's really unneeded and misleading to common users.

---

### Post by bl33d on 2009-09-01
> **hikaricore said:**
> Please stop poisoning threads with your concept of directx installation fixing everything, it's really unneeded and misleading to common users.

I didn't say it fixed everything, so stop putting words in my mouth.

---

### Post by sunshine1 on 2009-09-01
hey dont make afight now direct x is ok no dlls has problem but the game when i open it it told me to open dxdiag

---

