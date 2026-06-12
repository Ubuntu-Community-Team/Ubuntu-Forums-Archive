---
title: "Loss of application icons in GNOME Shell top bar"
date: 2018-07-10
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2018-07-10
I recently had to completely reinstall Ubuntu 18.10 due to a stupid error on my part. All was going well until a couple of hours ago when I noticed that I have lost the icon and menu for the current running application from GNOME Shell's top bar. It normally appears to the right of "Activities". Instead, a new coloured icon and menu appears to the left of the maximise and minimise buttons on the top bar of applications such as the terminal, calculator, settings, tweaks and even LibreOffice. See the screenshots below.

Other applications such as Chromium and Firefox do not display the new icon and menu. I don't think any functionality has been lost for those applications as I can right click the icon on the dock to open extra windows etc. 

I have three users set up on this PC. The other two have not been customised at all and they both show the icon for the running application in the top bar as I would expect so it's not a recent update to 18.10. For my main user, I have checked all the installed extensions, changed themes, removed communitheme and even reverted to using vanilla-gnome-desktop but nothing has brought back the missing icons and menus and removed them from the top bar of the relevant applications. I've also used the dconf editor to see if I can see a setting that needs to be changed but I can't.

I've searched the web for a solution but found nothing. What have I inadvertently changed? Am I missing some very obvious setting?

---

### Post by #&amp;thj^% on 2018-07-10
Sorry I just have to ask if Ubuntu appindicators is turned off in tweak-tool.
And maybe have a look @ "~/.config/menu/" I think that is still used but I'm on Arch today so I can't verify that for sure. And I remember having to delete that folder (~/.config/menu/) on 18.04 a time or two due to my tom-foolery :) to set things right again.

---

### Post by PaulW2U on 2018-07-10
> **1fallen said:**
> Sorry I just have to ask if Ubuntu appindicators is turned off in tweak-tool.
No definitely set to on. I've toggled that one several times and even reinstalled.
> **1fallen said:**
> And maybe have a look @ "~/.config/menu/" I think that is still used but I'm on Arch today so I can't verify that for sure. And I remember having to delete that folder (~/.config/menu/) on 18.04 a time or two due to my tom-foolery :) to set things right again.
There's nothing in ~/.config/menus worth deleting.

There is obviously something wrong as the first time I start Tweaks after logging in I am prompted to restart due to configuration changes. I've never seen that before.

---

### Post by dino99 on 2018-07-11
Have you enabled 'tasks' into tasbar extension ?  #-o

---

### Post by PaulW2U on 2018-07-11
No that's something different and I don't have that extension installed anyway.

On a new install an icon (and application name) is added to the top bar for the current running application. I do not have that. I'm also intrigued as to why a new icon with a drop down menu has appeared on applications such as the calculator and terminal.  See screenshot in first post.

---

### Post by vanadium on 2018-07-11
Open the Gnome Tweak tool (install it if you do not yet have it). Under "Top bar", turn "Application menu" on. This will move the application ion back from the application window to the gnome panel.

---

### Post by PaulW2U on 2018-07-11
> **vanadium said:**
> Open the Gnome Tweak tool (install it if you do not yet have it). Under "Top bar", turn "Application menu" on. This will move the application ion back from the application window to the gnome panel.
Thanks for your suggestion vanadium. I've tried that more than once as it was after playing with the Application Menu that I noticed something had changed. The application icon doesn't move back to the panel even after restarting GNOME Shell (Alt+F2, r and enter) or logging out and back in.

---

### Post by mc4man on 2018-07-11
You could ck. if it's a gsetting like,
First save a look at current non default settings,
```
dconf dump / > settings.txt
```

Then go to tty3 (ctrl+alt+F3) login & run
```
mv .config/dconf/user .config/dconf/user.bak && reboot
```
See if any better, if not you can reverse above, i.e from tty rm .config/dconf/user & mv .config/dconf/user.bak to .config/dconf/user  & reboot
If better then dump dconf to another txt. file & compare.

---

### Post by #&amp;thj^% on 2018-07-11
Dang It ](*,)why didn't I think of this. :(
mc4man that's why you get the big money. ;) he he.

---

### Post by vanadium on 2018-07-12
> **PaulW2U said:**
> Thanks for your suggestion vanadium. I've tried that more than once as it was after playing with the Application Menu that I noticed something had changed. The application icon doesn't move back to the panel even after restarting GNOME Shell (Alt+F2, r and enter) or logging out and back in.
You may want to check the key org.gnome.desktop.wm.preferences button-layout in dconf, to see if "appmenu" is in there. This key may look like, fore example, ':appmenu,close'. Perhaps that causes the appmenu never to appear in the header bar in your case. (On the other hand, one can then wonder how "appmenu" got removed from your key, unless you manually edited it).

---

### Post by PaulW2U on 2018-07-12
Sorry for the delay in getting back to this thread. All seems to be working today just as it should. vanadium's suggestion of toggling the setting "Tweaks | Top Bar | Application Menu" was all that was needed. 

Testing against a live session of yesterday's build of 18.10 I previously saw many more prompts to restart my session than I when running the live session. These prompts no longer appear when I open Tweaks but only when I toggle the Application Menu setting. I don't know whether there is a bug here, a clash with an extension or whether it was down to a simple human error.

Anyway, I'll mark this as solved on the basis that the simple toggling a setting was the correct solution even though for some unexplained reason it didn't work first time.

Thanks to all that replied.

---

### Post by nroetert on 2018-12-07
This just helped me tremendously, thanks!

---

### Post by slickymaster on 2018-12-07
18.10 has been released.

Thread closed

---

