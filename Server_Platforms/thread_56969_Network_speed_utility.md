---
title: "Network speed utility?"
date: 2005-08-14
forum: Server Platforms
---

### Post by Mr. Electric Wizard on 2005-08-14
Does anybody know of a network speed utility that can tell me how fast my lan is?
Maybe a utility that downloads a file from another computer of a said size, and tell me how fast?

---

### Post by Brian Puccio on 2005-08-14
Just use wget:

```
brian@alpha:~$ wget http://ubuntuforums.org/showthread.php?t=56969
--19:09:28--  http://ubuntuforums.org/showthread.php?t=56969
           => `showthread.php?t=56969'
Resolving ubuntuforums.org... 64.21.33.9
Connecting to ubuntuforums.org[64.21.33.9]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 41,671 [text/html]

100%[====================================>] 41,671        --.--K/s

19:09:29 (556.12 KB/s) - `showthread.php?t=56969' saved [41,671/41,671]

brian@alpha:~$
```

---

### Post by LordHunter317 on 2005-08-14
ttcp is good for testing maximum sustaniable transfer within a LAN.

---

### Post by Mr. Electric Wizard on 2005-08-15
Brian, I don't need the speed throught the internet.
I just mean Internally on my LAN, thanks though...

Mr. Hunter, is this what you mean?
[http://www.pcausa.com/Utilities/pcattcp.htm](http://www.pcausa.com/Utilities/pcattcp.htm)

---

### Post by LordHunter317 on 2005-08-15
Yes, though on Linux, you want a Linux version.

---

