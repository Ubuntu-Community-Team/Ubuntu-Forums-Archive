---
title: "wine &amp; usps shipping assistant"
date: 2008-12-23
forum: Wine
---

### Post by mylar on 2008-12-23
I am trying to run the usps (United States Post Office) shipping assistant (under ubuntu 8.10). When I enter the command 'wine setup.exe' the installer starts to run but fails with the following error: '1621: Failed to verify signature of file dotnetfx.exe'

I was wondering if anyone had gotten the usps shipping assistant to run and what I might do to get it to run too.

Thanks!

---

### Post by cogadh on 2008-12-23
You probably need to install Microsoft's .NET in order for it to work (the error would seem to indicate that). Easiest way to do that is by using [winetricks]("http://wiki.winehq.org/winetricks").

However, if that tracking software is a mission critical application for your business, I don't recommend using Wine for it. That app doesn't appear to be tested with Wine at all (it doesn't appear in Wine's application database), so it cannot really be considered a reliable app in Wine. You would probably be better off using a Windows machine or running Windows in a virtual machine for that software.

---

### Post by TylerRick on 2009-01-26
I tried installing .NET with 'winetricks dotnet20' but it gives this generic and useless error when I try to start Shipping Assistant:

"Exception has been thrown by the target of an invocation"

It show the splash window and says "Status: Initializing..." but it never finishes loading and it shows that error.

```
$ wine --version
wine-1.0.1
```

Does anyone know how to get this to work?

Are there any other winetricks I need to install? Or maybe I should try it with a newer version of wine...

---

### Post by needhelpplease on 2009-05-30
I also tried to install it and got that same signature error.  I didn't try the next step of installing dotNET.  If someone could confirm a way to get it working I would do it.

Otherwise, I'll install XP on virtualbox and use it that way, but I would definitely prefer to use wine for this.

---

