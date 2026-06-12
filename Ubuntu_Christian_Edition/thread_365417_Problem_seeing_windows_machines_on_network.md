---
title: "Problem seeing windows machines on network"
date: 2007-02-19
forum: Ubuntu Christian Edition
---

### Post by westwj on 2007-02-19
Hi,
I am having one problem with Ubuntu CE 2.1. Other editions of Ubuntu allow you to access windows machines on your network. The default setup for CE will show that there is a Windows Network present, but when you double click on it there is nothing there. Is Dansguardian blocking it perhaps? Any help would be appreciated.
Many thanks.

---

### Post by whitefort on 2007-02-19
Hi,

I'm not using CE - just plain ol' Ubuntu - but for what it's worth, I have exactly the same problem and have been unable to resolve it even after weeks of trying and the best efforts of the helpful people in the forums here.

In other words, it may not be a CE issue.

---

### Post by Dylnuge on 2007-02-19
Since this occurs outside of CE, it seems to be a networking problem. If one of the moderators could move this to Networking, it may be more suited there.

Can you tell me exactly what you are doing?

---

### Post by westwj on 2007-02-19
&#65279;Since Whitefort responded to my original post I have managed to make some headway on this subject by myself. But first a bit of background... (I hope this reply is not too long winded.) 
I am a journalist who has tried to promote Linux for a number of years now. Each time I have tried to promote it as an alternative for Windows users, the biggest problem I have come up with has been network related. In Windows, generally after an install you can see the other machines on your home LAN. Before I decided to try out Ubuntu CE, I ran the Ubuntu Live CD. With it, when you click on PLACES, NETWORK SERVERS, WINDOWS NETWORK, you instantly see all of the local Windows computers on your network. When you click on each one, you gain access to shared folders. 
When I came to to install Ubuntu CE I found this was not the case. I have posted questions in several places, but no-one has been able to help. Fortunatley, I have picked up some clues with some google searches, which I will now share. 
I discovered that if you right click on a folder in your home directory and click on SHARE FOLDER that Samba isn't even installed by default. (I had assumed that it would be installed, you see, because of my previous experience with the Ubuntu Live CD.) Since installing Samba I have found that I still can't see the computers on WINDOWS NETWORK, but by clicking on PLACES, CONNECT TO SERVER and entering the IP address of a Windows computer (NOTE: if you want to find out the IP adress of a Windows machine just open a Command Prompt on it, type in "ipconfig" and hit ENTER) you get a link to the computer on your desktop. By double clicking on this link you can gain access to the computer. So, at least that is a start. But I do think it would be preferable to have an easier setup for those wanting to migrate from Windows on at least some of their machines. I would be please to receive any further comments.
By the way, I still haven't been able to access a Windows computer which is running Vista. Nor have I succeeded in accessing the printer on this computer. Any suggestions would be much appreciated.

---

### Post by whitefort on 2007-02-19
> **westwj said:**
> &#65279; I still haven't been able to access a Windows computer which is running Vista. Nor have I succeeded in accessing the printer on this computer. Any suggestions would be much appreciated.

There was an interesting article in Linux Magazine a month or two ago.  Vista uses a new verson of the protocol.  They claim that if it encounters an OS that can't use the new shiny version, Vista will automatically 'degrade' to the old version and allow communication.

But Linux mags did tests and found that while it did work with some operating systems, the generousity didn't extend as far as Linux.  The result is that the Samba software will have to be updated, and apparently the Samba people are working on it.

I don't think you have quite the same problem as me.  My windows (XP) machine can access my Ubuntu machine's folders perfectly.  The Ubuntu machine can see the windows workgroup, but can't see anything inside it.

Networking is a headache.
I'm also trying to sell my friends on Linux, but I'm a terrible example - trouble with network, trouble with the (local) printer, trouble with the modem, etc, etc, etc!!  I'm determined to fully move to Linux this time, but it's turning out to be a struggle almost every step of the way!

All the best!

---

