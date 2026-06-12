---
title: "Can't build VB guest additions with 3.8.0-1.5 kernal"
date: 2013-01-21
forum: Ubuntu Development Version
---

### Post by loukingjr on 2013-01-21
I posted something about this elsewhere but I thought a new thread would be better. VirtualBox cannot build guest additions with the 3.8.0-1.5 kernel and matching headers.

---

### Post by Paddy Landau on 2013-02-08
I also have this problem.

The usual fixes don't work.

---

### Post by loukingjr on 2013-02-08
from what I understand it's something VirtualBox needs to address in the next maintenance  release.

---

### Post by Paddy Landau on 2013-02-08
> **loukingjr said:**
> from what I understand it's something VirtualBox needs to address in the next maintenance  release.
Thanks. We'll just have to wait, then.

---

### Post by PJs Ronin on 2013-02-22
This was driving me nuts as I was getting the same 'fail' result and without the additions a VM is pretty useless.   Found this link:
[http://www.tuxtrix.com/2013/02/how-to-install-virtualbox-guest.html](http://www.tuxtrix.com/2013/02/how-to-install-virtualbox-guest.html)
and it worked a treat.   I now have a Precise host with a Raring guest and guest additions installed into the guest!

---

### Post by loukingjr on 2013-02-22
this "semi" works for me. I tried it on Lubuntu 13.04 and sometimes the guest boots in full screen which is what I want and sometimes it doesn't. also, shared folders don't seem to be working.

---

### Post by Paddy Landau on 2013-02-22
> **PJs Ronin said:**
> Found this link:
[http://www.tuxtrix.com/2013/02/how-to-install-virtualbox-guest.html](http://www.tuxtrix.com/2013/02/how-to-install-virtualbox-guest.html)
Thanks for sharing the link.

It worked for me…

But…

All my window decorations have disappeared. I cannot use Compiz Config Settings Manager, because its window is almost all white.

So, I've had to restore the snapshot to before installing the Guest Additions. :(

---

### Post by PJs Ronin on 2013-02-22
> **Paddy Landau said:**
> But…

All my window decorations have disappeared. I cannot use Compiz Config Settings Manager, because its window is almost all white.

So, I've had to restore the snapshot to before installing the Guest Additions. :(

Is this issue the same as this one: [http://ubuntuforums.org/showthread.php?t=2118345](http://ubuntuforums.org/showthread.php?t=2118345)

---

### Post by Paddy Landau on 2013-02-22
> **PJs Ronin said:**
> Is this issue the same as this one: [http://ubuntuforums.org/showthread.php?t=2118345](http://ubuntuforums.org/showthread.php?t=2118345)
It could well be. But my window decorations were also missing. I think I should wait a couple of days and try again — that thread seems to indicate that it is a temporary problem.

---

### Post by Kow on 2013-02-22
If you disable 3D acceleration in the VM's settings, Unity 2D works well.

---

### Post by cariboo on 2013-02-22
> **Kow said:**
> If you disable 3D acceleration in the VM's settings, Unity 2D works well.

Raring doesn't have Unity 2D.

---

### Post by loukingjr on 2013-02-22
> **cariboo907 said:**
> Raring doesn't have Unity 2D.
I wasn't going to say anything :)

---

### Post by Kow on 2013-02-23
Unity using 3D software acceleration works fine.

Make sure Virtualbox Settings -> Display -> Extended Features: Enable 3D Acceleration and Enable 2D Video Acceleration are both unchecked.

---

### Post by PJs Ronin on 2013-03-07
VirtualBox 4.2.8 released.   Problem of guest editions not installing into the VM has been resolved.

---

