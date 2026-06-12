---
title: "Virtualbox Natty Alpha 3 Guest Fixed Resolution"
date: 2011-03-04
forum: Virtualisation
---

### Post by divergex on 2011-03-04
I have installed Natty Alpha 3 in a VM using Virtualbox on an OS X Host. It is working fine, but I would like to set the resolution to always be 1024x600 to simulate how the experience on a netbook would be. I can get close after installing the Guest Additions, but I really would like to force 1024x600 at every boot. Is there any way to do this?

---

### Post by CCO Makoto on 2011-03-05
I do not know about 11.04, but for 10.10, what you usually do is to manually change the resolution from Monitor Properties in the drop down menu.

It will boot at a smaller resolution (windowed) then as the GUI starts up, it will switch to your desired resolution.

---

### Post by divergex on 2011-03-05
Unfortunately the only choices I get are 1024x768, 800x600, and 640x480. I have it at 1036 x 608 from manually resizing the window. I will have to leave it at that for now as it's close enough to where I want it to be.

---

### Post by Hedgehog1 on 2011-03-07
I also could only use the manual resizing on Natty A3 to get a wide screen.  I suspect it is because the guest additions don't see Natty properly quite yet.

But at least it runs in Vbox - so I am happy about that.  We take what we can get :)

***The Hedge***

---

### Post by pengpengpeng on 2011-03-25
[I]try in terminal:
VBoxManage setextradata global GUI/MaxGuestResolution 1024,600[/I]

---

