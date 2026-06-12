---
title: "Systemd Container Problems"
date: 2020-02-29
forum: Virtualisation
---

### Post by arimakidd on 2020-02-29
I used the command:
```
[COLOR=#2E8B57][FONT=Monaco]machinectl pull-tar https://cloud-images.ubuntu.com/trusty/current/trusty-server-cloudimg-amd64-root.tar.gz  ubuntuTest[/FONT][/COLOR]
```

Expecting to pull an image and have the OS Tree setup so that my next command would be
```
[COLOR=#000000][FONT=Arial]systemd-nspawn -M ubuntuTest[/FONT][/COLOR]
```

But I keep getting an error that I am running out of space.  This is what it looks like:
```
[COLOR=#2E8B57][FONT=Monaco]tar: var/lib/dpkg/alternatives/telnet: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/awk: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/lzma: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/vtrgb: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/mt: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/jsondiff: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/newt-palette: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/www-browser: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/rename: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/vim: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/vi: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/locate: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/vimdiff: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/pico: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/ftp: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/pager: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/w: Cannot write: No space left on devicetar: var/lib/dpkg/alternatives/rview: Cannot write: No space left on device[/FONT][/COLOR]
```
I have a lot of space and this looks very similar to what is being described on github here:
[https://github.com/systemd/systemd/issues/5859](https://github.com/systemd/systemd/issues/5859)
From the link above this is what I think I am also experiencing:
```
[COLOR=inherit][FONT=Menlo]Apparently, machinectl creates a filesystem which [/FONT][/COLOR][COLOR=inherit][FONT=Menlo]**is**[/FONT][/COLOR][COLOR=inherit][FONT=Menlo] too small [/FONT][/COLOR][COLOR=inherit][FONT=Menlo]**and**[/FONT][/COLOR][COLOR=inherit][FONT=Menlo]**then**[/FONT][/COLOR][COLOR=inherit][FONT=Menlo] fails with a rather vague error message. My / filesystem has plenty [/FONT][/COLOR][COLOR=inherit][FONT=Menlo]**of**[/FONT][/COLOR][COLOR=inherit][FONT=Menlo] space free. I had to fiddle with qemu-img resize to resize /var/lib/machines.raw, btrfs filesystem resize to grow the file system [/FONT][/COLOR][COLOR=inherit][FONT=Menlo]**and**[/FONT][/COLOR][COLOR=inherit][FONT=Menlo] machinectl set-limit.[/FONT][/COLOR]
```

What can I do to install a  systemd container?

---

### Post by kevdog on 2020-03-02
Hi - I don't have a lot of knowledge of what you are trying to do.  Are you trying to containerize the trusty-server?  Could you not just use a docker image for a container?

---

### Post by arimakidd on 2020-03-03
Yes docker is most popular but I am familiarizing myself with systemd-containers as this offers a very quick way of setting up a virtual OS that is packaged with the excellent features of Systemd.  Machinectl and systemd-nspawn commands are easy to use.  I wish to learn more about systemd-containers.  It works well with CenotOS but debian based architectures are giving me some trouble.  I can't install a container on ubuntu nor mint.  I can't even pull the image.  Looking for help.

---

### Post by arimakidd on 2020-03-03
When you run the machinectl pull-tar command it appears to create  several squashfs that run out of space and a btrfs as well. I found this  out having ran "df -Th" after running the machinectl pull-tar command:
```
machinectl pull-tar https://cloud-images.ubuntu.com/trusty/current/trusty-server-cloudimg-amd64-root.tar.gz ubuntuTest
```
This is where I am stuck. Help wanted

[ATTACH=CONFIG]285142[/ATTACH]

---

### Post by arimakidd on 2020-03-04
Just wanted to let the forum know, this issue was solved.  Taken from this link:
[https://askubuntu.com/questions/1094245/machinectl-not-importing-diskimage](https://askubuntu.com/questions/1094245/machinectl-not-importing-diskimage)

The file system that machinectl creates has to be resized:
```

[LIST]
[*][FONT=inherit]Unmount /var/lib/machines & resize /var/lib/machines.raw:[/FONT]
$ umount /var/lib/machines ; qemu-img resize -f raw /var/lib/machines.raw +16G
[*][FONT=inherit]Restart machinectl Service:[/FONT]
$ systemctl restart /var/lib/machines
[*][FONT=inherit]Resize btrfs Volume:[/FONT]
$ btrfs filesystem resize max /var/lib/machines
[/LIST]

```

SOLVED

---

