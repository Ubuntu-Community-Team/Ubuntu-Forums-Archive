---
title: "Pokerstars - constant crash - CreateToolhelp32Snapshot"
date: 2010-07-02
forum: Wine
---

### Post by PhenixRising on 2010-07-02
Hello, I am already discussing this problem with PokerStars but I wanted to post here in case anyone is having trouble.  I am constantly crashing on PS.

I have not been able to get it to crash with out using a shortcut program.  A few days ago I would crash repeatedly even if I did not have a shortcut program running.  Something is obviously wrong but as of now I only have these few lines.  

Can someone help?

I'm pretty much useless when it comes to this.  I can build a computer but I have no idea how they actually work. :)

[PHP]fixme:heap:HeapSetInformation 0x937000 0 0x33fd6c 4
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:resource:GetGuiResources (0xffffffff,1): stub[/PHP]

---

### Post by asdfoo on 2010-07-02
> **PhenixRising said:**
> Hello, I am already discussing this problem with PokerStars but I wanted to post here in case anyone is having trouble.  I am constantly crashing on PS.

I have not been able to get it to crash with out using a shortcut program.  A few days ago I would crash repeatedly even if I did not have a shortcut program running.  Something is obviously wrong but as of now I only have these few lines.  

Can someone help?

I'm pretty much useless when it comes to this.  I can build a computer but I have no idea how they actually work. :)

[PHP]fixme:heap:HeapSetInformation 0x937000 0 0x33fd6c 4
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:resource:GetGuiResources (0xffffffff,1): stub[/PHP]

have you tried the latest version of Wine? open a terminal and type 'wine --version' it should print wine-1.2-rc6.

---

### Post by PhenixRising on 2010-07-03
> **asdfoo said:**
> have you tried the latest version of Wine? open a terminal and type 'wine --version' it should print wine-1.2-rc6.

I'm upgrading now.  I just realized that I did not post the full debug window :(

I'll have to re-crash pokerstars.

---

