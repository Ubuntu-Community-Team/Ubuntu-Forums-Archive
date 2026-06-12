---
title: "Connecting to work server"
date: 2009-01-29
forum: Server Platforms
---

### Post by marbig on 2009-01-29
Have been away from Ubuntu for a while on Windows and now back again. I had an .RDP file on my windows desktop at home that I could connect to our workplace server (Windows 2003). 
Now in Ubuntu I tried to use the same file and got a "There is no application for this file" message.
My question - Is there an application that I can use to connect from a linux machine to a windows server? And if so where might I find it.
Also, is this the correct forum to ask this? 
Many thanks for any suggestions.

---

### Post by volkswagner on 2009-01-29
Assuming .RDP is for Remote Desktop Protocol, you should be able to use Terminal Server Client.  You should be able to use the same password and select RDP as the protocol.  

Ubuntu locates the program under >applications>internet>Terminal Server Client.  If you don't already have it installed, run the following or open synaptic.

```
sudo aptitude install tsclient
```

---

### Post by marbig on 2009-01-29
Thanks for that volkswagner. Worked a treat. Only one other question. When I got the connection the window was only a small size. Had no option that I could find to maximise it. Any idea on this?
Thanks.

---

### Post by volkswagner on 2009-01-29
I have not used the RDP.  I have only just tried the VNC with ULTRvnc running on the windows "server/host" machine.  I do get a resize window running these protocols.  I did notice in the login (tsclient) screen there is a display tab.  Perhaps you can adjust settings there.

---

### Post by marbig on 2009-01-29
> **volkswagner said:**
>   I did notice in the login (tsclient) screen there is a display tab.  Perhaps you can adjust settings there.I should have looked there in the first place. Problem now solved and my Win XP now becoming more unnecessary. Thanks once again.

---

