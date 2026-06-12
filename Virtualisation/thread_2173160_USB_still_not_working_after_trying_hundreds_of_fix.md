---
title: "USB still not working after trying hundreds of fixes on VirtualBox"
date: 2013-09-08
forum: Virtualisation
---

### Post by tom36 on 2013-09-08
I recently installed VirtualBox on a Windows 8 PC with Ubuntu 13.04 as the guest. I tried to use USB, but I wasn't able to access my USB stick or my phone, it just showed up on Windows. I installed the Guest Addition and the extension pack and also added the filters. When I try to activate USB2.0 Controller, I can't start Ubuntu, it says that the deice helper structure has changed and closes. Also,I can't add me to the vboxusers group, because it doesn't exist.

---

### Post by JKyleOKC on 2013-09-08
Try re-installing vbox, from the Oracle download site. It's just come out with an update that takes the version to 4.2.18 and one of the fixes listed in the changelog involves USB. My experience trying to use vbox on a Win8 machine was so bad that I had to install VMWare Player in its place; the USB drivers have apparently changed at Win8 and vbox failed to keep up with it so far as I could tell.

---

### Post by tom36 on 2013-09-08
Thanks man! It solved my problem! Somehow VB didn't told me to update ;)

---

### Post by JKyleOKC on 2013-09-08
> **tom36 said:**
> Thanks man! It solved my problem! Somehow VB didn't told me to update ;)
That's why I said to reinstall from the Oracle download site. I think that's what you would have to do anyway for Windows, but for those who come to this thread in the future, remember that Canonical doesn't update its repositories for anything except security fixes, between releases. Thus re-installing on an Ubuntu host, from the repository, would not get the latest version. We can add the Oracle PPA to our repository list, though, and be advised of every update as soon as it's released. That's how I knew about 4.2.18...

You can mark the thread as solved; see my signature.

---

