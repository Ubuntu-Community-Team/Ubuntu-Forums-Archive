---
title: "Video drivers for Win7 guest in Virtualbox"
date: 2012-06-01
forum: Virtualisation
---

### Post by brad1138 on 2012-06-01
I just installed Win 7 in Virtual box inside Ubuntu 12.04. It is actually working very good. I did notice that Win 7 see the video card as "standard VGA adapter", I have a Nvidia GTX 260. Is that as good as the graphics are going to get, or can I get Win 7 to actually see it as what it is?

Thanks,
Brad

---

### Post by Habitual on 2012-06-01
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

---

### Post by lukeiamyourfather on 2012-06-01
The graphics card can't be utilized in a virtual machine like you're thinking. There's very limited support with many caveats. Maybe in a few more years this will improve. If you need hardware accelerated 3D graphics then dual boot with Windows instead of using a virtual machine.

If you just want to make the virtual machine use a different resolution install the VirtualBox guest additions in the Windows guest. They are available as an option for the optical drive, it says something like "Install Guest Addons" which will mount an image of the software in the guest so it can be installed.

---

### Post by brad1138 on 2012-06-01
> **lukeiamyourfather said:**
> The graphics card can't be utilized in a virtual machine like you're thinking. There's very limited support with many caveats. Maybe in a few more years this will improve. If you need hardware accelerated 3D graphics then dual boot with Windows instead of using a virtual machine.

If you just want to make the virtual machine use a different resolution install the VirtualBox guest additions in the Windows guest. They are available as an option for the optical drive, it says something like "Install Guest Addons" which will mount an image of the software in the guest so it can be installed.

Guest addons worked and it is working great thanks.

---

### Post by Habitual on 2012-06-01
Glad it worked out!

---

