---
title: "VirtualBox folder sharing"
date: 2008-05-05
forum: Virtualisation
---

### Post by ade234uk on 2008-05-05
I have Ubuntu installed as a Virtual Machine using VirtualBox in Windows. Please don't get angry!!

Can someone give me some pointers on how I share a folder inside Ubuntu on the Virtual machine with my main XP desktop.

I have LAMP set up on my Ubuntu Virtual Machine and I need the facility to be able to upload .sql files to MySQL so that I can test the database.

Thank you for your help.

---

### Post by p_quarles on 2008-05-05
Moved to Virtualization. 

I think that you will have better luck creating a shared folder on the host system (Windows) and then configure the guest system to save any files that need to be shared on that folder. 

Alternatively, you could set up an ftp/sftp server on the virtual machine, if you simply want to upload files.

---

### Post by ade234uk on 2008-05-05
Of course I never thought of the FTP solution.

---

