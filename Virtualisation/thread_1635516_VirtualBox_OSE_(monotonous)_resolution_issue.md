---
title: "VirtualBox OSE (monotonous) resolution issue"
date: 2010-12-01
forum: Virtualisation
---

### Post by CasparGrigoriNovykh on 2010-12-01
I have successfully installed Backtrack 4 R2 in VirtualBox OSE running in Ubuntu 10.10 (though I suppose "successful" is a subjective word for it, at the moment.)  The guest additions have been installed, and I've edited xorg.conf multiple times within Backtrack, each using a different combination of variables.  Upon adding "vboxvideo" driver under the "Devices" section, startx yields an error stating "no screen detected".  I have added the defaultdepth and the display subsection, and have left it there, as it seems to have no effect on boot, or as a solution.  For the life of me, I cannot get this thing to use 1280 x 800.  Currently,

xrandr:
```

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0*
   640x480        60.0

```

If, perhaps, it offers any clue, copying text internally does not allow pasting externally, and vice versa.  

I am quite new to this, so I apologize if I've missed an essential concept.  After searching many many forums, and trying each and every suggested fix, I figured the topic could use some fresh discussion.  Also, alert me if this issue is a Backtrack-specific issue, and not necessarily VirtualBox OSE (or Ubuntu).  Any further information provided upon request.

In case questions (for whatever reason) are asked, I have no illegal intentions regarding Backtrack - its only use to me is education.

Thank you in advance, for any help given!

Caspar

---

### Post by CharlesA on 2010-12-01
Sounds like the guest additions weren't installed successfully.

---

