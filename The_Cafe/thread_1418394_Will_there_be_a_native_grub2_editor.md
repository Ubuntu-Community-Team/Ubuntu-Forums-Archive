---
title: "Will there be a native grub2 editor?"
date: 2010-02-28
forum: The Cafe
---

### Post by chrismyers on 2010-02-28
Hi guys,

It seems that many people are struggling to get to grips with the new grub2.

Does anybody think that there would be any mileage in a grub2 editor?

There appears to be none in the repos, so I had taken a look on the net.

Ggrubeditor had been started, but development has stopped. There seems to be only a KDE source code download available.

Any ideas/further info anyone?

Cheers :D

---

### Post by -kg- on 2010-02-28
Frankly, unless you want to easily change the appearance or some aspect of functionality (which I really can't imagine what), I don't see much need for a GRUB2 editor.

"sudo update-grub" has worked flawlessly for me, and I have Vista and three different Linux distributions installed.  I can't really imagine a reason for one.  Perhaps if you or someone could suggest a reason or two?

---

### Post by deepredblood on 2010-12-26
Well...quite frankly I can mention one big one.

Deleting grub menu entries...such as the one created for dual booting with Windows 7. There are 2 entries for Windows 7 (loader)...and one for Vista loader. I have only one installation of Windows 7...I want to remove the other 2.  As of this writing I still have not found a way to do it.

Removing old kernel entries. Yes I realize you can go un-install all the old unnecessary ones and they will not appear in the grub menu...but why not just have an editor to remove the entries?

Then there's the useless memtest86+ entries. Yep I know I you can go into /etc/grub.d and change the mode of the file so it's non-executable....but that's a lot of rigmarole don't think...when it could easily just be removed by a simple gui editor?

---

