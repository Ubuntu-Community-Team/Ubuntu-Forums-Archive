---
title: "Ubuntu not start properly"
date: 2021-03-02
forum: Virtualisation
---

### Post by satimis on 2021-03-02
Hi all,

Ubuntu 20.04 desktop

For unknown cause I just found unable to start Ubuntu properly. Finally it ends at "Not listed?" screen. (Please see attached screenshot).

Please advise where I have to check to sort out the problem. Thanks

Regards

---

### Post by grahammechanical on 2021-03-02
What you are seeing is the login screen. It should show the username on top of the words "not listed." So, the big question is, why is your username not showing?

What happens if you press Enter? Does a panel for the password appear? That is what would happen normally. If you click "not listed" with the mouse a username panel should appear. Try entering the username and then press enter. A password panel should then appear. Put in the password and press Enter. What happens?

Is it possible that the only username for that machine has been deleted?

Regards

---

### Post by dino99 on 2021-03-03
you might boot into recovery mode or try tty, then glance at 'journalctl -b' output into a terminal , for error (red line)

---

### Post by satimis on 2021-03-03
Hi,

Clicking mouse or hitting Enter key without response.

I can't start boot loader, pressing ESC key during booting without response.  This is a VM/Guest of Oracle VirtualBox.  I have posted my problem on their Forum.  The moderator replied me saying that this is the problem of Ubuntu, not their problem.

Please advise how to start recovery mode after booting up Ubunru?

Regards

Edit:
===
Finally I started recovery mode, drop to root shell and performed follows;

# mount -o remount,rw /
# mount -a

# lsblk```

sda
 -sda1
     -ubuntu--vg-root
     -ubuntu--vg-swap_1
sr0 ......

```

# grep '/home' /etc/fstab | grep ext
# mount /dev/sda1 /home```

mount: /home: unknown filesystem tyep 'LVM2_member'/

```
I have no idea to go further?  Kindly advise.  Thanks

Regards

---

### Post by DuckHook on 2021-03-03
Your thread has been moved to Virtualisation for responses more relevant to your issue.

---

### Post by lammert-nijhof on 2021-03-08
Try to reinstall Ubuntu and avoid lvm2 installs. Just use the standard ext4 install and use the whole virtual disk.
Did you check the SHA codes for the download? Maybe the download had a problem.

---

### Post by satimis on 2021-03-08
> **lammert-nijhof said:**
> Try to reinstall Ubuntu and avoid lvm2 installs. Just use the standard ext4 install and use the whole virtual disk.
Did you check the SHA codes for the download? Maybe the download had a problem.
Hi,

Thanks for your advice.

According to my recollection I have upgraded Ubuntu lately.  Maybe the problem came from download.

I think to delete this VM would be easier for me.  I have only one cloned website running on it.  I'll clone another new VM from a VM having LAMP installed.  Afterwards I'll clone the deleted website on Duplicator packages created on its LIVE website.

Thanks

Regards

---

