---
title: "Intrepid virtualbox usb support"
date: 2008-11-20
forum: Virtualisation
---

### Post by Tucatts on 2008-11-20
I am getting the following error: Have looked at some previous threads but not sure I understand what to do. Most have to do with Hardy or Gutsy.
Here is what I get:
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)

Just need some instructions if someone has had this problem. Many thanks in advance!

---

### Post by niyonk on 2008-11-20
Hi!

If I'm not mistaken, I was having the same problem as you when I was installing XP.

I searched and finnaly i found adding ```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
``` to your fstab solves the problem. I think you will then have to reboot

Let me know if it works for you too!

---

### Post by soliac on 2008-12-31
"devgid" is not necessarily "46". To find what it is on your system, run this in a terminal:
grep vboxusers /etc/group

---

### Post by HotShotDJ on 2008-12-31
See the Virtualization Mega-Thread at the top of the Virtualization sub-forum.  It answers this and many other questions.

---

### Post by epyonx1 on 2009-01-05
I don't usually like to mess around with too many files on my system in case something goes wrong, and I didn't want to mess with my fstab on a whim either. Just looking at the code from the official method given on VirtualBox.org to add usb support + the fstab editing method + remembering how in earlier versions of Ubuntu, all it took was to add the "vboxusers" group to the group list, I decided to try something and it worked for me.

1] Open up the menu
2] Click System -> Administration -> Users and Groups
3] Click Unlock
4] Enter your password
5] Click Manage Groups
6] Click Add Group
7] Type in "vboxusers" in the Group Name box and check mark YOUR PARTICULAR USER NAME below
8] Click Okay and press Close twice to finish it up

9] Open up the menu again
10] Click Accessories -> Terminal
11] Type in (without quotes) "sudo gedit /etc/group"
12] Type in your password if the system asks for it
13] Find the entry for "plugdev" and it should look something like: 
"plugdev:x:46:YOUR.USER.NAME,root"
14] At the end of this entry add in "vboxusers" so you end up with:
"plugdev:x:46:YOUR.USER.NAME,root,vboxusers"


Now save it and close it.
Restart the computer.
DONE
----------------------------------------------------------------------

Aftermath:
Your device should now be detectable by Virtualbox.
And to get your particular device working inside Virtualbox, remember to add that particular usb device under: 
The yellow "Settings Button" -> USB -> "Enable USB Controller" -> + sign icon -> Your particular device

(I know this seems like a lot of steps but that's only because I wanted to put in enough detail to minimize confusion. Really it's only 2 steps, that is, one being the addition of the vboxusers group and the other editing the /etc/group file)

Hope it works for you. Worked for me. 
The easy, n00b way. :)

---

### Post by davidself1001 on 2009-01-05
Ok, I get the mouse in the VM but now I can't switch between capture modes (ie switch between host and guest).  I am always in the guest mode.  Making progress though.  Surely I only need to change one more thing and i'll be there.  Help please!

---

### Post by davidself1001 on 2009-01-05
Ok, I get the mouse in the VM but now I can't switch between capture modes (ie switch between host and guest).  I am always in the guest mode.  Making progress though.  Surely I only need to change one more thing and i'll be there.  Help please!

---

### Post by Richard Goldwing on 2009-01-05
To switch between guest and host, you need to press the right "ctrl" button (I think this is the default toggle key)
If that still doesn't work, see what it says next to the &#5838; (downarrow) at the bottom right of the window and just press it on your keyboard. That is meant to be the toggle key.

---

