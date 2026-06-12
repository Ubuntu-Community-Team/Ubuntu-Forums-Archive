---
title: "Ububtu 15.04 on VM, no sound."
date: 2015-07-10
forum: Virtualisation
---

### Post by leithanne2 on 2015-07-10
Optiplex 380, 8GB ram (2GB dedicated to VM), Win 7. Realtek HD Audio.

The Vervet runs so vividly, if only I could fix the sound....

I'm not a Muggle, but I'm also not a super penguin. I can copy and past into the terminal, but not much more, so please be kind.

---

### Post by Vladlenin5000 on 2015-07-10
Hi and welcome.

Well, the first thing that begs clarification is which OS is the host and which is the guest?

---

### Post by leithanne2 on 2015-07-10
Thanks for the welcome. Win 7 Pro is the host and Ubuntu 15.04 is the guest. (Sound works fine in Windows, BTW.)

---

### Post by Vladlenin5000 on 2015-07-10
If so the issue is somewhere in the VM definitions and those depend on the virtualisation software you're using.
This is the relevant information that's missing in your thread. 

PS - Meanwhile I suggested to the Mods to move your thread to where it belongs: Virtualisation.

---

### Post by leithanne2 on 2015-07-10
Thank you. VM is Vmware.

---

### Post by Vladlenin5000 on 2015-07-10
[https://www.vmware.com/support/ws3/doc/ws32_vidsound4.html](https://www.vmware.com/support/ws3/doc/ws32_vidsound4.html)

---

### Post by leithanne2 on 2015-07-10
I couldn't find the Configuration Editor in VM Player, but, poking around, I discovered Player/Manage/Virtual Machine Settings/Sound card, and was able to specify my sound card instead of using the default, and it's all better, now.

Thank you, again, for your help.

---

### Post by Vladlenin5000 on 2015-07-10
You're welcome but I did nothing you couldn't have done (find out) yourself. ;-)

Please use the thread tools to mark this one as solved so future users may benefit.

---

### Post by Frogs Hair on 2015-07-10
*Moved to **Virtualisation.***

---

