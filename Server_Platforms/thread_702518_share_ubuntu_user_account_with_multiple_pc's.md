---
title: "share ubuntu user account with multiple pc's"
date: 2008-02-20
forum: Server Platforms
---

### Post by Peturrr on 2008-02-20
Since this situation probably arises more in corp environments and I assume the server people here have more experience with it: Please check my thread with a question about [using 1 shared account on multiple pc's]("http://ubuntuforums.org/showthread.php?t=702509").

---

### Post by 0x845fed on 2008-02-21
The reply to the linked post seemed like the best alternative.

---

### Post by argraff on 2008-02-21
Working on this exact issue at a nonprofit at the moment. VNC wasn't fast enough (10 computers, 20 user accounts, 1 server for files). We're looking into LDAP and NFS now.

I would love to hear from people who've done this successfully!

---

### Post by Peturrr on 2008-02-24
if vnc wasn't fast enough, maybe you could look at nx from nomachine. It is a lot faster in terms of bandwith usage.

---

### Post by k_grdn on 2008-02-24
Hi,

For such a small no: of machines have you considered the good old yellow pages: NIS.

Straight forward and simple, for home drives use autofs or nfs.

LDAP is more suited for larger networks which require interoptability  with other services, mail, crm's etc..

Regards,

k_grdnc

---

### Post by astrotech226 on 2008-02-24
> **Peturrr said:**
> Since this situation probably arises more in corp environments and I assume the server people here have more experience with it:

If you get creative with your NFS mount, you could create symbolic links for the directories you want on both machines.  Obviously, the compiz stuff won't work because of the different architectures, but other files would be fine.  Let's say you create an nfs mount with your shared files on /mnt/nfs-share.  Here's a few links you could make that would allow Firefox, Thunderbird and your Documents to appear on both machines transparently.
```

ln -s /mnt/nfs-share/.mozilla-thunderbird ~/.mozilla-thunderbird
ln -s /mnt/nfs-share/.mozilla ~/.mozilla
ln -s /mnt/nfs-share/Documents ~/Documents
```

This allows you to pick and chose which directories you want shared.  Certain things will need to be maintained separately.  One example I can think of is your gnome panels, one machine may support cpu frequency scaling and the other doesn't.  So having that applet on both machines won't do you any good.  So the gnome portions may be better suited as individual configurations and not shared.

---

### Post by rome-NY on 2008-02-24
You want to NIS. On suse it works great but cannot get ubuntu clients to work. I have been trying for weeks and I can't get it and I'm real close. I am checking with other distros that will work with NIS. I will post back when I find one besdies outdated suse 10.0

---

### Post by k_grdn on 2008-02-26
Hi,

For ubuntu clients just install the nis package and edit /etc/nsswitch.conf:

passwd:         compat nis files
group:          compat nis files
shadow:         compat nis files

Regards,

k_grdn

---

