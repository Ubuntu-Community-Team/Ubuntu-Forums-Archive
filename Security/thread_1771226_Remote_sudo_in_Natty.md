---
title: "Remote sudo in Natty"
date: 2011-05-30
forum: Security
---

### Post by YesWeCan on 2011-05-30
Ok - what's changed?

When I access a remote Natty client using VNC I cannot use the sudo command in a terminal. In fact, the terminal closes itself as soon as I type the sequence sud. Even su d. Or su    d.

Sua, su a, su c, su e do not cause the terminal to close itself.


This appears to be some sort of new security "feature".

How do I "work around" it?

[edit]
I'd better elaborate.

I have a remote Natty running 11.04 64-bit desktop version. I have installed **tightvncserver** on it.
I log in on 5901 from a Ubuntu 10.04 64-bit desktop using **vinagre**.
The desktop works fine except when I open a terminal in it and type sud. As soon as I type the d the terminal vanishes. This appears to be a deliberate feature.
I also log in to other clients that run 10.04 and this does not happen.
I have run Mint 11 in VirtualBox on my local machine and created the same remote desktop and viewed it from mint 11 itself. Same thing happens.

It seems to me that 11.04 has been modified to kill a terminal that is part of a VNC display when sud are typed.

Can anyone confirm this change, reproduce it and/or tell me how to remotely administer a 11.04 desktop?

Thanks.

---

### Post by YesWeCan on 2011-05-30
The plot thickens.
It is whenever I type 'd' in any text field that the associated window is minimized. Nothing to do with sudo after all. :)

[edit]

Ha. It turns out to be the new keyboard shortcuts! Natty defaulted to 'd' being used to minimize/restore all windows. I had to disable this in "/System/Preferences/Keyboard Shortcuts" and then kill and recreate my remote VNC desktop. Now I can type a d without minimizing all the windows. Something is going wrong here.

---

### Post by drkitty on 2011-08-04
Many thanks!  Just had the same problem and you solution worked.

---

