---
title: "console of vmware server 2.0 freezes X-server"
date: 2009-07-18
forum: Virtualisation
---

### Post by rbaietta on 2009-07-18
Hi, since yesterday (jul 17th 2009) I have the following problem opening the console of vmware server 2.0: 

1. when the console opens, the whole PC seems to be frozen.
2. Mouse and keyboard stop responding.
3. after some minutes, a little pop-up windows shows "Failed to disconnect from the MKS: Pipe connection has been broken"
4. from this moment, the mouse and keyboard start responding again. The vmware console is a "total black" window, but I can close it.
5. I can access the console from an external XP client. This means that the problem is in the interaction between the X-server and the vmware console

"PC" is a kubuntu 9.0.4, x86_64
vmware is "VMware Server 2.0.0 build-122956"

I do not know what happened from jul 17th, I believe that the problem started after applying one of the latest bug-fixing patch.

Does anyone have the same problem? Can anyone help to solve it? I am in trouble because I use the guest os (XP) for work.
Regards

---

### Post by rbaietta on 2009-07-18
Hi, I have an update.
I have upgraded to VMware Server 2.0.1 build-156745

Now, a second after I open the console, the PC seems to be frozen, after few minutes the system responds to mouse and keyboard again, the console window remains black. I can only close it.

I am forced to access the guest os from another client.

Any idea/suggestions?

Regards

---

### Post by rbaietta on 2009-07-18
Hi, I finally solved the problem by reinstalling firefox plug-in.

---

### Post by arunncce2089 on 2009-07-31
Hi guys

I have one issue regarding X server. i am trying to do  achieve multihead on suse linux. 

I have 2 X servers running on different displays. the issue is when i start second X server , first X server gets freezed . I cant do anything in first display.

Can anybody tell me what could be the reason for that.

Thanks
Arun Mittal

---

