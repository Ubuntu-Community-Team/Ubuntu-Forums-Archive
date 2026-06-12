---
title: "seamless rdp not really seamless?"
date: 2009-03-13
forum: Virtualisation
---

### Post by isandor on 2009-03-13
Hi

I am not sure if this is the right place to ask but I found some similar posts around so I thought I give it a try.
I have a problem with seamless RDP on a Xububtu Intrepid box. 
I installed Virtualbox under Xubuntu and had WXP installed in it. I managed to access the WXP guest inside VirtualBox, I even managed to start the WXP guest headless.
However, when I start a seamless rdp session to the WXP guest, I get dual window decorations for my window. 
For instance, I start notepad and I get a window with XFCE decorations and inside it, I have a window with windows decorations. 

What am I missing here?

Imre

---

### Post by isandor on 2009-03-16
I found the solution. Ubuntu has a failing rdesktop package. The same version from Debian does not exhibit this problem.

Regards,

Imre

---

