---
title: "Dell Dimension 9100 and Virtualbox"
date: 2008-07-02
forum: Virtualisation
---

### Post by AlanR8 on 2008-07-02
Evening all

Have Goooooooogled and searched and am not coming up with answers! 

The problem is that I can get XP running in Virtualbox with no problems. It browses the web, won't play sound, for now, and will update.

What I CAN'T do is move the mouse outside the XP window, and by that I mean I can't get to the menu bar related to the XP window, or it's status bar. When I close the XP session, I have no mouse at all in Kubuntu and have to reboot.

I've downloaded the Guest additions .iso, but because I can't get to the menu bar I can't install it!

Any help would be MUCH appreciated....

---

### Post by AliTabuger7 on 2008-07-03
The gnome menu bar, XP menu bar, or menu on the Virtualbox window?

Are you using the Right Control key?

---

### Post by AlanR8 on 2008-07-03
First off I'm running Kubuntu, not Ubuntu.

The mouse is trapped on the Windows desktop and I can't access the Virtualbox menu bar or status bar. There's no way I can access my K desktop at all. As I said above, the only way out is to close the Windows session and that releases the keyboard so I can roughly navigate the K desktop but the mouse is still locked. And yes, the host key seems to have no effect.

Have thought about the problem overnight and am going to reinstall Gutsy 8.04 from clean. I realise that I updated from 7.10 and am wondering if a clean install might sort the problem. The other thing I'm going to try is a different mouse just to eliminate hardware as an issue.

Any other suggestions in the mean time would be gratefully accepted!

---

### Post by AliTabuger7 on 2008-07-03
Are you using your "host key" to get the mouse out of the window? It's "right control" by default. You might want to change it to something like "Right Super".

---

### Post by AlanR8 on 2008-07-03
Yup, am using the host key and no difference. However, I'm now using my Microsoft mouse rather than the default Dell mouse and when I exit Doze I now get control of my K desktop back again. Next step, before a full rebuild is to replace the Dell keyboard as well

---

### Post by AlanR8 on 2008-07-04
Sorted it out.

Was the Dell keyboard that was not responding. It appeared as a USB device whilst setting up Virtualbox so I added it to the machine. Today I removed it and I have full control of both desktops now!

---

