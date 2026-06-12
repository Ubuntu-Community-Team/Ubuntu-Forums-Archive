---
title: "Warty Backport: wine 20050211, winetools"
date: 2005-02-13
forum: Ubuntu Backports
---

### Post by jdong on 2005-02-13
**Synopsis**
WINE's one of those things you'd always want the latest version of. Thanks to wine.sf.net for being so prompt in making .deb packages.

**Backporting Process**
The source archive came from winehq's APT repository. All deps were satisfied with Warty deps.

I grabbed a "winetools" package too. Not sure what it is. It's pretty new, single entry in changelog.

**Packaging Status:**
i386 -- Staging at revision 25.
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
Test OpenGL support with Nvidia-glx, ATI's glx, and X Mesa glx cards. It was unclear in the building which GLX headers to compile WINE against.

---

### Post by jdong on 2005-02-13
Confirmed to run my suite of win32 console apps.

---

### Post by YokoZar on 2005-02-16
Ah yes, I forgot to tell you about it, heh.

Winetools is a cool little setup app.  If you have a fresh, virgin Wine install, try running Winetools first and have it setup your system for you.  It can even be used to install Internet Explorer in a couple of clicks.

---

### Post by Sapper2ID on 2005-02-16
I've installed wine, added to /apt/sources.list, I've run winetools setup, that went well. Now, How do I find it? I've been to Franks Corner, looked at faq's, I'm hitting a wall again with this. where is it? I thought I would bring up a windows lookalike window and go from there.

---

### Post by rufius on 2005-02-16
[QUOTE=Sapper2ID]I've installed wine, added to /apt/sources.list, I've run winetools setup, that went well. Now, How do I find it? I've been to Franks Corner, looked at faq's, I'm hitting a wall again with this. where is it? I thought I would bring up a windows lookalike window and go from there.[/QUOTE]
 Wine is just an interface to using windows programs. You have to issue a command like "wine setup.exe" for it to do anything windows related. It doesn't actually bring up a seperate Windows 'desktop'.

---

### Post by Sapper2ID on 2005-02-16
Thanks.

---

### Post by woutervanwijk on 2005-02-18
to use Winetools (it's great!), just type wt in the terminal. And don't forget to read the instructions in the intro, it's important!

---

### Post by Jonathan_ on 2005-02-26
I have successfully installed wine and tried to run a setup file, it works for a few moments and then says 'the installsheild engine (iKernel.exe) could not be launched. (0x80004005)'

any ideas?

---

### Post by jdong on 2005-02-26
That's probably a limitation of WINE. It certainly isn't caused by my packaging. I recommend you consult the WINE support mechanism (mailing list?), or google.

---

### Post by Jonathan_ on 2005-02-26
Ok thanks, i'll have a look around.

I have successfully installed another application, so maybe its a problem with the application I was trying to install before, however it says that it is supported by wine.

I installed this new application to C:\Program Files\Folder - How do I run the program now because I cannot find it anywhere?

---

### Post by jdong on 2005-02-26
cd ~/.wine

drive_c should be in there ;-). Should bring back haunting memories from MS days.

---

### Post by Jonathan_ on 2005-02-26
ahh I see :) Thanks

I'm having more problems with Wine however. I get an error message when I try and install Dreamweaver MX.

"the installsheild engine (iKernel.exe) could not be launched (0x80004005)"

any ideas?

---

