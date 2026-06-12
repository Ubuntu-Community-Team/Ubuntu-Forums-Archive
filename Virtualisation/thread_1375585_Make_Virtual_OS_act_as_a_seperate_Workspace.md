---
title: "Make Virtual OS act as a seperate Workspace"
date: 2010-01-08
forum: Virtualisation
---

### Post by BionicGear83 on 2010-01-08
I am currently using Virtual Box, I am just wondering if it would be possible for a Virtual OS act as a new workspace.
Does anybody know how to do it?

---

### Post by fouadatmeh on 2010-01-08
Hello,
You can drag virtualbox's guest window to the workspace you want and change it to full screen (ctrl+F) and that's it.. but make sure you have guest addiditions installed.
Hope that helps :)

---

### Post by BionicGear83 on 2010-01-09
Thanks for the info.

---

### Post by HermanAB on 2010-01-09
...or you can SSH into the VM from anywhere and do:
$ ssh -X -C -c blowfish user@vmipaddress gnome-panel

et voila!

---

### Post by akand074 on 2010-01-09
I just have my VM running in seamless mode in its own workspace and its great. If you don't like that you could just have it maximized or put it in full screen mode like stated above. I personally prefer it in seamless mode, just make sure you install guest additions regardless you get your native desktop's resolution as well as enabling all other features

---

### Post by akand074 on 2010-01-09
I just have my VM running in seamless mode in its own workspace and its great. If you don't like that you could just have it maximized or put it in full screen mode like stated above. I personally prefer it in seamless mode, just make sure you install guest additions regardless you get your native desktop's resolution as well as enabling all other features

---

