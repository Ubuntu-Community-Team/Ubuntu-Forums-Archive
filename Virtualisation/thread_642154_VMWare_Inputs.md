---
title: "VMWare Inputs"
date: 2007-12-16
forum: Virtualisation
---

### Post by Tteddo on 2007-12-16
I have a strange problem. I have VMWare running an actual install of Win2000 on it's own hard drive (I can dual boot also). I was in it yesterday doing a couple of things, then I shut it off instead of shutting down. Now when I run it, the keyboard and the mouse don't work after I see it grab the inputs. No NUM LOCK, etc...
Now here's the weirder part, when I boot to the actual Win2000 hard disk to the other hardware profile it does exactly the same thing. It works before Windows loads (i.e. I can select my hardware profile, and select F8 to go to safe mode) but not once Windows loads, not even in safe mode. Oh, the VMWare is the same, F8, etc...
I make my living fixing windows machines (11 years now- don't cry for me Argentina!), so I am not inexperienced, but this is a new one on me.
The keyboard and the mouse work great in Gutsy, obviously.
I even plugged in a USB mouse and it seemed to be loading the drivers for it, but nothing.

Anyone have any idea what VMWare could have done to it, or what happened?

---

### Post by Tteddo on 2007-12-22
Found a fix for my Win2000 problem, hope this helps someone!
There is a backup of the file system in the c:\windows\repair directory which was put there when windows was installed. I copied that file to c:\windows\system32\config, overwriting the one that is there. Then I booted into Win2000. Of course I had to reinstall all the hardware that had changed since first install, but the inputs all worked again. I had to setup the VMWare tools again also. When I was done, I copied the new system back to the repair directory for a backup.

---

