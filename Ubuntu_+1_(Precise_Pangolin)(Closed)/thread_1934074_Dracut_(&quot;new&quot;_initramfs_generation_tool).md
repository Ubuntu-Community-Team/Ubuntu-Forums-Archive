---
title: "Dracut (&quot;new&quot; initramfs generation tool)"
date: 2012-03-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-03-01
Read about this today in Linux Format and just tried it out blindly in a VM. I reinstalled to show the ouput here:

```
paul@precise:~$ sudo aptitude reinstall dracut
The following packages will be REINSTALLED:
  dracut 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/123 kB of archives. After unpacking 0 B will be used.
(Reading database ... 204485 files and directories currently installed.)
Preparing to replace dracut 013-2 (using .../archives/dracut_013-2_all.deb) ...
Unpacking replacement dracut ...
Processing triggers for man-db ...
Setting up dracut (013-2) ...
**[COLOR="Red"]dracut: Generating /boot/initramfs-3.2.0-17-generic.img[/COLOR]**
E: Directories consolefonts, consoletrans, keymaps, unimaps not found.  Please inform us about the issue including your OS name and version.
                                         
paul@precise:~$
```

Changed the **[COLOR="Red"]initrd[/COLOR]** line in **[COLOR="Red"]/boot/grub/grub.cfg[/COLOR]** to:

```
initrd  /boot/initramfs-3.2.0-17-generic.img
```

Rebooted ok, despite the complaint above about missing directories. Boot is supposed to be faster and I think maybe it was. Not a dramatic difference in the VM anyway.

Anyone else here tried it?

I'm not sure how this is supposed to play with grub2 and kernel upgrades or whether an **[COLOR="Red"]initrd[/COLOR]** line is even still needed.

There's some stuff about speeding up the boot process here:

[http://kernel.org/pub/linux/utils/boot/dracut/dracut.html#id388074](http://kernel.org/pub/linux/utils/boot/dracut/dracut.html#id388074)

Some other links I've found that I need to look at later:

[https://dracut.wiki.kernel.org/](https://dracut.wiki.kernel.org/)
[http://fedoraproject.org/wiki/Dracut](http://fedoraproject.org/wiki/Dracut)
[http://www.linux-archive.org/community-support-fedora-users-users-lists-fedoraproject-org/613695-quick-dracut-grub2-question.html](http://www.linux-archive.org/community-support-fedora-users-users-lists-fedoraproject-org/613695-quick-dracut-grub2-question.html)
[http://manpages.ubuntu.com/manpages/maverick/man8/dracut.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/dracut.8.html)

---

### Post by lucazade on 2012-03-01
Interesting, didn't know about it.. well.. I'll give it a try.
thanks for heads up!

---

### Post by zika on 2012-03-01
Dracut is in Ubuntu much before I've entered Ubuntu... It does not seem to have developed much in the meantime. I might be very wrong... About later, not about former...
Update. I'm wrong even about former: [https://launchpad.net/ubuntu/+source/dracut](https://launchpad.net/ubuntu/+source/dracut) but not so much wrong...

---

