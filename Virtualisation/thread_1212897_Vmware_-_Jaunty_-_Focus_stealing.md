---
title: "Vmware - Jaunty - Focus stealing"
date: 2009-07-14
forum: Virtualisation
---

### Post by swappa on 2009-07-14
Hi there
Running Vmware workstation with Ubuntu jaunty as host and Windows 7 as guest. It is working very well, albeit with one major annoyance;

The guest is always full screen, but whenever OSD displays something on the host, my screen flickers and the notification from OSD is displayed on top of the Windows desktop.  And, the mouse and the keyboard input reverts back to the Ubuntu desktop. Mouse input but not keyboard input (I need to click somewhere on my Windows desktop) will go back to the Windows guest after the osd display is done, but this is getting  really annoying since both Skype and Pidgin notifications are processed by osd (even if I have disabled those events in both Skype (events settings) and Pidgin (disabled lib-notify plugin)). 

How can I avoid osd interfering with my Windows desktop?
Any ideas? Thanks

---

### Post by krissdap on 2009-07-15
Hi There,

Not sure if this could be a solution for you or not.
I'm running vmware server 2.0 on 8.10 and have similar problem.

My workaround is to use remote desktop (rdesktop) to connect to vm instead of using vmware console.

---

### Post by swappa on 2009-07-15
> **krissdap said:**
> Hi There,

Not sure if this could be a solution for you or not.
I'm running vmware server 2.0 on 8.10 and have similar problem.

My workaround is to use remote desktop (rdesktop) to connect to vm instead of using vmware console.

Thanks for your input.
Glad to hear that others have the same issue. Maybe it will be fixed some day...
RDP could be one way to avoid this even if it seems kind of...well, osd should not steal focus like this. 

Thanks :-)

---

