---
title: "Server stop responding: goes into an automated scanning mode"
date: 2010-07-14
forum: Server Platforms
---

### Post by duceduc on 2010-07-14
I just installed ubuntu as a learning tool. It was going fine until the next day after the install. This happened on two reinstall of ubuntu server 10.4. All was installed was lamp, squid, privoxy, tor, shorewall, and phpmyadmin. I have added 3 websites to the server.

Today, I noticed my internet stopped responding on my other pc which is linked to my server for internet access( privoxy). When I turned on the server, I noticed the screen was purging out random lines. I don't know what they mean, but it was a never ending series of lines filling the whole screen. To stop it, I ctrl+c. Some of these lines read usb, keyboard, mouse, etc. I am guessing the system went hay-wired. 

When I reboot the machine, it did it again. This time I don't have the cmd prompt. I didn't know another other way to properly shutdown so I just cold reboot the machine. The next time it booted up, all seems normal like it always have been. My sites, internet is working.

I probably didn't provide enough info to diagnose this behavior.  As mentioned before, it happened the first time I installed the server and it is happening again with the same applications installed. 

If you need logs, please let me know where to find it. Excuse my noobs questions.

Edited: It happened again. Some of the lines I could make out are these.
```
Bug: unable to handle kernal NULL pointer deference
Kernal panic-not syncing: Attempted to kill the idle task!
Error panic  occured: Switching back to text console.
```

The server froze at this point.

---

### Post by duceduc on 2010-07-17
I figured out the problem; I had one bad RAM stick. Took it out and server had been running fine since.

---

