---
title: "Possible to run ROSE Online on Ubuntu?"
date: 2009-05-08
forum: Wine
---

### Post by Mandraix on 2009-05-08
I installed it through Wine and got as far as the login, after which the window closed itself. I didn't really expect this to work so simply as just installing it through Wine, does anyone have suggestions or have seen a thread similar to mine which found answers?

---

### Post by cogadh on 2009-05-08
ROSE Online does not work with Wine due to the GameGuard protection that it uses. See this thread for more information:
[http://ubuntuforums.org/showthread.php?t=1069960](http://ubuntuforums.org/showthread.php?t=1069960)

---

### Post by Mandraix on 2009-05-08
> **cogadh said:**
> ROSE Online does not work with Wine due to the GameGuard protection that it uses. See this thread for more information:
[http://ubuntuforums.org/showthread.php?t=1069960](http://ubuntuforums.org/showthread.php?t=1069960)

I've seen that thread and took note that ROSE Online was included, but I'd heard that some people had gotten it working. (Perhaps through a program similar to but having key differences to Wine? I'm fairly new to Ubuntu and Linux in general.)

---

### Post by cogadh on 2009-05-08
There really isn't anything similar to Wine that isn't actually based on Wine. The only other "Wine-like" applications are CrossOver by CodeWeavers, which is just the commercial version of Wine, and Cedega by Transgaming, which is based on an early fork of Wine called WineX. Both of them have the same issues that Wine has with this game and GameGuard in general.

It is possible that the game may run using a virtual machine application like VirtualBox, but if it actually uses 3D hardware acelleration, that might not work very well. 3D hardware support in most virtual machines is only experimental at the moment.

The only other way I can think of that the game might work in Wine (or its derivatives) is by using a private server client. Unfortunately, private server clients are a violation of the game's EULA and may be flat-out illegal in some countries, so we can't really help you with that here.

---

