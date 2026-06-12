---
title: "&quot;Ctrl&quot; Key in keyboard doesn't work in Windows hosted in Ubuntu 10.04 Lucid"
date: 2010-09-14
forum: Virtualisation
---

### Post by balakriz on 2010-09-14
Hi Experts,

I have windows XP running inside the "Virtual Box" installed in Ubuntu 10.04. Somehow the "Ctrl" key in the keyboard doesn't work in Windows. All the other keys work. Any pointers on this would be highly appreciated.

Br,
BK

---

### Post by sikander3786 on 2010-09-14
Have you checked that both Right Ctrl and Left Ctrl are not working?

Right Ctrl is bound to be the Host key in VirtualBox e.g, Right Ctrl + F = Fullscreen, so you might be getting problems with it. Still Left Ctrl should work.

---

### Post by JKyleOKC on 2010-09-14
My solution to this problem was to modify the "host" key for vbox to be "Menu" instead of right-ctrl. To do this, open vbox and pull down the "File" menu, choose "Preferences" and select the "input" tab. You'll see one edit box. Select it, and press the menu key. The wording will change. OK your way back out. The change takes effect immediately.

---

### Post by balakriz on 2010-09-21
Hi All, 

Thanks for the inputs. The options you have suggested doesn't solve the problem. I have indeed made Menu key as the host key and still the problem persists. Would be great if you could help. (Both the controls keys doesn't work.)

Br,
BBK

---

### Post by balakriz on 2010-09-21
Hi All, 

I have disabled the Gnome option "Show position of pointer when ctrl key is presses" and this solved the problem.

Br,
BBK

---

### Post by JKyleOKC on 2010-09-21
Glad to see that it's fixed. Please use the "Thread Tools" link at the top of the page to mark the thread as solved so that others will know there's a solution, if they run into the same problem.

---

