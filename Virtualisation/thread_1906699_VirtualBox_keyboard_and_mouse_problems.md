---
title: "VirtualBox keyboard and mouse problems"
date: 2012-01-09
forum: Virtualisation
---

### Post by ethanova on 2012-01-09
I am running Ubuntu 11.04 and I got VirtualBox to run my other Win7 partition (raw disk access) as a guest. Ever since then, my touchpad (this is a laptop) two-finger scrolling is inverted. I can fix this by using xinput to switch some settings on the virtual pointer created by VB. I also cannot any longer use my shortcut alt+w to initiate window picker for all windows (scale effect through compiz). Changing it to a different key combination does nothing. Capturing a key combination does nothing. 

I tried disabling the virtual keyboard, and that doesn't help. I tried disabling the virtual pointer/mouse, and it crashes and logs me out and forced me to log back in. So I'm stuck. Help?

EDIT: It seems different pointers are being used in different applications. My fix for scrolling works in most applications, but not in Firefox or Document Viewer (whatever comes up for PDFs automatically), possibly other applications. Doesn't make any sense to me, as the xinput set props that I used should have been for that specific pointer. As far as I know, the normal synaptic pointer shouldn't be inverted.

---

