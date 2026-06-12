---
title: "Create a share folder between winodws (host) and ubuntu server (guest) on virtualbox"
date: 2021-02-01
forum: Virtualisation
---

### Post by sed_faster on 2021-02-01
Hello everyone,

I installed ubuntu server (version: 20.4.1 LTS) on virtual box (as guest). I use windows 10 as host system. How can I configure a shared folder between system?

I run this command:
```
sudo apt-get install virtualbox-guest-additions-iso
```
and create a folder on my windows 10 and configure this menu (please see attached image).
[ATTACH=CONFIG]287874[/ATTACH]

But I don't know how resolve this issue. Thank you for your help in resolving this matter.
Thanks

---

### Post by CelticWarrior on 2021-02-01
I think you should use a different mount point, maybe some folder inside your /home/usteste

---

### Post by sed_faster on 2021-02-01
Didn't work. Please see the attached image and tell me if I did all right.[ATTACH=CONFIG]287875[/ATTACH]

---

### Post by ActionParsnip on 2021-02-01
If you bridge the NIC, you can access your Windows IP as if your VM was another system on the LAN. You can access any shares the Windows system has (Including the hidden shares) as long as you can provide credentials.

---

### Post by sed_faster on 2021-02-01
I can ping IP machine Ubuntu, through CMD Windows 10 (Host) but I can't ping IP machine Windows through Terminal Linux (guest). See another three images attached.

[ATTACH=CONFIG]287877[/ATTACH][ATTACH=CONFIG]287878[/ATTACH][ATTACH=CONFIG]287879[/ATTACH]

---

### Post by &amp;KyT$0P# on 2021-02-01
> **sed_faster said:**
> I run this command:
```
sudo apt-get install virtualbox-guest-additions-iso
```

This does not install Guest Additions.  You need to go to the menus at the top of the running VM window: Devices > Insert Guest Additions CD image.  Then, in the guest, run the [FONT=Courier New]VBoxLinuxAdditions.run[/FONT] file on that disc as root.

---

### Post by sed_faster on 2021-02-01
Hello,

Thanks, but I didn't know you needed mount cdrom on folder. This videos, link and your comments helped me.

[https://www.virtualbox.org/manual/ch04.html#additions-linux](https://www.virtualbox.org/manual/ch04.html#additions-linux)
[https://www.youtube.com/watch?v=WiYNrx1Grak](https://www.youtube.com/watch?v=WiYNrx1Grak)
[https://www.youtube.com/watch?v=1t1zrQy2HV4](https://www.youtube.com/watch?v=1t1zrQy2HV4)

---

### Post by wildmanne39 on 2021-02-01
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by sed_faster on 2021-02-01
Maybe this issue isn't entirely related to the virtualbox  but more with the nginx. I mount a share folder, between my windows10 (host) and ubuntu server (guest), to provide my php and html files. But I received page error 403 on my browser. I think it's because the owner or permissions folders (please see next image)
[ATTACH=CONFIG]287882[/ATTACH]

Already tried change the owner and permissions, through command "chown 777 or command chown" but I can't change the permission or owner. Any idea how can I solve this problem?

Thanks

---

