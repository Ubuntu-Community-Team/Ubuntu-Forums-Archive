---
title: "Installing Windows 8 after Ubuntu ."
date: 2014-07-03
forum: Windows
---

### Post by Ardeshir on 2014-07-03
HI Everyone !
I have 500 GB of H.D.D and I dedicated all to Ubuntu .
Later I wanted to install Ubuntu Studio Side By Side and I gave 250 GB to that , but the installation failed and I didn't install it again . I just formatted that part to empty space .
Now I want to install Windows 8 on that .
While installing , I got an error : "Windows can't be installed on this partition , it is a GPT partition systerm . Windows should be installed on a NTFS format partition . "
Then I formatted it to NTFS and launched it again , this time the message tuned into this : "Windows can't be installed on this partition , it is a GPT partition system ."

I also tried :
In my BIOS menu there are three different modes :
1 - Use both UEFI and legacy mode
2 - disable UEFI
3 - disable Legacy
I also tried all of them , but I got the same message .



WHat Should I do to install Windows 8 after linux side by side ?
Thanks .

If any further information is needed let me know .

---

### Post by kc1di on 2014-07-03
installing windows after linux is not the preferred method. For one thing Windows has to be installed on the first partition.
you'd be better off if you want windows 8 to do a fresh install of that using the first partion. then re-installing Ubuntu.

---

