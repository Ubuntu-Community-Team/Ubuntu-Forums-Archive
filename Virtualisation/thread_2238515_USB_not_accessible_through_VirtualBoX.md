---
title: "USB not accessible through VirtualBoX"
date: 2014-08-08
forum: Virtualisation
---

### Post by fernandojosecabral on 2014-08-08
I reinstalled linux and VirtualBox. To my surprise, VirtualBox and the guest system do not see the USB ports. It did work OK in the previous installation. The USB are all functional in the host system. VBoxGuestAdditions.iso is intalled...  What else should I check?  EDIT:  well, shame on me. After reinstalling the system, I forgot to add user to the vboxusers groups. So, solution was pretty straightforward. Since I know stupidity is not my privilege (and it may also strike me twice), e leave it documented bellow for my own benefit and the benefit of others they may incurr in the same omission I did: ```
sudo adduser yourusername vboxusers
```
Solved. Let's move forward.

---

### Post by jan4 on 2014-11-13
Excellent! Solved my issue :)

---

