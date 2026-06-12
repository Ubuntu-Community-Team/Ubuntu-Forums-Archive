---
title: "Drakan Level Editor now functional in Wine"
date: 2016-07-14
forum: Ubuntu, Linux and OS Chat
---

### Post by UCyborg on 2016-07-14
Just wanted to post about the level editor for the old 1999 action adventure game Drakan: Order of the Flame now finally seems to work with Wine. I won't go too technical about it to not upset some moderator/admin here, but let's just say that we have 2 distinct problems with the application, preventing it from working properly on modern Windows systems, resulting in crashes. Only one of those problems affect the application performance under Wine, and the bug has been resolved by the recent release of the unofficial patch. So it seems that Wine could be a viable alternative for running this app without encountering crashes, given that you just can't use Windows 98 on modern machines along with 3D acceleration. Of course, more thorough testing by someone proficient with the editor wouldn't hurt to make sure it really doesn't crash any more for some other reason, but the community is very small and nobody has made a new level for quite some time and it would be preferable that Windows app also works properly on Windows. The remaining crash issue is also dependent on certain other variables/quirks, something to do with how the editor application communicates with separate 3D engine, and it just doesn't behave as it should ever since Windows 2000.

Anyway, the point of this post was, I wanted to discuss technical side of things over at WineHQ forums, but my topic was disapproved just because I said this evil word "disassemble". I understand they have policies about not disassembling MICRSOSOFT DLLs when it comes to Wine development, but what does this have to do with using the said technique to find out how some 3rd party, abandonware app interacts with the Windows API? Whole purpose of Wine is to have alternative Win32 API implementation to supports such applications on Unix-like OSes... You could probably write test application that depends on that quirk without much effort, but why not stick to real-world example? Apparently they don't want to know about the flaws in their compatibility layer, because the said application works flawlessly on real Windows 98 without modification. Oh well, their loss.

---

### Post by howefield on 2016-07-14
Thread moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

