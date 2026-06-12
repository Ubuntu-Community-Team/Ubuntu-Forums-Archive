---
title: "Server stuck at boot - starting configure network devices"
date: 2016-09-10
forum: Server Platforms
---

### Post by Mahesh_More on 2016-09-10
My Ubuntu server is not booting after distro-update. It got stuck at "starting configure network devices". I tried booting through advance options and choosing old kernel version but northing worked.
Can someone here help me please to sort this issue.

---

### Post by darkod on 2016-09-10
In 16.04 the naming of the interfaces has changed, maybe that creates an issue in your case. Did you check /etc/network/interfaces and modified it if necessary?

---

### Post by Mahesh_More on 2016-09-11
It didnt boot into OS,cant check interfaces file.

---

### Post by darkod on 2016-09-11
Try this to open the root shell of a system that is not booting: [http://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell](http://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell)

That should allow you to check the /etc/network/interfaces content. And to modify it if needed. When you are in the root shell you can check all interface names by:
```
lshw -short | grep network
```

If the enable networking step does not work for you because of your network problems, simply skip that step and at the end in the root shell do this to enable RW mode:
```
mount -o rw,remount /
```

That will remount the root partition and give you access to write to it.

---

