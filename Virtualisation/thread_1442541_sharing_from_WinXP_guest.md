---
title: "sharing from WinXP guest"
date: 2010-03-30
forum: Virtualisation
---

### Post by capricornday on 2010-03-30
I'm sorry because i'm newbie here :)
I run Vbox on my Jaunty and have a WinXP guest on it.
There is no problem to share my folder (/home/myname/toXP) on Jaunty to WinXP. :)
From Windows Explorer i type : \\10.0.2.2\ 
i easily can find my shared folder. :)

But i'm searching for hours to find 
how to share my folder (c:\temp\) on WinXp to Jaunty.

If i run : ipconfig on command prompt (XP) it says : 
IP Address. . . . . . . . . . . . : 10.0.2.15
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 10.0.2.2

But when i type on Jaunty : smb://10.0.2.15, it says : 
Could not display "smb://10.0.2.15/"
Error: Failed to retrieve share list from server
Please select another viewer and try again.

Please help how can i access myWinXP folder (c:\temp\) ? 
Thanks

ubuntulovers

---

### Post by capricornday on 2010-04-04
does anyone can help me..
or some links to give me explanation.
thanks

---

### Post by wilee-nilee on 2010-04-04
You can have a easy two way share folder by right clicking on my computer in XP then map network device, it sounds like you already have a folder named share on jaunty, it will find it.

---

### Post by capricornday on 2010-04-05
> **wilee-nilee said:**
> You can have a easy two way share folder by right clicking on my computer in XP then map network device, it sounds like you already have a folder named share on jaunty, it will find it.

Thanks wilee-nilee, 
i have another point :), 
for example i have folder c:\temp on XP(guest).
How can i find it on Jaunty (host).

thank you.

---

### Post by wilee-nilee on 2010-04-05
> **capricornday said:**
> Thanks wilee-nilee, 
i have another point :), 
for example i have folder c:\temp on XP(guest).
How can i find it on Jaunty (host).

thank you.

That I don't know.

---

### Post by capricornday on 2010-04-05
> **wilee-nilee said:**
> That I don't know.

):P that's okay. 
i'll keep searching for this :)

---

