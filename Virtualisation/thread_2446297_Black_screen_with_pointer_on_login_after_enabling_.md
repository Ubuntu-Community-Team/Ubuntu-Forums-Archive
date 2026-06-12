---
title: "Black screen with pointer on login after enabling 3D acceleration"
date: 2020-06-27
forum: Virtualisation
---

### Post by tstewart42 on 2020-06-27
Host: Windows 10
Guest: Lubuntu 20.04 LTS

I recently created a Lubuntu 20.04 LTS VM using VirtualBox 6.1, and it worked fine for a few days. Today I decided to enable 3D hardware acceleration in the VM settings. I powered the VM down, enabled 3D acceleration, and set the memory to 128 MB. After logging in, I was only able to see the pointer but the screen remained otherwise black despite leaving it for over 20 minutes. I discovered that by switching to tty2 and back to tty1, I was able to see the LXQt desktop, with everything rendered correctly. Turning 3D acceleration off did not solve the problem, and now I have this issue whether 3D acceleration is enabled or not. 

I'd love to know why switching between tty2 and tty1 fixes this issue, and if anyone has an idea how to resolve it. I'd rather not need to do this every time I log in.

---

