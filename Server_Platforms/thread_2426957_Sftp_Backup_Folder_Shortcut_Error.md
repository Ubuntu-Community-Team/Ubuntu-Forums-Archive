---
title: "Sftp Backup Folder Shortcut Error"
date: 2019-09-16
forum: Server Platforms
---

### Post by chrispet on 2019-09-16
Hi! I have an ubuntu server 18.04 and i have installed and congifured openssh as sftp server. I have disabled all ways to log in the server except sftp connection. My backs are in other partition so i want to create a shortcut from backup partition into my site. I made the shortcut but when i'm trying to access it from filezilla i can't because filezilla can't regognize it. What can i do for that?

I made the shortcut with this way : ```
ln -s /backuppartition /webroot/
```

---

### Post by TheFu on 2019-09-16
Have you tried using a native sftp client like the normal CLI **sftp** program or a Linux file manager like **Caja**, **Thunar**, **Nautilus**, **Nemo**?  I didn't test them all, but caja followed the link using the sftp:// URL perfectly.  So did the **sftp** client program.  All of them fully honored by ssh-keys for authentication too, as expected.

I would guess it is a filezilla issue.  If you are stuck on Windows, might try **WinSCP**.  I don't specifically remember whether it supports symbolic links or not, but I don't recall problems, so it probably does. I've never used filezilla.

I'm a little concerned about linking a backup area to a website.  Backups usually contain lots of sensitive data.  Plus, if there aren't 3 separate copies of the files, on at least 2 different machines, then it isn't a real backup.

---

