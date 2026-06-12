---
title: "New Sable with X3100"
date: 2008-02-25
forum: System76 Support
---

### Post by natibo on 2008-02-25
I recently purchased a new Sable.  However, now I realize that the graphics card (Intel X3100 Graphics Media Accelerator) is blacklisted by compiz.  I found this out when trying to activate the more advanced desktop effects.  I have read the work around, but it seems to disable your ability to play video, and could crash the system.

Why would one of the premier preloaded Ubuntu computer manufacturers make the device with a blacklisted video card?  Is there a driver update expected soon?

---

### Post by thomasaaron on 2008-02-25
Did you do this workaround?
[http://knowledge76.com/index.php/GutsyCompizIntelX3100](http://knowledge76.com/index.php/GutsyCompizIntelX3100)

---

### Post by natibo on 2008-02-26
I tried the fix, and I still do not see the cube, wavy windows, etc. which I chose as an option.  In addition, when I click on the normal or extra visual effects box, it still says that it cannot be enabled.

---

### Post by thomasaaron on 2008-02-27
Just tested it on the shop Sable and it worked perfectly.

Perhaps you didn't do something correctly. Did you have any problems with the work-around? Anything that didn't seem clear?

---

### Post by natibo on 2008-02-27
When I went to make the directory, it said it already existed.  So I just pasted the text into that file.  That was the only thing that seemed odd.  Should I uninstall and re-install compiz?

---

### Post by thomasaaron on 2008-02-27
There is another file in that directory. I forget what it's called.  If you pasted into THAT file, it won't work.

You must create a new file. Run this command from a terminal...
```

gedit ~/.config/compiz/compiz-manager
```

And paste this into it. Then save it.

```
SKIP_CHECKS=yes
```

---

### Post by natibo on 2008-02-27
I have done everything you have said.

Terminal:

[INDENT]natibo@ubuntu:~$ mkdir ~/.config/compiz
mkdir: cannot create directory `/home/natibo/.config/compiz': File exists
natibo@ubuntu:~$ 
natibo@ubuntu:~$ gedit ~/.config/compiz/compiz-manager
natibo@ubuntu:~$ [/INDENT]

Gedit

SKIP_CHECKS=yes


When I go to System>Preferences>Appearance>Visual Effects
And press custion (or anything other than none) I get

Desktop effects could not be enabled


Help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by thomasaaron on 2008-02-28
Let's move this one to email support. Some configuration is hosed somewhere, and we will probably have to dig around for a while to find it. Plus, I need a better history of what you've installed on the machine, what custom configurations you've made, etc...

support(at)system76(dot)com.

---

### Post by Vadi on 2008-02-28
I'd say try running "compiz --replace" in the terminal, and paste the output.

That said, both ZaReason and Dell ship X3100. Surely there's something else here?

---

### Post by natibo on 2008-02-28
Here it is:

natibo@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by Vadi on 2008-02-28
It looks like that card was blacklisted because of a problem with video playback, but this has been fixed for hardy.

See here - [http://ubuntuforums.org/showthread.php?p=3451249](http://ubuntuforums.org/showthread.php?p=3451249), someone found a solution.

---

### Post by natibo on 2008-02-28
I could not understand what to do by following your links.

---

### Post by Vadi on 2008-02-28
Oh, er, true. That's for ThinkPads. Sorry, didn't follow it through.

---

