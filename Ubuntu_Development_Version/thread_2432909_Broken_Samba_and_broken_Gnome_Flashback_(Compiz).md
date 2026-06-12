---
title: "Broken Samba and broken Gnome Flashback (Compiz)"
date: 2019-12-10
forum: Ubuntu Development Version
---

### Post by Smask on 2019-12-10
Hello All!


With the latest update of Samba, I can't mount shares on my other machines (also running 20.04) and my old NAS.

Nautilus says "Unhandled error message: Failed to retrieve share list from server: Connection refused" when trying another Ubuntu 20.04 box and "Unhandled error message: Failed to mount Windows share: Invalid argument" when trying to mount the NAS-share.

When Gnome Flashback went v3.35 it broke Compiz so that I can't switch application using Alt-Tab or grab window edges to resize. And no standard windows caption bar, unless it is a compact one with extra buttons, menus and text fields, like Nautilus or Text Edit. You have to switch application using Gnome Panel.  Workaround: Use Metacity.

---

### Post by muktupavels on 2019-12-14
GNOME Flashback now provides upstream compiz configuration. Check CompizConfig Settings Manager, what profile it uses now?

---

### Post by Smask on 2019-12-15
> **muktupavels said:**
> GNOME Flashback now provides upstream compiz configuration. Check CompizConfig Settings Manager, what profile it uses now?

The only one available, "Default". There I discovered the Backend setting, which were set to "Flat-file Configuration Backend", so I tried the other option, the GSettings one, and that fixed my issues.



The Samba issues regarding mounting other Ubuntu machines seems to have it sorted itself out, but I still can't mount the old NAS. My guess is that they dropped some old Samba protocol versions. Is there a program that I can use to query Samba servers on other machines, to see what version of Samba they are using? (My NAS is a Netgear Duo, and the first models had Sparc CPUs with software based on Debian (Sparc). The last firmware update were dated from May 2017)

```
fredrik@Lenny:~$ smbclient -L nasse.local
Unable to initialize messaging context
protocol negotiation failed: NT_STATUS_CONNECTION_DISCONNECTED
fredrik@Lenny:~$ 

```

---

### Post by muktupavels on 2019-12-15
```
echo $COMPIZ_CONFIG_PROFILE
```

Can you post output from above command?

---

### Post by Smask on 2019-12-15
I noticed that I got more profile options with the GSettings Configuration Backend than with the Flat-file one. (Default, Unity-lowgfx and Unity)

```
fredrik@xccube:~$ echo $COMPIZ_CONFIG_PROFILE
gnome-flashback
fredrik@xccube:~$ 
```
I guess that gnome-flashback is the default one for me.

---

### Post by muktupavels on 2019-12-15
You had problem because gnome-flashback did not install needed configurations files. There will be update that will fix that. And then you should have also gnome-flashback profile. I don't know if compiz will automatically use that or keep using your current profile, but please test gnome-flashback profile. If you think defaults are not good then please suggest changes upstream - [https://gitlab.gnome.org/GNOME/gnome-flashback/issues](https://gitlab.gnome.org/GNOME/gnome-flashback/issues).

---

### Post by Smask on 2019-12-15
Please notice that all of my machines are old and upgraded, no new installs. I plan on adding an old basic machine that I will only use with my 3D-printer. I will wipe the HD and install fresh on this machine. I'll grab a monitor at work tomorrow (works at a second hand store and we throw lots of old VGA only computer displays in the recycle bin)

---

### Post by Morbius1 on 2019-12-15
For the samba issue: um ... gnome and samba developers aren't talking to each other again.

Edit /etc/samba/smb.conf.

Right under the workgrpup = WORKGROPUP line add these two on all your 20.04 machines:
```
client min protocol = NT1

server min protocol = NT1
```

Then reboot the box. Restarting the smbd server is not enough. You have to reboot.

**Or ...** you can start thinking about cifs mounts of these shares which takes things away from gvfs and gnome and puts it under the control of the Linux kernel and gives you more control over what's going on.

For example I suspect the problem with the NAS is that it's running with SMB1 but 20.04 by default can only access it with SMB2 so you get the protocol negotiation error. With a cifs mount you can specify that for that server run with smb1. For example:

sudo mount -t cifs //nasse.local/share-name /some-mount-point -o guest,uid=1000,vers=1.0

The vers=1.0 tells cifs to mount using the smb1 dialect.

---

