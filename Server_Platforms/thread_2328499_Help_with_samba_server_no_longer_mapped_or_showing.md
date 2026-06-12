---
title: "Help with samba server no longer mapped or showing from windows"
date: 2016-06-21
forum: Server Platforms
---

### Post by david472 on 2016-06-21
[COLOR=#000000][I]My server today (and only today), is no longer listed on the network.  Hase been working great for 3 months and now all of a sudden today, I can't access it through windows.
 This is strange. I can access it remotely using PUTTY, but can't access it using Windows. Any ideas?[/I][/COLOR]

1) I talked to tech support and they can see the server and can access it through their end, but can't figure out why all of a sudden I cannot access it through windows anymore in the network.

2) I am trying this batch file, but it doesn't work - I am unsure of the drive number anyway

net use z: \\xx.xxx.xx.xxx\test_share  /user:user1 guest1

[COLOR=#000000]*I did a samba status and it looks ok :*[/COLOR]

```

Samba version 4.1.6-UbuntuPID     Username      Group         Machine
-------------------------------------------------------------------


Service      pid     machine       Connected at
-------------------------------------------------------


No locked files
```

---

### Post by QDR06VV9 on 2016-06-21
Thread Moved to Server Platforms better fit.

---

### Post by bab1 on 2016-06-21
> **david472 said:**
> [COLOR=#000000][I]My server today (and only today), is no longer listed on the network.  Hase been working great for 3 months and now all of a sudden today, I can't access it through windows.
 This is strange. I can access it remotely using PUTTY, but can't access it using Windows. Any ideas?[/I][/COLOR]

1) I talked to tech support and they can see the server and can access it through their end, but can't figure out why all of a sudden I cannot access it through windows anymore in the network.

2) I am trying this batch file, but it doesn't work - I am unsure of the drive number anyway

net use z: \\xx.xxx.xx.xxx\test_share  /user:user1 guest1

[COLOR=#000000]*I did a samba status and it looks ok :*[/COLOR]

```

Samba version 4.1.6-UbuntuPID     Username      Group         Machine
-------------------------------------------------------------------


Service      pid     machine       Connected at
-------------------------------------------------------


No locked files
```
I assume you mean "windows sharing" as putty is also a windows application.  Can you see the host by browsing to the share?

---

### Post by david472 on 2016-06-21
I am not sure what "browsing the share means", but if it means seeing it in the Network section of Windows, the answer is no.

PUTTY (in windows environment)
- works great
-I can log onto the server no problem

When you helped  me out last time, as soon as the server was finished, it was recognized in Windows > Networking.  This worked until yesterday.  Now I can't see the commtechserver in the networking anymore.

---

### Post by bab1 on 2016-06-21
> **david472 said:**
> I am not sure what "browsing the share means", but if it means seeing it in the Network section of Windows, the answer is no.

PUTTY (in windows environment)
- works great
-I can log onto the server no problem

When you helped  me out last time, as soon as the server was finished, it was recognized in Windows > Networking.  This worked until yesterday.  Now I can't see the commtechserver in the networking anymore.
This sounds like a Windows problem. Is this really the name of the server```
commtechserver
```  The server can't have a name longer than 15 characters.

If the sever can be accessed in any way then it is working.  I'm not a Windows person at all, so I'm not going to go father than this.

---

### Post by david472 on 2016-06-21
Ok, thanks for trying.  It is no longer than 15 letters in any event.  So another forum?

---

