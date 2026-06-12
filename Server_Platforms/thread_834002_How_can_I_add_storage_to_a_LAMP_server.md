---
title: "How can I add storage to a LAMP server?"
date: 2008-06-19
forum: Server Platforms
---

### Post by thestitch on 2008-06-19
I have a lamp server running 8.04, and I need to add some hard drive space to it. I have a DAM program (resourcespace) running on the server and I would like to add the storage to expand the programs capacity.

The program stores all of it's assets in a single directory, and I need to expand the capacity available to that directory.

Since many server apps seem to have a central storage location and can grow rapidly, there must be some kind of standard method to add transparent storage to a server (I hope!).

I can install a new drive in the server or set up a NAS box, which ever is recommended by all of you.

Thanks for any replies.

---

### Post by hyper_ch on 2008-06-19
well, either you just add the new harddisk and mount it as that folder or you use LVM.... [https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)

---

### Post by gtdaqua on 2008-06-19
You can use open-iscsi to connect to SAN boxes. They are purely over the network so you can plug and play anytime you want. But this better be on a gigabit ethernet backbone.

Transparent storage at even higher levels would require storage virtualization. If you got $$, then try Lefthand Networks. Unlike server virtualization, storage v-zation does not necessarily save costs, but drastically improves management and performance.

---

### Post by thestitch on 2008-06-19
If I had used LVM from the beginning I could have added transparent storage whenever I needed?

Is storage v-zation the same as LVM? If I set up a 500 gb LVM, can I just add another drive to it later?


If so I can just rsync my filestore folder to the new LVM and mount it as the folder, then add another drive to the LVM when I need.

---

### Post by hyper_ch on 2008-06-20
yes, you can with lvm...

---

