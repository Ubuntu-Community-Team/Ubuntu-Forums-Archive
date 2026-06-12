---
title: "[IDEA] &quot;Map Network Folders&quot; applet"
date: 2007-11-24
forum: Ubuntu Brainstorm
---

### Post by maybeway36 on 2007-11-24
One nice thing for Ubuntu to have would be a "Map Network Folders" applet, the equivalent of "Map Network Drive" in Windows. The applet would allow the user to add, remove, and edit cifs and smbfs entires in /etc/fstab through a GUI.
The applet would allow configuration of:
Computer name
Share name
Username
Password (with a "NOTE: Everybody can read this" warning)
Mount point (lets user choose what comes after /media)
Writable by: one user, one group, or everybody?
Readable by: one user, one group, or everybody?
CIFS/SMBFS (in case one doesn't work; CIFS should be default)

---

### Post by tjagoda on 2007-11-25
Isnt this already doable with the "Connect to Server" applet?

---

### Post by maybeway36 on 2007-11-26
That doesn't actually mount the share, so only GNOME applications can connect to it.

---

### Post by tjagoda on 2007-11-26
Ahhhh, I see.  Perhaps it would be a better idea to expand upon that applet, instead of building another function which people could see as redundant?  I'm speaking plainly in terms of getting your idea more attractive to possible development.

---

### Post by maybeway36 on 2007-11-29
Isn't "Connect to Server" kind of pointless for anything besides FTP anyway? I don't think many people use that - we can take it off the menu.

---

### Post by 23meg on 2007-11-29
[QUOTE=maybeway36]Isn't "Connect to Server" kind of pointless for anything besides FTP anyway?[/QUOTE]

It's not. It has its bugs (known and filed), but especially with the introduction of gvfs in GNOME 2.22, it's reasonable to expect it to get much better.

[QUOTE=maybeway36]I don't think many people use that[/QUOTE]

How do you know?

---

### Post by maybeway36 on 2007-11-29
Connect to Server doesn't actually mount the share on the filesystem. There's no easy way to do that without editing fstab (for example, sharing a music library over the network.) Since it doesn't mount the share, it doesn't really have much advantage over just System>Network.

---

### Post by wormser on 2007-12-02
> **maybeway36 said:**
> Isn't "Connect to Server" kind of pointless for anything besides FTP anyway? I don't think many people use that - we can take it off the menu.

I use it! It is great tool for setting up ssh folders instead of using sshfs.  I would hate to see it go off the menu.

---

### Post by maybeway36 on 2007-12-02
How does Connect to Server work? Does it mount shares on the filesystem?

---

### Post by other guy on 2007-12-07
> **wormser said:**
> I use it! It is great tool for setting up ssh folders instead of using sshfs.  I would hate to see it go off the menu.


I really like this feature. It gives me a nice amount of flexibilty within my home network. Since I may create folders within a drive, that are not going to last long. Even the shares that are going to remain for long periods. It makes it easy for the other network user to get to her folders as she likes. 

Taking this out would kind of force me to move off Ubuntu or find something that has similar features. The ssh, it makes it work really nice. No setting up the fstab or anything. Plus it works really good with bookmarks within Nautilus too.

---

### Post by maybeway36 on 2007-12-07
I still would like to see a porgram for setting up CIFS mounts in the fstab, because as it is there's no other way to access a remote music library for new users. Obviously, Connect to Server needs to stay, though.

---

