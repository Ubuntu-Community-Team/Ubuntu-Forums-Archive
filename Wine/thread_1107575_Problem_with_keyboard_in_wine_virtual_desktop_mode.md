---
title: "Problem with keyboard in wine virtual desktop mode"
date: 2009-03-26
forum: Wine
---

### Post by zakaluka on 2009-03-26
Hello all,

I have tried asking this question in 2 other forums and have received no resolution, so I am hoping that people using Ubuntu have encountered this before.

Setup:
- Wine 1.1.17 w/shader models patch ([http://bugs.winehq.org/show_bug.cgi?id=17437](http://bugs.winehq.org/show_bug.cgi?id=17437) -- compiled using debian toolchain (apt-get source; patch; buildpkg; dpkg -i))
- Ubuntu 8.10
- Dell e1705 w/2gb ram
- Eve Online 6.x (Apocrypha)

Problem:
If I run the game using the menu or ```
wine "C:\Program Files\CCP\EVE\eve.exe
```, all keys / shortcuts work okay.  However, switching to other desktops and coming back corrupts / crashes the game very easily.

If I run the game using the virtual desktop, i.e. ```
wine explorer /desktop=1,1440x900 "C:\Program Files\CCP\EVE\eve.exe"
```, it is very stable.  However, I can no longer use any shortcut keys that use the CTRL key.  Also, using shortcuts like ALT+F1 activates the gdm menu instead of activating modules in-game.  

Does anyone know how I can make it so that keypresses go to the game instead of going to gdm first.  I don't think there is a keyboard emulator running in the background, and I shut all the processes I could.  As I mentioned, the problem only occurs in Wine's virtual desktop mode.  

Relevant thread from WineHQ Forums: [http://forum.winehq.org/viewtopic.php?p=21921&sid=07b69898ab2b5463af4bdd4ef6c20c04](http://forum.winehq.org/viewtopic.php?p=21921&sid=07b69898ab2b5463af4bdd4ef6c20c04)

Any help is greatly appreciated.

Regards,

z.

---

### Post by jnewl on 2009-03-27
I'm guessing from your description that wine must reserve the CTL and ALT keys for system use when in virtual desktop mode, although I've never noticed that myself. I'd see if you can make CTL + Anything do something noticeable like switch desktops or something. Then you'd know for sure.

Can you run EVE in a window (from a setting inside EVE itself)? If so, I'd think running it in a screen-sized window ought to stop any problems caused by switching desktops while playing. Another thing you might try, if you're running compiz, is disabling it. Perhaps one of its fancy effects is the source of the problem.

---

### Post by zakaluka on 2009-03-28
I can switch desktops for CTRL+ALT+Left/Right.  However, the odd thing is that the key combinations I am using are not system shortcuts (as far as I know).  

Plus, CTRL and ALT may be reserved for certain combinations, but I can still using ALT for certain things (for example, ALT+F1 brings up the gdm Applications menu, but ALT+F3 activates a module).  So, certain key combinations are getting through and others aren't (i.e. none of the CTRL combinations are getting through).  

I looked under System->Preferences->Keyboard Shortcuts, but didn't see any options that I could turn off to make this work.

I'll try to run Eve in a window to see if it ceases crashing.

Thanks for your help,

z.

---

